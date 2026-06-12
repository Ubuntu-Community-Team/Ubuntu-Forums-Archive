---
title: "Apache: how to use htpasswd?"
date: 2010-07-08
forum: Mythbuntu
---

### Post by redconfusion on 2010-07-08
Currently trying to setup my MythWeb as password protected website.

I changed listening port from 80 to 81 and have port 81 forwarded from my router since I already have a different computer forwarding port 80 for my main web site.

*Up to this point mythweb works fine*

Ran these commands try to setup a password:
  htpasswd - c /var/www/htpasswd root

sudo gedit /etc/apache2/enabled-sites/mythweb.conf (not sure if this is the correct file to modify)
  added the following below the line <Directory "/var/www/mythweb">
    AuthType Basic
    AuthName "My Private Directory"
    AuthUserFile "/var/www/htpasswd"
    Require valid-user
  </Directory>

now I'm getting error from other computer on my LAN to [http://10.0.0.102:81](http://10.0.0.102:81)
  "Unable to connect
  Firefox can't establish a connection to the server at 10.0.0.102:81"

-- New to Ubuntu: I'm a Windows user who is trying to get away from Windows :p

PS: Loving this feature in MythBuntu with setup recording over the web, something Media Center can't do. Just trying to make it more secure now.

---

### Post by redconfusion on 2010-07-09
Fixed it the </Directory> is not needed.

-- Love it when can answer your own questions :D

---

