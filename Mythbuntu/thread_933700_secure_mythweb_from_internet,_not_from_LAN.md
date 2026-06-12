---
title: "secure mythweb from internet, not from LAN"
date: 2008-09-29
forum: Mythbuntu
---

### Post by trakie on 2008-09-29
so i have been searching for a way to secure mythweb (or apache) from the internet but not from the LAN.  i am behind a router and right now i did not set up port forwarding for mythweb (yet).  i would like to be able to access mythweb from the internet, but with a username/password, however i would still like to be able to access mythweb from the LAN without a username/password.  while reading the mythtv.org wiki on securing mythweb i found out this option is available, however the example is geared to openSUSE and not ubuntu, and they never explain it very well ( [http://www.mythtv.org/wiki/index.php/Securing_MythWeb](http://www.mythtv.org/wiki/index.php/Securing_MythWeb) ). 

can anyone give me some help or point me in the right direction?

thanks

---

### Post by anonymousdog on 2008-09-29
You'll need to know what your local network's IP address space is.

Start here: [https://help.ubuntu.com/community/MythWeb](https://help.ubuntu.com/community/MythWeb) (except you edit /etc/apache2/sites-enabled/mythweb.conf instead of /etc/apache2/http.conf).  I also use /etc/mythtv/.htaccess for my htpasswd file (instead of /etc/apache2/httpd-passwords).

Once you've got that working (which will require auth internally, from localhost, and externally), change "require user MYUSER1 MYUSER2 MYUSER3" to "require valid-user".  That way you can just add users to the password file without reconfiguring the mythweb.conf file.  Next, change "Allow from all" to "Allow from Local.network.ip.addr" (e.g., if your network is 192.168.0.0, "Allow from 192.168.0.") and add a line "Allow from 127.0.0." to allow unauthenticated access from the server.  Note the trailing dot and lack of a final, host, octet in the address (i.e., shorthand for the local host and local network addresses).  Finally, just after the "Allow from..." lines, add a line "Satisfy any" and comment out any other uncommented "Satisfy..." lines.

Restart apache, 'sudo /etc/init.d/apache2 restart', and surf to mythweb from localhost.  It should not require any authentication.  Surfing from anywhere in your LAN will be the same.  Once you set up PAT, connecting from any internet location will require auth.

If you have wap devices (e.g., a PDA), you'll need a separate htpasswd credentials for that device, or you'll end up with the wap theme for mythweb on any device from which you surf mythweb and use a credential set you've used before on a wap device.  So, I have some general user accounts and one for all wap devices.

---

### Post by trakie on 2008-09-29
thank you for that, anondog, very helpful. 

however, there is still one thing - as noted in ( [http://www.mythtv.org/wiki/index.php/MythWeb](http://www.mythtv.org/wiki/index.php/MythWeb) ) right above the Troubleshooting section it mentions: "NOTE: I have found that "Allow from 192.168.1." does not work correctly when your webserver is behind a router, as any traffic forwarded over the router will appear to originate from 192.168.1.1 (or whatever your router's IP is). This will cause ANY outside traffic to satisfy the "Any" requirement. -- craftyguy".  i have just found this to be the case for me, is there any way around this?

---

### Post by anonymousdog on 2008-09-29
Here's the sequence in my mythweb.conf:```
        AuthType           Basic
        AuthName           "MythWeb"
        AuthUserFile       /etc/mythtv/.htaccess
        Require            valid-user
        BrowserMatch       "MSIE"      AuthDigestEnableQueryStringHack=On
     Order              allow,deny
    Allow from 10.0.10.
    Allow from 127.0.0.
        Satisfy            any
```
That works just fine on my home LAN (on 10.0.10.0/24) behind a typical home wireless router (and a DSL modem that acts as a router doing 1:1 NAT).  A properly NATting/PATting router should masquerade source IPs (of internal hosts) to the external hosts, not the other way around.  Regardless, there may be some home routers that try to NAT/PAT that way (i.e., using SNAT and DNAT both on incoming traffic).

My apache logs show external IPs for traffic initiated from the outside.```
69.89.124.114 - remote_host [29/Sep/2008:18:14:25 -0400] "GET /mythweb/streamtv HTTP/1.0" 200 123730 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.2) Gecko/2008091620 Firefox/3.0.2"
```Check your /var/log/apache2/access.log for traffic logs.

---

### Post by trakie on 2008-09-30
thank you again,

the problem (i think) was i was using the external address (through dyndns) from an internal computer, i guess that is not enough to fool the router.  to test again i went to a proxy site and then put in the external address, which prompted me for a username/password.  ill have to double check it when i get to work today, but i think its now working to my needs.

---

