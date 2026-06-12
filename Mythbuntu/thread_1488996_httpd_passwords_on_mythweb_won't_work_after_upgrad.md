---
title: "httpd passwords on mythweb won't work after upgraded to Lucid Lynx"
date: 2010-05-20
forum: Mythbuntu
---

### Post by vipasane on 2010-05-20
Title should be: 
httpd passwords on mythweb won't work after upgraded to Lucid Lynx


I don't have mythbuntu, but didn't get an help from other forums so I'm trying my luck here.

I Just upgraded to Lucid Lynx and the authentication on my mytheb haven't been working since.

My initial problem was that I didn't know which config apache was using to secure mythweb. That's already solved so you can skip 1st post, but I copy pasted it there for history.

Any help would be appreciated
Thanks in advance

My problems in detail below:
1st post:
-----------------------
My Mythweb is asking for authentication but none username/password will work. It just prompts for authentication over and over again.

I've found few configurations regarding authentication:

in /etc/apache2/httpd.conf I have following lines:

<Directory "/var/www/mythweb">
Options Indexes FollowSymLinks
AuthType Basic
AuthName "MythTV"
AuthUserFile /etc/apache2/httpd-passwords
require user user1 user2
Order allow,deny
Allow from all
</Directory>

and in /etc/apache2/sites-available/mythweb.conf I have another config:

AuthType Digest
AuthName "MythTV"
AuthUserFile /etc/mythtv/mythweb-digest
Require valid-user
BrowserMatch "MSIE" AuthDigestEnableQueryStringHack=On
Order allow,deny
Satisfy any

none of the username/paswd pairs in Authuserfile are working?
Can there be yet another file / configuraton somewhere?
How do I know which one apache is using right now? 
------------

2nd post:
-------------
Tried these with no luck, though first two were not enabled
[http://ubuntuforums.org/showthread.php?t=1470695](http://ubuntuforums.org/showthread.php?t=1470695)

I Have Joomla installed in another directory so changed httpd.conf authentication to point on upper directory --> to see if authentication works there as expected with success --> figured out that it's using httpd.conf, commented out authentication related lines from mythweb.config

Now everything works as expected under Joomla, but under mythweb it keeps on asking for authentication over and over again.

which log I should be digging?
----------------

---

### Post by tgm4883 on 2010-05-20
> **vipasane said:**
> Title should be: 
httpd passwords on mythweb won't work after upgraded to Lucid Lynx


I don't have mythbuntu, but didn't get an help from other forums so I'm trying my luck here.

I Just upgraded to Lucid Lynx and the authentication on my mytheb haven't been working since.

My initial problem was that I didn't know which config apache was using to secure mythweb. That's already solved so you can skip 1st post, but I copy pasted it there for history.

Any help would be appreciated
Thanks in advance

My problems in detail below:
1st post:
-----------------------
My Mythweb is asking for authentication but none username/password will work. It just prompts for authentication over and over again.

I've found few configurations regarding authentication:

in /etc/apache2/httpd.conf I have following lines:

<Directory "/var/www/mythweb">
Options Indexes FollowSymLinks
AuthType Basic
AuthName "MythTV"
AuthUserFile /etc/apache2/httpd-passwords
require user user1 user2
Order allow,deny
Allow from all
</Directory>

and in /etc/apache2/sites-available/mythweb.conf I have another config:

AuthType Digest
AuthName "MythTV"
AuthUserFile /etc/mythtv/mythweb-digest
Require valid-user
BrowserMatch "MSIE" AuthDigestEnableQueryStringHack=On
Order allow,deny
Satisfy any

none of the username/paswd pairs in Authuserfile are working?
Can there be yet another file / configuraton somewhere?
How do I know which one apache is using right now? 
------------

2nd post:
-------------
Tried these with no luck, though first two were not enabled
[http://ubuntuforums.org/showthread.php?t=1470695](http://ubuntuforums.org/showthread.php?t=1470695)

I Have Joomla installed in another directory so changed httpd.conf authentication to point on upper directory --> to see if authentication works there as expected with success --> figured out that it's using httpd.conf, commented out authentication related lines from mythweb.config

Now everything works as expected under Joomla, but under mythweb it keeps on asking for authentication over and over again.

which log I should be digging?
----------------

Have you tried reenabling it in MCC?

---

### Post by vipasane on 2010-05-25
So I installed MMC ja reconfigured mythyweb security and it did the trick,

---

