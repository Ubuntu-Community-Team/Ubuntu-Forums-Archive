---
title: "SSH login error after new install on the server"
date: 2006-04-21
forum: Networking &amp; Wireless
---

### Post by hedge on 2006-04-21
We reciently had a server spit out a HD so after the reinstall of Fedora Core 3, from my ubuntu box I get this error below. After LMAO! at it, I tried importing the key as per the wiki instructions and it fails to connect and import. Can someone please help with this?

thx

hedge

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX..
Please contact your system administrator.
Add correct host key in /home/jmb/.ssh/known_hosts to get rid of this message.
Offending key in /home/jmb/.ssh/known_hosts:1
RSA host key for oaihosting.net has changed and you have requested strict checking.
Host key verification failed.

---

### Post by Jason_25 on 2006-04-21
```

rm /home/jmb/.ssh/known_hosts

```

On the client PC, then try connecting again.

---

### Post by cgjones on 2006-04-21
There is no need to delete the entire know_hosts file. Just open it up in a text editor and remove the line pertaining to the server you are trying to connect to.

---

### Post by hedge on 2006-04-21
[quote=cgjones]There is no need to delete the entire know_hosts file. Just open it up in a text editor and remove the line pertaining to the server you are trying to connect to.[/quote]


cgjones thanks for the help worked well...

thx again 

hedge

---

### Post by cgjones on 2006-04-22
And I meant to say known_hosts, not know_hosts. Glad I could help.

---

### Post by buntunub on 2007-09-04
It is truly Ubuntu's userbase that make this Distro as great as it is. This really helped me out quite alot and this exact problem has been nagging me for the last week lol. Thanks guys!

---

