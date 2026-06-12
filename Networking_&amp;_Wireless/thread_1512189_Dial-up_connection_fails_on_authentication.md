---
title: "Dial-up connection fails on authentication"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by Lafon on 2010-06-17
Hi all. I have a softmodem and i got it to work in 10.04, but whenever I try to dial through wvdial or the graphical front gnome-ppp it always gets this error message:
me@my-desktop:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT6133450760
--> Waiting for carrier.
ATDT6133450760
CONNECT 460800 
belbrocnas01 line 94 
Unauthorized Access Prohibited
Acces non-autorise interdit
BELBROCNAS01 
User Access Verification
Username: 
--> Carrier detected.  Waiting for prompt.
Username: 
--> Looks like a login prompt.
--> Sending: cidc/c100w6145
cidc/c100w6145
Password: 
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed.
Username: 
--> Looks like a login prompt.
--> Sending: cidc/c100w6145
cidc/c100w6145
Password: 
--> Looks like a password prompt.
--> Sending: (password)
% Authentication failed.
Username: 
--> Looks like a login prompt.
--> Sending: cidc/c100w6145
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Thu Jun 17 20:20:17 2010
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 4394
--> Using interface ppp0
--> pppd: (&#65533;" P&#65533;" 
--> pppd: (&#65533;" P&#65533;" 
--> pppd: (&#65533;" P&#65533;" 
--> pppd: (&#65533;" P&#65533;" 
--> pppd: (&#65533;" P&#65533;" 
--> Disconnecting at Thu Jun 17 20:20:19 2010
--> The PPP daemon has died: Authentication error.
--> We failed to authenticate ourselves to the peer.
--> Maybe bad account or password? (exit code = 19)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 19)
.
(With gnome-ppp I don't even get the dial tone plus the sound of numbers dialling, though I get the static.)
The first time i tried dialling out it gave me an error message that I was missing something like bw43 cutter but after that the error never came up. Any idea what I can do. (Its pretty desperate; I have an exam I need to take online by this Sunday)
Thanks Lafon.

---

### Post by alexfish on 2010-06-18
hi

maybe permissions problem

have a look here

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

regards

alexfish

---

### Post by Lafon on 2010-06-18
I tried to run it as sudo but the only difference is that the cannot edit file error message doesn't appear

---

### Post by GeorgeVita on 2010-06-18
Hi **Lafon**,
using wvdial: check if the line 'Stupid mode = Yes' exist into your /etc/wvdial.conf 

at gnome-ppp check 'Ignore terminal strings (stupid mode)' at Settings>Options
(you can see attachments of [http://ubuntuforums.org/showpost.php?p=8153016&postcount=4](http://ubuntuforums.org/showpost.php?p=8153016&postcount=4))

Regards,
George

---

### Post by Lafon on 2010-06-18
I tried it in both stupid and regular modes but i get the same problems.

---

### Post by jonobr on 2010-06-18
Hello

try posting the results of
ls -l /etc/ppp/pap-secrets
ls -l /etc/ppp/chap-secrets

---

### Post by Lafon on 2010-06-19
Alright here it is
```
me@my-desktop:~$ls -l /etc/ppp/pap-secrets
-rw------- 1 root root 1690 2010-06-12 18:07 /etc/ppp/pap-secrets 
```
and
```

me@my-desktop:~$ls -l /etc/ppp/chap-secrets
-rw------- 1 root root 107 2010-06-12 18:07 /etc/ppp/chap-secrets 
```

---

### Post by alexfish on 2010-06-20
hi

the pap and chap are not part of dip

**Permissions for /etc/ppp/pap-secrets and etc/ppp/chap-secrets**

 If you want to save the username and password in gnome-ppp they are  saved in  /etc/ppp/pap-secrets and etc/ppp/chap-secrets and you need to give read and write access to them from group dip - if  you do not then you will get an warning message in the connection log.  This doeas not seem to have been done in the versions for hardy Heron  and Jaunty and I have not checked yet for Lucid but assume this is still  the case. In most cases this does not matter as the username and  password are not actually used or checked by most mobile internet  providers - they know who you are from the SIM which is already  registered before you can access data. Even so it is best to set these  permissions. I use a root file browser which is started in a terminal  by:


Code:

 gksudo nautilus


 You then navigate to folder /etc/ppp and right click on pap-secrets  -> Properties ->  Permissions tab then  select dip from the drop  down menu for Group and and then select read and write under Access.  Repeat for chap-secrets. The annoying warning messages should now  disappear.


also the output should look like


$ ls -l /etc/ppp/chap-secrets
-rw-rw---- 1[COLOR=Blue] root dip[/COLOR] 144 2010-05-28 18:08 /etc/ppp/chap-secrets


[http://www.pcurtis.com/ubuntu-mobile.htm#dip_dialout](http://www.pcurtis.com/ubuntu-mobile.htm#dip_dialout)


regards


alexfish

---

### Post by Lafon on 2010-06-20
Ok i did that but the only thing that happens is like running [COLOR="Red"]**[SIZE="2"]wvdial[/SIZE]**[/COLOR] as root (the "cannot edit the file" messages dont appear). i still get the "cannot connect to the peer" error message. in response to the previous post everything works as was posted. any idea whats happening?
Lafon

---

### Post by Lafon on 2010-07-15
Grrr... STILL no internet i think im just going to ask my dad to get hi-speed. ugh what horrible support for dial-up. hey is there any way to contact the creators of wvdial?
thanks by... well umm...ME!

---

### Post by ieee488 on 2010-07-15
To me, it looks like a problem of wrong username and wrong password.

---

### Post by Lafon on 2010-07-21
the thing is though im using the same username and password on another computer(windows) and it works. for another ive used these same entries in an earlier version of ubuntu.

---

### Post by Lafon on 2011-02-12
Ok guys i fixed it
just had to reinstall the package

---

