---
title: "Squid Proxy on Ubuntu"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by kkil82 on 2010-10-12
Hello,

I recently was working on a proxy server that had a custom build from linux called engageip.  They recently discontinued support and now I am trying to build a squid similiar to how engageip operated.  I have successfully setup the squid proxy and am running off it right now.  The only problem is I do not feel it is caching/working properly.  When I was running the other software I could go to speedtest.net and test the bandwidth and get 90 mbps results or higher so that told me the caching was working properly.  But now that I am running squid I am only getting what the actual network bandwidth is which is just around 3 mbps because we just have 2 T1 lines here.  I have researched and made changes to my conf file but still have not seen any difference.  Is this normal or is there something I am missing to fully utilize squid for caching purposes to improve my networks bandwidth issues?  I posted the file any recommendations are appreciated.

```

#    WELCOME TO SQUID 2.7.STABLE7
#    ----------------------------
#
#    This is the default Squid configuration file. You may wish
#    to look at the Squid home page (http://www.squid-cache.org/)
#    for the FAQ and other documentation.
#
#    The default Squid config file shows what the defaults for
#    various options happen to be.  If you don't need to change the
#    default, you shouldn't uncomment the line.  Doing so may cause
#    run-time problems.  In some cases "none" refers to no default
#    setting at all, while in other cases it refers to a valid
#    option - the comments for that keyword indicate if this is the
#    case.
#


#  Configuration options can be included using the "include" directive.
#  Include takes a list of files to include. Quoting and wildcards is
#  supported.
#
#  For example,
#
#  include /path/to/included/file/squid.acl.config
#
#  Includes can be nested up to a hard-coded depth of 16 levels.
#  This arbitrary restriction is to prevent recursive include references
#  from causing Squid entering an infinite loop whilst trying to load
#  configuration files.


# OPTIONS FOR AUTHENTICATION
# -----------------------------------------------------------------------------

#  TAG: auth_param
#    This is used to define parameters for the various authentication
#    schemes supported by Squid.
#
#    format: auth_param scheme parameter [setting]
#
#    The order in which authentication schemes are presented to the client is
#    dependent on the order the scheme first appears in config file. IE
#    has a bug (it's not RFC 2617 compliant) in that it will use the basic
#    scheme if basic is the first entry presented, even if more secure
#    schemes are presented. For now use the order in the recommended
#    settings section below. If other browsers have difficulties (don't
#    recognize the schemes offered even if you are using basic) either
#    put basic first, or disable the other schemes (by commenting out their
#    program entry).
#
#    Once an authentication scheme is fully configured, it can only be
#    shutdown by shutting squid down and restarting. Changes can be made on
#    the fly and activated with a reconfigure. I.E. You can change to a
#    different helper, but not unconfigure the helper completely.
#
#    Please note that while this directive defines how Squid processes
#    authentication it does not automatically activate authentication.
#    To use authentication you must in addition make use of ACLs based
#    on login name in http_access (proxy_auth, proxy_auth_regex or
#    external with %LOGIN used in the format tag). The browser will be
#    challenged for authentication on the first such acl encountered
#    in http_access processing and will also be re-challenged for new
#    login credentials if the request is being denied by a proxy_auth
#    type acl.
#
#    WARNING: authentication can't be used in a transparently intercepting
#    proxy as the client then thinks it is talking to an origin server and
#    not the proxy. This is a limitation of bending the TCP/IP protocol to
#    transparently intercepting port 80, not a limitation in Squid.
#
#    === Parameters for the basic scheme follow. ===
#
#    "program" cmdline
#    Specify the command for the external authenticator.  Such a program
#    reads a line containing "username password" and replies "OK" or
#    "ERR" in an endless loop. "ERR" responses may optionally be followed
#    by a error description available as %m in the returned error page.
#
#    By default, the basic authentication scheme is not used unless a
#    program is specified.
#
#    If you want to use the traditional proxy authentication, jump over to
#    the helpers/basic_auth/NCSA directory and type:
#        % make
#        % make install
#
#    Then, set this line to something like
#
#    auth_param basic program /usr/lib/squid/ncsa_auth /usr/etc/passwd
#
#    "children" numberofchildren
#    The number of authenticator processes to spawn. If you start too few
#    squid will have to wait for them to process a backlog of credential
#    verifications, slowing it down. When credential verifications are
#    done via a (slow) network you are likely to need lots of
#    authenticator processes.
#    auth_param basic children 5
#
#    "concurrency" numberofconcurrentrequests
#    The number of concurrent requests/channels the helper supports.
#    Changes the protocol used to include a channel number first on
#    the request/response line, allowing multiple requests to be sent
#    to the same helper in parallell without wating for the response.
#    Must not be set unless it's known the helper supports this.
#
#    "realm" realmstring
#    Specifies the realm name which is to be reported to the client for
#    the basic proxy authentication scheme (part of the text the user
#    will see when prompted their username and password).
#    auth_param basic realm Squid proxy-caching web server
#
#    "credentialsttl" timetolive
#    Specifies how long squid assumes an externally validated
#    username:password pair is valid for - in other words how often the
#    helper program is called for that user. Set this low to force
#    revalidation with short lived passwords.  Note that setting this high
#    does not impact your susceptibility to replay attacks unless you are
#    using an one-time password system (such as SecureID). If you are using
#    such a system, you will be vulnerable to replay attacks unless you
#    also use the max_user_ip ACL in an http_access rule.
#    auth_param basic credentialsttl 2 hours
#
#    "casesensitive" on|off
#    Specifies if usernames are case sensitive. Most user databases are
#    case insensitive allowing the same username to be spelled using both
#    lower and upper case letters, but some are case sensitive. This
#    makes a big difference for user_max_ip ACL processing and similar.
#    auth_param basic casesensitive off
#
#    "blankpassword" on|off
#    Specifies if blank passwords should be supported. Defaults to off
#    as there is multiple authentication backends which handles blank
#    passwords as "guest" access.
#
#    === Parameters for the digest scheme follow ===
#
#    "program" cmdline
#    Specify the command for the external authenticator.  Such a program
#    reads a line containing "username":"realm" and replies with the
#    appropriate H(A1) value hex encoded or ERR if the user (or his H(A1)
#    hash) does not exists.  See RFC 2616 for the definition of H(A1).
#    "ERR" responses may optionally be followed by a error description
#    available as %m in the returned error page.
#
#    By default, the digest authentication scheme is not used unless a
#    program is specified.
#
#    If you want to use a digest authenticator, jump over to the
#    helpers/digest_auth/ directory and choose the authenticator to use.
#    It it's directory type
#        % make
#        % make install
#
#    Then, set this line to something like
#
#    auth_param digest program /usr/lib/squid/digest_auth_pw /usr/etc/digpass
#
#    "children" numberofchildren
#    The number of authenticator processes to spawn. If you start too few
#    squid will have to wait for them to process a backlog of credential
#    verifications, slowing it down. When credential verifications are
#    done via a (slow) network you are likely to need lots of
#    authenticator processes.
#    auth_param digest children 5
#
#    "concurrency" numberofconcurrentrequests
#    The number of concurrent requests/channels the helper supports.
#    Changes the protocol used to include a channel number first on
#    the request/response line, allowing multiple requests to be sent
#    to the same helper in parallell without wating for the response.
#    Must not be set unless it's known the helper supports this.
#
#    "realm" realmstring
#    Specifies the realm name which is to be reported to the client for the
#    digest proxy authentication scheme (part of the text the user will see
#    when prompted their username and password).
#    auth_param digest realm Squid proxy-caching web server
#
#    "nonce_garbage_interval" timeinterval
#    Specifies the interval that nonces that have been issued to clients are
#    checked for validity.
#    auth_param digest nonce_garbage_interval 5 minutes
#
#    "nonce_max_duration" timeinterval
#    Specifies the maximum length of time a given nonce will be valid for.
#    auth_param digest nonce_max_duration 30 minutes
#
#    "nonce_max_count" number
#    Specifies the maximum number of times a given nonce can be used.
#    auth_param digest nonce_max_count 50
#
#    "nonce_strictness" on|off
#    Determines if squid requires strict increment-by-1 behavior for nonce
#    counts, or just incrementing (off - for use when useragents generate
#    nonce counts that occasionally miss 1 (ie, 1,2,4,6)).
#    auth_param digest nonce_strictness off
#
#    "check_nonce_count" on|off
#    This directive if set to off can disable the nonce count check
#    completely to work around buggy digest qop implementations in certain
#    mainstream browser versions. Default on to check the nonce count to
#    protect from authentication replay attacks.
#    auth_param digest check_nonce_count on
#
#    "post_workaround" on|off
#    This is a workaround to certain buggy browsers who sends an incorrect
#    request digest in POST requests when reusing the same nonce as acquired
#    earlier in response to a GET request.
#    auth_param digest post_workaround off
#
#    === NTLM scheme options follow ===
#
#    "program" cmdline
#    Specify the command for the external NTLM authenticator. Such a
#    program participates in the NTLMSSP exchanges between Squid and the
#    client and reads commands according to the Squid NTLMSSP helper
#    protocol. See helpers/ntlm_auth/ for details. Recommended ntlm
#    authenticator is ntlm_auth from Samba-3.X, but a number of other
#    ntlm authenticators is available.
#
#    By default, the ntlm authentication scheme is not used unless a
#    program is specified.
#
#    auth_param ntlm program /usr/bin/ntlm_auth --helper-protocol=squid-2.5-ntlmssp
#
#    "children" numberofchildren
#    The number of authenticator processes to spawn. If you start too few
#    squid will have to wait for them to process a backlog of credential
#    verifications, slowing it down. When credential verifications are
#    done via a (slow) network you are likely to need lots of
#    authenticator processes.
#    auth_param ntlm children 5
#
#    "keep_alive" on|off
#    This option enables the use of keep-alive on the initial
#    authentication request. It has been reported some versions of MSIE
#    have problems if this is enabled, but performance will be increased
#    if enabled.
#
#    auth_param ntlm keep_alive on
#
#    === Negotiate scheme options follow ===
#
#    "program" cmdline
#    Specify the command for the external Negotiate authenticator. Such a
#    program participates in the SPNEGO exchanges between Squid and the
#    client and reads commands according to the Squid ntlmssp helper
#    protocol. See helpers/ntlm_auth/ for details. Recommended SPNEGO
#    authenticator is ntlm_auth from Samba-4.X.
#
#    By default, the Negotiate authentication scheme is not used unless a
#    program is specified.
#
#    auth_param negotiate program /path/to/samba/bin/ntlm_auth --helper-protocol=gss-spnego
#
#    "children" numberofchildren
#    The number of authenticator processes to spawn. If you start too few
#    squid will have to wait for them to process a backlog of credential
#    verifications, slowing it down. When credential verifications are
#    done via a (slow) network you are likely to need lots of
#    authenticator processes.
#    auth_param negotiate children 5
#
#    "keep_alive" on|off
#    If you experience problems with PUT/POST requests when using the
#    Negotiate authentication scheme then you can try setting this to
#    off. This will cause Squid to forcibly close the connection on
#    the initial requests where the browser asks which schemes are
#    supported by the proxy.
#
#    auth_param negotiate keep_alive on
#
#Recommended minimum configuration per scheme:
#auth_param negotiate program <uncomment and complete this line to activate>
#auth_param negotiate children 5
#auth_param negotiate keep_alive on
#auth_param ntlm program <uncomment and complete this line to activate>
#auth_param ntlm children 5
#auth_param ntlm keep_alive on
#auth_param digest program <uncomment and complete this line>
#auth_param digest children 5
#auth_param digest realm Squid proxy-caching web server
#auth_param digest nonce_garbage_interval 5 minutes
#auth_param digest nonce_max_duration 30 minutes
#auth_param digest nonce_max_count 50
#auth_param basic program <uncomment and complete this line>
#auth_param basic children 5
#auth_param basic realm Squid proxy-caching web server
#auth_param basic credentialsttl 2 hours
#auth_param basic casesensitive off

#  TAG: authenticate_cache_garbage_interval
#    The time period between garbage collection across the username cache.
#    This is a tradeoff between memory utilization (long intervals - say
#    2 days) and CPU (short intervals - say 1 minute). Only change if you
#    have good reason to.
#
#Default:
# authenticate_cache_garbage_interval 1 hour

#  TAG: authenticate_ttl
#    The time a user & their credentials stay in the logged in user cache
#    since their last request. When the garbage interval passes, all user
#    credentials that have passed their TTL are removed from memory.
#
#Default:
# authenticate_ttl 1 hour

#  TAG: authenticate_ip_ttl
#    If you use proxy authentication and the 'max_user_ip' ACL, this
#    directive controls how long Squid remembers the IP addresses
#    associated with each user.  Use a small value (e.g., 60 seconds) if
#    your users might change addresses quickly, as is the case with
#    dialups. You might be safe using a larger value (e.g., 2 hours) in a
#    corporate LAN environment with relatively static address assignments.
#
#Default:
# authenticate_ip_ttl 0 seconds

#  TAG: authenticate_ip_shortcircuit_ttl
#    Cache authentication credentials per client IP address for this
#    long. Default is 0 seconds (disabled).
#
#    See also authenticate_ip_shortcircuit_access directive.
#
#Default:
# authenticate_ip_shortcircuit_ttl 0 seconds


# ACCESS CONTROLS
# -----------------------------------------------------------------------------

#  TAG: external_acl_type
#    This option defines external acl classes using a helper program to
#    look up the status
#
#      external_acl_type name [options] FORMAT.. /path/to/helper [helper arguments..]
#
#    Options:
#
#      ttl=n        TTL in seconds for cached results (defaults to 3600
#            for 1 hour)
#      negative_ttl=n
#            TTL for cached negative lookups (default same
#            as ttl)
#      children=n    number of processes spawn to service external acl
#            lookups of this type. (default 5).
#      concurrency=n    concurrency level per process. Only used with helpers
#              capable of processing more than one query at a time.
#            Note: see compatibility note below
#      cache=n    result cache size, 0 is unbounded (default)
#      grace=    Percentage remaining of TTL where a refresh of a
#            cached entry should be initiated without needing to
#            wait for a new reply. (default 0 for no grace period)
#      protocol=2.5  Compatibility mode for Squid-2.5 external acl helpers
#
#    FORMAT specifications
#
#      %LOGIN    Authenticated user login name
#      %EXT_USER    Username from external acl
#      %IDENT    Ident user name
#      %SRC        Client IP
#      %SRCPORT    Client source port
#      %URI        Requested URI
#      %DST        Requested host
#      %PROTO    Requested protocol
#      %PORT        Requested port
#      %METHOD    Request method
#      %MYADDR    Squid interface address
#      %MYPORT    Squid http_port number
#      %PATH        Requested URL-path (including query-string if any)
#      %USER_CERT    SSL User certificate in PEM format
#      %USER_CERTCHAIN SSL User certificate chain in PEM format
#      %USER_CERT_xx    SSL User certificate subject attribute xx
#      %USER_CA_xx    SSL User certificate issuer attribute xx
#      %{Header}    HTTP request header "Header"
#      %{Hdr:member}    HTTP request header "Hdr" list member "member"
#      %{Hdr:;member}
#            HTTP request header list member using ; as
#            list separator. ; can be any non-alphanumeric
#            character.
#     %ACL        The ACL name
#     %DATA        The ACL arguments. If not used then any arguments
#            is automatically added at the end
#
#    In addition to the above, any string specified in the referencing
#    acl will also be included in the helper request line, after the
#    specified formats (see the "acl external" directive)
#
#    The helper receives lines per the above format specification,
#    and returns lines starting with OK or ERR indicating the validity
#    of the request and optionally followed by additional keywords with
#    more details.
#
#    General result syntax:
#
#      OK/ERR keyword=value ...
#
#    Defined keywords:
#
#      user=        The users name (login also understood)
#      password=    The users password (for PROXYPASS login= cache_peer)
#      message=    Error message or similar used as %o in error messages
#            (error also understood)
#      log=        String to be logged in access.log. Available as
#            %ea in logformat specifications
#
#    If protocol=3.0 (the default) then URL escaping is used to protect
#    each value in both requests and responses.
#
#    If using protocol=2.5 then all values need to be enclosed in quotes
#    if they may contain whitespace, or the whitespace escaped using \.
#    And quotes or \ characters within the keyword value must be \ escaped.
#
#    When using the concurrency= option the protocol is changed by
#    introducing a query channel tag infront of the request/response.
#    The query channel tag is a number between 0 and concurrency-1.
#
#    Compatibility Note: The children= option was named concurrency= in
#    Squid-2.5.STABLE3 and earlier, and was accepted as an alias for the
#    duration of the Squid-2.5 releases to keep compatibility. However,
#    the meaning of concurrency= option has changed in Squid-2.6 to match
#    that of Squid-3 and the old syntax no longer works.
#
#Default:
# none

#  TAG: acl
#    Defining an Access List
#
#    Every access list definition must begin with an aclname and acltype, 
#    followed by either type-specific arguments or a quoted filename that
#    they are read from.
#
#    acl aclname acltype argument ...
#    acl aclname acltype "file" ...
#
#    when using "file", the file should contain one item per line.
#
#    By default, regular expressions are CASE-SENSITIVE.  To make
#    them case-insensitive, use the -i option.
#
#    acl aclname src      ip-address/netmask ... (clients IP address)
#    acl aclname src      addr1-addr2/netmask ... (range of addresses)
#    acl aclname dst      ip-address/netmask ... (URL host's IP address)
#    acl aclname myip     ip-address/netmask ... (local socket IP address)
#
#    acl aclname arp      mac-address ... (xx:xx:xx:xx:xx:xx notation)
#      # The arp ACL requires the special configure option --enable-arp-acl.
#      # Furthermore, the arp ACL code is not portable to all operating systems.
#      # It works on Linux, Solaris, FreeBSD and some other *BSD variants.
#      #
#      # NOTE: Squid can only determine the MAC address for clients that are on
#      # the same subnet. If the client is on a different subnet, then Squid cannot
#      # find out its MAC address.
#
#    acl aclname srcdomain   .foo.com ...    # reverse lookup, client IP
#    acl aclname dstdomain   .foo.com ...    # Destination server from URL
#    acl aclname srcdom_regex [-i] xxx ...   # regex matching client name
#    acl aclname dstdom_regex [-i] xxx ...   # regex matching server
#      # For dstdomain and dstdom_regex a reverse lookup is tried if a IP
#      # based URL is used and no match is found. The name "none" is used
#      # if the reverse lookup fails.
#
#    acl aclname time     [day-abbrevs]  [h1:m1-h2:m2]
#        # day-abbrevs:
#        # S - Sunday
#        # M - Monday
#        # T - Tuesday
#        # W - Wednesday
#        # H - Thursday
#        # F - Friday
#        # A - Saturday
#        # h1:m1 must be less than h2:m2
#    acl aclname url_regex [-i] ^http:// ...        # regex matching on whole URL
#    acl aclname urlpath_regex [-i] \.gif$ ...    # regex matching on URL path
#    acl aclname urllogin [-i] [^a-zA-Z0-9] ...    # regex matching on URL login field
#    acl aclname port     80 70 21 ...
#    acl aclname port     0-1024 ...        # ranges allowed
#    acl aclname myport   3128 ...        # (local socket TCP port)
#    acl aclname myportname 3128 ...        # http(s)_port name
#    acl aclname proto    HTTP FTP ...
#    acl aclname method   GET POST ...
#    acl aclname browser  [-i] regexp ...
#      # pattern match on User-Agent header (see also req_header below)
#    acl aclname referer_regex  [-i] regexp ...
#      # pattern match on Referer header
#      # Referer is highly unreliable, so use with care
#    acl aclname ident    username ...
#    acl aclname ident_regex [-i] pattern ...
#      # string match on ident output.
#      # use REQUIRED to accept any non-null ident.
#    acl aclname src_as   number ...
#    acl aclname dst_as   number ...
#      # Except for access control, AS numbers can be used for
#      # routing of requests to specific caches. Here's an
#      # example for routing all requests for AS#1241 and only
#      # those to mycache.mydomain.net:
#      # acl asexample dst_as 1241
#      # cache_peer_access mycache.mydomain.net allow asexample
#      # cache_peer_access mycache_mydomain.net deny all
#
#    acl aclname proxy_auth [-i] username ...
#    acl aclname proxy_auth_regex [-i] pattern ...
#      # list of valid usernames
#      # use REQUIRED to accept any valid username.
#      #
#      # NOTE: when a Proxy-Authentication header is sent but it is not
#      # needed during ACL checking the username is NOT logged
#      # in access.log.
#      #
#      # NOTE: proxy_auth requires a EXTERNAL authentication program
#      # to check username/password combinations (see
#      # auth_param directive).
#      #
#      # NOTE: proxy_auth can't be used in a transparent proxy as
#      # the browser needs to be configured for using a proxy in order
#      # to respond to proxy authentication.
#
#    acl aclname snmp_community string ...
#      # A community string to limit access to your SNMP Agent
#      # Example:
#      #
#      #    acl snmppublic snmp_community public
#
#    acl aclname maxconn number
#      # This will be matched when the client's IP address has
#      # more than <number> HTTP connections established.
#
#    acl aclname max_user_ip [-s] number
#      # This will be matched when the user attempts to log in from more
#      # than <number> different ip addresses. The authenticate_ip_ttl
#      # parameter controls the timeout on the ip entries.
#      # If -s is specified the limit is strict, denying browsing
#      # from any further IP addresses until the ttl has expired. Without
#      # -s Squid will just annoy the user by "randomly" denying requests.
#      # (the counter is reset each time the limit is reached and a
#      # request is denied)
#      # NOTE: in acceleration mode or where there is mesh of child proxies,
#      # clients may appear to come from multiple addresses if they are
#      # going through proxy farms, so a limit of 1 may cause user problems.
#
#    acl aclname req_mime_type mime-type ...
#      # regex match against the mime type of the request generated
#      # by the client. Can be used to detect file upload or some
#      # types HTTP tunneling requests.
#      # NOTE: This does NOT match the reply. You cannot use this
#      # to match the returned file type.
#
#    acl aclname req_header header-name [-i] any\.regex\.here
#      # regex match against any of the known request headers.  May be
#      # thought of as a superset of "browser", "referer" and "mime-type"
#      # ACLs.
#
#    acl aclname rep_mime_type mime-type ...
#      # regex match against the mime type of the reply received by
#      # squid. Can be used to detect file download or some
#      # types HTTP tunneling requests.
#      # NOTE: This has no effect in http_access rules. It only has
#      # effect in rules that affect the reply data stream such as
#      # http_reply_access.
#
#    acl aclname rep_header header-name [-i] any\.regex\.here
#      # regex match against any of the known reply headers. May be
#      # thought of as a superset of "browser", "referer" and "mime-type"
#      # ACLs.
#      #
#      # Example:
#      #
#      # acl many_spaces rep_header Content-Disposition -i [[:space:]]{3,}
#
#    acl aclname external class_name [arguments...]
#      # external ACL lookup via a helper class defined by the
#      # external_acl_type directive.
#
#    acl aclname urlgroup group1 ...
#      # match against the urlgroup as indicated by redirectors
#
#    acl aclname user_cert attribute values...
#      # match against attributes in a user SSL certificate
#      # attribute is one of DN/C/O/CN/L/ST
#
#    acl aclname ca_cert attribute values...
#      # match against attributes a users issuing CA SSL certificate
#      # attribute is one of DN/C/O/CN/L/ST
#
#    acl aclname ext_user username ...
#    acl aclname ext_user_regex [-i] pattern ...
#      # string match on username returned by external acl helper
#      # use REQUIRED to accept any non-null user name.
#
#Examples:
#acl macaddress arp 09:00:2b:23:45:67
#acl myexample dst_as 1241
#acl password proxy_auth REQUIRED
#acl fileupload req_mime_type -i ^multipart/form-data$
#acl javascript rep_mime_type -i ^application/x-javascript$
#
#Recommended minimum configuration:
acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32
#
# Example rule allowing access from your local networks.
# Adapt to list your (internal) IP networks from where browsing
# should be allowed
acl localnet src 10.0.0.0/8    # RFC1918 possible internal network
acl localnet src 172.16.0.0/12    # RFC1918 possible internal network
acl localnet src 192.168.0.0/16    # RFC1918 possible internal network
#
acl SSL_ports port 443        # https
acl SSL_ports port 563        # snews
acl SSL_ports port 873        # rsync
acl Safe_ports port 80        # http
acl Safe_ports port 21        # ftp
acl Safe_ports port 443        # https
acl Safe_ports port 70        # gopher
acl Safe_ports port 210        # wais
acl Safe_ports port 1025-65535    # unregistered ports
acl Safe_ports port 280        # http-mgmt
acl Safe_ports port 488        # gss-http
acl Safe_ports port 591        # filemaker
acl Safe_ports port 777        # multiling http
acl Safe_ports port 631        # cups
acl Safe_ports port 873        # rsync
acl Safe_ports port 901        # SWAT
acl purge method PURGE
acl CONNECT method CONNECT

#  TAG: http_access
#    Allowing or Denying access based on defined access lists
#
#    Access to the HTTP port:
#    http_access allow|deny [!]aclname ...
#
#    NOTE on default values:
#
#    If there are no "access" lines present, the default is to deny
#    the request.
#
#    If none of the "access" lines cause a match, the default is the
#    opposite of the last line in the list.  If the last line was
#    deny, the default is allow.  Conversely, if the last line
#    is allow, the default will be deny.  For these reasons, it is a
#    good idea to have an "deny all" or "allow all" entry at the end
#    of your access lists to avoid potential confusion.
#
#Default:
# http_access deny all
#
#Recommended minimum configuration:
#
# Only allow cachemgr access from localhost
http_access allow manager localhost
http_access deny manager
# Only allow purge requests from localhost
http_access allow purge localhost
http_access deny purge
# Deny requests to unknown ports
http_access deny !Safe_ports
# Deny CONNECT to other than SSL ports
http_access deny CONNECT !SSL_ports
#
# We strongly recommend the following be uncommented to protect innocent
# web applications running on the proxy server who think the only
# one who can access services on "localhost" is a local user
#http_access deny to_localhost
#
# INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS

# Example rule allowing access from your local networks.
# Adapt localnet in the ACL section to list your (internal) IP networks
# from where browsing should be allowed
#http_access allow localnet
http_access allow localhost
http_access allow localnet
# And finally deny all other access to this proxy
http_access deny all

#  TAG: http_access2
#    Allowing or Denying access based on defined access lists
#
#    Identical to http_access, but runs after redirectors. If not set
#    then only http_access is used.
#
#Default:
# none

#  TAG: http_reply_access
#    Allow replies to client requests. This is complementary to http_access.
#
#    http_reply_access allow|deny [!] aclname ...
#
#    NOTE: if there are no access lines present, the default is to allow
#    all replies
#
#    If none of the access lines cause a match the opposite of the
#    last line will apply. Thus it is good practice to end the rules
#    with an "allow all" or "deny all" entry.
#
#Default:
# http_reply_access allow all

#  TAG: icp_access
#    Allowing or Denying access to the ICP port based on defined
#    access lists
#
#    icp_access  allow|deny [!]aclname ...
#
#    See http_access for details
#
#Default:
# icp_access deny all
#
#Allow ICP queries from local networks only
icp_access allow localnet
icp_access deny all

#  TAG: htcp_access
#    Allowing or Denying access to the HTCP port based on defined
#    access lists
#
#    htcp_access  allow|deny [!]aclname ...
#
#    See http_access for details
#
#    NOTE: The default if no htcp_access lines are present is to
#    deny all traffic. This default may cause problems with peers
#    using the htcp or htcp-oldsquid options.
#
#Default:
# htcp_access deny all
#
#Allow HTCP queries from local networks only
# htcp_access allow localnet
# htcp_access deny all

#  TAG: htcp_clr_access
#    Allowing or Denying access to purge content using HTCP based
#    on defined access lists
#
#    htcp_clr_access  allow|deny [!]aclname ...
#
#    See http_access for details
#
##Allow HTCP CLR requests from trusted peers
#acl htcp_clr_peer src 172.16.1.2
#htcp_clr_access allow htcp_clr_peer
#
#Default:
# htcp_clr_access deny all

#  TAG: miss_access
#    Use to force your neighbors to use you as a sibling instead of
#    a parent.  For example:
#
#        acl localclients src 172.16.0.0/16
#        miss_access allow localclients
#        miss_access deny  !localclients
#
#    This means only your local clients are allowed to fetch
#    MISSES and all other clients can only fetch HITS.
#
#    By default, allow all clients who passed the http_access rules
#    to fetch MISSES from us.
#
#Default setting:
# miss_access allow all

#  TAG: ident_lookup_access
#    A list of ACL elements which, if matched, cause an ident
#    (RFC931) lookup to be performed for this request.  For
#    example, you might choose to always perform ident lookups
#    for your main multi-user Unix boxes, but not for your Macs
#    and PCs.  By default, ident lookups are not performed for
#    any requests.
#
#    To enable ident lookups for specific client addresses, you
#    can follow this example:
#
#    acl ident_aware_hosts src 198.168.1.0/255.255.255.0
#    ident_lookup_access allow ident_aware_hosts
#    ident_lookup_access deny all
#
#    Only src type ACL checks are fully supported.  A src_domain
#    ACL might work at times, but it will not always provide
#    the correct result.
#
#Default:
# ident_lookup_access deny all

#  TAG: reply_body_max_size    bytes allow|deny acl acl...
#    This option specifies the maximum size of a reply body in bytes.
#    It can be used to prevent users from downloading very large files,
#    such as MP3's and movies. When the reply headers are received,
#    the reply_body_max_size lines are processed, and the first line with
#    a result of "allow" is used as the maximum body size for this reply.
#    This size is checked twice. First when we get the reply headers,
#    we check the content-length value.  If the content length value exists
#    and is larger than the allowed size, the request is denied and the
#    user receives an error message that says "the request or reply
#    is too large." If there is no content-length, and the reply
#    size exceeds this limit, the client's connection is just closed
#    and they will receive a partial reply.
#
#    WARNING: downstream caches probably can not detect a partial reply
#    if there is no content-length header, so they will cache
#    partial responses and give them out as hits.  You should NOT
#    use this option if you have downstream caches.
#
#    If you set this parameter to zero (the default), there will be
#    no limit imposed.
#
#Default:
# reply_body_max_size 0 allow all

#  TAG: authenticate_ip_shortcircuit_access
#    Access list determining when shortcicuiting the authentication process
#    based on source IP cached credentials is acceptable. Use this to deny
#    using the ip auth cache on requests from child proxies or other source
#    ip's having multiple users.
#
#    See also authenticate_ip_shortcircuit_ttl directive
#
#Default:
# none


# OPTIONS FOR X-Forwarded-For
# -----------------------------------------------------------------------------

#  TAG: follow_x_forwarded_for
#    Allowing or Denying the X-Forwarded-For header to be followed to
#    find the original source of a request.
#
#    Requests may pass through a chain of several other proxies
#    before reaching us.  The X-Forwarded-For header will contain a
#    comma-separated list of the IP addresses in the chain, with the
#    rightmost address being the most recent.
#
#    If a request reaches us from a source that is allowed by this
#    configuration item, then we consult the X-Forwarded-For header
#    to see where that host received the request from.  If the
#    X-Forwarded-For header contains multiple addresses, and if
#    acl_uses_indirect_client is on, then we continue backtracking
#    until we reach an address for which we are not allowed to
#    follow the X-Forwarded-For header, or until we reach the first
#    address in the list.  (If acl_uses_indirect_client is off, then
#    it's impossible to backtrack through more than one level of
#    X-Forwarded-For addresses.)
#
#    The end result of this process is an IP address that we will
#    refer to as the indirect client address.  This address may
#    be treated as the client address for access control, delay
#    pools and logging, depending on the acl_uses_indirect_client,
#    delay_pool_uses_indirect_client and log_uses_indirect_client
#    options.
#
#    SECURITY CONSIDERATIONS:
#
#        Any host for which we follow the X-Forwarded-For header
#        can place incorrect information in the header, and Squid
#        will use the incorrect information as if it were the
#        source address of the request.  This may enable remote
#        hosts to bypass any access control restrictions that are
#        based on the client's source addresses.
#
#    For example:
#
#        acl localhost src 127.0.0.1
#        acl my_other_proxy srcdomain .proxy.example.com
#        follow_x_forwarded_for allow localhost
#        follow_x_forwarded_for allow my_other_proxy
#
#Default:
# follow_x_forwarded_for deny all

#  TAG: acl_uses_indirect_client    on|off
#    Controls whether the indirect client address
#    (see follow_x_forwarded_for) is used instead of the
#    direct client address in acl matching.
#
#Default:
# acl_uses_indirect_client on

#  TAG: delay_pool_uses_indirect_client    on|off
#    Controls whether the indirect client address
#    (see follow_x_forwarded_for) is used instead of the
#    direct client address in delay pools.
#
#Default:
# delay_pool_uses_indirect_client on

#  TAG: log_uses_indirect_client    on|off
#    Controls whether the indirect client address
#    (see follow_x_forwarded_for) is used instead of the
#    direct client address in the access log.
#
#Default:
# log_uses_indirect_client on


# SSL OPTIONS
# -----------------------------------------------------------------------------

#  TAG: ssl_unclean_shutdown
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    Some browsers (especially MSIE) bugs out on SSL shutdown
#    messages.
#
#Default:
# ssl_unclean_shutdown off

#  TAG: ssl_engine
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    The OpenSSL engine to use. You will need to set this if you
#    would like to use hardware SSL acceleration for example.
#
#Default:
# none

#  TAG: sslproxy_client_certificate
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    Client SSL Certificate to use when proxying https:// URLs
#
#Default:
# none

#  TAG: sslproxy_client_key
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    Client SSL Key to use when proxying https:// URLs
#
#Default:
# none

#  TAG: sslproxy_version
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    SSL version level to use when proxying https:// URLs
#
#Default:
# sslproxy_version 1

#  TAG: sslproxy_options
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    SSL engine options to use when proxying https:// URLs
#
#Default:
# none

#  TAG: sslproxy_cipher
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    SSL cipher list to use when proxying https:// URLs
#
#Default:
# none

#  TAG: sslproxy_cafile
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    file containing CA certificates to use when verifying server
#    certificates while proxying https:// URLs
#
#Default:
# none

#  TAG: sslproxy_capath
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    directory containing CA certificates to use when verifying
#    server certificates while proxying https:// URLs
#
#Default:
# none

#  TAG: sslproxy_flags
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    Various flags modifying the use of SSL while proxying https:// URLs:
#        DONT_VERIFY_PEER    Accept certificates even if they fail to
#                verify.
#        NO_DEFAULT_CA       Don't use the default CA list built in
#                to OpenSSL.
#
#Default:
# none

#  TAG: sslpassword_program
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    Specify a program used for entering SSL key passphrases
#    when using encrypted SSL certificate keys. If not specified
#    keys must either be unencrypted, or Squid started with the -N
#    option to allow it to query interactively for the passphrase.
#
#Default:
# none


# NETWORK OPTIONS
# -----------------------------------------------------------------------------

#  TAG: http_port
#    Usage:    port [options]
#        hostname:port [options]
#        1.2.3.4:port [options]
#
#    The socket addresses where Squid will listen for HTTP client
#    requests.  You may specify multiple socket addresses.
#    There are three forms: port alone, hostname with port, and
#    IP address with port.  If you specify a hostname or IP
#    address, Squid binds the socket to that specific
#    address.  This replaces the old 'tcp_incoming_address'
#    option.  Most likely, you do not need to bind to a specific
#    address, so you can use the port number alone.
#
#    If you are running Squid in accelerator mode, you
#    probably want to listen on port 80 also, or instead.
#
#    The -I command line option will override the *first* port
#    specified here.
#
#    You may specify multiple socket addresses on multiple lines.
#
#    Options:
#
#       transparent    Support for transparent interception of
#            outgoing requests without browser settings.
#
#       tproxy    Support Linux TPROXY for spoofing outgoing
#            connections using the client IP address.
#
#       accel    Accelerator mode. See also the related vhost,
#            vport and defaultsite directives.
#
#       defaultsite=domainname
#            What to use for the Host: header if it is not present
#            in a request. Determines what site (not origin server)
#            accelerators should consider the default.
#            Defaults to visible_hostname:port if not set
#            May be combined with vport=NN to override the port number.
#            Implies accel.
#
#       vhost    Accelerator mode using Host header for virtual
#            domain support. Implies accel.
#
#       vport    Accelerator with IP based virtual host support.
#            Implies accel.
#
#       vport=NN    As above, but uses specified port number rather
#            than the http_port number. Implies accel.
#
#       allow-direct    Allow direct forwarding in accelerator mode. Normally
#               accelerated requests is denied direct forwarding as it
#            never_direct was used.
#
#       urlgroup=    Default urlgroup to mark requests with (see
#            also acl urlgroup and url_rewrite_program)
#
#       protocol=    Protocol to reconstruct accelerated requests with.
#            Defaults to http.
#
#       no-connection-auth
#            Prevent forwarding of Microsoft connection oriented
#            authentication (NTLM, Negotiate and Kerberos)
#
#       act-as-origin
#               Act is if this Squid is the origin server.
#            This currently means generate own Date: and
#            Expires: headers. Implies accel.
#
#       http11    Enables HTTP/1.1 support to clients. The HTTP/1.1
#            support is still incomplete with an internal HTTP/1.0
#            hop, but should work with most clients. The main
#            HTTP/1.1 features missing due to this is forwarding
#            of requests using chunked transfer encoding (results
#            in 411) and forwarding of 1xx responses (silently
#            dropped)
#
#       name=    Specifies a internal name for the port. Defaults to
#            the port specification (port or addr:port)
#
#       tcpkeepalive[=idle,interval,timeout]
#            Enable TCP keepalive probes of idle connections
#            idle is the initial time before TCP starts probing
#            the connection, interval how often to probe, and
#            timeout the time before giving up.
#
#    If you run Squid on a dual-homed machine with an internal
#    and an external interface we recommend you to specify the
#    internal address:port in http_port. This way Squid will only be
#    visible on the internal address.
#
# Squid normally listens to port 3128
http_port 3128

#  TAG: https_port
# Note: This option is only available if Squid is rebuilt with the
#       --enable-ssl option
#
#    Usage:  [ip:]port cert=certificate.pem [key=key.pem] [options...]
#
#    The socket address where Squid will listen for HTTPS client
#    requests.
#
#    This is really only useful for situations where you are running
#    squid in accelerator mode and you want to do the SSL work at the
#    accelerator level.
#
#    You may specify multiple socket addresses on multiple lines,
#    each with their own SSL certificate and/or options.
#
#    Options:
#
#    In addition to the options specified for http_port the folling
#    SSL related options is supported:
#
#       cert=    Path to SSL certificate (PEM format).
#
#       key=        Path to SSL private key file (PEM format)
#            if not specified, the certificate file is
#            assumed to be a combined certificate and
#            key file.
#
#       version=    The version of SSL/TLS supported
#                1    automatic (default)
#                2    SSLv2 only
#                3    SSLv3 only
#                4    TLSv1 only
#
#       cipher=    Colon separated list of supported ciphers.
#
#       options=    Various SSL engine options. The most important
#            being:
#                NO_SSLv2  Disallow the use of SSLv2
#                NO_SSLv3  Disallow the use of SSLv3
#                NO_TLSv1  Disallow the use of TLSv1
#                SINGLE_DH_USE Always create a new key when using
#                      temporary/ephemeral DH key exchanges
#            See src/ssl_support.c or OpenSSL SSL_CTX_set_options
#            documentation for a complete list of options.
#
#       clientca=    File containing the list of CAs to use when
#            requesting a client certificate.
#
#       cafile=    File containing additional CA certificates to
#            use when verifying client certificates. If unset
#            clientca will be used.
#
#       capath=    Directory containing additional CA certificates
#            and CRL lists to use when verifying client certificates.
#
#       crlfile=    File of additional CRL lists to use when verifying
#            the client certificate, in addition to CRLs stored in
#            the capath. Implies VERIFY_CRL flag below.
#
#       dhparams=    File containing DH parameters for temporary/ephemeral
#            DH key exchanges.
#
#       sslflags=    Various flags modifying the use of SSL:
#                DELAYED_AUTH
#                Don't request client certificates
#                immediately, but wait until acl processing
#                requires a certificate (not yet implemented).
#                NO_DEFAULT_CA
#                Don't use the default CA lists built in
#                to OpenSSL.
#                NO_SESSION_REUSE
#                Don't allow for session reuse. Each connection
#                will result in a new SSL session.
#                VERIFY_CRL
#                Verify CRL lists when accepting client
#                certificates.
#                VERIFY_CRL_ALL
#                Verify CRL lists for all certificates in the
#                client certificate chain.
#
#       sslcontext=    SSL session ID context identifier.
#
#
#Default:
# none

#  TAG: tcp_outgoing_tos
#    Allows you to select a TOS/Diffserv value to mark outgoing
#    connections with, based on the username or source address
#    making the request.
#
#    tcp_outgoing_tos ds-field [!]aclname ...
#
#    Example where normal_service_net uses the TOS value 0x00
#    and good_service_net uses 0x20
#
#    acl normal_service_net src 10.0.0.0/255.255.255.0
#    acl good_service_net src 10.0.1.0/255.255.255.0
#    tcp_outgoing_tos 0x00 normal_service_net
#    tcp_outgoing_tos 0x20 good_service_net
#
#    TOS/DSCP values really only have local significance - so you should
#    know what you're specifying. For more information, see RFC2474 and
#    RFC3260.
#
#    The TOS/DSCP byte must be exactly that - a octet value  0 - 255, or
#    "default" to use whatever default your host has. Note that in
#    practice often only values 0 - 63 is usable as the two highest bits
#    have been redefined for use by ECN (RFC3168).
#
#    Processing proceeds in the order specified, and stops at first fully
#    matching line.
#
#    Note: The use of this directive using client dependent ACLs is
#    incompatible with the use of server side persistent connections. To
#    ensure correct results it is best to set server_persisten_connections
#    to off when using this directive in such configurations.
#
#Default:
# none

#  TAG: tcp_outgoing_address
#    Allows you to map requests to different outgoing IP addresses
#    based on the username or source address of the user making
#    the request.
#
#    tcp_outgoing_address ipaddr [[!]aclname] ...
#
#    Example where requests from 10.0.0.0/24 will be forwarded
#    with source address 10.1.0.1, 10.0.2.0/24 forwarded with
#    source address 10.1.0.2 and the rest will be forwarded with
#    source address 10.1.0.3.
#
#    acl normal_service_net src 10.0.0.0/24
#    acl good_service_net src 10.0.1.0/24 10.0.2.0/24
#    tcp_outgoing_address 10.1.0.1 normal_service_net
#    tcp_outgoing_address 10.1.0.2 good_service_net
#    tcp_outgoing_address 10.1.0.3
#
#    Processing proceeds in the order specified, and stops at first fully
#    matching line.
#
#    Note: The use of this directive using client dependent ACLs is
#    incompatible with the use of server side persistent connections. To
#    ensure correct results it is best to set server_persistent_connections
#    to off when using this directive in such configurations.
#
#Default:
# none

#  TAG: zph_mode
#    This option enables packet level marking of HIT/MISS responses,
#    either using IP TOS or socket priority.
#        off        Feature disabled
#        tos        Set the IP TOS/Diffserv field
#        priority    Set the socket priority (may get mapped to TOS by OS,
#            otherwise only usable in local rulesets)
#        option    Embed the mark in an IP option field. See also
#                zph_option.
#
#    See also tcp_outgoing_tos for details/requirements about TOS usage.
#
#Default:
# zph_mode off

#  TAG: zph_local
#    Allows you to select a TOS/Diffserv/Priority value to mark local hits.
#    Default: 0 (disabled).
#
#Default:
# zph_local 0

#  TAG: zph_sibling
#    Allows you to select a TOS/Diffserv/Priority value to mark sibling hits.
#    Default: 0 (disabled).
#
#Default:
# zph_sibling 0

#  TAG: zph_parent
#    Allows you to select a TOS/Diffserv/Priority value to mark parent hits. 
#    Default: 0 (disabled).
#
#Default:
# zph_parent 0

#  TAG: zph_option
#    The IP option to use when zph_mode is set to "option". Defaults to
#    136 which is officially registered as "SATNET Stream ID".
#
#Default:
# zph_option 136


# OPTIONS WHICH AFFECT THE NEIGHBOR SELECTION ALGORITHM
# -----------------------------------------------------------------------------

#  TAG: cache_peer
#    To specify other caches in a hierarchy, use the format:
#
#        cache_peer hostname type http-port icp-port [options]
#
#    For example,
#
#    #                                        proxy  icp
#    #          hostname             type     port   port  options
#    #          -------------------- -------- ----- -----  -----------
#    cache_peer parent.foo.net       parent    3128  3130  proxy-only default
#    cache_peer sib1.foo.net         sibling   3128  3130  proxy-only
#    cache_peer sib2.foo.net         sibling   3128  3130  proxy-only
#
#          type:  either 'parent', 'sibling', or 'multicast'.
#
#    proxy-port:  The port number where the cache listens for proxy
#             requests.
#
#      icp-port:  Used for querying neighbor caches about
#             objects.  To have a non-ICP neighbor
#             specify '7' for the ICP port and make sure the
#             neighbor machine has the UDP echo port
#             enabled in its /etc/inetd.conf file.
#        NOTE: Also requires icp_port option enabled to send/receive
#              requests via this method.
#
#        options: proxy-only
#             weight=n
#             ttl=n
#             no-query
#             default
#             round-robin
#             carp
#             multicast-responder
#             multicast-siblings
#             closest-only
#             no-digest
#             no-netdb-exchange
#             no-delay
#             login=user:password | PASS | *:password
#             connect-timeout=nn
#             digest-url=url
#             allow-miss
#             max-conn=n
#             htcp
#             htcp-oldsquid
#             originserver
#             userhash
#             sourcehash
#             name=xxx
#             monitorurl=url
#             monitorsize=sizespec
#             monitorinterval=seconds
#             monitortimeout=seconds
#             forceddomain=name
#             ssl
#             sslcert=/path/to/ssl/certificate
#             sslkey=/path/to/ssl/key
#             sslversion=1|2|3|4
#             sslcipher=...
#             ssloptions=...
#             front-end-https[=on|auto]
#             connection-auth[=on|off|auto]
#             idle=n
#             http11
#
#             use 'proxy-only' to specify objects fetched
#             from this cache should not be saved locally.
#
#             use 'weight=n' to affect the selection of a peer
#             during any weighted peer-selection mechanisms.
#             The weight must be an integer; default is 1,
#             larger weights are favored more.
#             This option does not affect parent selection if a peering
#             protocol is not in use.
#
#             use 'ttl=n' to specify a IP multicast TTL to use
#             when sending an ICP queries to this address.
#             Only useful when sending to a multicast group.
#             Because we don't accept ICP replies from random
#             hosts, you must configure other group members as
#             peers with the 'multicast-responder' option below.
#
#             use 'no-query' to NOT send ICP queries to this
#             neighbor.
#
#             use 'default' if this is a parent cache which can
#             be used as a "last-resort" if a peer cannot be located
#             by any of the peer-selection mechanisms.
#             If specified more than once, only the first is used.
#
#             use 'round-robin' to define a set of parents which
#             should be used in a round-robin fashion in the
#             absence of any ICP queries.
#
#             use 'carp' to define a set of parents which should
#             be used as a CARP array. The requests will be
#             distributed among the parents based on the CARP load
#             balancing hash function based on their weight.
#
#             'multicast-responder' indicates the named peer
#             is a member of a multicast group.  ICP queries will
#             not be sent directly to the peer, but ICP replies
#             will be accepted from it.
#
#             the 'multicast-siblings' option is meant to be used
#             only for cache peers of type "multicast". It instructs
#             Squid that ALL members of this multicast group have
#             "sibling" relationship with it, not "parent".  This is
#             an optimization that avoids useless multicast queries
#             to a multicast group when the requested object would
#             be fetched only from a "parent" cache, anyway.  It's
#             useful, e.g., when configuring a pool of redundant
#             Squid proxies, being members of the same
#             multicast group.
#
#             'closest-only' indicates that, for ICP_OP_MISS
#             replies, we'll only forward CLOSEST_PARENT_MISSes
#             and never FIRST_PARENT_MISSes.
#
#             use 'no-digest' to NOT request cache digests from
#             this neighbor.
#
#             'no-netdb-exchange' disables requesting ICMP
#             RTT database (NetDB) from the neighbor.
#
#             use 'no-delay' to prevent access to this neighbor
#             from influencing the delay pools.
#
#             use 'login=user:password' if this is a personal/workgroup
#             proxy and your parent requires proxy authentication.
#             Note: The string can include URL escapes (i.e. %20 for
#             spaces). This also means % must be written as %%.
#
#             use 'login=PASS' if users must authenticate against
#             the upstream proxy or in the case of a reverse proxy
#             configuration, the origin web server.  This will pass
#             the users credentials as they are to the peer.
#             Note: To combine this with local authentication the Basic
#             authentication scheme must be used, and both servers must
#             share the same user database as HTTP only allows for
#             a single login (one for proxy, one for origin server).
#             Also be warned this will expose your users proxy
#             password to the peer. USE WITH CAUTION
#
#             use 'login=*:password' to pass the username to the
#             upstream cache, but with a fixed password. This is meant
#             to be used when the peer is in another administrative
#             domain, but it is still needed to identify each user.
#             The star can optionally be followed by some extra
#             information which is added to the username. This can
#             be used to identify this proxy to the peer, similar to
#             the login=username:password option above.
#
#             use 'connect-timeout=nn' to specify a peer
#             specific connect timeout (also see the
#             peer_connect_timeout directive)
#
#             use 'digest-url=url' to tell Squid to fetch the cache
#             digest (if digests are enabled) for this host from
#             the specified URL rather than the Squid default
#             location.
#
#             use 'allow-miss' to disable Squid's use of only-if-cached
#             when forwarding requests to siblings. This is primarily
#             useful when icp_hit_stale is used by the sibling. To
#             extensive use of this option may result in forwarding
#             loops, and you should avoid having two-way peerings
#             with this option. (for example to deny peer usage on
#             requests from peer by denying cache_peer_access if the
#             source is a peer)
#
#             use 'max-conn=n' to limit the amount of connections Squid
#             may open to this peer.
#
#             use 'htcp' to send HTCP, instead of ICP, queries
#             to the neighbor.  You probably also want to
#             set the "icp port" to 4827 instead of 3130.
#             You must also allow this Squid htcp_access and
#             http_access in the peer Squid configuration.
#
#             use 'htcp-oldsquid' to send HTCP to old Squid versions
#             You must also allow this Squid htcp_access and
#             http_access in the peer Squid configuration.
#
#             'originserver' causes this parent peer to be contacted as
#             a origin server. Meant to be used in accelerator setups.
#
#             use 'userhash' to load-balance amongst a set of parents
#             based on the client proxy_auth or ident username.
#
#             use 'sourcehash' to load-balance amongst a set of parents
#             based on the client source ip.
#
#             use 'name=xxx' if you have multiple peers on the same
#             host but different ports. This name can be used to
#             differentiate the peers in cache_peer_access and similar
#             directives.
#
#             use 'monitorurl=url' to have periodically request a given
#             URL from the peer, and only consider the peer as alive
#             if this monitoring is successful (default none)
#
#             use 'monitorsize=min[-max]' to limit the size range of
#             'monitorurl' replies considered valid. Defaults to 0 to
#             accept any size replies as valid.
#
#             use 'monitorinterval=seconds' to change frequency of
#             how often the peer is monitored with 'monitorurl'
#             (default 300 for a 5 minute interval). If set to 0
#             then monitoring is disabled even if a URL is defined.
#
#             use 'monitortimeout=seconds' to change the timeout of
#             'monitorurl'. Defaults to 'monitorinterval'.
#
#             use 'forceddomain=name' to forcibly set the Host header
#             of requests forwarded to this peer. Useful in accelerator
#             setups where the server (peer) expects a certain domain
#             name and using redirectors to feed this domain name
#             is not feasible.
#
#             use 'ssl' to indicate connections to this peer should
#             be SSL/TLS encrypted.
#
#             use 'sslcert=/path/to/ssl/certificate' to specify a client
#             SSL certificate to use when connecting to this peer.
#
#             use 'sslkey=/path/to/ssl/key' to specify the private SSL
#             key corresponding to sslcert above. If 'sslkey' is not
#             specified 'sslcert' is assumed to reference a
#             combined file containing both the certificate and the key.
#
#             Notes:
#             
#             On Debian/Ubuntu system a default snakeoil certificate is
#             available in /etc/ssl and users can set:
#             
#               cert=/etc/ssl/certs/ssl-cert-snakeoil.pem
#             
#             and
#             
#               key=/etc/ssl/private/ssl-cert-snakeoil.key
#             
#             for testing.
#
#             use sslversion=1|2|3|4 to specify the SSL version to use
#             when connecting to this peer
#            1 = automatic (default)
#            2 = SSL v2 only
#            3 = SSL v3 only
#            4 = TLS v1 only
#
#             use sslcipher=... to specify the list of valid SSL ciphers
#             to use when connecting to this peer.
#
#             use ssloptions=... to specify various SSL engine options:
#            NO_SSLv2  Disallow the use of SSLv2
#            NO_SSLv3  Disallow the use of SSLv3
#            NO_TLSv1  Disallow the use of TLSv1
#             See src/ssl_support.c or the OpenSSL documentation for
#             a more complete list.
#
#             use sslcafile=... to specify a file containing
#             additional CA certificates to use when verifying the
#             peer certificate.
#
#             use sslcapath=... to specify a directory containing
#             additional CA certificates to use when verifying the
#             peer certificate.
#
#             use sslcrlfile=... to specify a certificate revocation
#             list file to use when verifying the peer certificate.
#
#             use sslflags=... to specify various flags modifying the
#             SSL implementation:
#            DONT_VERIFY_PEER
#                Accept certificates even if they fail to
#                verify.
#            NO_DEFAULT_CA
#                Don't use the default CA list built in
#                to OpenSSL.
#
#             use ssldomain= to specify the peer name as advertised
#             in it's certificate. Used for verifying the correctness
#             of the received peer certificate. If not specified the
#             peer hostname will be used.
#
#             use front-end-https to enable the "Front-End-Https: On"
#             header needed when using Squid as a SSL frontend in front
#             of Microsoft OWA. See MS KB document Q307347 for details
#             on this header. If set to auto the header will
#             only be added if the request is forwarded as a https://
#             URL.
#
#             use connection-auth=off to tell Squid that this peer does
#             not support Microsoft connection oriented authentication,
#             and any such challenges received from there should be
#             ignored. Default is auto to automatically determine the
#             status of the peer.
#
#             use idle=n to specify a minimum number of idle connections
#             that should be kept open to this peer.
#
#             use http11 to send requests using HTTP/1.1 to this peer.
#             Note: The HTTP/1.1 support is still incomplete, with an
#             internal HTTP/1.0 hop. As result 1xx responses will not
#             be forwarded.
#
#Default:
# none

#  TAG: cache_peer_domain
#    Use to limit the domains for which a neighbor cache will be
#    queried.  Usage:
#
#    cache_peer_domain cache-host domain [domain ...]
#    cache_peer_domain cache-host !domain
#
#    For example, specifying
#
#        cache_peer_domain parent.foo.net    .edu
#
#    has the effect such that UDP query packets are sent to
#    'bigserver' only when the requested object exists on a
#    server in the .edu domain.  Prefixing the domain name
#    with '!' means the cache will be queried for objects
#    NOT in that domain.
#
#    NOTE:    * Any number of domains may be given for a cache-host,
#          either on the same or separate lines.
#        * When multiple domains are given for a particular
#          cache-host, the first matched domain is applied.
#        * Cache hosts with no domain restrictions are queried
#          for all requests.
#        * There are no defaults.
#        * There is also a 'cache_peer_access' tag in the ACL
#          section.
#
#Default:
# none

#  TAG: cache_peer_access
#    Similar to 'cache_peer_domain' but provides more flexibility by
#    using ACL elements.
#
#    cache_peer_access cache-host allow|deny [!]aclname ...
#
#    The syntax is identical to 'http_access' and the other lists of
#    ACL elements.  See the comments for 'http_access' below, or
#    the Squid FAQ (http://www.squid-cache.org/FAQ/FAQ-10.html).
#
#Default:
# none

#  TAG: neighbor_type_domain
#    usage: neighbor_type_domain neighbor parent|sibling domain domain ...
#
#    Modifying the neighbor type for specific domains is now
#    possible.  You can treat some domains differently than the the
#    default neighbor type specified on the 'cache_peer' line.
#    Normally it should only be necessary to list domains which
#    should be treated differently because the default neighbor type
#    applies for hostnames which do not match domains listed here.
#
#EXAMPLE:
#    cache_peer cache.foo.org parent 3128 3130
#    neighbor_type_domain cache.foo.org sibling .com .net
#    neighbor_type_domain cache.foo.org sibling .au .de
#
#Default:
# none

#  TAG: dead_peer_timeout    (seconds)
#    This controls how long Squid waits to declare a peer cache
#    as "dead."  If there are no ICP replies received in this
#    amount of time, Squid will declare the peer dead and not
#    expect to receive any further ICP replies.  However, it
#    continues to send ICP queries, and will mark the peer as
#    alive upon receipt of the first subsequent ICP reply.
#
#    This timeout also affects when Squid expects to receive ICP
#    replies from peers.  If more than 'dead_peer' seconds have
#    passed since the last ICP reply was received, Squid will not
#    expect to receive an ICP reply on the next query.  Thus, if
#    your time between requests is greater than this timeout, you
#    will see a lot of requests sent DIRECT to origin servers
#    instead of to your parents.
#
#Default:
# dead_peer_timeout 10 seconds

#  TAG: hierarchy_stoplist
#    A list of words which, if found in a URL, cause the object to
#    be handled directly by this cache.  In other words, use this
#    to not query neighbor caches for certain objects.  You may
#    list this option multiple times. Note: never_direct overrides
#    this option.
#We recommend you to use at least the following line.
hierarchy_stoplist cgi-bin ?


# MEMORY CACHE OPTIONS
# -----------------------------------------------------------------------------

#  TAG: cache_mem    (bytes)
#    NOTE: THIS PARAMETER DOES NOT SPECIFY THE MAXIMUM PROCESS SIZE.
#    IT ONLY PLACES A LIMIT ON HOW MUCH ADDITIONAL MEMORY SQUID WILL
#    USE AS A MEMORY CACHE OF OBJECTS. SQUID USES MEMORY FOR OTHER
#    THINGS AS WELL. SEE THE SQUID FAQ SECTION 8 FOR DETAILS.
#
#    'cache_mem' specifies the ideal amount of memory to be used
#    for:
#        * In-Transit objects
#        * Hot Objects
#        * Negative-Cached objects
#
#    Data for these objects are stored in 4 KB blocks.  This
#    parameter specifies the ideal upper limit on the total size of
#    4 KB blocks allocated.  In-Transit objects take the highest
#    priority.
#
#    In-transit objects have priority over the others.  When
#    additional space is needed for incoming data, negative-cached
#    and hot objects will be released.  In other words, the
#    negative-cached and hot objects will fill up any unused space
#    not needed for in-transit objects.
#
#    If circumstances require, this limit will be exceeded.
#    Specifically, if your incoming request rate requires more than
#    'cache_mem' of memory to hold in-transit objects, Squid will
#    exceed this limit to satisfy the new requests.  When the load
#    decreases, blocks will be freed until the high-water mark is
#    reached.  Thereafter, blocks will be used to store hot
#    objects.
#
#Default:
# cache_mem 8 MB
cache_mem 512 MB
#  TAG: maximum_object_size_in_memory    (bytes)
#    Objects greater than this size will not be attempted to kept in
#    the memory cache. This should be set high enough to keep objects
#    accessed frequently in memory to improve performance whilst low
#    enough to keep larger objects from hoarding cache_mem.
#
#Default:
# maximum_object_size_in_memory 8 KB

#  TAG: memory_replacement_policy
#    The memory replacement policy parameter determines which
#    objects are purged from memory when memory space is needed.
#
#    See cache_replacement_policy for details.
#
#Default:
# memory_replacement_policy lru


# DISK CACHE OPTIONS
# -----------------------------------------------------------------------------

#  TAG: cache_replacement_policy
#    The cache replacement policy parameter determines which
#    objects are evicted (replaced) when disk space is needed.
#
#        lru       : Squid's original list based LRU policy
#        heap GDSF : Greedy-Dual Size Frequency
#        heap LFUDA: Least Frequently Used with Dynamic Aging
#        heap LRU  : LRU policy implemented using a heap
#
#    Applies to any cache_dir lines listed below this.
#
#    The LRU policies keeps recently referenced objects.
#
#    The heap GDSF policy optimizes object hit rate by keeping smaller
#    popular objects in cache so it has a better chance of getting a
#    hit.  It achieves a lower byte hit rate than LFUDA though since
#    it evicts larger (possibly popular) objects.
#
#    The heap LFUDA policy keeps popular objects in cache regardless of
#    their size and thus optimizes byte hit rate at the expense of
#    hit rate since one large, popular object will prevent many
#    smaller, slightly less popular objects from being cached.
#
#    Both policies utilize a dynamic aging mechanism that prevents
#    cache pollution that can otherwise occur with frequency-based
#    replacement policies.
#
#    NOTE: if using the LFUDA replacement policy you should increase
#    the value of maximum_object_size above its default of 4096 KB to
#    to maximize the potential byte hit rate improvement of LFUDA.
#
#    For more information about the GDSF and LFUDA cache replacement
#    policies see http://www.hpl.hp.com/techreports/1999/HPL-1999-69.html
#    and http://fog.hpl.external.hp.com/techreports/98/HPL-98-173.html.
#
#Default:
# cache_replacement_policy lru

#  TAG: cache_dir
#    Usage:
#
#    cache_dir Type Directory-Name Fs-specific-data [options]
#
#    You can specify multiple cache_dir lines to spread the
#    cache among different disk partitions.
#
#    Type specifies the kind of storage system to use. Only "ufs"
#    is built by default. To enable any of the other storage systems
#    see the --enable-storeio configure option.
#
#    'Directory' is a top-level directory where cache swap
#    files will be stored. If you want to use an entire disk
#    for caching, this can be the mount-point directory.
#    The directory must exist and be writable by the Squid
#    process. Squid will NOT create this directory for you.
#    Only using COSS, a raw disk device or a stripe file can
#    be specified, but the configuration of the "cache_swap_log"
#    tag is mandatory.
#
#    The ufs store type:
#
#    "ufs" is the old well-known Squid storage format that has always
#    been there.
#
#    cache_dir ufs Directory-Name Mbytes L1 L2 [options]
#
#    'Mbytes' is the amount of disk space (MB) to use under this
#    directory.  The default is 100 MB.  Change this to suit your
#    configuration.  Do NOT put the size of your disk drive here.
#    Instead, if you want Squid to use the entire disk drive,
#    subtract 20% and use that value.
#
#    'Level-1' is the number of first-level subdirectories which
#    will be created under the 'Directory'.  The default is 16.
#
#    'Level-2' is the number of second-level subdirectories which
#    will be created under each first-level directory.  The default
#    is 256.
#
#    The aufs store type:
#
#    "aufs" uses the same storage format as "ufs", utilizing
#    POSIX-threads to avoid blocking the main Squid process on
#    disk-I/O. This was formerly known in Squid as async-io.
#
#    cache_dir aufs Directory-Name Mbytes L1 L2 [options]
#
#    see argument descriptions under ufs above
#
#    The diskd store type:
#
#    "diskd" uses the same storage format as "ufs", utilizing a
#    separate process to avoid blocking the main Squid process on
#    disk-I/O.
#
#    cache_dir diskd Directory-Name Mbytes L1 L2 [options] [Q1=n] [Q2=n]
#
#    see argument descriptions under ufs above
#
#    Q1 specifies the number of unacknowledged I/O requests when Squid
#    stops opening new files. If this many messages are in the queues,
#    Squid won't open new files. Default is 64
#
#    Q2 specifies the number of unacknowledged messages when Squid
#    starts blocking.  If this many messages are in the queues,
#    Squid blocks until it receives some replies. Default is 72
#
#    When Q1 < Q2 (the default), the cache directory is optimized
#    for lower response time at the expense of a decrease in hit
#    ratio.  If Q1 > Q2, the cache directory is optimized for
#    higher hit ratio at the expense of an increase in response
#    time.
#
#    The coss store type:
#
#    block-size=n defines the "block size" for COSS cache_dir's.
#    Squid uses file numbers as block numbers.  Since file numbers
#    are limited to 24 bits, the block size determines the maximum
#    size of the COSS partition.  The default is 512 bytes, which
#    leads to a maximum cache_dir size of 512<<24, or 8 GB.  Note
#    you should not change the COSS block size after Squid
#    has written some objects to the cache_dir.
#
#    overwrite-percent=n defines the percentage of disk that COSS
#    must write to before a given object will be moved to the
#    current stripe.  A value of "n" closer to 100 will cause COSS
#    to waste less disk space by having multiple copies of an object
#    on disk, but will increase the chances of overwriting a popular
#    object as COSS overwrites stripes.  A value of "n" close to 0
#    will cause COSS to keep all current objects in the current COSS
#    stripe at the expense of the hit rate.  The default value of 50
#    will allow any given object to be stored on disk a maximum of
#    2 times.
#
#    max-stripe-waste=n defines the maximum amount of space that COSS
#    will waste in a given stripe (in bytes).  When COSS writes data
#    to disk, it will potentially waste up to "max-size" worth of disk
#    space for each 1MB of data written.  If "max-size" is set to a
#    large value (ie >256k), this could potentially result in large
#    amounts of wasted disk space. Setting this value to a lower value
#    (ie 64k or 32k) will result in a COSS disk refusing to cache
#    larger objects until the COSS stripe has been filled to within
#    "max-stripe-waste" of the maximum size (1MB).
#
#    membufs=n defines the number of "memory-only" stripes that COSS
#    will use.  When an cache hit is performed on a COSS stripe before
#    COSS has reached the overwrite-percent value for that object,
#    COSS will use a series of memory buffers to hold the object in
#    while the data is sent to the client.  This will define the maximum
#    number of memory-only buffers that COSS will use.  The default value
#    is 10, which will use a maximum of 10MB of memory for buffers.
#
#    maxfullbufs=n defines the maximum number of stripes a COSS partition
#    will have in memory waiting to be freed (either because the disk is
#    under load and the stripe is unwritten, or because clients are still
#    transferring data from objects using the memory).  In order to try
#    and maintain a good hit rate under load, COSS will reserve the last
#    2 full stripes for object hits. (ie a COSS cache_dir will reject
#    new objects when the number of full stripes is 2 less than maxfullbufs)
#
#    The null store type:
#
#    no options are allowed or required
#
#    Common options:
#
#    no-store, no new objects should be stored to this cache_dir
#
#    min-size=n, refers to the min object size this storedir will accept.
#    It's used to restrict a storedir to only store large objects
#    (e.g. aufs) while other storedirs are optimized for smaller objects
#    (e.g. COSS). Defaults to 0.
#
#    max-size=n, refers to the max object size this storedir supports.
#    It is used to initially choose the storedir to dump the object.
#    Note: To make optimal use of the max-size limits you should order
#    the cache_dir lines with the smallest max-size value first and the
#    ones with no max-size specification last.
#
#    Note that for coss, max-size must be less than COSS_MEMBUF_SZ
#    (hard coded at 1 MB).
#
#Default:
# cache_dir ufs /var/spool/squid 100 16 256
cache_dir ufs /var/spool/squid 40000 16 256
#  TAG: store_dir_select_algorithm
#    Set this to 'round-robin' as an alternative.
#
#Default:
# store_dir_select_algorithm least-load

#  TAG: max_open_disk_fds
#    To avoid having disk as the I/O bottleneck Squid can optionally
#    bypass the on-disk cache if more than this amount of disk file
#    descriptors are open.
#
#    A value of 0 indicates no limit.
#
#Default:
# max_open_disk_fds 0

#  TAG: minimum_object_size    (bytes)
#    Objects smaller than this size will NOT be saved on disk.  The
#    value is specified in kilobytes, and the default is 0 KB, which
#    means there is no minimum.
#
#Default:
# minimum_object_size 0 KB

#  TAG: maximum_object_size    (bytes)
#    Objects larger than this size will NOT be saved on disk.  The
#    value is specified in kilobytes, and the default is 4MB.  If
#    you wish to get a high BYTES hit ratio, you should probably
#    increase this (one 32 MB object hit counts for 3200 10KB
#    hits).  If you wish to increase speed more than your want to
#    save bandwidth you should leave this low.
#
#    NOTE: if using the LFUDA replacement policy you should increase
#    this value to maximize the byte hit rate improvement of LFUDA!
#    See replacement_policy below for a discussion of this policy.
#
#    NOTE 2: In Debian the default is raised to 20MB allowing cache
#    of Packages files in debian repositories. This makes squid a
#    proper proxy for APT.
#
#Default:
# maximum_object_size 20480 KB

#  TAG: cache_swap_low    (percent, 0-100)
#  TAG: cache_swap_high    (percent, 0-100)
#
#    The low- and high-water marks for cache object replacement.
#    Replacement begins when the swap (disk) usage is above the
#    low-water mark and attempts to maintain utilization near the
#    low-water mark.  As swap utilization gets close to high-water
#    mark object eviction becomes more aggressive.  If utilization is
#    close to the low-water mark less replacement is done each time.
#
#    Defaults are 90% and 95%. If you have a large cache, 5% could be
#    hundreds of MB. If this is the case you may wish to set these
#    numbers closer together.
#
#Default:
# cache_swap_low 90
# cache_swap_high 95

#  TAG: update_headers    on|off
#    By default Squid updates stored HTTP headers when receiving
#    a 304 response. Set this to off if you want to disable this
#    for disk I/O performance reasons. Disabling this VIOLATES the
#    HTTP standard, and could make you liable for problems which it
#    causes.
#
#Default:
# update_headers on


# LOGFILE OPTIONS
# -----------------------------------------------------------------------------

#  TAG: logformat
#    Usage:
#
#    logformat <name> <format specification>
#
#    Defines an access log format.
#
#    The <format specification> is a string with embedded % format codes
#
#    % format codes all follow the same basic structure where all but
#    the formatcode is optional. Output strings are automatically escaped
#    as required according to their context and the output format
#    modifiers are usually not needed, but can be specified if an explicit
#    output format is desired.
#
#        % ["|[|'|#] [-] [[0]width] [{argument}] formatcode
#
#        "    output in quoted string format
#        [    output in squid text log format as used by log_mime_hdrs
#        #    output in URL quoted format
#        '    output as-is
#
#        -    left aligned
#        width    field width. If starting with 0 the
#            output is zero padded
#        {arg}    argument such as header name etc
#
#    Format codes:
#
#        >a    Client source IP address
#        >A    Client FQDN
#        >p    Client source port
#        <A    Server IP address or peer name
#        la    Local IP address (http_port)
#        lp    Local port number (http_port)
#        oa    Our outgoing IP address (tcp_outgoing_address)
#        ts    Seconds since epoch
#        tu    subsecond time (milliseconds)
#        tl    Local time. Optional strftime format argument
#            default %d/%b/%Y:%H:%M:%S %z
#        tg    GMT time. Optional strftime format argument
#            default %d/%b/%Y:%H:%M:%S %z
#        tr    Response time (milliseconds)
#        >h    Request header. Optional header name argument
#            on the format header[:[separator]element]
#        <h    Reply header. Optional header name argument
#            as for >h
#        un    User name
#        ul    User name from authentication
#        ui    User name from ident
#        us    User name from SSL
#        ue    User name from external acl helper
#        Hs    HTTP status code
#        Ss    Squid request status (TCP_MISS etc)
#        Sh    Squid hierarchy status (DEFAULT_PARENT etc)
#        mt    MIME content type
#        rm    Request method (GET/POST etc)
#        ru    Request URL
#        rp    Request URL-Path excluding hostname
#        rv    Request protocol version
#        ea    Log string returned by external acl
#        <st    Reply size including HTTP headers
#        >st    Request size including HTTP headers
#        st    Request+Reply size including HTTP headers
#        sn    Unique sequence number per log line entry
#        %    a literal % character
#
#    The default formats available (which do not need re-defining) are:
#
#logformat squid %ts.%03tu %6tr %>a %Ss/%03Hs %<st %rm %ru %un %Sh/%<A %mt
#logformat squidmime %ts.%03tu %6tr %>a %Ss/%03Hs %<st %rm %ru %un %Sh/%<A %mt [%>h] [%<h]
#logformat common %>a %ui %un [%tl] "%rm %ru HTTP/%rv" %Hs %<st %Ss:%Sh
#logformat combined %>a %ui %un [%tl] "%rm %ru HTTP/%rv" %Hs %<st "%{Referer}>h" "%{User-Agent}>h" %Ss:%Sh
#
#Default:
# none

#  TAG: access_log
#    These files log client request activities. Has a line every HTTP or
#    ICP request. The format is:
#    access_log <filepath> [<logformat name> [acl acl ...]]
#    access_log none [acl acl ...]]
#
#    Will log to the specified file using the specified format (which
#    must be defined in a logformat directive) those entries which match
#    ALL the acl's specified (which must be defined in acl clauses).
#    If no acl is specified, all requests will be logged to this file.
#
#    To disable logging of a request use the filepath "none", in which case
#    a logformat name should not be specified.
#
#    To log the request via syslog specify a filepath of "syslog":
#
#    access_log syslog[:facility.priority] [format [acl1 [acl2 ....]]]
#    where facility could be any of:
#    authpriv, daemon, local0 .. local7 or user.
#
#    And priority could be any of:
#    err, warning, notice, info, debug.
access_log /var/log/squid/access.log squid

#  TAG: log_access    allow|deny acl acl...
#    This options allows you to control which requests gets logged
#    to access.log (see access_log directive). Requests denied for
#    logging will also not be accounted for in performance counters.
#
#Default:
# none

#  TAG: logfile_daemon
#    Specify the path to the logfile-writing daemon. This daemon is
#    used to write the access and store logs, if configured.
#
#Default:
# logfile_daemon /usr/lib/squid/logfile-daemon

#  TAG: cache_log
#    Cache logging file. This is where general information about
#    your cache's behavior goes. You can increase the amount of data
#    logged to this file with the "debug_options" tag below.
#
#Default:
# cache_log /var/log/squid/cache.log

#  TAG: cache_store_log
#    Logs the activities of the storage manager.  Shows which
#    objects are ejected from the cache, and which objects are
#    saved and for how long.  To disable, enter "none". There are
#    not really utilities to analyze this data, so you can safely
#    disable it.
#
#Default:
# cache_store_log /var/log/squid/store.log

#  TAG: cache_swap_state
#    Location for the cache "swap.state" file. This index file holds
#    the metadata of objects saved on disk.  It is used to rebuild
#    the cache during startup.  Normally this file resides in each
#    'cache_dir' directory, but you may specify an alternate
#    pathname here.  Note you must give a full filename, not just
#    a directory. Since this is the index for the whole object
#    list you CANNOT periodically rotate it!
#
#    If %s can be used in the file name it will be replaced with a
#    a representation of the cache_dir name where each / is replaced
#    with '.'. This is needed to allow adding/removing cache_dir
#    lines when cache_swap_log is being used.
#
#    If have more than one 'cache_dir', and %s is not used in the name
#    these swap logs will have names such as:
#
#        cache_swap_log.00
#        cache_swap_log.01
#        cache_swap_log.02
#
#    The numbered extension (which is added automatically)
#    corresponds to the order of the 'cache_dir' lines in this
#    configuration file.  If you change the order of the 'cache_dir'
#    lines in this file, these index files will NOT correspond to
#    the correct 'cache_dir' entry (unless you manually rename
#    them).  We recommend you do NOT use this option.  It is
#    better to keep these index files in each 'cache_dir' directory.
#
#Default:
# none

#  TAG: logfile_rotate
#    Specifies the number of logfile rotations to make when you
#    type 'squid -k rotate'.  The default is 10, which will rotate
#    with extensions 0 through 9.  Setting logfile_rotate to 0 will
#    disable the file name rotation, but the logfiles are still closed
#    and re-opened.  This will enable you to rename the logfiles
#    yourself just before sending the rotate signal.
#
#    Note, the 'squid -k rotate' command normally sends a USR1
#    signal to the running squid process.  In certain situations
#    (e.g. on Linux with Async I/O), USR1 is used for other
#    purposes, so -k rotate uses another signal.  It is best to get
#    in the habit of using 'squid -k rotate' instead of 'kill -USR1
#    <pid>'.
#
#    Note2, for Debian/Linux the default of logfile_rotate is
#    zero, since it includes external logfile-rotation methods.
#
#Default:
# logfile_rotate 0

#  TAG: emulate_httpd_log    on|off
#    The Cache can emulate the log file format which many 'httpd'
#    programs use.  To disable/enable this emulation, set
#    emulate_httpd_log to 'off' or 'on'.  The default
#    is to use the native log format since it includes useful
#    information Squid-specific log analyzers use.
#
#Default:
# emulate_httpd_log off

#  TAG: log_ip_on_direct    on|off
#    Log the destination IP address in the hierarchy log tag when going
#    direct. Earlier Squid versions logged the hostname here. If you
#    prefer the old way set this to off.
#
#Default:
# log_ip_on_direct on

#  TAG: mime_table
#    Pathname to Squid's MIME table. You shouldn't need to change
#    this, but the default file contains examples and formatting
#    information if you do.
#
#Default:
# mime_table /usr/share/squid/mime.conf

#  TAG: log_mime_hdrs    on|off
#    The Cache can record both the request and the response MIME
#    headers for each HTTP transaction.  The headers are encoded
#    safely and will appear as two bracketed fields at the end of
#    the access log (for either the native or httpd-emulated log
#    formats).  To enable this logging set log_mime_hdrs to 'on'.
#
#Default:
# log_mime_hdrs off

#  TAG: useragent_log
#    Squid will write the User-Agent field from HTTP requests
#    to the filename specified here.  By default useragent_log
#    is disabled.
#
#Default:
# none

#  TAG: referer_log
#    Squid will write the Referer field from HTTP requests to the
#    filename specified here.  By default referer_log is disabled.
#    Note that "referer" is actually a misspelling of "referrer"
#    however the misspelt version has been accepted into the HTTP RFCs
#    and we accept both.
#
#Default:
# none

#  TAG: pid_filename
#    A filename to write the process-id to.  To disable, enter "none".
#
#Default:
# pid_filename /var/run/squid.pid

#  TAG: debug_options
#    Logging options are set as section,level where each source file
#    is assigned a unique section.  Lower levels result in less
#    output,  Full debugging (level 9) can result in a very large
#    log file, so be careful.  The magic word "ALL" sets debugging
#    levels for all sections.  We recommend normally running with
#    "ALL,1".
#
#Default:
# debug_options ALL,1

#  TAG: log_fqdn    on|off
#    Turn this on if you wish to log fully qualified domain names
#    in the access.log. To do this Squid does a DNS lookup of all
#    IP's connecting to it. This can (in some situations) increase
#    latency, which makes your cache seem slower for interactive
#    browsing.
#
#Default:
# log_fqdn off

#  TAG: client_netmask
#    A netmask for client addresses in logfiles and cachemgr output.
#    Change this to protect the privacy of your cache clients.
#    A netmask of 255.255.255.0 will log all IP's in that range with
#    the last digit set to '0'.
#
#Default:
# client_netmask 255.255.255.255

#  TAG: forward_log
# Note: This option is only available if Squid is rebuilt with the
#       --enable-forward-log option
#
#    Logs the server-side requests.
#
#    This is currently work in progress.
#
#Default:
# none

#  TAG: strip_query_terms
#    By default, Squid strips query terms from requested URLs before
#    logging.  This protects your user's privacy.
#
#Default:
# strip_query_terms on

#  TAG: buffered_logs    on|off
#    cache.log log file is written with stdio functions, and as such
#    it can be buffered or unbuffered. By default it will be unbuffered.
#    Buffering it can speed up the writing slightly (though you are
#    unlikely to need to worry unless you run with tons of debugging
#    enabled in which case performance will suffer badly anyway..).
#
#Default:
# buffered_logs off

#  TAG: netdb_filename
#    A filename where Squid stores it's netdb state between restarts.
#    To disable, enter "none".
#
#Default:
# netdb_filename /var/spool/squid/logs/netdb.state


# OPTIONS FOR FTP GATEWAYING
# -----------------------------------------------------------------------------

#  TAG: ftp_user
#    If you want the anonymous login password to be more informative
#    (and enable the use of picky ftp servers), set this to something
#    reasonable for your domain, like wwwuser@somewhere.net
#
#    The reason why this is domainless by default is the
#    request can be made on the behalf of a user in any domain,
#    depending on how the cache is used.
#    Some ftp server also validate the email address is valid
#    (for example perl.com).
#
#Default:
# ftp_user Squid@

#  TAG: ftp_list_width
#    Sets the width of ftp listings. This should be set to fit in
#    the width of a standard browser. Setting this too small
#    can cut off long filenames when browsing ftp sites.
#
#Default:
# ftp_list_width 32

#  TAG: ftp_passive
#    If your firewall does not allow Squid to use passive
#    connections, turn off this option.
#
#Default:
# ftp_passive on

#  TAG: ftp_sanitycheck
#    For security and data integrity reasons Squid by default performs
#    sanity checks of the addresses of FTP data connections ensure the
#    data connection is to the requested server. If you need to allow
#    FTP connections to servers using another IP address for the data
#    connection turn this off.
#
#Default:
# ftp_sanitycheck on

#  TAG: ftp_telnet_protocol
#    The FTP protocol is officially defined to use the telnet protocol
#    as transport channel for the control connection. However, many
#    implementations are broken and does not respect this aspect of
#    the FTP protocol.
#
#    If you have trouble accessing files with ASCII code 255 in the
#    path or similar problems involving this ASCII code you can
#    try setting this directive to off. If that helps, report to the
#    operator of the FTP server in question that their FTP server
#    is broken and does not follow the FTP standard.
#
#Default:
# ftp_telnet_protocol on


# OPTIONS FOR EXTERNAL SUPPORT PROGRAMS
# -----------------------------------------------------------------------------

#  TAG: diskd_program
#    Specify the location of the diskd executable.
#    Note this is only useful if you have compiled in
#    diskd as one of the store io modules.
#
#Default:
# diskd_program /usr/lib/squid/diskd-daemon

#  TAG: unlinkd_program
#    Specify the location of the executable for file deletion process.
#
#Default:
# unlinkd_program /usr/lib/squid/unlinkd

#  TAG: pinger_program
# Note: This option is only available if Squid is rebuilt with the
#       --enable-icmp option
#
#    Specify the location of the executable for the pinger process.
#
#Default:
# pinger_program /usr/lib/squid/pinger


# OPTIONS FOR URL REWRITING
# -----------------------------------------------------------------------------

#  TAG: storeurl_rewrite_program
#    Specify the location of the executable for the Store URL rewriter.
#    The Store URL rewriter allows URLs to be "normalised" ; mapping
#    multiple URLs to a single URL representation for cache operations.
#
#    For example, if you request an object at:
#
#    http://srv1.example.com/image.gif
#
#    and a subsequent request for:
#
#    http://srv2.example.com/image.gif
#
#    then Squid will treat these both as different URLs and cache them
#    seperately.
#
#    This is almost the normal case, but an increasing number of sites
#    distribute the same content between multiple frontend hosts.
#    The Store URL rewriter allows you to rewrite these URLs to one URL
#    to use for cache operations, but not -fetches-. Fetches are still
#    made from the original site, but stored with the store URL rewritten
#    URL as the store key.
#
#    For each requested URL rewriter will receive on line with the format
#
#    URL <SP> client_ip "/" fqdn <SP> user <SP> method <SP> urlgroup
#     [<SP> kvpairs] <NL>
#
#    In the future, the rewriter interface will be extended with
#    key=value pairs ("kvpairs" shown above).  Rewriter programs
#    should be prepared to receive and possibly ignore additional
#    whitespace-separated tokens on each input line.
#
#    And the rewriter may return a rewritten URL. The other components of
#    the request line does not need to be returned (ignored if they are).
#
#    By default, a Store URL rewriter is not used.
#
#    Please note - the normal URL rewriter rewrites Squid's _destination_
#    URL - ie, what it fetches. The Store URL rewriter rewrites Squid's
#    _store_ URL - ie, what it uses to store and retrieve objects.
#
#Default:
# none

#  TAG: storeurl_rewrite_children
#
#
#Default:
# storeurl_rewrite_children 5

#  TAG: storeurl_rewrite_concurrency
#
#
#Default:
# storeurl_rewrite_concurrency 0

#  TAG: url_rewrite_program
#    Specify the location of the executable for the URL rewriter.
#    Since they can perform almost any function there isn't one included.
#
#    For each requested URL rewriter will receive on line with the format
#
#    URL <SP> client_ip "/" fqdn <SP> user <SP> method <SP> urlgroup
#     [<SP> kvpairs] <NL>
#
#    In the future, the rewriter interface will be extended with
#    key=value pairs ("kvpairs" shown above).  Rewriter programs
#    should be prepared to receive and possibly ignore additional
#    whitespace-separated tokens on each input line.
#
#    And the rewriter may return a rewritten URL. The other components of
#    the request line does not need to be returned (ignored if they are).
#
#    The rewriter can also indicate that a client-side redirect should
#    be performed to the new URL. This is done by prefixing the returned
#    URL with "301:" (moved permanently) or 302: (moved temporarily).
#
#    It can also return a "urlgroup" that can subsequently be matched
#    in cache_peer_access and similar ACL driven rules. An urlgroup is
#    returned by prefixing the returned URL with "!urlgroup!".
#
#    By default, a URL rewriter is not used.
#
#Default:
# none

#  TAG: url_rewrite_children
#    The number of redirector processes to spawn. If you start
#    too few Squid will have to wait for them to process a backlog of
#    URLs, slowing it down. If you start too many they will use RAM
#    and other system resources.
#
#Default:
# url_rewrite_children 5

#  TAG: url_rewrite_concurrency
#    The number of requests each redirector helper can handle in
#    parallel. Defaults to 0 which indicates the redirector
#    is a old-style single threaded redirector.
#
#    When this directive is set to a value >= 1 then the protocol
#    used to communicate with the helper is modified to include
#    a request ID in front of the request/response. The request
#    ID from the request must be echoed back with the response
#    to that request.
#
#Default:
# url_rewrite_concurrency 0

#  TAG: url_rewrite_host_header
#    By default Squid rewrites any Host: header in redirected
#    requests.  If you are running an accelerator this may
#    not be a wanted effect of a redirector.
#
#    WARNING: Entries are cached on the result of the URL rewriting
#    process, so be careful if you have domain-virtual hosts.
#
#Default:
# url_rewrite_host_header on

#  TAG: url_rewrite_access
#    If defined, this access list specifies which requests are
#    sent to the redirector processes.  By default all requests
#    are sent.
#
#Default:
# none

#  TAG: storeurl_access
#
#
#Default:
# none

#  TAG: redirector_bypass
#    When this is 'on', a request will not go through the
#    redirector if all redirectors are busy.  If this is 'off'
#    and the redirector queue grows too large, Squid will exit
#    with a FATAL error and ask you to increase the number of
#    redirectors.  You should only enable this if the redirectors
#    are not critical to your caching system.  If you use
#    redirectors for access control, and you enable this option,
#    users may have access to pages they should not
#    be allowed to request.
#
#Default:
# redirector_bypass off

#  TAG: location_rewrite_program
#    Specify the location of the executable for the Location rewriter,
#    used to rewrite server generated redirects. Usually used in
#    conjunction with a url_rewrite_program
#
#    For each Location header received the location rewriter will receive
#    one line with the format:
#
#       location URL <SP> requested URL <SP> urlgroup <NL>
#
#    And the rewriter may return a rewritten Location URL or a blank line.
#    The other components of the request line does not need to be returned
#    (ignored if they are).
#
#    By default, a Location rewriter is not used.
#
#Default:
# none

#  TAG: location_rewrite_children
#    The number of location rewriting processes to spawn. If you start
#    too few Squid will have to wait for them to process a backlog of
#    URLs, slowing it down. If you start too many they will use RAM
#    and other system resources.
#
#Default:
# location_rewrite_children 5

#  TAG: location_rewrite_concurrency
#    The number of requests each Location rewriter helper can handle in
#    parallel. Defaults to 0 which indicates that the helper
#    is a old-style singlethreaded helper.
#
#Default:
# location_rewrite_concurrency 0

#  TAG: location_rewrite_access
#    If defined, this access list specifies which requests are
#    sent to the location rewriting processes.  By default all Location
#    headers are sent.
#
#Default:
# none


# OPTIONS FOR TUNING THE CACHE
# -----------------------------------------------------------------------------

#  TAG: cache
#    A list of ACL elements which, if matched, cause the request to
#    not be satisfied from the cache and the reply to not be cached.
#    In other words, use this to force certain objects to never be cached.
#
#    You must use the word 'DENY' to indicate the ACL names which should
#    NOT be cached.
#
#    Default is to allow all to be cached.
#
#Default:
# none

#  TAG: max_stale    time-units
#    This option puts an upper limit on how stale content Squid
#    will serve from the cache if cache validation fails.
#
#Default:
# max_stale 1 week

#  TAG: refresh_pattern
#    usage: refresh_pattern [-i] regex min percent max [options]
#
#    By default, regular expressions are CASE-SENSITIVE.  To make
#    them case-insensitive, use the -i option.
#
#    'Min' is the time (in minutes) an object without an explicit
#    expiry time should be considered fresh. The recommended
#    value is 0, any higher values may cause dynamic applications
#    to be erroneously cached unless the application designer
#    has taken the appropriate actions.
#
#    'Percent' is a percentage of the objects age (time since last
#    modification age) an object without explicit expiry time
#    will be considered fresh.
#
#    'Max' is an upper limit on how long objects without an explicit
#    expiry time will be considered fresh.
#
#    options: override-expire
#         override-lastmod
#         reload-into-ims
#         ignore-reload
#         ignore-no-cache
#         ignore-private
#         ignore-auth
#         stale-while-revalidate=NN
#         ignore-stale-while-revalidate
#         max-stale=NN
#         negative-ttl=NN
#
#        override-expire enforces min age even if the server
#        sent an explicit expiry time (e.g., with the
#        Expires: header or Cache-Control: max-age). Doing this
#        VIOLATES the HTTP standard.  Enabling this feature
#        could make you liable for problems which it causes.
#
#        Note: this does not enforce staleness - it only extends
#        freshness / min. If the server returns a Expires time which
#        is longer than your max time, Squid will still consider
#        the object fresh for that period of time.
#
#        override-lastmod enforces min age even on objects
#        that were modified recently.
#
#        reload-into-ims changes client no-cache or ``reload''
#        to If-Modified-Since requests. Doing this VIOLATES the
#        HTTP standard. Enabling this feature could make you
#        liable for problems which it causes.
#
#        ignore-reload ignores a client no-cache or ``reload''
#        header. Doing this VIOLATES the HTTP standard. Enabling
#        this feature could make you liable for problems which
#        it causes.
#
#        ignore-no-cache ignores any ``Pragma: no-cache'' and
#        ``Cache-control: no-cache'' headers received from a server.
#        The HTTP RFC never allows the use of this (Pragma) header
#        from a server, only a client, though plenty of servers
#        send it anyway.
#
#        ignore-private ignores any ``Cache-control: private''
#        headers received from a server. Doing this VIOLATES
#        the HTTP standard. Enabling this feature could make you
#        liable for problems which it causes.
#
#        ignore-auth caches responses to requests with authorization,
#        as if the originserver had sent ``Cache-control: public''
#        in the response header. Doing this VIOLATES the HTTP standard.
#        Enabling this feature could make you liable for problems which
#        it causes.
#
#        stale-while-revalidate=NN makes Squid perform an asyncronous
#        cache validation if the object isn't more stale than NN.
#        Doing this VIOLATES the HTTP standard. Enabling this
#        feature could make you liable for problems which it
#        causes.
#
#        ignore-stale-while-revalidate makes Squid ignore any 'Cache-Control:
#        stale-while-revalidate=NN' headers received from a server. Can be
#        combined with stale-while-revalidate=NN to override the server provided
#        value.
#
#        max-stale=NN provided a maximum staleness factor. Squid won't
#        serve objects more stale than this even if it failed to
#        validate the object.
#
#        negative-ttl=NN overrides the global negative_ttl parameter
#        selectively for URLs matching this pattern (in seconds).
#
#    Basically a cached object is:
#
#        FRESH if expires < now, else STALE
#        STALE if age > max
#        FRESH if lm-factor < percent, else STALE
#        FRESH if age < min
#        else STALE
#
#    The refresh_pattern lines are checked in the order listed here.
#    The first entry which matches is used.  If none of the entries
#    match the default will be used.
#
#    Note, you must uncomment all the default lines if you want
#    to change one. The default setting is only active if none is
#    used.
#
#Suggested default:
refresh_pattern ^ftp:        1440    20%    10080
refresh_pattern ^gopher:    1440    0%    1440
refresh_pattern -i (/cgi-bin/|\?) 0    0%    0
refresh_pattern (Release|Package(.gz)*)$    0    20%    2880
# example line deb packages
#refresh_pattern (\.deb|\.udeb)$   129600 100% 129600
refresh_pattern .        0    20%    4320

#  TAG: quick_abort_min    (KB)
#  TAG: quick_abort_max    (KB)
#  TAG: quick_abort_pct    (percent)
#    The cache by default continues downloading aborted requests
#    which are almost completed (less than 16 KB remaining). This
#    may be undesirable on slow (e.g. SLIP) links and/or very busy
#    caches.  Impatient users may tie up file descriptors and
#    bandwidth by repeatedly requesting and immediately aborting
#    downloads.
#
#    When the user aborts a request, Squid will check the
#    quick_abort values to the amount of data transfered until
#    then.
#
#    If the transfer has less than 'quick_abort_min' KB remaining,
#    it will finish the retrieval.
#
#    If the transfer has more than 'quick_abort_max' KB remaining,
#    it will abort the retrieval.
#
#    If more than 'quick_abort_pct' of the transfer has completed,
#    it will finish the retrieval.
#
#    If you do not want any retrieval to continue after the client
#    has aborted, set both 'quick_abort_min' and 'quick_abort_max'
#    to '0 KB'.
#
#    If you want retrievals to always continue if they are being
#    cached set 'quick_abort_min' to '-1 KB'.
#
#Default:
# quick_abort_min 16 KB
# quick_abort_max 16 KB
# quick_abort_pct 95

#  TAG: read_ahead_gap    buffer-size
#    The amount of data the cache will buffer ahead of what has been
#    sent to the client when retrieving an object from another server.
#
#Default:
# read_ahead_gap 16 KB

#  TAG: negative_ttl    time-units
#    Time-to-Live (TTL) for failed requests.  Certain types of
#    failures (such as "connection refused" and "404 Not Found") are
#    negatively-cached for a configurable amount of time.  The
#    default is 5 minutes.  Note that this is different from
#    negative caching of DNS lookups.
#
#Default:
# negative_ttl 5 minutes

#  TAG: positive_dns_ttl    time-units
#    Upper limit on how long Squid will cache positive DNS responses.
#    Default is 6 hours (360 minutes). This directive must be set
#    larger than negative_dns_ttl.
#
#Default:
# positive_dns_ttl 6 hours

#  TAG: negative_dns_ttl    time-units
#    Time-to-Live (TTL) for negative caching of failed DNS lookups.
#    This also sets the lower cache limit on positive lookups.
#    Minimum value is 1 second, and it is not recommendable to go
#    much below 10 seconds.
#
#Default:
# negative_dns_ttl 1 minute

#  TAG: range_offset_limit    (bytes)
#    Sets a upper limit on how far into the the file a Range request
#    may be to cause Squid to prefetch the whole file. If beyond this
#    limit Squid forwards the Range request as it is and the result
#    is NOT cached.
#
#    This is to stop a far ahead range request (lets say start at 17MB)
#    from making Squid fetch the whole object up to that point before
#    sending anything to the client.
#
#    A value of -1 causes Squid to always fetch the object from the
#    beginning so it may cache the result. (2.0 style)
#
#    A value of 0 causes Squid to never fetch more than the
#    client requested. (default)
#
#Default:
# range_offset_limit 0 KB

#  TAG: minimum_expiry_time    (seconds)
#    The minimum caching time according to (Expires - Date)
#    Headers Squid honors if the object can't be revalidated
#    defaults to 60 seconds. In reverse proxy enorinments it
#    might be desirable to honor shorter object lifetimes. It
#    is most likely better to make your server return a
#    meaningful Last-Modified header however.
#
#Default:
# minimum_expiry_time 60 seconds

#  TAG: store_avg_object_size    (kbytes)
#    Average object size, used to estimate number of objects your
#    cache can hold.  The default is 13 KB.
#
#Default:
# store_avg_object_size 13 KB

#  TAG: store_objects_per_bucket
#    Target number of objects per bucket in the store hash table.
#    Lowering this value increases the total number of buckets and
#    also the storage maintenance rate.  The default is 20.
#
#Default:
# store_objects_per_bucket 20


# HTTP OPTIONS
# -----------------------------------------------------------------------------

#  TAG: request_header_max_size    (KB)
#    This specifies the maximum size for HTTP headers in a request.
#    Request headers are usually relatively small (about 512 bytes).
#    Placing a limit on the request header size will catch certain
#    bugs (for example with persistent connections) and possibly
#    buffer-overflow or denial-of-service attacks.
#
#Default:
# request_header_max_size 20 KB

#  TAG: reply_header_max_size    (KB)
#    This specifies the maximum size for HTTP headers in a reply.
#    Reply headers are usually relatively small (about 512 bytes).
#    Placing a limit on the reply header size will catch certain
#    bugs (for example with persistent connections) and possibly
#    buffer-overflow or denial-of-service attacks.
#
#Default:
# reply_header_max_size 20 KB

#  TAG: request_body_max_size    (KB)
#    This specifies the maximum size for an HTTP request body.
#    In other words, the maximum size of a PUT/POST request.
#    A user who attempts to send a request with a body larger
#    than this limit receives an "Invalid Request" error message.
#    If you set this parameter to a zero (the default), there will
#    be no limit imposed.
#
#Default:
# request_body_max_size 0 KB

#  TAG: broken_posts
#    A list of ACL elements which, if matched, causes Squid to send
#    an extra CRLF pair after the body of a PUT/POST request.
#
#    Some HTTP servers has broken implementations of PUT/POST,
#    and rely on an extra CRLF pair sent by some WWW clients.
#
#    Quote from RFC2616 section 4.1 on this matter:
#
#      Note: certain buggy HTTP/1.0 client implementations generate an
#      extra CRLF's after a POST request. To restate what is explicitly
#      forbidden by the BNF, an HTTP/1.1 client must not preface or follow
#      a request with an extra CRLF.
#
#Example:
# acl buggy_server url_regex ^http://....
# broken_posts allow buggy_server
#
#Default:
# none

#  TAG: upgrade_http0.9
#    This access list controls when HTTP/0.9 responses is upgraded
#    to our current HTTP version. The default is to always upgrade.
#
#    Some applications expect to be able to respond with non-HTTP
#    responses and clients gets confused if the response is upgraded.
#    For example SHOUTcast servers used for mp3 streaming.
#
#    To enable some flexibility in detection of such applications
#    the first line of the response is available in the internal header
#    X-HTTP09-First-Line for use in the rep_header acl.
#
# Don't upgrade ShoutCast responses to HTTP
acl shoutcast rep_header X-HTTP09-First-Line ^ICY.[0-9]
upgrade_http0.9 deny shoutcast

#  TAG: via    on|off
#    If set (default), Squid will include a Via header in requests and
#    replies as required by RFC2616.
#
#Default:
# via on

#  TAG: cache_vary
#    When 'cache_vary' is set to off, response that have a
#    Vary header will not be stored in the cache.
#
#Default:
# cache_vary on

#  TAG: broken_vary_encoding
#    Many servers have broken support for on-the-fly Content-Encoding,
#    returning the same ETag on both plain and gzip:ed variants.
#    Vary replies matching this access list will have the cache split
#    on the Accept-Encoding header of the request and not trusting the
#    ETag to be unique.
#
# Apache mod_gzip and mod_deflate known to be broken so don't trust
# Apache to signal ETag correctly on such responses
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache

#  TAG: collapsed_forwarding    (on|off)
#    This option enables multiple requests for the same URI to be
#    processed as one request. Normally disabled to avoid increased
#    latency on dynamic content, but there can be benefit from enabling
#    this in accelerator setups where the web servers are the bottleneck
#    and reliable and returns mostly cacheable information.
#
#Default:
# collapsed_forwarding off

#  TAG: refresh_stale_hit    (time)
#    This option changes the refresh algorithm to allow concurrent
#    requests while an object is being refreshed to be processed as
#    cache hits if the object expired less than X seconds ago. Default
#    is 0 to disable this feature. This option is mostly interesting
#    in accelerator setups where a few objects is accessed very
#    frequently.
#
#Default:
# refresh_stale_hit 0 seconds

#  TAG: ie_refresh    on|off
#    Microsoft Internet Explorer up until version 5.5 Service
#    Pack 1 has an issue with transparent proxies, wherein it
#    is impossible to force a refresh.  Turning this on provides
#    a partial fix to the problem, by causing all IMS-REFRESH
#    requests from older IE versions to check the origin server
#    for fresh content.  This reduces hit ratio by some amount
#    (~10% in my experience), but allows users to actually get
#    fresh content when they want it.  Note because Squid
#    cannot tell if the user is using 5.5 or 5.5SP1, the behavior
#    of 5.5 is unchanged from old versions of Squid (i.e. a
#    forced refresh is impossible).  Newer versions of IE will,
#    hopefully, continue to have the new behavior and will be
#    handled based on that assumption.  This option defaults to
#    the old Squid behavior, which is better for hit ratios but
#    worse for clients using IE, if they need to be able to
#    force fresh content.
#
#Default:
# ie_refresh off

#  TAG: vary_ignore_expire    on|off
#    Many HTTP servers supporting Vary gives such objects
#    immediate expiry time with no cache-control header
#    when requested by a HTTP/1.0 client. This option
#    enables Squid to ignore such expiry times until
#    HTTP/1.1 is fully implemented.
#    WARNING: This may eventually cause some varying
#    objects not intended for caching to get cached.
#
#Default:
# vary_ignore_expire off

#  TAG: extension_methods
#    Squid only knows about standardized HTTP request methods.
#    You can add up to 20 additional "extension" methods here.
extension_methods REPORT MERGE MKACTIVITY CHECKOUT

#  TAG: request_entities
#    Squid defaults to deny GET and HEAD requests with request entities,
#    as the meaning of such requests are undefined in the HTTP standard
#    even if not explicitly forbidden.
#
#    Set this directive to on if you have clients which insists
#    on sending request entities in GET or HEAD requests. But be warned
#    that there is server software (both proxies and web servers) which
#    can fail to properly process this kind of request which may make you
#    vulnerable to cache pollution attacks if enabled.
#
#Default:
# request_entities off

#  TAG: header_access
#    Usage: header_access header_name allow|deny [!]aclname ...
#
#    WARNING: Doing this VIOLATES the HTTP standard.  Enabling
#    this feature could make you liable for problems which it
#    causes.
#
#    This option replaces the old 'anonymize_headers' and the
#    older 'http_anonymizer' option with something that is much
#    more configurable. This new method creates a list of ACLs
#    for each header, allowing you very fine-tuned header
#    mangling.
#
#    You can only specify known headers for the header name.
#    Other headers are reclassified as 'Other'. You can also
#    refer to all the headers with 'All'.
#
#    For example, to achieve the same behavior as the old
#    'http_anonymizer standard' option, you should use:
#
#        header_access From deny all
#        header_access Referer deny all
#        header_access Server deny all
#        header_access User-Agent deny all
#        header_access WWW-Authenticate deny all
#        header_access Link deny all
#
#    Or, to reproduce the old 'http_anonymizer paranoid' feature
#    you should use:
#
#        header_access Allow allow all
#        header_access Authorization allow all
#        header_access WWW-Authenticate allow all
#        header_access Proxy-Authorization allow all
#        header_access Proxy-Authenticate allow all
#        header_access Cache-Control allow all
#        header_access Content-Encoding allow all
#        header_access Content-Length allow all
#        header_access Content-Type allow all
#        header_access Date allow all
#        header_access Expires allow all
#        header_access Host allow all
#        header_access If-Modified-Since allow all
#        header_access Last-Modified allow all
#        header_access Location allow all
#        header_access Pragma allow all
#        header_access Accept allow all
#        header_access Accept-Charset allow all
#        header_access Accept-Encoding allow all
#        header_access Accept-Language allow all
#        header_access Content-Language allow all
#        header_access Mime-Version allow all
#        header_access Retry-After allow all
#        header_access Title allow all
#        header_access Connection allow all
#        header_access Proxy-Connection allow all
#        header_access All deny all
#
#    By default, all headers are allowed (no anonymizing is
#    performed).
#
#Default:
# none

#  TAG: header_replace
#    Usage:   header_replace header_name message
#    Example: header_replace User-Agent Nutscrape/1.0 (CP/M; 8-bit)
#
#    This option allows you to change the contents of headers
#    denied with header_access above, by replacing them with
#    some fixed string. This replaces the old fake_user_agent
#    option.
#
#    By default, headers are removed if denied.
#
#Default:
# none

#  TAG: relaxed_header_parser    on|off|warn
#    In the default "on" setting Squid accepts certain forms
#    of non-compliant HTTP messages where it is unambiguous
#    what the sending application intended even if the message
#    is not correctly formatted. The messages is then normalized
#    to the correct form when forwarded by Squid.
#
#    If set to "warn" then a warning will be emitted in cache.log
#    each time such HTTP error is encountered.
#
#    If set to "off" then such HTTP errors will cause the request
#    or response to be rejected.
#
#Default:
# relaxed_header_parser on

#  TAG: server_http11    on|off
#    This option enables the use ot HTTP/1.1 on outgoing "direct" requests.
#    See also the http11 cache_peer option.
#    Note: The HTTP/1.1 support is still incomplete, with an
#    internal HTTP/1.0 hop. As result 1xx responses will not
#    be forwarded.
#
#Default:
# server_http11 off

#  TAG: ignore_expect_100    on|off
#    This option makes Squid ignore any Expect: 100-continue header present
#    in the request.
#    Note: Enabling this is a HTTP protocol violation, but some client may
#    not handle it well..
#
#Default:
# ignore_expect_100 off

#  TAG: external_refresh_check
#    This option defines an external helper for determining whether to
#    refresh a stale response. It will be called when Squid receives a
#    request for a cached response that is stale; the helper can either
#    confirm that the response is stale with a STALE response, or
#    extend the freshness of the response (thereby avoiding a refresh
#    check) with a FRESH response, along with a freshness=nnn keyword.
#
#      external_refresh_check [options] FORMAT.. /path/to/helper [helper_args]
#
#    If present, helper_args will be passed to the helper on the command
#    line verbatim.
#
#    Options:
#
#      children=n    Number of processes to spawn to service external
#            refresh checks (default 5).
#      concurrency=n    Concurrency level per process. Only used with
#            helpers capable of processing more than one query
#            at a time.
#
#    When using the concurrency option, the protocol is changed by introducing
#    a query channel tag infront of the request/response. The query channel
#    tag is a number between 0 and concurrency-1.
#
#    FORMAT specifications:
#
#      %CACHE_URI    The URI of the cached response
#      %RES{Header}    HTTP response header value
#      %AGE        The age of the cached response
#
#    The request sent to the helper consists of the data in the format
#    specification in the order specified.
#
#    The helper receives lines per the above format specification, and
#    returns lines starting with OK or ERR indicating the validity of
#    the request and optionally followed by additional keywords with
#    more details.  URL escaping is used to protect each value in both
#    requests and responses.
#
#    General result syntax:
#
#      FRESH / STALE keyword=value ...
#
#    Defined keywords:
#
#      freshness=nnn    The number of seconds to extend the freshness of
#            the response by.
#      log=string    String to be logged in access.log. Available as
#            %ef in logformat specifications.
#      res{Header}=value
#            Value to update response headers with. If already
#            present, the supplied value completely replaces
#            the cached value.
#
#    In the event of a helper-related error (e.g., overload), Squid
#    will always default to STALE.
#
#Default:
# none


# TIMEOUTS
# -----------------------------------------------------------------------------

#  TAG: forward_timeout    time-units
#    This parameter specifies how long Squid should at most attempt in
#    finding a forwarding path for the request before giving up.
#
#Default:
# forward_timeout 4 minutes

#  TAG: connect_timeout    time-units
#    This parameter specifies how long to wait for the TCP connect to
#    the requested server or peer to complete before Squid should
#    attempt to find another path where to forward the request.
#
#Default:
# connect_timeout 1 minute

#  TAG: peer_connect_timeout    time-units
#    This parameter specifies how long to wait for a pending TCP
#    connection to a peer cache.  The default is 30 seconds.   You
#    may also set different timeout values for individual neighbors
#    with the 'connect-timeout' option on a 'cache_peer' line.
#
#Default:
# peer_connect_timeout 30 seconds

#  TAG: read_timeout    time-units
#    The read_timeout is applied on server-side connections.  After
#    each successful read(), the timeout will be extended by this
#    amount.  If no data is read again after this amount of time,
#    the request is aborted and logged with ERR_READ_TIMEOUT.  The
#    default is 15 minutes.
#
#Default:
# read_timeout 15 minutes

#  TAG: request_timeout
#    How long to wait for an HTTP request after initial
#    connection establishment.
#
#Default:
# request_timeout 5 minutes

#  TAG: persistent_request_timeout
#    How long to wait for the next HTTP request on a persistent
#    connection after the previous request completes.
#
#Default:
# persistent_request_timeout 2 minutes

#  TAG: client_lifetime    time-units
#    The maximum amount of time a client (browser) is allowed to
#    remain connected to the cache process.  This protects the Cache
#    from having a lot of sockets (and hence file descriptors) tied up
#    in a CLOSE_WAIT state from remote clients that go away without
#    properly shutting down (either because of a network failure or
#    because of a poor client implementation).  The default is one
#    day, 1440 minutes.
#
#    NOTE:  The default value is intended to be much larger than any
#    client would ever need to be connected to your cache.  You
#    should probably change client_lifetime only as a last resort.
#    If you seem to have many client connections tying up
#    filedescriptors, we recommend first tuning the read_timeout,
#    request_timeout, persistent_request_timeout and quick_abort values.
#
#Default:
# client_lifetime 1 day

#  TAG: half_closed_clients
#    Some clients may shutdown the sending side of their TCP
#    connections, while leaving their receiving sides open.    Sometimes,
#    Squid can not tell the difference between a half-closed and a
#    fully-closed TCP connection.  By default, half-closed client
#    connections are kept open until a read(2) or write(2) on the
#    socket returns an error.  Change this option to 'off' and Squid
#    will immediately close client connections when read(2) returns
#    "no more data to read."
#
#Default:
# half_closed_clients on

#  TAG: pconn_timeout
#    Timeout for idle persistent connections to servers and other
#    proxies.
#
#Default:
# pconn_timeout 1 minute

#  TAG: ident_timeout
#    Maximum time to wait for IDENT lookups to complete.
#
#    If this is too high, and you enabled IDENT lookups from untrusted
#    users, you might be susceptible to denial-of-service by having
#    many ident requests going at once.
#
#Default:
# ident_timeout 10 seconds

#  TAG: shutdown_lifetime    time-units
#    When SIGTERM or SIGHUP is received, the cache is put into
#    "shutdown pending" mode until all active sockets are closed.
#    This value is the lifetime to set for all open descriptors
#    during shutdown mode.  Any active clients after this many
#    seconds will receive a 'timeout' message.
#
#Default:
# shutdown_lifetime 30 seconds


# ADMINISTRATIVE PARAMETERS
# -----------------------------------------------------------------------------

#  TAG: cache_mgr
#    Email-address of local cache manager who will receive
#    mail if the cache dies. The default is "webmaster".
#
#Default:
# cache_mgr webmaster
cache_mgr kevin@mydoctorcomputer.com
#  TAG: mail_from
#    From: email-address for mail sent when the cache dies.
#    The default is to use 'appname@unique_hostname'.
#    Default appname value is "squid", can be changed into
#    src/globals.h before building squid.
#
#Default:
# none

#  TAG: mail_program
#    Email program used to send mail if the cache dies.
#    The default is "mail". The specified program must comply
#    with the standard Unix mail syntax:
#      mail-program recipient < mailfile
#
#    Optional command line options can be specified.
#
#Default:
# mail_program mail

#  TAG: cache_effective_user
#    If you start Squid as root, it will change its effective/real
#    UID/GID to the user specified below.  The default is to change
#    to UID to proxy.  If you define cache_effective_user, but not
#    cache_effective_group, Squid sets the GID to the effective
#    user's default group ID (taken from the password file) and
#    supplementary group list from the from groups membership of
#    cache_effective_user.
#
#Default:
# cache_effective_user proxy

#  TAG: cache_effective_group
#    If you want Squid to run with a specific GID regardless of
#    the group memberships of the effective user then set this
#    to the group (or GID) you want Squid to run as. When set
#    all other group privileges of the effective user is ignored
#    and only this GID is effective. If Squid is not started as
#    root the user starting Squid must be member of the specified
#    group.
#
#Default:
# none

#  TAG: httpd_suppress_version_string    on|off
#    Suppress Squid version string info in HTTP headers and HTML error pages.
#
#Default:
# httpd_suppress_version_string off

#  TAG: visible_hostname
#    If you want to present a special hostname in error messages, etc,
#    define this.  Otherwise, the return value of gethostname()
#    will be used. If you have multiple caches in a cluster and
#    get errors about IP-forwarding you must set them to have individual
#    names with this setting.
#
#Default:
# none
visible_hostname proxy.sd150.org
#  TAG: unique_hostname
#    If you want to have multiple machines with the same
#    'visible_hostname' you must give each machine a different
#    'unique_hostname' so forwarding loops can be detected.
#
#Default:
# none

#  TAG: hostname_aliases
#    A list of other DNS names your cache has.
#
#Default:
# none

#  TAG: umask
#    Minimum umask which should be enforced while the proxy
#    is running, in addition to the umask set at startup.
#
#    Note: Should start with a 0 to indicate the normal octal
#    representation of umasks
#
#Default:
# umask 027


# OPTIONS FOR THE CACHE REGISTRATION SERVICE
# -----------------------------------------------------------------------------
#
#    This section contains parameters for the (optional) cache
#    announcement service.  This service is provided to help
#    cache administrators locate one another in order to join or
#    create cache hierarchies.
#
#    An 'announcement' message is sent (via UDP) to the registration
#    service by Squid.  By default, the announcement message is NOT
#    SENT unless you enable it with 'announce_period' below.
#
#    The announcement message includes your hostname, plus the
#    following information from this configuration file:
#
#        http_port
#        icp_port
#        cache_mgr
#
#    All current information is processed regularly and made
#    available on the Web at http://www.ircache.net/Cache/Tracker/.

#  TAG: announce_period
#    This is how frequently to send cache announcements.  The
#    default is `0' which disables sending the announcement
#    messages.
#
#    To enable announcing your cache, just uncomment the line
#    below.
#
#Default:
# announce_period 0
#
#To enable announcing your cache, just uncomment the line below.
#announce_period 1 day

#  TAG: announce_host
#  TAG: announce_file
#  TAG: announce_port
#    announce_host and announce_port set the hostname and port
#    number where the registration message will be sent.
#
#    Hostname will default to 'tracker.ircache.net' and port will
#    default default to 3131.  If the 'filename' argument is given,
#    the contents of that file will be included in the announce
#    message.
#
#Default:
# announce_host tracker.ircache.net
# announce_port 3131


# HTTPD-ACCELERATOR OPTIONS
# -----------------------------------------------------------------------------

#  TAG: httpd_accel_no_pmtu_disc    on|off
#    In many setups of transparently intercepting proxies Path-MTU
#    discovery can not work on traffic towards the clients. This is
#    the case when the intercepting device does not fully track
#    connections and fails to forward ICMP must fragment messages
#    to the cache server.
#
#    If you have such setup and experience that certain clients
#    sporadically hang or never complete requests set this to on.
#
#Default:
# httpd_accel_no_pmtu_disc off


# DELAY POOL PARAMETERS
# -----------------------------------------------------------------------------

#  TAG: delay_pools
#    This represents the number of delay pools to be used.  For example,
#    if you have one class 2 delay pool and one class 3 delays pool, you
#    have a total of 2 delay pools.
#
#Default:
# delay_pools 0

#  TAG: delay_class
#    This defines the class of each delay pool.  There must be exactly one
#    delay_class line for each delay pool.  For example, to define two
#    delay pools, one of class 2 and one of class 3, the settings above
#    and here would be:
#
#Example:
# delay_pools 2      # 2 delay pools
# delay_class 1 2    # pool 1 is a class 2 pool
# delay_class 2 3    # pool 2 is a class 3 pool
#
#    The delay pool classes are:
#
#        class 1        Everything is limited by a single aggregate
#                bucket.
#
#        class 2     Everything is limited by a single aggregate
#                bucket as well as an "individual" bucket chosen
#                from bits 25 through 32 of the IP address.
#
#        class 3        Everything is limited by a single aggregate
#                bucket as well as a "network" bucket chosen
#                from bits 17 through 24 of the IP address and a
#                "individual" bucket chosen from bits 17 through
#                32 of the IP address.
#
#    NOTE: If an IP address is a.b.c.d
#        -> bits 25 through 32 are "d"
#        -> bits 17 through 24 are "c"
#        -> bits 17 through 32 are "c * 256 + d"
#
#Default:
# none

#  TAG: delay_access
#    This is used to determine which delay pool a request falls into.
#
#    delay_access is sorted per pool and the matching starts with pool 1,
#    then pool 2, ..., and finally pool N. The first delay pool where the
#    request is allowed is selected for the request. If it does not allow
#    the request to any pool then the request is not delayed (default).
#
#    For example, if you want some_big_clients in delay
#    pool 1 and lotsa_little_clients in delay pool 2:
#
#Example:
# delay_access 1 allow some_big_clients
# delay_access 1 deny all
# delay_access 2 allow lotsa_little_clients
# delay_access 2 deny all
#
#Default:
# none

#  TAG: delay_parameters
#    This defines the parameters for a delay pool.  Each delay pool has
#    a number of "buckets" associated with it, as explained in the
#    description of delay_class.  For a class 1 delay pool, the syntax is:
#
#delay_parameters pool aggregate
#
#    For a class 2 delay pool:
#
#delay_parameters pool aggregate individual
#
#    For a class 3 delay pool:
#
#delay_parameters pool aggregate network individual
#
#    The variables here are:
#
#        pool        a pool number - ie, a number between 1 and the
#                number specified in delay_pools as used in
#                delay_class lines.
#
#        aggregate    the "delay parameters" for the aggregate bucket
#                (class 1, 2, 3).
#
#        individual    the "delay parameters" for the individual
#                buckets (class 2, 3).
#
#        network        the "delay parameters" for the network buckets
#                (class 3).
#
#    A pair of delay parameters is written restore/maximum, where restore is
#    the number of bytes (not bits - modem and network speeds are usually
#    quoted in bits) per second placed into the bucket, and maximum is the
#    maximum number of bytes which can be in the bucket at any time.
#
#    For example, if delay pool number 1 is a class 2 delay pool as in the
#    above example, and is being used to strictly limit each host to 64kbps
#    (plus overheads), with no overall limit, the line is:
#
#delay_parameters 1 -1/-1 8000/8000
#
#    Note that the figure -1 is used to represent "unlimited".
#
#    And, if delay pool number 2 is a class 3 delay pool as in the above
#    example, and you want to limit it to a total of 256kbps (strict limit)
#    with each 8-bit network permitted 64kbps (strict limit) and each
#    individual host permitted 4800bps with a bucket maximum size of 64kb
#    to permit a decent web page to be downloaded at a decent speed
#    (if the network is not being limited due to overuse) but slow down
#    large downloads more significantly:
#
#delay_parameters 2 32000/32000 8000/8000 600/8000
#
#    There must be one delay_parameters line for each delay pool.
#
#Default:
# none

#  TAG: delay_initial_bucket_level    (percent, 0-100)
#    The initial bucket percentage is used to determine how much is put
#    in each bucket when squid starts, is reconfigured, or first notices
#    a host accessing it (in class 2 and class 3, individual hosts and
#    networks only have buckets associated with them once they have been
#    "seen" by squid).
#
#Default:
# delay_initial_bucket_level 50


# WCCPv1 AND WCCPv2 CONFIGURATION OPTIONS
# -----------------------------------------------------------------------------

#  TAG: wccp_router
#  TAG: wccp2_router
#    Use this option to define your WCCP ``home'' router for
#    Squid.
#
#    wccp_router supports a single WCCP(v1) router
#
#    wccp2_router supports multiple WCCPv2 routers
#
#    only one of the two may be used at the same time and defines
#    which version of WCCP to use.
#
#Default:
# wccp_router 0.0.0.0

#  TAG: wccp_version
#    This directive is only relevant if you need to set up WCCP(v1)
#    to some very old and end-of-life Cisco routers. In all other
#    setups it must be left unset or at the default setting.
#    It defines an internal version in the WCCP(v1) protocol,
#    with version 4 being the officially documented protocol.
#
#    According to some users, Cisco IOS 11.2 and earlier only
#    support WCCP version 3.  If you're using that or an earlier
#    version of IOS, you may need to change this value to 3, otherwise
#    do not specify this parameter.
#
#Default:
# wccp_version 4

#  TAG: wccp2_rebuild_wait
#    If this is enabled Squid will wait for the cache dir rebuild to finish
#    before sending the first wccp2 HereIAm packet
#
#Default:
# wccp2_rebuild_wait on

#  TAG: wccp2_forwarding_method
#    WCCP2 allows the setting of forwarding methods between the
#    router/switch and the cache.  Valid values are as follows:
#
#    1 - GRE encapsulation (forward the packet in a GRE/WCCP tunnel)
#    2 - L2 redirect (forward the packet using Layer 2/MAC rewriting)
#
#    Currently (as of IOS 12.4) cisco routers only support GRE.
#    Cisco switches only support the L2 redirect assignment method.
#
#Default:
# wccp2_forwarding_method 1

#  TAG: wccp2_return_method
#    WCCP2 allows the setting of return methods between the
#    router/switch and the cache for packets that the cache
#    decides not to handle.  Valid values are as follows:
#
#    1 - GRE encapsulation (forward the packet in a GRE/WCCP tunnel)
#    2 - L2 redirect (forward the packet using Layer 2/MAC rewriting)
#
#    Currently (as of IOS 12.4) cisco routers only support GRE.
#    Cisco switches only support the L2 redirect assignment.
#
#    If the "ip wccp redirect exclude in" command has been
#    enabled on the cache interface, then it is still safe for
#    the proxy server to use a l2 redirect method even if this
#    option is set to GRE.
#
#Default:
# wccp2_return_method 1

#  TAG: wccp2_assignment_method
#    WCCP2 allows the setting of methods to assign the WCCP hash
#    Valid values are as follows:
#
#    1 - Hash assignment
#    2 - Mask assignment
#
#    As a general rule, cisco routers support the hash assignment method
#    and cisco switches support the mask assignment method.
#
#Default:
# wccp2_assignment_method 1

#  TAG: wccp2_service
#    WCCP2 allows for multiple traffic services. There are two
#    types: "standard" and "dynamic". The standard type defines
#    one service id - http (id 0). The dynamic service ids can be from
#    51 to 255 inclusive.  In order to use a dynamic service id
#    one must define the type of traffic to be redirected; this is done
#    using the wccp2_service_info option.
#
#    The "standard" type does not require a wccp2_service_info option,
#    just specifying the service id will suffice.
#
#    MD5 service authentication can be enabled by adding
#    "password=<password>" to the end of this service declaration.
#
#    Examples:
#
#    wccp2_service standard 0    # for the 'web-cache' standard service
#    wccp2_service dynamic 80    # a dynamic service type which will be
#                    # fleshed out with subsequent options.
#    wccp2_service standard 0 password=foo
#
#
#Default:
# wccp2_service standard 0

#  TAG: wccp2_service_info
#    Dynamic WCCPv2 services require further information to define the
#    traffic you wish to have diverted.
#
#    The format is:
#
#    wccp2_service_info <id> protocol=<protocol> flags=<flag>,<flag>..
#        priority=<priority> ports=<port>,<port>..
#
#    The relevant WCCPv2 flags:
#    + src_ip_hash, dst_ip_hash
#    + source_port_hash, dst_port_hash
#    + src_ip_alt_hash, dst_ip_alt_hash
#    + src_port_alt_hash, dst_port_alt_hash
#    + ports_source
#
#    The port list can be one to eight entries.
#
#    Example:
#
#    wccp2_service_info 80 protocol=tcp flags=src_ip_hash,ports_source
#        priority=240 ports=80
#
#    Note: the service id must have been defined by a previous
#    'wccp2_service dynamic <id>' entry.
#
#Default:
# none

#  TAG: wccp2_weight
#    Each cache server gets assigned a set of the destination
#    hash proportional to their weight.
#
#Default:
# wccp2_weight 10000

#  TAG: wccp_address
#  TAG: wccp2_address
#    Use this option if you require WCCP to use a specific
#    interface address.
#
#    The default behavior is to not bind to any specific address.
#
#Default:
# wccp_address 0.0.0.0
# wccp2_address 0.0.0.0


# PERSISTENT CONNECTION HANDLING
# -----------------------------------------------------------------------------
#
# Also see "pconn_timeout" in the TIMEOUTS section

#  TAG: client_persistent_connections
#  TAG: server_persistent_connections
#    Persistent connection support for clients and servers.  By
#    default, Squid uses persistent connections (when allowed)
#    with its clients and servers.  You can use these options to
#    disable persistent connections with clients and/or servers.
#
#Default:
# client_persistent_connections on
# server_persistent_connections on

#  TAG: persistent_connection_after_error
#    With this directive the use of persistent connections after
#    HTTP errors can be disabled. Useful if you have clients
#    who fail to handle errors on persistent connections proper.
#
#Default:
# persistent_connection_after_error off

#  TAG: detect_broken_pconn
#    Some servers have been found to incorrectly signal the use
#    of HTTP/1.0 persistent connections even on replies not
#    compatible, causing significant delays. This server problem
#    has mostly been seen on redirects.
#
#    By enabling this directive Squid attempts to detect such
#    broken replies and automatically assume the reply is finished
#    after 10 seconds timeout.
#
#Default:
# detect_broken_pconn off


# CACHE DIGEST OPTIONS
# -----------------------------------------------------------------------------

#  TAG: digest_generation
#    This controls whether the server will generate a Cache Digest
#    of its contents.
#
#Default:
# digest_generation on

#  TAG: digest_bits_per_entry
#    This is the number of bits of the server's Cache Digest which
#    will be associated with the Digest entry for a given HTTP
#    Method and URL (public key) combination.  The default is 5.
#
#Default:
# digest_bits_per_entry 5

#  TAG: digest_rebuild_period    (seconds)
#    This is the wait time between Cache Digest rebuilds.
#
#Default:
# digest_rebuild_period 1 hour

#  TAG: digest_rewrite_period    (seconds)
#    This is the wait time between Cache Digest writes to disk.
#
#Default:
# digest_rewrite_period 1 hour

#  TAG: digest_swapout_chunk_size    (bytes)
#    This is the number of bytes of the Cache Digest to write to
#    disk at a time.  It defaults to 4096 bytes (4KB), the Squid
#    default swap page.
#
#Default:
# digest_swapout_chunk_size 4096 bytes

#  TAG: digest_rebuild_chunk_percentage    (percent, 0-100)
#    This is the percentage of the Cache Digest to be scanned at a
#    time.  By default it is set to 10% of the Cache Digest.
#
#Default:
# digest_rebuild_chunk_percentage 10


# SNMP OPTIONS
# -----------------------------------------------------------------------------

#  TAG: snmp_port
#    Squid can now serve statistics and status information via SNMP.
#    By default it listens to port 3401 on the machine. If you don't
#    wish to use SNMP, set this to "0".
#
#    Note: on Debian/Linux, the default is zero - you need to
#    set it to 3401 to enable it.
#
#Default:
# snmp_port 0
snmp_port 3401
#  TAG: snmp_access
#    Allowing or denying access to the SNMP port.
#
#    All access to the agent is denied by default.
#    usage:
#
#    snmp_access allow|deny [!]aclname ...
#
#Example:
# snmp_access allow snmppublic localhost
# snmp_access deny all
#
#Default:
# snmp_access deny all

#  TAG: snmp_incoming_address
#  TAG: snmp_outgoing_address
#    Just like 'udp_incoming_address' above, but for the SNMP port.
#
#    snmp_incoming_address    is used for the SNMP socket receiving
#                messages from SNMP agents.
#    snmp_outgoing_address    is used for SNMP packets returned to SNMP
#                agents.
#
#    The default snmp_incoming_address (0.0.0.0) is to listen on all
#    available network interfaces.
#
#    If snmp_outgoing_address is set to 255.255.255.255 (the default)
#    it will use the same socket as snmp_incoming_address. Only
#    change this if you want to have SNMP replies sent using another
#    address than where this Squid listens for SNMP queries.
#
#    NOTE, snmp_incoming_address and snmp_outgoing_address can not have
#    the same value since they both use port 3401.
#
#Default:
# snmp_incoming_address 0.0.0.0
# snmp_outgoing_address 255.255.255.255


# ICP OPTIONS
# -----------------------------------------------------------------------------

#  TAG: icp_port
#    The port number where Squid sends and receives ICP queries to
#    and from neighbor caches.  Default is 3130.  To disable use
#    "0".  May be overridden with -u on the command line.
#
#Default:
# icp_port 3130

#  TAG: htcp_port
#    The port number where Squid sends and receives HTCP queries to
#    and from neighbor caches.  To turn it on you want to set it 4827.
#    By default it is set to "0" (disabled).
#
#Default:
# htcp_port 0

#  TAG: log_icp_queries    on|off
#    If set, ICP queries are logged to access.log. You may wish
#    do disable this if your ICP load is VERY high to speed things
#    up or to simplify log analysis.
#
#Default:
# log_icp_queries on

#  TAG: udp_incoming_address
#    udp_incoming_address    is used for UDP packets received from other
#                caches.
#
#    The default behavior is to not bind to any specific address.
#
#    Only change this if you want to have all UDP queries received on
#    a specific interface/address.
#
#    NOTE: udp_incoming_address is used by the ICP, HTCP, and DNS
#    modules. Altering it will affect all of them in the same manner.
#
#    see also; udp_outgoing_address
#
#    NOTE, udp_incoming_address and udp_outgoing_address can not
#    have the same value since they both use the same port.
#
#Default:
# udp_incoming_address 0.0.0.0

#  TAG: udp_outgoing_address
#    udp_outgoing_address    is used for UDP packets sent out to other
#                caches.
#
#    The default behavior is to not bind to any specific address.
#
#    Instead it will use the same socket as udp_incoming_address.
#    Only change this if you want to have UDP queries sent using another
#    address than where this Squid listens for UDP queries from other
#    caches.
#
#    NOTE: udp_outgoing_address is used by the ICP, HTCP, and DNS
#    modules. Altering it will affect all of them in the same manner.
#
#    see also; udp_incoming_address
#
#    NOTE, udp_incoming_address and udp_outgoing_address can not
#    have the same value since they both use the same port.
#
#Default:
# udp_outgoing_address 255.255.255.255

#  TAG: icp_hit_stale    on|off
#    If you want to return ICP_HIT for stale cache objects, set this
#    option to 'on'.  If you have sibling relationships with caches
#    in other administrative domains, this should be 'off'.  If you only
#    have sibling relationships with caches under your control,
#    it is probably okay to set this to 'on'.
#    If set to 'on', your siblings should use the option "allow-miss"
#    on their cache_peer lines for connecting to you.
#
#Default:
# icp_hit_stale off

#  TAG: minimum_direct_hops
#    If using the ICMP pinging stuff, do direct fetches for sites
#    which are no more than this many hops away.
#
#Default:
# minimum_direct_hops 4

#  TAG: minimum_direct_rtt
#    If using the ICMP pinging stuff, do direct fetches for sites
#    which are no more than this many rtt milliseconds away.
#
#Default:
# minimum_direct_rtt 400

#  TAG: netdb_low
#  TAG: netdb_high
#    The low and high water marks for the ICMP measurement
#    database.  These are counts, not percents.  The defaults are
#    900 and 1000.  When the high water mark is reached, database
#    entries will be deleted until the low mark is reached.
#
#Default:
# netdb_low 900
# netdb_high 1000

#  TAG: netdb_ping_period
#    The minimum period for measuring a site.  There will be at
#    least this much delay between successive pings to the same
#    network.  The default is five minutes.
#
#Default:
# netdb_ping_period 5 minutes

#  TAG: query_icmp    on|off
#    If you want to ask your peers to include ICMP data in their ICP
#    replies, enable this option.
#
#    If your peer has configured Squid (during compilation) with
#    '--enable-icmp' that peer will send ICMP pings to origin server
#    sites of the URLs it receives.  If you enable this option the
#    ICP replies from that peer will include the ICMP data (if available).
#    Then, when choosing a parent cache, Squid will choose the parent with
#    the minimal RTT to the origin server.  When this happens, the
#    hierarchy field of the access.log will be
#    "CLOSEST_PARENT_MISS".  This option is off by default.
#
#Default:
# query_icmp off

#  TAG: test_reachability    on|off
#    When this is 'on', ICP MISS replies will be ICP_MISS_NOFETCH
#    instead of ICP_MISS if the target host is NOT in the ICMP
#    database, or has a zero RTT.
#
#Default:
# test_reachability off

#  TAG: icp_query_timeout    (msec)
#    Normally Squid will automatically determine an optimal ICP
#    query timeout value based on the round-trip-time of recent ICP
#    queries.  If you want to override the value determined by
#    Squid, set this 'icp_query_timeout' to a non-zero value.  This
#    value is specified in MILLISECONDS, so, to use a 2-second
#    timeout (the old default), you would write:
#
#        icp_query_timeout 2000
#
#Default:
# icp_query_timeout 0

#  TAG: maximum_icp_query_timeout    (msec)
#    Normally the ICP query timeout is determined dynamically.  But
#    sometimes it can lead to very large values (say 5 seconds).
#    Use this option to put an upper limit on the dynamic timeout
#    value.  Do NOT use this option to always use a fixed (instead
#    of a dynamic) timeout value. To set a fixed timeout see the
#    'icp_query_timeout' directive.
#
#Default:
# maximum_icp_query_timeout 2000

#  TAG: minimum_icp_query_timeout    (msec)
#    Normally the ICP query timeout is determined dynamically.  But
#    sometimes it can lead to very small timeouts, even lower than
#    the normal latency variance on your link due to traffic.
#    Use this option to put an lower limit on the dynamic timeout
#    value.  Do NOT use this option to always use a fixed (instead
#    of a dynamic) timeout value. To set a fixed timeout see the
#    'icp_query_timeout' directive.
#
#Default:
# minimum_icp_query_timeout 5


# MULTICAST ICP OPTIONS
# -----------------------------------------------------------------------------

#  TAG: mcast_groups
#    This tag specifies a list of multicast groups which your server
#    should join to receive multicasted ICP queries.
#
#    NOTE!  Be very careful what you put here!  Be sure you
#    understand the difference between an ICP _query_ and an ICP
#    _reply_.  This option is to be set only if you want to RECEIVE
#    multicast queries.  Do NOT set this option to SEND multicast
#    ICP (use cache_peer for that).  ICP replies are always sent via
#    unicast, so this option does not affect whether or not you will
#    receive replies from multicast group members.
#
#    You must be very careful to NOT use a multicast address which
#    is already in use by another group of caches.
#
#    If you are unsure about multicast, please read the Multicast
#    chapter in the Squid FAQ (http://www.squid-cache.org/FAQ/).
#
#    Usage: mcast_groups 239.128.16.128 224.0.1.20
#
#    By default, Squid doesn't listen on any multicast groups.
#
#Default:
# none

#  TAG: mcast_miss_addr
# Note: This option is only available if Squid is rebuilt with the
#       --enable-multicast-miss option
#
#    If you enable this option, every "cache miss" URL will
#    be sent out on the specified multicast address.
#
#    Do not enable this option unless you are are absolutely
#    certain you understand what you are doing.
#
#Default:
# mcast_miss_addr 255.255.255.255

#  TAG: mcast_miss_ttl
# Note: This option is only available if Squid is rebuilt with the
#       --enable-multicast-miss option
#
#    This is the time-to-live value for packets multicasted
#    when multicasting off cache miss URLs is enabled.  By
#    default this is set to 'site scope', i.e. 16.
#
#Default:
# mcast_miss_ttl 16

#  TAG: mcast_miss_port
# Note: This option is only available if Squid is rebuilt with the
#       --enable-multicast-miss option
#
#    This is the port number to be used in conjunction with
#    'mcast_miss_addr'.
#
#Default:
# mcast_miss_port 3135

#  TAG: mcast_miss_encode_key
# Note: This option is only available if Squid is rebuilt with the
#       --enable-multicast-miss option
#
#    The URLs that are sent in the multicast miss stream are
#    encrypted.  This is the encryption key.
#
#Default:
# mcast_miss_encode_key XXXXXXXXXXXXXXXX

#  TAG: mcast_icp_query_timeout    (msec)
#    For multicast peers, Squid regularly sends out ICP "probes" to
#    count how many other peers are listening on the given multicast
#    address.  This value specifies how long Squid should wait to
#    count all the replies.  The default is 2000 msec, or 2
#    seconds.
#
#Default:
# mcast_icp_query_timeout 2000


# INTERNAL ICON OPTIONS
# -----------------------------------------------------------------------------

#  TAG: icon_directory
#    Where the icons are stored. These are normally kept in
#    /usr/share/squid/icons
#
#Default:
# icon_directory /usr/share/squid/icons

#  TAG: global_internal_static
#    This directive controls is Squid should intercept all requests for
#    /squid-internal-static/ no matter which host the URL is requesting
#    (default on setting), or if nothing special should be done for
#    such URLs (off setting). The purpose of this directive is to make
#    icons etc work better in complex cache hierarchies where it may
#    not always be possible for all corners in the cache mesh to reach
#    the server generating a directory listing.
#
#Default:
# global_internal_static on

#  TAG: short_icon_urls
#    If this is enabled Squid will use short URLs for icons.
#
#    If off the URLs for icons will always be absolute URLs
#    including the proxy name and port.
#
#Default:
# short_icon_urls off


# ERROR PAGE OPTIONS
# -----------------------------------------------------------------------------

#  TAG: error_directory
#    If you wish to create your own versions of the default
#    (English) error files, either to customize them to suit your
#    language or company copy the template English files to another
#    directory and point this tag at them.
#
#    The squid developers are interested in making squid available in
#    a wide variety of languages. If you are making translations for a
#    langauge that Squid does not currently provide please consider
#    contributing your translation back to the project.
#
#Default:
# error_directory /usr/share/squid/errors/en

#  TAG: error_map
#    Map errors to custom messages
#
#        error_map message_url http_status ...
#
#    http_status ... is a list of HTTP status codes or Squid error
#    messages.
#
#    Use in accelerators to substitute the error messages returned
#    by servers with other custom errors.
#
#        error_map http://your.server/error/404.shtml 404
#
#    Requests for error messages is a GET request for the configured
#    URL with the following special headers
#
#        X-Error-Status:    The received HTTP status code (i.e. 404)
#        X-Request-URI:    The requested URI where the error occurred
#
#    In Addition the following headers are forwarded from the client
#    request:
#
#        User-Agent, Cookie, X-Forwarded-For, Via, Authorization,
#        Accept, Referer
#
#    And the following headers from the server reply:
#
#        Server, Via, Location, Content-Location
#
#    The reply returned to the client will carry the original HTTP
#    headers from the real error message, but with the reply body
#    of the configured error message.
#
#
#Default:
# none

#  TAG: err_html_text
#    HTML text to include in error messages.  Make this a "mailto"
#    URL to your admin address, or maybe just a link to your
#    organizations Web page.
#
#    To include this in your error messages, you must rewrite
#    the error template files (found in the "errors" directory).
#    Wherever you want the 'err_html_text' line to appear,
#    insert a %L tag in the error template file.
#
#Default:
# none

#  TAG: deny_info
#    Usage:   deny_info err_page_name acl
#    or       deny_info http://... acl
#    Example: deny_info ERR_CUSTOM_ACCESS_DENIED bad_guys
#
#    This can be used to return a ERR_ page for requests which
#    do not pass the 'http_access' rules.  Squid remembers the last
#    acl it evaluated in http_access, and if a 'deny_info' line exists
#    for that ACL Squid returns a corresponding error page.
#
#    The acl is typically the last acl on the http_access deny line which
#    denied access. The exceptions to this rule are:
#    - When Squid needs to request authentication credentials. It's then
#      the first authentication related acl encountered
#    - When none of the http_access lines matches. It's then the last
#      acl processed on the last http_access line.
#
#    You may use ERR_ pages that come with Squid or create your own pages
#    and put them into the configured errors/ directory.
#
#    Alternatively you can specify an error URL. The browsers will
#    get redirected (302) to the specified URL. %s in the redirection
#    URL will be replaced by the requested URL.
#
#    Alternatively you can tell Squid to reset the TCP connection
#    by specifying TCP_RESET.
#
#Default:
# none


# OPTIONS INFLUENCING REQUEST FORWARDING 
# -----------------------------------------------------------------------------

#  TAG: nonhierarchical_direct
#    By default, Squid will send any non-hierarchical requests
#    (matching hierarchy_stoplist or not cacheable request type) direct
#    to origin servers.
#
#    If you set this to off, Squid will prefer to send these
#    requests to parents.
#
#    Note that in most configurations, by turning this off you will only
#    add latency to these request without any improvement in global hit
#    ratio.
#
#    If you are inside an firewall see never_direct instead of
#    this directive.
#
#Default:
# nonhierarchical_direct on

#  TAG: prefer_direct
#    Normally Squid tries to use parents for most requests. If you for some
#    reason like it to first try going direct and only use a parent if
#    going direct fails set this to on.
#
#    By combining nonhierarchical_direct off and prefer_direct on you
#    can set up Squid to use a parent as a backup path if going direct
#    fails.
#
#    Note: If you want Squid to use parents for all requests see
#    the never_direct directive. prefer_direct only modifies how Squid
#    acts on cacheable requests.
#
#Default:
# prefer_direct off

#  TAG: ignore_ims_on_miss    on|off
#    This options makes Squid ignore If-Modified-Since on
#    cache misses. This is useful while the cache is
#    mostly empty to more quickly have the cache populated.
#
#Default:
# ignore_ims_on_miss off

#  TAG: always_direct
#    Usage: always_direct allow|deny [!]aclname ...
#
#    Here you can use ACL elements to specify requests which should
#    ALWAYS be forwarded by Squid to the origin servers without using
#    any peers.  For example, to always directly forward requests for
#    local servers ignoring any parents or siblings you may have use
#    something like:
#
#        acl local-servers dstdomain my.domain.net
#        always_direct allow local-servers
#
#    To always forward FTP requests directly, use
#
#        acl FTP proto FTP
#        always_direct allow FTP
#
#    NOTE: There is a similar, but opposite option named
#    'never_direct'.  You need to be aware that "always_direct deny
#    foo" is NOT the same thing as "never_direct allow foo".  You
#    may need to use a deny rule to exclude a more-specific case of
#    some other rule.  Example:
#
#        acl local-external dstdomain external.foo.net
#        acl local-servers dstdomain  .foo.net
#        always_direct deny local-external
#        always_direct allow local-servers
#
#    NOTE: If your goal is to make the client forward the request
#    directly to the origin server bypassing Squid then this needs
#    to be done in the client configuration. Squid configuration
#    can only tell Squid how Squid should fetch the object.
#
#    NOTE: This directive is not related to caching. The replies
#    is cached as usual even if you use always_direct. To not cache
#    the replies see no_cache.
#
#    This option replaces some v1.1 options such as local_domain
#    and local_ip.
#
#Default:
# none

#  TAG: never_direct
#    Usage: never_direct allow|deny [!]aclname ...
#
#    never_direct is the opposite of always_direct.  Please read
#    the description for always_direct if you have not already.
#
#    With 'never_direct' you can use ACL elements to specify
#    requests which should NEVER be forwarded directly to origin
#    servers.  For example, to force the use of a proxy for all
#    requests, except those in your local domain use something like:
#
#        acl local-servers dstdomain .foo.net
#        acl all src 0.0.0.0/0.0.0.0
#        never_direct deny local-servers
#        never_direct allow all
#
#    or if Squid is inside a firewall and there are local intranet
#    servers inside the firewall use something like:
#
#        acl local-intranet dstdomain .foo.net
#        acl local-external dstdomain external.foo.net
#        always_direct deny local-external
#        always_direct allow local-intranet
#        never_direct allow all
#
#    This option replaces some v1.1 options such as inside_firewall
#    and firewall_ip.
#
#Default:
# none


# ADVANCED NETWORKING OPTIONS
# -----------------------------------------------------------------------------

#  TAG: max_filedescriptors
#    The maximum number of filedescriptors supported.
#
#    The default "0" means Squid inherits the current ulimit setting.
#
#    Note: Changing this requires a restart of Squid. Also
#    not all comm loops supports values larger than --with-maxfd.
#
#Default:
# max_filedescriptors 0

#  TAG: accept_filter
#    FreeBSD:
#
#    The name of an accept(2) filter to install on Squid's
#    listen socket(s).  This feature is perhaps specific to
#    FreeBSD and requires support in the kernel.
#
#    The 'httpready' filter delays delivering new connections
#    to Squid until a full HTTP request has been received.
#    See the accf_http(9) man page for details.
#
#    The 'dataready' filter delays delivering new connections
#    to Squid until there is some data to process.
#    See the accf_dataready(9) man page for details.
#
#    Linux:
#    
#    The 'data' filter delays delivering of new connections
#    to Squid until there is some data to process by TCP_ACCEPT_DEFER.
#    You may optionally specify a number of seconds to wait by
#    'data=N' where N is the number of seconds. Defaults to 30
#    if not specified.  See the tcp(7) man page for details.
#EXAMPLE:
## FreeBSD
#accept_filter httpready
## Linux
#accept_filter data
#
#Default:
# none

#  TAG: tcp_recv_bufsize    (bytes)
#    Size of receive buffer to set for TCP sockets.  Probably just
#    as easy to change your kernel's default.  Set to zero to use
#    the default buffer size.
#
#Default:
# tcp_recv_bufsize 0 bytes

#  TAG: incoming_rate
#    This directive controls how aggressive Squid should accept new
#    connections compared to processing existing connections. 
#    The lower number the more frequent Squid will look for new
#    incoming requests.
#
#Default:
# incoming_rate 30


# DNS OPTIONS
# -----------------------------------------------------------------------------

#  TAG: check_hostnames
#    For security and stability reasons Squid by default checks
#    hostnames for Internet standard RFC compliance. If you do not want
#    Squid to perform these checks then turn this directive off.
#
#Default:
# check_hostnames on

#  TAG: allow_underscore
#    Underscore characters is not strictly allowed in Internet hostnames
#    but nevertheless used by many sites. Set this to off if you want
#    Squid to be strict about the standard.
#    This check is performed only when check_hostnames is set to on.
#
#Default:
# allow_underscore on

#  TAG: cache_dns_program
# Note: This option is only available if Squid is rebuilt with the
#       --disable-internal-dns option
#
#    Specify the location of the executable for dnslookup process.
#
#Default:
# cache_dns_program /usr/lib/squid/dnsserver

#  TAG: dns_children
# Note: This option is only available if Squid is rebuilt with the
#       --disable-internal-dns option
#
#    The number of processes spawn to service DNS name lookups.
#    For heavily loaded caches on large servers, you should
#    probably increase this value to at least 10.  The maximum
#    is 32.  The default is 5.
#
#    You must have at least one dnsserver process.
#
#Default:
# dns_children 5

#  TAG: dns_retransmit_interval
#    Initial retransmit interval for DNS queries. The interval is
#    doubled each time all configured DNS servers have been tried.
#
#
#Default:
# dns_retransmit_interval 5 seconds

#  TAG: dns_timeout
#    DNS Query timeout. If no response is received to a DNS query
#    within this time all DNS servers for the queried domain
#    are assumed to be unavailable.
#
#Default:
# dns_timeout 2 minutes

#  TAG: dns_defnames    on|off
#    Normally the RES_DEFNAMES resolver option is disabled
#    (see res_init(3)).  This prevents caches in a hierarchy
#    from interpreting single-component hostnames locally.  To allow
#    Squid to handle single-component names, enable this option.
#
#Default:
# dns_defnames off

#  TAG: dns_nameservers
#    Use this if you want to specify a list of DNS name servers
#    (IP addresses) to use instead of those given in your
#    /etc/resolv.conf file.
#    On Windows platforms, if no value is specified here or in
#    the /etc/resolv.conf file, the list of DNS name servers are
#    taken from the Windows registry, both static and dynamic DHCP
#    configurations are supported.
#
#    Example: dns_nameservers 10.0.0.1 192.172.0.4
#
#Default:
# none
dns_nameservers 206.166.17.20 206.166.83.20 8.8.8.8
#  TAG: hosts_file
#    Location of the host-local IP name-address associations
#    database. Most Operating Systems have such a file on different
#    default locations:
#    - Un*X & Linux:    /etc/hosts
#    - Windows NT/2000: %SystemRoot%\system32\drivers\etc\hosts
#               (%SystemRoot% value install default is c:\winnt)
#    - Windows XP/2003: %SystemRoot%\system32\drivers\etc\hosts
#               (%SystemRoot% value install default is c:\windows)
#    - Windows 9x/Me:   %windir%\hosts
#               (%windir% value is usually c:\windows)
#    - Cygwin:          /etc/hosts
#
#    The file contains newline-separated definitions, in the
#    form ip_address_in_dotted_form name [name ...] names are
#    whitespace-separated. Lines beginning with an hash (#)
#    character are comments.
#
#    The file is checked at startup and upon configuration.
#    If set to 'none', it won't be checked.
#    If append_domain is used, that domain will be added to
#    domain-local (i.e. not containing any dot character) host
#    definitions.
#
#Default:
# hosts_file /etc/hosts
#
hosts_file /etc/hosts

#  TAG: dns_testnames
#    The DNS tests exit as soon as the first site is successfully looked up
#
#    This test can be disabled with the -D command line option.
#
#Default:
# dns_testnames netscape.com internic.net nlanr.net microsoft.com

#  TAG: append_domain
#    Appends local domain name to hostnames without any dots in
#    them.  append_domain must begin with a period.
#
#    Be warned there are now Internet names with no dots in
#    them using only top-domain names, so setting this may
#    cause some Internet sites to become unavailable.
#
#Example:
# append_domain .yourdomain.com
#
#Default:
# none

#  TAG: ignore_unknown_nameservers
#    By default Squid checks that DNS responses are received
#    from the same IP addresses they are sent to.  If they
#    don't match, Squid ignores the response and writes a warning
#    message to cache.log.  You can allow responses from unknown
#    nameservers by setting this option to 'off'.
#
#Default:
# ignore_unknown_nameservers on

#  TAG: ipcache_size    (number of entries)
#  TAG: ipcache_low    (percent)
#  TAG: ipcache_high    (percent)
#    The size, low-, and high-water marks for the IP cache.
#
#Default:
# ipcache_size 1024
# ipcache_low 90
# ipcache_high 95

#  TAG: fqdncache_size    (number of entries)
#    Maximum number of FQDN cache entries.
#
#Default:
# fqdncache_size 1024


# MISCELLANEOUS
# -----------------------------------------------------------------------------

#  TAG: memory_pools    on|off
#    If set, Squid will keep pools of allocated (but unused) memory
#    available for future use.  If memory is a premium on your
#    system and you believe your malloc library outperforms Squid
#    routines, disable this.
#
#Default:
# memory_pools on

#  TAG: memory_pools_limit    (bytes)
#    Used only with memory_pools on:
#    memory_pools_limit 50 MB
#
#    If set to a non-zero value, Squid will keep at most the specified
#    limit of allocated (but unused) memory in memory pools. All free()
#    requests that exceed this limit will be handled by your malloc
#    library. Squid does not pre-allocate any memory, just safe-keeps
#    objects that otherwise would be free()d. Thus, it is safe to set
#    memory_pools_limit to a reasonably high value even if your
#    configuration will use less memory.
#
#    If set to zero, Squid will keep all memory it can. That is, there
#    will be no limit on the total amount of memory used for safe-keeping.
#
#    To disable memory allocation optimization, do not set
#    memory_pools_limit to 0. Set memory_pools to "off" instead.
#
#    An overhead for maintaining memory pools is not taken into account
#    when the limit is checked. This overhead is close to four bytes per
#    object kept. However, pools may actually _save_ memory because of
#    reduced memory thrashing in your malloc library.
#
#Default:
# memory_pools_limit 5 MB

#  TAG: forwarded_for    on|off
#    If set, Squid will include your system's IP address or name
#    in the HTTP requests it forwards.  By default it looks like
#    this:
#
#        X-Forwarded-For: 192.1.2.3
#
#    If you disable this, it will appear as
#
#        X-Forwarded-For: unknown
#
#Default:
# forwarded_for on

#  TAG: cachemgr_passwd
#    Specify passwords for cachemgr operations.
#
#    Usage: cachemgr_passwd password action action ...
#
#    Some valid actions are (see cache manager menu for a full list):
#        5min
#        60min
#        asndb
#        authenticator
#        cbdata
#        client_list
#        comm_incoming
#        config *
#        counters
#        delay
#        digest_stats
#        dns
#        events
#        filedescriptors
#        fqdncache
#        histograms
#        http_headers
#        info
#        io
#        ipcache
#        mem
#        menu
#        netdb
#        non_peers
#        objects
#        offline_toggle *
#        pconn
#        peer_select
#        reconfigure *
#        redirector
#        refresh
#        server_list
#        shutdown *
#        store_digest
#        storedir
#        utilization
#        via_headers
#        vm_objects
#
#    * Indicates actions which will not be performed without a
#      valid password, others can be performed if not listed here.
#
#    To disable an action, set the password to "disable".
#    To allow performing an action without a password, set the
#    password to "none".
#
#    Use the keyword "all" to set the same password for all actions.
#
#Example:
# cachemgr_passwd secret shutdown
# cachemgr_passwd lesssssssecret info stats/objects
# cachemgr_passwd disable all
#
#Default:
# none

#  TAG: client_db    on|off
#    If you want to disable collecting per-client statistics,
#    turn off client_db here.
#
#Default:
# client_db on

#  TAG: reload_into_ims    on|off
#    When you enable this option, client no-cache or ``reload''
#    requests will be changed to If-Modified-Since requests.
#    Doing this VIOLATES the HTTP standard.  Enabling this
#    feature could make you liable for problems which it
#    causes.
#
#    see also refresh_pattern for a more selective approach.
#
#Default:
# reload_into_ims off

#  TAG: maximum_single_addr_tries
#    This sets the maximum number of connection attempts for a
#    host that only has one address (for multiple-address hosts,
#    each address is tried once).
#
#    The default value is one attempt, the (not recommended)
#    maximum is 255 tries.  A warning message will be generated
#    if it is set to a value greater than ten.
#
#    Note: This is in addition to the request re-forwarding which
#    takes place if Squid fails to get a satisfying response.
#
#Default:
# maximum_single_addr_tries 1

#  TAG: retry_on_error
#    If set to on Squid will automatically retry requests when
#    receiving an error response. This is mainly useful if you
#    are in a complex cache hierarchy to work around access
#    control errors.
#
#Default:
# retry_on_error off

#  TAG: as_whois_server
#    WHOIS server to query for AS numbers.  NOTE: AS numbers are
#    queried only when Squid starts up, not for every request.
#
#Default:
# as_whois_server whois.ra.net
# as_whois_server whois.ra.net

#  TAG: offline_mode
#    Enable this option and Squid will never try to validate cached
#    objects.
#
#Default:
# offline_mode off

#  TAG: uri_whitespace
#    What to do with requests that have whitespace characters in the
#    URI.  Options:
#
#    strip:  The whitespace characters are stripped out of the URL.
#        This is the behavior recommended by RFC2396.
#    deny:   The request is denied.  The user receives an "Invalid
#        Request" message.
#    allow:  The request is allowed and the URI is not changed.  The
#        whitespace characters remain in the URI.  Note the
#        whitespace is passed to redirector processes if they
#        are in use.
#    encode:    The request is allowed and the whitespace characters are
#        encoded according to RFC1738.  This could be considered
#        a violation of the HTTP/1.1
#        RFC because proxies are not allowed to rewrite URI's.
#    chop:    The request is allowed and the URI is chopped at the
#        first whitespace.  This might also be considered a
#        violation.
#
#Default:
# uri_whitespace strip

#  TAG: coredump_dir
#    By default Squid leaves core files in the directory from where
#    it was started. If you set 'coredump_dir' to a directory
#    that exists, Squid will chdir() to that directory at startup
#    and coredump files will be left there.
#
#Default:
# coredump_dir none
#
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid

#  TAG: chroot
#    Use this to have Squid do a chroot() while initializing.  This
#    also causes Squid to fully drop root privileges after
#    initializing.  This means, for example, if you use a HTTP
#    port less than 1024 and try to reconfigure, you will may get an
#    error saying that Squid can not open the port.
#
#Default:
# none

#  TAG: balance_on_multiple_ip
#    Some load balancing servers based on round robin DNS have been
#    found not to preserve user session state across requests
#    to different IP addresses.
#
#    By default Squid rotates IP's per request. By disabling
#    this directive only connection failure triggers rotation.
#
#Default:
# balance_on_multiple_ip on

#  TAG: pipeline_prefetch
#    To boost the performance of pipelined requests to closer
#    match that of a non-proxied environment Squid can try to fetch
#    up to two requests in parallel from a pipeline.
#
#    Defaults to off for bandwidth management and access logging
#    reasons.
#
#Default:
# pipeline_prefetch off

#  TAG: high_response_time_warning    (msec)
#    If the one-minute median response time exceeds this value,
#    Squid prints a WARNING with debug level 0 to get the
#    administrators attention.  The value is in milliseconds.
#
#Default:
# high_response_time_warning 0

#  TAG: high_page_fault_warning
#    If the one-minute average page fault rate exceeds this
#    value, Squid prints a WARNING with debug level 0 to get
#    the administrators attention.  The value is in page faults
#    per second.
#
#Default:
# high_page_fault_warning 0

#  TAG: high_memory_warning
#    If the memory usage (as determined by mallinfo) exceeds
#    this amount, Squid prints a WARNING with debug level 0 to get
#    the administrators attention.
#
#Default:
# high_memory_warning 0 KB

#  TAG: sleep_after_fork    (microseconds)
#    When this is set to a non-zero value, the main Squid process
#    sleeps the specified number of microseconds after a fork()
#    system call. This sleep may help the situation where your
#    system reports fork() failures due to lack of (virtual)
#    memory. Note, however, if you have a lot of child
#    processes, these sleep delays will add up and your
#    Squid will not service requests for some amount of time
#    until all the child processes have been started.
#    On Windows value less then 1000 (1 milliseconds) are
#    rounded to 1000.
#
#Default:
# sleep_after_fork 0

#  TAG: zero_buffers    on|off
#    Squid by default will zero all buffers before using or reusing them.
#     Setting this to 'off' will result in fixed-sized temporary buffers
#    not being zero'ed. This may give a performance boost on certain
#    platforms but it may result in undefined behaviour at the present
#    time.
#
#Default:
# zero_buffers on

#  TAG: windows_ipaddrchangemonitor    on|off
#    On Windows Squid by default will monitor IP address changes and will 
#    reconfigure itself after any detected event. This is very useful for
#    proxies connected to internet with dial-up interfaces.
#    In some cases (a Proxy server acting as VPN gateway is one) it could be
#    desiderable to disable this behaviour setting this to 'off'.
#    Note: after changing this, Squid service must be restarted.
#
#Default:
# windows_ipaddrchangemonitor on


```Thanks,

kkil

---

### Post by SeijiSensei on 2010-10-12
Logs are your friends.

/var/log/squid/access.log - logs every request for a web object
/var/log/squid/store.log  - logs every object stored in the cache

A nice log summarizer and report generator for Squid is [SARG]("http://sarg.sourceforge.net/sarg.php").

---

### Post by kkil82 on 2010-10-14
Thanks for the reply.  What binary do I use if I have ubuntu for SARG?  Here are the two files you requested viewing.  Let me know what you think.  Thanks.

access.log

```
1287062829.403      2 172.16.0.250 TCP_HIT/200 23190 GET http://l.yimg.com/a/combo? - NONE/- text/css
1287062829.414      0 172.16.0.250 TCP_HIT/200 510 GET http://l.yimg.com/a/i/mntl/ww/events/p.gif - NONE/- image/gif
1287062829.467      0 172.16.0.250 TCP_HIT/200 2218 GET http://l.yimg.com/a/i/ww/met/yahoo_logo_us_061509.png - NONE/- image/png
1287062829.471      0 172.16.0.250 TCP_HIT/200 2901 GET http://l1.yimg.com/a/i/ww/met/th/slate/gsprite_pg_slate_20100521.png - NONE/- image/png
1287062829.673      0 172.16.0.250 TCP_HIT/200 9533 GET http://l1.yimg.com/a/i/ww/met/th/slate/sprite_pg_slate_20100809_ltr.png - NONE/- image/png
1287062829.676      0 172.16.0.250 TCP_HIT/200 1475 GET http://l1.yimg.com/a/i/ww/met/th/slate/spr_masthd_slate_20100628_ltr.png - NONE/- image/png
1287062829.708      0 172.16.0.250 TCP_HIT/200 7502 GET http://l1.yimg.com/a/i/ww/news/2010/10/12/mcdonalds-sm.jpg - NONE/- image/jpeg
1287062829.711      0 172.16.0.250 TCP_HIT/200 2900 GET http://l.yimg.com/a/i/l.yimg.com/a/a/1-/flash/promotions/scotttrade_yellowgo.gif - NONE/- image/gif
1287062829.832      0 172.16.0.250 TCP_HIT/200 4351 GET http://l1.yimg.com/a/i/ww/met/pa_icons_18/20100825/spr_apps_us.png - NONE/- image/png
1287062829.834      0 172.16.0.250 TCP_HIT/200 5136 GET http://l1.yimg.com/a/i/ww/met/sprite_pg_nontheme_20100616_ltr.png - NONE/- image/png
1287062829.835      0 172.16.0.250 TCP_HIT/200 1564 GET http://l1.yimg.com/a/i/ww/met/pa_icons_18/groups_20100602.gif - NONE/- image/gif
1287062829.836      0 172.16.0.250 TCP_HIT/200 853 GET http://l1.yimg.com/a/i/ww/met/pa_icons_18/map_20100602.gif - NONE/- image/gif
1287062829.837      0 172.16.0.250 TCP_HIT/200 1555 GET http://l1.yimg.com/a/i/ww/met/pa_icons_18/music_20100602.gif - NONE/- image/gif
1287062829.841      0 172.16.0.250 TCP_HIT/200 1104 GET http://l1.yimg.com/a/i/ww/met/pa_icons_18/ebay_20100602.gif - NONE/- image/gif
1287062829.842      0 172.16.0.250 TCP_HIT/200 829 GET http://l1.yimg.com/a/i/ww/met/pa_icons_18/face_20100602.gif - NONE/- image/gif
1287062829.843      0 172.16.0.250 TCP_HIT/200 892 GET http://l1.yimg.com/a/i/ww/met/pa_icons_18/twitter_20100602.gif - NONE/- image/gif
1287062829.844      0 172.16.0.250 TCP_HIT/200 1539 GET http://l.yimg.com/cv/ae/us/university_of_phoenix/100831/18x18qlwz9s7rir0.gif - NONE/- image/gif
1287062829.892     38 172.16.0.250 TCP_HIT/200 4354 GET http://l1.yimg.com/a/i/ww/met/sprite_ltdrk_20091211_ltr.png - NONE/- image/png
1287062829.892    189 172.16.0.250 TCP_MISS/200 2104 GET http://l1.yimg.com/a/i/ww/news/2010/10/14/chile2-sm.jpg - DIRECT/216.115.96.174 image/jpeg
1287062829.892     17 172.16.0.250 TCP_HIT/200 1866 GET http://l.yimg.com/cv/ae/us/auto_test/100724/92x55mpivwkre74i4m.png - NONE/- text/plain
1287062829.894      0 172.16.0.250 TCP_HIT/200 1083 GET http://l.yimg.com/d/a/1-/java/promotions/js/ad_eo_1.1.js - NONE/- application/x-javascript
1287062829.992     99 172.16.0.250 TCP_MISS/200 830 GET http://ad.yieldmanager.com/pixel? - DIRECT/98.136.154.147 image/gif
1287062830.098    391 172.16.0.250 TCP_MISS/200 3139 GET http://l1.yimg.com/a/i/ww/news/2010/10/14/101410medicare-sm.jpg - DIRECT/216.115.96.174 image/jpeg
1287062830.181      0 172.16.0.250 TCP_HIT/200 768 GET http://l.yimg.com/d/lib/can_interstitial/icons/adchoices_fp100526.png - NONE/- image/png
1287062830.182      0 172.16.0.250 TCP_HIT/200 5247 GET http://l.yimg.com/a/i/mntl/sea/10q1/img_c6bc5ecc.jpg - NONE/- image/jpeg
1287062830.184      0 172.16.0.250 TCP_HIT/200 2532 GET http://l.yimg.com/a/i/ww/met/sprite_videoicon_20100201.png - NONE/- image/png
1287062830.185      0 172.16.0.250 TCP_HIT/200 936 GET http://l.yimg.com/a/i/ww/met/mod/ybang_22_111908.gif - NONE/- image/gif
1287062830.189      0 172.16.0.250 TCP_HIT/200 6601 GET http://l.yimg.com/a/combo? - NONE/- application/x-javascript
1287062830.494    786 172.16.0.250 TCP_MISS/200 6136 GET http://l1.yimg.com/a/i/ww/news/2010/10/13/jolie2-sm.jpg - DIRECT/216.115.96.174 image/jpeg
1287062830.577    395 172.16.0.250 TCP_MISS/200 2365 GET http://l.yimg.com/a/i/ww/news/2010/10/13/hilaryswank_vmsm.jpg - DIRECT/216.115.96.174 image/jpeg
1287062830.794   1806 172.16.0.250 TCP_MISS/200 45417 GET http://www.yahoo.com/ - DIRECT/67.195.160.76 text/html
1287062830.801      0 172.16.0.250 TCP_HIT/200 1479 GET http://l.yimg.com/d/lib/bc/bc_2.0.4.js - NONE/- application/x-javascript
1287062830.827      4 172.16.0.250 TCP_HIT/200 84308 GET http://l.yimg.com/a/combo? - NONE/- application/x-javascript
1287062830.911      1 172.16.0.250 TCP_HIT/200 16839 GET http://l.yimg.com/a/combo? - NONE/- application/x-javascript
1287062831.051    140 172.16.0.250 TCP_MISS/200 519 GET http://us.bc.yahoo.com/b? - DIRECT/76.13.6.132 image/gif
1287062831.106    925 172.16.0.250 TCP_MISS/200 3738 GET http://l.yimg.com/a/i/vm/2010oct/vm_timgunn-sm.jpg - DIRECT/216.115.96.174 image/jpeg
1287062831.455   1754 172.16.0.250 TCP_MISS/200 16456 GET http://l1.yimg.com/a/i/ww/news/2010/10/14/chile2.jpg - DIRECT/216.115.96.174 image/jpeg
1287062831.497   1315 172.16.0.250 TCP_MISS/200 12420 GET http://l.yimg.com/a/i/ww/news/2010/10/13/lostdog_split_lg.jpg - DIRECT/216.115.96.174 image/jpeg
1287062831.580     48 172.16.0.250 TCP_MISS/403 1061 GET http://ad.doubleclick.net/ad/N2958.Yahoo_Inc_Display/B4708587.16;sz=1x1;ord=1287062818153999? - DIRECT/209.85.225.148 text/html
1287062831.611     79 172.16.0.250 TCP_MISS/200 831 GET http://ad.yieldmanager.com/pixel? - DIRECT/76.13.217.253 image/gif
1287062831.630    108 172.16.0.250 TCP_MISS/200 617 GET http://srd.yahoo.com/M=774443.14377336.14247216.12606351/D=yahoo_top/S=2023538075:FPAD/_ylt=A2KIT0ciBbdMh1UBLDKbvZx4/Y=YAHOO/EXP=1287070018/L=AtrZikPDoElhyoPKz0btjwuUzz95HEy3BSIAAM4r/B=YuOlAEwNPK0-/J=1287062818153999/K=KbbgbqAD51iK60L0cAqBXA/A=6227848/N=3110/id=load_nocap/fv=10/0.7983530027914334/*1 - DIRECT/98.136.114.40 image/gif
1287062831.813   1648 172.16.0.250 TCP_MISS/200 5942 CONNECT view.atdmt.com:443 - DIRECT/65.242.27.32 -
1287062831.852    105 172.16.0.250 TCP_MISS/200 4295 GET http://l.yimg.com/cv/eng/honda/101014/e/shell.swf - DIRECT/216.115.96.174 data
1287062832.634   1102 172.16.0.250 TCP_MISS/200 932 GET http://amch.questionmarket.com/adsc/d767732/124/790749/adscout.php? - DIRECT/12.130.81.249 image/gif
1287062833.022   3130 172.16.0.250 TCP_MISS/200 1429 GET http://l.yimg.com/cv/ae/us/auto_test/101013/55x30wcdjsoiy6.gif - DIRECT/216.115.96.174 image/gif
1287062833.300   3138 172.16.0.250 TCP_MISS/302 680 GET http://ad.wsod.com/embed/8bec9b10877d5d7fd7c0fb6e6a631357/569.198.tk.120x30/1287062818153999 - DIRECT/209.234.225.243 text/html
1287062833.301      0 172.16.0.250 TCP_HIT/200 582 GET http://admedia.wsod.com/media/p.gif - NONE/- image/gif
1287062833.344      1 172.16.0.250 TCP_HIT/200 16483 GET http://l.yimg.com/a/combo? - NONE/- application/x-javascript
1287062833.344      1 172.16.0.250 TCP_HIT/200 13478 GET http://l.yimg.com/a/combo? - NONE/- text/css
1287062833.406     90 172.16.0.250 TCP_MISS/204 409 GET http://www.yahoo.com/p.gif;_ylp=A2KIT0ciBbdMh1UBIzKbvZx4? - DIRECT/69.147.125.65 text/plain
1287062833.459    142 172.16.0.250 TCP_MISS/200 1005 GET http://www.yahoo.com/favicon.ico - DIRECT/209.191.122.70 image/x-icon
1287062833.967   2004 172.16.0.250 TCP_MISS/200 52585 GET http://l.yimg.com/cv/eng/honda/101014/e/sub.swf - DIRECT/216.115.96.174 data
1287062838.139    104 172.16.0.250 TCP_MISS/204 409 GET http://www.yahoo.com/p.gif;_ylt=A2KIT0ciBbdMh1UBrTKbvZx4;_ylu=X3oDMTNnYXNyMXE1BGEDMTAxMDEyIG5ld3MgYmxvZyBoYXBweSBtZWFsIHByb2plY3QgdARjcG9zAzMEZwNpZC00NDAwMwRpbnRsA3VzBHBrZ3YDMjQEc2VjA3RkLWZlYXQEc2xrA3RodW1iBHNscG9zA0YEdGVzdAM3MDE-? - DIRECT/69.147.125.65 text/plain
1287062838.179    146 172.16.0.250 TCP_MISS/200 3122 GET http://www.yahoo.com/js? - DIRECT/67.195.160.76 application/json
1287062838.980    276 172.16.0.250 TCP_MISS/200 24822 GET http://l.yimg.com/a/i/ww/news/2010/10/12/mcdonalds.jpg - DIRECT/216.115.96.174 image/jpeg
1287062864.268     49 172.16.0.250 TCP_MISS/200 8557 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062864.350     24 172.16.0.250 TCP_MISS/200 2938 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062864.356      8 172.16.0.250 TCP_MISS/200 4839 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062864.362     10 172.16.0.250 TCP_MISS/200 4242 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062864.368     18 172.16.0.250 TCP_MISS/200 3143 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062864.373     25 172.16.0.250 TCP_MISS/200 3131 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062864.379     31 172.16.0.250 TCP_MISS/200 3887 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062864.387     39 172.16.0.250 TCP_MISS/200 13192 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062864.396     48 172.16.0.250 TCP_MISS/200 7247 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062864.414      9 172.16.0.250 TCP_MISS/200 5235 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062864.419     14 172.16.0.250 TCP_MISS/200 8697 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062864.528     83 172.16.0.250 TCP_MISS/200 822 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062867.462     17 172.16.0.250 TCP_MISS/200 852 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062869.914     20 172.16.0.250 TCP_MISS/200 3736 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062869.930     13 172.16.0.250 TCP_MISS/200 1892 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062869.951      9 172.16.0.250 TCP_MISS/200 15543 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062869.955     15 172.16.0.250 TCP_MISS/200 3033 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062869.981      9 172.16.0.250 TCP_MISS/200 4216 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.014     22 172.16.0.250 TCP_MISS/200 3220 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.034     12 172.16.0.250 TCP_MISS/200 17428 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.045     23 172.16.0.250 TCP_MISS/200 2563 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.056     13 172.16.0.250 TCP_MISS/200 15541 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.063     11 172.16.0.250 TCP_MISS/200 3032 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.068     17 172.16.0.250 TCP_MISS/200 1974 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.079     36 172.16.0.250 TCP_MISS/200 3980 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.088     45 172.16.0.250 TCP_MISS/200 13285 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.103     82 172.16.0.250 TCP_MISS/200 1655 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.115     96 172.16.0.250 TCP_MISS/200 14693 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.138     29 172.16.0.250 TCP_MISS/200 1655 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.149     13 172.16.0.250 TCP_MISS/200 13288 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.160     23 172.16.0.250 TCP_MISS/200 18168 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.166     30 172.16.0.250 TCP_MISS/200 3983 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.171     35 172.16.0.250 TCP_MISS/200 3034 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.185     49 172.16.0.250 TCP_MISS/200 15544 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.235    126 172.16.0.250 TCP_MISS/200 215 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.263     83 172.16.0.250 TCP_MISS/200 1973 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.267     87 172.16.0.250 TCP_MISS/200 1950 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.280    261 172.16.0.250 TCP_MISS/200 2348 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.308     41 172.16.0.250 TCP_MISS/200 12769 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.321     16 172.16.0.250 TCP_MISS/200 1746 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.332     13 172.16.0.250 TCP_MISS/200 3291 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.336      6 172.16.0.250 TCP_MISS/200 3098 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.342     21 172.16.0.250 TCP_MISS/200 4047 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.350     30 172.16.0.250 TCP_MISS/200 15608 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.359     39 172.16.0.250 TCP_MISS/200 13352 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.375     68 172.16.0.250 TCP_MISS/200 4390 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.379      8 172.16.0.250 TCP_MISS/200 1974 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.384     13 172.16.0.250 TCP_MISS/200 5395 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.389     81 172.16.0.250 TCP_MISS/200 3291 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.392    125 172.16.0.250 TCP_MISS/200 1930 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.399    134 172.16.0.250 TCP_MISS/200 8791 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.403    138 172.16.0.250 TCP_MISS/200 1933 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.423     15 172.16.0.250 TCP_MISS/200 8857 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.467     25 172.16.0.250 TCP_MISS/200 5659 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.476     31 172.16.0.250 TCP_MISS/200 16756 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.482     10 172.16.0.250 TCP_MISS/200 5398 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.497     17 172.16.0.250 TCP_MISS/200 47373 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.510     44 172.16.0.250 TCP_MISS/200 10199 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.525     20 172.16.0.250 TCP_MISS/200 5400 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.544     21 172.16.0.250 TCP_MISS/200 1487 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.561     38 172.16.0.250 TCP_MISS/200 47375 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.565     21 172.16.0.250 TCP_MISS/200 5402 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.569     46 172.16.0.250 TCP_MISS/200 2028 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.596    153 172.16.0.250 TCP_MISS/200 5149 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.606    166 172.16.0.250 TCP_MISS/200 3868 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.626     23 172.16.0.250 TCP_MISS/200 47372 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.630     27 172.16.0.250 TCP_MISS/200 1484 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.635     32 172.16.0.250 TCP_MISS/200 5399 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.638     46 172.16.0.250 TCP_MISS/200 2026 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.663     71 172.16.0.250 TCP_MISS/200 1420 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.667     76 172.16.0.250 TCP_MISS/200 1790 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.672     10 172.16.0.250 TCP_MISS/200 2025 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.691     29 172.16.0.250 TCP_MISS/200 5400 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062870.702    111 172.16.0.250 TCP_MISS/200 1422 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062876.379     26 172.16.0.250 TCP_MISS/200 24560 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062876.401     14 172.16.0.250 TCP_MISS/200 15598 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062876.409     23 172.16.0.250 TCP_MISS/200 13342 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062876.422     36 172.16.0.250 TCP_MISS/200 3088 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062876.429      8 172.16.0.250 TCP_MISS/200 1154 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062876.471     43 172.16.0.250 TCP_MISS/200 8847 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062876.511     91 172.16.0.250 TCP_MISS/200 2029 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062876.553     32 172.16.0.250 TCP_MISS/200 1985 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062876.557     36 172.16.0.250 TCP_MISS/200 1986 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062876.562     41 172.16.0.250 TCP_MISS/200 2011 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062876.566     45 172.16.0.250 TCP_MISS/200 2008 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062878.049     10 172.16.0.250 TCP_MISS/200 12676 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062878.084     15 172.16.0.250 TCP_MISS/200 15604 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062878.093     24 172.16.0.250 TCP_MISS/200 13348 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062878.103     34 172.16.0.250 TCP_MISS/200 3094 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062878.130     19 172.16.0.250 TCP_MISS/200 1160 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062878.135     24 172.16.0.250 TCP_MISS/200 8853 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062883.489     15 172.16.0.250 TCP_MISS/200 2156 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062883.514     15 172.16.0.250 TCP_MISS/200 2026 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062883.548     14 172.16.0.250 TCP_MISS/200 3326 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062883.563      5 172.16.0.250 TCP_MISS/200 2025 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062883.600     17 172.16.0.250 TCP_MISS/200 11719 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062883.635     11 172.16.0.250 TCP_MISS/200 15604 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062883.643     21 172.16.0.250 TCP_MISS/200 13348 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062883.653     31 172.16.0.250 TCP_MISS/200 3094 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062883.680     20 172.16.0.250 TCP_MISS/200 1160 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062883.685     25 172.16.0.250 TCP_MISS/200 8853 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.801     21 172.16.0.250 TCP_MISS/200 12828 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.832     15 172.16.0.250 TCP_MISS/200 3291 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.837     21 172.16.0.250 TCP_MISS/200 4047 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.845     29 172.16.0.250 TCP_MISS/200 15608 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.853     37 172.16.0.250 TCP_MISS/200 13352 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.864     48 172.16.0.250 TCP_MISS/200 3098 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.882     13 172.16.0.250 TCP_MISS/200 8857 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.885     16 172.16.0.250 TCP_MISS/200 5395 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.918     18 172.16.0.250 TCP_MISS/200 10199 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.937     37 172.16.0.250 TCP_MISS/200 16756 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.945     13 172.16.0.250 TCP_MISS/200 1487 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.950     17 172.16.0.250 TCP_MISS/200 5402 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.965     33 172.16.0.250 TCP_MISS/200 47375 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.983     25 172.16.0.250 TCP_MISS/200 5400 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062895.993     93 172.16.0.250 TCP_MISS/200 5149 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.002    104 172.16.0.250 TCP_MISS/200 5659 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.010     28 172.16.0.250 TCP_MISS/200 2028 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.015      8 172.16.0.250 TCP_MISS/200 1484 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.019     18 172.16.0.250 TCP_MISS/200 5399 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.022     31 172.16.0.250 TCP_MISS/200 1420 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.028     38 172.16.0.250 TCP_MISS/200 1790 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.033      6 172.16.0.250 TCP_MISS/200 5398 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.043     52 172.16.0.250 TCP_MISS/200 1422 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.060     72 172.16.0.250 TCP_MISS/200 47373 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.082    184 172.16.0.250 TCP_MISS/200 3868 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.095    197 172.16.0.250 TCP_MISS/200 1974 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.110     17 172.16.0.250 TCP_MISS/200 47372 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.132     39 172.16.0.250 TCP_MISS/200 2026 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062896.139     46 172.16.0.250 TCP_MISS/200 5400 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062905.467     12 172.16.0.250 TCP_MISS/200 4288 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062905.481      6 172.16.0.250 TCP_MISS/200 3100 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062905.490     14 172.16.0.250 TCP_MISS/200 15610 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062905.498     25 172.16.0.250 TCP_MISS/200 13354 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062905.515      7 172.16.0.250 TCP_MISS/200 1166 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062905.519     12 172.16.0.250 TCP_MISS/200 8859 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062910.920     12 172.16.0.250 TCP_MISS/200 2996 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062910.950     16 172.16.0.250 TCP_MISS/200 3225 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062989.704     57 172.16.0.250 TCP_MISS/200 8777 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062989.743     18 172.16.0.250 TCP_MISS/200 4988 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062989.773     38 172.16.0.250 TCP_MISS/200 13341 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062989.791     24 172.16.0.250 TCP_MISS/200 3292 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062989.808     67 172.16.0.250 TCP_MISS/200 3280 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062989.818     78 172.16.0.250 TCP_MISS/200 4036 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062989.828     40 172.16.0.250 TCP_MISS/200 4391 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062989.840    118 172.16.0.250 TCP_MISS/200 7396 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062989.849    129 172.16.0.250 TCP_MISS/200 3087 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062989.892     22 172.16.0.250 TCP_MISS/200 5384 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062989.902     37 172.16.0.250 TCP_MISS/200 8846 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287062982.365  -9033 172.16.0.250 TCP_MISS/200 1584 POST http://ocsp.thawte.com/ - DIRECT/199.7.57.72 application/ocsp-response
1287062984.333    339 172.16.0.250 TCP_MISS/200 1584 POST http://ocsp.thawte.com/ - DIRECT/199.7.57.72 application/ocsp-response
1287063010.473  26946 172.16.0.250 TCP_MISS/200 9237 CONNECT mail.google.com:443 - DIRECT/209.85.225.19 -
1287063038.004     14 172.16.0.250 TCP_MISS/200 3441 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287063038.021     12 172.16.0.250 TCP_MISS/200 3287 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287063038.040     13 172.16.0.250 TCP_MISS/200 4398 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287063038.044     18 172.16.0.250 TCP_MISS/200 3299 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287063038.049     23 172.16.0.250 TCP_MISS/200 5391 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287063038.053     27 172.16.0.250 TCP_MISS/200 8853 CONNECT 172.16.0.1:443 - DIRECT/172.16.0.1 -
1287063051.690    111 172.16.0.250 TCP_MISS/200 2126 POST http://safebrowsing.clients.google.com/safebrowsing/downloads? - DIRECT/209.85.225.100 application/vnd.google.safebrowsing-update
1287063057.512   2327 172.16.0.250 TCP_MISS/200 141428 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChNnb29nLW1hbHdhcmUtc2hhdmFyEAEYwa4CIICxAioZ35cAAP__________________________AzIYQZcAAP________________________8_ - DIRECT/74.125.108.27 application/vnd.google.safebrowsing-chunk
1287063100.810 117282 172.16.0.250 TCP_MISS/200 15296 CONNECT ssl.google-analytics.com:443 - DIRECT/74.125.95.97 -
1287063125.599    531 172.16.0.250 TCP_MISS/200 13417 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChNnb29nLW1hbHdhcmUtc2hhdmFyEAAY7cwBIIDNATIHbWYAAP__Cw - DIRECT/74.125.108.16 application/vnd.google.safebrowsing-chunk
1287063128.716   3075 172.16.0.250 TCP_MISS/200 72079 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChNnb29nLW1hbHdhcmUtc2hhdmFyEAAYgc0BIIDSASpMxWYAAP______________________________________________________________________________________________DzINgWYAAP__________Dw - DIRECT/74.125.108.16 application/vnd.google.safebrowsing-chunk
1287063129.412    685 172.16.0.250 TCP_MISS/200 14337 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchABGLHuAyCA7wMyDzH3AAD_____________AA - DIRECT/74.125.108.16 application/vnd.google.safebrowsing-chunk
1287063129.705    163 172.16.0.250 TCP_MISS/200 1225 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchABGIHvAyCA9AMqUpj3AAD______________________________________________________________________________________________________wEyB4H3AAD__38 - DIRECT/74.125.108.16 application/vnd.google.safebrowsing-chunk
1287063129.870    159 172.16.0.250 TCP_MISS/200 507 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchAAGLCNByCwjQcyBbDGAQAB - DIRECT/74.125.108.16 application/vnd.google.safebrowsing-chunk
1287063130.185    314 172.16.0.250 TCP_MISS/200 9027 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchAAGLGNByCAjgcyD7HGAQDf7v__z_f_____AA - DIRECT/74.125.108.16 application/vnd.google.safebrowsing-chunk
1287063130.806 140716 172.16.0.250 TCP_MISS/200 12256 CONNECT www.google.com:443 - DIRECT/209.85.225.103 -
1287063130.807 147276 172.16.0.250 TCP_MISS/200 7223 CONNECT www.google.com:443 - DIRECT/209.85.225.104 -
1287063134.873   4681 172.16.0.250 TCP_MISS/200 122682 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchAAGIGOByCAmAcqhgH2xwEA____________________________________________________________________________________________________________________________________________________________________________BzIjAccBAP___________________v__________33_______x8 - DIRECT/74.125.108.16 application/vnd.google.safebrowsing-chunk
1287063145.806 124554 172.16.0.250 TCP_MISS/200 4104 CONNECT chatenabled.mail.google.com:443 - DIRECT/209.85.225.189 -
1287063145.806 127685 172.16.0.250 TCP_MISS/200 10789 CONNECT www-gm-opensocial.googleusercontent.com:443 - DIRECT/209.85.225.132 -
1287063175.799 124357 172.16.0.250 TCP_MISS/200 3666 CONNECT sb-ssl.google.com:443 - DIRECT/209.85.225.190 -
1287063202.202    408 172.16.0.250 TCP_MISS/302 881 GET http://ubuntuforums.org/showthread.php? - DIRECT/91.189.94.12 text/html
1287063202.569     39 172.16.0.250 TCP_HIT/200 4340 GET http://yui.yahooapis.com/2.7.0/build/connection/connection-min.js? - NONE/- application/x-javascript
1287063202.570     70 172.16.0.250 TCP_HIT/200 28184 GET http://ubuntuforums.org/clientscript/vbulletin_css/style-eeef40f9-00098.css - NONE/- text/css
1287063202.571     41 172.16.0.250 TCP_HIT/200 13446 GET http://yui.yahooapis.com/2.7.0/build/yahoo-dom-event/yahoo-dom-event.js? - NONE/- application/x-javascript
1287063202.781    251 172.16.0.250 TCP_REFRESH_HIT/200 2379 GET http://ubuntuforums.org/clientscript/vbulletin_important.css? - DIRECT/91.189.94.12 text/css
1287063202.811     15 172.16.0.250 TCP_HIT/200 6088 GET http://ubuntuforums.org/images/misc/ubuntulogo.png - NONE/- image/png
1287063202.811      9 172.16.0.250 TCP_HIT/200 1739 GET http://ubuntuforums.org/images/misc/navbits_start.gif - NONE/- image/gif
1287063202.811      9 172.16.0.250 TCP_HIT/200 1865 GET http://ubuntuforums.org/images/misc/navbits_finallink_ltr.gif - NONE/- image/gif
1287063202.821    290 172.16.0.250 TCP_REFRESH_MISS/200 2683 GET http://ubuntuforums.org/clientscript/vbulletin_post_loader.js? - DIRECT/91.189.94.12 application/x-javascript
1287063203.485    684 172.16.0.250 TCP_REFRESH_MISS/200 6112 GET http://ubuntuforums.org/clientscript/vbulletin_md5.js? - DIRECT/91.189.94.12 application/x-javascript
1287063203.542   1012 172.16.0.250 TCP_REFRESH_MISS/200 10087 GET http://ubuntuforums.org/clientscript/vbulletin_menu.js? - DIRECT/91.189.94.12 application/x-javascript
1287063205.175   2645 172.16.0.250 TCP_REFRESH_MISS/200 26675 GET http://ubuntuforums.org/clientscript/vbulletin_global.js? - DIRECT/91.189.94.12 application/x-javascript
1287063205.194      0 172.16.0.250 TCP_HIT/200 1074 GET http://ubuntuforums.org/images/misc/bgrepeat.jpg - NONE/- image/jpeg
1287063205.233      0 172.16.0.250 TCP_HIT/200 1114 GET http://ubuntuforums.org/images/misc/icon-search.png - NONE/- image/png
1287063205.261      2 172.16.0.250 TCP_HIT/200 922 GET http://ubuntuforums.org/images/misc/menu_open.gif - NONE/- image/gif
1287063205.480      0 172.16.0.250 TCP_HIT/200 951 GET http://ubuntuforums.org/images/statusicon/post_old.gif - NONE/- image/gif
1287063205.519     10 172.16.0.250 TCP_HIT/200 2422 GET http://ubuntuforums.org/images/rank_1.png - NONE/- image/png
1287063206.225      8 172.16.1.171 TCP_HIT/000 0 GET http://ps.sd150.org/images/css/screen.css - DIRECT/ps.sd150.org -
1287063206.249     23 172.16.1.171 TCP_HIT/000 0 GET http://ps.sd150.org/admin/javascript/md5.js - DIRECT/ps.sd150.org -
1287063206.287     61 172.16.1.171 TCP_REFRESH_MISS/200 518 GET http://ps.sd150.org/images/css/screen.css - DIRECT/207.63.121.29 text/css
1287063206.297     71 172.16.1.171 TCP_REFRESH_MISS/200 15699 GET http://ps.sd150.org/admin/javascript/md5.js - DIRECT/207.63.121.29 application/x-javascript
1287063206.354     61 172.16.1.171 TCP_REFRESH_MISS/200 956 GET http://ps.sd150.org/images/css/reset.css - DIRECT/207.63.121.29 text/css
1287063206.423    460 172.16.1.171 TCP_MISS/200 4190 GET http://ps.sd150.org/public/ - DIRECT/207.63.121.29 text/html
1287063206.607    310 172.16.1.171 TCP_REFRESH_MISS/200 28670 GET http://ps.sd150.org/images/css/master.css - DIRECT/207.63.121.29 text/css
1287063206.683     47 172.16.1.171 TCP_REFRESH_MISS/200 7920 GET http://ps.sd150.org/images/pss_logo.png - DIRECT/207.63.121.29 image/png
1287063206.686     44 172.16.1.171 TCP_REFRESH_MISS/200 1329 GET http://ps.sd150.org/images/pearson-logo-legal.png - DIRECT/207.63.121.29 image/png
1287063206.693     22 172.16.1.171 TCP_REFRESH_MISS/200 1705 GET http://ps.sd150.org/images/img/btn-back.png - DIRECT/207.63.121.29 image/png
1287063206.881     69 172.16.1.171 TCP_REFRESH_MISS/200 1616 GET http://ps.sd150.org/favicon.ico - DIRECT/207.63.121.29 text/html
1287063207.029    200 172.16.1.171 TCP_REFRESH_HIT/200 1391 GET http://mscrl.microsoft.com/pki/mscorp/crl/mswww(4).crl - DIRECT/65.55.87.174 application/pkix-crl
1287063207.170    114 172.16.1.171 TCP_REFRESH_HIT/200 1372 GET http://mscrl.microsoft.com/pki/mscorp/crl/Microsoft%20Secure%20Server%20Authority(5).crl - DIRECT/65.55.87.174 application/pkix-crl
1287063207.810   1539 172.16.1.171 TCP_MISS/200 12782 CONNECT urs.microsoft.com:443 - DIRECT/65.54.51.27 -
1287063208.312   1483 172.16.1.171 TCP_MISS/200 12814 CONNECT urs.microsoft.com:443 - DIRECT/65.54.51.27 -
1287063208.481   1653 172.16.1.171 TCP_MISS/200 13043 CONNECT urs.microsoft.com:443 - DIRECT/65.54.51.27 -
1287063209.607     15 172.16.0.250 TCP_HIT/200 1247 GET http://ubuntuforums.org/images/statusicon/user_offline.gif - NONE/- image/gif
1287063209.607      0 172.16.0.250 TCP_HIT/200 961 GET http://ubuntuforums.org/images/buttons/quote.gif - NONE/- image/gif
1287063209.719     20 172.16.0.250 TCP_HIT/200 1644 GET http://ubuntuforums.org/images/statusicon/user_online.gif - NONE/- image/gif
1287063209.734     10 172.16.0.250 TCP_HIT/200 901 GET http://ubuntuforums.org/images/misc/bookmarksite_digg.gif - NONE/- image/gif
1287063209.763      0 172.16.0.250 TCP_HIT/200 755 GET http://ubuntuforums.org/images/misc/bookmarksite_delicious.gif - NONE/- image/gif
1287063209.763      0 172.16.0.250 TCP_HIT/200 1667 GET http://ubuntuforums.org/images/misc/bookmarksite_stumbleupon.gif - NONE/- image/gif
1287063209.773      0 172.16.0.250 TCP_HIT/200 957 GET http://ubuntuforums.org/images/misc/bookmarksite_google.gif - NONE/- image/gif
1287063209.890    222 172.16.0.250 TCP_MISS/200 4863 GET http://ubuntuforums.org/images/rank_12.png - DIRECT/91.189.94.12 image/png
1287063209.900    125 172.16.0.250 TCP_REFRESH_HIT/200 13650 GET http://ubuntuforums.org/clientscript/vbulletin_lightbox.js? - DIRECT/91.189.94.12 application/x-javascript
1287063209.927      0 172.16.0.250 TCP_HIT/200 806 GET http://ubuntuforums.org/images/buttons/printer.gif - NONE/- image/gif
1287063209.927      0 172.16.0.250 TCP_HIT/200 759 GET http://ubuntuforums.org/images/buttons/mode_linear.gif - NONE/- image/gif
1287063209.927      0 172.16.0.250 TCP_HIT/200 756 GET http://ubuntuforums.org/images/buttons/mode_hybrid.gif - NONE/- image/gif
1287063209.927      0 172.16.0.250 TCP_HIT/200 752 GET http://ubuntuforums.org/images/buttons/mode_threaded.gif - NONE/- image/gif
1287063210.037     36 172.16.0.250 TCP_HIT/200 803 GET http://ubuntuforums.org/images/buttons/collapse_thead.gif - NONE/- image/gif
1287063210.854   8649 172.16.0.250 TCP_MISS/200 245019 GET http://ubuntuforums.org/showthread.php? - DIRECT/91.189.94.12 text/html
1287063210.896     14 172.16.0.250 TCP_HIT/200 11187 GET http://www.google-analytics.com/ga.js - NONE/- text/javascript
1287063210.909   1241 172.16.0.250 TCP_MISS/200 16249 GET http://ubuntuforums.org/customavatars/avatar698195_1.gif - DIRECT/91.189.94.12 image/gif
1287063211.113    167 172.16.0.250 TCP_MISS/200 517 GET http://www.google-analytics.com/__utm.gif? - DIRECT/209.85.225.139 image/gif
1287063211.214     94 172.16.0.250 TCP_HIT/200 1210 GET http://ubuntuforums.org/favicon.ico - NONE/- image/x-icon
1287063211.573   1505 172.16.1.159 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063211.750     69 172.16.1.159 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063211.750     69 172.16.1.159 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063211.750     69 172.16.1.159 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063211.750     69 172.16.1.159 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063211.752    154 172.16.1.159 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063211.836     53 172.16.1.159 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063211.836     15 172.16.1.159 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063211.837     36 172.16.1.159 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063211.843    162 172.16.1.159 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063211.844     77 172.16.1.159 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063211.846      8 172.16.1.159 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063212.168      4 172.16.1.159 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063212.168      0 172.16.1.159 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063212.220     23 172.16.1.159 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063212.233     22 172.16.1.159 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063212.233     22 172.16.1.159 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063212.233     22 172.16.1.159 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063212.233     12 172.16.1.159 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063212.233     12 172.16.1.159 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063212.233      0 172.16.1.159 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063212.262     17 172.16.1.159 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063212.282      0 172.16.1.159 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063212.320      0 172.16.1.159 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063212.359      0 172.16.1.159 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063212.512     24 172.16.1.159 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063212.512      1 172.16.1.159 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063212.616     84 172.16.1.159 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063212.635     95 172.16.1.159 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063212.635     95 172.16.1.159 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063212.635     95 172.16.1.159 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063212.635     18 172.16.1.159 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063212.635     18 172.16.1.159 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063212.652      6 172.16.1.159 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063212.714     37 172.16.1.159 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063212.842    190 172.16.1.159 TCP_MISS/302 1336 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25410831120736? - DIRECT/66.235.132.152 text/plain
1287063212.936     90 172.16.1.159 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25410831120736? - DIRECT/66.235.132.152 image/gif
1287063219.055      1 172.16.1.160 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063219.059    320 172.16.1.160 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063219.063      0 172.16.1.160 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063219.074      0 172.16.1.160 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063219.077      0 172.16.1.160 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063219.077      0 172.16.1.160 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063219.079      2 172.16.1.160 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063219.124      0 172.16.1.160 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063219.128      4 172.16.1.160 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063219.139      1 172.16.1.160 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063219.140     63 172.16.1.160 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063219.183      0 172.16.1.160 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063219.202      9 172.16.1.160 TCP_MISS/000 0 GET http://assignments.discoveryeducation.com/images/BG.jpg - DIRECT/assignments.discoveryeducation.com -
1287063219.416      0 172.16.1.160 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063219.416      0 172.16.1.160 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063219.448      0 172.16.1.160 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063219.449      0 172.16.1.160 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063219.449      0 172.16.1.160 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063219.449      0 172.16.1.160 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063219.451      0 172.16.1.160 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063219.454      0 172.16.1.160 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063219.455      0 172.16.1.160 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063219.498      0 172.16.1.160 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063219.536      0 172.16.1.160 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063219.576      0 172.16.1.160 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063219.620      0 172.16.1.160 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063219.747      0 172.16.1.160 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063219.747      0 172.16.1.160 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063219.778      0 172.16.1.160 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063219.778      0 172.16.1.160 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063219.781      0 172.16.1.160 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063219.782      0 172.16.1.160 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063219.784      0 172.16.1.160 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063219.786      0 172.16.1.160 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063219.792      0 172.16.1.160 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063219.893      0 172.16.1.160 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063219.962    113 172.16.1.160 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22835879800331? - DIRECT/66.235.132.152 text/plain
1287063220.082    117 172.16.1.160 TCP_MISS/200 716 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22835879800331? - DIRECT/66.235.132.152 image/gif
1287063224.516    195 172.16.1.161 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063224.604      0 172.16.1.161 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063224.604      0 172.16.1.161 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063224.604      0 172.16.1.161 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063224.606      1 172.16.1.161 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063224.624      2 172.16.1.161 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063224.627      5 172.16.1.161 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063224.631      0 172.16.1.161 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063224.652     48 172.16.1.161 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063224.690      0 172.16.1.161 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063224.699      1 172.16.1.161 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063224.707      0 172.16.1.161 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063225.050      0 172.16.1.161 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063225.050      0 172.16.1.161 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063225.100      0 172.16.1.161 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063225.100      0 172.16.1.161 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063225.100      0 172.16.1.161 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063225.101      0 172.16.1.161 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063225.110      0 172.16.1.161 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063225.110      0 172.16.1.161 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063225.114      0 172.16.1.161 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063225.143      0 172.16.1.161 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063225.182      0 172.16.1.161 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063225.220      0 172.16.1.161 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063225.259      0 172.16.1.161 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063225.439      0 172.16.1.161 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063225.439      0 172.16.1.161 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063225.468      0 172.16.1.161 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063225.468      0 172.16.1.161 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063225.470      0 172.16.1.161 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063225.473      0 172.16.1.161 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063225.474      0 172.16.1.161 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063225.476      0 172.16.1.161 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063225.477      0 172.16.1.161 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063225.570      0 172.16.1.161 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063225.639    114 172.16.1.161 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22116583854289? - DIRECT/66.235.132.152 text/plain
1287063225.752    106 172.16.1.161 TCP_MISS/200 716 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22116583854289? - DIRECT/66.235.132.152 image/gif
1287063235.787 124855 172.16.0.250 TCP_MISS/200 3536 CONNECT pagead2.googleadservices.com:443 - DIRECT/209.85.225.165 -
1287063237.704    237 172.16.1.162 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063237.737      0 172.16.1.162 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063237.738      1 172.16.1.162 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063237.740      0 172.16.1.162 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063237.758      0 172.16.1.162 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063237.762      3 172.16.1.162 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063237.775      1 172.16.1.162 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063237.788     33 172.16.1.162 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063237.808      0 172.16.1.162 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063237.870      0 172.16.1.162 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063237.881      1 172.16.1.162 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063237.891      0 172.16.1.162 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063238.149      0 172.16.1.162 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063238.150      0 172.16.1.162 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063238.186      0 172.16.1.162 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063238.186      0 172.16.1.162 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063238.191      0 172.16.1.162 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063238.192      0 172.16.1.162 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063238.192      0 172.16.1.162 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063238.192      0 172.16.1.162 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063238.192      0 172.16.1.162 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063238.251      0 172.16.1.162 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063238.288      0 172.16.1.162 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063238.326      0 172.16.1.162 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063238.364      0 172.16.1.162 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063238.490      0 172.16.1.162 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063238.491      0 172.16.1.162 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063238.523      0 172.16.1.162 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063238.524      0 172.16.1.162 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063238.527      0 172.16.1.162 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063238.528      0 172.16.1.162 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063238.528      0 172.16.1.162 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063238.528      0 172.16.1.162 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063238.533      0 172.16.1.162 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063238.699      0 172.16.1.162 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063238.741    151 172.16.1.162 TCP_MISS/302 1334 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25743690312498? - DIRECT/66.235.132.232 text/plain
1287063238.828     78 172.16.1.162 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25743690312498? - DIRECT/66.235.132.232 image/gif
1287063238.906     51 172.16.1.171 TCP_MISS/200 4277 POST http://ps.sd150.org/guardian/home.html - DIRECT/207.63.121.29 text/html
1287063238.956     26 172.16.1.171 TCP_REFRESH_MISS/200 679 GET http://ps.sd150.org/images/alert_other.gif - DIRECT/207.63.121.29 image/gif
1287063243.860    283 172.16.1.163 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063243.905      0 172.16.1.163 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063243.905      0 172.16.1.163 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063243.906      1 172.16.1.163 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063243.907      0 172.16.1.163 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063243.924      0 172.16.1.163 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063243.924      3 172.16.1.163 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063243.941      0 172.16.1.163 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063243.943     38 172.16.1.163 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063243.997      1 172.16.1.163 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063243.998      2 172.16.1.163 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063244.009      0 172.16.1.163 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063244.351      0 172.16.1.163 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063244.352      0 172.16.1.163 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063244.388      0 172.16.1.163 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063244.389      0 172.16.1.163 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063244.389      0 172.16.1.163 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063244.389      0 172.16.1.163 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063244.395      0 172.16.1.163 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063244.395      0 172.16.1.163 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063244.396      0 172.16.1.163 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063244.412      0 172.16.1.163 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063244.412      0 172.16.1.163 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063244.485      0 172.16.1.163 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063244.522      0 172.16.1.163 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063244.561      0 172.16.1.163 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063244.600      0 172.16.1.163 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063244.726      0 172.16.1.163 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063244.726      0 172.16.1.163 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063244.729      0 172.16.1.163 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063244.730      0 172.16.1.163 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063244.730      0 172.16.1.163 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063244.730      0 172.16.1.163 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063244.737      0 172.16.1.163 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063244.846      0 172.16.1.163 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063244.852     71 172.16.1.163 TCP_MISS/302 1334 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23975506012537? - DIRECT/66.235.132.232 text/plain
1287063244.945     82 172.16.1.163 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23975506012537? - DIRECT/66.235.132.232 image/gif
1287063254.716    245 172.16.1.164 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063254.741      0 172.16.1.164 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063254.741      0 172.16.1.164 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063254.741      0 172.16.1.164 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063254.742      2 172.16.1.164 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063254.743      3 172.16.1.164 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063254.771      2 172.16.1.164 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063254.773      0 172.16.1.164 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063254.776     35 172.16.1.164 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063254.807      1 172.16.1.164 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063254.811      1 172.16.1.164 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063254.814      0 172.16.1.164 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063255.145      0 172.16.1.164 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063255.146      0 172.16.1.164 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063255.180      0 172.16.1.164 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063255.180      0 172.16.1.164 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063255.180      0 172.16.1.164 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063255.180      0 172.16.1.164 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063255.186      0 172.16.1.164 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063255.193      0 172.16.1.164 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063255.193      0 172.16.1.164 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063255.223      0 172.16.1.164 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063255.261      0 172.16.1.164 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063255.299      0 172.16.1.164 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063255.337      0 172.16.1.164 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063255.490      0 172.16.1.164 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063255.491      0 172.16.1.164 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063255.529      0 172.16.1.164 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063255.529      0 172.16.1.164 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063255.531      0 172.16.1.164 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063255.531      0 172.16.1.164 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063255.532      0 172.16.1.164 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063255.532      0 172.16.1.164 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063255.540      0 172.16.1.164 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063255.627      0 172.16.1.164 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063255.726    144 172.16.1.164 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s27925738011862? - DIRECT/66.235.133.1 text/plain
1287063255.813     82 172.16.1.164 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s27925738011862? - DIRECT/66.235.133.1 image/gif
1287063259.837    144 172.16.1.165 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063259.959      1 172.16.1.165 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063259.960      0 172.16.1.165 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063259.971      0 172.16.1.165 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063259.978      2 172.16.1.165 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063260.000     25 172.16.1.165 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063260.068      0 172.16.1.165 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063260.073      0 172.16.1.165 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063260.074      0 172.16.1.165 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063260.102      1 172.16.1.165 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063260.108      0 172.16.1.165 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063260.111      2 172.16.1.165 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063260.456      0 172.16.1.165 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063260.456      0 172.16.1.165 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063260.457      0 172.16.1.165 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063260.460      0 172.16.1.165 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063260.462      0 172.16.1.165 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063260.463      0 172.16.1.165 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063260.463      0 172.16.1.165 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063260.464      0 172.16.1.165 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063260.470      0 172.16.1.165 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063260.579      0 172.16.1.165 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063260.701      0 172.16.1.165 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063260.701      0 172.16.1.165 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063260.701      0 172.16.1.165 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063260.702      0 172.16.1.165 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063260.703      0 172.16.1.165 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063260.733      0 172.16.1.165 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063260.799      0 172.16.1.165 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063260.800      0 172.16.1.165 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063260.832      0 172.16.1.165 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063260.832      0 172.16.1.165 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063260.836      0 172.16.1.165 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063260.836      0 172.16.1.165 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063260.846      0 172.16.1.165 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063260.847      0 172.16.1.165 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063260.849      0 172.16.1.165 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063260.849      0 172.16.1.165 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063260.851      0 172.16.1.165 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063260.855      0 172.16.1.165 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063260.855      0 172.16.1.165 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063260.857      0 172.16.1.165 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063260.858      0 172.16.1.165 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063260.945      0 172.16.1.165 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063260.974     86 172.16.1.165 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23504574692269? - DIRECT/66.235.133.1 text/plain
1287063261.095     82 172.16.1.165 TCP_MISS/200 716 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23504574692269? - DIRECT/66.235.133.1 image/gif
1287063261.184    136 172.16.1.165 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23619244997522? - DIRECT/66.235.133.11 image/gif
1287063264.014    199 172.16.1.172 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063264.090      1 172.16.1.172 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063264.091      0 172.16.1.172 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063264.126      0 172.16.1.172 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063264.128      0 172.16.1.172 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063264.132      3 172.16.1.172 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063264.137      0 172.16.1.172 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063264.144      0 172.16.1.172 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063264.160     32 172.16.1.172 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063264.191      1 172.16.1.172 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063264.191      2 172.16.1.172 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063264.205      0 172.16.1.172 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063264.564      0 172.16.1.172 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063264.564      0 172.16.1.172 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063264.601      0 172.16.1.172 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063264.601      0 172.16.1.172 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063264.601      0 172.16.1.172 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063264.601      0 172.16.1.172 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063264.604      0 172.16.1.172 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063264.611      0 172.16.1.172 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063264.611      0 172.16.1.172 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063264.642      0 172.16.1.172 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063264.681      0 172.16.1.172 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063264.720      0 172.16.1.172 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063264.758      0 172.16.1.172 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063264.816    194 172.16.1.166 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063264.865      0 172.16.1.166 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063264.865      1 172.16.1.166 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063264.865      1 172.16.1.166 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063264.867      2 172.16.1.166 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063264.870      1 172.16.1.166 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063264.891      0 172.16.1.166 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063264.894      3 172.16.1.166 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063264.899     35 172.16.1.166 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063264.917      0 172.16.1.172 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063264.917      0 172.16.1.172 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063264.936      1 172.16.1.166 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063264.937      2 172.16.1.166 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063264.939      4 172.16.1.166 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063264.944      0 172.16.1.172 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063264.945      0 172.16.1.172 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063264.945      0 172.16.1.172 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063264.949      0 172.16.1.172 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063264.949      0 172.16.1.172 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063264.949      0 172.16.1.172 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063264.954      0 172.16.1.172 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063265.078      0 172.16.1.172 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063265.095 254589 172.16.0.250 TCP_MISS/200 245629 CONNECT mail.google.com:443 - DIRECT/209.85.225.17 -
1287063265.101     82 172.16.1.172 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s24257972298015? - DIRECT/66.235.133.11 text/plain
1287063265.204     83 172.16.1.172 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s24257972298015? - DIRECT/66.235.133.11 image/gif
1287063265.245      0 172.16.1.166 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063265.245      0 172.16.1.166 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063265.282      0 172.16.1.166 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063265.282      0 172.16.1.166 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063265.282      0 172.16.1.166 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063265.282      0 172.16.1.166 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063265.290      0 172.16.1.166 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063265.290      0 172.16.1.166 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063265.295      0 172.16.1.166 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063265.325      0 172.16.1.166 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063265.364      0 172.16.1.166 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063265.401      0 172.16.1.166 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063265.440      0 172.16.1.166 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063265.594      0 172.16.1.166 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063265.594      0 172.16.1.166 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063265.628      0 172.16.1.166 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063265.628      0 172.16.1.166 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063265.628      0 172.16.1.166 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063265.633      0 172.16.1.166 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063265.634      0 172.16.1.166 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063265.634      0 172.16.1.166 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063265.639      0 172.16.1.166 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063265.772     84 172.16.1.166 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25246483829993? - DIRECT/66.235.133.11 text/plain
1287063265.800      0 172.16.1.166 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063265.860     84 172.16.1.166 TCP_MISS/200 716 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25246483829993? - DIRECT/66.235.133.11 image/gif
1287063270.920    176 172.16.1.173 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063271.009      1 172.16.1.173 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063271.015      0 172.16.1.173 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063271.021      0 172.16.1.173 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063271.033      0 172.16.1.173 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063271.033      0 172.16.1.173 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063271.037      4 172.16.1.173 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063271.070     37 172.16.1.173 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063271.085      0 172.16.1.173 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063271.132      1 172.16.1.173 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063271.134      3 172.16.1.173 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063271.134      3 172.16.1.173 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063271.383      0 172.16.1.173 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063271.384      0 172.16.1.173 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063271.424      0 172.16.1.173 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063271.424      0 172.16.1.173 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063271.424      0 172.16.1.173 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063271.424      0 172.16.1.173 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063271.429      0 172.16.1.173 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063271.433      0 172.16.1.173 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063271.433      0 172.16.1.173 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063271.466      0 172.16.1.173 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063271.505      0 172.16.1.173 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063271.542      0 172.16.1.173 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063271.581      0 172.16.1.173 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063271.736      0 172.16.1.173 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063271.737      0 172.16.1.173 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063271.770      0 172.16.1.173 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063271.770      0 172.16.1.173 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063271.773      0 172.16.1.173 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063271.774      0 172.16.1.173 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063271.776      0 172.16.1.173 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063271.776      0 172.16.1.173 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063271.785      0 172.16.1.173 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063271.927     85 172.16.1.173 TCP_MISS/302 1336 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s29271473113394? - DIRECT/66.235.133.11 text/plain
1287063271.962      0 172.16.1.173 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063272.010     79 172.16.1.173 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s29271473113394? - DIRECT/66.235.133.11 image/gif
1287063272.816    155 172.16.1.167 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063272.917      2 172.16.1.167 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063272.930      0 172.16.1.167 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063272.933      0 172.16.1.167 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063272.946      0 172.16.1.167 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063272.946      0 172.16.1.167 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063272.946      4 172.16.1.167 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063272.956      0 172.16.1.167 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063272.964     28 172.16.1.167 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063272.996      0 172.16.1.167 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063272.996      1 172.16.1.167 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063273.000      5 172.16.1.167 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063273.348      0 172.16.1.167 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063273.349      0 172.16.1.167 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063273.407      0 172.16.1.167 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063273.407      0 172.16.1.167 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063273.408      0 172.16.1.167 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063273.408      0 172.16.1.167 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063273.415      0 172.16.1.167 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063273.420      0 172.16.1.167 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063273.420      0 172.16.1.167 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063273.450      0 172.16.1.167 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063273.488      0 172.16.1.167 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063273.525      0 172.16.1.167 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063273.563      0 172.16.1.167 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063273.721      0 172.16.1.167 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063273.722      0 172.16.1.167 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063273.749      0 172.16.1.167 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063273.749      0 172.16.1.167 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063273.751      0 172.16.1.167 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063273.753      0 172.16.1.167 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063273.754      0 172.16.1.167 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063273.754      0 172.16.1.167 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063273.760      0 172.16.1.167 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063273.856      0 172.16.1.167 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063273.896     85 172.16.1.167 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25905059461507? - DIRECT/66.235.133.11 text/plain
1287063273.985     84 172.16.1.167 TCP_MISS/200 716 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25905059461507? - DIRECT/66.235.133.11 image/gif
1287063274.753      0 172.16.1.171 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063274.753      0 172.16.1.171 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063274.753      0 172.16.1.171 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063274.753      0 172.16.1.171 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063274.755      2 172.16.1.171 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063274.771      3 172.16.1.171 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063274.775    189 172.16.1.171 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063274.787     30 172.16.1.171 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063274.795      0 172.16.1.171 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063274.797      2 172.16.1.171 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063274.829      0 172.16.1.171 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063274.848      0 172.16.1.171 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063275.042      0 172.16.1.171 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063275.043      0 172.16.1.171 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063275.082      0 172.16.1.171 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063275.083      0 172.16.1.171 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063275.083      0 172.16.1.171 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063275.084      0 172.16.1.171 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063275.084      0 172.16.1.171 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063275.084      0 172.16.1.171 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063275.085      0 172.16.1.171 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063275.129      0 172.16.1.171 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063275.167      0 172.16.1.171 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063275.205      0 172.16.1.171 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063275.242      0 172.16.1.171 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063275.393      0 172.16.1.171 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063275.393      0 172.16.1.171 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063275.397      0 172.16.1.171 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063275.397      0 172.16.1.171 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063275.397      0 172.16.1.171 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063275.397      0 172.16.1.171 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063275.404      0 172.16.1.171 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063275.405      0 172.16.1.171 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063275.405      0 172.16.1.171 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063275.563     93 172.16.1.171 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21996430395222? - DIRECT/66.235.133.11 text/plain
1287063275.577      0 172.16.1.171 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063275.646     79 172.16.1.171 TCP_MISS/200 716 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21996430395222? - DIRECT/66.235.133.11 image/gif
1287063281.782    160 172.16.1.169 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063281.854      1 172.16.1.169 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063281.855      0 172.16.1.169 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063281.856      0 172.16.1.169 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063281.873      2 172.16.1.169 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063281.875      0 172.16.1.169 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063281.904     35 172.16.1.169 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063281.940      0 172.16.1.169 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063281.944      0 172.16.1.169 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063281.953      0 172.16.1.169 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063281.954      1 172.16.1.169 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063281.957      4 172.16.1.169 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063282.248      0 172.16.1.169 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063282.248      0 172.16.1.169 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063282.286      0 172.16.1.169 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063282.286      0 172.16.1.169 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063282.286      0 172.16.1.169 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063282.286      0 172.16.1.169 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063282.292      0 172.16.1.169 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063282.299      0 172.16.1.169 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063282.299      0 172.16.1.169 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063282.329      0 172.16.1.169 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063282.366      0 172.16.1.169 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063282.405      0 172.16.1.169 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063282.443      0 172.16.1.169 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063282.604      0 172.16.1.169 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063282.604      0 172.16.1.169 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063282.633      0 172.16.1.169 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063282.633      0 172.16.1.169 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063282.637      0 172.16.1.169 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063282.638      0 172.16.1.169 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063282.638      0 172.16.1.169 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063282.638      0 172.16.1.169 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063282.643      0 172.16.1.169 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063282.769     79 172.16.1.169 TCP_MISS/302 1336 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26291646119153? - DIRECT/66.235.133.11 text/plain
1287063282.815      0 172.16.1.169 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063282.852     79 172.16.1.169 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26291646119153? - DIRECT/66.235.133.11 image/gif
1287063285.110    213 172.16.1.228 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063285.166      0 172.16.1.228 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063285.166      0 172.16.1.228 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063285.166      0 172.16.1.228 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063285.169      3 172.16.1.228 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063285.172      6 172.16.1.228 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063285.187      0 172.16.1.228 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063285.191     25 172.16.1.228 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063285.234      0 172.16.1.228 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063285.251      1 172.16.1.228 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063285.259      0 172.16.1.228 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063285.270      0 172.16.1.228 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063285.538      0 172.16.1.228 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063285.538      0 172.16.1.228 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063285.576      0 172.16.1.228 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063285.577      0 172.16.1.228 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063285.577      0 172.16.1.228 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063285.577      0 172.16.1.228 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063285.578      0 172.16.1.228 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063285.579      0 172.16.1.228 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063285.579      0 172.16.1.228 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063285.621      0 172.16.1.228 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063285.659      0 172.16.1.228 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063285.698      0 172.16.1.228 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063285.736      0 172.16.1.228 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063285.903      0 172.16.1.228 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063285.904      0 172.16.1.228 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063285.932      0 172.16.1.228 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063285.932      0 172.16.1.228 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063285.935      0 172.16.1.228 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063285.935      0 172.16.1.228 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063285.935      0 172.16.1.228 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063285.935      0 172.16.1.228 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063285.945      0 172.16.1.228 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063286.074     81 172.16.1.228 TCP_MISS/302 1336 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25213673262513? - DIRECT/66.235.133.11 text/plain
1287063286.111      0 172.16.1.228 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063286.165     80 172.16.1.228 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25213673262513? - DIRECT/66.235.133.11 image/gif
1287063288.538    136 172.16.1.229 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063288.675      0 172.16.1.229 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063288.675      0 172.16.1.229 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063288.676      0 172.16.1.229 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063288.677      2 172.16.1.229 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063288.682      6 172.16.1.229 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063288.694      0 172.16.1.229 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063288.709      1 172.16.1.229 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063288.713     38 172.16.1.229 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063288.751      1 172.16.1.229 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063288.754      1 172.16.1.229 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063288.755      0 172.16.1.229 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063289.057      0 172.16.1.229 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063289.057      0 172.16.1.229 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063289.102      0 172.16.1.229 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063289.102      0 172.16.1.229 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063289.102      0 172.16.1.229 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063289.102      0 172.16.1.229 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063289.105      0 172.16.1.229 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063289.115      0 172.16.1.229 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063289.115      0 172.16.1.229 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063289.145      0 172.16.1.229 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063289.183      0 172.16.1.229 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063289.222      0 172.16.1.229 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063289.260      0 172.16.1.229 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063289.420      0 172.16.1.229 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063289.420      0 172.16.1.229 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063289.450      0 172.16.1.229 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063289.450      0 172.16.1.229 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063289.453      0 172.16.1.229 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063289.453      0 172.16.1.229 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063289.454      0 172.16.1.229 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063289.454      0 172.16.1.229 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063289.461      0 172.16.1.229 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063289.578     70 172.16.1.229 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22869974201158? - DIRECT/66.235.133.11 text/plain
1287063289.626      0 172.16.1.229 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063289.674     92 172.16.1.229 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22869974201158? - DIRECT/66.235.133.11 image/gif
1287063293.675    209 172.16.1.230 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063293.783      0 172.16.1.230 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063293.784      1 172.16.1.230 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063293.798      0 172.16.1.230 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063293.804      0 172.16.1.230 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063293.807      3 172.16.1.230 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063293.832     32 172.16.1.230 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063293.842      0 172.16.1.230 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063293.846      0 172.16.1.230 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063293.856      1 172.16.1.230 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063293.859      3 172.16.1.230 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063293.898      0 172.16.1.230 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063294.158      0 172.16.1.230 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063294.159      0 172.16.1.230 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063294.191      0 172.16.1.230 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063294.191      0 172.16.1.230 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063294.192      0 172.16.1.230 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063294.192      0 172.16.1.230 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063294.196      0 172.16.1.230 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063294.201      0 172.16.1.230 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063294.201      0 172.16.1.230 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063294.234      0 172.16.1.230 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063294.273      0 172.16.1.230 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063294.312      0 172.16.1.230 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063294.350      0 172.16.1.230 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063294.512      0 172.16.1.230 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063294.513      0 172.16.1.230 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063294.543      0 172.16.1.230 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063294.543      0 172.16.1.230 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063294.545      0 172.16.1.230 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063294.548      0 172.16.1.230 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063294.548      0 172.16.1.230 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063294.548      0 172.16.1.230 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063294.558      0 172.16.1.230 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063294.635      0 172.16.1.230 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063294.658     70 172.16.1.230 TCP_MISS/302 1336 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s24020899344824? - DIRECT/66.235.133.11 text/plain
1287063294.760     82 172.16.1.230 TCP_MISS/200 716 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s24020899344824? - DIRECT/66.235.133.11 image/gif
1287063296.626    212 172.16.1.231 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063296.656      0 172.16.1.231 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063296.657      0 172.16.1.231 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063296.658      1 172.16.1.231 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063296.676      0 172.16.1.231 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063296.679      3 172.16.1.231 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063296.691      0 172.16.1.231 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063296.692      0 172.16.1.231 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063296.711     35 172.16.1.231 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063296.756      0 172.16.1.231 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063296.760      4 172.16.1.231 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063296.777      0 172.16.1.231 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063297.020      0 172.16.1.231 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063297.021      0 172.16.1.231 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063297.060      0 172.16.1.231 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063297.061      0 172.16.1.231 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063297.061      0 172.16.1.231 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063297.061      0 172.16.1.231 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063297.068      0 172.16.1.231 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063297.068      0 172.16.1.231 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063297.073      0 172.16.1.231 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063297.105      0 172.16.1.231 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063297.146      0 172.16.1.231 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063297.185      0 172.16.1.231 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063297.221      0 172.16.1.231 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063297.391      0 172.16.1.231 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063297.391      0 172.16.1.231 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063297.422      0 172.16.1.231 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063297.422      0 172.16.1.231 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063297.424      0 172.16.1.231 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063297.425      0 172.16.1.231 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063297.425      0 172.16.1.231 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063297.425      0 172.16.1.231 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063297.430      0 172.16.1.231 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063297.568     88 172.16.1.231 TCP_MISS/302 1336 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21327049256569? - DIRECT/66.235.133.11 text/plain
1287063297.629      0 172.16.1.231 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063297.676     81 172.16.1.231 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21327049256569? - DIRECT/66.235.133.11 image/gif
1287063299.708    211 172.16.1.232 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063299.799      0 172.16.1.232 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063299.801      1 172.16.1.232 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063299.801      0 172.16.1.232 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063299.812      0 172.16.1.232 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063299.815      3 172.16.1.232 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063299.839      0 172.16.1.232 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063299.839      0 172.16.1.232 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063299.849     37 172.16.1.232 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063299.894      1 172.16.1.232 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063299.904      1 172.16.1.232 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063299.914      0 172.16.1.232 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063300.165      0 172.16.1.232 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063300.165      0 172.16.1.232 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063300.204      0 172.16.1.232 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063300.204      0 172.16.1.232 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063300.204      0 172.16.1.232 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063300.204      0 172.16.1.232 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063300.206      0 172.16.1.232 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063300.213      0 172.16.1.232 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063300.213      0 172.16.1.232 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063300.249      0 172.16.1.232 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063300.287      0 172.16.1.232 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063300.325      0 172.16.1.232 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063300.363      0 172.16.1.232 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063300.525      0 172.16.1.232 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063300.525      0 172.16.1.232 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063300.556      0 172.16.1.232 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063300.556      0 172.16.1.232 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063300.559      0 172.16.1.232 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063300.559      0 172.16.1.232 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063300.559      0 172.16.1.232 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063300.559      0 172.16.1.232 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063300.563      0 172.16.1.232 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063300.695     88 172.16.1.232 TCP_MISS/302 1334 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21909122828843? - DIRECT/66.235.133.11 text/plain
1287063300.752      0 172.16.1.232 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063300.773     74 172.16.1.232 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21909122828843? - DIRECT/66.235.133.11 image/gif
1287063303.538    169 172.16.1.233 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063303.641      0 172.16.1.233 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063303.641      0 172.16.1.233 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063303.641      0 172.16.1.233 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063303.643      2 172.16.1.233 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063303.644      2 172.16.1.233 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063303.673      0 172.16.1.233 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063303.676      3 172.16.1.233 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063303.678     37 172.16.1.233 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063303.717      0 172.16.1.233 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063303.717      1 172.16.1.233 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063303.721      5 172.16.1.233 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063304.039      0 172.16.1.233 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063304.040      0 172.16.1.233 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063304.092      0 172.16.1.233 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063304.092      0 172.16.1.233 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063304.093      0 172.16.1.233 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063304.094      0 172.16.1.233 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063304.095      0 172.16.1.233 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063304.099      0 172.16.1.233 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063304.099      0 172.16.1.233 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063304.138      0 172.16.1.233 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063304.177      0 172.16.1.233 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063304.215      0 172.16.1.233 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063304.253      0 172.16.1.233 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063304.416      0 172.16.1.233 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063304.416      0 172.16.1.233 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063304.447      0 172.16.1.233 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063304.448      0 172.16.1.233 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063304.449      0 172.16.1.233 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063304.451      0 172.16.1.233 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063304.452      0 172.16.1.233 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063304.452      0 172.16.1.233 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063304.462      0 172.16.1.233 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063304.568      0 172.16.1.233 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063304.579     82 172.16.1.233 TCP_MISS/302 1334 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s28430864401465? - DIRECT/66.235.133.11 text/plain
1287063304.663     79 172.16.1.233 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s28430864401465? - DIRECT/66.235.133.11 image/gif
1287063306.598    156 172.16.1.234 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063306.704      0 172.16.1.234 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063306.705      1 172.16.1.234 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063306.741      0 172.16.1.234 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063306.769      0 172.16.1.234 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063306.771      2 172.16.1.234 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063306.774      5 172.16.1.234 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063306.804     37 172.16.1.234 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063306.815      0 172.16.1.234 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063306.816      0 172.16.1.234 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063306.823      0 172.16.1.234 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063306.827      3 172.16.1.234 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063307.135      0 172.16.1.234 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063307.135      0 172.16.1.234 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063307.188      0 172.16.1.234 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063307.188      0 172.16.1.234 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063307.188      0 172.16.1.234 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063307.188      0 172.16.1.234 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063307.193      0 172.16.1.234 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063307.198      0 172.16.1.234 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063307.198      0 172.16.1.234 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063307.246      0 172.16.1.234 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063307.284      0 172.16.1.234 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063307.323      0 172.16.1.234 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063307.362      0 172.16.1.234 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063307.519      0 172.16.1.234 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063307.519      0 172.16.1.234 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063307.555      0 172.16.1.234 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063307.555      0 172.16.1.234 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063307.558      0 172.16.1.234 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063307.558      0 172.16.1.234 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063307.558      0 172.16.1.234 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063307.561      0 172.16.1.234 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063307.564      0 172.16.1.234 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063307.682     71 172.16.1.234 TCP_MISS/302 1334 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23418664428453? - DIRECT/66.235.133.11 text/plain
1287063307.722      0 172.16.1.234 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063307.765     79 172.16.1.234 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23418664428453? - DIRECT/66.235.133.11 image/gif
1287063309.783    272 172.16.1.235 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063309.880      1 172.16.1.235 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063309.888      0 172.16.1.235 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063309.898      0 172.16.1.235 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063309.902      0 172.16.1.235 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063309.904      1 172.16.1.235 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063309.908      5 172.16.1.235 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063309.929     27 172.16.1.235 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063309.951      0 172.16.1.235 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063309.957      0 172.16.1.235 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063309.958      1 172.16.1.235 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063309.959      2 172.16.1.235 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063310.278      0 172.16.1.235 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063310.279      0 172.16.1.235 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063310.312      0 172.16.1.235 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063310.312      0 172.16.1.235 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063310.312      0 172.16.1.235 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063310.312      0 172.16.1.235 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063310.313      0 172.16.1.235 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063310.313      0 172.16.1.235 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063310.313      0 172.16.1.235 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063310.358      0 172.16.1.235 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063310.396      0 172.16.1.235 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063310.442      0 172.16.1.235 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063310.480      0 172.16.1.235 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063310.600      0 172.16.1.235 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063310.600      0 172.16.1.235 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063310.629      0 172.16.1.235 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063310.629      0 172.16.1.235 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063310.631      0 172.16.1.235 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063310.632      0 172.16.1.235 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063310.632      0 172.16.1.235 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063310.633      0 172.16.1.235 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063310.638      0 172.16.1.235 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063310.781     86 172.16.1.235 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26945053934624? - DIRECT/66.235.133.11 text/plain
1287063310.808      0 172.16.1.235 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063310.871     83 172.16.1.235 TCP_MISS/200 716 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26945053934624? - DIRECT/66.235.133.11 image/gif
1287063314.943    209 172.16.1.236 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063314.968      0 172.16.1.236 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063314.969      1 172.16.1.236 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063314.982      0 172.16.1.236 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063314.997      0 172.16.1.236 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063315.001      4 172.16.1.236 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063315.005      0 172.16.1.236 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063315.012      0 172.16.1.236 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063315.029     33 172.16.1.236 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063315.047      0 172.16.1.236 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063315.052      4 172.16.1.236 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063315.082      0 172.16.1.236 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063315.352      0 172.16.1.236 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063315.352      0 172.16.1.236 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063315.386      0 172.16.1.236 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063315.386      0 172.16.1.236 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063315.386      0 172.16.1.236 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063315.389      0 172.16.1.236 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063315.391      0 172.16.1.236 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063315.393      0 172.16.1.236 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063315.393      0 172.16.1.236 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063315.414      0 172.16.1.236 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063315.414      0 172.16.1.236 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063315.497      0 172.16.1.236 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063315.535      0 172.16.1.236 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063315.573      0 172.16.1.236 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063315.612      0 172.16.1.236 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063315.742      0 172.16.1.236 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063315.742      0 172.16.1.236 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063315.745      0 172.16.1.236 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063315.745      0 172.16.1.236 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063315.745      0 172.16.1.236 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063315.746      0 172.16.1.236 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063315.756      0 172.16.1.236 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063315.875     72 172.16.1.236 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26971927629113? - DIRECT/66.235.133.11 text/plain
1287063315.920      0 172.16.1.236 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063315.960     82 172.16.1.236 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26971927629113? - DIRECT/66.235.133.11 image/gif
1287063318.638 304628 172.16.0.250 TCP_MISS/200 212689 CONNECT mail.google.com:443 - DIRECT/209.85.225.18 -
1287063318.638 335109 172.16.0.250 TCP_MISS/200 444207 CONNECT mail.google.com:443 - DIRECT/209.85.225.19 -
1287063318.639 334776 172.16.0.250 TCP_MISS/200 149439 CONNECT mail.google.com:443 - DIRECT/209.85.225.83 -
1287063318.985    169 172.16.1.237 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063319.058      2 172.16.1.237 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063319.060      0 172.16.1.237 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063319.080      0 172.16.1.237 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063319.082      0 172.16.1.237 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063319.090      7 172.16.1.237 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063319.093     10 172.16.1.237 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063319.110      0 172.16.1.237 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063319.113     32 172.16.1.237 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063319.165      0 172.16.1.237 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063319.174      9 172.16.1.237 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063319.174      4 172.16.1.237 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063319.434      0 172.16.1.237 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063319.435      0 172.16.1.237 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063319.475      0 172.16.1.237 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063319.475      0 172.16.1.237 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063319.476      0 172.16.1.237 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063319.476      0 172.16.1.237 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063319.481      0 172.16.1.237 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063319.482      0 172.16.1.237 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063319.486      0 172.16.1.237 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063319.524      0 172.16.1.237 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063319.562      0 172.16.1.237 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063319.600      0 172.16.1.237 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063319.638      0 172.16.1.237 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063319.782      0 172.16.1.237 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063319.783      0 172.16.1.237 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063319.805      0 172.16.1.237 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063319.805      0 172.16.1.237 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063319.808      0 172.16.1.237 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063319.808      0 172.16.1.237 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063319.810      0 172.16.1.237 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063319.813      0 172.16.1.237 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063319.816      0 172.16.1.237 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063319.935     83 172.16.1.237 TCP_MISS/302 1335 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22782826941265? - DIRECT/66.235.133.11 text/plain
1287063319.970      0 172.16.1.237 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063320.029     84 172.16.1.237 TCP_MISS/200 716 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22782826941265? - DIRECT/66.235.133.11 image/gif
1287063324.842    123 172.16.1.238 TCP_MISS/200 18361 GET http://assignments.discoveryeducation.com/ - DIRECT/199.199.210.28 text/html
1287063324.935      2 172.16.1.238 TCP_HIT/200 30714 GET http://assignments.discoveryeducation.com/css/main.css - NONE/- text/css
1287063324.943      0 172.16.1.238 TCP_HIT/200 1359 GET http://assignments.discoveryeducation.com/css/global.css - NONE/- text/css
1287063324.950      0 172.16.1.238 TCP_HIT/200 1524 GET http://assignments.discoveryeducation.com/js/ajax.js - NONE/- application/javascript
1287063324.960      0 172.16.1.238 TCP_HIT/200 2176 GET http://assignments.discoveryeducation.com/css/pz-login-buttons.css - NONE/- text/css
1287063324.960      0 172.16.1.238 TCP_HIT/200 6797 GET http://static.discoveryeducation.com/global/js/wddx.js - NONE/- application/x-javascript
1287063324.969      9 172.16.1.238 TCP_HIT/200 72078 GET http://static.discoveryeducation.com/global/js/de-global-lib-rel4.js - NONE/- application/x-javascript
1287063324.994     36 172.16.1.238 TCP_REFRESH_HIT/200 12954 GET http://static.discoveryeducation.com/global/css/style-rel5.css? - DIRECT/199.199.210.14 text/css
1287063324.996      0 172.16.1.238 TCP_HIT/200 36769 GET http://assignments.discoveryeducation.com/js/engine.js - NONE/- application/javascript
1287063325.001      6 172.16.1.238 TCP_HIT/200 20617 GET http://ws.discoveryeducation.com/common/javascript/s_code_edu_tools.js - NONE/- application/x-javascript
1287063325.008      2 172.16.1.238 TCP_HIT/200 23414 GET http://assignments.discoveryeducation.com/js/wddx.js - NONE/- application/javascript
1287063325.038      2 172.16.1.238 TCP_HIT/200 39219 GET http://assignments.discoveryeducation.com/js/util.js - NONE/- application/javascript
1287063325.317      0 172.16.1.238 TCP_HIT/200 3070 GET http://static.discoveryeducation.com/global/images/de-header-nav-els.jpg - NONE/- image/jpeg
1287063325.317      0 172.16.1.238 TCP_HIT/200 5070 GET http://static.discoveryeducation.com/www/img/header/de-logo-new.png - NONE/- image/png
1287063325.364      0 172.16.1.238 TCP_HIT/200 525 GET http://assignments.discoveryeducation.com/images/spacer.gif - NONE/- image/gif
1287063325.364      0 172.16.1.238 TCP_HIT/200 591 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topleft.gif - NONE/- image/gif
1287063325.364      0 172.16.1.238 TCP_HIT/200 589 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_topright.gif - NONE/- image/gif
1287063325.364      0 172.16.1.238 TCP_HIT/200 2223 GET http://assignments.discoveryeducation.com/images/ajax-waitRed.gif - NONE/- image/gif
1287063325.376      0 172.16.1.238 TCP_HIT/200 582 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomright.gif - NONE/- image/gif
1287063325.377      0 172.16.1.238 TCP_HIT/200 580 GET http://assignments.discoveryeducation.com/images/colorBox/red/cap_bottomleft.gif - NONE/- image/gif
1287063325.377      0 172.16.1.238 TCP_HIT/200 2718 GET http://assignments.discoveryeducation.com/images/goRed.jpg - NONE/- image/jpeg
1287063325.405      0 172.16.1.238 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063325.444      0 172.16.1.238 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063325.482      0 172.16.1.238 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063325.519      0 172.16.1.238 TCP_HIT/200 389 GET http://static.discoveryeducation.com/blank/blank.html - NONE/- text/html
1287063325.678      0 172.16.1.238 TCP_HIT/200 592 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_top.gif - NONE/- image/gif
1287063325.678      0 172.16.1.238 TCP_HIT/200 570 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_left.gif - NONE/- image/gif
1287063325.756      0 172.16.1.238 TCP_HIT/200 578 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_right.gif - NONE/- image/gif
1287063325.756      0 172.16.1.238 TCP_HIT/200 551 GET http://assignments.discoveryeducation.com/images/colorBox/red/background_bottom.gif - NONE/- image/gif
1287063325.766      0 172.16.1.238 TCP_HIT/200 3708 GET http://assignments.discoveryeducation.com/images/progresszone/btn-benchmark.gif - NONE/- image/gif
1287063325.766      0 172.16.1.238 TCP_HIT/200 3707 GET http://assignments.discoveryeducation.com/images/progresszone/btn-indicator.gif - NONE/- image/gif
1287063325.766      0 172.16.1.238 TCP_HIT/200 3225 GET http://assignments.discoveryeducation.com/images/progresszone/btn-pz.gif - NONE/- image/gif
1287063325.769      0 172.16.1.238 TCP_HIT/200 3705 GET http://assignments.discoveryeducation.com/images/progresszone/btn-rti.gif - NONE/- image/gif
1287063325.777      0 172.16.1.238 TCP_HIT/200 4017 GET http://static.discoveryeducation.com/global/images/logo-black/hub.png - NONE/- image/png
1287063325.919     87 172.16.1.238 TCP_MISS/302 1336 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23395962174461? - DIRECT/66.235.133.11 text/plain
1287063325.964      0 172.16.1.238 TCP_HIT/200 2727 GET http://assignments.discoveryeducation.com/favicon.ico - NONE/- image/x-icon
1287063326.000     76 172.16.1.238 TCP_MISS/200 715 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23395962174461? - DIRECT/66.235.133.11 image/gif
1287063415.785    107 172.16.0.250 TCP_MISS/200 2226 POST http://ocsp.verisign.com/ - DIRECT/199.7.59.72 application/ocsp-response
1287063416.116    272 172.16.0.250 TCP_MISS/200 1981 POST http://evsecure-ocsp.verisign.com/ - DIRECT/199.7.52.72 application/ocsp-response
1287063416.192    734 172.16.0.250 TCP_MISS/200 2914 CONNECT versioncheck.addons.mozilla.org:443 - DIRECT/63.245.209.92 -
1287063416.195    738 172.16.0.250 TCP_MISS/200 2914 CONNECT versioncheck.addons.mozilla.org:443 - DIRECT/63.245.209.92 -
1287063416.230    766 172.16.0.250 TCP_MISS/200 2914 CONNECT versioncheck.addons.mozilla.org:443 - DIRECT/63.245.209.92 -
1287063416.233    770 172.16.0.250 TCP_MISS/200 2914 CONNECT versioncheck.addons.mozilla.org:443 - DIRECT/63.245.209.92 -
1287063416.237    775 172.16.0.250 TCP_MISS/200 2914 CONNECT versioncheck.addons.mozilla.org:443 - DIRECT/63.245.209.92 -
1287063416.240    780 172.16.0.250 TCP_MISS/200 2914 CONNECT versioncheck.addons.mozilla.org:443 - DIRECT/63.245.209.92 -
1287063416.356    232 172.16.0.250 TCP_MISS/200 1771 CONNECT versioncheck.addons.mozilla.org:443 - DIRECT/63.245.209.92 -
1287063416.364    240 172.16.0.250 TCP_MISS/200 2865 CONNECT versioncheck.addons.mozilla.org:443 - DIRECT/63.245.209.92 -
1287063416.418    224 172.16.0.250 TCP_MISS/200 1760 CONNECT versioncheck.addons.mozilla.org:443 - DIRECT/63.245.209.92 -
1287063423.173   7758 172.16.0.250 TCP_MISS/200 10494 CONNECT addons.mozilla.org:443 - DIRECT/63.245.217.40 -
1287063429.264  13770 172.16.0.250 TCP_MISS/200 2694 CONNECT aus2.mozilla.org:443 - DIRECT/63.245.209.105 -
1287063492.277 470621 172.16.0.250 TCP_MISS/200 52802 CONNECT mail.google.com:443 - DIRECT/209.85.225.19 -

```

store.log

```
1287062829.875 SWAPOUT 00 00009459 BCEBBC85041E4D7B08C10D687E78F042  200 1287055345 1287052955 1602415345 image/jpeg 1635/1635 GET http://l1.yimg.com/a/i/ww/news/2010/10/14/chile2-sm.jpg
1287062829.992 RELEASE -1 FFFFFFFF 8DFE0521FBB309A411D212BAC5C95EA8  200 1287062818 1287062818        -1 image/gif 43/43 GET http://ad.yieldmanager.com/pixel?id=677524&t=2
1287062830.098 SWAPOUT 00 0000945A 155738E71C9218664ECE2BDB3E7101D4  200 1287060256 1287057157 1602420256 image/jpeg 2670/2670 GET http://l1.yimg.com/a/i/ww/news/2010/10/14/101410medicare-sm.jpg
1287062830.494 SWAPOUT 00 0000945C F4AB1B124ECBC666E242ACE968A5BA69  200 1287001145 1286999577 1602361145 image/jpeg 5666/5666 GET http://l1.yimg.com/a/i/ww/news/2010/10/13/jolie2-sm.jpg
1287062830.577 SWAPOUT 00 0000945D B34F03D44F4D12D2BF265D5DA006023E  200 1287025233 1287011590 1602385233 image/jpeg 1895/1895 GET http://l.yimg.com/a/i/ww/news/2010/10/13/hilaryswank_vmsm.jpg
1287062830.794 RELEASE -1 FFFFFFFF B2DAD4440677BB4D4A886B368B7A883B  200 1287062818        -1        -1 text/html -1/43077 GET http://www.yahoo.com/
1287062831.051 RELEASE -1 FFFFFFFF A6FA650C35A444CB722E8224214AA70C  200 1287062819        -1        -1 image/gif -1/43 GET http://us.bc.yahoo.com/b?P=AtrZikPDoElhyoPKz0btjwuUzz95HEy3BSIAAM4r&T=17v5pnmgd%2fX%3d1287062818%2fE%3d2023538075%2fR%3dyahoo_top%2fK%3d5%2fV%3d1.1%2fW%3dJ%2fY%3dYAHOO%2fF%3d3924018594%2fH%3dc2VydmVJZD0iQXRyWmlrUERvRWxoeW9QS3owYnRqd3VVeno5NUhFeTNCU0lBQU00ciIgc2l0ZUlkPSI0NDUyMDUxIiB0U3RtcD0iMTI4NzA2MjgxODE0MzQ0OCIg%2fS%3d1%2fJ%3d474F8862&U=12dcmd95h%2fN%3daOOlAEwNPK0-%2fC%3d-1%2fD%3dRSCH1%2fB%3d-1%2fV%3d0&U=13fav11hd%2fN%3dZuOlAEwNPK0-%2fC%3d749251.14302047.14217523.12518940%2fD%3dQL2%2fB%3d6189756%2fV%3d1&U=13gf5rmtm%2fN%3dauOlAEwNPK0-%2fC%3d757168.14056051.14000177.12829484%2fD%3dSTCK%2fB%3d5955130%2fV%3d1&U=13hnvac1v%2fN%3dZOOlAEwNPK0-%2fC%3d781086.14319545.14230151.12933099%2fD%3dPROMO%2fB%3d6158531%2fV%3d1&U=13ft7igmq%2fN%3da.OlAEwNPK0-%2fC%3d767715.14395970.14254223.13260325%2fD%3dTL1%2fB%3d6144542%2fV%3d1&U=13fel8uq1%2fN%3dbOOlAEwNPK0-%2fC%3d784090.14373876.14242029.13674767%2fD%3dTL2%2fB%3d6223822%2fV%3d1&U=13gflmvdr%2fN%3dYuOlAEwNPK0-%2fC%3d774443.14377336.14247216.12606351%2fD%3dFPAD%2fB%3d6227848%2fV%3d1&U=13h5tp9o8%2fN%3dYOOlAEwNPK0-%2fC%3d637076.14362684.14225598.12816525%2fD%3dCRSL2%2fB%3d6046410%2fV%3d1&U=12de63nh0%2fN%3dY.OlAEwNPK0-%2fC%3d-1%2fD%3dHDLN2%2fB%3d-1%2fV%3d0&U=12dvh5o1u%2fN%3dX.OlAEwNPK0-%2fC%3d-2%2fD%3dADBCN%2fB%3d-2%2fV%3d0&Q=0&O=0.5562060354216712
1287062831.106 SWAPOUT 00 0000945F F25167C5F365432DC5375E0469574684  200 1287010892 1287008709 1602370892 image/jpeg 3268/3268 GET http://l.yimg.com/a/i/vm/2010oct/vm_timgunn-sm.jpg
1287062831.455 SWAPOUT 00 0000945B 83DD2F864522179C661FC266ADA89D3D  200 1287055344 1287052955 1602415344 image/jpeg 15986/15986 GET http://l1.yimg.com/a/i/ww/news/2010/10/14/chile2.jpg
1287062831.497 SWAPOUT 00 0000945E A6089B3451A9572BEE9C946CD1A54302  200 1287057633 1287013023 1602417633 image/jpeg 11950/11950 GET http://l.yimg.com/a/i/ww/news/2010/10/13/lostdog_split_lg.jpg
1287062831.611 RELEASE -1 FFFFFFFF 08823CD70FE4943321A9F1B02D6565E1  200 1287062820 1287062820        -1 image/gif 43/43 GET http://ad.yieldmanager.com/pixel?id=1019501&t=2
1287062831.630 SWAPOUT 00 00009460 57F5B74ABE9AD2607369FA4D10B2E96C  200 1287062820 1209757867        -1 image/gif 43/43 GET http://srd.yahoo.com/M=774443.14377336.14247216.12606351/D=yahoo_top/S=2023538075:FPAD/_ylt=A2KIT0ciBbdMh1UBLDKbvZx4/Y=YAHOO/EXP=1287070018/L=AtrZikPDoElhyoPKz0btjwuUzz95HEy3BSIAAM4r/B=YuOlAEwNPK0-/J=1287062818153999/K=KbbgbqAD51iK60L0cAqBXA/A=6227848/N=3110/id=load_nocap/fv=10/0.7983530027914334/*1
1287062831.852 SWAPOUT 00 00009461 7DC7572B7EEE9C169467C8B510A52B7E  200 1287032894 1287032068 1854680894 data 3422/3422 GET http://l.yimg.com/cv/eng/honda/101014/e/shell.swf
1287062832.634 RELEASE -1 FFFFFFFF C7AF7C4BAC58CE17317EEC279BF7E66A  200 1287062820        -1 1287062820 image/gif 43/43 GET http://amch.questionmarket.com/adsc/d767732/124/790749/adscout.php?ord=1287062818153999
1287062833.022 SWAPOUT 00 00009463 B0017CCF28B1814C4F2ABFC500A8884E  200 1287016819 1287016709 1854664819 image/gif 551/551 GET http://l.yimg.com/cv/ae/us/auto_test/101013/55x30wcdjsoiy6.gif
1287062833.300 RELEASE -1 FFFFFFFF 5AEA1BDD48AD971F3DC122C2E0214C84  302 1287062819        -1        -1 text/html 0/0 GET http://ad.wsod.com/embed/8bec9b10877d5d7fd7c0fb6e6a631357/569.198.tk.120x30/1287062818153999
1287062833.406 RELEASE -1 FFFFFFFF 8F1548752B46E7C7D05D570275150BF5  204 1287062822        -1 766368000 text/plain 0/0 GET http://www.yahoo.com/p.gif;_ylp=A2KIT0ciBbdMh1UBIzKbvZx4?t=1287062819948&hpset=1
1287062833.459 RELEASE -1 FFFFFFFF A313AC96D829E1A75F27C14E61367620  200 1287062822 1285382028 1292246822 image/x-icon 318/318 GET http://www.yahoo.com/favicon.ico
1287062833.967 SWAPOUT 00 00009462 49785E24D55279D0C689D3C9F854BD23  200 1287032894 1287032070 1854680894 data 51711/51711 GET http://l.yimg.com/cv/eng/honda/101014/e/sub.swf
1287062838.139 RELEASE -1 FFFFFFFF 12681AC0958E338146EB60C01D78A394  204 1287062827        -1 766368000 text/plain 0/0 GET http://www.yahoo.com/p.gif;_ylt=A2KIT0ciBbdMh1UBrTKbvZx4;_ylu=X3oDMTNnYXNyMXE1BGEDMTAxMDEyIG5ld3MgYmxvZyBoYXBweSBtZWFsIHByb2plY3QgdARjcG9zAzMEZwNpZC00NDAwMwRpbnRsA3VzBHBrZ3YDMjQEc2VjA3RkLWZlYXQEc2xrA3RodW1iBHNscG9zA0YEdGVzdAM3MDE-?t=1287062824673
1287062838.179 RELEASE -1 FFFFFFFF 5A3D1DB860152DE447B3E4EB16A4DCCA  200 1287062827        -1        -1 application/json -1/2268 GET http://www.yahoo.com/js?&__r=1287062824672&post=%7B%22reqs%22%3A%5B%7B%22handler%22%3A%22cfg.maple_dali.handler.refresh%22%2C%22data%22%3A%7B%22maple%22%3A%7B%22module%22%3A%22p_13872472%22%2C%22ba%22%3A%7B%22_txnid%22%3A0%2C%22_mode%22%3A%22json%22%2C%22_id%22%3A%22p_13872472%22%2C%22_container%22%3A0%2C%22_action%22%3A%22show%22%2C%22_subAction%22%3A%22story%22%2C%22storyId%22%3A%22id-44003%22%2C%22storyIndex%22%3A2%2C%22cokeTestId%22%3A%22%22%2C%22todaytop%22%3A%221%22%2C%22headlineBuzzUrn%22%3Anull%7D%7D%7D%2C%22txId%22%3A1%7D%5D%2C%22props%22%3A%7B%22dali%22%3A%7B%22crumb%22%3A%221G.rehocEP3%22%2C%22yuid%22%3A%22%22%2C%22loggedIn%22%3A%220%22%2C%22mLogin%22%3A0%7D%7D%7D
1287062838.980 SWAPOUT 00 00009464 94B6373D0EE7A4C42F43FA6D317BF6AC  200 1286910270 1286899540 1602270270 image/jpeg 24350/24350 GET http://l.yimg.com/a/i/ww/news/2010/10/12/mcdonalds.jpg
1287062982.365 RELEASE -1 FFFFFFFF 52D145D6723C885A8F5D62B3EE2083F8  200 1287062981 1286963181 1287567981 application/ocsp-response 1085/1085 POST http://ocsp.thawte.com/
1287062984.333 RELEASE -1 FFFFFFFF B42E9DEFB149AFFBA3915DD70A1540FF  200 1287062984 1286968581 1287573381 application/ocsp-response 1085/1085 POST http://ocsp.thawte.com/
1287063051.690 RELEASE -1 FFFFFFFF 862476FE405477410540963E607DD2C6  200 1287063051        -1        -1 application/vnd.google.safebrowsing-update 1704/1704 POST http://safebrowsing.clients.google.com/safebrowsing/downloads?client=navclient-auto-ffox&appver=3.6.10&pver=2.2&wrkey=AKEgNivGd8EQXvYPtGt7uyjrcrOqGBzXPEmgK1ziyq8RM2fIvPnHLq14dEgrzVYWI9QfSqH6VdpPlHKC--y2SIaYOSxCVZwB2Q==
1287063057.511 SWAPOUT 00 00000048 8613F5D6564C102C931C12771DD26BD1  200 1287061233        -1 1287234033 application/vnd.google.safebrowsing-chunk 140956/140956 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChNnb29nLW1hbHdhcmUtc2hhdmFyEAEYwa4CIICxAioZ35cAAP__________________________AzIYQZcAAP________________________8_
1287063125.599 SWAPOUT 00 0000004A 8839A7A408EF598BBC418F0F445D0B7D  200 1286954033        -1 1287126833 application/vnd.google.safebrowsing-chunk 12944/12944 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChNnb29nLW1hbHdhcmUtc2hhdmFyEAAY7cwBIIDNATIHbWYAAP__Cw
1287063128.716 SWAPOUT 00 00000DCF E0ECD36663B703B612F8E2BFC3F1D106  200 1287061234        -1 1287234034 application/vnd.google.safebrowsing-chunk 71608/71608 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChNnb29nLW1hbHdhcmUtc2hhdmFyEAAYgc0BIIDSASpMxWYAAP______________________________________________________________________________________________DzINgWYAAP__________Dw
1287063129.412 SWAPOUT 00 000013B4 9925983480D9AB897EA8800EB46B6BF7  200 1287027547        -1 1287200347 application/vnd.google.safebrowsing-chunk 13865/13865 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchABGLHuAyCA7wMyDzH3AAD_____________AA
1287063129.705 SWAPOUT 00 0000178A FDADA40F44D5F0BF87F982DFE3F3835D  200 1287061701        -1 1287234501 application/vnd.google.safebrowsing-chunk 756/756 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchABGIHvAyCA9AMqUpj3AAD______________________________________________________________________________________________________wEyB4H3AAD__38
1287063129.861 SWAPOUT 00 00001A69 4F5571F2C4B2C23EA31729299F06488F  200 1286916099        -1 1287088899 application/vnd.google.safebrowsing-chunk 37/37 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchAAGLCNByCwjQcyBbDGAQAB
1287063130.185 SWAPOUT 00 00001A6A 7CC432D3FC5D347762633C428A7B00CE  200 1286974521        -1 1287147321 application/vnd.google.safebrowsing-chunk 8556/8556 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchAAGLGNByCAjgcyD7HGAQDf7v__z_f_____AA
1287063134.873 SWAPOUT 00 00001A70 A7C3F753573287EEC25BE7F0D5B7831F  200 1287062779        -1 1287235579 application/vnd.google.safebrowsing-chunk 122211/122211 GET http://safebrowsing-cache.google.com/safebrowsing/rd/ChFnb29nLXBoaXNoLXNoYXZhchAAGIGOByCAmAcqhgH2xwEA____________________________________________________________________________________________________________________________________________________________________________BzIjAccBAP___________________v__________33_______x8
1287063202.202 RELEASE -1 FFFFFFFF 580068B230023A0EC67139070EEF0434  302 1287063202        -1        -1 text/html 0/0 GET http://ubuntuforums.org/showthread.php?t=1594407&goto=newpost
1287063202.781 RELEASE -1 FFFFFFFF 4EE5DD930FC599F791D97CED74875D17  304 1287063202        -1        -1 unknown -1/0 GET http://ubuntuforums.org/clientscript/vbulletin_important.css?v=384
1287063202.781 SWAPOUT 00 00001A72 B9E79D94AA498DFE67F10022CFBFCC7E  200 1287063202 1263305068        -1 text/css 1749/1749 GET http://ubuntuforums.org/clientscript/vbulletin_important.css?v=384
1287063202.781 RELEASE 00 00005A8E 2CE4966B08C2CD5465A2E51617818CE8  200 1287063202 1263305068        -1 text/css 1749/-510 GET http://ubuntuforums.org/clientscript/vbulletin_important.css?v=384
1287063202.789 RELEASE 00 00005A91 1A8626DB85D71E99259A129FCCC76F46  200 1286911100 1263305068        -1 application/x-javascript 26027/-528 GET http://ubuntuforums.org/clientscript/vbulletin_global.js?v=384
1287063202.801 RELEASE 00 00005A90 3F2221376221F114DCA96BC7E90C57FC  200 1286911100 1263305068        -1 application/x-javascript 9440/-527 GET http://ubuntuforums.org/clientscript/vbulletin_menu.js?v=384
1287063202.811 RELEASE 00 00005A8F 3A1B0F0FD584F9F92BB9648535070029  200 1286911100 1263305068        -1 application/x-javascript 2037/-526 GET http://ubuntuforums.org/clientscript/vbulletin_post_loader.js?v=384
1287063202.812 SWAPOUT 00 00001A75 F1EBCFEB018B89DE63F2FF45DCF6465F  200 1287063190 1263305068        -1 application/x-javascript 2037/2037 GET http://ubuntuforums.org/clientscript/vbulletin_post_loader.js?v=384
1287063202.963 RELEASE 00 00005A92 B85DB94F6BA32AC0841C3E72BF6D62C3  200 1286911100 1263305068        -1 application/x-javascript 5464/-526 GET http://ubuntuforums.org/clientscript/vbulletin_md5.js?v=384
1287063203.484 SWAPOUT 00 00001A7F C4FEDCEFC0E3AA33BC16D4134771CEEE  200 1287063203 1263305068        -1 application/x-javascript 5464/5464 GET http://ubuntuforums.org/clientscript/vbulletin_md5.js?v=384
1287063203.542 SWAPOUT 00 00001A84 B019FEA987449CE94253D3C3D4D82577  200 1287063174 1263305068        -1 application/x-javascript 9440/9440 GET http://ubuntuforums.org/clientscript/vbulletin_menu.js?v=384
1287063205.175 SWAPOUT 00 00001A7E 6A1C8100472C9E1045A724FA450799E4  200 1287063187 1263305068        -1 application/x-javascript 26027/26027 GET http://ubuntuforums.org/clientscript/vbulletin_global.js?v=384
1287063206.226 RELEASE -1 FFFFFFFF E92536F91D502687A4B8172C0A0108CB    0        -1        -1        -1 unknown -1/0 GET http://ps.sd150.org/images/css/screen.css
1287063206.249 RELEASE -1 FFFFFFFF AE89A9AF2648EF1562CDC2CBEA0B0C72    0        -1        -1        -1 unknown -1/0 GET http://ps.sd150.org/admin/javascript/md5.js
1287063206.285 RELEASE 00 00005C0D 6B5BC627ED4A64A3420ADB893693F425  200 1286982565 1268430529 1287050400 text/css 122/-227 GET http://ps.sd150.org/images/css/screen.css
1287063206.287 SWAPOUT 00 00001A85 8B3851BDE155EE8D5A6BB8AF3E7041AC  200 1287063206 1268430529 1287136800 text/css 122/122 GET http://ps.sd150.org/images/css/screen.css
1287063206.289 RELEASE 00 00000F8F EB6A2BF752C39D3B841A34F341F525AD  200 1286978785 1286978764 1287050400 application/x-javascript 15285/-245 GET http://ps.sd150.org/admin/javascript/md5.js
1287063206.297 SWAPOUT 00 00001A87 FD28754336766D2F65F63636507D070E  200 1287063206 1287063206 1287136800 application/x-javascript 15285/15285 GET http://ps.sd150.org/admin/javascript/md5.js
1287063206.352 RELEASE 00 00005C0E 8FD698E44C38F1D487BF7130372C61C0  200 1286982565 1271460688 1287050400 text/css 560/-227 GET http://ps.sd150.org/images/css/reset.css
1287063206.354 SWAPOUT 00 00001A93 0EEEE81298A267FB1D2D72CA308B1B82  200 1287063206 1271460688 1287136800 text/css 560/560 GET http://ps.sd150.org/images/css/reset.css
1287063206.356 RELEASE 00 00005C0F 5D43DDC9CFC1BF985D83B992A3B175CA  200 1286982565 1271795445 1287050400 text/css 28272/-229 GET http://ps.sd150.org/images/css/master.css
1287063206.423 RELEASE -1 FFFFFFFF B9ADA2375D06C6A8EF5E9DD839229F11  200 1287063206        -1        -1 text/html -1/3859 GET http://ps.sd150.org/public/
1287063206.607 SWAPOUT 00 00001C2C 2186DD11AAE7785A64719D8D912173DE  200 1287063206 1271795445 1287136800 text/css 28272/28272 GET http://ps.sd150.org/images/css/master.css
1287063206.680 RELEASE 00 00005C10 CD79AA9AD8F766E5D30E9590ADF11A99  200 1286982565 1241113252 1287050400 image/png 7522/-229 GET http://ps.sd150.org/images/pss_logo.png
1287063206.683 SWAPOUT 00 00001ED8 847B4955DD87DE054635B9090B389A9A  200 1287063207 1241113252 1287136800 image/png 7522/7522 GET http://ps.sd150.org/images/pss_logo.png
1287063206.684 RELEASE 00 0000102E 18E639695C7B1CBB4D3F2073A73AACE6  200 1286978786 1241206278 1287050400 image/png 933/-227 GET http://ps.sd150.org/images/pearson-logo-legal.png
1287063206.686 SWAPOUT 00 00001EEC E6625DBE5F961998C3D2FC95DA896D52  200 1287063207 1241206278 1287136800 image/png 933/933 GET http://ps.sd150.org/images/pearson-logo-legal.png
1287063206.691 RELEASE 00 00005C11 AB501E9AE7F560CEBCCEBA5E0F5B038E  200 1286982565 1258158224 1287050400 image/png 1307/-229 GET http://ps.sd150.org/images/img/btn-back.png
1287063206.693 SWAPOUT 00 00001F03 85C2A50F8BFD08FC813D635E0FA1CEBF  200 1287063207 1258158224 1287136800 image/png 1307/1307 GET http://ps.sd150.org/images/img/btn-back.png
1287063206.879 RELEASE 00 00001031 A83B6D4336EBC802A08AA51054D9ABBD  200 1286978786 1286978764 1287050400 text/html 1218/-229 GET http://ps.sd150.org/favicon.ico
1287063206.881 SWAPOUT 00 00002152 18418CB584F442D1F69B9BA71C88E590  200 1287063207 1287063206 1287136800 text/html 1218/1218 GET http://ps.sd150.org/favicon.ico
1287063207.028 RELEASE -1 FFFFFFFF 72C7E39F2C5B1BB861FF26227127D0B3  304 1287063207        -1 1287064026 application/pkix-crl -1/0 GET http://mscrl.microsoft.com/pki/mscorp/crl/mswww(4).crl
1287063207.029 SWAPOUT 00 00002617 E9BF38BCF2C09C080783C3627A86EA1C  200 1287063207 1285883870 1287064107 application/pkix-crl 727/727 GET http://mscrl.microsoft.com/pki/mscorp/crl/mswww(4).crl
1287063207.029 RELEASE 00 000090FB 6E45DEAC8C91D9062039780FD2D840E0  200 1287063207 1285883870 1287064107 application/pkix-crl 727/-502 GET http://mscrl.microsoft.com/pki/mscorp/crl/mswww(4).crl
1287063207.160 RELEASE -1 FFFFFFFF 7A67B4720C3D733464C0B705AF9E8374  304 1287063207        -1 1287063558 application/pkix-crl -1/0 GET http://mscrl.microsoft.com/pki/mscorp/crl/Microsoft%20Secure%20Server%20Authority(5).crl
1287063207.160 SWAPOUT 00 0000261C BBD6EA081C7956EEDDC6295E0D8D09E1  200 1287063207 1286563697 1287064107 application/pkix-crl 706/706 GET http://mscrl.microsoft.com/pki/mscorp/crl/Microsoft%20Secure%20Server%20Authority(5).crl
1287063207.170 RELEASE 00 00008F6F F8A545C58800172FF2B548D77D7D8A75  200 1287063207 1286563697 1287064107 application/pkix-crl 706/-503 GET http://mscrl.microsoft.com/pki/mscorp/crl/Microsoft%20Secure%20Server%20Authority(5).crl
1287063209.890 SWAPOUT 00 00002633 5B79EEF175FA7892A59CF129B5DAEAA7  200 1287062802 1229698828        -1 image/png 4220/4220 GET http://ubuntuforums.org/images/rank_12.png
1287063209.899 RELEASE -1 FFFFFFFF 984FDCF003DB73592D57A46FE430DBC7  304 1287063210        -1        -1 unknown -1/0 GET http://ubuntuforums.org/clientscript/vbulletin_lightbox.js?v=384
1287063209.899 SWAPOUT 00 00002634 F8513EB43BCFBF44012E9033CA33957A  200 1287063210 1263305068        -1 application/x-javascript 13002/13002 GET http://ubuntuforums.org/clientscript/vbulletin_lightbox.js?v=384
1287063209.900 RELEASE 00 00005AB3 4CC6780B7A52C3CF61B3D3EB999C0020  200 1287063210 1263305068        -1 application/x-javascript 13002/-527 GET http://ubuntuforums.org/clientscript/vbulletin_lightbox.js?v=384
1287063210.854 RELEASE -1 FFFFFFFF A99BA2AB8F79EB555C162BA372DAD106  200 1287063202        -1 1287063202 text/html -1/244415 GET http://ubuntuforums.org/showthread.php?p=9962256
1287063210.909 SWAPOUT 00 00002635 991C00E80F3BA1A291BA0FC0A05EDAFE  200 1287035596 1285017523        -1 image/gif 15603/15603 GET http://ubuntuforums.org/customavatars/avatar698195_1.gif
1287063211.113 RELEASE -1 FFFFFFFF 690D895FE099F09F8AC5FC89C6E4E12B  200 1287059528 1074714690 956144580 image/gif 35/35 GET http://www.google-analytics.com/__utm.gif?utmwv=4.8.6&utmn=359538311&utmhn=ubuntuforums.org&utmcs=ISO-8859-1&utmsr=1024x768&utmsc=24-bit&utmul=en-us&utmje=1&utmfl=10.1%20r85&utmdt=%5Bubuntu%5D%20Squid%20Proxy%20on%20Ubuntu%20-%20Ubuntu%20Forums&utmhid=701640994&utmr=-&utmp=%2Fshowthread.php%3Fs%3D2a6f0159e74925cccdd008bffa6348af%26p%3D9962256&utmac=UA-361826-29&utmcc=__utma%3D234146522.751969358.1287063209.1287063209.1287063209.1%3B%2B__utmz%3D234146522.1287063209.1.1.utmcsr%3D(direct)%7Cutmccn%3D(direct)%7Cutmcmd%3D(none)%3B&utmu=D
1287063211.573 RELEASE -1 FFFFFFFF E84691044B3DAAC39C88D4CC331CF4F3  200 1287063210        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063211.836 RELEASE -1 FFFFFFFF CB44D31369C19C8073FA881EAEC0401C  304 1287063212 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063211.836 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063212 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063211.843 RELEASE 00 00004811 86C513A7F04CB68BCF5A536F42B0657F  200 1287063212 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063212.842 RELEASE -1 FFFFFFFF 0E64AAA0820A48D664A760E089013530  302 1287063212 1287149612 1287063212 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25410831120736?AQB=1&ndh=1&t=14/9/2010%208%3A33%3A32%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063212.936 RELEASE -1 FFFFFFFF 9AEF5E77A6BF375959A2918124F1EB80  200 1287063213 1287149613 1287063213 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25410831120736?AQB=1&pccr=true&vidn=265B8356050109EE-400001148003F956&&ndh=1&t=14/9/2010%208%3A33%3A32%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063219.059 RELEASE -1 FFFFFFFF 463A22ED4FE22688744E0A21F57FCE79  200 1287063219        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063219.138 RELEASE -1 FFFFFFFF 337FCFA5B0B5DB58CF382647B96F6633  304 1287063219 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063219.138 SWAPOUT 00 00002637 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063219 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063219.140 RELEASE 00 00002636 9F1FFB44BB7B755BD9964045FB70CB50  200 1287063219 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063219.202 RELEASE -1 FFFFFFFF 1EC2F1BFACB531019BBC4B212F456CB6    0        -1        -1        -1 unknown -1/0 GET http://assignments.discoveryeducation.com/images/BG.jpg
1287063219.962 RELEASE -1 FFFFFFFF CDE36E6A97F28BAACCE40EA9A78C99EC  302 1287063220 1287149620 1287063220 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22835879800331?AQB=1&ndh=1&t=14/9/2010%208%3A33%3A41%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063220.082 RELEASE -1 FFFFFFFF 7B50085FBC9868687F7FB473E39DA5F0  200 1287063220 1287149620 1287063220 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22835879800331?AQB=1&pccr=true&vidn=265B835A0501339A-60000109E0017943&&ndh=1&t=14/9/2010%208%3A33%3A41%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063224.516 RELEASE -1 FFFFFFFF 5602B32A56B7B4D47CFE243EC73AA548  200 1287063224        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063224.651 RELEASE -1 FFFFFFFF 10DEA4897D14C5A48C0AE527AB540115  304 1287063224 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063224.651 SWAPOUT 00 00002638 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063224 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063224.652 RELEASE 00 00002637 DC0AD9E0736488812B557846D238EB6B  200 1287063224 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063225.639 RELEASE -1 FFFFFFFF B60C38E55F4EC4831956C5B96D0EC87B  302 1287063226 1287149626 1287063226 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22116583854289?AQB=1&ndh=1&t=14/9/2010%208%3A33%3A44%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063225.752 RELEASE -1 FFFFFFFF 8FBA0900BE2C290D832C590653492A3A  200 1287063226 1287149626 1287063226 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22116583854289?AQB=1&pccr=true&vidn=265B835D050121A8-40000101C00118F9&&ndh=1&t=14/9/2010%208%3A33%3A44%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063237.704 RELEASE -1 FFFFFFFF D251D9C6D080FE7278108610FEB4CE63  200 1287063237        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063237.788 RELEASE -1 FFFFFFFF 5848C73CC32EF940F4207203186BBD4C  304 1287063237 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063237.788 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063237 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063237.788 RELEASE 00 00002638 A4751BB653DDA01D37866D53C7FC4669  200 1287063237 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063238.741 RELEASE -1 FFFFFFFF 72B34233D74BACF7CFDC285C015CAC24  302 1287063238 1287149638 1287063238 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25743690312498?AQB=1&ndh=1&t=14/9/2010%208%3A33%3A59%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063238.828 RELEASE -1 FFFFFFFF 98129741F94DA34D10E3EA79A678E82F  200 1287063238 1287149638 1287063238 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25743690312498?AQB=1&pccr=true&vidn=265B836305010BE7-4000010060021A47&&ndh=1&t=14/9/2010%208%3A33%3A59%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063238.906 RELEASE -1 FFFFFFFF 790B2B8B04162A54000DC341080DC904  200 1287063239        -1        -1 text/html -1/3946 POST http://ps.sd150.org/guardian/home.html
1287063238.954 RELEASE 00 00006817 078556D0AA7FEDF3CC8417717D8A2AFA  200 1286989259 1114815947 1287050400 image/gif 282/-228 GET http://ps.sd150.org/images/alert_other.gif
1287063238.956 SWAPOUT 00 00002637 2705BE019D067E14EABA1EC3EFDC1F85  200 1287063239 1114815947 1287136800 image/gif 282/282 GET http://ps.sd150.org/images/alert_other.gif
1287063243.860 RELEASE -1 FFFFFFFF ACD48D419DE8E120F736A923E2FB89AC  200 1287063243        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063243.942 RELEASE -1 FFFFFFFF 3BA9EDF9036E2E6140DF3EA52F66B693  304 1287063244 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063243.943 SWAPOUT 00 00002638 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063244 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063243.943 RELEASE 00 00002636 6ED67BAB8D766800D0B0ED6F3CE31BD2  200 1287063244 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063244.852 RELEASE -1 FFFFFFFF 7A50BD4536D88EDB5F79FDB1FC59025D  302 1287063244 1287149644 1287063244 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23975506012537?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A3%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063244.945 RELEASE -1 FFFFFFFF B62B643C10A48D6DEF730177FB0B07EF  200 1287063244 1287149644 1287063244 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23975506012537?AQB=1&pccr=true&vidn=265B836605011248-4000010520037584&&ndh=1&t=14/9/2010%208%3A34%3A3%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063254.716 RELEASE -1 FFFFFFFF B022998C66A3C6B517446D7F3AC8A653  200 1287063254        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063254.773 RELEASE -1 FFFFFFFF 1BD71100666CB0B8CDC5BA576998413C  304 1287063254 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063254.774 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063254 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063254.776 RELEASE 00 00002638 2D0B06D3FCBD33C43260760A3485E1F2  200 1287063254 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063255.726 RELEASE -1 FFFFFFFF 10CA6404D4AFC6EA3B7DE6CDD52E0C9F  302 1287063255 1287149655 1287063255 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s27925738011862?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A14%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063255.813 RELEASE -1 FFFFFFFF DC3669251A518A6E0FFEAE250B6DFC92  200 1287063256 1287149656 1287063256 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s27925738011862?AQB=1&pccr=true&vidn=265B836B85013F41-400001084000673E&&ndh=1&t=14/9/2010%208%3A34%3A14%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063259.837 RELEASE -1 FFFFFFFF C0576144C4AF9A22A49775712BBEC8B5  200 1287063259        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063259.999 RELEASE -1 FFFFFFFF 407B1E99B142731060889151560620EE  304 1287063260 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063260.000 SWAPOUT 00 00002638 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063260 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063260.000 RELEASE 00 00002636 5E7DC2E7F3A152351B502068BC039120  200 1287063260 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063260.974 RELEASE -1 FFFFFFFF 34A22371C19FDC958415E2DF2DD077DA  302 1287063261 1287149661 1287063261 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23504574692269?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A20%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063261.095 RELEASE -1 FFFFFFFF 9B06E9F8FCA29A1245F96E094E6BD768  200 1287063261 1287149661 1287063261 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23504574692269?AQB=1&pccr=true&vidn=265B836E85012E8F-6000010820002633&&ndh=1&t=14/9/2010%208%3A34%3A20%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063261.184 RELEASE -1 FFFFFFFF 3A030DDAD5E2A83F8F692B4FEC39DFEE  200 1287063261 1287149661 1287063261 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23619244997522?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A20%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063264.014 RELEASE -1 FFFFFFFF 485E1B997A5582DE11E0CE858D275B62  200 1287063264        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063264.159 RELEASE -1 FFFFFFFF 1C66653619E2F38546BDF6D3501B12B5  304 1287063264 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063264.160 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063264 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063264.160 RELEASE 00 00002638 46A18C2C1C699B0F75C5ED8EE6F8F02F  200 1287063264 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063264.816 RELEASE -1 FFFFFFFF 27E391D04BC6B5195A0A9F42791A633D  200 1287063264        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063264.898 RELEASE -1 FFFFFFFF BF11279F7BBA79497CF3B7C7947AB046  304 1287063265 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063264.898 SWAPOUT 00 00002638 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063265 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063264.899 RELEASE 00 00002636 52A24EA89765D99D059C7AF58E2D7991  200 1287063265 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063265.101 RELEASE -1 FFFFFFFF 7D2E61A3E7997A6D53981D6D12B287B1  302 1287063265 1287149665 1287063265 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s24257972298015?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A24%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063265.204 RELEASE -1 FFFFFFFF 36F885DE5F658CD26AD3A1EAD01F17B1  200 1287063265 1287149665 1287063265 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s24257972298015?AQB=1&pccr=true&vidn=265B837085010483-60000107E0000B4C&&ndh=1&t=14/9/2010%208%3A34%3A24%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063265.772 RELEASE -1 FFFFFFFF DD9EF9DE96DCA6588EB65646FABA76CC  302 1287063265 1287149665 1287063265 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25246483829993?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A23%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063265.860 RELEASE -1 FFFFFFFF 616F0237A1A7F01E7F3B630A163F34E3  200 1287063265 1287149665 1287063265 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25246483829993?AQB=1&pccr=true&vidn=265B83708501250E-40000101E00034F7&&ndh=1&t=14/9/2010%208%3A34%3A23%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063270.920 RELEASE -1 FFFFFFFF 7398B7A206903F35F718297D46D164E0  200 1287063271        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063271.069 RELEASE -1 FFFFFFFF 410FAF871E88022E632E3E250C6E5E84  304 1287063271 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063271.069 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063271 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063271.070 RELEASE 00 00002638 420202906BDECF26979CF7E6088FB59B  200 1287063271 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063271.927 RELEASE -1 FFFFFFFF 542666ECFE5E78F2F319E4D8375DC931  302 1287063272 1287149672 1287063272 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s29271473113394?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A30%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063272.010 RELEASE -1 FFFFFFFF 0BAEEBEB947FE8A7BB8206B3EAF352EA  200 1287063272 1287149672 1287063272 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s29271473113394?AQB=1&pccr=true&vidn=265B837405011A91-40000110E0012621&&ndh=1&t=14/9/2010%208%3A34%3A30%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063272.816 RELEASE -1 FFFFFFFF 6EB71D768C8D4A1EF1E4D623311322CD  200 1287063272        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063272.963 RELEASE -1 FFFFFFFF 42E5A47470AE347BADF8D521C1F08D89  304 1287063273 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063272.964 SWAPOUT 00 00002638 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063273 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063272.964 RELEASE 00 00002636 C54CE5C84B39F8ED36CCC02612ED0BBA  200 1287063273 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063273.896 RELEASE -1 FFFFFFFF B33D434329C255D99842FD8920ABCFED  302 1287063274 1287149674 1287063274 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25905059461507?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A34%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063273.985 RELEASE -1 FFFFFFFF CF48C5DCEAB1F7F46183E682849890AD  200 1287063274 1287149674 1287063274 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25905059461507?AQB=1&pccr=true&vidn=265B8375050124DD-40000108C0004BCA&&ndh=1&t=14/9/2010%208%3A34%3A34%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063274.775 RELEASE -1 FFFFFFFF E61FA68F1477EB53EB349E5B9276A8F3  200 1287063274        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063274.786 RELEASE -1 FFFFFFFF A812D754B38C7894B703C0084C7486DB  304 1287063274 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063274.787 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063274 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063274.787 RELEASE 00 00002638 D2AD2895EF6CE7225699095DB2A95A75  200 1287063274 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063275.563 RELEASE -1 FFFFFFFF 91AB18B9714267D247A3D6A48A1772AC  302 1287063275 1287149675 1287063275 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21996430395222?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A35%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063275.646 RELEASE -1 FFFFFFFF 317438EE97761DF4A53DFA9CE573F23B  200 1287063275 1287149675 1287063275 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21996430395222?AQB=1&pccr=true&vidn=265B837585012A42-4000010440006806&&ndh=1&t=14/9/2010%208%3A34%3A35%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063281.782 RELEASE -1 FFFFFFFF 01B5D77B377484B4A0000E5CBFFFDC56  200 1287063281        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063281.904 RELEASE -1 FFFFFFFF 7C6DC900D3C8A87362997774B4A64A60  304 1287063282 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063281.904 SWAPOUT 00 00002638 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063282 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063281.904 RELEASE 00 00002636 21765B1A15BE75FB61BB9B299E6D0421  200 1287063282 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063282.769 RELEASE -1 FFFFFFFF 14E672FC398E7CA99C6650B741BC9F16  302 1287063283 1287149683 1287063283 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26291646119153?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A42%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063282.852 RELEASE -1 FFFFFFFF A1C5D9FB0C7B1C57918F34FE8E4278BA  200 1287063283 1287149683 1287063283 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26291646119153?AQB=1&pccr=true&vidn=265B837985012F0A-4000010FA0002821&&ndh=1&t=14/9/2010%208%3A34%3A42%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063285.110 RELEASE -1 FFFFFFFF 2947B398DD2FF60577DEBD7F6D116E2F  200 1287063285        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063285.190 RELEASE -1 FFFFFFFF 528468DE7A0443E67DF06FA87A0CE72A  304 1287063285 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063285.190 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063285 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063285.191 RELEASE 00 00002638 455A81086EE30A19F4441D02077F4B3B  200 1287063285 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063286.074 RELEASE -1 FFFFFFFF 9140F3B91F03652CEA152F353F889CD2  302 1287063286 1287149686 1287063286 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25213673262513?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A45%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063286.165 RELEASE -1 FFFFFFFF 6D1479F3DCD85201D582BA1779E857E2  200 1287063286 1287149686 1287063286 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s25213673262513?AQB=1&pccr=true&vidn=265B837B05013B7A-60000114C0003698&&ndh=1&t=14/9/2010%208%3A34%3A45%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063288.538 RELEASE -1 FFFFFFFF 835E12868C1833EA800C1AE7EE2DF8C5  200 1287063288        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063288.712 RELEASE -1 FFFFFFFF 1D5978E1627F15464D68DCBCD318D411  304 1287063288 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063288.712 SWAPOUT 00 00002638 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063288 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063288.713 RELEASE 00 00002636 177C35161E41E4C649EF20E6D245D587  200 1287063288 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063289.578 RELEASE -1 FFFFFFFF 5872BF11B29CB348E0978275D8911FA5  302 1287063289 1287149689 1287063289 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22869974201158?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A49%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063289.674 RELEASE -1 FFFFFFFF 20ADA7C1D1EF96D331800275F9530838  200 1287063289 1287149689 1287063289 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22869974201158?AQB=1&pccr=true&vidn=265B837C850127CC-60000108C000052F&&ndh=1&t=14/9/2010%208%3A34%3A49%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063293.675 RELEASE -1 FFFFFFFF 383B7AB7A59512443A24FF1A0B90A82D  200 1287063293        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063293.832 RELEASE -1 FFFFFFFF A1BCF5A033129566D1E37A0352402FA7  304 1287063294 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063293.832 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063294 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063293.832 RELEASE 00 00002638 BDB85D5E315966618E1AA32614B5A015  200 1287063294 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063294.658 RELEASE -1 FFFFFFFF 0B326021EB865BCB66AD42E28ACB83C1  302 1287063294 1287149694 1287063294 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s24020899344824?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A54%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063294.760 RELEASE -1 FFFFFFFF 9AA1AD5B545C731F98FD0CEB1E0505CA  200 1287063295 1287149695 1287063295 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s24020899344824?AQB=1&pccr=true&vidn=265B837F05012F62-4000010E80005266&&ndh=1&t=14/9/2010%208%3A34%3A54%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063296.626 RELEASE -1 FFFFFFFF 75AA7A1EF11619E6A1768E336DAD9BFA  200 1287063296        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063296.710 RELEASE -1 FFFFFFFF 21CCC28E8FA2C08C20C197E2684048A0  304 1287063296 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063296.711 SWAPOUT 00 00002638 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063296 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063296.711 RELEASE 00 00002636 CD18FB37EC2E87655A3E0C790A5FC5EB  200 1287063296 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063297.568 RELEASE -1 FFFFFFFF D35B19754475B03F9D2F3BC230E33187  302 1287063297 1287149697 1287063297 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21327049256569?AQB=1&ndh=1&t=14/9/2010%208%3A34%3A57%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063297.676 RELEASE -1 FFFFFFFF F68DDBE0171982249459214D9AC62797  200 1287063297 1287149697 1287063297 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21327049256569?AQB=1&pccr=true&vidn=265B838085012FE0-6000010FA00016EC&&ndh=1&t=14/9/2010%208%3A34%3A57%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063299.708 RELEASE -1 FFFFFFFF 3E020680E4BD04D66D4301F4FA0734AD  200 1287063299        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063299.848 RELEASE -1 FFFFFFFF F877EB095F6B8E2DCC44C04CACE9E869  304 1287063300 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063299.848 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063300 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063299.849 RELEASE 00 00002638 0D2D27BBF684D1313F3566629AEA7C67  200 1287063300 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063300.695 RELEASE -1 FFFFFFFF 3FBBA2596EB13F773EA2E8C47810E292  302 1287063300 1287149700 1287063300 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21909122828843?AQB=1&ndh=1&t=14/9/2010%208%3A35%3A0%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063300.773 RELEASE -1 FFFFFFFF 5CE4605F004CB5BC6D769A91D09E487B  200 1287063300 1287149700 1287063300 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s21909122828843?AQB=1&pccr=true&vidn=265B838205013C1C-4000010B400074B4&&ndh=1&t=14/9/2010%208%3A35%3A0%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063303.538 RELEASE -1 FFFFFFFF 0F6C15B148428CC200A7914DF8EAE042  200 1287063303        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063303.675 RELEASE -1 FFFFFFFF 487B18A5F60356CF3B9ECA784E9175F7  304 1287063303 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063303.675 SWAPOUT 00 00002638 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063303 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063303.678 RELEASE 00 00002636 586917C69F20C7CCC0A5739D8E64682E  200 1287063303 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063304.579 RELEASE -1 FFFFFFFF 8314DD577470E2FA0B0F50B0B9B1EF6A  302 1287063304 1287149704 1287063304 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s28430864401465?AQB=1&ndh=1&t=14/9/2010%208%3A35%3A4%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063304.663 RELEASE -1 FFFFFFFF 7440A4A908C97F57F6C87FD0CE1466C1  200 1287063304 1287149704 1287063304 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s28430864401465?AQB=1&pccr=true&vidn=265B838405012A45-4000010440007DB5&&ndh=1&t=14/9/2010%208%3A35%3A4%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063306.598 RELEASE -1 FFFFFFFF D8A50578C99B127AD64D625BB08B0A5E  200 1287063306        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063306.803 RELEASE -1 FFFFFFFF 221005B7EF22193D6C41A4A9A68AB4A3  304 1287063307 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063306.804 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063307 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063306.804 RELEASE 00 00002638 D9CB88EA023945C41414E1C24D4A6FB2  200 1287063307 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063307.682 RELEASE -1 FFFFFFFF 2A0E31E24E7F9BD1C5FF027410D5467A  302 1287063308 1287149708 1287063308 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23418664428453?AQB=1&ndh=1&t=14/9/2010%208%3A35%3A6%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063307.765 RELEASE -1 FFFFFFFF 43CFAE6F60C5DA94C32838D49F86C3DA  200 1287063308 1287149708 1287063308 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23418664428453?AQB=1&pccr=true&vidn=265B83860501142D-4000010A400041BF&&ndh=1&t=14/9/2010%208%3A35%3A6%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063309.783 RELEASE -1 FFFFFFFF 5C5581E5630AAB0146D644CE41E379D3  200 1287063309        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063309.929 RELEASE -1 FFFFFFFF B07E7EB6AAB18D2970187B5553B0605E  304 1287063310 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063309.929 SWAPOUT 00 00002638 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063310 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063309.929 RELEASE 00 00002636 F04B9408E2402B87EC38CE804F7AE1C0  200 1287063310 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063310.781 RELEASE -1 FFFFFFFF A4C3090C49336F6AE32983D5F27C5882  302 1287063310 1287149710 1287063310 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26945053934624?AQB=1&ndh=1&t=14/9/2010%208%3A35%3A10%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063310.871 RELEASE -1 FFFFFFFF 0105C819522C63FF127FA1426763CD0E  200 1287063310 1287149710 1287063310 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26945053934624?AQB=1&pccr=true&vidn=265B838705012847-4000010A60000F4E&&ndh=1&t=14/9/2010%208%3A35%3A10%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063314.943 RELEASE -1 FFFFFFFF 401C95150228BA7C1BC365EECF2CDDFA  200 1287063315        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063315.028 RELEASE -1 FFFFFFFF 7EE05FBE1A8FB69F58FEE697C417A7B5  304 1287063315 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063315.029 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063315 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063315.029 RELEASE 00 00002638 7C1F29691C868CAE3E29C9032990F501  200 1287063315 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063315.875 RELEASE -1 FFFFFFFF F2DF92F17F5FFFB0ACD99828D2739C3B  302 1287063315 1287149715 1287063315 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26971927629113?AQB=1&ndh=1&t=14/9/2010%208%3A35%3A14%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063315.960 RELEASE -1 FFFFFFFF 284F434CF54A566C35FECA8107482BF6  200 1287063316 1287149716 1287063316 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s26971927629113?AQB=1&pccr=true&vidn=265B83898501393C-60000109C0003E22&&ndh=1&t=14/9/2010%208%3A35%3A14%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063318.985 RELEASE -1 FFFFFFFF 28BFC571E9C6A6B28A4398CCA7CB159B  200 1287063319        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063319.112 RELEASE -1 FFFFFFFF B9E2A7D46989C4E645923CD35D85D440  304 1287063319 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063319.112 SWAPOUT 00 00002638 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063319 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063319.113 RELEASE 00 00002636 E6561DB259C131A1478F916F0AC430D5  200 1287063319 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063319.935 RELEASE -1 FFFFFFFF 6D5FEAD3FE41A9B045D341AA29201A80  302 1287063320 1287149720 1287063320 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22782826941265?AQB=1&ndh=1&t=14/9/2010%208%3A35%3A18%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063320.029 RELEASE -1 FFFFFFFF 921BEBA78671604E1F82D6068886D451  200 1287063319 1287149719 1287063319 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s22782826941265?AQB=1&pccr=true&vidn=265B838C0501274E-4000010BC0001D6C&&ndh=1&t=14/9/2010%208%3A35%3A18%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063324.842 RELEASE -1 FFFFFFFF 95DDE8E475FB407CE84FCBC0019B6031  200 1287063324        -1        -1 text/html -1/17720 GET http://assignments.discoveryeducation.com/
1287063324.994 RELEASE -1 FFFFFFFF 82D3FC1B9E0A0B5A168CBDE4B26A4002  304 1287063325 1286409592        -1 unknown -1/0 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063324.994 SWAPOUT 00 00002636 29452D45E8FBB08B0450DC29A3C0DD25  200 1287063325 1286409592        -1 text/css -1/12572 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063324.994 RELEASE 00 00002638 8D870FE1D135A5D55B7961985B96C2F9  200 1287063325 1286409592        -1 text/css -1/-196 GET http://static.discoveryeducation.com/global/css/style-rel5.css?062210
1287063325.919 RELEASE -1 FFFFFFFF 3044CC474992DCB1D0777AFEC2ED0EBE  302 1287063325 1287149725 1287063325 text/plain 0/0 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23395962174461?AQB=1&ndh=1&t=14/9/2010%208%3A35%3A25%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063326.000 RELEASE -1 FFFFFFFF FB2C0FF521934090EC4494A6B6CCB0C4  200 1287063326 1287149726 1287063326 image/gif 43/43 GET http://img.discovery.com/b/ss/disccedutools/1/H.17/s23395962174461?AQB=1&pccr=true&vidn=265B838E85012528-40000114A0005A42&&ndh=1&t=14/9/2010%208%3A35%3A25%204%20300&ce=ISO-8859-1&pageName=assignments.discoveryeducation.com/&g=http%3A//assignments.discoveryeducation.com/&cc=USD&ch=EDU%3ATools&server=assignments.discoveryeducation.com&c1=EDU&h1=Education%7CTools&c2=EDU%3ATools&c3=EDU%3ATools%3Aassignments.discoveryeducation.com&c7=EDU%3ATools%3Aassignments.discoveryeducation.com&s=1024x768&c=32&j=1.5&v=Y&k=Y&bw=1008&bh=562&ct=lan&hp=N&AQE=1
1287063415.785 RELEASE -1 FFFFFFFF 62BE138F2FA533588D4EA31637C95B62  200 1287063415 1287027397 1287632197 application/ocsp-response 1727/1727 POST http://ocsp.verisign.com/
1287063416.116 RELEASE -1 FFFFFFFF BC6792E11D1EABA9D4BA51E873056891  200 1287063416 1286867427 1287472227 application/ocsp-response 1482/1482 POST http://evsecure-ocsp.verisign.com/

```

---

### Post by SeijiSensei on 2010-10-15
A "TCP/HIT" entry in access.log indicates that the item was found in the cache.  The store log shows it's definitely caching objects.

Most of the time you can run Squid with its default settings.  If you want to play around a bit, you can read [http://www.deckle.co.za/squid-users-guide/Main_Page](http://www.deckle.co.za/squid-users-guide/Main_Page).

If you run the speed test from the machine running Squid itself, do you get different performance scores than if you run it from a machine behind the proxy?

---

### Post by kkil82 on 2010-10-15
When I run a speed test with speedtest.net I get at best the same numbers as I do without the proxy.  I am also looking to enable caching with java apps online any ideas?  Thanks for replying any other ideas?  I know I should be getting higher numbers because the old proxy would.  Thanks.

---

### Post by SeijiSensei on 2010-10-15
Well the best linespeed you'll see is from the proxy host itself.  If that's the same as you get with Squid, then the proxy is performing fine.  Is Squid running on the same hardware you were using before?  What kind of network cards does the proxy host have?  What kind of connection do you have between the host and the Internet? Between the host and the LAN?

SARG is in the repositories; just use "sudo apt-get install sarg".

---

### Post by kkil82 on 2010-10-15
I have 2 T1 lines for a maximum of 3 mbps.  I am running the exact same hardware.  Gigabit NIC with gigabit switches between locations.  The logisense proxy software I was using on the same hardware would give me 90 mbps or better with that proxy but the squid only does what is available?  Shouldn't I see the same high numbers once the pages are cached?  How do I know how long the files reside until they are deleted in squid cache?

---

