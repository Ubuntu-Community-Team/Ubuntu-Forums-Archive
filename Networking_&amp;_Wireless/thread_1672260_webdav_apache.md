---
title: "webdav apache"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by eriverag on 2011-01-20
Recently configure apache with modules davfs, and ssl and .htaccess, in a folder called share ... everything works fine on the local network and internet, using WebDAV clients.  But when I go with Firefox to https: / /192.168.221.125 /share... identification does not ask me to login and allows me to see contents of the folder (I know cannot be edited) even download files.  I need this folder is not accessible only by WebDAV (for security purpose)

---

### Post by SeijiSensei on 2011-01-21
Set up [HTTP Basic Authentication]("http://httpd.apache.org/docs/2.2/mod/mod_auth_basic.html") on the webdav share.  The clients will then prompt for a username and password.

---

