---
title: "Mythweb: .htaccess in settings dir?"
date: 2008-05-21
forum: Mythbuntu
---

### Post by joe0815 on 2008-05-21
Hello,

how can I prevent a user to access the settings dialog in mythweb? I tried it with another .htaccess file for a further user in the mythweb/modules/settings/ directory, but this had no success.

Is there any possibility?

Regards
Jo

---

### Post by joe0815 on 2008-05-21
Hello,

I just made a fault. Now it's protected. But there is one thing which makes it quiet unusable. I have this settings in my http.conf:

<Directory "/var/www/mythweb/">
        Options Indexes FollowSymLinks
        AuthType           Digest
        AuthName           "MythTV"
        AuthUserFile       /etc/mythtv/mythweb-digest
        Require            user user
        BrowserMatch       "MSIE"      AuthDigestEnableQueryStringHack=On
        Order allow,deny
        Allow from all
</Directory>

<LocationMatch .*/settings>
        AuthType        Digest
        AuthName        "MythTV Settings"
        AuthUserFile    /etc/mythtv/mythweb-digest
        Require         user admin
        BrowserMatch    "MSIE"  AuthDigestEnableQueryStringHack=On
        Order           Allow,Deny
        Satisfy         Any
</LocationMatch>

But now, when I start mythweb with the browser there must be a redirect on every page that wants the password of admin.

Is this not possible what I want to do?

Regards
Jo

---

### Post by cynicismic on 2009-05-27
I'm also setting this up, but with LDAP groups rather than htaccess, it works really nicely apart from this.
Think a better regex is needed to allow disallow access to the URL, whilst still allowing access to the png image, which according to HTTP headers is /mythweb/skins/default/img/settings.png

I've not worked out a decent regex that satisfies this yet..

For now I've just left it as:

<LocationMatch ".*/settings">
  Order Allow,Deny
  Allow from 192.168.120
</LocationMatch>

Where 192.168.120 is my own /24 subnet - change for whatever subnet you're on or specify a single IP address of your workstation.


Users just then get the red X rather than being prompted.

Will update if/when I get this working properly.

Cheers,

---

### Post by cynicismic on 2009-05-27
sometimes the answer is far simpler than first envisioned...

as the denied image is /mythweb/skins/default/img/settings.png


simply change the regex to be: ".*web/settings"..

in full:

</Directory>
        <LocationMatch ".*web/settings">
                AuthType Basic
                AuthBasicProvider ldap
                AuthzLDAPAuthoritative on
                AuthName "admin users only"
                AuthLDAPURL ldap://netserv.internal.example.com:389/ou=people,dc=example,dc=co,dc=uk?uid?sub
                AuthLDAPGroupAttribute memberUid
                AuthLDAPGroupAttributeIsDN off
                Require ldap-group cn=mythWebAdmins,ou=groups,dc=example,dc=co,dc=uk
        </LocationMatch>

have updated the wiki at mythtv.org with the updated regex.

---

