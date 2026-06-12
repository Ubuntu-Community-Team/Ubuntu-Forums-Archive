---
title: "Beginner-536ep on Ubuntu"
date: 2006-04-23
forum: Networking &amp; Wireless
---

### Post by lifeartist on 2006-04-23
I have installed 536ep on Ubuntu 5.10 successfuly, and i coonect via gnome-ppp(that has wvdial in background), then coonection breaks after 30-32 seconds. I live in Serbia&Montenegro, but I do not believe that my area causes the problem, since I am on digital phone line. Did anyone had similiar problems?

---

### Post by mips on 2006-04-23
What is 536ep ??? An ISDN card ?

---

### Post by lifeartist on 2006-04-23
536ep Intel chipset modem. Thnks 4 the link, by the way :)

---

### Post by lifeartist on 2006-04-24
Here's the log message copied from shell:

[FONT="Courier New"]GNOME PPP: Connecting...
GNOME PPP: STDERR: --> WvDial: Internet dialer version 1.54.0
GNOME PPP: STDERR: --> Initializing modem.
GNOME PPP: STDERR: --> Sending: ATX3
GNOME PPP: STDERR: ATX3
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Sending: ATX3
GNOME PPP: STDERR: ATX3
GNOME PPP: STDERR: OK
GNOME PPP: STDERR: --> Modem initialized.
GNOME PPP: STDERR: --> Sending: ATM1L3DT042110220
GNOME PPP: STDERR: --> Waiting for carrier.
GNOME PPP: STDERR: ATM1L3DT042110220
GNOME PPP: STDERR: CONNECT 31200
GNOME PPP: STDERR: --> Carrier detected.  Starting PPP immediately.
GNOME PPP: STDERR: --> Starting pppd at Mon Apr 24 11:33:00 2006
GNOME PPP: STDERR: --> pid of pppd: 9176
GNOME PPP: STDERR: --> Using interface ppp0
GNOME PPP: STDERR: --> pppd: TX3
GNOME PPP: STDERR: --> pppd: TX3
GNOME PPP: STDERR: --> pppd: TX3
GNOME PPP: STDERR: --> pppd: TX3
GNOME PPP: STDERR: --> pppd: TX3
GNOME PPP: STDERR: --> pppd: TX3
GNOME PPP: STDERR: --> Disconnecting at Mon Apr 24 11:33:35 2006
GNOME PPP: STDERR: --> The PPP daemon has died: A modem hung up the phone (exit code = 16)
GNOME PPP: STDERR: --> man pppd explains pppd error codes in more detail.
GNOME PPP: STDERR: --> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.[/FONT][/FONT]

Any ideas why would my modem hangup whit no reason?Bad driver? I found some people that made modem same as mine(INtel 536ep) to work on Breezy.

---

### Post by lifeartist on 2006-04-24
WEEEEEEEEE!!!!!!!!! i made it work. I'm online via Ubuntu :)  And connection is even better then in WinXP. I don't know whut I've done, I've justed waited and done nothing 30secs after coonection, and modem did not hanged up. :) :) :) :) :) :) :)

---

### Post by okaate on 2006-04-24
Well, I would like to ask any one of you who know and understand Xubuntu I have decide install xubuntu on our Pentium II s that we have recieaved from our donors. But most of them fail to copy some files when istalling ubuntu and fail to install.so I downloaded this Xubuntu and many are now installed but most of the commands seem to be not active. so please help me  I would like to configure them and also to learn more about LinuX
where and how can I config the network cards so connect to the internet.
Oscar Kaate
Zambia

---

