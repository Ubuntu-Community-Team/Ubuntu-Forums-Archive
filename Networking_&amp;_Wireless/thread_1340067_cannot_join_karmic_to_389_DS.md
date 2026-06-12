---
title: "cannot join karmic to 389 DS"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by tenmoi on 2009-11-28
HI everyone,

I set up 389 DS on fedora 12 x64 and is trying to join karmic x64 to this server to no avail.

(Fedora 11 client and even winxp can join it without problem)

At first I did this:

[HTML]
auth-client-config -t nss -p lac_ldap
pam-auth-update ldap
[/HTML]

getent passwd could retrieve the domain server user, which is ubuntu if you are interested.

I logged out and back using the ubuntu user credentials and karmic said it could not create ICEauthority and blah blah. (THis together with the result of getent does prove the fact that Karmic could reach the DS server, though)

Second,
I wiped karmic out and did a fresh install only to find that it won't bind to the server for what reasons I do not know. So please help!

########################################################
I have tried:
logging on the DS server from fedora 11 and winxp: successful
-from karmic:
nslookup the DS server: successful
ping the DS server: successful

[COLOR="Red"]ldapsearch: unsuccessful[/COLOR] 
(ldapsearch -x -h server_IP -base "dc=example,dc=com" 'uid=ubuntu')
getent passwd ubuntu returns nothing

What have I done wrong? Or ubuntu distros are not ready for enterprise environment yet!

THank you.

P.S
I have uninstalled apparmor on karmic and disabled firwall and selinux on fedora 12 (DS server).

---

### Post by tenmoi on 2009-11-28
hm.
REstart the server and done!

---

### Post by tenmoi on 2009-11-28
But when logging on the DS server from karmic there was this nagging: 

"Could not update ICEauthority file /home/blalba/.ICEauthority "

CLicking on CLOSE and you are presented with some more errors messages. And finally, you see that familiar background of karmic with nothing to click on.

To solve this:

#nano /etc/pam.d/common-session

and add this line to the bottom:

session required pam_mkhomedir.so umask=0022 skel=/etc/skel

And happily you go!

Just wonder how this error can ever happen.

---

