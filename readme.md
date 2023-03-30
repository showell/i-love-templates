
# I F***ing LOVE templates! #
# They are so damn elegant and composable!!! #
## How are you not understanding this??? ##

#### navbar_icon_and_title.hbs ####
<pre>
{{#if web_public_stream}}
<i class="zulip-icon zulip-icon-globe" aria-hidden="true"></i>
{{else if icon}}
<i class="fa fa-{{icon}}" aria-hidden="true"></i>
{{/if}}
{{title}}

</pre>
#### message_feed_errors.hbs ####
<pre>
<div class="history-limited-box">
    <p>
        <i class="fa fa-exclamation-circle" aria-hidden="true"></i>
        {{#tr}}
        Some older messages are unavailable.
        <z-link>Upgrade your organization</z-link>
        to access your full message history.
        {{#*inline "z-link"}}<a href="/plans/" target="_blank" rel="noopener noreferrer">{{> @partial-block}}</a>{{/inline}}
        {{/tr}}
    </p>
</div>
<div class="all-messages-search-caution hidden-for-spectators" hidden>
    <p>
        <i class="fa fa-exclamation-circle" aria-hidden="true"></i>
        {{#tr}}
        End of results from your
        <z-link>history</z-link>.
        {{#*inline "z-link"}}<a href="/help/search-for-messages#searching-shared-history"
          target="_blank" rel="noopener noreferrer">{{> @partial-block}}</a>{{/inline}}
        {{/tr}}
        &nbsp;
        <span>
            {{#tr}}
            Consider <z-link>searching all public streams</z-link>.
            {{#*inline "z-link"}}<a class="search-shared-history" href="">{{> @partial-block}}</a>{{/inline}}
            {{/tr}}
        </span>
    </p>
</div>
<div class="empty_feed_notice_main"></div>

</pre>
#### navbar.hbs ####
<pre>
<div class="header">
    <nav class="header-main" id="top_navbar">
        <div class="column-left">
            <a class="brand no-style" href="#">
                <img id="realm-logo" src="" alt="" class="nav-logo no-drag"/>
            </a>
        </div>
        <div class="column-middle" id="navbar-middle">
            <div class="column-middle-inner">
                <div id="streamlist-toggle" {{#if embedded}}class="hide-streamlist-toggle-visibility"{{/if}} title="{{t 'Stream list' }} (q)">
                    <a id="streamlist-toggle-button" role="button" tabindex="0"><i class="fa fa-reorder" aria-hidden="true"></i>
                        <span id="streamlist-toggle-unreadcount">0</span>
                    </a>
                </div>
                <div class="top-navbar-border top-navbar-container">
                    <div id="message_view_header" class="notdisplayed">
                    </div>
                    {{#if search_pills_enabled }}
                    <div id="searchbox">
                        <form id="searchbox_form" class="navbar-search">
                            <div id="search_arrows" class="pill-container input-append">
                                <span class="search_icon search_open" ><i class="zulip-icon zulip-icon-search"></i></span>
                                <div contenteditable="true" class="input search-query input-block-level" id="search_query" type="text" placeholder="{{t 'Search' }}"
                                  autocomplete="off" aria-label="{{t 'Search' }}" title="{{t 'Search' }} (/)">
                                </div>
                                <button class="btn search_close_button" type="button" id="search_exit" aria-label="{{t 'Exit search' }}">
                                    <i class="zulip-icon zulip-icon-close" aria-hidden="true"></i>
                                </button>
                            </div>
                        </form>
                    </div>
                    {{else}}
                    <div id="searchbox_legacy">
                        <form id="searchbox_form" class="navbar-search">
                            <div id="search_arrows" class="input-append">
                                <span class="search_icon search_open" ><i class="zulip-icon zulip-icon-search"></i></span>
                                <input class="search-query input-block-level home-page-input" id="search_query" type="text" placeholder="{{t 'Search' }}"
                                  autocomplete="off" aria-label="{{t 'Search' }}" title="{{t 'Search' }} (/)"/>
                                <button class="btn search_close_button" type="button" id="search_exit" aria-label="{{t 'Exit search' }}"><i class="zulip-icon zulip-icon-close" aria-hidden="true"></i></button>
                            </div>
                        </form>
                    </div>
                    {{/if}}
                </div>
            </div>
        </div>
        <div class="column-right">
            <div class="only-visible-for-spectators">
                <div class="spectator_login_buttons hide-xl">
                    <a href="/register/"  class="signup_button">
                        <span>{{t 'Sign up' }}</span>
                    </a>
                    <div class="divider">|</div>
                    <a class="login_button">
                        <span>{{t 'Log in' }}</span>
                    </a>
                </div>
                <div class="spectator_narrow_login_button hide show-xl" data-tippy-content="{{t 'Log in' }}" data-tippy-placement="bottom">
                    <a class="login_button">
                        <i class="fa fa-sign-in"></i>
                    </a>
                </div>
            </div>
            <div id="userlist-toggle" title="{{t 'User list' }} (w)" class="hidden-for-spectators">
                <a id="userlist-toggle-button" role="button" tabindex="0"><i class="fa fa-group" aria-hidden="true"></i>
                    <span id="userlist-toggle-unreadcount">0</span>
                </a>
            </div>
            <div id="navbar-buttons" {{#if embedded}}class="hide-navbar-buttons-visibility"{{/if}}>
            </div>
        </div>
    </nav>
</div>

</pre>
#### typing_notifications.hbs ####
<pre>
{{! Typing notifications }}
<ul id="typing_notification_list">
    {{#if several_users}}
        <li class="typing_notification">{{t "Several people are typing…" }}</li>
    {{else}}
        {{#each users}}
            {{> typing_notification}}
        {{/each}}
    {{/if}}
</ul>

</pre>
#### compose_select_enter_behaviour_popover.hbs ####
<pre>
<div class="enter_sends_choices grey-box">
    <label class="enter_sends_choice">
        <input type="radio" class="prop-element" value="true"{{#if enter_sends_true }} checked{{/if}} />
        <div class="enter_sends_choice_text">
            <span>
                {{#tr}}
                    <z-shortcut></z-shortcut> to send
                    {{#*inline "z-shortcut"}}<kbd>Enter</kbd>{{/inline}}
                {{/tr}}
            </span>
            <span class="enter_sends_minor">
                {{#tr}}
                    <z-shortcut></z-shortcut> to add a new line
                    {{#*inline "z-shortcut"}}<kbd>Ctrl</kbd>+<kbd>Enter</kbd>{{/inline}}
                {{/tr}}
            </span>
        </div>
    </label>
    <label class="enter_sends_choice">
        <input type="radio" class="prop-element" value="false"{{#unless enter_sends_true }} checked{{/unless}} />
        <div class="enter_sends_choice_text">
            <span>
                {{#tr}}
                    <z-shortcut></z-shortcut> to send
                    {{#*inline "z-shortcut"}}<kbd>Ctrl</kbd>+<kbd>Enter</kbd>{{/inline}}
                {{/tr}}
            </span>
            <span class="enter_sends_minor">
                {{#tr}}
                    <z-shortcut></z-shortcut> to add a new line
                    {{#*inline "z-shortcut"}}<kbd>Enter</kbd>{{/inline}}
                {{/tr}}
            </span>
        </div>
    </label>
</div>

</pre>
#### read_receipts.hbs ####
<pre>
<ul id="read_receipts_list">
    {{#each users}}
        <li class="view_user_profile" data-user-id="{{user_id}}" tabindex="0" role="button">
            <img class="read_receipts_user_avatar" src="{{avatar_url}}" />
            <span>{{full_name}}</span>
        </li>
    {{/each}}
</ul>

</pre>
#### compose_control_buttons_in_popover.hbs ####
<pre>
<a role="button" data-format-type="bold" class="compose_control_button fa fa-bold formatting_button" aria-label="{{t 'Bold' }}" tabindex=0 data-tippy-content="{{t 'Bold' }}"></a>
<a role="button" data-format-type="italic" class="compose_control_button fa fa-italic formatting_button" aria-label="{{t 'Italic' }}" tabindex=0 data-tippy-content="{{t 'Italic' }}"></a>
<a role="button" data-format-type="link" class="compose_control_button fa fa-link formatting_button" aria-label="{{t 'Link' }}" tabindex=0 data-tippy-content="{{t 'Link' }}"></a>
<div class="divider hide-sm">|</div>
<a role="button" class="compose_control_button compose_help_button fa fa-question" tabindex=0 data-tippy-content="{{t 'Message formatting' }}" data-overlay-trigger="message-formatting"></a>

</pre>
#### accounts_send_confirm.html ####
<pre>
{% extends "zerver/portico_signup.html" %}
{# Displayed after a user attempts to sign up. #}

{% block title %}
<title>{{ _("Confirm your email address") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<!-- The following empty tag has unique data-page-id so that this
page can be easily identified in it's respective JavaScript file -->
<div data-page-id="accounts-send-confirm"></div>
<div class="app portico-page">
    <div class="app-main portico-page-container center-block flex full-page account-creation new-style">
        <div class="inline-block">

            <div class="get-started">
                <h1>{{ _("Thanks for signing up!") }}</h1>
            </div>

            <div class="white-box">
                <p>{% trans %}Check your email (<span class="user_email semi-bold">{{ email }}</span>) so we can get started.{% endtrans %}</p>

                {% include 'zerver/dev_env_email_access_details.html' %}

                <p>{% trans %}Still no email? We can <a href="#" id="resend_email_link">resend it</a>.{% endtrans %}
                    <i class="grey">({{ _("Just in case, take a look at your Spam folder.") }})</i></p>
                {% if realm_creation %}
                <form class="resend_confirm" action="/new/" method="post" style="position: absolute;">
                    {{ csrf_input }}
                    <input type="hidden" class="email" id="email" value="{{ email }}" name="email"/>&nbsp;
                </form>
                {% else %}
                <form class="resend_confirm" action="/accounts/home/" method="post" style="position: absolute;">
                    {{ csrf_input }}
                    <input type="hidden" class="email" id="email" value="{{ email }}" name="email"/>&nbsp;
                </form>
                {% endif %}
            </div>
        </div>
    </div>
</div>
{% endblock %}

{% block customhead %}
{{ super() }}
{% endblock %}

</pre>
#### status_emoji.hbs ####
<pre>
{{#if .}}
{{#if emoji_alt_code}}
<span class="emoji_alt_code">&nbsp;:{{emoji_name}}:</span>
{{else if still_url}}
<img src="{{still_url}}" class="emoji status-emoji" data-animated-url="{{url}}" data-still-url="{{still_url}}" />
{{else if url}}
{{!-- note that we have no still_url --}}
<img src="{{url}}" class="emoji status-emoji" data-animated-url="{{url}}" />
{{else if emoji_code}}
<span class="emoji status-emoji emoji-{{emoji_code}}"></span>
{{/if}}
{{/if}}

</pre>
#### config_error.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Configuration error") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

<div class="error_page" style="padding-bottom: 60px;">
    <div class="container">
        <div class="row-fluid">
            <img src="{{ static('images/errors/500art.svg') }}" alt=""/>
            <div class="errorbox config-error">
                <div class="errorcontent">
                    <h1 class="lead">{{ _("Configuration error") }}</h1>
                    <br />
                    {% if error_name == "ldap_error_realm_is_none" %}
                        {% trans %}
                        You are trying to log in using LDAP without creating an
                        organization first. Please use EmailAuthBackend to create
                        your organization and then try again.
                        {% endtrans %}
                    {% endif %}

                    {% if error_name == "smtp_error" %}
                        <p>
                            It appears there are problems with the
                            email configuration.
                        </p>
                        {% if not development_environment %}
                        <p>
                            See <code>/var/log/zulip/errors.log</code> for more
                            details on the error.
                        </p>
                        <p>
                            You may also want to test your email configuration,
                            as described in the
                            <a href="https://zulip.readthedocs.io/en/latest/production/email.html">Production installation docs</a>.
                        </p>
                        {% else %}
                        <p>
                            Please have a look at our
                            <a target="_blank" rel="noopener noreferrer" href="https://zulip.readthedocs.io/en/latest/subsystems/email.html#development-and-testing"> setup guide</a>
                            for forwarding emails sent in development
                            environment to an email account.
                        </p>
                        {% endif %}
                    {% endif %}

                    {% if error_name == "dev_not_supported_error" %}
                        {% include "zerver/authentication_backends/dev-not-supported-error.html" %}
                    {% endif %}

                    {% if has_error_template %}
                        {% if development_environment %}
                        {% with %}
                            {% set settings_path = secrets_path %}
                            {% set client_id_key_name = "social_auth_" + social_backend_name + "_key" %}
                            {% include "zerver/authentication_backends/" + social_backend_name + "-error.html" %}
                        {% endwith %}
                        <p>
                            For more information, have a look at
                            the <a href="https://zulip.readthedocs.io/en/latest/development/authentication.html#{{ social_backend_name }}">authentication
                            setup guide</a> for the development environment.
                        </p>
                        {% else %}
                        {% with %}
                            {% set client_id_key_name = "SOCIAL_AUTH_" + social_backend_name.upper() + "_KEY" %}
                            {% include "zerver/authentication_backends/" + social_backend_name + "-error.html" %}
                        {% endwith %}
                        <p>
                            For more information, have a look at
                            our <a href="https://zulip.readthedocs.io/en/latest/production/authentication-methods.html">authentication
                            setup guide</a> and the comments in <code>{{ settings_comments_path }}</code>.
                        </p>
                        {% endif %}
                    {% endif %}

                    {% if social_backend_name == "saml" %}
                        <p>
                            SAML authentication is either not enabled or misconfigured. Have a look at
                            our <a href="https://zulip.readthedocs.io/en/latest/production/authentication-methods.html#SAML">setup guide</a>.
                        </p>
                        {% if development_environment %}
                        <p>
                            See also the
                            <a href="https://zulip.readthedocs.io/en/latest/development/authentication.html#saml">SAML guide</a>
                            for the development environment.
                        </p>
                        {% endif %}
                    {% endif %}

                    {% if error_name == "remoteuser_error_backend_disabled" %}
                    <p>
                        Authentication via the REMOTE_USER header is
                        disabled in `/etc/zulip/settings.py`.
                    </p>
                    {% endif %}
                    {% if error_name == "remoteuser_error_remote_user_header_missing" %}
                    <p>
                        The REMOTE_USER header is not set.
                    </p>
                    {% endif %}
                    {% if error_name == "oidc_error" %}
                    <p>
                        The OpenID Connect backend is not configured correctly.
                    </p>
                    {% endif %}

                    <p>After making your changes, remember to restart
                    the Zulip server.</p>
                    <p><a href=""> Refresh</a> to try again or <a href="/login/">click here</a> to go back to the login page.</p>
                </div>

            </div>
        </div>
    </div>
</div>

{% endblock %}

</pre>
#### streams_subheader.hbs ####
<pre>
<div class="streams_subheader">
    <span>{{ subheader_name }}</span>
</div>

</pre>
#### copy_message_button.hbs ####
<pre>
<div class="copy_button_base copy_message tippy-zulip-tooltip" data-tippy-content="{{t 'Copy and close' }}" aria-label="{{t 'Copy and close' }}" role="button">
    {{> copy_to_clipboard_svg }}
</div>

</pre>
#### portico-header.html ####
<pre>
<div class="header portico-header">
    <div class="header-main" id="top_navbar">
        <div class="float-left">
            {% if custom_logo_url %}
            <a class="brand logo" href="{{ root_domain_uri }}/"><img draggable="false" src="{{ custom_logo_url }}" class="portico-logo" alt="{{ _('Zulip') }}" content="Zulip" /></a>
            {% else %}
            <div class="brand logo">
                <a href="{{ root_domain_uri }}/">
                    <svg class="brand-logo" role="img" aria-label="{{ _('Zulip') }}" xmlns="http://www.w3.org/2000/svg" viewBox="68.96 55.62 1742.12 450.43" height="25">
                        <path fill="hsl(0, 0%, 27%)" d="M473.09 122.97c0 22.69-10.19 42.85-25.72 55.08L296.61 312.69c-2.8 2.4-6.44-1.47-4.42-4.7l55.3-110.72c1.55-3.1-.46-6.91-3.64-6.91H129.36c-33.22 0-60.4-30.32-60.4-67.37 0-37.06 27.18-67.37 60.4-67.37h283.33c33.22-.02 60.4 30.3 60.4 67.35zM129.36 506.05h283.33c33.22 0 60.4-30.32 60.4-67.37 0-37.06-27.18-67.37-60.4-67.37H198.2c-3.18 0-5.19-3.81-3.64-6.91l55.3-110.72c2.02-3.23-1.62-7.1-4.42-4.7L94.68 383.6c-15.53 12.22-25.72 32.39-25.72 55.08 0 37.05 27.18 67.37 60.4 67.37zm522.5-124.15l124.78-179.6v-1.56H663.52v-48.98h190.09v34.21L731.55 363.24v1.56h124.01v48.98h-203.7V381.9zm338.98-230.14V302.6c0 45.09 17.1 68.03 47.43 68.03 31.1 0 48.2-21.77 48.2-68.03V151.76h59.09V298.7c0 80.86-40.82 119.34-109.24 119.34-66.09 0-104.96-36.54-104.96-120.12V151.76h59.48zm244.91 0h59.48v212.25h104.18v49.76h-163.66V151.76zm297 0v262.01h-59.48V151.76h59.48zm90.18 3.5c18.27-3.11 43.93-5.44 80.08-5.44 36.54 0 62.59 7 80.08 20.99 16.72 13.22 27.99 34.99 27.99 60.64 0 25.66-8.55 47.43-24.1 62.2-20.21 19.05-50.15 27.6-85.13 27.6-7.77 0-14.77-.39-20.21-1.17v93.69h-58.7V155.26zm58.7 118.96c5.05 1.17 11.27 1.55 19.83 1.55 31.49 0 50.92-15.94 50.92-42.76 0-24.1-16.72-38.49-46.26-38.49-12.05 0-20.21 1.17-24.49 2.33v77.37z"/>
                    </svg>
                </a>

                {% if page_is_help_center %}
                <span class="light"> | <a href="{{ root_domain_uri }}/help/">{{ doc_root_title }}</a></span>
                {% endif %}
                {% if page_is_api_center %}
                <span class="light"> | <a href="{{ root_domain_uri }}/api/">{{ doc_root_title }}</a></span>
                {% endif %}
                {% if page_is_policy_center %}
                <span class="light"> | <a href="{{ root_domain_uri }}/policies/">{{ doc_root_title }}</a></span>
                {% endif %}
            </div>
            {% endif %}
        </div>

        <div class="float-right top-links">
            {% if user_is_authenticated %}
                {% include 'zerver/portico-header-dropdown.html' %}
            {% else %}
                {% if login_link_disabled %}
                {% elif not only_sso %}
                <a href="{{login_url}}">{{ _('Log in') }}</a>
                {% endif %}
            {% endif %}

            {% if register_link_disabled %}
            {% elif only_sso %}
                <a href="{{ url('login-sso') }}">{{ _('Log in') }}</a>
            {% else %}
                {% if user_is_authenticated %}
                {% else %}
                <a href="{{ url('register') }}">{{ _('Sign up') }}</a>
                {% endif %}
            {% endif %}

            {% if find_team_link_disabled %}
            {% else %}
            <a href="{{ root_domain_uri }}/accounts/find/">{{ _('Find accounts') }}</a>
            <a href="{{ root_domain_uri }}/new/">{{ _('New organization') }}</a>
            {% endif %}
        </div>
    </div>
</div>

</pre>
#### landing_nav.html ####
<pre>
{% if not isolated_page %}
    {% if landing_page_navbar_message %}
    <div id="navbar-custom-message">
        {{ landing_page_navbar_message |safe }}
    </div>
    {% endif %}
{% endif %}

{% if not isolated_page %}
<nav class="top-menu">
    <div class="top-menu-container">
        <a class="top-menu-logo nav-zulip-logo" href="https://zulip.com" tabindex="1"></a>
        <div class='top-menu-items-group-1'>
            <div class='top-menu-item top-menu-tab'>
                <div class="top-menu-tab-unselect"></div>
                <input type="radio" name="top-menu-tabs" class="top-menu-tab-input" id="top-menu-tab-product" />
                <label for="top-menu-tab-product" class="nav-menu-label" tabindex="0">Product</label>
                <div class="top-menu-submenu">
                    <div class="top-menu-submenu-column">
                        <ul class="top-menu-submenu-list">
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com">Home</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/why-zulip/">Why Zulip</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/features/">Features</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/security/">Security</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/integrations/">Integrations</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/apps/">Apps</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/try-zulip/">Try Zulip</a></li>
                        </ul>
                    </div>
                    <div class="top-menu-submenu-column">
                        <ul class="top-menu-submenu-list">
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/self-hosting/">Self-hosting</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/help/getting-your-organization-started-with-zulip">Moving to Zulip</a></li>
                            <li class="top-menu-submenu-list-item"><a href="/api/">API</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://github.com/zulip/zulip" target="_blank" rel="noopener noreferrer">GitHub</a></li>
                        </ul>
                    </div>
                </div>
            </div>
            <div class='top-menu-item top-menu-tab'>
                <div class="top-menu-tab-unselect"></div>
                <input type="radio" name="top-menu-tabs" class="top-menu-tab-input" id="top-menu-tab-solutions" />
                <label for="top-menu-tab-solutions" class="nav-menu-label" tabindex="0">Solutions</label>
                <div class="top-menu-submenu">
                    <div class="top-menu-submenu-column">
                        <span class="top-menu-submenu-section">USE CASES</span>
                        <ul class="top-menu-submenu-list">
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/business/">Business</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/education/">Education</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/research/">Research</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/events/">Events and conferences</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/open-source/">Open source projects</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/communities/">Communities</a></li>
                        </ul>
                    </div>
                    <div class="top-menu-submenu-column">
                        <span class="top-menu-submenu-section">CUSTOMER STORIES</span>
                        <ul class="top-menu-submenu-list">
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/idrift/">Efficient distributed team management at iDrift AS</a></li>
                            <li class="top-menu-submenu-list-item"><a href="/case-studies/end-point/">Managing hundreds of projects at End Point Dev</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/tum/">Organized chat for 1000s of students at TUM</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/ucsd/">Communication hub across 6 continents at UCSD</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/lean/">Research collaboration at scale in the Lean mathematical community</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/asciidoctor/">Inclusive discussion in the open-source Asciidoctor community</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/rust/">Faster decision-making in the Rust language community</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/recurse-center/">Platform for a worldwide community since 2013 at Recurse Center</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/communities/">Open communities directory</a></li>
                        </ul>
                    </div>
                </div>
            </div>
            <div class='top-menu-item top-menu-tab'>
                <div class="top-menu-tab-unselect"></div>
                <input type="radio" name="top-menu-tabs" class="top-menu-tab-input" id="top-menu-tab-resources" />
                <label for="top-menu-tab-resources" class="nav-menu-label" tabindex="0">Resources</label>
                <div class="top-menu-submenu">
                    <div class="top-menu-submenu-column">
                        <span class="top-menu-submenu-section">FOR USERS</span>
                        <ul class="top-menu-submenu-list">
                            <li class="top-menu-submenu-list-item"><a href="/help/getting-started-with-zulip">Getting started</a></li>
                            <li class="top-menu-submenu-list-item"><a href="/help/">Help center</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/development-community/" target="_blank" rel="noopener noreferrer">Community chat</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.com/help/contact-support">Contact support</a></li>
                        </ul>
                    </div>
                    <div class="top-menu-submenu-column">
                        <span class="top-menu-submenu-section">FOR ADMINISTRATORS</span>
                        <ul class="top-menu-submenu-list">
                            <li class="top-menu-submenu-list-item"><a href="/help/getting-your-organization-started-with-zulip">Setting up your organization</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.readthedocs.io/en/stable/production/install.html">Installing a Zulip server</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://zulip.readthedocs.io/en/stable/production/upgrade-or-modify.html">Upgrading a Zulip server</a></li>
                            <li class="top-menu-submenu-list-item"><a href="https://github.com/zulip/zulip" target="_blank" rel="noopener noreferrer">GitHub</a></li>
                        </ul>
                    </div>
                </div>
            </div>
            <a class='top-menu-item' href="https://zulip.com/plans/">Pricing</a>
            <a class='top-menu-item' href="https://zulip.com/apps/">Download</a>
        </div>
        <div class='top-menu-item-spacer'></div>
        <div class='top-menu-items-group-2'>
            <a class='top-menu-item' href="/new/">New organization</a>
            {% if user_is_authenticated %}
            <div class='top-menu-item top-menu-tab'>
                <div class="top-menu-tab-unselect"></div>
                <input type="radio" name="top-menu-tabs" class="top-menu-tab-input" id="top-menu-tab-user" />
                <label class="top-menu-tab-user-label nav-menu-label" for="top-menu-tab-user" tabindex="0">
                    <img class="top-menu-tab-user-img" src="{{ realm_icon }}" />
                    <span>{{ realm_name }}</span>
                </label>
                <div class="top-menu-submenu singup-column">
                    <div class="top-menu-submenu-column">
                        <ul class="top-menu-submenu-list">
                            <li class="top-menu-submenu-list-item">
                                <a href="/">Go to app</a>
                            </li>
                            <div class="hidden">
                                <form id="logout_form" action="/accounts/logout/" method="POST">{{ csrf_input }}
                                </form>
                            </div>
                            <li class="top-menu-submenu-list-item">
                                <a class="logout_button">
                                Log out
                                </a>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
            {% else %}
            {% if login_link_disabled %}
            {% else %}
            <a class='top-menu-item' href="/login/">Log in</a>
            {% endif %}
            {% if register_link_disabled %}
            {% else %}
            <a class='top-menu-item' href="/register/">Sign up</a>
            {% endif %}
            {% endif %}
            {% if find_team_link_disabled %}
            {% else %}
            <a class='top-menu-item' href="/accounts/find/">Find accounts</a>
            {% endif %}
        </div>
    </div>
    <input type="radio" name="top-menu-tabs" class="top-menu-tab-input-unselect" id="top-menu-tab-close" checked />
    <div id='top-menu-submenu-backdrop' class="top-menu-submenu-backdrop"></div>
    <label class="top-menu-tab-label-unselect nav-menu-label" for="top-menu-tab-close" tabindex="0"></label>
</nav>
<details class="top-menu-mobile">
    <summary class="top-menu-mobile-summary">
        <a class="top-menu-logo nav-zulip-logo" href="https://zulip.com"></a>
    </summary>
    <div class="top-menu-mobile-items-group-1">
        <details>
            <summary class="top-menu-mobile-item-summary">Product</summary>
            <div class="top-menu-mobile-submenu">
                <ul class="top-menu-submenu-list">
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com">Home</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/why-zulip">Why Zulip</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/features/">Features</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/security/">Security</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/integrations/">Integrations</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/apps">Apps</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/try-zulip/">Try Zulip</a></li>
                </ul>
            </div>
            <div class="top-menu-mobile-submenu">
                <ul class="top-menu-submenu-list">
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/self-hosting/">Self-hosting</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/help/getting-your-organization-started-with-zulip">Moving to Zulip</a></li>
                    <li class="top-menu-submenu-list-item"><a href="/api/">API</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://github.com/zulip/zulip" target="_blank" rel="noopener noreferrer">GitHub</a></li>
                </ul>
            </div>
        </details>
        <details>
            <summary class="top-menu-mobile-item-summary">Solutions</summary>
            <div class="top-menu-mobile-submenu">
                <span class="top-menu-mobile-submenu-section">USE CASES</span>
                <ul class="top-menu-submenu-list">
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/business/">Business</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/education/">Education</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/research/">Research</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/events/">Events and conferences</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/open-source/">Open source projects</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/for/communities/">Communities</a></li>
                </ul>
                <span class="top-menu-mobile-submenu-section">CUSTOMER STORIES</span>
                <ul class="top-menu-submenu-list">
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/idrift/">Efficient distributed team management at iDrift AS</a></li>
                    <li class="top-menu-submenu-list-item"><a href="/case-studies/end-point/">Managing hundreds of projects at End Point Dev</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/tum/">Organized chat for 1000s of students at TUM</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/ucsd/">Communication hub across 6 continents at UCSD</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/lean/">Research collaboration at scale in the Lean mathematical community</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/asciidoctor/">Inclusive discussion in the open-source Asciidoctor community</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/rust/">Faster decision-making in the Rust language community</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/case-studies/recurse-center/">Platform for a worldwide community since 2013 at Recurse Center</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/communities/">Open communities directory</a></li>
                </ul>
            </div>
        </details>
        <details>
            <summary class="top-menu-mobile-item-summary">Resources</summary>
            <div class="top-menu-mobile-submenu">
                <span class="top-menu-mobile-submenu-section">FOR USERS</span>
                <ul class="top-menu-submenu-list">
                    <li class="top-menu-submenu-list-item"><a href="/help/getting-started-with-zulip">Getting started</a></li>
                    <li class="top-menu-submenu-list-item"><a href="/help">Help center</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/development-community/" target="_blank" rel="noopener noreferrer">Community chat</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.com/help/contact-support">Contact support</a></li>
                </ul>
                <span class="top-menu-mobile-submenu-section">FOR ADMINISTRATORS</span>
                <ul class="top-menu-submenu-list">
                    <li class="top-menu-submenu-list-item"><a href="/help/getting-your-organization-started-with-zulip">Setting up your organization</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.readthedocs.io/en/stable/production/install.html">Installing a Zulip server</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://zulip.readthedocs.io/en/stable/production/upgrade-or-modify.html">Upgrading a Zulip server</a></li>
                    <li class="top-menu-submenu-list-item"><a href="https://github.com/zulip/zulip" target="_blank" rel="noopener noreferrer">GitHub</a></li>
                </ul>
            </div>
        </details>
        <div class='top-menu-mobile-item'><a href="https://zulip.com/plans/">Pricing</a></div>
        <div class='top-menu-mobile-item'><a href="https://zulip.com/apps/">Download</a></div>
    </div>
    <div class="top-menu-mobile-items-group-2">
        <div class='top-menu-mobile-item'><a href="/new/">New organization</a></div>
        {% if user_is_authenticated %}
        <details>
            <summary class="top-menu-mobile-item-summary">
                <img class="top-menu-mobile-user-img"
                  src="{{ realm_icon }}" />
                {{ realm_name }}
            </summary>
            <div class="top-menu-mobile-submenu">
                <ul class="top-menu-submenu-list">
                    <li class="top-menu-submenu-list-item">
                        <a href="/">Go to app</a>
                    </li>
                    <div class="hidden">
                        <form id="logout_form" action="/accounts/logout/" method="POST">{{ csrf_input }}
                        </form>
                    </div>
                    <li class="top-menu-submenu-list-item">
                        <a class="logout_button">
                        Log out
                        </a>
                    </li>
                </ul>
            </div>
        </details>
        {% else %}
        {% if login_link_disabled %}
        {% else %}
        <div class='top-menu-mobile-item'><a href="/login/">Log in</a></div>
        {% endif %}
        {% if register_link_disabled %}
        {% else %}
        <div class='top-menu-mobile-item'><a href="/register/">Sign up</a></div>
        {% endif %}
        {% endif %}
        {% if find_team_link_disabled %}
        {% else %}
        <div class='top-menu-mobile-item'><a href="/accounts/find/">Find accounts</a></div>
        {% endif %}
    </div>
</details>
{% endif %}

</pre>
#### no_arrow_popover.hbs ####
<pre>
<div class="popover {{class}}">
    <div class="popover-inner">
        <div class="popover-title"></div>
        <div class="popover-content">
            <div></div>
        </div>
    </div>
</div>

</pre>
#### message_history_modal.hbs ####
<pre>
<div class="controls" id="message-history"></div>

</pre>
#### markdown_time_tooltip.hbs ####
<pre>
{{t 'Everyone sees this in their own time zone.' }}
<br/>
{{t 'Your time zone:' }} {{ tz_offset_str }}

</pre>
#### desktop_login.html ####
<pre>
{% extends "zerver/portico.html" %}
{% set entrypoint = "desktop-login" %}

{% block title %}
<title>{{ _("Finish desktop app login") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<div class="flex new-style">
    <div class="desktop-redirect-box">
        <h1>{% trans %}Finish desktop login{% endtrans %}</h1>

        <div class="white-box">
            <p class="copy-token-info">{% trans %}Use your web browser to finish logging in, then come back here to paste in your login token.{% endtrans %}</p>

            <form id="form" action="blob:">
                <span class="input-box">
                    <input id="token" placeholder="{% trans %}Paste token here{% endtrans %}" type="text"/>
                </span>
                <button id="submit" disabled>{% trans %}Finish{% endtrans %}</button>
            </form>

            <p id="bad-token" hidden>
                {% trans %}Incorrect token.{% endtrans %}
            </p>

            <p id="done" hidden>
                {% trans %}Token accepted.  Logging you in…{% endtrans %}
            </p>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### deactivated.html ####
<pre>
{% extends "zerver/portico_signup.html" %}

{% block title %}
<title>{{ _("Deactivated organization") }} | Zulip</title>
{% endblock %}

{% block customhead %}
{{ super() }}
<meta http-equiv="refresh" content="60;URL='/'" />
{% endblock %}

{% block portico_content %}

<div class="app portico-page">
    <div class="app-main portico-page-container center-block flex full-page account-creation new-style">
        <div class="inline-block">

            <div class="get-started">
                <h1>{{ _("Deactivated organization") }}</h1>
            </div>

            <div class="white-box deactivated-realm-container">
                <p>
                    {% trans %}
                    The organization you are trying to join, {{ deactivated_domain_name }}, has been deactivated.
                    {% endtrans %}
                    {% if deactivated_redirect %}
                        {% trans %}
                        It has moved to <a href="{{ deactivated_redirect }}">{{ deactivated_redirect }}</a>.
                        {% endtrans %}
                    {% endif %}
                    {% trans %}
                    Please contact <a href="mailto:{{ support_email }}">{{ support_email }}</a> to reactivate
                    this group.
                    {% endtrans %}
                </p>
            </div>

        </div>
    </div>
</div>

{% endblock %}

</pre>
#### portico-help.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block content %}
<div class="portico-container help">
    <div class="portico-wrap">
        {% include 'zerver/portico-header.html' %}
        <div class="app portico-page">
            <div class="app-main portico-page-container{% block hello_page_container %}{% endblock %}">
                {% block portico_content %}
                {% endblock %}
            </div>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### edited_notice.hbs ####
<pre>
{{#if msg/local_edit_timestamp}}
<div class="message_edit_notice auto-select" title="{{t 'Edited ({last_edit_timestr})' }}">
    {{t "SAVING" }}
</div>
{{else if moved}}
<div class="message_edit_notice auto-select" title="{{t 'Moved ({last_edit_timestr})' }}">
    {{t "MOVED" }}
</div>
{{else}}
<div class="message_edit_notice auto-select" title="{{t 'Edited ({last_edit_timestr})' }}">
    {{t "EDITED" }}
</div>
{{/if}}

</pre>
#### recent_topic_row.hbs ####
<pre>
<tr id="recent_conversation:{{conversation_key}}" class="{{#if unread_count}}unread_topic{{/if}} {{#if is_private}}private_conversation_row{{/if}}">
    <td class="recent_topic_stream">
        <div class="flex_container flex_container_pm">
            <div class="left_part recent_topics_focusable">
                {{#if is_private}}
                <span class="fa fa-envelope"></span>
                <a href="{{pm_url}}">Direct messages</a>
                {{else}}
                <span class="stream-privacy-{{stream_id}} stream-privacy filter-icon" style="color: {{stream_color}}">
                    {{> stream_privacy }}
                </span>
                <a href="{{topic_url}}">{{stream}}</a>
                {{/if}}
            </div>
            {{!-- For presence/group indicator --}}
            {{#if is_private}}
            <div class="right_part">
                <span class="pm_status_icon {{#unless is_group}}show-tooltip{{/unless}}" data-tippy-placement="top" data-user-ids-string="{{user_ids_string}}">
                    {{#if is_group}}
                    <span class="fa fa-group"></span>
                    {{else}}
                    <span class="{{user_circle_class}} user_circle"></span>
                    {{/if}}
                </span>
            </div>
            {{/if}}
        </div>
    </td>
    <td class="recent_topic_name">
        <div class="flex_container">
            <div class="left_part recent_topics_focusable line_clamp">
                {{#if is_private}}
                <a href="{{pm_url}}">{{{rendered_pm_with}}}</a>
                {{else}}
                <a href="{{topic_url}}">{{topic}}</a>
                {{/if}}
            </div>
            <div class="right_part">
                {{#if is_private}}
                <div class="recent_topic_actions">
                    <div class="recent_topics_focusable">
                        <span class="unread_count unread_count_pm {{#unless unread_count}}unread_hidden{{/unless}} tippy-zulip-tooltip on_hover_topic_read" data-user-ids-string="{{user_ids_string}}" data-tippy-content="{{t 'Mark as read' }}" role="button" tabindex="0" aria-label="{{t 'Mark as read' }}">{{unread_count}}</span>
                    </div>
                </div>
                <div class="recent_topic_actions dummy_action_button">
                    <div class="recent_topics_focusable">
                        {{!-- Invisible icon, used only for alignment of unread count. --}}
                        <i class="zulip-icon zulip-icon-mute on_hover_topic_unmute recipient_bar_icon"></i>
                    </div>
                </div>
                {{else}}
                <span class="unread_mention_info {{#unless mention_in_unread}}unread_hidden{{/unless}}">@</span>
                <div class="recent_topic_actions">
                    <div class="recent_topics_focusable hidden-for-spectators">
                        <span class="unread_count {{#unless unread_count}}unread_hidden{{/unless}} tippy-zulip-tooltip on_hover_topic_read" data-stream-id="{{stream_id}}" data-topic-name="{{topic}}" data-tippy-content="{{t 'Mark as read' }}" role="button" tabindex="0" aria-label="{{t 'Mark as read' }}">{{unread_count}}</span>
                    </div>
                </div>
                <div class="recent_topic_actions">
                    <div class="recent_topics_focusable hidden-for-spectators">
                        {{#if topic_muted}}
                        <i class="zulip-icon zulip-icon-mute on_hover_topic_unmute recipient_bar_icon tippy-zulip-tooltip" data-stream-id="{{stream_id}}" data-topic-name="{{topic}}" data-tippy-content="{{t 'Unmute topic' }}" role="button" tabindex="0" aria-label="{{t 'Unmute topic' }}"></i>
                        {{else}}
                        <i class="zulip-icon zulip-icon-mute on_hover_topic_mute recipient_bar_icon tippy-zulip-tooltip" data-stream-id="{{stream_id}}" data-topic-name="{{topic}}" data-tippy-content="{{t 'Mute topic' }}" role="button" tabindex="0" aria-label="{{t 'Mute topic' }}"></i>
                        {{/if}}
                    </div>
                </div>
                {{/if}}
            </div>
        </div>
    </td>
    <td class='recent_topic_users'>
        <ul class="recent_topics_participants">
            {{#if other_senders_count}}
            <li class="recent_topics_participant_item tippy-zulip-tooltip" data-tooltip-template-id="recent_topics_participant_overflow_tooltip:{{conversation_key}}">
                <span class="recent_topics_participant_overflow">+{{other_senders_count}}</span>
            </li>
            <template id="recent_topics_participant_overflow_tooltip:{{conversation_key}}">{{{other_sender_names_html}}}</template>
            {{/if}}
            {{#each senders}}
                {{#if this.is_muted}}
                <li class="recent_topics_participant_item participant_profile tippy-zulip-tooltip" data-tippy-content="{{t 'Muted user'}}" data-user-id="{{this.user_id}}">
                    <span><i class="fa fa-user recent_topics_participant_overflow"></i></span>
                </li>
                {{else}}
                <li class="recent_topics_participant_item participant_profile tippy-zulip-tooltip" data-tippy-content="{{this.full_name}}" data-user-id="{{this.user_id}}">
                    <img src="{{this.avatar_url_small}}" class="recent_topics_participant_avatar" />
                </li>
                {{/if}}
            {{/each}}
        </ul>
    </td>
    <td class="recent_topic_timestamp">
        <div class="last_msg_time tippy-zulip-tooltip" data-tippy-content="{{this.full_last_msg_date_time}}">
            <a href="{{last_msg_url}}">{{ last_msg_time }}</a>
        </div>
    </td>
</tr>

</pre>
#### desktop_redirect.html ####
<pre>
{% extends "zerver/portico.html" %}
{% set entrypoint = "desktop-redirect" %}

{% block title %}
<title>{{ _("Log in to desktop app") }} | Zulip</title>
{% endblock %}

{% block content %}
<div class="flex new-style">
    <div class="desktop-redirect-box white-box">
        <img class="avatar desktop-redirect-image" src="{{ realm_icon_url }}" alt=""/><br />
        <p class="copy-token-info">{% trans %}Copy this login token and return to your Zulip app to finish logging in:{% endtrans %}</p>
        <p>
            <span class="input-box">
                <input id="desktop-data" value="{{ desktop_data }}" type="text" readonly />
            </span>
            <button id="copy" tabindex="0" data-clipboard-target="#desktop-data">{% trans %}Copy{% endtrans %}</button>
        </p>
        <p>{% trans %}You may then close this window.{% endtrans %}</p>
        <p><a href="{{ browser_url }}">{% trans %}Or, continue in your browser.{% endtrans %}</a></p>
    </div>
</div>
{% endblock %}

</pre>
#### close_window.html ####
<pre>
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
        <title>{{ _("Video call ended") }} | Zulip</title>
        <script>
            window.close();
            // Why doesn’t this work in Firefox?  See
            // https://bugzilla.mozilla.org/show_bug.cgi?id=1353466
        </script>
    </head>
    <body>
        <p>{{ _("You may now close this window.") }}</p>
    </body>
</html>

</pre>
#### help_link_widget.hbs ####
<pre>
<a class="help_link_widget" href="{{ link }}" target="_blank" rel="noopener noreferrer">
    <i class="fa fa-question-circle-o" aria-hidden="true"></i>
</a>

</pre>
#### reset_done.html ####
<pre>
{% extends "zerver/portico_signup.html" %}

{% block title %}
<title>{{ _(" New password successfully set") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<div class="app portico-page">
    <div class="app-main portico-page-container center-block flex full-page account-creation new-style">
        <div class="inline-block">

            <div class="get-started">
                <h1>{{ _("You've set a new password!") }}</h1>
            </div>

            <div class="white-box">
                <p>{% trans login_url=url('login') %}Please <a href="{{ login_url }}">log in</a> with your new password.{% endtrans %}</p>
            </div>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### presence_rows.hbs ####
<pre>
{{#each presence_rows}}
    {{> presence_row}}
{{/each}}

</pre>
#### me_message.hbs ####
<pre>
<span class="message_sender no-select is_me_message">
    <span class="sender_info_hover">
        <span>
            {{> message_avatar}}
        </span>
    </span>

    <span class="sender-status">
        <span class="sender_info_hover sender_name-in-status auto-select" role="button" tabindex="0">
            <span class="view_user_card_tooltip">
                {{msg/sender_full_name}}
            </span>
        </span>
        {{#if sender_is_bot}}
        <i class="zulip-icon zulip-icon-bot" aria-label="{{t 'Bot' }}"></i>
        {{/if}}

        <span class="rendered_markdown status-message auto-select">{{rendered_markdown status_message}}</span>

        {{#if edited_status_msg}}
        {{> edited_notice}}
        {{/if}}
    </span>
</span>

</pre>
#### all_messages_sidebar_actions.hbs ####
<pre>
{{! Contents of the "all messages sidebar" popup }}
<ul class="nav nav-list">
    <li>
        {{! tabindex="0" Makes anchor tag focusable. Needed for keyboard support. }}
        <a tabindex="0" id="mark_all_messages_as_read">
            <i class="fa fa-book" aria-hidden="true"></i>
            {{t "Mark all messages as read" }}
        </a>
    </li>
</ul>

</pre>
#### giphy_picker_mobile.hbs ####
<pre>
<div class='popover-flex'>
    {{> giphy_picker }}
</div>

</pre>
#### reset_emailed.html ####
<pre>
{% extends "zerver/portico_signup.html" %}

{% block title %}
<title>{{ _("Password reset email sent") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<div class="app portico-page">
    <div class="app-main portico-page-container center-block flex full-page account-creation new-style">
        <div class="inline-block">

            <div class="get-started">
                <h1>{{ _("Password reset sent!") }}</h1>
            </div>

            <div class="white-box">
                <p>{{ _('Check your email in a few minutes to finish the process.') }}</p>
                {% include 'zerver/dev_env_email_access_details.html' %}
                {% include 'zerver/include/back_to_login_component.html' %}
            </div>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### recipient_row.hbs ####
<pre>
{{#if is_stream}}
<div class="message_header message_header_stream right_part">
    <div class="message-header-wrapper">
        <div class="message-header-contents">
            {{! stream link }}
            <a class="message_label_clickable narrows_by_recipient stream_label {{color_class}}"
              style="background: {{background_color}}; border-left-color: {{background_color}};"
              href="{{stream_url}}"
              title="{{t 'Narrow to stream "{display_recipient}"' }}">
                {{~! Icons for invite-only/web-public streams ~}}
                {{~#if invite_only ~}}
                    <i class="fa fa-lock recipient-row-stream-icon" title="{{t 'This is a private stream' }}" aria-label="{{t 'This is a private stream' }}"></i>
                {{/if}}

                {{~#if is_web_public ~}}
                    <i class="zulip-icon zulip-icon-globe recipient-row-stream-icon" title="{{t 'This is a web-public stream' }}" aria-label="{{t 'This is a web-public stream' }}"></i>
                {{/if}}

                {{~! Recipient (e.g. stream/topic or topic) ~}}
                {{~display_recipient~}}
            </a>

            {{! hidden narrow icon for copy-pasting }}
            <span class="copy-paste-text">&gt;</span>

            {{! topic stuff }}
            <span class="stream_topic">
                {{! topic link }}
                <a class="message_label_clickable narrows_by_topic"
                  href="{{topic_url}}"
                  title="{{t 'Narrow to stream "{display_recipient}", topic "{topic}"' }}">
                    {{#if use_match_properties}}
                        {{{match_topic}}}
                    {{else}}
                        {{topic}}
                    {{/if}}
                </a>
            </span>
            <span class="recipient_bar_controls no-select">
                <span class="topic_edit hidden-for-spectators">
                    <span class="topic_edit_form"></span>
                </span>

                {{! exterior links (e.g. to a trac ticket) }}
                {{#each topic_links}}
                    <a href="{{this.url}}" target="_blank" rel="noopener noreferrer" class="no-underline">
                        <i class="fa fa-external-link-square recipient_bar_icon" data-tippy-content="Open {{this.text}}" aria-label="{{t 'External link' }}"></i>
                    </a>
                {{/each}}

                {{! edit topic pencil icon }}
                {{#if always_visible_topic_edit}}
                    <i class="fa fa-pencil always_visible_topic_edit recipient_bar_icon hidden-for-spectators" data-tippy-content="{{t 'Edit topic'}}" role="button" tabindex="0" aria-label="{{t 'Edit topic' }}"></i>
                {{else if on_hover_topic_edit}}
                    <i class="fa fa-pencil on_hover_topic_edit recipient_bar_icon hidden-for-spectators" data-tippy-content="{{t 'Edit topic'}}" role="button" tabindex="0" aria-label="{{t 'Edit topic' }}"></i>
                {{/if}}

                {{#if user_can_resolve_topic}}
                    {{#if topic_is_resolved}}
                        <i class="fa fa-check on_hover_topic_unresolve recipient_bar_icon hidden-for-spectators" data-topic-name="{{topic}}" data-tippy-content="{{t 'Mark as unresolved' }}" role="button" tabindex="0" aria-label="{{t 'Mark as unresolved' }}"></i>
                    {{else}}
                        <i class="fa fa-check on_hover_topic_resolve recipient_bar_icon hidden-for-spectators" data-topic-name="{{topic}}" data-tippy-content="{{t 'Mark as resolved' }}" role="button" tabindex="0" aria-label="{{t 'Mark as resolved' }}"></i>
                    {{/if}}
                {{/if}}

                {{#if topic_muted}}
                    <i class="zulip-icon zulip-icon-mute on_hover_topic_unmute recipient_bar_icon" data-stream-id="{{stream_id}}" data-topic-name="{{topic}}" data-tooltip-template-id="topic-unmute-tooltip-template" role="button" tabindex="0" aria-label="{{t 'Unmute topic' }}"></i>
                    <template id="topic-unmute-tooltip-template">
                        {{t "Unmute topic" }}
                        {{tooltip_hotkey_hints "M"}}
                    </template>
                {{else}}
                    <i class="zulip-icon zulip-icon-mute on_hover_topic_mute recipient_bar_icon hidden-for-spectators" data-stream-id="{{stream_id}}" data-topic-name="{{topic}}" data-tooltip-template-id="topic-mute-tooltip-template" role="button" tabindex="0" aria-label="{{t 'Mute topic' }}"></i>
                    <template id="topic-mute-tooltip-template">
                        {{t "Mute topic" }}
                        {{tooltip_hotkey_hints "M"}}
                    </template>
                {{/if}}
            </span>
            <span class="recipient_row_date {{#if date_unchanged}}recipient_row_date_unchanged{{/if}}">{{{date}}}</span>
        </div>
    </div>
</div>
{{else}}
<div class="message_header message_header_private_message dark_background">
    <div class="message-header-wrapper">
        <div class="message-header-contents">
            <a class="message_label_clickable narrows_by_recipient stream_label"
              href="{{pm_with_url}}"
              title="{{t 'Narrow to your direct messages with {display_reply_to}' }}">
                {{t "You and {display_reply_to}" }}
            </a>

            <span class="recipient_row_date {{#if date_unchanged}}recipient_row_date_unchanged{{/if}}">{{{date}}}</span>
        </div>
    </div>
</div>
{{/if}}

</pre>
#### message_group.hbs ####
<pre>
{{! Client-side Handlebars template for rendering messages. }}

{{#each message_groups}}
    {{#with this}}
        {{#if bookend_top}}
        {{> bookend}}
        {{/if}}

        <div class="recipient_row" id="{{message_group_id}}">
            {{> recipient_row use_match_properties=../use_match_properties}}
            {{#each message_containers}}
                {{#with this}}
                {{> single_message use_match_properties=../../use_match_properties table_name=../../table_name}}
                {{/with}}
            {{/each}}
        </div>
    {{/with}}
{{/each}}

</pre>
#### user_profile_modal.hbs ####
<pre>
<div class="micromodal" id="user-profile-modal" data-user-id="{{user_id}}" aria-hidden="true">
    <div class="modal__overlay" tabindex="-1">
        <div class="modal__container new-style" role="dialog" aria-modal="true" aria-labelledby="dialog_title">
            <div class="modal__header">
                <div class="tippy-zulip-tooltip" data-tippy-content="{{last_seen}}">
                    <span class="{{user_circle_class}} user_circle user_profile_presence"></span>
                </div>
                <h1 class="modal__title user_profile_name_heading" id="name">
                    <span class="user_profile_name">{{full_name}}</span>
                    {{#if is_bot}}
                    <i class="zulip-icon zulip-icon-bot" aria-hidden="true"></i>
                    {{/if}}
                    {{#if is_me}}
                    <a href="/#settings/profile" class="user_profile_edit_button">
                        <i class="fa fa-edit" id="user_profile_edit_button_icon" aria-hidden="true"></i>
                    </a>
                    {{/if}}
                </h1>
                <button class="modal__close" aria-label="{{t 'Close modal' }}" data-micromodal-close></button>
            </div>
            <div id="tab-toggle" class="center"></div>
            <main class="modal__body" id="body" data-simplebar data-simplebar-auto-hide="false">
                <div class="tab-data">
                    <div class="tabcontent active" id="profile-tab">
                        <div class="top">
                            <div class="col-wrap col-left">
                                <div id="default-section">
                                    {{#if email}}
                                    <div id="email" class="default-field">
                                        <div class="name">{{t "Email" }}</div>
                                        <div class="value">{{email}}</div>
                                    </div>
                                    {{/if}}
                                    <div id="user-id" class="default-field">
                                        <div class="name">{{t "User ID" }}</div>
                                        <div class="value">{{user_id}}</div>
                                    </div>
                                    <div id="user-type" class="default-field">
                                        <div class="name">{{t "Role" }}</div>
                                        {{#if is_bot}}
                                            {{#if is_system_bot}}
                                            <div class="value">{{t "System bot" }}</div>
                                            {{else}}
                                            <div class="value">{{t "Bot" }}</div>
                                            {{/if}}
                                        {{else}}
                                            <div class="value">{{user_type}}</div>
                                        {{/if}}
                                    </div>
                                    <div id="date-joined" class="default-field">
                                        <div class="name">{{t "Joined" }}</div>
                                        <div class="value">{{date_joined}}</div>
                                    </div>
                                    {{#if user_time}}
                                    <div class="default-field">
                                        <div class="name">{{t "Local time" }}</div>
                                        <div class="value">{{user_time}}</div>
                                    </div>
                                    {{/if}}
                                </div>
                            </div>
                            <div class="col-wrap col-right">
                                <div id="avatar" {{#if user_is_guest}} class="guest-avatar" {{/if}}
                                  style="background-image: url('{{user_avatar}}');">
                                </div>
                            </div>
                        </div>
                        <div class="bottom">
                            <div id="content">
                                {{#if is_bot}}
                                    <div class="field-section">
                                        <div class="name">{{t "Bot type" }}</div>
                                        <div class="bot_info_value">{{bot_type}}</div>
                                    </div>
                                    {{#if bot_owner}}
                                    <div class="field-section bot_owner_user_field" data-field-id="{{bot_owner.user_id}}">
                                        <div class="name">{{t "Owner" }}</div>
                                        <div class="pill-container not-editable">
                                            <div class="input" contenteditable="false" style="display: none;"></div>
                                        </div>
                                    </div>
                                    {{/if}}
                                {{else}}
                                    {{> user_custom_profile_fields profile_fields=profile_data}}
                                {{/if}}
                            </div>
                        </div>
                    </div>

                    <div class="tabcontent" id="user-profile-streams-tab">
                        <div class="stream-list-top-section">
                            <div class="header-section">
                                <h3 class="stream-list-header">{{t 'Subscribed streams' }}</h3>
                            </div>
                            <input type="text" class="stream-search modal_text_input" placeholder="{{t 'Filter streams' }}" />
                            <button type="button" class="clear_search_button" id="clear_stream_search">
                                <i class="fa fa-remove" aria-hidden="true"></i>
                            </button>
                        </div>
                        <div class="alert stream_list_info"></div>
                        <div class="subscription-stream-list">
                            <table class="user-stream-list" data-empty="{{t 'No stream subscriptions.'}}"></table>
                        </div>
                    </div>

                    <div class="tabcontent" id="user-profile-groups-tab">
                        <div class="subscription-group-list">
                            <table class="user-group-list" data-empty="{{t 'No user group subscriptions.'}}"></table>
                        </div>
                    </div>
                </div>
            </main>
        </div>
    </div>
</div>

</pre>
#### playground_links_popover_content.hbs ####
<pre>
{{! Contents of "view code in playground" popover for code blocks}}
<ul class="nav nav-list">
    {{#each playground_info}}
        <li>
            <a href="{{this/playground_url}}" target="_blank" rel="noopener noreferrer" class="popover_playground_link">
                {{t "View in {name}" }}
            </a>
        </li>
    {{/each}}
</ul>


</pre>
#### accounts_accept_terms.html ####
<pre>
{% extends "zerver/portico_signup.html" %}

{% block title %}
<title>{{ _("Accept the Terms of Service") }} | Zulip</title>
{% endblock %}

{#
Allow the user to accept a TOS, creating an email record of that fact.
Users only hit this page if they are coming from a migration or other update of the TOS;
the registration flow has its own (nearly identical) copy of the fields below in register.html.
#}

{% block portico_content %}

<div class="account-accept-terms-page flex full-page">
    <div class="center-block new-style">
        <div class="pitch">
            <h1 class="get-started">{{ _("Accept the Terms of Service") }}</h1>
        </div>

        <div class="white-box">
            <form method="post" id="registration" action="{{ url('accept_terms') }}">
                {{ csrf_input }}
                <div id="registration-email">
                    <label for="id_email">{{ _("Email") }}</label>
                    <div class="controls fakecontrol">
                        <p>{{ email }}</p>
                    </div>
                </div>

                {% if first_time_terms_of_service_message_template %}
                {% include first_time_terms_of_service_message_template %}
                {% elif terms_of_service_message %}
                <div class="description">
                    <p>{{ terms_of_service_message |safe }}</p>
                </div>
                {% endif %}

                <div class="input-group terms-of-service">
                    {#
                    This is somewhat subtle.
                    Checkboxes have a name and value, and when the checkbox is ticked, the form posts
                    with name=value. If the checkbox is unticked, the field just isn't present at all.

                    This is distinct from 'checked', which determines whether the checkbox appears
                    at all. (So, it's not symmetric to the code above.)
                    #}
                    <label for="id_terms" class="inline-block checkbox">
                        <input id="id_terms" class="required" type="checkbox" name="terms"
                          {% if form.terms.value() %}checked="checked"{% endif %} />
                        <span></span>
                        {% trans %}I agree to the <a href="{{ root_domain_uri }}/policies/terms" target="_blank" rel="noopener noreferrer">Terms of Service</a>.{% endtrans %}
                    </label>
                    {% if form.terms.errors %}
                        {% for error in form.terms.errors %}
                        <p class="help-inline text-error">{{ error }}</p>
                        {% endfor %}
                    {% endif %}
                </div>
                <div class="controls">
                    <button id="accept_tos_button" type="submit">{{ _('Accept') }}</button>
                    <input type="hidden" name="next" value="{{ next }}" />
                </div>
            </form>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### status_emoji_selector.hbs ####
<pre>
{{#if selected_emoji}}
    {{#if selected_emoji.emoji_alt_code}}
        <div class="emoji_alt_code">&nbsp;:{{selected_emoji.emoji_name}}:</div>
    {{else if selected_emoji.url}}
        <img src="{{selected_emoji.url}}" class="emoji selected-emoji" />
    {{else}}
        <div class="emoji selected-emoji emoji-{{selected_emoji.emoji_code}}"></div>
    {{/if}}
{{else}}
    <a type="button" class="smiley-icon show fa fa-smile-o"></a>
{{/if}}

</pre>
#### starred_messages_sidebar_actions.hbs ####
<pre>
{{! Contents of the "starred messages sidebar" popup }}
<ul class="nav nav-list">
    {{! tabindex="0" Makes anchor tag focusable. Needed for keyboard support. }}
    {{#if show_unstar_all_button}}
    <li>
        <a tabindex="0" id="unstar_all_messages">
            <i class="fa fa-star-o" aria-hidden="true"></i>
            {{t "Unstar all messages" }}
        </a>
    </li>
    {{/if}}
    <li>
        <a tabindex="0" id="toggle_display_starred_msg_count">
            {{#if starred_message_counts}}
                <i class="fa fa-eye-slash" aria-hidden="true"></i>
                {{t "Hide starred message count" }}
            {{else}}
                <i class="fa fa-eye" aria-hidden="true"></i>
                {{t "Show starred message count" }}
            {{/if}}
        </a>
    </li>
</ul>

</pre>
#### invitation_failed_error.hbs ####
<pre>
<p id="invitation_error_message">{{ error_message }}</p>
{{#if daily_limit_reached}}
    {{#tr}}
        Please <z-link-support>contact support</z-link-support> for an exception or <z-link-invite-help>add users with a reusable invite link</z-link-invite-help>.
        {{#*inline "z-link-support"}}<a href="https://zulip.com/help/contact-support">{{> @partial-block}}</a>{{/inline}}
        {{#*inline "z-link-invite-help"}}<a href="https://zulip.com/help/invite-new-users#create-an-invitation-link">{{> @partial-block}}</a>{{/inline}}
    {{/tr}}
{{/if}}
<ul>
    {{#each error_list}}
        <li>{{this}}</li>
    {{/each}}
</ul>
{{#if is_invitee_deactivated}}
    {{#if is_admin}}
    <p id="invitation_admin_message">
        {{#tr}}
            You can reactivate deactivated users from <z-link>organization settings</z-link>.
            {{#*inline "z-link"}}<a href="#organization/deactivated-users-admin">{{> @partial-block}}</a>{{/inline}}
        {{/tr}}
    </p>
    {{else}}
    <p id="invitation_non_admin_message">{{t "Organization administrators can reactivate deactivated users." }}</p>
    {{/if}}
{{/if}}
{{#if license_limit_reached}}
    {{#if has_billing_access}}
        {{#tr}}
            To invite users, please <z-link-billing>increase the number of licenses</z-link-billing> or <z-link-help-page>deactivate inactive users</z-link-help-page>.
            {{#*inline "z-link-billing"}}<a href="/billing/#settings">{{> @partial-block}}</a>{{/inline}}
            {{#*inline "z-link-help-page"}}<a href="/help/deactivate-or-reactivate-a-user">{{> @partial-block}}</a>{{/inline}}
        {{/tr}}
    {{else}}
        {{#tr}}
            Please ask a billing administrator to <z-link-billing>increase the number of licenses</z-link-billing> or <z-link-help-page>deactivate inactive users</z-link-help-page>, and try again.
            {{#*inline "z-link-billing"}}<a href="/billing/#settings">{{> @partial-block}}</a>{{/inline}}
            {{#*inline "z-link-help-page"}}<a href="/help/deactivate-or-reactivate-a-user">{{> @partial-block}}</a>{{/inline}}
        {{/tr}}
    {{/if}}
{{/if}}

</pre>
#### insecure_desktop_app.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Update required") }} | Zulip</title>
{% endblock %}

{% block content %}

<div class="error_page">
    <div class="container">
        <div class="row-fluid">
            <img src="{{ static('images/errors/400art.svg') }}" alt=""/>
            <div class="errorbox config-error">
                <div class="errorcontent">
                    <h1 class="lead">{{ _('Update required') }}</h1>
                    <p>
                        {% trans %}
                        You are using old version of the Zulip desktop
                        app that is no longer supported.
                        {% endtrans %}
                    </p>

                    {% if auto_update_broken %}
                    <p>
                        {% trans %}
                        The auto-update feature in this old version of
                        Zulip desktop app no longer works.
                        {% endtrans %}
                    </p>
                    {% endif %}

                    <p>
                        <a href="https://zulip.com/apps/" target="_blank" rel="noopener noreferrer">
                            {{ _("Download the latest release.") }}
                        </a>
                    </p>
                </div>

            </div>
        </div>
    </div>
</div>

{% endblock %}

</pre>
#### message_controls.hbs ####
<pre>
<div class="message_controls{{#status_message}} sender-status-controls{{/status_message}} no-select">
    {{#if msg/sent_by_me}}
    <div class="edit_content message_control_button" data-tooltip-template-id="view-source-tooltip-template"></div>
    <template id="edit-content-tooltip-template">
        {{t "Edit message" }}
        {{tooltip_hotkey_hints "E"}}
    </template>
    <template id="move-message-tooltip-template">
        {{t "Move message" }}
        {{tooltip_hotkey_hints "M"}}
    </template>
    <template id="view-source-tooltip-template">
        {{t "View message source" }}
        {{tooltip_hotkey_hints "E"}}
    </template>
    {{/if}}

    {{#unless msg/sent_by_me}}
    <div class="reaction_button message_control_button" data-tooltip-template-id="add-emoji-tooltip-template">
        <i class="fa fa-smile-o" aria-label="{{t 'Add emoji reaction' }} (:)" role="button" aria-haspopup="true" tabindex="0"></i>
    </div>
    <template id="add-emoji-tooltip-template">
        {{t "Add emoji reaction" }}
        {{tooltip_hotkey_hints ":"}}
    </template>
    {{/unless}}

    {{#unless msg/locally_echoed}}
    <div class="actions_hover message_control_button" data-tooltip-template-id="message-actions-tooltip-template" >
        <i class="zulip-icon zulip-icon-ellipsis-v-solid" role="button" aria-haspopup="true" tabindex="0" aria-label="{{t 'Message actions' }}"></i>
    </div>
    <template id="message-actions-tooltip-template">
        {{t "Message actions" }}
        {{tooltip_hotkey_hints "I"}}
    </template>
    {{/unless}}

    <div class="message_failed {{#unless msg.failed_request}}hide{{/unless}}">
        <div class="message_control_button failed_message_action" data-tippy-content="{{t 'Retry' }}">
            <i class="fa fa-refresh refresh-failed-message" aria-label="{{t 'Retry' }}" role="button" tabindex="0"></i>
        </div>

        <div class="message_control_button failed_message_action" data-tippy-content="{{t 'Cancel' }}">
            <i class="fa fa-times-circle remove-failed-message" aria-label="{{t 'Cancel' }}" role="button" tabindex="0"></i>
        </div>
    </div>

    {{#unless msg/locally_echoed}}
    <div class="star_container message_control_button {{#if msg/starred}}{{else}}empty-star{{/if}}" data-tooltip-template-id="{{#if msg/starred}}unstar{{else}}star{{/if}}-message-tooltip-template">
        <i role="button" tabindex="0" class="star fa {{#if msg/starred}}fa-star{{else}}fa-star-o{{/if}}"></i>
    </div>
    <template id="star-message-tooltip-template">
        <span class="starred-status">{{t "Star this message" }}</span>
        {{tooltip_hotkey_hints "Ctrl" "S"}}
    </template>
    <template id="unstar-message-tooltip-template">
        <span class="starred-status">{{t "Unstar this message" }}</span>
        {{tooltip_hotkey_hints "Ctrl" "S"}}
    </template>
    {{/unless}}

</div>

</pre>
#### digest_base.html ####
<pre>
{% extends "zerver/base.html" %}
{% set entrypoint = "digest" %}

{% block title %}
<title>{{ _("Digest") }} | Zulip</title>
{% endblock %}

{% block content %}
<body>
    <div class="portico-wrap">
        {% include 'zerver/portico-header.html' %}
    </div>
    <div class="digest-container">
        <div class="digest-email-container">
            <div class="portico-page digest-page-title">
                <h1> Zulip digest </h1>
            </div>
            <div class="digest-email-html">
                {% include 'zerver/emails/compiled/digest.html' %}
                <img id="digest-footer" src="{{ static('images/emails/footer.png') }}"/>
            </div>
            <br />
            <br />
            <h2 class="digest-page-title">Plain text version</h2>
            <pre>{% include 'zerver/emails/digest.txt' %}</pre>
            <div class="digest-address-link"> {{physical_address}}</div>
        </div>
        {% include 'zerver/footer.html' %}
    </div>
</body>
{% endblock %}

</pre>
#### mobile_message_buttons_popover_content.hbs ####
<pre>
<ul class="nav nav-list">
    <li>
        <a class="compose_mobile_stream_button">
            <i class="fa fa-bullhorn" aria-hidden="true"></i>
            {{#if is_in_private_narrow }}
            {{t "New stream message" }}
            {{else}}
            {{t "New topic" }}
            {{/if}}
        </a>
    </li>
    <li>
        <a class="compose_mobile_private_button">
            <i class="fa fa-envelope" aria-hidden="true"></i>
            {{#if is_in_private_narrow }}
            {{t "New direct message" }}
            {{else}}
            {{t "New direct message" }}
            {{/if}}
        </a>
    </li>
</ul>

</pre>
#### hotspot_icon.hbs ####
<pre>
<div class="hotspot-icon" id="hotspot_{{name}}_icon">
    <span class="dot"></span>
    <span class="pulse"></span>
    <div class="bounce"><span class="bounce-icon">?</span></div>
</div>

</pre>
#### filter_topics.hbs ####
<pre>
<div class="input-append topic_search_section filter-topics">
    <input class="topic-list-filter home-page-input" id="filter-topic-input" type="text" autocomplete="off" placeholder="{{t 'Filter topics'}}" />
    <button type="button" class="btn clear_search_button" id="clear_search_topic_button">
        <i class="fa fa-remove" aria-hidden="true"></i>
    </button>
</div>

</pre>
#### actions_popover_content.hbs ####
<pre>
{{! Contents of the "message actions" popup }}
<ul class="nav nav-list actions_popover">
    {{#if should_display_quote_and_reply}}
    <li>
        <a class="respond_button" data-message-id="{{message_id}}" tabindex="0">
            <i class="fa fa-reply" aria-hidden="true"></i> {{t "Quote and reply or forward" }}
            <span class="hotkey-hint">(>)</span>
        </a>
    </li>
    <hr />
    {{/if}}

    {{#if editability_menu_item}}
    <li>
        <a class="popover_edit_message" data-message-id="{{message_id}}" tabindex="0">
            <i class="fa fa-pencil" aria-hidden="true"></i> {{editability_menu_item}}
            <span class="hotkey-hint">(e)</span>
        </a>
    </li>
    {{/if}}

    {{#if move_message_menu_item}}
    <li>
        <a class="popover_move_message" data-message-id="{{message_id}}" tabindex="0">
            <i class="fa fa-arrows" aria-hidden="true"></i> {{move_message_menu_item}}
            <span class="hotkey-hint">(m)</span>
        </a>
    </li>
    {{/if}}

    {{#if should_display_delete_option}}
    <li>
        <a class="delete_message" data-message-id="{{message_id}}" tabindex="0">
            <i class="fa fa-times" aria-hidden="true"></i>
            {{t "Delete message" }}
        </a>
    </li>
    {{/if}}

    {{#if (or editability_menu_item move_message_menu_item should_display_delete_option)}}
    <hr />
    {{/if}}

    {{#if should_display_add_reaction_option}}
    <li>
        <a class="reaction_button" data-message-id="{{message_id}}" tabindex="0">
            <i class="fa fa-smile-o" aria-hidden="true"></i>
            {{t "Add emoji reaction" }}
        </a>
    </li>
    <hr />
    {{/if}}

    {{#if should_display_mark_as_unread}}
        <li>
            <a class="mark_as_unread" data-message-id="{{message_id}}" tabindex="0">
                <span class="unread_count">1</span>
                {{t "Mark as unread from here" }}
                <span class="hotkey-hint">(U)</span>
            </a>
        </li>
    {{/if}}

    {{#if should_display_reminder_option}}
    <li>
        <a class='reminder_button' data-message-id="{{message_id}}" tabindex="0">
            <i class="fa fa-bell" aria-hidden="true"></i> {{t "Remind me about this" }}
        </a>
    </li>
    {{/if}}

    {{#if should_display_hide_option}}
    <li>
        <a class="rehide_muted_user_message" data-message-id="{{message_id}}" tabindex="0">
            <i class="fa fa-eye-slash" aria-hidden="true"></i>
            {{t "Hide muted message again" }}
        </a>
    </li>
    {{/if}}

    {{#if should_display_collapse}}
    <li>
        <a class="popover_toggle_collapse" data-message-id="{{message_id}}" tabindex="0">
            <i class="fa fa-minus" aria-hidden="true"></i>
            {{t "Collapse message" }} <span class="hotkey-hint">(–)</span>
        </a>
    </li>
    {{/if}}

    {{#if should_display_uncollapse}}
    <li>
        <a class="popover_toggle_collapse" data-message-id="{{message_id}}" tabindex="0">
            <i class="fa fa-plus" aria-hidden="true"></i>
            {{t "Expand message" }} <span class="hotkey-hint">(–)</span>
        </a>
    </li>
    {{/if}}

    {{#if (or should_display_mark_as_unread should_display_reminder_option should_display_hide_option should_display_collapse should_display_uncollapse)}}
    <hr />
    {{/if}}

    {{#if view_source_menu_item}}
    <li>
        <a class="popover_view_source" data-message-id="{{message_id}}" tabindex="0">
            <i class="fa fa-file-code-o" aria-hidden="true"></i> {{view_source_menu_item}}
            <span class="hotkey-hint">(e)</span>
        </a>
    </li>
    {{/if}}

    {{#if should_display_edit_history_option}}
    <li>
        <a class="view_edit_history" data-message-id="{{message_id}}" tabindex="0">
            <i class="fa fa-clock-o" aria-hidden="true"></i>
            {{t "View edit history" }}
        </a>
    </li>
    {{/if}}

    {{#if should_display_read_receipts_option}}
    <li>
        <a class="view_read_receipts" data-message-id="{{message_id}}" tabindex="0">
            <i class="zulip-icon zulip-icon-readreceipts" aria-label="{{t 'View read receipts' }}"></i> {{t "View read receipts" }}
        </a>
    </li>
    {{/if}}

    <li>
        <a class="copy_link" data-message-id="{{message_id}}" data-clipboard-text="{{ conversation_time_uri }}" tabindex="0">
            <i class="fa fa-link" aria-hidden="true"></i> {{t "Copy link to message" }}
        </a>
    </li>
</ul>

</pre>
#### user_info_popover_title.hbs ####
<pre>
<div class="popover-avatar{{#if user_is_guest}} guest-avatar{{/if}}" style="background-image: url('{{user_avatar}}');" >
</div>

</pre>
#### dialog_widget.hbs ####
<pre>
<div class="micromodal" id="dialog_widget_modal" aria-hidden="true">
    <div class="modal__overlay" tabindex="-1">
        <div {{#if id}}id="{{id}}" {{/if}}class="modal__container" role="dialog" aria-modal="true" aria-labelledby="dialog_title">
            <header class="modal__header">
                <h1 class="modal__title dialog_heading">
                    {{{ heading_text }}}
                    {{#if link}}
                    {{> help_link_widget }}
                    {{/if}}
                </h1>
                <button class="modal__close" aria-label="{{t 'Close modal' }}" data-micromodal-close></button>
            </header>
            <main class="modal__content" data-simplebar>
                <div class="alert" id="dialog_error"></div>
                {{{ html_body }}}
            </main>
            <footer class="modal__footer">
                {{#unless single_footer_button}}
                <button class="modal__btn dialog_cancel_button" aria-label="{{t 'Close this dialog window' }}" data-micromodal-close>{{t "Cancel" }}</button>
                {{/unless}}
                <button class="modal__btn dialog_submit_button"{{#if single_footer_button}} aria-label="{{t 'Close this dialog window' }}" data-micromodal-close{{/if}}>
                    <span>{{{ html_submit_button }}}</span>
                    <div class="modal__spinner"></div>
                </button>
            </footer>
        </div>
    </div>
</div>

</pre>
#### announce_stream_docs.hbs ####
<pre>
{{! Explanation of what "announce stream" does when creating a stream }}
<div>

    {{#tr}}
    <p>Stream will be announced in <b>#{notifications_stream}</b>.</p>
    {{/tr}}
    <p>{{t 'Organization administrators can change the announcement stream in the organization settings.' }}</p>

</div>

</pre>
#### embedded_bot_config_item.hbs ####
<pre>
<div class="input-group" name="{{botname}}" id="{{botname}}_{{key}}">
    <label for="{{botname}}_{{key}}_input">{{key}}</label>
    <input type="text" name="{{key}}" id="{{botname}}_{{key}}_input" class="modal_text_input"
      maxlength=1000 placeholder="{{value}}" value="" />
</div>

</pre>
#### copy_code_button.hbs ####
<pre>
<button class="btn pull-left copy_button_base copy_codeblock" data-tippy-content="{{t 'Copy code' }}" aria-label="{{t 'Copy code' }}">
    {{> copy_to_clipboard_svg }}
</button>

</pre>
#### view_code_in_playground.hbs ####
<pre>
{{! Display the "view code in playground" option for code blocks}}
<a target="_blank" rel="noopener noreferrer" class="code_external_link"><i class="fa fa-external-link"></i></a>

</pre>
#### realm_creation_disabled.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Organization creation link required") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<div class="error_page">
    <div class="container row-fluid">
        <img src="{{ static('images/errors/500art.svg') }}" alt=""/>
        <div class="errorbox">
            <div class="errorcontent">
                <h1 class="lead">{{ _("Organization creation link required") }}</h1>
                <p>
                    {% trans %}
                    Creating a new organization on this server requires a valid organization creation link.
                    Please see <a href="https://zulip.readthedocs.io/en/stable/production/multiple-organizations.html">documentation</a> on creating a new organization for more information.
                    {% endtrans %}
                </p>
            </div>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### realm_creation_form.html ####
<pre>
<div class="realm-creation-editable-inputs {% if user_registration_form and not form.realm_subdomain.errors %}hide{% endif %}">
    <div class="input-box">
        <div class="inline-block relative">
            <input id="id_team_name" class="required" type="text"
              placeholder="Acme or Ακμή"
              value="{% if form.realm_name.value() %}{{ form.realm_name.value() }}{% endif %}"
              name="realm_name" maxlength="{{ MAX_REALM_NAME_LENGTH }}" required {% if not user_registration_form %}autofocus{% endif %} />
        </div>
        <label for="id_team_name" class="inline-block label-title">{{ _('Organization name') }}</label>
        {% if form.realm_name.errors %}
            {% for error in form.realm_name.errors %}
            <p class="help-inline text-error">{{ error }}</p>
            {% endfor %}
        {% endif %}

        {% if not user_registration_form %}
        <div class="help-text">
            {{ _('Shorter is better than longer.') }}
        </div>
        {% endif %}
    </div>

    <div class="input-box">
        <div class="inline-block relative">
            <select name="realm_type" id="realm_type">
                {% for realm_type in sorted_realm_types %}
                    {% if not realm_type.hidden %}
                    <option value="{{ realm_type.id }}" {% if form.realm_type.value() == realm_type.id %}selected{% endif %} >{{ _(realm_type.name) }}</option>
                    {% endif %}
                {% endfor %}
            </select>
        </div>

        <label for="realm_type" class="inline-block label-title">{{ _('Organization type') }}</label>
    </div>

    <div class="input-box">
        <label class="static org-url">
            {{ _('Organization URL') }}
        </label>
        {% if root_domain_available %}
        <label class="checkbox static" for="realm_in_root_domain">
            <input type="checkbox" name="realm_in_root_domain" id="realm_in_root_domain"
              {% if not form.realm_subdomain.value() and not form.realm_subdomain.errors %}checked="checked"{% endif %}/>
            <span></span>
            {% trans %}Use {{ external_host }}{% endtrans %}
        </label>
        {% endif %}

        <div id="subdomain_section" {% if root_domain_available and
          not form.realm_subdomain.errors and not form.realm_subdomain.value() %}style="display: none;"{% endif %}>
            <div class="or"><span>{{ _('OR') }}</span></div>
            <div class="inline-block relative">
                <input id="id_team_subdomain"
                  class="{% if root_domain_landing_page %}required{% endif %} subdomain" type="text"
                  placeholder="acme"
                  value="{% if form.realm_subdomain.value() %}{{ form.realm_subdomain.value() }}{% endif %}"
                  name="realm_subdomain" maxlength="{{ MAX_REALM_SUBDOMAIN_LENGTH }}"
                  {% if root_domain_landing_page %}required{% endif %} />
                <label for="id_team_subdomain" class="realm_subdomain_label">.{{ external_host }}</label>
                <p id="id_team_subdomain_error_client" class="error help-inline text-error"></p>
            </div>
            {% if form.realm_subdomain.errors %}
                {% for error in form.realm_subdomain.errors %}
                <p class="error help-inline text-error team_subdomain_error_server">{{ error }}</p>
                {% endfor %}
            {% endif %}
        </div>
    </div>
</div>

</pre>
#### message_inline_image_tooltip.hbs ####
<pre>
<div id="message_inline_image_tooltip">
    <strong>{{ title }}</strong>
    <br/>
    <span class="tooltip-inner-content italic">{{t 'Click to view or download.'}}</span>
</div>

</pre>
#### remind_me_popover_content.hbs ####
<pre>
{{! Contents of the "remind me about this actions" popup }}
<ul class="nav nav-list remind_me_popover">
    <li>
        <a class="remind in_20m" data-message-id="{{message.id}}" tabindex="0">
            {{t "in 20 minutes" }}
        </a>
    </li>

    <li>
        <a class="remind in_1h" data-message-id="{{message.id}}" tabindex="0">
            {{t "in 1 hour" }}
        </a>
    </li>

    <li>
        <a class="remind in_3h" data-message-id="{{message.id}}" tabindex="0">
            {{t "in 3 hours" }}
        </a>
    </li>

    <li>
        <a class="remind tomo" data-message-id="{{message.id}}" tabindex="0">
            {{t "Tomorrow" }}
        </a>
    </li>

    <li>
        <a class="remind nxtw" data-message-id="{{message.id}}" tabindex="0">
            {{t "Next week" }}
        </a>
    </li>

    <li>
        <a class='remind custom' data-message-id="{{message.id}}" tabindex="0">
            {{t "Select date and time" }}
        </a>
    </li>

</ul>

</pre>
#### left_sidebar_stream_setting_popover.hbs ####
<pre>
<ul class="nav nav-list">
    <li>
        <a href="#streams/all" class="navigate_and_close_popover">
            {{t "Browse streams" }}
        </a>
    </li>
    <li>
        <a href="#streams/new" class="navigate_and_close_popover">
            {{t "Create a stream" }}
        </a>
    </li>
</ul>

</pre>
#### stream_topic_widget.hbs ####
<pre>
<strong>
    <span class="stream">{{stream_name}}</span> &gt; <span class="topic">{{topic}}</span>
</strong>

</pre>
#### realm_redirect.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Log in to your organization") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

<div class="app goto-account-page flex full-page">
    <div class="inline-block new-style">
        <div class="lead">
            <h1 class="get-started">{{ _("Log in to your organization") }}</h1>
        </div>

        <div class="app-main goto-account-page-container white-box">
            <div class="realm-redirect-form">
                <form class="form-inline" name="realm_redirect_form"
                  action="/accounts/go/{% if request.GET %}?{{ request.GET.urlencode() }}{% endif %}" method="post">
                    {{ csrf_input }}
                    <div class="input-box horizontal">
                        <div class="inline-block relative">
                            <p id="realm_redirect_description">{{ _("Enter your organization's Zulip URL:") }}</p>
                            <input
                              type="text" value="{% if form.subdomain.value() %}{{ form.subdomain.value() }}{% endif %}"
                              placeholder="{{ _('your-organization-url') }}" autofocus id="realm_redirect_subdomain" name="subdomain"
                              autocomplete="off" required/>
                            <span id="realm_redirect_external_host">.{{external_host}}</span>
                        </div>
                        <div id="errors">
                            {% if form.subdomain.errors %}
                                {% for error in form.subdomain.errors %}
                                <div class="alert alert-error">{{ error }}</div>
                                {% endfor %}
                            {% endif %}
                        </div>
                        <button id="enter-realm-button" type="submit">{{ _('Next') }}</button>
                        <p class="bottom-text">
                            {{ _("Don't know your organization URL?") }}
                            <a target="_blank" rel="noopener noreferrer" href="/accounts/find/">{{ _("Find your organization.") }}</a>
                        </p>
                    </div>
                </form>
            </div>
        </div>

        <div class="bottom-text">
            {{ _("Need to get your group started on Zulip?") }} <a target="_blank" rel="noopener noreferrer" href="/new/">{{ _("Create a new organization.") }}</a>
        </div>
    </div>

</div>
{% endblock %}

</pre>
#### bookend.hbs ####
<pre>
{{! Client-side Handlebars template for rendering the trailing bookend. }}
<div class="{{#if is_trailing_bookend}}trailing_bookend {{/if}}bookend sub-unsub-message">
    {{#if is_spectator}}
        <span class="recent-topics-link">
            <a href="#recent">{{t "Browse recent conversations" }}</a>
        </span>
    {{else}}
        <span class="stream-status">
            {{#if deactivated}}
                {{t "This stream has been deactivated" }}
            {{else if subscribed }}
                {{t "You subscribed to stream {stream_name}" }}
            {{else if just_unsubscribed }}
                {{t "You unsubscribed from stream {stream_name}" }}
            {{else}}
                {{t "You are not subscribed to stream {stream_name}" }}
            {{/if}}
        </span>
    {{/if}}
    {{#if can_toggle_subscription}}
    <div class="sub_button_row new-style">
        <button class="button white rounded stream_sub_unsub_button {{#unless subscribed}}sea-green{{/unless}}" type="button" name="subscription">
            {{#if subscribed}}
            {{t 'Unsubscribe' }}
            {{else}}
            {{t 'Subscribe' }}
            {{/if}}
        </button>
    </div>
    {{/if}}
</div>

</pre>
#### user_group_list_item.hbs ####
<pre>
<tr data-group-id="{{group_id}}">
    <td class="group_list_item">
        {{name}}
    </td>
</tr>

</pre>
#### stream_sidebar_actions.hbs ####
<pre>
{{! Contents of the "stream actions" popup }}
<ul class="nav nav-list streams_popover" data-stream-id="{{ stream.stream_id }}" data-name="{{ stream.name }}">
    <li>
        <p class="topic-name">
            <span class="stream-privacy-{{stream.stream_id}} stream-privacy filter-icon" style="color: {{stream.color}}">
                {{> stream_privacy
                  invite_only=stream.invite_only
                  is_web_public=stream.is_web_public }}
            </span>
            <b>{{stream.name}}</b>
        </p>
    </li>

    <hr />

    {{! tabindex="0" Makes anchor tag focusable. Needed for keyboard support. }}
    <li>
        <a tabindex="0" class="open_stream_settings">
            <i class="fa fa-cog" aria-hidden="true"></i>
            {{t "Stream settings" }}
        </a>
    </li>
    <li class="hidden-for-spectators">
        <a tabindex="0" class="pin_to_top">
            <i class="fa fa-thumb-tack stream-pin-icon" aria-hidden="true"></i>
            {{#if stream.pin_to_top}}
            {{t "Unpin stream from top"}}
            {{else}}
            {{t "Pin stream to top"}}
            {{/if}}
        </a>
    </li>
    <li class="hidden-for-spectators">
        <a tabindex="0" class="mark_stream_as_read">
            <i class="fa fa-book" aria-hidden="true"></i>
            {{t "Mark all messages as read"}}
        </a>
    </li>
    <li class="hidden-for-spectators">
        <a tabindex="0" class="toggle_stream_muted">
            {{#if stream.is_muted}}
            <i class="zulip-icon zulip-icon-mute" aria-hidden="true"></i>
            {{t "Unmute stream"}}
            {{else}}
            <i class="zulip-icon zulip-icon-mute" aria-hidden="true"></i>
            {{t "Mute stream"}}
            {{/if}}
        </a>
    </li>
    <li>
        <a tabindex="0" class="popover_new_topic_button">
            <i class="fa fa-plus" aria-hidden="true"></i>
            {{t "New topic" }}
        </a>
    </li>
    <li class="hidden-for-spectators">
        <a tabindex="0" class="popover_sub_unsub_button" data-name="{{stream.name}}">
            <i class='fa fa-envelope' aria-hidden="true"></i>
            {{t "Unsubscribe" }}
        </a>
    </li>
    <li class="hidden-for-spectators">
        <span class="colorpicker-container"><input stream_id="{{stream.stream_id}}" class="colorpicker" type="text" value="{{stream.color}}" /></span>
        <a tabindex="0" class="choose_stream_color">
            <i class="fa fa-eyedropper" aria-hidden="true"></i>
            {{t "Change color" }}
        </a>
    </li>

</ul>

</pre>
#### presence_row.hbs ####
<pre>
<li data-user-id="{{user_id}}" class="user_sidebar_entry {{#if is_current_user}}user_sidebar_entry_me {{/if}}{{#if num_unread}} user-with-count {{/if}} narrow-filter {{#if faded}} user-fade {{/if}}">
    <div class="selectable_sidebar_block">
        <span class="{{user_circle_class}} user_circle"></span>
        <a class="user-presence-link"
          href="{{href}}"
          data-user-id="{{user_id}}"
          data-name="{{name}}">
            {{#if user_list_style.WITH_STATUS}}
                <div class="user-name-and-status-wrapper">
                    <div class="user-name-and-status-emoji">
                        <span class="user-name">{{name}}</span>
                        {{> status_emoji status_emoji_info}}
                    </div>
                    <span class="status-text">{{status_text}}</span>
                </div>
            {{else}}
                <span class="user-name">{{name}}</span>
                {{> status_emoji status_emoji_info}}
            {{/if}}
        </a>
        <span class="unread_count">{{#if num_unread}}{{num_unread}}{{/if}}</span>
    </div>
    <span class="user-list-sidebar-menu-icon"><i class="zulip-icon zulip-icon-ellipsis-v-solid" aria-hidden="true"></i></span>
</li>

</pre>
#### user_info_popover_content.hbs ####
<pre>
{{! Contents of the "message info" popup }}
<ul class="nav nav-list info_popover_actions" id="user_info_popover" data-user-id="{{user_id}}">
    <li class="popover_user_name_row">
        <b class="user_full_name" data-tippy-content="{{user_full_name}}">{{user_full_name}}</b>
        {{#if is_active }}
            {{#if is_bot}}
            <i class="zulip-icon zulip-icon-bot" aria-hidden="true"></i>
            {{else}}
            <span class="{{user_circle_class}} user_circle popover_user_presence tippy-zulip-tooltip hidden-for-spectators" data-tippy-content="{{user_last_seen_time_status}}"></span>
            {{/if}}
        {{/if}}
        {{#if show_manage_menu }}
        <span class="user_info_popover_action_buttons">
            <a class="user_info_popover_manage_menu_btn" role="button" tabindex="0" aria-haspopup="true">
                <i class="popover_action_icon zulip-icon zulip-icon-ellipsis-v-solid" aria-hidden="true"></i>
            </a>
        </span>
        {{/if}}
    </li>


    {{#if is_active }}
        {{#if user_email}}
        {{!-- This div is added to enable interactivity for tooltip - https://atomiks.github.io/tippyjs/v5/accessibility/#interactivity --}}
        <div>
            <li class="user_popover_email">
                <i class="fa fa-clone hide_copy_icon" data-clipboard-text="{{ user_email }}"></i>
                {{ user_email }}
            </li>
        </div>
        {{/if}}
    {{else}}
        <li class="user_popover_email half-opacity italic">{{#if is_bot}}{{t "This bot has been deactivated." }}{{else}}{{t "This user has been deactivated." }}{{/if}}</li>
    {{/if}}


    {{#if is_bot}}
        {{#if bot_owner}}
            <li class="bot_owner" data-tippy-content="{{ bot_owner.full_name }}">{{t "Bot owner" }}:
                <span class="bot-owner-name view_user_profile" data-user-id='{{ bot_owner.user_id }}'>
                    {{bot_owner.full_name}}
                </span>
            </li>
        {{else if is_system_bot}}
            <li>{{t "System bot" }}</li>
        {{else}}
            <li>{{t "Bot" }}</li>
        {{/if}}
    {{else}}
        <li>{{ user_type }}</li>
    {{/if}}
    {{!-- Display selected custom profile fields in this popover. --}}
    {{> user_custom_profile_fields profile_fields=display_profile_fields for_user_info_popover=true}}

    <li class="only-visible-for-spectators">{{t "Joined {date_joined}" }}</li>

    {{#if (or (and user_time is_active) is_me status_content_available) }}
        <hr />
    {{/if}}
    {{#if (and user_time is_active)}}
        <li class="hidden-for-spectators local_time">{{t "{user_time} local time" }}</li>
    {{/if}}

    {{#if status_content_available}}
        <li class="user_info_status_text">
            <span id="status_message">
                {{#if status_emoji_info}}
                    {{#if status_emoji_info.emoji_alt_code}}
                        <div class="emoji_alt_code">&nbsp;:{{status_emoji_info.emoji_name}}:</div>
                    {{else if status_emoji_info.url}}
                        <img src="{{status_emoji_info.url}}" class="emoji status-emoji" />
                    {{else}}
                        <div class="emoji status-emoji emoji-{{status_emoji_info.emoji_code}}"></div>
                    {{/if}}
                {{/if}}
                <span class="status_text">
                    {{status_text}}
                    {{#if is_me}}
                    <span class="clear_status_button">(<a tabindex="0" class="clear_status">{{t "clear" }}</a>)</span>
                    {{/if}}
                </span>
            </span>
        </li>
    {{/if}}

    {{#if is_me}}
        <li>
            <a tabindex="0" class="update_status_text">
                <i class="fa fa-comments" aria-hidden="true"></i>
                {{#if status_text}}
                    {{t "Edit status" }}
                {{else}}
                    {{t "Set a status" }}
                {{/if}}
            </a>
        </li>
        {{#if invisible_mode}}
        <li>
            <a tabindex="0" class="invisible_mode_turn_off">
                <i class="fa fa-circle-o" aria-hidden="true"></i> {{t "Turn off invisible mode" }}
            </a>
        </li>
        {{else}}
        <li>
            <a tabindex="0" class="invisible_mode_turn_on">
                <i class="fa fa-circle-o" aria-hidden="true"></i> {{t "Go invisible" }}
            </a>
        </li>
        {{/if}}
    {{/if}}


    {{#unless spectator_view}}
        <hr />
        <li>
            <a tabindex="0" class="view_full_user_profile">
                {{#if is_me}}
                    <i class="fa fa-user" aria-hidden="true"></i> {{t "View your profile" }}
                {{else}}
                    <i class="fa fa-user" aria-hidden="true"></i> {{t "View profile" }}
                {{/if}}
            </a>
        </li>
        {{#if can_send_private_message}}
            <li>
                <a tabindex="0" class="{{ private_message_class }}">
                    <i class="fa fa-comment" aria-hidden="true"></i> {{t "Send direct message" }} {{#if is_sender_popover}}<span class="hotkey-hint">(R)</span>{{/if}}
                </a>
            </li>
        {{/if}}
        {{#unless is_me}}
        <li>
            {{#if has_message_context}}
            <a tabindex="0" class="mention_user">
                <i class="fa fa-at" aria-hidden="true"></i>
                {{#if is_bot}}{{t "Reply mentioning bot" }}{{else}}{{t "Reply mentioning user" }}{{/if}}
                {{#if is_sender_popover}}<span class="hotkey-hint">(@)</span>{{/if}}
            </a>
            {{else}}
            <a tabindex="0" class="copy_mention_syntax" data-clipboard-text="{{ user_mention_syntax }}">
                <i class="fa fa-at" aria-hidden="true"></i>
                {{t "Copy mention syntax" }}
                {{#if is_sender_popover}}<span class="hotkey-hint">(@)</span>{{/if}}
            </a>
            {{/if}}
        </li>
        {{/unless}}
        {{#if is_me}}
        <li>
            <a href="/#settings/profile">
                <i class="fa fa-edit" aria-hidden="true"></i> {{t "Edit your profile" }}
            </a>
        </li>
        {{/if}}
        <hr />
        <li>
            <a href="{{ pm_with_url }}" class="narrow_to_private_messages">
                <i class="fa fa-envelope" aria-hidden="true"></i>
                {{#if is_me}}
                    {{t "View messages with yourself" }}
                {{else}}
                    {{t "View direct messages" }}
                {{/if}}
            </a>
        </li>
        <li>
            <a href="{{ sent_by_uri }}" class="narrow_to_messages_sent">
                <i class="fa fa-paper-plane" aria-hidden="true"></i> {{t "View messages sent" }}
            </a>
        </li>
    {{/unless}}
</ul>

</pre>
#### user_with_status_icon.hbs ####
<pre>
<div class="user_status_icon_wrapper">
    <span class="user-name">{{name}}</span>
    {{> status_emoji status_emoji_info}}
</div>

</pre>
#### set_status_overlay.hbs ####
<pre>
<div class="new-style user-status-content-wrapper">
    <div class="status-emoji-wrapper tippy-zulip-tooltip"  data-tippy-content="{{t 'Select emoji' }}" data-tippy-placement="top" aria-label="{{t 'Select emoji' }}"  tabindex="0" id="selected_emoji">
        {{> status_emoji_selector}}
    </div>
    <input type="text" class="user-status" placeholder="{{t 'Your status' }}" maxlength="60"/>
    <button type="button" class="btn clear_search_button" id="clear_status_message_button" disabled="disabled">
        <i class="fa fa-remove" aria-hidden="true"></i>
    </button>
</div>
<div class="new-style user-status-options">
    {{#each default_status_messages_and_emoji_info}}
        <button type="button" class="button no-style user-status-value">
            {{#if emoji.emoji_alt_code}}
                <div class="emoji_alt_code">&nbsp;:{{emoji.emoji_name}}:</div>
            {{else if emoji.url}}
                <img src="{{emoji.url}}" class="emoji status-emoji" />
            {{else}}
                <div class="emoji status-emoji emoji-{{emoji.emoji_code}}"></div>
            {{/if}}
            {{status_text}}
        </button>
    {{/each}}
</div>

</pre>
#### blueslip_stacktrace.hbs ####
<pre>
<div class="stacktrace-header">
    <div class="warning-symbol">
        <i class="fa fa-exclamation-triangle"></i>
    </div>
    <div class="message"><strong>Error:</strong> {{ error }}</div>
    <div class="exit"></div>
</div>
<div class="stacktrace-content">
    {{#each stackframes}}
        <div data-full-path="{{ full_path }}" data-line-no="{{ line_number }}">
            <div class="stackframe">
                <i class="fa fa-caret-right expand"></i>
                <span class="subtle">at</span>
                {{#if function_name}}
                {{ function_name.scope }}<b>{{ function_name.name }}</b>
                {{/if}}
                <span class="subtle">{{ show_path }}:{{ line_number }}</span>
            </div>
            <div class="code-context" style="display: none">
                <div class="code-context-content">
                    {{~#each context~}}
                        <div {{#if focus}}class="focus-line"{{/if}}><span class="line-number">{{ line_number }}</span> {{ line }}</div>
                    {{~/each~}}
                </div>
            </div>
        </div>
    {{/each}}
</div>

</pre>
#### typeahead_list_item.hbs ####
<pre>
{{#if is_emoji}}
    {{#if has_image}}
        <img class="emoji" src="{{ img_src }}" />
    {{else}}
        <span class='emoji emoji-{{ emoji_code }}'></span>
    {{/if}}
    &nbsp;&nbsp;
{{else if is_person}}
    {{#if user_circle_class}}
    <span class="{{user_circle_class}} user_circle"></span>
    {{/if}}
    {{#if has_image}}
    <img class="typeahead-image" src="{{ img_src }}" />
    {{else}}
    <span class='typeahead-image fa fa-bullhorn no-presence-circle'></span>
    {{/if}}
{{else if is_user_group}}
    <i class="typeahead-image icon fa fa-group no-presence-circle" aria-hidden="true"></i>
{{/if}}
<strong>
    {{~ primary ~}}
</strong>
{{~#if has_status}}
{{> status_emoji status_emoji_info}}
{{~/if}}
{{~#if has_secondary}}
&nbsp;&nbsp;
<small class="autocomplete_secondary">
    {{~ secondary ~}}
</small>
{{#if is_unsubscribed}}
&nbsp;
<span class="fa fa-exclamation-triangle unsubscribed_icon"
  title="{{t 'You are not currently subscribed to this stream.' }}"></span>
{{/if}}
{{~/if}}

</pre>
#### user_group_info_popover.hbs ####
<pre>
<div class="popover message-info-popover group-info-popover">
    <div class="popover-inner">
        <div class="popover-content">
            <div></div>
        </div>
    </div>
</div>

</pre>
#### emoji_showcase.hbs ####
<pre>
{{#with emoji_dict}}
<div class="emoji-showcase">
    {{#if is_realm_emoji}}
    <img src="{{url}}" class="emoji emoji-preview"/>
    {{else}}
    <div class="emoji emoji-preview emoji-{{emoji_code}}"></div>
    {{/if}}
    <div class="emoji-canonical-name" title="{{name}}">{{name}}</div>
</div>
{{/with}}

</pre>
#### topic_sidebar_actions.hbs ####
<pre>
<ul class="nav nav-list topics_popover">
    <li>
        <p class="topic-name">
            <i class="fa fa-chevron-right" aria-hidden="true" style="color: {{color}}"></i>
            <b>{{topic_name}}</b>
        </p>
    </li>

    <hr />

    {{#unless topic_muted}}
    <li class="hidden-for-spectators">
        <a tabindex="0" class="sidebar-popover-mute-topic" data-stream-id="{{ stream_id }}" data-topic-name="{{ topic_name }}">
            <i class="zulip-icon zulip-icon-mute" aria-hidden="true"></i>
            {{t "Mute topic"}}
        </a>
    </li>
    {{else}}
    <li class="hidden-for-spectators">
        <a tabindex="0" class="sidebar-popover-unmute-topic" data-stream-id="{{ stream_id }}" data-topic-name="{{ topic_name }}">
            <i class="zulip-icon zulip-icon-mute" aria-hidden="true"></i>
            {{t "Unmute topic"}}
        </a>
    </li>
    {{/unless}}

    {{#if has_starred_messages}}
    <li class="hidden-for-spectators">
        <a tabindex="0" class="sidebar-popover-unstar-all-in-topic" data-stream-id="{{ stream_id }}" data-topic-name="{{ topic_name }}">
            <i class="fa fa-star-o" aria-hidden="true"></i>
            {{t "Unstar all messages in topic" }}
        </a>
    </li>
    {{/if}}

    <li class="hidden-for-spectators">
        <a tabindex="0" class="sidebar-popover-mark-topic-read" data-stream-id="{{ stream_id }}" data-topic-name="{{ topic_name }}">
            <i class="fa fa-book" aria-hidden="true"></i>
            {{t "Mark all messages as read"}}
        </a>
    </li>

    <li>
        <a tabindex="0" class="sidebar-popover-copy-link-to-topic" data-stream-id="{{ stream_id }}" data-topic-name="{{ topic_name }}">
            <i class="fa fa-link" aria-hidden="true"></i>
            {{t "Copy link to topic"}}
        </a>
    </li>

    {{#if can_move_topic}}
    <hr />

    <li>
        <a tabindex="0" class="sidebar-popover-move-topic-messages" data-stream-id="{{ stream_id }}" data-topic-name="{{ topic_name }}">
            <i class="fa fa-arrows" aria-hidden="true"></i>
            {{t "Move topic"}}
        </a>
    </li>
    <li>
        <a tabindex="0" class="sidebar-popover-toggle-resolved" data-stream-id="{{ stream_id }}" data-topic-name="{{ topic_name }}">
            <i class="fa fa-check" aria-hidden="true"></i>
            {{# if topic_is_resolved }}
            {{t "Mark as unresolved"}}
            {{else}}
            {{t "Mark as resolved"}}
            {{/if}}
        </a>
    </li>
    {{/if}}

    {{#if is_realm_admin}}
    <li>
        <a tabindex="0" class="sidebar-popover-delete-topic-messages" data-stream-id="{{ stream_id }}" data-topic-name="{{ topic_name }}">
            <i class="fa fa-trash" aria-hidden="true"></i>
            {{t "Delete topic"}}
        </a>
    </li>
    {{/if}}
</ul>

</pre>
#### feedback_container.hbs ####
<pre>
<div class="float-header">
    <h3 class="light no-margin small-line-height float-left feedback_title"></h3>
    <div class="exit-me float-right">&#215;</div>
    <button class="button small rounded float-right feedback_undo" type="button" name="button"></button>
    <div class="float-clear"></div>
</div>
<p class="n-margin feedback_content"></p>

</pre>
#### default_language_modal.hbs ####
<pre>
<p>
    {{t "A language is marked as 100% translated only if every string in the web, desktop,
      and mobile apps is translated, including administrative UI and error messages." }}
</p>
<p>
    {{#tr}}
        Zulip's translations are contributed by our amazing community of volunteer
        translators. If you'd like to help, see the
        <z-link>Zulip translation guidelines</z-link>.
        {{#*inline "z-link"}}<a target="_blank" rel="noopener noreferrer" href="https://zulip.readthedocs.io/en/latest/translating/translating.html">{{> @partial-block}}</a>{{/inline}}
    {{/tr}}
</p>
<div class="default_language_modal_table">
    {{#each language_list}}
        <div class="language_block">
            <a class="language" data-code="{{this.code}}" data-name="{{this.name}}">
                {{#if this.selected}}
                <b>{{this.name_with_percent}}</b>
                {{else}}
                {{this.name_with_percent}}
                {{/if}}
            </a>
        </div>
    {{/each}}
</div>

</pre>
#### user_info_popover_manage_menu.hbs ####
<pre>
<ul class="nav nav-list user_info_popover_manage_menu" data-user-id="{{user_id}}">
    {{#if can_mute }}
    <li>
        <a tabindex="0" class="sidebar-popover-mute-user">
            <i class="fa fa-eye-slash" aria-hidden="true"></i> {{t "Mute this user" }}
        </a>
    </li>
    {{/if}}
    {{#if can_unmute}}
    <li>
        <a tabindex="0" class="sidebar-popover-unmute-user">
            <i class="fa fa-eye" aria-hidden="true"></i> {{t "Unmute this user" }}
        </a>
    </li>
    {{/if}}
    {{#if can_manage_user}}
        {{#if is_active}}
        <li>
            <a tabindex="0" class="sidebar-popover-manage-user">
                <i class="fa fa-edit" aria-hidden="true"></i> {{#if is_bot}}{{t "Manage this bot" }}{{else}}{{t "Manage this user" }}{{/if}}
            </a>
        </li>
        {{else}}
        <li>
            <a tabindex="0" class="sidebar-popover-reactivate-user">
                <i class="fa fa-user-plus" aria-hidden="true"></i> {{#if is_bot}}{{t "Reactivate this bot" }}{{else}}{{t "Reactivate this user" }}{{/if}}
            </a>
        </li>
        {{/if}}
    {{/if}}
</ul>

</pre>
#### emoji_popover_search_results.hbs ####
<pre>
{{#each search_results}}
    {{> emoji_popover_emoji type="emoji_search_result" section="0" index=@index message_id=../message_id is_status_emoji_popover=../is_status_emoji_popover emoji_dict=this }}
{{/each}}

</pre>
#### empty_feed_notice.hbs ####
<pre>
<div class="empty_feed_notice">
    <h4> {{ title }} </h4>
    {{#if search_data}}
    <div>
        {{#if search_data.has_stop_word}}{{t "Some common words were excluded from your search." }} <br/>{{/if}}{{t "You searched for:" }}
        {{#if search_data.stream_query}}
        <span>stream: {{search_data.stream_query}}</span>
        {{/if}}
        {{#if search_data.topic_query}}
        <span>topic: {{search_data.topic_query}}</span>
        {{/if}}
        {{#each search_data.query_words}}
            {{#if is_stop_word}}
            <del>{{query_word}}</del>
            {{else}}
            <span>{{query_word}}</span>
            {{/if}}
        {{/each}}
    </div>
    {{else}}
    {{{ html }}}
    {{/if}}
</div>

</pre>
#### settings_overlay.hbs ####
<pre>
<div id="settings_page" class="new-style overlay-content modal-bg">
    <div class="settings-header mobile">
        <i class="fa fa-chevron-left" aria-hidden="true"></i>
        <h1>{{t "Settings" }}<span class="section"></span></h1>
        <div class="exit">
            <span class="exit-sign">&times;</span>
        </div>
        <div class="clear-float"></div>
    </div>
    <div class="sidebar-wrapper">
        <div class="center tab-container settings-sticky-bar"></div>
        <div class="sidebar left" data-simplebar>
            <div class="sidebar-list dark-grey small-text">
                <ul class="normal-settings-list">
                    <li tabindex="0" data-section="profile">
                        <i class="icon fa fa-user" aria-hidden="true"></i>
                        <div class="text">{{t "Profile" }}</div>
                    </li>
                    <li tabindex="0" data-section="account-and-privacy">
                        <i class="icon fa fa-lock" aria-hidden="true"></i>
                        <div class="text">{{t "Account & privacy" }}</div>
                    </li>
                    <li tabindex="0" data-section="display-settings">
                        <i class="icon fa fa-clock-o" aria-hidden="true"></i>
                        <div class="text">{{t "Display settings" }}</div>
                    </li>
                    <li tabindex="0" data-section="notifications">
                        <i class="icon fa fa-exclamation-triangle" aria-hidden="true"></i>
                        <div class="text">{{t "Notifications" }}</div>
                    </li>
                    {{#unless is_guest}}
                    <li tabindex="0" data-section="your-bots">
                        <i class="icon fa fa-github" aria-hidden="true"></i>
                        <div class="text">{{t "Bots" }}</div>
                    </li>
                    {{/unless}}
                    <li tabindex="0" data-section="alert-words">
                        <i class="icon fa fa-book" aria-hidden="true"></i>
                        <div class="text">{{t "Alert words" }}</div>
                    </li>
                    {{#if show_uploaded_files_section}}
                    <li tabindex="0" data-section="uploaded-files">
                        <i class="icon fa fa-paperclip" aria-hidden="true"></i>
                        <div class="text">{{t "Uploaded files" }}</div>
                    </li>
                    {{/if}}
                    <li tabindex="0" data-section="muted-topics">
                        <i class="icon zulip-icon zulip-icon-mute" aria-hidden="true"></i>
                        <div class="text">{{t "Muted topics" }}</div>
                    </li>
                    <li tabindex="0" data-section="muted-users">
                        <i class="icon fa fa-eye-slash" aria-hidden="true"></i>
                        <div class="text">{{t "Muted users" }}</div>
                    </li>
                </ul>

                <ul class="org-settings-list">
                    <li tabindex="0" data-section="organization-profile">
                        <i class="icon fa fa-id-card" aria-hidden="true"></i>
                        <div class="text">{{t "Organization profile" }}</div>
                        {{#unless is_admin}}
                        <i class="locked fa fa-lock" title="{{t 'Only organization administrators can edit these settings.' }}"></i>
                        {{/unless}}
                    </li>
                    <li class="collapse-org-settings {{#unless is_admin}}hide-org-settings{{/unless}}" tabindex="0" data-section="organization-settings">
                        <i class="icon fa fa-sliders" aria-hidden="true"></i>
                        <div class="text">{{t "Organization settings" }}</div>
                        {{#unless is_admin}}
                        <i class="locked fa fa-lock" title="{{t 'Only organization administrators can edit these settings' }}"></i>
                        {{/unless}}
                    </li>
                    <li class="collapse-org-settings {{#unless is_admin}}hide-org-settings{{/unless}}" tabindex="0" data-section="organization-permissions">
                        <i class="icon fa fa-lock" aria-hidden="true"></i>
                        <div class="text">{{t "Organization permissions" }}</div>
                        {{#unless is_admin}}
                        <i class="locked fa fa-lock" title="{{t 'Only organization administrators can edit these settings.' }}"></i>
                        {{/unless}}
                    </li>
                    <li tabindex="0" data-section="emoji-settings">
                        <i class="icon fa fa-smile-o" aria-hidden="true"></i>
                        <div class="text">{{t "Custom emoji" }}</div>
                        {{#if is_guest}}
                            <i class="locked fa fa-lock" title="{{t 'Guest users cannot edit custom emoji.' }}"></i>
                        {{else if show_emoji_settings_lock}}
                            <i class="locked fa fa-lock" title="{{t 'Only organization administrators can edit these settings.'}}"></i>
                        {{/if}}
                    </li>
                    <li tabindex="0" data-section="linkifier-settings">
                        <i class="icon fa fa-font" aria-hidden="true"></i>
                        <div class="text">{{t "Linkifiers" }}</div>
                        {{#unless is_admin}}
                        <i class="locked fa fa-lock" title="{{t 'Only organization administrators can edit these settings.' }}"></i>
                        {{/unless}}
                    </li>
                    <li tabindex="0" data-section="playground-settings">
                        <i class="icon fa fa-external-link" aria-hidden="true"></i>
                        <div class="text">{{t "Code playgrounds" }}</div>
                        {{#unless is_admin}}
                        <i class="locked fa fa-lock" title="{{t 'Only organization administrators can edit these settings.' }}"></i>
                        {{/unless}}
                    </li>
                    {{#unless is_guest}}
                    <li tabindex="0" data-section="user-groups-admin">
                        <i class="icon fa fa-group" aria-hidden="true"></i>
                        <div class="text">{{t "User groups" }}</div>
                    </li>
                    {{/unless}}
                    {{#unless is_guest}}
                    <li tabindex="0" data-section="user-list-admin">
                        <i class="icon fa fa-user" aria-hidden="true"></i>
                        <div class="text">{{t "Users" }}</div>
                        {{#unless is_admin}}
                        <i class="locked fa fa-lock" title="{{t 'Only organization administrators can edit these settings.' }}"></i>
                        {{/unless}}
                    </li>
                    {{/unless}}
                    {{#unless is_guest}}
                    <li class="collapse-org-settings {{#unless is_admin}}hide-org-settings{{/unless}}" tabindex="0" data-section="deactivated-users-admin">
                        <i class="icon fa fa-user-times" aria-hidden="true"></i>
                        <div class="text">{{t "Deactivated users" }}</div>
                        {{#unless is_admin}}
                        <i class="locked fa fa-lock" title="{{t 'Only organization administrators can edit these settings.' }}"></i>
                        {{/unless}}
                    </li>
                    {{/unless}}
                    {{#unless is_guest}}
                    <li tabindex="0" data-section="bot-list-admin">
                        <i class="icon fa fa-github" aria-hidden="true"></i>
                        <div class="text">{{t "Bots" }}</div>
                        {{#unless is_admin}}
                        <i class="locked fa fa-lock" title="{{t 'Only organization administrators can edit these settings.' }}"></i>
                        {{/unless}}
                    </li>
                    {{/unless}}
                    {{#unless is_guest}}
                    <li tabindex="0" data-section="invites-list-admin">
                        <i class="icon fa fa-user-plus" aria-hidden="true"></i>
                        <div class="text">{{t "Invitations" }}</div>
                    </li>
                    {{/unless}}
                    {{#if is_admin}}
                    <li tabindex="0" data-section="profile-field-settings">
                        <i class="icon fa fa-id-card" aria-hidden="true"></i>
                        <div class="text">{{t "Custom profile fields" }}</div>
                    </li>
                    {{/if}}
                    <li class="collapse-org-settings {{#unless is_admin}}hide-org-settings{{/unless}}" tabindex="0" data-section="organization-level-user-defaults">
                        <i class="icon fa fa-cog" aria-hidden="true"></i>
                        <div class="text">{{t "Default user settings" }}</div>
                        {{#unless is_admin}}
                        <i class="locked fa fa-lock" title="{{t 'Only organization administrators can edit these settings.' }}"></i>
                        {{/unless}}
                    </li>
                    {{#unless is_guest}}
                    <li class="collapse-org-settings {{#unless is_admin}}hide-org-settings{{/unless}}" tabindex="0" data-section="default-streams-list">
                        <i class="icon fa fa-exchange" aria-hidden="true"></i>
                        <div class="text">{{t "Default streams" }}</div>
                        {{#unless is_admin}}
                        <i class="locked fa fa-lock" title="{{t 'Only organization administrators can edit these settings.' }}"></i>
                        {{/unless}}
                    </li>
                    {{/unless}}
                    <li class="collapse-org-settings {{#unless is_admin}}hide-org-settings{{/unless}}" tabindex="0" data-section="auth-methods">
                        <i class="icon fa fa-key" aria-hidden="true"></i>
                        <div class="text">{{t "Authentication methods" }}</div>
                        {{#unless is_owner}}
                        <i class="locked fa fa-lock" title="{{t 'Only organization owners can edit these settings.' }}"></i>
                        {{/unless}}
                    </li>
                    {{#if is_admin}}
                    <li tabindex="0" data-section="data-exports-admin">
                        <i class="icon fa fa-database" aria-hidden="true"></i>
                        <div class="text">{{t "Data exports" }}</div>
                    </li>
                    {{/if}}
                    {{#unless is_admin}}
                    <div class="collapse-settings-btn">
                        <i id='toggle_collapse_chevron' class='fa fa-angle-double-down'></i>
                        <p id='toggle_collapse'>{{t "Show more" }}</p>
                    </div>
                    {{/unless}}
                </ul>
            </div>
        </div>
    </div>
    <div class="content-wrapper right">
        <div class="settings-header">
            <h1>{{t "Settings" }}<span class="section"></span></h1>
            <div class="exit">
                <span class="exit-sign">&times;</span>
            </div>
        </div>
        <div id="settings_content" data-simplebar data-simplebar-auto-hide="false">
            <div class="organization-box organization">

            </div>
            <div class="settings-box">
            </div>
        </div>
    </div>
</div>

</pre>
#### muted_topic_ui_row.hbs ####
<pre>
{{#with muted_topic}}
<tr data-stream-id="{{stream_id}}" data-stream="{{stream}}" data-topic="{{topic}}" data-date-muted="{{date_muted_str}}">
    <td>{{stream}}</td>
    <td>{{topic}}</td>
    <td class="topic_date_muted">{{date_muted_str}}</td>
    <td class="actions">
        <span><a class="settings-unmute-topic">{{t "Unmute" }}</a></span>
    </td>
</tr>
{{/with}}

</pre>
#### footer.html ####
<pre>
<footer id="footer">
    {% if corporate_enabled %}
    <div class='footer__container'>
        <div class="footer__section">
            <h3 class="footer__section-title">
                {{ _("Product") }}
            </h3>
            <ul>
                <li><a href="/why-zulip/">{{ _("Why Zulip") }}</a></li>
                <li><a href="/features/">{{ _("Features") }}</a></li>
                <li><a href="/plans/">{{ _("Plans & pricing") }}</a></li>
                <li><a href="/self-hosting/">{{ _("Self-hosting") }}</a></li>
                <li><a href="/security/">{{ _("Security") }}</a></li>
                <li><a href="/integrations/">{{ _("Integrations") }}</a></li>
                <li class="extra_margin"><a href="/apps/">{{ _("Desktop & mobile apps") }}</a></li>
                <li><a href="/new/">{{ _("New organization") }}</a></li>
                <li><a href="/accounts/go/">{{ _("Log in") }}</a></li>
            </ul>
        </div>
        <div class="footer__section">
            <h3 class="footer__section-title">
                {{ _("Solutions") }}
            </h3>
            <ul>
                <li><a href="/for/business/">{{ _("Business") }}</a></li>
                <li><a href="/for/education/">{{ _("Education") }}</a></li>
                <li><a href="/for/research/">{{ _("Research") }}</a></li>
                <li><a href="/for/events/">{{ _("Events & conferences") }}</a></li>
                <li><a href="/for/open-source/">{{ _("Open source projects") }}</a></li>
                <li class="extra_margin"><a href="/for/communities/">{{ _("Communities") }}</a></li>
                <li><a href="/use-cases/">{{ _("Customer stories") }}</a></li>
                <li><a href="/communities/">{{ _("Open communities") }}</a></li>
            </ul>
        </div>
        <div class="footer__section">
            <h3 class="footer__section-title">
                {{ _("Resources") }}
            </h3>
            <ul>
                <li><a href="/help/getting-started-with-zulip">{{ _("Getting started") }}</a></li>
                <li><a href="/help/">{{ _("Help center") }}</a></li>
                <li><a href="/development-community/" target="_blank">{{ _("Community chat") }}</a></li>
                <li class="extra_margin"><a href="/help/contact-support">{{ _("Contact support") }}</a></li>
                <li>
                    <a href="/help/getting-your-organization-started-with-zulip">
                        {{ _("Organization set up") }}
                    </a>
                </li>
                <li>
                    <a href="https://zulip.readthedocs.io/en/stable/production/install.html">
                        {{ _("Installing a Zulip server") }}
                    </a>
                </li>
                <li>
                    <a href="https://zulip.readthedocs.io/en/stable/production/upgrade-or-modify.html">
                        {{ _("Upgrading a Zulip server") }}
                    </a>
                </li>
            </ul>
        </div>
        <div class="footer__section">
            <h3 class="footer__section-title">
                {{ _("Contributing") }}
            </h3>
            <ul>
                <li>
                    <a href="https://zulip.readthedocs.io/en/latest/contributing/contributing.html">
                        {{ _("Contributing guide") }}
                    </a>
                </li>
                <li><a href="/development-community/">{{ _("Development community") }}</a></li>
                <li>
                    <a href="https://zulip.readthedocs.io/en/latest/translating/translating.html">
                        {{ _("Translation") }}
                    </a>
                </li>
                <li><a href="/api/">API</a></li>
                <li><a href="https://github.com/zulip/zulip/">{{ _("GitHub") }}</a></li>
            </ul>
        </div>
        <div class="footer__section">
            <h3 class="footer__section-title">
                {{ _("About us") }}
            </h3>
            <ul>
                <li>
                    <a href="/team/">{{ _("Team") }}</a>
                    &
                    <a href="/history/">{{ _("History") }}</a>
                </li>
                <li><a href="/values/">{{ _("Values") }}</a></li>
                <li><a href="/jobs/">{{ _("Jobs") }}</a></li>
                <li><a href="https://blog.zulip.com/"  target="_blank">{{ _("Blog") }}</a></li>
                <li><a href="https://twitter.com/zulip/">Twitter</a></li>
                <li><a href="https://zulip.com/help/support-zulip-project">{{ _("Support Zulip") }}</a></li>
            </ul>
        </div>
    </div>
    {% endif %}
    <div class="footer__legal {% if not corporate_enabled %}footer__legal_not_corporate{% endif %}">
        <div class="footer__legal-container">
            {% if corporate_enabled %}
            <div class="copyright">© Kandra Labs, Inc. (“Zulip”)</div>
            {% else %}
            <div class="copyright">{% trans %}Powered by <a href="https://zulip.com">Zulip</a>{% endtrans %}</div>
            {% endif %}
            <div class="footer__legal-spacer"></div>
            {% if not corporate_enabled %}
            <a href="/help/">{{ _("Help center") }}</a>
            {% endif %}
            <a href="{{ root_domain_uri }}/policies/terms">{{ _("Terms of Service") }}</a>
            <a href="{{ root_domain_uri }}/policies/privacy">{{ _("Privacy policy") }}</a>
            {% if corporate_enabled %}
            <a href="https://zulip.com/attribution/">{{ _("Website attributions") }}</a>
            {% endif %}
        </div>
    </div>
</footer>

</pre>
#### message_edit_history.hbs ####
<pre>
{{! Client-side Handlebars template for viewing message edit history. }}

{{#each edited_messages}}
    {{#if show_date_row}}
    <div class="date_row"><span>{{ display_date }}</span></div>
    {{/if}}
    <div class="messagebox-content">
        <div class="message_top_line"><span class="message_time">{{ timestamp }}</span></div>
        {{#if topic_edited}}
        <div class="message_content message_edit_history_content"><p>Topic: <span class="highlight_text_inserted">{{ new_topic }}</span> <span class="highlight_text_deleted">{{ prev_topic }}</span></p></div>
        {{/if}}
        {{#if stream_changed}}
        <div class="message_content message_edit_history_content"><p>Stream: <span class="highlight_text_inserted">{{ new_stream }}</span> <span class="highlight_text_deleted">{{ prev_stream }}</span></p></div>
        {{/if}}
        {{#if body_to_render}}
        <div class="message_content rendered_markdown message_edit_history_content">{{rendered_markdown body_to_render}}</div>
        {{/if}}
        <div class="message_author"><div class="author_details">{{ edited_by_notice }}</div></div>
    </div>
    <hr />
{{/each}}

</pre>
#### message_reaction.hbs ####
<pre>
<div class="{{this.class}}" aria-label="{{this.label}}" data-reaction-id="{{this.local_id}}">
    {{#if this.emoji_alt_code}}
        <div class="emoji_alt_code">&nbsp;:{{this.emoji_name}}:</div>
    {{else if this.is_realm_emoji}}
        <img src="{{this.url}}" class="emoji" />
    {{else}}
        <div class="emoji emoji-{{this.emoji_code}}"></div>
    {{/if}}
    <div class="message_reaction_count">{{this.vote_text}}</div>
</div>

</pre>
#### email.html ####
<pre>
{% if from_email != envelope_from %}
<h4>Envelope-From: {{ envelope_from }}</h4>
{% endif %}
<h4>From: {{ from_email }}</h4>
{% if reply_to %}
<h4>Reply to:
    {% for email in reply_to %}
    {{ email }}&nbsp;
    {% endfor %}
</h4>
{% endif %}
<h4>To:
    {% for recipient in recipients %}
    {{ recipient }}&nbsp;
    {% endfor %}
</h4>
<h4>Subject: {{subject}}</h4>
<div class="email-html" style="display: block;">
    {% autoescape off %}
    {{ html_message }}
    {% endautoescape %}
</div>
<div class="email-text" style="display: none;">
    <pre>{{ body }}</pre>
</div>
<hr />

</pre>
#### compose_control_buttons.hbs ####
<pre>
<div class="compose_control_buttons_container order-1">
    <input type="file" class="file_input notvisible pull-left" multiple />
    {{#if file_upload_enabled }}
    <a role="button" class="compose_control_button compose_upload_file fa fa-paperclip notdisplayed" aria-label="{{t 'Upload files' }}" tabindex=0 data-tippy-content="{{t 'Upload files' }}"></a>
    {{/if}}
    <a role="button" class="markdown_preview compose_control_button fa fa-eye" aria-label="{{t 'Preview' }}" tabindex=0 data-tippy-content="{{t 'Preview' }}"></a>
    <a role="button" class="undo_markdown_preview compose_control_button fa fa-edit" aria-label="{{t 'Write' }}" tabindex=0 style="display:none;" data-tippy-content="{{t 'Write' }}"></a>
    <a role="button" class="compose_control_button fa fa-video-camera video_link" aria-label="{{t 'Add video call' }}" tabindex=0 data-tippy-content="{{t 'Add video call' }}"></a>
    <a role="button" class="compose_control_button fa fa-smile-o emoji_map" aria-label="{{t 'Add emoji' }}" tabindex=0 data-tippy-content="{{t 'Add emoji' }}"></a>
    <a role="button" class="compose_control_button fa fa-clock-o time_pick" aria-label="{{t 'Add global time' }}" tabindex=0 data-tooltip-template-id="add-global-time-tooltip" data-tippy-maxWidth="none"></a>
    <a role="button" class="compose_control_button compose_gif_icon {{#unless giphy_enabled }} hide {{/unless}} zulip-icon zulip-icon-gif" aria-label="{{t 'Add GIF' }}" tabindex=0 data-tippy-content="{{t 'Add GIF' }}"></a>
    <div class="divider hide-sm">|</div>
    <div class="{{#if message_id}}hide-lg{{else}}hide-sm{{/if}}">
        {{> compose_control_buttons_in_popover}}
    </div>
    <a role="button" class="compose_control_button compose_draft_button hide-sm" tabindex=0 href="#drafts" data-tooltip-template-id="compose_draft_tooltip_template">
        {{t 'Drafts' }}
    </a>
    <template id="compose_draft_tooltip_template">
        {{t 'Drafts' }}
        {{tooltip_hotkey_hints "D"}}
    </template>
    <div class="compose_control_menu_wrapper" role="button" tabindex=0>
        <a class="compose_control_button zulip-icon zulip-icon-ellipsis-v-solid hide {{#if message_id}}show-lg{{else}}show-sm{{/if}} compose_control_menu" tabindex="-1" data-tippy-content="Compose actions"></a>
    </div>
</div>

</pre>
#### compose.hbs ####
<pre>
<div id="compose-content">
    {{!-- scroll to bottom button is not part of compose but
    helps us align it at various screens sizes with
    minimal css and no JS. We keep it `position: absolute` to prevent
    it changing compose box layout in any way. --}}
    <div id="scroll-to-bottom-button-container" aria-hidden="true">
        <div id="scroll-to-bottom-button-clickable-area" data-tooltip-template-id="scroll-to-bottom-button-tooltip-template">
            <div id="scroll-to-bottom-button">
                <i class="fa fa-chevron-down"></i>
            </div>
        </div>
        <template id="scroll-to-bottom-button-tooltip-template">
            {{t 'Scroll to bottom' }}
            {{tooltip_hotkey_hints "End"}}
        </template>
    </div>
    <div id="compose_controls" class="new-style">
        <div id="compose_buttons">
            <span class="new_message_button reply_button_container ">
                <button type="button" class="button small rounded compose_reply_button"
                  id="left_bar_compose_reply_button_big"
                  title="{{t 'Reply to selected message' }} (r)">
                    <span class="compose_reply_button_label">{{t 'Compose message' }}</span>
                </button>
            </span>
            <span class="new_message_button mobile_button_container">
                <button type="button" class="button small rounded compose_mobile_button"
                  id="left_bar_compose_mobile_button_big"
                  title="{{t 'New message' }} (c)">
                    <span>+</span>
                </button>
            </span>
            <span class="new_message_button stream_button_container">
                <button type="button" class="button small rounded compose_stream_button"
                  id="left_bar_compose_stream_button_big"
                  title="{{t 'New topic' }} (c)">
                    <span class="compose_stream_button_label">{{t 'New topic' }}</span>
                </button>
            </span>
            {{#unless embedded }}
            <span class="new_message_button private_button_container">
                <button type="button" class="button small rounded compose_private_button"
                  id="left_bar_compose_private_button_big"
                  title="{{t 'New direct message' }} (x)">
                    <span class="compose_private_button_label">{{t 'New direct message' }}</span>
                </button>
            </span>
            {{/unless}}
        </div>
    </div>
    <div class="message_comp">
        <div id="compose_banners"></div>
        <div class="composition-area">
            <form id="send_message_form" action="/json/messages" method="post">
                <div class="compose_table">
                    <div id="compose_top">
                        <div id="compose_top_right" class="order-2">
                            <button type="button" class="expand_composebox_button fa fa-chevron-up" aria-label="{{t 'Expand compose' }}" data-tippy-content="{{t 'Expand compose' }}"></button>
                            <button type="button" class="collapse_composebox_button fa fa-chevron-down" aria-label="{{t 'Collapse compose' }}" data-tippy-content="{{t 'Collapse compose' }}"></button>
                            <button type="button" class="close fa fa-times" id='compose_close' data-tooltip-template-id="compose_close_tooltip_template"></button>
                            <template id="compose_close_tooltip_template">
                                {{t 'Cancel compose' }}
                                {{tooltip_hotkey_hints "Esc"}}
                            </template>
                            <template id="compose_close_and_save_tooltip_template">
                                {{t 'Cancel compose and save draft' }}
                                {{tooltip_hotkey_hints "Esc"}}
                            </template>
                        </div>
                        <div id="stream-message" class="order-1">
                            <div class="stream-selection-header-colorblock message_header_stream left_part" tab-index="-1"></div>
                            <div class="right_part">
                                <span id="compose-lock-icon">
                                    <i class="fa fa-lock" title="{{t 'This is a private stream' }}" aria-hidden="true"></i>
                                </span>
                                <span id="compose-globe-icon">
                                    <i class="zulip-icon zulip-icon-globe" title="{{t 'This is a web-public stream' }}" aria-hidden="true"></i>
                                </span>
                                <a role="button" class="narrow_to_compose_recipients zulip-icon zulip-icon-arrow-left-circle order-1" data-tooltip-template-id="narrow_to_compose_recipients_tooltip" tabindex="0">
                                </a>
                                <input type="text" class="recipient_box" name="stream_message_recipient_stream" id="stream_message_recipient_stream" maxlength="{{ max_stream_name_length }}" value="" placeholder="{{t 'Stream' }}" autocomplete="off" tabindex="0" aria-label="{{t 'Stream' }}" />
                                <i class="fa fa-angle-right" aria-hidden="true"></i>
                                <input type="text" class="recipient_box" name="stream_message_recipient_topic" id="stream_message_recipient_topic" maxlength="{{ max_topic_length }}" value="" placeholder="{{t 'Topic' }}" autocomplete="off" tabindex="0" aria-label="{{t 'Topic' }}" />
                            </div>
                        </div>
                        <div id="private-message" class="order-1">
                            <div class="to_text">
                                <span>{{t 'To' }}:</span>
                            </div>
                            <div class="right_part">
                                <div class="pm_recipient">
                                    <a role="button" class="narrow_to_compose_recipients zulip-icon zulip-icon-arrow-left-circle order-1" data-tooltip-template-id="narrow_to_compose_recipients_tooltip" tabindex="0"></a>
                                    <div class="pill-container" data-before="{{t 'You and' }}">
                                        <div class="input" contenteditable="true" id="private_message_recipient" data-no-recipients-text="{{t 'Add one or more users' }}" data-some-recipients-text="{{t 'Add another user...' }}"></div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="messagebox-wrapper">
                        <div class="messagebox">
                            <textarea class="new_message_textarea" name="content" id='compose-textarea' placeholder="{{t 'Compose your message here' }}" tabindex="0" aria-label="{{t 'Compose your message here...' }}"></textarea>
                            <div class="scrolling_list preview_message_area" data-simplebar id="preview_message_area" style="display:none;">
                                <div class="markdown_preview_spinner"></div>
                                <div class="preview_content rendered_markdown"></div>
                            </div>
                            <div class="drag"></div>
                            <div id="below-compose-content">
                                <div class="compose_bottom_top_container">
                                    <div class="compose_right_float_container order-3">
                                        <button type="submit" id="compose-send-button" class="button small send_message animated-purple-button" title="{{t 'Send' }} (Ctrl + Enter)">
                                            <img class="loader" alt="" src="" />
                                            <span>{{t 'Send' }}</span>
                                        </button>
                                    </div>
                                    {{> compose_control_buttons }}
                                </div>
                                <div class="compose_bottom_bottom_container">
                                    <span id="compose_limit_indicator"></span>
                                    <div class="enter_sends">
                                        <span class="enter_sends_true">
                                            {{#tr}}
                                                <z-shortcut></z-shortcut> to send
                                                {{#*inline "z-shortcut"}}<kbd>Enter</kbd>{{/inline}}
                                            {{/tr}}
                                        </span>
                                        <span class="enter_sends_false">
                                            {{#tr}}
                                                <z-shortcut></z-shortcut> to send
                                                {{#*inline "z-shortcut"}}<kbd>Ctrl</kbd>+<kbd>Enter</kbd>{{/inline}}
                                            {{/tr}}
                                        </span>
                                        <i class="fa fa-caret-down" aria-hidden="true"></i>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </form>
        </div>
    </div>
</div>

<template id="add-global-time-tooltip">
    <div>
        <span>{{t "Add global time" }}</span><br/>
        <span class="tooltip-inner-content italic">{{t "Everyone sees global times in their own time zone." }}</span>
    </div>
</template>

</pre>
#### reset.html ####
<pre>
{% extends "zerver/portico_signup.html" %}

{% block title %}
<title>{{ _("Reset your password") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

<div class="flex new-style app portico-page">
    <div class="inline-block">
        <div class="lead">
            <h1 class="get-started">{{ _('Reset your password') }}</h1>
        </div>

        <div class="app-main forgot-password-container white-box new-style">

            <p>{{ _("Forgot your password? No problem, we'll send a link to reset your password to the email you signed up with.") }}</p>

            <form method="post" action="{{ url('password_reset') }}">
                {{ csrf_input }}
                <div class="new-style">
                    <div class="input-box horizontal">
                        <div class="inline-block relative">
                            <label for="id_email" class="">{{ _('Email') }}</label>
                            <input id="id_email" class="required" type="text" name="email"
                              value="{% if form.email.value() %}{{ form.email.value() }}{% endif %}"
                              maxlength="100" placeholder="{{ _("Enter your email address") }}" autofocus required />
                            {% if form.email.errors %}
                                {% for error in form.email.errors %}
                                <div class="alert alert-error">{{ error }}</div>
                                {% endfor %}
                            {% endif %}
                        </div>
                        <button type="submit">{{ _('Send reset link') }}</button>

                    </div>
                </div>
            </form>
            {% include 'zerver/include/back_to_login_component.html' %}
        </div>
    </div>
</div>


{% endblock %}

</pre>
#### billing_nav.html ####
<pre>
<nav class="portico-header">
    <div class="content">
        <a class="brand logo" href="{{ root_domain_uri }}">
            <svg role="img" aria-label="{{ _('Zulip') }}" xmlns="http://www.w3.org/2000/svg" viewBox="68.96 55.62 1742.12 450.43" height="25">
                <path fill="hsl(0, 0%, 100%)" d="M473.09 122.97c0 22.69-10.19 42.85-25.72 55.08L296.61 312.69c-2.8 2.4-6.44-1.47-4.42-4.7l55.3-110.72c1.55-3.1-.46-6.91-3.64-6.91H129.36c-33.22 0-60.4-30.32-60.4-67.37 0-37.06 27.18-67.37 60.4-67.37h283.33c33.22-.02 60.4 30.3 60.4 67.35zM129.36 506.05h283.33c33.22 0 60.4-30.32 60.4-67.37 0-37.06-27.18-67.37-60.4-67.37H198.2c-3.18 0-5.19-3.81-3.64-6.91l55.3-110.72c2.02-3.23-1.62-7.1-4.42-4.7L94.68 383.6c-15.53 12.22-25.72 32.39-25.72 55.08 0 37.05 27.18 67.37 60.4 67.37zm522.5-124.15l124.78-179.6v-1.56H663.52v-48.98h190.09v34.21L731.55 363.24v1.56h124.01v48.98h-203.7V381.9zm338.98-230.14V302.6c0 45.09 17.1 68.03 47.43 68.03 31.1 0 48.2-21.77 48.2-68.03V151.76h59.09V298.7c0 80.86-40.82 119.34-109.24 119.34-66.09 0-104.96-36.54-104.96-120.12V151.76h59.48zm244.91 0h59.48v212.25h104.18v49.76h-163.66V151.76zm297 0v262.01h-59.48V151.76h59.48zm90.18 3.5c18.27-3.11 43.93-5.44 80.08-5.44 36.54 0 62.59 7 80.08 20.99 16.72 13.22 27.99 34.99 27.99 60.64 0 25.66-8.55 47.43-24.1 62.2-20.21 19.05-50.15 27.6-85.13 27.6-7.77 0-14.77-.39-20.21-1.17v93.69h-58.7V155.26zm58.7 118.96c5.05 1.17 11.27 1.55 19.83 1.55 31.49 0 50.92-15.94 50.92-42.76 0-24.1-16.72-38.49-46.26-38.49-12.05 0-20.21 1.17-24.49 2.33v77.37z"/>
            </svg>
        </a>
    </div>
</nav>

</pre>
#### search_list_item.hbs ####
<pre>
<div class="search_list_item">
    <span>{{{ description_html }}}</span>
    {{#if is_person}}
    <span class="pill-container pill-container-btn">
        {{> input_pill user_pill_context}}
    </span>
    {{/if}}
</div>

</pre>
#### reset_confirm.html ####
<pre>
{% extends "zerver/portico_signup.html" %}
{% set entrypoint = "register" %}

{% block title %}
<title>{{ _("Set a new password") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

<div class="password-container flex full-page new-style">

    <!-- wrapper for flex content -->
    <div>
        <div class="get-started">
            <h1>{{ _('Set a new password.') }}</h1>
        </div>
        <div class="password-reset white-box">
            <!-- TODO: Ask about meta viewport 1:1 scaling -->

            {% if validlink %}
            <form method="post" id="password_reset" autocomplete="off">
                {{ csrf_input }}
                <div class="input-box" id="email-section">
                    <label for="id_email">{{ _("Email") }}</label>
                    <div>
                        <input type="text" name="name" placeholder='{{ form.user.delivery_email }}' disabled />
                    </div>
                </div>

                <div class="input-box password-div">
                    <label for="id_new_password1" class="">{{ _('Password') }}</label>
                    <input id="id_new_password1" class="required" type="password" name="new_password1" autocomplete="new-password"
                      value="{% if form.new_password1.value() %}{{ form.new_password1.value() }}{% endif %}"
                      maxlength="100"
                      data-min-length="{{password_min_length}}"
                      data-min-guesses="{{password_min_guesses}}" autofocus required />
                    <i class="fa fa-eye-slash password_visibility_toggle" role="button"></i>
                    {% if form.new_password1.errors %}
                        {% for error in form.new_password1.errors %}
                        <div class="alert alert-error">{{ error }}</div>
                        {% endfor %}
                    {% endif %}
                </div>
                <div class="input-box">
                    <div class="">
                        <div class="progress" id="pw_strength">
                            <div class="bar bar-danger" style="width: 10%;"></div>
                        </div>
                    </div>
                </div>
                <div class="input-box password-div">
                    <label for="id_new_password2" class="">{{ _('Confirm password') }}</label>
                    <input id="id_new_password2" class="required" type="password" name="new_password2" autocomplete="off"
                      value="{% if form.new_password2.value() %}{{ form.new_password2.value() }}{% endif %}"
                      maxlength="100" required />
                    <i class="fa fa-eye-slash password_visibility_toggle" role="button"></i>
                    {% if form.new_password2.errors %}
                        {% for error in form.new_password2.errors %}
                        <div class="alert alert-error">{{ error }}</div>
                        {% endfor %}
                    {% endif %}
                </div>

                <div class="input-box m-t-30">
                    <div class="centered-button">
                        <button type="submit" class="" value="Submit">Submit</button>
                    </div>
                </div>
            </form>

            {% else %}
            <p>{{ _('Sorry, the link you provided is invalid or has already been used.') }}</p>
            {% endif %}
        </div>
    </div>
</div>

{% endblock %}

</pre>
#### hotspot_overlay.hbs ####
<pre>
<div id="hotspot_{{name}}_overlay" class="hotspot overlay" data-overlay="hotspot_{{name}}_overlay">
    <div class="hotspot-popover">
        <div class="hotspot-popover-top">
            <h1 class="hotspot-title">{{title}}</h1>
        </div>
        <div class="hotspot-popover-content">
            <p class="hotspot-description">{{description}}</p>
        </div>
        <div class="hotspot-popover-bottom">
            <img class="hotspot-img" src="{{img}}" />
            <button class="hotspot-confirm">{{t 'Got it!' }}</button>
        </div>
    </div>
</div>

</pre>
#### topic_typeahead_hint.hbs ####
<pre>
<em>{{t 'Start a new topic or select one from the list.' }}</em>

</pre>
#### input_pill.hbs ####
<pre>
<div class='pill {{#if deactivated}} deactivated-pill {{/if}}' tabindex=0>
    {{#if has_image}}
    <img class="pill-image" src="{{img_src}}" />
    {{/if}}
    <span class="pill-value">{{ display_value }}
        {{~#if has_status~}}
        {{~> status_emoji status_emoji_info~}}
        {{~/if~}}
    </span>
    <div class="exit">
        <span aria-hidden="true">&times;</span>
    </div>
</div>

</pre>
#### invalid_email.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Invalid email") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

    <h3>{{ _('Invalid email') }}</h3>

    <p>{{ _('Hi there! Thank you for your interest in Zulip.') }}</p>

    {% if invalid_email %}
    <p>
        {% trans %}
        The email address you are trying to sign up with is not valid.
        Please sign up using a valid email address.
        {% endtrans %}
    </p>
    {% endif %}

    {% if closed_domain %}
    <p>
        {% trans %}
        The organization you are trying to join, {{ realm_name }},
        only allows users with email addresses within the
        organization. Please sign up using appropriate email address.
        {% endtrans %}
    </p>
    {% endif %}

    {% if disposable_emails_not_allowed %}
    <p>
        {% trans %}The organization you are trying to join,
        {{realm_name}}, does not allow signups using disposable email
        addresses. Please sign up using a real email address.
        {% endtrans %}
    </p>
    {% endif %}

    {% if email_contains_plus %}
    <p>
        {% trans %}The organization you are trying to join,
        {{realm_name}}, does not allow signups using emails
        that contains +. Please sign up using appropriate email address.
        {% endtrans %}
    </p>
    {% endif %}

{% endblock %}

</pre>
#### dev_env_email_access_details.html ####
<pre>
{% if development_environment %}
<div class="alert alert-info" style="display:inline-block;">
    In the development environment, outgoing emails are logged to
    <a href="/emails">/emails</a>.
</div>
{% endif %}

</pre>
#### message_hidden_dialog.hbs ####
<pre>
<p>
    <em>
        {{t "This message was hidden because you have muted the sender." }}
        <a class="reveal_hidden_message">{{t "Click here to reveal." }}</a>
    </em>
</p>

</pre>
#### loader.hbs ####
<pre>
<svg width='100%' height='100%' xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" preserveAspectRatio="xMidYMid" class="uil-ring">
    <rect x="0" y="0" width="100" height="100" fill="none" class="bk"></rect>
    <defs>
        <filter id="uil-ring-shadow-{{ container_id }}" x="-100%" y="-100%" width="300%" height="300%">
            <feOffset result="offOut" in="SourceGraphic" dx="0" dy="0"></feOffset>
            <feGaussianBlur result="blurOut" in="offOut" stdDeviation="0"></feGaussianBlur>
            <feBlend in="SourceGraphic" in2="blurOut" mode="normal"></feBlend>
        </filter>
    </defs>
    <path d="M10,50c0,0,0,0.5,0.1,1.4c0,0.5,0.1,1,0.2,1.7c0,0.3,0.1,0.7,0.1,1.1c0.1,0.4,0.1,0.8,0.2,1.2c0.2,0.8,0.3,1.8,0.5,2.8 c0.3,1,0.6,2.1,0.9,3.2c0.3,1.1,0.9,2.3,1.4,3.5c0.5,1.2,1.2,2.4,1.8,3.7c0.3,0.6,0.8,1.2,1.2,1.9c0.4,0.6,0.8,1.3,1.3,1.9 c1,1.2,1.9,2.6,3.1,3.7c2.2,2.5,5,4.7,7.9,6.7c3,2,6.5,3.4,10.1,4.6c3.6,1.1,7.5,1.5,11.2,1.6c4-0.1,7.7-0.6,11.3-1.6 c3.6-1.2,7-2.6,10-4.6c3-2,5.8-4.2,7.9-6.7c1.2-1.2,2.1-2.5,3.1-3.7c0.5-0.6,0.9-1.3,1.3-1.9c0.4-0.6,0.8-1.3,1.2-1.9 c0.6-1.3,1.3-2.5,1.8-3.7c0.5-1.2,1-2.4,1.4-3.5c0.3-1.1,0.6-2.2,0.9-3.2c0.2-1,0.4-1.9,0.5-2.8c0.1-0.4,0.1-0.8,0.2-1.2 c0-0.4,0.1-0.7,0.1-1.1c0.1-0.7,0.1-1.2,0.2-1.7C90,50.5,90,50,90,50s0,0.5,0,1.4c0,0.5,0,1,0,1.7c0,0.3,0,0.7,0,1.1 c0,0.4-0.1,0.8-0.1,1.2c-0.1,0.9-0.2,1.8-0.4,2.8c-0.2,1-0.5,2.1-0.7,3.3c-0.3,1.2-0.8,2.4-1.2,3.7c-0.2,0.7-0.5,1.3-0.8,1.9 c-0.3,0.7-0.6,1.3-0.9,2c-0.3,0.7-0.7,1.3-1.1,2c-0.4,0.7-0.7,1.4-1.2,2c-1,1.3-1.9,2.7-3.1,4c-2.2,2.7-5,5-8.1,7.1 c-0.8,0.5-1.6,1-2.4,1.5c-0.8,0.5-1.7,0.9-2.6,1.3L66,87.7l-1.4,0.5c-0.9,0.3-1.8,0.7-2.8,1c-3.8,1.1-7.9,1.7-11.8,1.8L47,90.8 c-1,0-2-0.2-3-0.3l-1.5-0.2l-0.7-0.1L41.1,90c-1-0.3-1.9-0.5-2.9-0.7c-0.9-0.3-1.9-0.7-2.8-1L34,87.7l-1.3-0.6 c-0.9-0.4-1.8-0.8-2.6-1.3c-0.8-0.5-1.6-1-2.4-1.5c-3.1-2.1-5.9-4.5-8.1-7.1c-1.2-1.2-2.1-2.7-3.1-4c-0.5-0.6-0.8-1.4-1.2-2 c-0.4-0.7-0.8-1.3-1.1-2c-0.3-0.7-0.6-1.3-0.9-2c-0.3-0.7-0.6-1.3-0.8-1.9c-0.4-1.3-0.9-2.5-1.2-3.7c-0.3-1.2-0.5-2.3-0.7-3.3 c-0.2-1-0.3-2-0.4-2.8c-0.1-0.4-0.1-0.8-0.1-1.2c0-0.4,0-0.7,0-1.1c0-0.7,0-1.2,0-1.7C10,50.5,10,50,10,50z" fill="#444" filter="url(#uil-ring-shadow-{{ container_id }})">
        <animateTransform attributeName="transform" type="rotate" from="0 50 50" to="360 50 50" repeatCount="indefinite" dur="1s"></animateTransform>
    </path>
</svg>

</pre>
#### message_reactions.hbs ####
<pre>
{{#each this/msg/message_reactions}}
    {{> message_reaction}}
{{/each}}
<div class="reaction_button" data-tippy-content="{{t 'Add emoji reaction' }}" aria-label="{{t 'Add emoji reaction' }} (:)">
    <i class="fa fa-smile-o" role="button" aria-haspopup="true" tabindex="0" aria-label="{{t 'Add emoji reaction' }} (:)"></i>
    <div class="message_reaction_count">+</div>
</div>

</pre>
#### realm_creation_link_invalid.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Organization creation link expired or invalid") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<div class="error_page">
    <div class="container">
        <div class="row-fluid">
            <img class="hourglass-img" src="{{ static('images/errors/timeout_hourglass.png') }}" alt=""/>
            <div class="errorbox">
                <div class="errorcontent">
                    <h1 class="lead">{{ _("Organization creation link expired or invalid") }}</h1>
                    <p>
                        {% trans %}
                        Unfortunately, this is not a valid link for creating an organization. Please <a href="/new/">obtain a new link</a> and try again.
                        {% endtrans %}
                    </p>
                </div>
            </div>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### unsubscribe_success.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Email settings updated") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

<div class="app portico-page">
    <div class="app-main portico-page-container center-block flex full-page new-style">
        <div class="inline-block">

            <div class="get-started">
                <h1>{{ _("Email settings updated") }}</h1>
            </div>

            <div class="white-box">
                <p>
                    {% trans %}
                    You've successfully unsubscribed from Zulip {{ subscription_type }} emails.
                    {% endtrans %}
                </p>

                <p>
                    {% trans %}
                    You can undo this change or review your
                    preferences in your
                    <a href="{{ realm_uri }}/#settings/notifications">Zulip notification
                    settings</a>.
                    {% endtrans %}
                </p>
            </div>
        </div>
    </div>
</div>

{% endblock %}

</pre>
#### dialog_change_password.hbs ####
<pre>
<form id="change_password_container">
    <div class="field password-div">
        <label for="old_password" class="title">{{t "Old password" }}</label>
        <input type="password" autocomplete="off" name="old_password" id="old_password" class="w-200 inline-block modal_text_input" value="" />
        <i class="fa fa-eye-slash password_visibility_toggle tippy-zulip-tooltip" role="button"></i>
        <div class="settings-forgot-password">
            <a href="/accounts/password/reset/" class="sea-green" target="_blank" rel="noopener noreferrer">{{t "Forgot it?" }}</a>
        </div>
    </div>
    <div class="field password-div">
        <label for="new_password" class="title">{{t "New password" }}</label>
        <input type="password" autocomplete="new-password" name="new_password" id="new_password" class="w-200 inline-block modal_text_input" value=""
          data-min-length="{{password_min_length}}" data-min-guesses="{{password_min_guesses}}" />
        <i class="fa fa-eye-slash password_visibility_toggle tippy-zulip-tooltip" role="button"></i>
        <div class="progress inline-block" id="pw_strength">
            <div class="bar bar-danger fade" style="width: 10%;"></div>
        </div>
    </div>
</form>

</pre>
#### invite_user_modal.hbs ####
<pre>
<form id="invite-user-form">{{ csrf_input }}
    {{#if development_environment}}
    <div class="alert" id="dev_env_msg"></div>
    {{/if}}
    <div class="input-group">
        <label for="invitee_emails">{{t "Emails (one on each line or comma-separated)" }}</label>
        <textarea rows="2" id="invitee_emails" name="invitee_emails" class="invitee_emails" placeholder="{{t 'One or more email addresses...' }}"></textarea>
        {{#if is_admin}}
        <div id="invite-method-choice">
            {{t "or" }} <a role="button" tabindex="0" id="generate_multiuse_invite_button">{{t "Generate invite link" }}</a>
        </div>
        <div id="multiuse_radio_section" class="new-style">
            <label class="checkbox display-block" for="generate_multiuse_invite_radio">
                <input type="checkbox" name="generate_multiuse_invite_radio" id="generate_multiuse_invite_radio"/>
                <span></span>
                {{t "Generate invite link" }}
            </label>
        </div>
        {{/if}}
    </div>
    <div class="input-group">
        <label for="expires_in">{{t "Invitation expires after" }}</label>
        <select id="expires_in" class="invite-expires-in bootstrap-focus-style">
            {{#each expires_in_options}}
                <option {{#if this.default }}selected{{/if}} name="expires_in" value="{{this.value}}">{{this.description}}</option>
            {{/each}}
        </select>
        <p id="expires_on"></p>
        <div id="custom-invite-expiration-time" class="dependent-settings-block">
            <label for="expires_in">{{t "Custom time" }}</label>
            <input type="text" autocomplete="off" name="custom-expiration-time" id="custom-expiration-time-input" class="custom-expiration-time inline-block" value="{{time_input}}" maxlength="3"/>
            <select class="custom-expiration-time bootstrap-focus-style" id="custom-expiration-time-unit">
                {{#each time_choices}}
                    <option name="custom_time_choice" class="custom_time_choice" value="{{this}}">{{this}}</option>
                {{/each}}
            </select>
            <p id="custom_expires_on"></p>
        </div>
    </div>
    <div class="input-group">
        <label for="invite_as">{{t "User(s) join as" }}
            {{> help_link_widget link="/help/roles-and-permissions" }}
        </label>
        <select id="invite_as" class="invite-as bootstrap-focus-style">
            <option name="invite_as" value="{{ invite_as_options.guest.code }}">{{t "Guests" }}</option>
            <option name="invite_as" selected="selected" value="{{ invite_as_options.member.code }}">{{t "Members" }}</option>
            {{#if is_admin}}
            <option name="invite_as" value="{{ invite_as_options.moderator.code }}">{{t "Moderators" }}</option>
            <option name="invite_as" value="{{ invite_as_options.admin.code }}">{{t "Organization administrators" }}</option>
            {{/if}}
            {{#if is_owner}}
            <option name="invite_as" value="{{ invite_as_options.owner.code }}">{{t "Organization owners" }}</option>
            {{/if}}
        </select>
    </div>
    <div>
        <label>{{t "Streams they should join" }}</label>
        <div id="streams_to_add">
            <div class="invite-stream-controls">
                <button class="btn btn-link" type="button" id="invite_check_all_button">{{t "Check all" }}</button> |
                <button class="btn btn-link" type="button" id="invite_uncheck_all_button">{{t "Uncheck all" }}</button>
            </div>
            <div id="invite-stream-checkboxes" class="new-style">
                {{#each streams}}

                    <label class="checkbox display-block">
                        <input type="checkbox" name="stream" value="{{stream_id}}"
                          {{#if default_stream}}checked="checked"{{/if}} />
                        <span></span>
                        {{#if (or invite_only is_web_public)}} {{>stream_privacy}} {{name}}
                        {{else}}
                        #{{name}}
                        {{/if}}
                        {{#if (eq name ../notifications_stream)}}
                        <i>({{t 'Receives new stream announcements' }})</i>
                        {{/if}}
                    </label>
                {{/each}}
            </div>
        </div>
    </div>
</form>

</pre>
#### inline_decorated_stream_name.hbs ####
<pre>
{{! This controls whether the swatch next to streams in the left sidebar has a lock icon. }}
{{#if stream.invite_only }}
<i class="fa fa-lock stream-privacy-type-icon" aria-hidden="true"></i>{{stream.name ~}}
{{ else if stream.is_web_public }}
<i class="zulip-icon zulip-icon-globe stream-privacy-type-icon" aria-hidden="true"></i>{{stream.name ~}}
{{ else }}
<span class="hashtag stream-privacy-type-icon"></span>{{stream.name ~}}
{{/if}}

</pre>
#### lightbox_overlay.hbs ####
<pre>
<div id="lightbox_overlay" class="overlay new-style" data-overlay="lightbox" data-noclose="false">
    <div class="image-info-wrapper">
        <div class="image-description">
            <div class="title"></div>
            <div class="user"></div>
        </div>
        <div class="image-actions">
            <a class="button small lightbox-zoom-reset disabled">{{t "Reset zoom" }}</a>
            <a class="button small open" rel="noopener noreferrer" target="_blank">{{t "Open" }}</a>
            <a class="button small download" download>{{t "Download" }}</a>
        </div>
        <div class="exit" aria-label="{{t 'Close' }}"><span aria-hidden="true">x</span></div>
    </div>

    <div class="image-preview no-select">
        <div class="zoom-element no-select"></div>
    </div>
    <div class="player-container"></div>
    <div class="center">
        <div class="arrow no-select" data-direction="prev">&lt;</div>
        <div class="image-list"></div>
        <div class="arrow no-select" data-direction="next">&gt;</div>
    </div>
</div>

</pre>
#### more_topics_spinner.hbs ####
<pre>
<li class="searching-for-more-topics">
    <img src="../images/loading/loading-ellipsis.svg" alt="" />
</li>

</pre>
#### unsupported_browser.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Unsupported browser") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

<div class="error_page unsupported_browser_page">
    <div class="container">
        <div class="row-fluid">
            <img src="{{ static('images/errors/400art.svg') }}" alt=""/>
            <div class="errorbox config-error">
                <div class="errorcontent">
                    <h1 class="lead">{{ _('Unsupported browser') }}</h1>
                    <p>
                        {% trans %}
                        {{ browser_name }} is not supported by Zulip.
                        {% endtrans %}
                    </p>
                    <p>
                        {% trans supported_browsers_page_link="/help/supported-browsers" %}
                        Zulip supports <a href="{{ supported_browsers_page_link }}">modern browsers</a>
                        like Firefox, Chrome, and Edge.
                        {% endtrans %}
                    </p>
                    <p>
                        {% trans apps_page_link="https://zulip.com/apps/" %}
                        You can also use the <a href="{{ apps_page_link }}">Zulip desktop app</a>.
                        {% endtrans %}
                    </p>
                </div>

            </div>
        </div>
    </div>
</div>

{% endblock %}

</pre>
#### unsubscribe_link_error.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Error unsubscribing email") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

<h1>{% trans %}Unknown email unsubscribe request{% endtrans %}</h1>

<p>
    {% trans %}Hi there! It looks like you tried to unsubscribe from something,
    but we don't recognize the URL.{% endtrans %}
</p>

<p>{% trans %}Please double-check that you have the full URL and try again, or <a href="mailto:{{ support_email }}">email us</a> and we'll get this squared away!{% endtrans %}</p>

{% endblock %}

</pre>
#### message_edit_form.hbs ####
<pre>
{{! Client-side Handlebars template for rendering the message edit form. }}

<form id="edit_form_{{message_id}}" class="new-style">
    <div class="banners"></div>
    <div class="edit-controls">
        {{> copy_message_button message_id=this.message_id}}
        <textarea class="message_edit_content" maxlength="{{ max_message_length }}">{{content}}</textarea>
        <div class="scrolling_list preview_message_area" id="preview_message_area_{{message_id}}" style="display:none;">
            <div class="markdown_preview_spinner"></div>
            <div class="preview_content rendered_markdown"></div>
        </div>
    </div>
    <div class="action-buttons">
        <div class="message_edit_spinner"></div>
        <div class="controls edit-controls">
            {{#if is_editable}}
                <div class="btn-wrapper inline-block">
                    <button type="button" class="button small rounded sea-green message_edit_save">
                        <img class="loader" alt="" src="" />
                        <span>{{t "Save" }}</span>
                    </button>
                </div>
                <div class="btn-wrapper inline-block">
                    <button type="button" class="button small rounded message_edit_cancel">{{t "Cancel" }}</button>
                </div>
                {{#if is_editable}}
                <div class="message-edit-feature-group">
                    {{> compose_control_buttons }}
                </div>
                {{/if}}
            {{else}}
                <button type="button" class="button small rounded message_edit_close">{{t "Close" }}</button>
            {{/if}}
            {{#if is_editable}}
            <div class="message-edit-timer">
                <span class="message_edit_countdown_timer"></span>
                <span>
                    <i id="message_edit_tooltip" class="tippy-zulip-tooltip message_edit_tooltip fa fa-question-circle" aria-hidden="true"
                      data-tippy-content="{{t 'This organization is configured to restrict editing of message content to {minutes_to_edit} minutes after it is sent.' }}">
                    </i>
                </span>
            </div>
            {{/if}}
        </div>
    </div>
    <div class="alert alert-error edit_error hide"></div>
</form>

</pre>
#### more_topics.hbs ####
<pre>
<li class="topic-list-item show-more-topics bottom_left_row {{#unless more_topics_unreads}}zero-topic-unreads{{/unless}}">
    <span class='topic-box'>
        <a class="topic-name" tabindex="0">{{t "more topics" }}</a>
        {{#if more_topics_have_unread_mention_messages}}
            <span class="unread_mention_info">
                @
            </span>
        {{/if}}
        <span class="unread_count {{#unless more_topics_unreads}}zero_count{{/unless}}">
            {{more_topics_unreads}}
        </span>
    </span>
</li>

</pre>
#### mark_as_read_turned_off_banner.hbs ####
<pre>
<p id="mark_as_read_turned_off_content">
    {{t 'To preserve your reading state, this view does not mark messages as read.' }}
</p>
<div id="mark_as_read_controls">
    <button id="mark_view_read" class="btn btn-warning" title="{{t 'Mark as read' }}">
        {{t 'Mark as read' }}
    </button>
</div>
<button type="button" id="mark_as_read_close" class="close">×</button>

</pre>
#### favicon.svg.hbs ####
<pre>
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16">
    <style>
        @font-face {
        font-family: 'Source Sans 3';
        font-style: normal;
        font-weight: 700;
        src: url({{{favicon_font_url}}}) format('truetype');
        }
    </style>
    <linearGradient id="a" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0" stop-color="#50adff" />
        <stop offset="1" stop-color="#7877fc" />
    </linearGradient>
    <path d="M688.52 150.67c0 33.91-15.23 64.04-38.44 82.31L424.79 434.17c-4.18 3.59-9.62-2.19-6.61-7.03l82.64-165.46c2.31-4.63-.69-10.33-5.44-10.33H174.86c-49.64 0-90.26-45.31-90.26-100.68 0-55.37 40.62-100.68 90.26-100.68h423.39c49.65 0 90.27 45.31 90.27 100.68zM174.86 723.13h423.39c49.64 0 90.26-45.31 90.26-100.68 0-55.37-40.62-100.68-90.26-100.68H277.73c-4.75 0-7.76-5.7-5.44-10.33l82.64-165.46c3.01-4.83-2.42-10.62-6.61-7.03L123.04 540.14c-23.21 18.27-38.44 48.4-38.44 82.31 0 55.37 40.62 100.68 90.26 100.68z" fill="url(#a)" transform="translate(8 8) scale(0.023769201057729446) translate(-386.56 -386.56)" />
    <text x="15" y="15" text-anchor="end"
      font-family="'Source Sans 3'" font-weight="bold" letter-spacing="-0.5"
      fill="white" stroke="white" stroke-width="2" stroke-linejoin="round" opacity=".5"
      {{#if count_long}}font-size="9" textLength="14" lengthAdjust="spacingAndGlyphs"{{else}}font-size="11"{{/if}}>
        {{count}}
    </text>
    <text x="15" y="15" text-anchor="end"
      font-family="'Source Sans 3'" font-weight="bold" letter-spacing="-0.5"
      {{#if count_long}}font-size="9" textLength="14" lengthAdjust="spacingAndGlyphs"{{else}}font-size="11"{{/if}}>
        {{count}}
    </text>
    {{#if have_pm}}
    <circle cx="14" cy="4" r="2" fill="#f00" />
    {{/if}}
</svg>

</pre>
#### search_operators.hbs ####
<pre>
<div class="overlay-modal hide" id="search-operators" tabindex="-1" role="dialog" aria-label="{{t 'Search filters' }}">
    <div class="modal-body" data-simplebar data-simplebar-auto-hide="false">
        <div id="operators-instructions">
            <table class="table table-striped table-condensed table-rounded table-bordered help-table">
                <thead>
                    <tr>
                        <th>{{t "Filter" }}</th>
                        <th>{{t "Effect" }}</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td class="operator"><span class="operator_value">keyword</span></td>
                        <td class="definition">
                            {{#tr}}
                                Search for <z-value></z-value> in the topic or message content.
                                {{#*inline "z-value"}}<span class="operator_value">keyword</span>{{/inline}}
                            {{/tr}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">stream:<span class="operator_value">stream</span></td>
                        <td class="definition">
                            {{#tr}}
                                Narrow to messages on stream <z-value></z-value>.
                                {{#*inline "z-value"}}<span class="operator_value">stream</span>{{/inline}}
                            {{/tr}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">topic:<span class="operator_value">topic</span></td>
                        <td class="definition">
                            {{#tr}}
                                Narrow to messages with topic <z-value></z-value>.
                                {{#*inline "z-value"}}<span class="operator_value">topic</span>{{/inline}}
                            {{/tr}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">is:private</td>
                        <td class="definition">
                            {{t 'Narrow to direct messages.'}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">pm-with:<span class="operator_value">user</span></td>
                        <td class="definition">
                            {{#tr}}
                                Narrow to direct messages with <z-value></z-value>.
                                {{#*inline "z-value"}}<span class="operator_value">user</span>{{/inline}}
                            {{/tr}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">group-pm-with:<span class="operator_value">user</span></td>
                        <td class="definition">
                            {{#tr}}
                                Narrow to group direct messages with <z-value></z-value>.
                                {{#*inline "z-value"}}<span class="operator_value">user</span>{{/inline}}
                            {{/tr}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">streams:public</td>
                        <td class="definition">
                            {{t 'Search all public streams in the organization.'}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">sender:<span class="operator_value">user</span></td>
                        <td class="definition">
                            {{#tr}}
                                Narrow to messages sent by <z-value></z-value>.
                                {{#*inline "z-value"}}<span class="operator_value">user</span>{{/inline}}
                            {{/tr}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">sender:me</td>
                        <td class="definition">
                            {{t 'Narrow to messages sent by you.'}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">has:link</td>
                        <td class="definition">
                            {{t 'Narrow to messages containing links.'}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">has:attachment</td>
                        <td class="definition">
                            {{t 'Narrow to messages containing uploads.'}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">has:image</td>
                        <td class="definition">
                            {{t 'Narrow to messages containing images.'}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">is:alerted</td>
                        <td class="definition">
                            {{t 'Narrow to messages with alert words.'}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">is:mentioned</td>
                        <td class="definition">
                            {{t 'Narrow to messages that mention you.'}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">is:starred</td>
                        <td class="definition">
                            {{t 'Narrow to starred messages.'}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">is:resolved</td>
                        <td class="definition">
                            {{t 'Narrow to messages in resolved topics.'}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">is:unread</td>
                        <td class="definition">
                            {{t 'Narrow to unread messages.'}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">near:<span class="operator_value">id</span></td>
                        <td class="definition">
                            {{#tr}}
                                Center the view around message ID <z-value></z-value>.
                                {{#*inline "z-value"}}<span class="operator_value">id</span>{{/inline}}
                            {{/tr}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">id:<span class="operator_value">id</span></td>
                        <td class="definition">
                            {{#tr}}
                                Narrow to just message ID <z-value></z-value>.
                                {{#*inline "z-value"}}<span class="operator_value">id</span>{{/inline}}
                            {{/tr}}
                        </td>
                    </tr>
                    <tr>
                        <td class="operator">-topic:<span class="operator_value">topic</span></td>
                        <td class="definition">
                            {{#tr}}
                                Exclude messages with topic <z-value></z-value>.
                                {{#*inline "z-value"}}<span class="operator_value">topic</span>{{/inline}}
                            {{/tr}}
                        </td>
                    </tr>
                </tbody>
            </table>
            <p>{{t "You can combine search filters as needed." }}</p>
            <hr />
            <a href="help/search-for-messages#search-filters" target="_blank" rel="noopener noreferrer">{{t "Detailed search filters documentation" }}</a>
        </div>
    </div>
</div>

</pre>
#### buddy_list_tooltip_content.hbs ####
<pre>
<div class="buddy_list_tooltip_content">
    <span>
        {{first_line}}
        {{#if show_you}}
        <span class="my_user_status">{{t "(you)" }}</span>
        {{/if}}
    </span>
    {{#if second_line}}
    <br /><span class="tooltip-inner-content">{{second_line}}</span>
    {{/if}}
    {{#if third_line}}
    <br /><span class="tooltip-inner-content">{{third_line}}</span>
    {{/if}}
</div>

</pre>
#### copy_to_clipboard_svg.hbs ####
<pre>
<svg height="20" width="16" viewBox="0 0 1000 1000" xmlns="http://www.w3.org/2000/svg" id="clipboard_image">
    <path fill="#777" d="M128 768h256v64H128v-64z m320-384H128v64h320v-64z m128 192V448L384 640l192 192V704h320V576H576z m-288-64H128v64h160v-64zM128 704h160v-64H128v64z m576 64h64v128c-1 18-7 33-19 45s-27 18-45 19H64c-35 0-64-29-64-64V192c0-35 29-64 64-64h192C256 57 313 0 384 0s128 57 128 128h192c35 0 64 29 64 64v320h-64V320H64v576h640V768zM128 256h512c0-35-29-64-64-64h-64c-35 0-64-29-64-64s-29-64-64-64-64 29-64 64-29 64-64 64h-64c-35 0-64 29-64 64z" />
</svg>

</pre>
#### more_pms.hbs ####
<pre>
<li id="show_more_private_messages" class="pm-list-item bottom_left_row {{#unless more_conversations_unread_count}}zero-pm-unreads{{/unless}}">
    <span>
        <a class="pm-name" tabindex="0">{{t "more conversations" }}</a>
        <span class="unread_count {{#unless more_conversations_unread_count}}zero_count{{/unless}}">
            {{more_conversations_unread_count}}
        </span>
    </span>
</li>

</pre>
#### gradients.html ####
<pre>
<div class="gradients">
    <div class="gradient pattern"></div>
    <div class="gradient sunburst"></div>
    <div class="gradient dark-blue"></div>
    <div class="gradient green"></div>
    <div class="gradient blue"></div>
    <div class="gradient white-fade"></div>
</div>

</pre>
#### realm_reactivation.html ####
<pre>
{% extends "zerver/portico_signup.html" %}

{% block title %}
<title>{{ _("Organization successfully reactivated") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<div class="app portico-page">
    <div class="app-main portico-page-container center-block flex full-page account-creation new-style">
        <div class="inline-block">

            <div class="get-started">
                <h1>{{ _("Your organization has been successfully reactivated.") }}</h1>
            </div>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### edit_content_button.hbs ####
<pre>
{{#if is_content_editable}}
<i class="fa fa-pencil edit_content_button edit_message_button" role="button" tabindex="0" aria-label="{{t 'Edit message' }} (e)"></i>
{{else if can_move_message}}
<i class="fa fa-arrows move_message_button edit_message_button" role="button" tabindex="0" aria-label="{{t 'Move message' }} (m)"></i>
{{else}}
<i class="fa fa-file-code-o view_source_button edit_message_button" role="button" tabindex="0" aria-label="{{t 'View message source' }} (e)" data-message-id="{{msg_id}}"></i>
{{/if}}

</pre>
#### emoji_popover.hbs ####
<pre>
<div class="popover {{class}}">
    <div class="arrow"></div>
    <div class="popover-content">
        <div></div>
    </div>
    <div class="emoji-showcase-container"></div>
</div>

</pre>
#### move_topic_to_stream.hbs ####
<pre>
{{#unless from_message_actions_popover}}
<p>{{#tr}}Move all messages in <strong>{topic_name}</strong>{{/tr}} to:</p>
{{/unless}}
<form class="new-style" id="move_topic_form">
    <p>{{t "Select a stream below or change topic name." }}</p>
    <div class="topic_stream_edit_header">
        <div class="stream_header_colorblock"></div>
        <div class="move-topic-dropdown">
            {{> settings/dropdown_list_widget
              widget_name="select_stream"
              list_placeholder=(t 'Filter streams')}}
        </div>
        <i class="fa fa-angle-right" aria-hidden="true"></i>
        <input name="new_topic_name" type="text" class="inline_topic_edit modal_text_input" autocomplete="off" value="{{topic_name}}" {{#if disable_topic_input}}disabled{{/if}} />
        <input name="old_topic_name" type="hidden" class="inline_topic_edit" value="{{topic_name}}" />
        <input name="current_stream_id" type="hidden" value="{{current_stream_id}}" />
        {{#if from_message_actions_popover}}
        <select class="message_edit_topic_propagate modal_select bootstrap-focus-style">
            <option value="change_one"> {{t "Move only this message" }}</option>
            <option selected="selected" value="change_later"> {{t "Move this and all following messages in this topic" }}</option>
            <option value="change_all"> {{t "Move all messages in this topic" }}</option>
        </select>
        {{/if}}
        <div class="topic_move_breadcrumb_messages">
            <label class="checkbox">
                <input class="send_notification_to_new_thread" name="send_notification_to_new_thread" type="checkbox" {{#if notify_new_thread}}checked="checked"{{/if}} />
                <span></span>
                {{t "Send automated notice to new topic" }}
            </label>
            <label class="checkbox">
                <input class="send_notification_to_old_thread" name="send_notification_to_old_thread" type="checkbox" {{#if notify_old_thread}}checked="checked"{{/if}} />
                <span></span>
                {{t "Send automated notice to old topic" }}
            </label>
        </div>
    </div>
</form>

</pre>
#### copy_invite_link.hbs ####
<pre>
{{t "Link:" }}
<a href="{{ invite_link }}" id="multiuse_invite_link">{{ invite_link }}</a>
&nbsp;
<a class="btn pull-right copy_button_base tippy-zulip-tooltip" data-tippy-content="{{t 'Copy link' }}" aria-label="{{t 'Copy link' }}"
  id='copy_generated_invite_link' data-clipboard-text="{{ invite_link }}">
    {{> copy_to_clipboard_svg }}
</a>

</pre>
#### muted_user_ui_row.hbs ####
<pre>
{{#with muted_user}}
<tr data-user-id="{{user_id}}" data-user-name="{{user_name}}" data-date-muted="{{date_muted_str}}">
    <td>{{user_name}}</td>
    <td>{{date_muted_str}}</td>
    <td class="actions">
        <span><a class="settings-unmute-user">{{t "Unmute" }}</a></span>
    </td>
</tr>
{{/with}}

</pre>
#### right_sidebar.hbs ####
<pre>
<div class="right-sidebar" id="right-sidebar" role="navigation">
    <div class="right-sidebar-items">
        <div id="user-list">
            <div id="userlist-header">
                <h4 class='sidebar-title' data-tooltip-template-id="search-people-tooltip-template"
                  id='userlist-title'>
                    {{t 'USERS' }}
                </h4>
                <i id="user_filter_icon" class="fa fa-search"
                  aria-hidden="true" aria-label="{{t 'Search people' }}"
                  data-tooltip-template-id="search-people-tooltip-template">
                </i>
            </div>
            <template id="search-people-tooltip-template">
                {{t 'Search people' }}
                {{tooltip_hotkey_hints "W"}}
            </template>
            <div class="input-append notdisplayed" id="user_search_section">
                <input class="user-list-filter home-page-input" type="text" autocomplete="off" placeholder="{{t 'Search people' }}" />
                <button type="button" class="btn clear_search_button" id="clear_search_people_button">
                    <i class="fa fa-remove" aria-hidden="true"></i>
                </button>
            </div>
            <div id="buddy_list_wrapper" class="scrolling_list" data-simplebar>
                <ul id="user_presences" class="filters required-text" data-empty="{{t 'No matching users.' }}"></ul>
                <div id="buddy_list_wrapper_padding"></div>
            </div>
        </div>
        <div class="right-sidebar-shortcuts">
            {{#if can_invite_others_to_realm}}
            <a class="invite-user-link" role="button"><i class="fa fa-user-plus" aria-hidden="true"></i>{{t 'Invite more users' }}</a>
            {{/if}}
            <a id="sidebar-keyboard-shortcuts" data-overlay-trigger="keyboard-shortcuts" class="hidden-for-spectators">
                <i class="fa fa-keyboard-o fa-2x tippy-zulip-tooltip" id="keyboard-icon" data-tooltip-template-id="keyboard-icon-tooltip-template"></i>
                <template id="keyboard-icon-tooltip-template">
                    {{t 'Keyboard shortcuts' }}
                    {{tooltip_hotkey_hints "?"}}
                </template>
            </a>
            <div class="only-visible-for-spectators">
                <div class="realm-description">
                    <div class="rendered_markdown">{{rendered_markdown realm_rendered_description }}</div>
                </div>
            </div>
        </div>
    </div>
</div>

</pre>
#### portico-header-dropdown.html ####
<pre>
<div class="dropdown">
    <div class="dropdown-pill">
        <img class="header-realm-icon" src="{{ realm_icon }}" alt="{{ _('Go to Zulip') }}"/>
        <div class="realm-name">{{ realm_name }}<i class="fa fa-chevron-down"></i></div>
    </div>
    <ul>
        <li>
            <a href="/">
                <i class="fa fa-home"></i>
                Go to app
            </a>
        </li>
        <li class="logout">
            <div class="hidden">
                <form id="logout_form" action="/accounts/logout/" method="POST">{{ csrf_input }}
                </form>
            </div>
            <a href="#logout">
                <i class="fa fa-sign-out"></i>
                Log out
            </a>
        </li>
    </ul>
</div>

</pre>
#### login_to_access.hbs ####
<pre>
<div class="micromodal" id="login_to_access_modal" aria-hidden="true">
    <div class="modal__overlay" tabindex="-1">
        <div class="modal__container" role="dialog" aria-modal="true" aria-labelledby="login_to_access_modal_label">
            <header class="modal__header">
                <h1 class="modal__title" id="login_to_access_modal_label">
                    {{t "Join {realm_name}" }}
                </h1>
                <button class="modal__close" aria-label="{{t 'Close modal' }}" data-micromodal-close></button>
            </header>
            <main class="modal__content">
                {{#if empty_narrow}}
                <p>
                    {{#tr}}
                        This is not a <z-link>publicly accessible</z-link> conversation.
                        {{#*inline "z-link"}}<a target="_blank" rel="noopener noreferrer" href="/help/public-access-option">{{> @partial-block}}</a>{{/inline}}
                    {{/tr}}
                </p>
                {{/if}}
                <p>
                    {{t "You can fully access this community and participate in conversations
                      by creating a Zulip account in this organization." }}
                </p>
            </main>
            <footer class="modal__footer">
                <a class="modal__btn dialog_submit_button" href="{{signup_link}}">
                    <span>{{t "Sign up" }}</span>
                </a>
                <a class="modal__btn dialog_submit_button" href="{{login_link}}">
                    <span>{{t "Log in" }}</span>
                </a>
            </footer>
        </div>
    </div>
</div>

</pre>
#### left_sidebar.hbs ####
<pre>
<div class="left-sidebar" id="left-sidebar" role="navigation">
    <div class="narrows_panel">
        <ul id="global_filters" class="filters">
            {{!-- Special-case this link so we don't actually go to page top. --}}
            <li class="top_left_all_messages top_left_row" title="{{t 'All messages' }} (a)">
                <a href="#all_messages" class="home-link">
                    <span class="filter-icon">
                        <i class="fa fa-align-left" aria-hidden="true"></i>
                    </span>
                    {{~!-- squash whitespace --~}}
                    <span>{{t 'All messages' }}</span>
                    <span class="unread_count"></span>
                </a>
                <span class="arrow all-messages-sidebar-menu-icon hidden-for-spectators"><i class="zulip-icon zulip-icon-ellipsis-v-solid" aria-hidden="true"></i></span>
            </li>
            <li class="top_left_recent_topics top_left_row" title="{{t 'Recent conversations' }} (t)">
                <a href="#recent">
                    <span class="filter-icon">
                        <i class="fa fa-clock-o" aria-hidden="true"></i>
                    </span>
                    {{~!-- squash whitespace --~}}
                    <span>{{t 'Recent conversations' }}</span>
                </a>
            </li>
            <li class="top_left_mentions top_left_row hidden-for-spectators" title="{{t 'Mentions' }}">
                <a href="#narrow/is/mentioned">
                    <span class="filter-icon">
                        <i class="fa fa-at" aria-hidden="true"></i>
                    </span>
                    {{~!-- squash whitespace --~}}
                    <span>{{t 'Mentions' }}</span>
                    <span class="unread_count"></span>
                </a>
            </li>
            <li class="top_left_starred_messages top_left_row hidden-for-spectators" title="{{t 'Starred messages' }}">
                <a href="#narrow/is/starred">
                    <span class="filter-icon">
                        <i class="fa fa-star" aria-hidden="true"></i>
                    </span>
                    {{~!-- squash whitespace --~}}
                    <span>{{t 'Starred messages' }}</span>
                    <span class="unread_count"></span>
                </a>
                <span class="arrow starred-messages-sidebar-menu-icon"><i class="zulip-icon zulip-icon-ellipsis-v-solid" aria-hidden="true"></i></span>
            </li>
            <li class="top_left_drafts top_left_row hidden-for-spectators" title="{{t 'Drafts' }} (d)">
                <a href="#drafts">
                    <span class="filter-icon">
                        <i class="fa fa-pencil" aria-hidden="true"></i>
                    </span>
                    {{~!-- squash whitespace --~}}
                    <span>{{t 'Drafts' }}</span>
                    <span class="unread_count"></span>
                </a>
                <span class="arrow drafts-sidebar-menu-icon"><i class="zulip-icon zulip-icon-ellipsis-v-solid" aria-hidden="true"></i></span>
            </li>
        </ul>
    </div>

    <div id="private_messages_sticky_header" class="private_messages_container zoom-out hidden-for-spectators">
        <div id="private_messages_section">
            <div id="private_messages_section_header" class="zoom-out zoom-in-sticky">
                <span id="pm_tooltip_container">
                    <i id="toggle_private_messages_section_icon" class="fa fa-sm fa-caret-down toggle_private_messages_section zoom-in-hide" aria-hidden="true"></i>
                    <h4 class="sidebar-title toggle_private_messages_section">{{t 'DIRECT MESSAGES' }}</h4>
                </span>
                <span class="unread_count"></span>
                <a id="show_all_private_messages" href="#narrow/is/private">
                    <i class="fa fa-align-right" aria-label="{{t 'All direct messages' }}"></i>
                </a>
            </div>
        </div>
        <a class="zoom-out-hide" id="hide_more_private_messages">
            <span> {{t 'back to streams' }}</span>
        </a>
    </div>
    {{~!-- squash whitespace --~}}
    <div id="left_sidebar_scroll_container" class="scrolling_list" data-simplebar>
        <div class="private_messages_container zoom-out hidden-for-spectators">
            <div id="private_messages_list"></div>
        </div>

        <div id="streams_list" class="zoom-out">
            <div id="streams_header" class="zoom-in-hide"><h4 class="sidebar-title" data-tooltip-template-id="filter-streams-tooltip-template">{{t 'STREAMS' }}</h4>
                <span class="tippy-zulip-tooltip streams_inline_icon_wrapper hidden-for-spectators" data-tippy-content="{{t 'Add streams' }}">
                    <i id="streams_inline_icon" class='fa fa-plus' aria-hidden="true" ></i>
                </span>
                <i class="streams_filter_icon fa fa-filter tippy-zulip-tooltip" aria-hidden="true" data-tooltip-template-id="filter-streams-tooltip-template"></i>
                <div class="input-append notdisplayed stream_search_section">
                    <input class="stream-list-filter home-page-input" type="text" autocomplete="off" placeholder="{{t 'Filter streams' }}" />
                    <button type="button" class="btn clear_search_button" id="clear_search_stream_button">
                        <i class="fa fa-remove" aria-hidden="true"></i>
                    </button>
                </div>
                <template id="filter-streams-tooltip-template">
                    {{t 'Filter streams' }}
                    {{tooltip_hotkey_hints "Q"}}
                </template>
            </div>
            <div id="topics_header">
                <a class="show-all-streams" tabindex="0">{{t 'Back to streams' }}</a>
            </div>
            <div id="stream-filters-container">
                <ul id="stream_filters" class="filters"></ul>
                {{#unless is_guest }}
                    <div id="subscribe-to-more-streams"></div>
                {{/unless}}
                <div id="login-link-container" class="only-visible-for-spectators">
                    <a class="login_button">
                        <i class="fa fa-sign-in" aria-hidden="true"></i>
                        {{~!-- squash whitespace --~}}
                        {{t 'Log in to browse more streams'}}
                    </a>
                </div>
            </div>
        </div>
    </div>
</div>

</pre>
#### meta_tags.html ####
<pre>
<!-- Google / search engine tags -->
{% if allow_search_engine_indexing %}
    {% if PAGE_DESCRIPTION %}
    <meta name="description" content="{{ PAGE_DESCRIPTION }}" />
    {% endif %}
{% else %}
    <meta name="robots" content="noindex,nofollow" />
{% endif %}

<!-- Open Graph / Facebook / Twitter meta tags -->
<meta property="og:url" content="{{ PAGE_METADATA_URL }}" />
<meta property="og:type" content="website" />
<meta property="og:site_name" content="Zulip" />
{% if PAGE_TITLE %}
<meta property="og:title" content="{{ PAGE_TITLE }}" />
{% endif %}
{% if PAGE_DESCRIPTION %}
<meta property="og:description" content="{{ PAGE_DESCRIPTION }}" />
{% endif %}
{% if PAGE_METADATA_IMAGE %}
<meta property="og:image" content="{{ PAGE_METADATA_IMAGE }}" />
{% else %}
<meta property="og:image" content="{{ static('images/logo/zulip-icon-128x128.png') }}" />
{% endif %}
<meta name="twitter:card" content="summary" />

</pre>
#### stream_sidebar_row.hbs ####
<pre>
{{! Stream sidebar rows }}

<li class="narrow-filter{{#if is_muted}} out_of_home_view{{/if}}" data-stream-id="{{id}}">
    <div class="bottom_left_row">
        <div class="subscription_block selectable_sidebar_block">

            <span class="stream-privacy-{{id}} stream-privacy filter-icon" style="color: {{color}}">
                {{> stream_privacy }}
            </span>

            <a href="{{uri}}" title="{{name}}" class="stream-name">{{name}}</a>

            <span class="unread_mention_info"></span>
            <span class="unread_count"></span>
        </div>
        <span class="stream-sidebar-menu-icon hidden-for-spectators"><i class="zulip-icon zulip-icon-ellipsis-v-solid" aria-hidden="true"></i></span>
    </div>
</li>

</pre>
#### invalid_realm.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Organization does not exist") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

<div class="app find-account-page flex full-page">
    <div class="inline-block new-style">
        <div class="lead">
            <h1 class="get-started">{{ _('Organization does not exist') }}…</h1>
        </div>

        <div class="app-main white-box">
            {{ _('Hi there! Thank you for your interest in Zulip.') }}
            <br />
            {% trans %}There is no Zulip organization hosted at this subdomain.{% endtrans %}
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### pm_list_item.hbs ####
<pre>
<li class='{{#if is_active}}active-sub-filter{{/if}} {{#if is_zero}}zero-pm-unreads{{/if}} pm-list-item bottom_left_row' data-user-ids-string='{{user_ids_string}}'>
    <span class='pm-box pm_user_status' data-user-ids-string='{{user_ids_string}}' data-is-group='{{is_group}}'>

        <div class="pm_left_col">
            {{#if is_group}}
            <span class="fa fa-group"></span>
            {{else}}
            <span class="{{user_circle_class}} user_circle"></span>
            {{/if}}
        </div>

        <a href='{{url}}' class="conversation-partners">
            {{recipients}}
            {{> status_emoji status_emoji_info}}
        </a>
        <span class="unread_count {{#if is_zero}}zero_count{{/if}}">
            {{unread}}
        </span>
    </span>
</li>

</pre>
#### recent_topics_filters.hbs ####
<pre>
<button data-filter="all" type="button" class="btn btn-default btn-recent-filters">{{t 'All' }}</button>
<button data-filter="include_private" type="button" class="btn btn-default btn-recent-filters {{#if is_spectator}}fake_disabled_button{{/if}}" role="checkbox" aria-checked="true">
    {{#if filter_pm}}
    <i class="fa fa-check-square-o"></i>
    {{else}}
    <i class="fa fa-square-o"></i>
    {{/if}}
    {{t 'Include DMs' }}
</button>
<button data-filter="include_muted" type="button" class="btn btn-default btn-recent-filters {{#if is_spectator}}fake_disabled_button{{/if}}" role="checkbox" aria-checked="false">
    {{#if filter_muted }}
    <i class="fa fa-check-square-o"></i>
    {{else}}
    <i class="fa fa-square-o"></i>
    {{/if}}
    {{t 'Include muted' }}
</button>
<button data-filter="unread" type="button" class="btn btn-default btn-recent-filters {{#if is_spectator}}fake_disabled_button{{/if}}" role="checkbox" aria-checked="false">
    {{#if filter_unread}}
    <i class="fa fa-check-square-o"></i>
    {{else}}
    <i class="fa fa-square-o"></i>
    {{/if}}
    {{t 'Unread' }}
</button>
<button data-filter="participated" type="button" class="btn btn-default btn-recent-filters {{#if is_spectator}}fake_disabled_button{{/if}}" role="checkbox" aria-checked="false">
    {{#if filter_participated}}
    <i class="fa fa-check-square-o"></i>
    {{else}}
    <i class="fa fa-square-o"></i>
    {{/if}}
    {{t 'Participated' }}
</button>

</pre>
#### drafts_sidebar_action.hbs ####
<pre>
{{! Contents of the "drafts sidebar" popup }}
<ul class="nav nav-list">
    <li>
        {{! tabindex="0" Makes anchor tag focusable. Needed for keyboard support. }}
        <a tabindex="0" id="delete_all_drafts_sidebar">
            <i class="fa fa-trash-o" aria-hidden="true"></i>
            {{t "Delete all drafts" }}
        </a>
    </li>
</ul>

</pre>
#### recent_topics_table.hbs ####
<pre>
<div id="recent_topics_filter_buttons" class="btn-group" role="group">
    <div id="recent_filters_group">
        {{> recent_topics_filters}}
    </div>
    <div class="search_group" role="group">
        <input type="text" id="recent_topics_search" value="{{ search_val }}" autocomplete="off" placeholder="{{t 'Filter topics (t)' }}" />
        <button type="button" class="btn clear_search_button" id="recent_topics_search_clear">
            <i class="fa fa-remove" aria-hidden="true"></i>
        </button>
    </div>
</div>
<div class="table_fix_head" data-simplebar>
    <table class="table table-responsive">
        <thead>
            <tr>
                <th data-sort="stream_sort">{{t 'Stream' }}</th>
                <th data-sort="topic_sort">{{t 'Topic' }}</th>
                <th class='participants_header'>{{t 'Participants' }}</th>
                <th data-sort="numeric" data-sort-prop="last_msg_id" class="last_msg_time_header active descend">{{t 'Time' }}</th>
            </tr>
        </thead>
        <tbody data-empty="{{t 'No topics match your current filter.' }}"></tbody>
    </table>
</div>

</pre>
#### narrow_to_compose_recipients_tooltip.hbs ####
<pre>
<div>
    <span>{{t 'Go to conversation' }}</span>
    {{#if display_current_view}}
    <p class="narrow_to_compose_recipient_current_view_help tooltip-inner-content italic">{{display_current_view}}</p>
    {{/if}}
</div>
{{tooltip_hotkey_hints "Ctrl" "."}}

</pre>
#### gear_menu.hbs ####
<pre>
<ul class="nav" role="navigation">
    <li class="dropdown actual-dropdown-menu" id="gear-menu">
        <a id="settings-dropdown" tabindex="0" role="button" class="dropdown-toggle" data-target="nada" data-toggle="dropdown" title="{{t 'Menu' }} (g)">
            <i class="fa fa-cog settings-dropdown-cog" aria-hidden="true"></i>
        </a>
        <ul class="dropdown-menu" role="menu" aria-labelledby="settings-dropdown">
            <li class="org-info org-name">{{realm_name}}</li>
            <li class="org-info org-url">{{realm_uri}}</li>
            {{#if is_self_hosted }}
                <li class="org-info org-version">
                    <a href="#about-zulip" role="menuitem">{{version_display_string}}</a>
                </li>
                {{#if server_needs_upgrade }}
                <li class="org-info org-upgrade small-font-size">
                    <a href="https://zulip.readthedocs.io/en/stable/production/upgrade-or-modify.html" target="_blank" rel="noopener noreferrer" role="menuitem">{{t 'Upgrade to the latest release' }}</a>
                </li>
                {{/if}}
            {{else}}
                <li class="org-info org-plan hidden-for-spectators small-font-size">
                    {{#if is_plan_limited }}
                        <a href="/plans/" target="_blank" rel="noopener noreferrer" role="menuitem">Zulip Cloud Free</a>
                    {{else if is_plan_standard}}
                        <a href="/plans/" target="_blank" rel="noopener noreferrer" role="menuitem">Zulip Cloud Standard</a>
                    {{else if is_plan_standard_sponsored_for_free}}
                        <a href="/plans/" target="_blank" rel="noopener noreferrer" role="menuitem">Zulip Cloud Standard (sponsored)</a>
                    {{/if}}
                </li>
            {{/if}}
            {{#if (and is_plan_limited is_owner) }}
            <li class="org-info org-upgrade small-font-size">
                <a href="/upgrade/" target="_blank" rel="noopener noreferrer" role="menuitem">{{t "Upgrade to {standard_plan_name}" }}</a>
            </li>
            {{/if}}
            {{#if is_plan_limited }}
                {{#if is_education_org }}
                <li class="org-info org-upgrade small-font-size">
                    <a href="/upgrade/" target="_blank" rel="noopener noreferrer" role="menuitem">{{t 'Request education pricing' }}</a>
                </li>
                {{else if (not is_business_org) }}
                <li class="org-info org-upgrade small-font-size">
                    <a href="/upgrade/" target="_blank" rel="noopener noreferrer" role="menuitem">{{t 'Request sponsorship' }}</a>
                </li>
                {{/if}}
            {{/if}}
            <li class="divider" role="presentation"></li>
            <li class="hidden-for-spectators" role="presentation">
                <a href="#streams/subscribed" role="menuitem">
                    <i class="fa fa-exchange" aria-hidden="true"></i> {{t 'Manage streams' }}
                </a>
            </li>
            <li class="hidden-for-spectators" role="presentation">
                <a href="#settings" role="menuitem">
                    <i class="fa fa-wrench" aria-hidden="true"></i> {{t 'Personal settings' }}
                </a>
            </li>
            <li class="admin-menu-item hidden-for-spectators" role="presentation">
                <a href="#organization" role="menuitem">
                    <i class="fa fa-bolt" aria-hidden="true"></i>
                    <span>{{t 'Organization settings' }}</span>
                </a>
            </li>
            {{#unless is_guest}}
            <li class="hidden-for-spectators" role="presentation">
                <a href="/stats" target="_blank" rel="noopener noreferrer" role="menuitem">
                    <i class="fa fa-bar-chart" aria-hidden="true"></i>
                    <span>{{t 'Usage statistics' }}</span>
                </a>
            </li>
            {{/unless}}
            <li role="presentation" class="only-visible-for-spectators">
                <a class="change-language-spectator" role="menuitem">
                    <i class="zulip-icon zulip-icon-language" aria-hidden="true"></i> {{t 'Select language' }}
                </a>
            </li>
            <li role="presentation" class="only-visible-for-spectators">
                <a class="dark-theme" role="menuitem">
                    <i class="fa fa-moon-o" aria-hidden="true"></i> {{t 'Switch to dark theme' }}
                </a>
            </li>
            <li role="presentation" class="only-visible-for-spectators">
                <a class="light-theme" role="menuitem">
                    <i class="fa fa-sun-o" aria-hidden="true"></i> {{t 'Switch to light theme' }}
                </a>
            </li>
            <li class="divider" role="presentation"></li>
            <li role="presentation">
                <a href="/help/" target="_blank" rel="noopener noreferrer" role="menuitem">
                    <i class="fa fa-question-circle" aria-hidden="true"></i> {{t 'Help center' }}
                </a>
            </li>
            <li role="presentation">
                <a tabindex="0" role="menuitem" data-overlay-trigger="keyboard-shortcuts">
                    <i class="fa fa-keyboard-o" aria-hidden="true"></i> {{t 'Keyboard shortcuts' }} <span class="hotkey-hint">(?)</span>
                </a>
            </li>
            <li role="presentation" class="hidden-for-spectators">
                <a tabindex="0" role="menuitem" data-overlay-trigger="message-formatting">
                    <i class="fa fa-pencil" aria-hidden="true"></i> {{t 'Message formatting' }}
                </a>
            </li>
            <li role="presentation">
                <a tabindex="0" role="menuitem" data-overlay-trigger="search-operators">
                    <i class="fa fa-search" aria-hidden="true"></i> {{t 'Search filters' }}
                </a>
            </li>
            <li class="divider only-visible-for-spectators" role="presentation"></li>
            <li role="presentation" id="gear_menu_about_zulip">
                <a href="#about-zulip" role="menuitem" class="menuitem-version">
                    <span class="white_zulip_icon_without_text"></span>
                    <span class="about_zulip_text">{{t "About Zulip" }}</span>
                </a>
            </li>
            {{#if corporate_enabled}}
            <li role="presentation">
                <a href="/help/contact-support" target="_blank" rel="noopener noreferrer" role="menuitem">
                    <i class="fa fa-envelope" aria-hidden="true"></i> {{t 'Contact support' }}
                </a>
            </li>
            {{/if}}
            <li class="divider" role="presentation"></li>
            <li role="presentation" class="hidden-for-spectators">
                <a href="{{ apps_page_url }}" target="_blank" rel="noopener noreferrer" role="menuitem">
                    <i class="fa fa-desktop" aria-hidden="true"></i> {{t 'Desktop & mobile apps' }}
                </a>
            </li>
            <li role="presentation" class="hidden-for-spectators">
                <a href="/integrations/" target="_blank" rel="noopener noreferrer" role="menuitem">
                    <i class="fa fa-github" aria-hidden="true"></i> {{t 'Integrations' }}
                </a>
            </li>
            <li role="presentation" class="hidden-for-spectators">
                <a href="/api" target="_blank" rel="noopener noreferrer" role="menuitem">
                    <i class="fa fa-sitemap" aria-hidden="true"></i> {{t 'API documentation' }}
                </a>
            </li>
            {{#if show_billing}}
            <li role="presentation" class="hidden-for-spectators">
                <a href="/billing/" target="_blank" rel="noopener noreferrer" role="menuitem">
                    <i class="fa fa-credit-card" aria-hidden="true"></i> {{t 'Billing' }}
                </a>
            </li>
            {{/if}}
            {{#if promote_sponsoring_zulip}}
            <li role="presentation" class="hidden-for-spectators">
                <a href="https://zulip.com/help/support-zulip-project" target="_blank" rel="noopener noreferrer" role="menuitem">
                    <i class="fa fa-heart" aria-hidden="true"></i> {{t 'Support Zulip' }}
                </a>
            </li>
            {{/if}}
            {{#if show_plans}}
            <li role="presentation" class="hidden-for-spectators">
                <a href="/plans/" target="_blank" rel="noopener noreferrer" role="menuitem">
                    <i class="fa fa-rocket" aria-hidden="true"></i> {{t 'Plans and pricing' }}
                </a>
            </li>
            {{/if}}
            <li class="divider hidden-for-spectators" role="presentation"></li>
            {{#if can_invite_others_to_realm}}
            <li role="presentation">
                <a class="invite-user-link" role="menuitem">
                    <i class="fa fa-user-plus" aria-hidden="true"></i> {{t 'Invite users' }}
                </a>
            </li>
            <li class="divider" role="presentation"></li>
            {{/if}}
            {{#if show_webathena}}
            <li title="{{t 'Grant Zulip the Kerberos tickets needed to run your Zephyr mirror via Webathena' }}" id="webathena_login_menu" role="presentation">
                <a href="#webathena" class="webathena_login" role="menuitem">
                    <i class="fa fa-bolt" aria-hidden="true"></i>{{t 'Link with Webathena' }}
                </a>
            </li>
            {{/if}}
            <li role="presentation" class="only-visible-for-spectators">
                <a href="{{login_link}}" role="menuitem">
                    <i class="fa fa-sign-in" aria-hidden="true"></i> {{t 'Log in' }}
                </a>
            </li>
            <li role="presentation">
                <a href="#logout" class="logout_button hidden-for-spectators" role="menuitem">
                    <i class="fa fa-power-off" aria-hidden="true"></i> {{t 'Log out' }}
                </a>
            </li>
        </ul>
    </li>
</ul>

</pre>
#### find_account.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Find your accounts") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

<div class="app find-account-page flex full-page">
    <div class="inline-block new-style">
        <div class="lead">
            <h1 class="get-started">{{ _("Find your Zulip accounts") }}…</h1>
        </div>

        <div class="app-main find-account-page-container white-box">
            {% if emails %}
            <div id="results">
                <p>
                    Emails sent! You will only receive emails at addresses associated
                    with Zulip organizations. The addresses entered on the previous page
                    are listed below:
                </p>

                <ul>
                    {% for email in emails %}
                    <li>{{ email }}</li>
                    {% endfor %}
                </ul>

                {% include 'zerver/dev_env_email_access_details.html' %}

            </div>
            {% else %}
            <div class="find-account-form">
                <p>
                    We will send you an email with the sign-in information for
                    any Zulip organization(s) associated with the addresses you enter below.
                </p>
                <form class="form-inline" id="find_account" name="email_form"
                  action="{{ current_url() }}" method="post">
                    {{ csrf_input }}
                    <div class="input-box moving-label horizontal">
                        <div class="inline-block relative">
                            <input type="text" autofocus id="emails" name="emails" required />
                            <label for="emails">{{ _('Email addresses') }}</label>
                        </div>
                        <button type="submit">{{ _('Find accounts') }}</button>
                    </div>
                    <div><i>{{ form.emails.help_text }}</i></div>
                </form>
                <div id="errors"></div>
                {% if form.emails.errors %}
                    {% for error in form.emails.errors %}
                    <div class="alert alert-error">{{ error }}</div>
                    {% endfor %}
                {% endif %}
            </div>
            {% endif %}
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### auth_subdomain.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Authentication subdomain error") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

<div class="error_page">
    <div class="container">
        <div class="row-fluid">
            <img src="{{ static('images/errors/500art.svg') }}" alt=""/>
            <div class="errorbox">
                <div class="errorcontent">
                    <h1 class="lead">{{ _("Authentication subdomain") }}</h1>
                    <p>
                        {% trans %}
                        It appears you ended up here by accident. This site
                        is meant to be an intermediate step in the authentication process
                        and shouldn't be accessed manually. If you came here directly,
                        you probably got the address wrong. If you got stuck here while trying
                        to log in, this is most likely a server bug or misconfiguration.
                        {% endtrans %}
                    </p>
                </div>
            </div>
        </div>
    </div>
</div>

{% endblock %}

</pre>
#### portico_signup.html ####
<pre>
{% extends "zerver/portico.html" %}
{% set entrypoint = entrypoint|default("signup") %}

{# Portico page with signup code #}

</pre>
#### user_stream_list_item.hbs ####
<pre>
<tr data-stream-id="{{stream_id}}">
    <td class="subscription_list_stream">
        <span class="stream-privacy-{{stream_id}} stream-privacy filter-icon" style="color: {{stream_color}}">
            {{> stream_privacy }}
        </span>
        <a class = "stream_list_item" href="{{stream_edit_url}}">{{name}}</a>
    </td>
    {{#if show_unsubscribe_button}}
    <td class="remove_subscription">
        <div class="subscription_list_remove">
            <button type="button" name="unsubscribe" class="remove-subscription-button button small rounded btn-danger {{#if show_private_stream_unsub_tooltip}}tippy-zulip-tooltip{{/if}}" data-tippy-content='{{t "Use stream settings to unsubscribe from private streams."}}'>
                {{t 'Unsubscribe' }}
            </button>
        </div>
    </td>
    {{/if}}
</tr>

</pre>
#### realm_reactivation_link_error.html ####
<pre>
{% extends "zerver/portico_signup.html" %}

{% block title %}
<title>{{ _("Organization reactivation link expired or invalid") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<div class="app portico-page">
    <div class="app-main portico-page-container center-block flex full-page account-creation new-style">
        <div class="inline-block">

            <div class="get-started">
                <h1>{{ _("The organization reactivation link has expired or is not valid.") }}</h1>
            </div>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### login.html ####
<pre>
{% extends "zerver/portico.html" %}
{% set entrypoint = "signup" %}

{% block title %}
<title>{{ _("Log in") }} | Zulip</title>
{% endblock %}

{# Login page. #}

{% block portico_content %}

<!-- The following empty tag has unique data-page-id so that this
page can be easily identified in it's respective JavaScript file. -->
<div data-page-id="login-page"></div>
<div class="app login-page split-view new-style flex full-page">
    <div class="inline-block">
        <div class="lead">
            <h1 class="get-started">{{ _("Log in to Zulip") }}</h1>
        </div>

        <div class="app-main login-page-container white-box inline-block">
            {% if realm_name %}
            <div class="left-side">
                <div class="org-header">
                    <img class="avatar" src="{{ realm_icon }}" alt="" />
                    <div class="info-box">
                        <div class="organization-name">{{ realm_name }}</div>
                        <div class="organization-path">{{ realm_uri }}</div>
                    </div>
                </div>
                <div class="description">
                    {{ realm_description|safe }}
                </div>
            </div>
            {% endif %}

            <div class="right-side">
                {% if realm_web_public_access_enabled %}
                    <div class="login-social">
                        <form class="anonymous_access_form form-inline" action="/" method="post">
                            {{ csrf_input }}
                            <input type="hidden" name="next" value="{{ next }}" />
                            <button class="full-width">
                                {{ _('View without an account') }}
                            </button>
                        </form>
                    </div>
                    {% if no_auth_enabled %}
                    {% else %}
                    <div class="or"><span>{{ _('OR') }}</span></div>
                    {% endif %}
                {% endif %}
                {% if no_auth_enabled %}
                    <div class="alert">
                        <p>
                            No authentication backends are enabled on this
                            server yet, so it is impossible to log in!
                        </p>

                        <p>
                            See the <a href="https://zulip.readthedocs.io/en/latest/production/install.html#step-3-configure-zulip">
                            Zulip authentication documentation</a> to learn how to configure authentication backends.
                        </p>
                    </div>
                {% else %}

                    {% if already_registered %}
                    <div class="alert">
                        {{ _("You've already registered with this email address. Please log in below.") }}
                    </div>
                    {% endif %}

                    {% if deactivated_account_error %}
                    <div class="alert">
                        {{ deactivated_account_error }}
                    </div>
                    {% endif %}

                    {% if password_auth_enabled %}
                        <form name="login_form" id="login_form" method="post" class="login-form"
                          action="{{ url('login') }}">
                            <input type="hidden" name="next" value="{{ next }}" />

                            {% if two_factor_authentication_enabled %}
                            {{ wizard.management_form }}
                            {% endif %}
                            {{ csrf_input }}

                            <!-- .no-validation is for removing the red star in CSS -->
                            {% if not two_factor_authentication_enabled or wizard.steps.current == 'auth' %}
                            <div class="input-box no-validation">
                                <input id="id_username" type="{% if not require_email_format_usernames %}text{% else %}email{% endif %}"
                                  name="username" class="{% if require_email_format_usernames %}email {% endif %}required"
                                  {% if email %} value="{{ email }}" {% else %} value="" autofocus {% endif %}
                                  maxlength="72" required />
                                <label for="id_username">
                                    {% if not require_email_format_usernames and email_auth_enabled %}
                                    {{ _('Email or username') }}
                                    {% elif not require_email_format_usernames %}
                                    {{ _('Username') }}
                                    {% else %}
                                    {{ _('Email') }}
                                    {% endif %}
                                </label>
                            </div>

                            <div class="input-box no-validation password-div">
                                <input id="id_password" name="password" class="required" type="password" autocomplete="off"
                                  {% if email %} autofocus {% endif %}
                                  required />
                                <label for="id_password">{{ _('Password') }}</label>
                                <i class="fa fa-eye-slash password_visibility_toggle" role="button"></i>
                            </div>
                            {% else %}
                            {% include "two_factor/_wizard_forms.html" %}
                            {% endif %}

                            {% if form.errors %}
                            <div class="alert alert-error">
                                {% for error in form.errors.values() %}
                                <div>{{ error | striptags }}</div>
                                {% endfor %}
                            </div>
                            {% endif %}

                            <button type="submit" name="button" class="full-width">
                                <img class="loader" src="{{ static('images/loading/loader-white.svg') }}" alt="" />
                                <span class="text">{{ _("Log in") }}</span>
                            </button>
                        </form>

                        {% if page_params.external_authentication_methods|length > 0 %}
                        <div class="or"><span>{{ _('OR') }}</span></div>
                        {% endif %}

                    {% endif %} <!-- if password_auth_enabled -->

                    {% for backend in page_params.external_authentication_methods %}
                    <div class="login-social">
                        <form class="social_login_form form-inline" action="{{ backend.login_url }}" method="get">
                            <input type="hidden" name="next" value="{{ next }}" />
                            <button id="login_{{ backend.button_id_suffix }}" class="login-social-button"
                              {% if backend.display_icon %} style="background-image:url({{ backend.display_icon }})"  {% endif %}> {{ _('Log in with %(identity_provider)s', identity_provider=backend.display_name) }}
                            </button>
                        </form>
                    </div>
                    {% endfor %}

                    <div class="actions">
                        {% if email_auth_enabled %}
                        <a class="forgot-password" href="/accounts/password/reset/">{{ _('Forgot your password?') }}</a>
                        {% endif %}
                        {% if not register_link_disabled %}
                        <a class="register-link float-right" href="/register/">{{ _('Sign up') }}</a>
                        {% endif %}
                    </div>
                {% endif %}
            </div>
        </div>

        {% if realm_invite_required %}
        <div class="contact-admin">
            <p class="invite-hint">{{ _("Don't have an account yet? You need to be invited to join this organization.") }}</p>
        </div>
        {% endif %}
    </div>
</div>

{% endblock %}

</pre>
#### user_group_info_popover_content.hbs ####
<pre>
{{! Contents of the "user group info" popup }}
<div class="group-info">
    <div class="group-name"> {{group_name}} </div>
    <div class="group-description">
        {{group_description}}
    </div>
</div>
<hr />
<ul class="nav nav-list member-list" data-simplebar data-simplebar-auto-hide="false">
    {{#each members}}
        <li>
            {{#if is_active }}
                {{#if is_bot}}
                <i class="zulip-icon zulip-icon-bot" aria-hidden="true"></i>
                {{else}}
                <span class="user_circle {{user_circle_class}}  popover_user_presence" title="{{user_last_seen_time_status}}"></span>
                {{/if}}
            {{/if}}
            <span>{{full_name}}</span>
        </li>
    {{/each}}
</ul>
<hr />
<ul class="nav nav-list manage-group">
    <li>
        <a href="#organization/user-groups-admin">
            <i class="fa fa-cog" aria-hidden="true"></i>
            {{t 'Manage user groups' }}
        </a>
    </li>
</ul>

</pre>
#### draft_table_body.hbs ####
<pre>
<div id="draft_overlay" class="overlay new-style" data-overlay="drafts">
    <div class="flex overlay-content">
        <div class="drafts-container modal-bg">
            <div class="drafts-header">
                <h1>{{t 'Drafts' }}</h1>
                <div class="exit">
                    <span class="exit-sign">&times;</span>
                </div>
                <div class="removed-drafts">
                    {{t "Drafts are not synced to other devices and browsers." }}
                    <br />
                    {{#tr}}Drafts older than <strong>{draft_lifetime}</strong> days are automatically removed.{{/tr}}
                </div>
            </div>
            <div class="drafts-list">
                <div class="no-drafts">
                    {{t 'No drafts.'}}
                </div>

                <div id="drafts-from-conversation">
                    <h2>{{narrow_drafts_header}}</h2>
                    {{#each narrow_drafts}}
                        {{> draft}}
                    {{/each}}
                </div>
                <div id="other-drafts">
                    <h2 id="other-drafts-header">Other drafts</h2>
                    {{#each other_drafts}}
                        {{> draft}}
                    {{/each}}
                </div>
            </div>
        </div>
    </div>
</div>

</pre>
#### no_spare_licenses.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("No licenses available") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<br/>
<br/>
<br/>

<h3>{{ _("This organization cannot accept new members right now.") }}</h3>

<p>
    {% trans %}
    New members cannot join this organization because all Zulip licenses are currently in use. Please contact the person who
    invited you and ask them to increase the number of licenses, then try again.
    {% endtrans %}
</p>
{% endblock %}

</pre>
#### login_to_view_image_button.hbs ####
<pre>
<div class="spectator_login_for_image_button">
    <a class="login_button color_animated_button" href="/login/">
        <i class='fa fa-sign-in'></i>
        <span>Log in to view image</span>
    </a>
</div>

</pre>
#### read_receipts_modal.hbs ####
<pre>
<div class="micromodal" id="read_receipts_modal" aria-hidden="true">
    <div class="modal__overlay" tabindex="-1">
        <div class="modal__container" role="dialog" aria-modal="true" aria-labelledby="read_receipts_modal_label">
            <header class="modal__header">
                <h1 class="modal__title" id="read_receipts_modal_label">
                    {{t "Read receipts" }}
                </h1>
                <button class="modal__close" aria-label="{{t 'Close modal' }}" data-micromodal-close></button>
            </header>
            <hr/>
            <main class="modal__content">
                <div class="alert" id="read_receipts_error"></div>
                <div class="read_receipts_info">
                </div>
                <div class="loading_indicator"></div>
            </main>
        </div>
    </div>
</div>

</pre>
#### compare-education.html ####
<pre>
<div class="compare-education">
    <div class="padded-content">
        <div class="text-header">
            <div class="text-content">
                <h1 class="center"><span>Zulip: The most complete communication hub for your class.</span></h1>
            </div>
        </div>

        <div class="table-container">
            <table>
                <thead>
                    <tr>
                        <th>Feature</th>
                        <th >Zulip</th>
                        <th class="normal">Slack</th>
                        <th class="normal">Discord</th>
                        <th class="normal">Piazza</th>
                        <th class="normal">CampusWire</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Rich, modern chat</td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                    </tr>
                    <tr>
                        <td>Apps for every platform</td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                    </tr>
                    <tr>
                        <td>Self-hosting option for full control over data</td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                    </tr>
                    <tr>
                        <td>Dedicated account</td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                    </tr>
                    <tr>
                        <td>Topic-based threading</td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                    </tr>
                    <tr>
                        <td>Resolve topics/questions</td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                    </tr>
                    <tr>
                        <td>Move topics/questions</td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                    </tr>
                    <tr>
                        <td>Native LaTeX support</td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                    </tr>
                    <tr>
                        <td>Built-in spoilers</td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                    </tr>
                    <tr>
                        <td>Emoji reactions</td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                    </tr>
                    <tr>
                        <td>@-mention groups</td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                    </tr>
                    <tr>
                        <td>Scales to 10,000s of users</td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                        <td class="yes"></td>
                        <td class="no"></td>
                        <td class="no"></td>
                    </tr>
                    <tr>
                        <td># supported languages</td>
                        <td class="number">23</td>
                        <td class="number">13</td>
                        <td class="number">30</td>
                        <td class="number one">1</td>
                        <td class="number one">1</td>
                    </tr>

                </tbody>
            </table>
        </div>
    </div>
</div>

</pre>
#### rate_limit_exceeded.html ####
<pre>
{% extends "zerver/portico.html" %}

{% block title %}
<title>{{ _("Rate limit exceeded") }} | Zulip</title>
{% endblock %}

{% block portico_content %}

<div class="error_page">
    <div class="container">
        <div class="row-fluid">
            <img src="{{ static('images/errors/500art.svg') }}" alt=""/>
            <div class="errorbox">
                <div class="errorcontent">
                    <h1 class="lead">{{ _("Rate limit exceeded.") }}</h1>
                    <p>
                        {% trans %}You have exceeded the limit for how
                        often a user can perform this action.{% endtrans %}
                        {% trans %}You can try again in {{retry_after}} seconds.{% endtrans %}
                    </p>
                </div>
            </div>
        </div>
    </div>
</div>

{% endblock %}

</pre>
#### giphy_picker.hbs ####
<pre>
<div class="popover" id="giphy_grid_in_popover">
    <div class="arrow"></div>
    <div class="popover-inner">
        <div class="search-box">
            <input type="text" tabindex=0 id="giphy-search-query" class="search-query" placeholder="{{t 'Search GIFs' }}" />
            <button type="button" class="btn clear_search_button" id="giphy_search_clear">
                <i class="fa fa-remove" aria-hidden="true"></i>
            </button>
        </div>
        <div class="popover-content" data-simplebar>
            {{! We need a container we can replace
            without removing the simplebar wrappers.
            We replace the `giphy-content` when
            searching for GIFs. }}
            <div class="giphy-content"></div>
        </div>
        <div class="popover-footer">
            <img src="../images/giphy/GIPHY_attribution.png" alt="{{t 'GIPHY attribution' }}" />
        </div>
    </div>
</div>

</pre>
#### draft.hbs ####
<pre>
<div class="draft-row" data-draft-id="{{draft_id}}">
    <div class="draft-info-box" tabindex="0">
        {{#if is_stream}}
        <div class="message_header message_header_stream">
            <div class="message-header-contents">
                <div class="message_label_clickable stream_label {{dark_background}}"
                  style="background: {{stream_color}}; border-left-color: {{stream_color}};">
                    {{stream_name}}
                </div>

                <span class="stream_topic">
                    <div class="message_label_clickable narrows_by_topic">
                        {{topic}}
                    </div>
                </span>
                <span class="recipient_bar_controls"></span>
                <div class="recipient_row_date" title="{{t 'Last modified'}}">{{ time_stamp }}</div>
            </div>
        </div>
        {{else}}
        <div class="message_header message_header_private_message dark_background">
            <div class="message-header-contents">
                <div class="message_label_clickable stream_label">
                    {{t "You and {recipients}" }}
                </div>
                <div class="recipient_row_date" title="{{t 'Last modified'}}">{{ time_stamp }}</div>
            </div>

        </div>
        {{/if}}
        <div class="message_row{{^is_stream}} private-message{{/is_stream}}" role="listitem">
            <div class="messagebox">
                <div class="messagebox-content">
                    <div class="message_top_line">
                        <div class="draft_controls">
                            <i class="fa fa-pencil fa-lg restore-draft tippy-zulip-tooltip" aria-hidden="true" data-tippy-content="{{t 'Restore draft' }} (Enter)"></i>
                            <i class="fa fa-trash-o fa-lg delete-draft tippy-zulip-tooltip" aria-hidden="true" data-tippy-content="{{t 'Delete draft' }} (Backspace)"></i>
                        </div>
                    </div>
                    <div class="message_content rendered_markdown restore-draft" title="{{t 'Restore draft' }}">{{rendered_markdown content}}</div>
                </div>
            </div>
        </div>
    </div>
</div>

</pre>
#### register.html ####
<pre>
{% extends "zerver/portico_signup.html" %}
{% set entrypoint = "register" %}

{% block title %}
<title>{{ _("Registration") }} | Zulip</title>
{% endblock %}

{#
Gather other user information, after having confirmed
their email address.

Form is validated both client-side using jquery-validation (see signup.js) and server-side.
#}

{% block portico_content %}
<div class="register-account flex full-page">
    <div class="center-block new-style" style="padding: 20px 0px">

        <div class="pitch">
            {% if creating_new_realm %}
            <h1>{{ _('Create your organization') }}</h1>
            {% else %}
            <h1>{{ _('Create your account') }}</h1>
            {% endif %}

            {% trans %}
            <p>Enter your account details to complete registration.</p>
            {% endtrans %}
        </div>

        <form method="post" class="white-box" id="registration" action="{{ url('accounts_register') }}">
            {{ csrf_input }}

            <fieldset class="org-registration">
                {% if creating_new_realm %}
                <legend>{{ _('Your organization') }}
                    {% if not form.realm_subdomain.errors %}
                    <span class="edit-realm-details" role="button" tabindex="0"><i class="fa fa-pencil"></i></span>
                    {% endif %}
                </legend>
                {% with %}
                    {% set user_registration_form = "true" %}
                    {% include 'zerver/realm_creation_form.html' %}
                {% endwith %}
                {% if not form.realm_subdomain.errors %}
                <div class="not-editable-realm-details">
                    <div class="input-box">
                        <label for="id_realm_name" class="inline-block label-title">{{ _('Organization name') }}</label>
                        <div id="id_realm_name" class="not-editable-realm-field">{{ form.realm_name.value() }}</div>
                    </div>
                    <div class="input-box">
                        <label for="id_realm_type" class="inline-block label-title">{{ _('Organization type') }}</label>
                        <div id="id_realm_type" class="not-editable-realm-field">{{ selected_realm_type_name }}</div>
                    </div>
                    <div class="input-box">
                        <label for="id_realm_subdomain" class="inline-block label-title">{{ _('Organization URL') }}</label>
                        <div id="id_realm_subdomain" class="not-editable-realm-field">{% if form.realm_subdomain.value() %}{{ form.realm_subdomain.value() }}.{% endif %}{{external_host}}</div>
                    </div>
                </div>
                {% endif %}
                {% endif %}
            </fieldset>

            <fieldset class="user-registration">
                {% if creating_new_realm %}
                <legend>{{ _('Your account') }}</legend>
                {% endif %}
                {% if realm_name and not creating_new_realm %}
                <img class="avatar inline-block" src="{{ realm_icon }}" alt="" />
                <div class="info-box inline-block">
                    <div class="organization-name">{{ realm_name }}</div>
                    <div class="organization-path">{{ realm_uri }}</div>
                </div>
                {% endif %}

                <div class="input-box no-validation">
                    <input type='hidden' name='key' value='{{ key }}' />
                    <input type='hidden' name='timezone' id='timezone'/>
                    <input type="hidden" name="email_address_visibility" id="email_address_visibility"/>
                    <label for="id_email" class="inline-block label-title">{{ _('Email') }}</label>
                    <div id="id_email">{{ email }}</div>
                    {% if not creating_new_realm %}
                    <p id="new-user-email-address-visibility">
                        <span class="current-selected-option">
                            {% if default_email_address_visibility == email_address_visibility_admins_only %}
                                {% trans %}Administrators of this Zulip organization will be able to see this email address.
                                {% endtrans %}
                            {% elif default_email_address_visibility == email_address_visibility_moderators %}
                                {% trans %}Administrators and moderators of this Zulip organization will be able to see this email address.
                                {% endtrans %}
                            {% elif default_email_address_visibility == email_address_visibility_nobody %}
                                {% trans %}Nobody in this Zulip organization will be able to see this email address.
                                {% endtrans %}
                            {% else %}
                                {% trans %}Other users in this Zulip organization will be able to see this email address.
                                {% endtrans %}
                            {% endif %}
                        </span>
                        <a target="_blank" class="change_email_address_visibility" rel="noopener noreferrer">{{ _('Change') }}</a>
                    </p>
                    {% endif %}
                </div>

                {% if accounts %}
                <div class="input-box">
                    <div class="inline-block relative">
                        <select class="select" name="source_realm_id" id="source_realm_select">
                            <option value=""
                              {% if "source_realm_id" in form.data and form.data["source_realm_id"] == "" %}selected {% endif %}>
                                {{ _('Don&rsquo;t import settings') }}
                            </option>
                            {% for account in accounts %}
                            <option value="{{ account.realm_id }}" data-full-name="{{account.full_name}}" data-avatar="{{account.avatar}}"
                              {% if ("source_realm_id" in form.data and account.realm_id == form.data["source_realm_id"]|int)
                              or ("source_realm_id" not in form.data and loop.index0 == 0) %} selected {% endif %}>
                                {{ account.realm_name }}
                            </option>
                            {% endfor %}
                        </select>
                    </div>
                    <label for="source_realm_id" class="inline-block">{{ _('Import settings from existing Zulip account') }}
                        <a href="{{ root_domain_uri }}/help/import-your-settings"><i class="fa fa-question-circle"></i></a>
                    </label>
                </div>
                {% endif %}

                <div class="input-box" id="full_name_input_section">
                    {% if lock_name %}
                        <p class="fakecontrol">{{ full_name }}</p>
                    {% else %}
                        <input id="id_full_name" class="required" type="text" name="full_name"
                          value="{% if full_name %}{{ full_name }}{% elif form.full_name.value() %}{{ form.full_name.value() }}{% endif %}"
                          maxlength="{{ MAX_NAME_LENGTH }}" placeholder="{% trans %}Full name or 名前{% endtrans %}" required />
                        <label for="id_full_name" class="inline-block label-title">{{ _('Full name') }}</label>
                        {% if form.full_name.errors %}
                            {% for error in form.full_name.errors %}
                            <p class="help-inline text-error">{{ error }}</p>
                            {% endfor %}
                        {% endif %}
                    {% endif %}
                </div>

                <div class="input-box" id="profile_info_section" style="display:none;">
                    <img id="profile_avatar" />
                    <div id="profile_full_name"></div>
                </div>

                {% if require_ldap_password %}
                <div class="input-box password-div">
                    <input id="ldap-password" class="required" type="password" name="password" autocomplete="off" required />
                    <label for="ldap-password" class="inline-block">{{ _('Password') }}</label>
                    <i class="fa fa-eye-slash password_visibility_toggle" role="button"></i>
                    <span class="help-inline">
                        {{ _('Enter your LDAP/Active Directory password.') }}
                    </span>
                </div>
                {% elif password_required %}
                <div class="input-box password-div">
                    <input id="id_password" class="required" type="password" name="password" autocomplete="new-password"
                      value="{% if form.password.value() %}{{ form.password.value() }}{% endif %}"
                      maxlength="{{ MAX_PASSWORD_LENGTH }}"
                      data-min-length="{{password_min_length}}"
                      data-min-guesses="{{password_min_guesses}}" required />
                    <label for="id_password" class="inline-block">{{ _('Password') }}</label>
                    <i class="fa fa-eye-slash password_visibility_toggle" role="button"></i>
                    {% if full_name %}
                    <span class="help-inline">
                        {{ _('This is used for mobile applications and other tools that require a password.') }}
                    </span>
                    {% endif %}
                    {% if form.password.errors %}
                        {% for error in form.password.errors %}
                        <p class="help-inline text-error">{{ error }}</p>
                        {% endfor %}
                    {% endif %}
                    <div class="progress" id="pw_strength" title="{{ _('Password strength') }}">
                        <div class="bar bar-danger" style="width: 10%;"></div>
                    </div>
                </div>
                {% endif %}
            </fieldset>
            {% if default_stream_groups %}
            <hr />
            <div class="default-stream-groups">
                <p class="margin">{{ _('What are you interested in?') }}</p>
                {% for default_stream_group in default_stream_groups %}
                <div class="input-group margin">
                    <label for="id_default_stream_group__{{ default_stream_group.id }}"
                      class="inline-block checkbox">
                        <input class="inline-block" type="checkbox"
                          name="default_stream_group"
                          id="id_default_stream_group__{{ default_stream_group.id }}" value="{{ default_stream_group.name }}"
                          {% if "default_stream_group" in form.data and default_stream_group.id in form.data.getlist('default_stream_group') %} checked {% endif %} />
                        <span></span>
                        {% set comma = joiner(", ") %}
                        <div class="default_stream_group_name inline-block"
                          title="{{ default_stream_group.description }}">
                            {{ default_stream_group.name }}
                        </div>
                        (
                        {%- for stream in default_stream_group.streams.all() -%}
                            {{- comma() -}} <div class="stream_name inline-block">#{{ stream.name }}</div>
                        {%- endfor -%}
                        )
                    </label>
                </div>
                {% endfor %}
            </div>
            <hr />
            {% endif %}

            <div class="input-group margin terms-of-service">
                {% if terms_of_service %}
                <div class="input-group">
                    {#
                    This is somewhat subtle.
                    Checkboxes have a name and value, and when the checkbox is ticked, the form posts
                    with name=value. If the checkbox is unticked, the field just isn't present at all.

                    This is distinct from 'checked', which determines whether the checkbox appears
                    at all. (So, it's not symmetric to the code above.)
                    #}
                    <label for="id_terms" class="inline-block checkbox">
                        <input id="id_terms" class="required" type="checkbox" name="terms"
                          {% if form.terms.value() %}checked="checked"{% endif %} />
                        <span></span>
                        {% trans %}I agree to the <a href="{{ root_domain_uri }}/policies/terms" target="_blank" rel="noopener noreferrer">Terms of Service</a>.{% endtrans %}
                    </label>
                    {% if form.terms.errors %}
                        {% for error in form.terms.errors %}
                        <p class="help-inline text-error">{{ error }}</p>
                        {% endfor %}
                    {% endif %}
                </div>
                {% endif %}
                {% if corporate_enabled %}
                <div class="input-group">
                    <label for="id_enable_marketing_emails" class="inline-block checkbox marketing_emails_checkbox">
                        <input id="id_enable_marketing_emails" type="checkbox" name="enable_marketing_emails"
                          checked="checked" />
                        <span></span>
                        {% trans %}Subscribe me to Zulip's low-traffic newsletter (a few emails a year).{% endtrans %}
                    </label>
                </div>
                {% endif %}
                <div class="register-button-box">
                    <button class="register-button" type="submit">
                        <span>{{ _('Sign up') }}</span>
                        <object class="loader" type="image/svg+xml" data="{{ static('images/loading/loader-white.svg') }}"></object>
                    </button>
                    <input type="hidden" name="next" value="{{ next }}" />
                </div>
            </div>
        </form>

    </div>
</div>

{% if not creating_new_realm %}
<div class="micromodal" id="change-email-address-visibility-modal" aria-hidden="true">
    <div class="modal__overlay" tabindex="-1">
        <div class="modal__container" role="dialog" aria-modal="true" aria-labelledby="dialog_title">
            <header class="modal__header">
                <h1 class="modal__title dialog_heading">
                    {{ _('Configure email address privacy') }}
                </h1>
                <button class="modal__close" aria-label="{{ _('Close modal') }}" data-micromodal-close></button>
            </header>
            <main class="modal__content">
                <p>
                    {{ _('Zulip lets you control which roles in the organization can view your email address.') }}
                    {{ _('Do you want to change the privacy setting for your email from the default configuration for this organization?') }}
                </p>
                <label for="new_user_email_address_visibility">{{ _('Who can access your email address') }}</label>
                <select id="new_user_email_address_visibility" class="modal_select">
                    {% for value, name in email_address_visibility_options_dict.items() %}
                        <option value="{{ value }}" {% if value == default_email_address_visibility %}selected{% endif %}>{{name}}</option>
                    {% endfor %}
                </select>
                <p>
                    {% trans %}You can also change this setting <a href="{{ root_domain_uri }}/help/configure-email-visibility" target="_blank" rel="noopener noreferrer">after you join</a>.{% endtrans %}
                </p>
            </main>
            <footer class="modal__footer">
                <button class="modal__btn dialog_cancel_button" aria-label="{{ '(Close this dialog window)' }}" data-micromodal-close>{{ _('Cancel') }}</button>
                <button class="modal__btn dialog_submit_button">
                    <span>{{ _('Confirm') }}</span>
                </button>
            </footer>
        </div>
    </div>
</div>
{% endif %}

{% endblock %}

</pre>
#### social_auth_select_email.html ####
<pre>
{% extends "zerver/portico_signup.html" %}

{% block title %}
<title>{{ _("Select account for authentication") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<div class="register-account flex full-page new-style" id="choose_email">
    <div class="lead">
        {% trans %}
        <h1 class="get-started">Select account</h1>
        {% endtrans %}
    </div>

    <div class="white-box">
        <form method="post" class="select-email-form" action="/complete/{{ backend }}/">
            <div class="choose-email-box">
                <input type="hidden" name="email" value="{{ primary_email }}" />
                {% if avatar_urls[primary_email] %}
                <img src="{{ avatar_urls[primary_email] }}" alt=""/>
                {% else %}
                <i class="fa fa-plus" aria-hidden="true"></i>
                {% endif %}
                <div>
                    <p class="email">
                        {{ primary_email }}
                    </p>
                    <p>
                        GitHub primary
                        {% if avatar_urls[primary_email] %}
                        - Log in
                        {% else %}
                        - Create new account
                        {% endif %}
                    </p>
                </div>
            </div>
        </form>
        {% for email in verified_non_primary_emails %}
        <form method="post" class="select-email-form" action="/complete/{{ backend }}/">
            <div class="choose-email-box">
                <input type="hidden" name="email" value="{{ email }}" />
                {% if avatar_urls[email] %}
                <img src="{{ avatar_urls[email] }}" alt="" class="no-drag"/>
                {% else %}
                <i class="fa fa-plus" aria-hidden="true"></i>
                {% endif %}
                <div>
                    <p class="email">
                        {{ email }}
                    </p>
                    <p>
                        {% if avatar_urls[email] %}
                        Log in
                        {% else %}
                        Create new account
                        {% endif %}
                    </p>
                </div>
            </div>
        </form>
        {% endfor %}
    </div>
    {% if unverified_emails %}
    <div class="bottom-text">
        <p>
            {% trans %}
            Your GitHub account also has unverified email addresses
            associated with it.
            {% endtrans %}
        </p>
        <p>
            {% trans %}
            To use one of these to log in to Zulip, you must first
            <a href="https://github.com/settings/emails">verify it with GitHub.</a>
            {% endtrans %}
        </p>
    </div>
    {% endif %}
</div>
{% endblock %}

</pre>
#### emoji_popover_content.hbs ####
<pre>
<div class="emoji-popover">
    <div class="emoji-popover-top">
        <input class="emoji-popover-filter" type="text" autofocus placeholder="{{t 'Search' }}" />
        <i class="fa fa-search" aria-hidden="true"></i>
    </div>
    <div class="emoji-popover-category-tabs">
        {{#each emoji_categories}}
            <span class="emoji-popover-tab-item {{#if @first}} active {{/if}}" data-tab-name='{{name}}' title='{{name}}'><i class="fa {{icon}}"></i></span>
        {{/each}}
    </div>
    <div class="emoji-popover-emoji-map" data-simplebar data-simplebar-auto-hide="false" data-message-id="{{message_id}}">
        {{#each emoji_categories }}
            <div class="emoji-popover-subheading" data-section="{{name}}">{{name}}</div>
            <div class="emoji-collection" data-section="{{name}}">
                {{#each this.emojis }}
                    {{> emoji_popover_emoji type="emoji_picker_emoji" section=@../index index=@index message_id=../../message_id is_status_emoji_popover=../../is_status_emoji_popover emoji_dict=this}}
                {{/each}}
            </div>
        {{/each}}
    </div>
    <div class="emoji-search-results-container" data-simplebar data-simplebar-auto-hide="false" data-message-id="{{message_id}}">
        <div class="emoji-popover-results-heading">{{t "Search results" }}</div>
        <div class="emoji-search-results"></div>
    </div>
</div>

</pre>
#### change_email_modal.hbs ####
<pre>
<form id="change_email_form" class="new-style">
    <label for="email">{{t "New email" }}</label>
    <input type="text" name="email" class="modal_text_input" value="{{delivery_email}}" autocomplete="off" spellcheck="false" autofocus="autofocus"/>
</form>

</pre>
#### message_avatar.hbs ####
<pre>
<div class="u-{{msg/sender_id}} inline_profile_picture {{#sender_is_guest}} guest-avatar{{/sender_is_guest}} view_user_card_tooltip" aria-hidden="true">
    <img src="{{small_avatar_url}}" alt="" class="no-drag"/>
</div>
{{~! remove whitespace ~}}

</pre>
#### non_editable_user_group.hbs ####
<pre>
{{#with user_group}}
<div class="user-group white-box ntm" id="{{id}}">
    <h4>
        <span class="name" data-placeholder="{{t 'Name' }}">{{name}}</span>
        —
        <span class="description" data-placeholder="{{t 'Description' }}">{{description}}</span>
    </h4>
    <p class="subscribers">{{t 'Subscribers' }}</p>
    <div class="pill-container not-editable" data-group-pills="{{id}}"></div>
</div>
{{/with}}

</pre>
#### message_body.hbs ####
<pre>
{{#unless status_message}}
<span class="message_sender sender_info_hover no-select">
    {{#if include_sender}}
    <span>
        {{> message_avatar ~}}
        <span class="sender_name auto-select" role="button" tabindex="0">
            <span class="sender_name_padding view_user_card_tooltip"></span>
            <span class="view_user_card_tooltip">{{msg/sender_full_name}}{{> status_emoji msg/status_emoji_info}}</span>
        </span>
        {{#if sender_is_bot}}
        <i class="zulip-icon zulip-icon-bot" aria-label="{{t 'Bot' }}"></i>
        {{/if}}
        {{#if edited_alongside_sender}}
        {{> edited_notice}}
        {{/if}}
    </span>
    {{/if}}
</span>
{{/unless}}

{{#if status_message}}
{{> me_message}}
{{/if}}

<span class="alert-msg"></span>

<a href="{{ msg/url }}" class="message_time{{#if status_message}} status-time{{/if}}">
    {{#unless include_sender}}
    <span class="copy-paste-text">&nbsp;</span>
    {{/unless}}
    {{timestr}}
</a>

{{> message_controls}}

{{#unless status_message}}
    {{#unless is_hidden}}
    <div class="message_content rendered_markdown">
        {{#if use_match_properties}}
            {{rendered_markdown msg/match_content}}
        {{else}}
            {{rendered_markdown msg/content}}
        {{/if}}
    </div>
    {{else}}
    <div class="message_content rendered_markdown">
        {{> message_hidden_dialog}}
    </div>
    {{/unless}}
{{/unless}}

{{#if edited_in_left_col}}
{{> edited_notice}}
{{/if}}

<div class="message_edit">
    <div class="message_edit_form"></div>
</div>
<div class="message_expander message_length_controller" title="{{t 'Expand message (-)' }}">{{t "[More…]" }}</div>
<div class="message_condenser message_length_controller" title="{{t 'Show less' }} (-)">[{{t "Show less" }}]</div>

{{#unless is_hidden}}
<div class="message_reactions">{{> message_reactions }}</div>
{{/unless}}

</pre>
#### create_realm.html ####
<pre>
{% extends "zerver/portico_signup.html" %}
{# Home page for not logged-in users. #}

{% block title %}
<title>{{ _("Create a new organization") }} | Zulip</title>
{% endblock %}

{# This is where we pitch the app and solicit signups. #}

{% block portico_content %}
<div class="app register-page">
    <div class="app-main register-page-container new-style flex full-page center">

        <div class="register-form left" id="new-realm-creation">
            <div class="lead">
                <h1 class="get-started">{{ _("Create a new Zulip organization") }}</h1>
            </div>
            <div class="white-box">
                <form class="form-inline" id="create_realm" name="email_form"
                  action="{{ current_url() }}" method="post">
                    {{ csrf_input }}

                    {% include 'zerver/realm_creation_form.html' %}

                    <div class="input-box horizontal">
                        <div class="inline-block relative">
                            <input type="text" class="email required" placeholder="{{ _("Enter your email address") }}"
                              id="email" name="email" required />
                            <label for="email">{{ _('Your email') }}</label>
                        </div>
                        {% if form.email.errors %}
                        {% for error in form.email.errors %}
                            <div class="alert alert-error">{{ error }}</div>
                        {% endfor %}
                        {% endif %}
                    </div>
                    <div class="input-box">
                        <button type="submit" class="new-organization-button register-button">{{ _("Create organization") }}</button>
                    </div>
                </form>
            </div>
            <div class="bottom-text">
                {% trans %}
                Or import
                from <a href="/help/import-from-slack">Slack</a>, <a href="/help/import-from-mattermost">Mattermost</a>,
                <a href="/help/import-from-gitter">Gitter</a>, or <a href="/help/import-from-rocketchat">Rocket.Chat</a>.
                {% endtrans %}
            </div>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### topic_list_item.hbs ####
<pre>
<li class='bottom_left_row {{#if is_active_topic}}active-sub-filter{{/if}} {{#if is_zero}}zero-topic-unreads{{/if}} {{#if is_muted}}muted_topic{{/if}} topic-list-item' data-topic-name='{{topic_name}}'>
    <span class='topic-box'>
        <span class="sidebar-topic-check">
            {{topic_resolved_prefix}}
        </span>
        <a href='{{url}}' class="topic-name" title="{{topic_name}}">
            {{topic_display_name}}
        </a>
        {{#if contains_unread_mention}}
            <span class="unread_mention_info">
                @
            </span>
        {{/if}}
        <span class="unread_count {{#if is_zero}}zero_count{{/if}}">
            {{unread}}
        </span>
    </span>
    <span class="topic-sidebar-menu-icon">
        <i class="zulip-icon zulip-icon-ellipsis-v-solid" aria-hidden="true"></i>
    </span>
</li>

</pre>
#### markdown_timestamp.hbs ####
<pre>
<i class="fa fa-clock-o"></i>
{{ text }}

</pre>
#### markdown_help.hbs ####
<pre>
<div class="overlay-modal hide" id="message-formatting" tabindex="-1" role="dialog"
  aria-label="{{t 'Message formatting' }}">
    <div class="modal-body" data-simplebar data-simplebar-auto-hide="false">
        <div id="markdown-instructions">
            <table class="table table-striped table-condensed table-rounded table-bordered help-table">
                <thead>
                    <tr>
                        <th>{{t "You type" }}</th>
                        <th>{{t "You get" }}</th>
                    </tr>
                </thead>

                <tbody>
                    {{#each markdown_help_rows}}
                        <tr>
                            {{#if note_html}}
                            <td colspan="2">{{{note_html}}}</td>
                            {{else}}
                            <td><div class="preserve_spaces">{{markdown}}</div> {{{usage_html}}}</td>
                            <td class="rendered_markdown">{{{output_html}}} {{{effect_html}}}</td>
                            {{/if}}
                        </tr>
                    {{/each}}
                </tbody>
            </table>
        </div>
        <hr />
        <a href="/help/format-your-message-using-markdown" target="_blank" rel="noopener noreferrer">{{t "Detailed message formatting documentation" }}</a>
    </div>
</div>

</pre>
#### base.html ####
<pre>
<!DOCTYPE html>
<html lang='{{LANGUAGE_CODE}}' {% if color_scheme == 1 %} class="color-scheme-automatic" {% elif color_scheme == 2 %} class="dark-theme" {% endif %}>

    {# Base template for the whole site. #}

    <head>
        <meta charset="UTF-8" />
        {% block title %}
            {% if user_profile and user_profile.realm.name %}
                <title>{{user_profile.realm.name}} - Zulip</title>
            {% else %}
                {% if PAGE_TITLE %}
                <title>{{ PAGE_TITLE }}</title>
                {% endif %}
            {% endif %}
        {% endblock %}
        <link id="favicon" rel="icon" href="{{ static('images/favicon.svg') }}?v=4" />
        <link rel="alternate icon" href="{{ static('images/favicon.png') }}?v=4" />
        {% block meta_viewport %}
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        {% endblock %}
        {% if not user_profile %}
        {% include 'zerver/meta_tags.html' %}
        {% endif %}

        {% block webpack %}
            {% for filename in webpack_entry(entrypoint) -%}
                {% if filename.endswith(".css") -%}
                    <link href="{{ filename }}" rel="stylesheet" {% if csp_nonce %}nonce="{{ csp_nonce }}"{% endif %} />
                {% elif filename.endswith(".js") -%}
                    <script src="{{ filename }}" defer {% if csp_nonce %}nonce="{{ csp_nonce }}"{% endif %}></script>
                {% endif -%}
            {% endfor %}
        {% endblock %}

        {% block customhead %}
        {% endblock %}
    </head>

    <body>
        {% block content %}
        {% endblock %}

        {% set all_page_params = default_page_params.copy() %}
        {% set _ = all_page_params.update(page_params|default({})) %}
        <div hidden id="page-params" data-params='{{ all_page_params|tojson }}'></div>
    </body>

</html>

{% set entrypoint = entrypoint|default("common") %}

</pre>
#### actions_popover_template.hbs ####
<pre>
<div class="popover actions_popover_wrapper">
    <div class="arrow hide-xl"></div>
    <div class="popover-content">
        <div></div>
    </div>
</div>

</pre>
#### about_zulip.hbs ####
<pre>
<div id="about-zulip" class="overlay flex new-style" tabindex="-1" role="dialog" data-overlay="about-zulip" aria-hidden="true">
    <div class="overlay-content modal-bg">
        <button type="button" class="exit" aria-label="{{t 'Close' }}"><span aria-hidden="true">&times;</span></button>
        <div class="modal-body">
            <div class="about-zulip-logo">
                <a target="_blank" rel="noopener noreferrer" href="https://zulip.com"><img src="../../static/images/logo/zulip-org-logo.svg" alt="{{t 'Zulip' }}" /></a>
            </div>
            <p>
                <strong>Zulip Server</strong>
                <br />
                {{t "Version {zulip_version}" }}
                <i class="fa fa-copy tippy-zulip-tooltip" data-tippy-content="{{t 'Copy version' }}" data-tippy-placement="right" data-clipboard-text="{{zulip_version}}"></i>
                {{#if is_fork}}
                    <br />
                    {{t "Forked from upstream at {zulip_merge_base}" }}
                    <i class="fa fa-copy tippy-zulip-tooltip" data-tippy-content="{{t 'Copy version' }}" data-tippy-placement="right" data-clipboard-text="{{zulip_merge_base}}"></i>
                {{/if}}
            </p>
            <p>
                Copyright 2012–2015 Dropbox, Inc., 2015–2021 Kandra Labs, Inc., and contributors.
            </p>
            <p>
                Zulip is <a target="_blank" rel="noopener noreferrer" href="https://github.com/zulip/zulip#readme">open-source software</a>,
                distributed under the Apache 2.0 license.
            </p>
        </div>
    </div>
</div>

</pre>
#### topic_edit_form.hbs ####
<pre>
{{! Client-side Handlebars template for rendering the topic edit form. }}

<form id="topic_edit_form">
    <input type="text" value="" class="inline_topic_edit header-v" id="inline_topic_edit"
      autocomplete="off" maxlength="{{ max_topic_length }}" />
    <button type="button" class="topic_edit_save small_square_button animated-purple-button"><i class="fa fa-check" aria-hidden="true"></i></button>
    <button type="button" class="topic_edit_cancel small_square_button small_square_x"><i class="fa fa-remove" aria-hidden="true"></i></button>
    <div class="alert alert-error edit_error" style="display: none"></div>
    <div class="topic_edit_spinner"></div>
</form>

</pre>
#### single_message.hbs ####
<pre>
<div zid="{{msg/id}}" id="{{table_name}}{{msg/id}}"
  class="message_row{{#unless msg/is_stream}} private-message{{/unless}}{{#include_sender}} include-sender{{/include_sender}}{{#if mention_classname}} {{mention_classname}}{{/if}}{{#msg.unread}} unread{{/msg.unread}} {{#if msg.locally_echoed}}local{{/if}} selectable_row"
  role="listitem">
    <div class="unread_marker"><div class="unread-marker-fill"></div></div>
    {{#if want_date_divider}}
    <div class="date_row no-select" {{#if msg/is_stream}}style="box-shadow: inset 3px 0px 0px -1px {{background_color}}, -1px 0px 0px 0px {{background_color}};"{{/if}}>{{{date_divider_html}}}</div>
    {{/if}}
    <div class="messagebox"
      {{#if msg/is_stream}}style="box-shadow: inset 3px 0px 0px -1px {{background_color}}, -1px 0px 0px 0px {{background_color}};"{{/if}}>
        <div class="messagebox-content">
            {{> message_body}}
        </div>
    </div>
</div>

</pre>
#### compose_control_buttons_popover.hbs ####
<pre>
<div class="compose_control_buttons_container order-1">
    {{> compose_control_buttons_in_popover}}
</div>

</pre>
#### confirm_continue_registration.html ####
<pre>
{% extends "zerver/portico_signup.html" %}

{% block title %}
<title>{{ _("Account not found") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<div class="app register-page">
    <div class="app-main confirm-continue-page-container">
        <div class="center-container">
            <div class="center-block">
                <div class="register-form new-style">
                    <div class="lead">
                        <h1 class="get-started">{{ _("Zulip account not found.") }}</h1>
                    </div>
                    <div class="white-box">
                        <p>
                            {% trans %}
                            No account found for {{ email }}.
                            {% endtrans %}
                        </p>
                        <div style="text-align: center;">
                            <form class="form-inline" id="send_confirm" name="send_confirm"
                              action="/login/" method="get">
                                <input type="hidden"
                                  id="email"
                                  name="email"
                                  value="{{ email }}" />
                                <button>
                                    {{ _("Log in with another account") }}
                                </button>
                            </form>
                            <br />
                            <form class="form-inline" id="send_confirm" name="send_confirm"
                              action="{{ continue_link }}" method="get">
                                <button class="outline">
                                    {{ _("Continue to registration") }}
                                </button>
                                {% if full_name %}
                                <input type="hidden" name="full_name" value="{{ full_name }}" />
                                {% endif %}
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <div class="footer-padder"></div>
</div>

{% endblock %}

</pre>
#### stream_privacy.hbs ####
<pre>
{{! This controls whether the swatch next to streams in the left sidebar has a lock icon. }}
{{#if invite_only}}
<i class="fa fa-lock" aria-hidden="true"></i>
{{else if is_web_public}}
<i class="zulip-icon zulip-icon-globe" aria-hidden="true"></i>
{{else}}
<span class="hashtag"></span>
{{/if}}

</pre>
#### typing_notification.hbs ####
<pre>
<li data-email="{{this.email}}" class="typing_notification">{{t "{full_name} is typing…" }}</li>

</pre>
#### message_feed_bottom_whitespace.hbs ####
<pre>
<div class="bottom-messages-logo">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 773.12 773.12">
        <circle cx="386.56" cy="386.56" r="386.56"/>
        <path d="M566.66 527.25c0 33.03-24.23 60.05-53.84 60.05H260.29c-29.61 0-53.84-27.02-53.84-60.05 0-20.22 9.09-38.2 22.93-49.09l134.37-120c2.5-2.14 5.74 1.31 3.94 4.19l-49.29 98.69c-1.38 2.76.41 6.16 3.25 6.16h191.18c29.61 0 53.83 27.03 53.83 60.05zm0-281.39c0 20.22-9.09 38.2-22.93 49.09l-134.37 120c-2.5 2.14-5.74-1.31-3.94-4.19l49.29-98.69c1.38-2.76-.41-6.16-3.25-6.16H260.29c-29.61 0-53.84-27.02-53.84-60.05s24.23-60.05 53.84-60.05h252.54c29.61 0 53.83 27.02 53.83 60.05z"/>
    </svg>
</div>
<div id="loading_newer_messages_indicator"></div>

</pre>
#### emoji_popover_emoji.hbs ####
<pre>
{{#with emoji_dict}}
<div class="emoji-popover-emoji {{#if ../message_id }}{{#if has_reacted}} reacted {{/if}} reaction {{else if ../is_status_emoji_popover}} status-emoji {{else}} composition {{/if}}" data-emoji-name="{{name}}" tabindex="0" data-emoji-id="{{../type}},{{../section}},{{../index}}">
    {{#if is_realm_emoji}}
    <img src="{{url}}" class="emoji"/>
    {{else}}
    <div class="emoji emoji-{{emoji_code}}"></div>
    {{/if}}
</div>
{{/with}}

</pre>
#### message_view_header.hbs ####
<pre>
{{#if stream_settings_link}}
<a class="stream" href="{{stream_settings_link}}">
    {{> navbar_icon_and_title }}
</a>
<div class="divider only-visible-for-spectators">|</div>
<a class="sub_count no-style tippy-zulip-tooltip hidden-for-spectators" data-tippy-content="{{sub_count_tooltip_text}}" data-tippy-placement="bottom" href="{{stream_settings_link}}">
    <i class="fa fa-user-o"></i>{{formatted_sub_count}}
</a>
<span class="narrow_description navbar-click-opens-search rendered_markdown">
    {{#if rendered_narrow_description}}
    {{rendered_markdown rendered_narrow_description}}
    {{else}}
    {{t "(no description)"}}
    {{/if}}
</span>
{{else}}
<span class="navbar-click-opens-search">
    {{> navbar_icon_and_title }}
</span>
{{/if}}
<span class="search_icon search_closed" role="button"><i class="zulip-icon zulip-icon-search" aria-hidden="true"></i></span>

</pre>
#### accounts_home.html ####
<pre>
{% extends "zerver/portico_signup.html" %}
{# Home page for not logged-in users. #}

{% block title %}
<title>{{ _("Sign up") }} | Zulip</title>
{% endblock %}

{# This is where we pitch the app and solicit signups. #}

{% block portico_content %}

<!-- The following empty tag has unique data-page-id so that this
page can be easily identified in it's respective JavaScript file -->
<div data-page-id="accounts-home"></div>
<div class="app register-page split-view flex full-page new-style">
    <div class="inline-block">
        <div class="lead">
            <h1 class="get-started">{{ _("Sign up for Zulip") }}</h1>
        </div>
        <div class="app-main register-page-container white-box {% if realm_invite_required and not from_multiuse_invite %}closed-realm{% endif %}">
            <div class="register-form new-style">
                {% if realm_name %}
                <div class="left-side">
                    <div class="org-header">
                        <img class="avatar" src="{{ realm_icon }}" alt="" />
                        <div class="info-box">
                            <div class="organization-name">{{ realm_name }}</div>
                            <div class="organization-path">{{ realm_uri }}</div>
                        </div>
                    </div>
                    <div class="description">
                        {{ realm_description|safe }}
                    </div>

                    <div class="invite-required">
                        <hr />
                        <i class="fa fa-lock"></i>{{ _("You need an invitation to join this organization.") }}
                    </div>
                </div>
                {% endif %}

                <div class="right-side">
                    {% if no_auth_enabled %}
                        <div class="alert">
                            <p>No authentication backends are enabled on this
                            server yet, so it is impossible to register!</p>

                            <p>
                                See
                                the <a href="https://zulip.readthedocs.io/en/latest/production/install.html#step-3-configure-zulip">Zulip
                                authentication documentation</a> to learn how to
                                configure authentication backends.
                            </p>
                        </div>
                    {% else %}
                        {% if password_auth_enabled %}
                            <form class="form-inline" id="send_confirm" name="email_form"
                              action="{{ current_url() }}" method="post">
                                {{ csrf_input }}

                                <div class="input-box no-validate">
                                    <input type="email" id="email" class="email" name="email" value="" autofocus required />
                                    <label for="email">Email</label>
                                    <div class="alert alert-error email-frontend-error"></div>
                                    {% if form.email.errors %}
                                        {% for error in form.email.errors %}
                                        <div class="email-backend-error alert alert-error">{{ error }}</div>
                                        {% endfor %}
                                    {% endif %}
                                </div>

                                <button class="full-width" type="submit">{{ _('Sign up') }}</button>
                            </form>

                            {% if page_params.external_authentication_methods|length > 0 %}
                            <div class="or"><span>{{ _('OR') }}</span></div>
                            {% endif %}
                        {% endif %}

                        {% for backend in page_params.external_authentication_methods %}
                        <div class="login-social">
                            <form class="form-inline" action="{{ backend.signup_url }}" method="get">
                                <input type='hidden' name='multiuse_object_key' value='{{ multiuse_object_key }}' />
                                <button id="register_{{ backend.button_id_suffix }}" class="login-social-button full-width"
                                  {% if backend.display_icon %} style="background-image:url({{ backend.display_icon }})"  {% endif %}>
                                    {{ _('Sign up with %(identity_provider)s', identity_provider=backend.display_name) }}
                                </button>
                            </form>
                        </div>
                        {% endfor %}
                    {% endif %}
                </div>
            </div>
        </div>
    </div>
</div>

{% endblock %}

</pre>
#### documentation_main.html ####
<pre>
{% extends "zerver/portico-help.html" %}
{% set entrypoint = "help" %}

{# Zulip user and API documentation. #}
{% block title %}
<title>{{ PAGE_TITLE }}</title>
{% endblock %}

{% block portico_content %}
<div class="app help terms-page inline-block{% if page_is_help_center %} help-center{% endif %}{% if page_is_api_center %} api-center{% endif %}">
    <div class="sidebar">
        <div class="content">
            {% if not page_is_policy_center %}
            <h1><a href="https://zulip.com" class="no-underline">Zulip homepage</a></h1>
            <h1><a href="{{ doc_root }}" class="no-underline">{{ doc_root_title }} home</a></h1>
            {% endif %}

            {% if page_is_policy_center %}
            {{ render_markdown_path(sidebar_index) }}
            {% elif page_is_help_center %}
            {{ render_markdown_path(sidebar_index) }}
            {% else %}
            {{ render_markdown_path(sidebar_index, context=api_uri_context) }}
            {% endif %}

            {% if not page_is_policy_center %}
            <h1 class="home-link"><a href="/" class="no-underline">Back to Zulip</a></h1>
            {% endif %}
        </div>
    </div>

    <svg height="32px" class="hamburger" style="enable-background:new 0 0 32 32;" version="1.1" viewBox="0 0 32 32" width="32px" xml:space="preserve" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
        <path d="M4,10h24c1.104,0,2-0.896,2-2s-0.896-2-2-2H4C2.896,6,2,6.896,2,8S2.896,10,4,10z M28,14H4c-1.104,0-2,0.896-2,2  s0.896,2,2,2h24c1.104,0,2-0.896,2-2S29.104,14,28,14z M28,22H4c-1.104,0-2,0.896-2,2s0.896,2,2,2h24c1.104,0,2-0.896,2-2  S29.104,22,28,22z"></path>
    </svg>

    <div class="markdown">
        <div class="content">
            {% if page_is_policy_center %}
            {{ render_markdown_path(article) }}
            {% elif page_is_help_center %}
            {{ render_markdown_path(article, context=api_uri_context, help_center=True) }}
            {% else %}
            {{ render_markdown_path(article, context=api_uri_context) }}
            {% endif %}

            <div class="documentation-footer">
                <hr />
                {% if corporate_enabled %}
                    {% if page_is_policy_center %}
                    <p>Please contact {{ support_email_html_tag }} with any questions about Zulip's policies.</p>
                    {% else %}
                    <p>Your feedback helps us make Zulip better for everyone! Please <a href="mailto:{{ support_email }}">contact us</a> with questions, suggestions, and feature requests.</p>
                    {% endif %}
                {% else %}
                    <p>Don't see an answer to your question? <a href="mailto:{{ support_email }}">Contact this Zulip server's administrators</a> for support.</p>
                {% endif %}
            </div>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### topic_muted.hbs ####
<pre>
{{#tr}}
    You have muted <z-stream-topic></z-stream-topic>.
    {{#*inline "z-stream-topic"}}<strong><span class="stream"></span> &gt; <span class="topic"></span></strong>{{/inline}}
{{/tr}}

</pre>
#### subscribe_to_more_streams.hbs ####
<pre>
{{#if exactly_one_unsubscribed_stream}}
    <a href="#streams/all">
        <i class="fa fa-plus-circle" aria-hidden="true"></i>
        {{~#tr}}Browse 1 more stream{{/tr~}}
    </a>
{{else if can_subscribe_stream_count}}
    <a href="#streams/all">
        <i class="fa fa-plus-circle" aria-hidden="true"></i>
        {{~#tr}}Browse {can_subscribe_stream_count} more streams{{/tr~}}
    </a>
{{else if can_create_streams}}
    <a href="#streams/new">
        <i class="fa fa-plus-circle" aria-hidden="true"></i>
        {{~t "Create a stream"~}}
    </a>
{{/if}}

</pre>
#### keyboard_shortcuts.hbs ####
<pre>
<div class="overlay-modal" id="keyboard-shortcuts" tabindex="-1" role="dialog"
  aria-label="{{t 'Keyboard shortcuts' }}">
    <div class="modal-body" data-simplebar data-simplebar-auto-hide="false">
        <div>
            <table class="hotkeys_table table table-striped table-bordered table-condensed">
                <thead>
                    <tr>
                        <th colspan="2">{{t "The basics" }}</th>
                    </tr>
                </thead>
                <tr>
                    <td class="definition">{{t 'Reply to message' }}</td>
                    <td><span class="hotkey"><kbd>Enter</kbd> or <kbd>R</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'New stream message' }}</td>
                    <td><span class="hotkey"><kbd>C</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'New direct message' }}</td>
                    <td><span class="hotkey"><kbd>X</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Cancel compose and save draft' }}</td>
                    <td><span class="hotkey"><kbd>Esc</kbd> or <kbd>Ctrl</kbd> + <kbd>[</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'View drafts' }}</td>
                    <td><span class="hotkey"><kbd>D</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Next message' }}</td>
                    <td><span class="hotkey"><kbd class="arrow-key">↓</kbd> or <kbd>J</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Last message' }}</td>
                    <td><span class="hotkey"><kbd>End</kbd> or <kbd>Shift</kbd> + <kbd>G</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Next unread topic' }}</td>
                    <td><span class="hotkey"><kbd>N</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Next unread direct message' }}</td>
                    <td><span class="hotkey"><kbd>P</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Initiate a search' }}</td>
                    <td><span class="hotkey"><kbd>Ctrl</kbd> + <kbd>K</kbd> or <kbd>/</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Show keyboard shortcuts' }}</td>
                    <td><span class="hotkey"><kbd>?</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Go to default view' }}</td>
                    <td><span class="hotkey"><kbd>Ctrl</kbd> + <kbd>[</kbd><span id="go-to-default-view-hotkey-help"> or <kbd>Esc</kbd></span></span></td>
                </tr>
            </table>
        </div>
        <div>
            <table class="hotkeys_table table table-striped table-bordered table-condensed">
                <thead>
                    <tr>
                        <th colspan="2">{{t 'Navigation' }}</th>
                    </tr>
                </thead>
                <tr>
                    <td class="definition">{{t 'Initiate a search' }}</td>
                    <td><span class="hotkey"><kbd>Ctrl</kbd> + <kbd>K</kbd> or <kbd>/</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Filter streams' }}</td>
                    <td><span class="hotkey"><kbd>Q</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Search people' }}</td>
                    <td><span class="hotkey"><kbd>W</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Previous message' }}</td>
                    <td><span class="hotkey"><kbd class="arrow-key">↑</kbd> or <kbd>K</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Next message' }}</td>
                    <td><span class="hotkey"><kbd class="arrow-key">↓</kbd> or <kbd>J</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Scroll up' }}</td>
                    <td><span class="hotkey"><kbd>PgUp</kbd> or <kbd>Shift</kbd> + <kbd>K</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Scroll down' }}</td>
                    <td><span class="hotkey"><kbd>PgDn</kbd> or <kbd>Shift</kbd> + <kbd>J</kbd> or <kbd>Space</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Last message' }}</td>
                    <td><span class="hotkey"><kbd>End</kbd> or <kbd>Shift</kbd> + <kbd>G</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'First message' }}</td>
                    <td><span class="hotkey"><kbd>Home</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Go back through viewing history' }}</td>
                    <td><span class="hotkey"><kbd>Alt</kbd> + <kbd class="arrow-key">←</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Go forward through viewing history' }}</td>
                    <td><span class="hotkey"><kbd>Alt</kbd> + <kbd class="arrow-key">→</kbd></span></td>
                </tr>
            </table>
        </div>
        <div>
            <table class="hotkeys_table table table-striped table-bordered table-condensed">
                <thead>
                    <tr>
                        <th colspan="2">{{t 'Composing messages' }}</th>
                    </tr>
                </thead>
                <tr>
                    <td class="definition">{{t 'Reply to message' }}</td>
                    <td><span class="hotkey"><kbd>Enter</kbd> or <kbd>R</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Reply to author' }}</td>
                    <td><span class="hotkey"><kbd>Shift</kbd> + <kbd>R</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Quote and reply to message' }}</td>
                    <td><span class="hotkey"><kbd>></kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'New stream message' }}</td>
                    <td><span class="hotkey"><kbd>C</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'New direct message' }}</td>
                    <td><span class="hotkey"><kbd>X</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Compose a reply @-mentioning author' }}</td>
                    <td><span class="hotkey"><kbd>@</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Send message' }}</td>
                    <td><span class="hotkey"><span class="small_hotkey"><kbd>Tab</kbd> then <kbd>Enter</kbd> or <kbd>Ctrl</kbd> + <kbd>Enter</kbd></span></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Insert new line' }}</td>
                    <td><span class="hotkey"><kbd>Shift</kbd> + <kbd>Enter</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Cancel compose and save draft' }}</td>
                    <td><span class="hotkey"><kbd>Esc</kbd> or <kbd>Ctrl</kbd> + <kbd>[</kbd></span></td>
                </tr>
            </table>
        </div>
        <div>
            <table class="hotkeys_table table table-striped table-bordered table-condensed">
                <thead>
                    <tr>
                        <th colspan="2">{{t 'Narrowing' }}</th>
                    </tr>
                </thead>
                <tr>
                    <td class="definition">{{t 'Narrow to stream' }}</td>
                    <td><span class="hotkey"><kbd>S</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Narrow to topic or DM conversation' }}</td>
                    <td><span class="hotkey"><kbd>Shift</kbd> + <kbd>S</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Narrow to all direct messages' }}</td>
                    <td><span class="hotkey"><kbd>Shift</kbd> + <kbd>P</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Zoom to message in conversation context' }}</td>
                    <td><span class="hotkey"><kbd>Z</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Narrow to next unread topic' }}</td>
                    <td><span class="hotkey"><kbd>N</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Narrow to next unread direct message' }}</td>
                    <td><span class="hotkey"><kbd>P</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Cycle between stream narrows' }}</td>
                    <td><span class="hotkey"><kbd>Shift</kbd> + <kbd>A</kbd> or <kbd>Shift</kbd> + <kbd>D</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Narrow to all unmuted messages' }}</td>
                    <td><span class="hotkey"><kbd>A</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Narrow to current compose box recipient' }}</td>
                    <td><span class="hotkey"><kbd>Ctrl</kbd> + <kbd>.</kbd></span></td>
                </tr>
            </table>
        </div>
        <div>
            <table class="hotkeys_table table table-striped table-bordered table-condensed">
                <thead>
                    <tr>
                        <th colspan="2">{{t 'Message actions' }}</th>
                    </tr>
                </thead>
                <tr>
                    <td class="definition">{{t 'Edit your last message' }}</td>
                    <td><span class="hotkey"><kbd class="arrow-key">←</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t "Show message sender's user card"   }}</td>
                    <td><span class="hotkey"><kbd>U</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Show images in thread' }}</td>
                    <td><span class="hotkey"><kbd>V</kbd></span></td>
                </tr>
                <tr id="edit-message-hotkey-help">
                    <td class="definition">{{t 'Edit selected message or view source' }}</td>
                    <td><span class="hotkey"><kbd>E</kbd></span></td>
                </tr>
                <tr id="move-message-hotkey-help">
                    <td class="definition">{{t 'Move messages or topic' }}</td>
                    <td><span class="hotkey"><kbd>M</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Star selected message' }}</td>
                    <td><span class="hotkey"><kbd>Ctrl</kbd> + <kbd>S</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">
                        {{t 'React to selected message with' }}
                        <img alt=":thumbs_up:"
                          class="emoji"
                          src="../../static/generated/emoji/images/emoji/unicode/1f44d.png"
                          title=":thumbs_up:"/>
                    </td>
                    <td><span class="hotkey"><kbd>+</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Toggle first emoji reaction on selected message' }}</td>
                    <td><span class="hotkey"><kbd>=</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Mark as unread from selected message' }}</td>
                    <td><span class="hotkey"><kbd>Shift</kbd> + <kbd>U</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Collapse/show selected message' }}</td>
                    <td><span class="hotkey"><kbd>-</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Toggle topic mute' }}</td>
                    <td><span class="hotkey"><kbd>Shift</kbd> + <kbd>M</kbd></span></td>
                </tr>
            </table>
        </div>
        <div>
            <table class="hotkeys_table table table-striped table-bordered table-condensed">
                <thead>
                    <tr>
                        <th colspan="2">{{t 'Recent conversations' }}</th>
                    </tr>
                </thead>
                <tr>
                    <td class="definition">{{t 'View recent conversations' }}</td>
                    <td><span class="hotkey"><kbd>T</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Filter topics' }}</td>
                    <td><span class="hotkey"><kbd>T</kbd></span></td>
                </tr>
            </table>
        </div>
        <div>
            <table class="hotkeys_table table table-striped table-bordered table-condensed">
                <thead>
                    <tr>
                        <th colspan="2">{{t 'Drafts' }}</th>
                    </tr>
                </thead>
                <tr>
                    <td class="definition">{{t 'View drafts' }}</td>
                    <td><span class="hotkey"><kbd>D</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Edit selected draft' }}</td>
                    <td><span class="hotkey"><kbd>Enter</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Delete selected draft' }}</td>
                    <td><span class="hotkey"><kbd>Backspace</kbd></span></td>
                </tr>
            </table>
        </div>
        <div>
            <table class="hotkeys_table table table-striped table-bordered table-condensed">
                <thead>
                    <tr>
                        <th colspan="2">{{t 'Menus' }}</th>
                    </tr>
                </thead>
                <tr>
                    <td class="definition">{{t 'Toggle the gear menu' }}</td>
                    <td><span class="hotkey"><kbd>G</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Open message menu' }}</td>
                    <td><span class="hotkey"><kbd>I</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Open reactions menu' }}</td>
                    <td><span class="hotkey"><kbd>:</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Show keyboard shortcuts' }}</td>
                    <td><span class="hotkey"><kbd>?</kbd></span></td>
                </tr>
            </table>
        </div>
        <div>
            <table class="hotkeys_table table table-striped table-bordered table-condensed">
                <thead>
                    <tr>
                        <th colspan="2">{{t 'Streams settings' }}</th>
                    </tr>
                </thead>
                <tr>
                    <td class="definition">{{t 'Scroll through streams' }}</td>
                    <td><span class="hotkey"><kbd class="arrow-key">↑</kbd> or <kbd class="arrow-key">↓</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Switch between tabs' }}</td>
                    <td><span class="hotkey"><kbd class="arrow-key">←</kbd> or <kbd class="arrow-key">→</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'View stream messages' }}</td>
                    <td><span class="hotkey"><kbd>Shift</kbd> + <kbd>V</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Subscribe to/unsubscribe from selected stream' }}</td>
                    <td><span class="hotkey"><kbd>Shift</kbd> + <kbd>S</kbd></span></td>
                </tr>
                <tr>
                    <td class="definition">{{t 'Create new stream' }}</td>
                    <td><span class="hotkey"><kbd>N</kbd></span></td>
                </tr>
            </table>
        </div>
        <hr />
        <a href="/help/keyboard-shortcuts" target="_blank" rel="noopener noreferrer">{{t 'Detailed keyboard shortcuts documentation' }}</a>
    </div>
</div>

</pre>
#### log_into_subdomain_token_invalid.html ####
<pre>
{% extends "zerver/portico_signup.html" %}

{% block title %}
<title>{{ _("Invalid or expired login session") }} | Zulip</title>
{% endblock %}

{% block portico_content %}
<div class="app portico-page">
    <div class="app-main portico-page-container center-block flex full-page account-creation new-style">
        <div class="inline-block">
            <div class="app-main white-box">
                <h1>{{ _("Invalid or expired login session.") }}</h1>
                <a href="{{ login_url }}">{{ _("Log in") }}</a>.
            </div>
        </div>
    </div>
</div>
{% endblock %}

</pre>
#### portico.html ####
<pre>
{% extends "zerver/base.html" %}
{% set entrypoint = entrypoint|default("portico") %}

{# A base template for stuff like login, register, etc.

Not inside the app itself, but covered by the same structure,
hence the name.
#}

{% block content %}
<div class="portico-container" data-platform="{{ platform }}">
    <div class="portico-wrap">
        {% if not isolated_page %}
        {% include 'zerver/portico-header.html' %}
        {% endif %}
        <div class="app portico-page {% block portico_class_name %}{% endblock %}">
            <div class="app-main portico-page-container{% block hello_page_container %}{% endblock %}">
                {% block portico_content %}
                {% endblock %}
            </div>
        </div>
    </div>
    <div class="alert-box"></div>
    {% if not isolated_page %}
    {% include 'zerver/footer.html' %}
    {% endif %}
</div>
{% endblock %}

</pre>
#### user_custom_profile_fields.hbs ####
<pre>
{{#each profile_fields}}
    <li data-type="{{this.type}}" class="field-section custom_user_field" data-field-id="{{this.id}}">
        {{#unless ../for_user_info_popover}}
            <div class="name">{{this.name}}</div>
        {{/unless}}
        {{#if this.is_link}}
            <a tabindex="0" href="{{this.value}}" target="_blank" rel="noopener noreferrer" class="value custom_profile_fields_link {{#if ../for_user_info_popover}}tippy-zulip-tooltip{{/if}}" data-tippy-content="{{this.name}}">{{this.value}}</a>
        {{else if this.is_external_account}}
            <a tabindex="0" href="{{this.link}}" target="_blank" rel="noopener noreferrer" class="value custom_profile_fields_link {{#if ../for_user_info_popover}}tippy-zulip-tooltip{{/if}}" data-tippy-content="{{this.name}}">
                {{#if (eq this.subtype "github") }}
                <i class="fa fa-github" aria-hidden="true"></i>
                {{else if (eq this.subtype "twitter") }}
                <i class="fa fa-twitter" aria-hidden="true"></i>
                {{/if}}
                {{this.value}}
            </a>
        {{else if this.is_user_field}}
            <div class="pill-container not-editable" data-field-id="{{this.id}}">
                <div class="input" contenteditable="false" style="display: none;"></div>
            </div>
        {{else}}
            {{#if this.rendered_value}}
            <span class="value rendered_markdown {{#if ../for_user_info_popover}}tippy-zulip-tooltip{{/if}}" data-tippy-content="{{this.name}}">{{rendered_markdown this.rendered_value}}</span>
            {{else}}
            <span class="value {{#if ../for_user_info_popover}}tippy-zulip-tooltip"{{/if}} data-tippy-content="{{this.name}}">{{this.value}}</span>
            {{/if}}
        {{/if}}
    </li>
{{/each}}

</pre>
#### settings_tab.hbs ####
<pre>
<div id="settings-change-box" class="new-style">
    {{> settings/profile_settings }}

    {{> settings/account_settings }}

    {{> settings/user_display_settings }}

    {{> settings/user_notification_settings }}

    {{> settings/bot_settings }}

    {{> settings/alert_word_settings }}

    {{> settings/attachments_settings }}

    {{> settings/muted_topics_settings }}

    {{> settings/muted_users_settings }}
</div>

</pre>
### ARE YOU NOT CONVINCED THAT TEMPLATES ARE F***ING AWESOME? ###
