---
title: "Dialup problem: ppp0 interface isn't there?"
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by apeitheo on 2006-03-04
I recently installed wvdial to configure dialup, and all worked well until I went to get on the internet. It seems ppp0 isn't up (or is it?) when I type ifconfig I only see 'lo' and no 'ppp0.' Wvdial **is** connected though, the interface simply isn't there...

When I load up wvdial and finally connect it shows:

```
--> WvDial: Internet dialer version 1.53
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT**********
--> Waiting for carrier.
ATDT**********
CONNECT 115200
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Mar  4 20:49:26 2006
--> pid of pppd: 2876
```
and stays there, connected, but pinging anything (domains or ip addresses give me "Network unreachable")

I haven't a clue how to resolve this issue, I would appreciate any help in solving this. Thank you.

**EDIT:**

Hmm, I just set this up using the same version of wvdial (1.54.0) on another computer (running Slackware) and got this after the last line of the output above (after "--> pid of pppd: 2876") :
```
--> Using interface ppp0
--> Authentication (PAP) started
--> Authentication (PAP) successful
--> local  IP address 4.238.147.174
--> remote IP address 209.244.30.249
--> primary   DNS address 204.122.16.8
--> secondary DNS address 204.122.16.9
--> Script /etc/ppp/ip-up run successful
--> Default route Ok.
--> Nameserver (DNS) Ok.
--> Connected... Press Ctrl-C to disconnect

```
For some reason Ubuntu is having trouble using the ppp0 interface, why is this? I'll google around and see if I can find anything.

---

### Post by Bentu on 2006-03-05
I'm thinking from your post that you're not able to actually get to the web? If so, I suspect that your problem is with your driver, either you installed the wrong one or something happened to it during the installation. I would make sure that I had the correct driver and, if so, do an uninstall and the install it again.

---

### Post by apeitheo on 2006-03-05
Well I can get to the web with 'pon' (or manually configuring pppd and running it manually) and it works fine. I just needed to use wvdial for "gnome-ppp," since that's a frontend to wvdial.. and if wvdial isn't working, neither is gnome-ppp. I tried out the program, gkdial (frontend to pppd instead of wvdial), and I can actually use the web with it, but there is a minor glitch in that it doesn't ever stop saying "dialing..." and so I just have to minimize it instead of it automatically disappearing into the notification area next to the clock (which I want). It doesn't have to be gnome-ppp or gkdial, I just want a graphical dialer for Gnome that actually WORKS (I've tried about five of them and none of them work fully). Gkdial works partially, at least enough for my parents to use it for now, so I don't need a solution immediately (though for long-term it'd be nice to have a completely working solution).

---

### Post by towsonu2003 on 2006-03-05
here's what I always get with wvdial: ```
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at xxxxxxxxxxxxxxxxxxxxxxxxx
--> pid of pppd: 9545
--> Using interface ppp0
--> local  IP address xxxxxxxxx
--> remote IP address xxxxxxxxxx
--> primary   DNS address xxxxxxxxxxxxxxxxx
--> secondary DNS address xxxxxxxxxxxxxxxxx

```
Using interface: ppp0 means ppp is up and your computer is negotiating with the server. From my experience, until you see your ip address there you're not connected. Wait for ppp0 to exit / die (should die within a couple of minutes) and look at the error. this should give some insight to what's going on. 

If it doesn't exit at all, maybe a bug report to its developers?[1] tweak driver configuration? but, I'd say: don't fix what ain't broke (you can get connected, so don't tweak your stuff). a google search for something like vwdial ppp0 exit problem"?

[1]we don't have enough experienced dial up users here...

edit: you put your username and password to wvdial.conf, right? just making sure :p

---

### Post by apeitheo on 2006-03-07
Well, I no longer need to use wvdial, because I decided I'd fix up the gkdial program since I have C skills, and figured I might as well put them to use for something that Gnome is currently lacking :) It was just a quick job, however, so the code is quite messy, but at least it works. I'll have to clean it up before considering releasing it anywhere. If anyone is interested, let me know and I'll send you the tarball.

I'm probably not having it detect if the ppp0 interface is up in the correct manner (though it works fine), but the old method doesn't work anymore (for whatever reason, I'm not sure -- I'll see if I can find out).

---

### Post by georgewa on 2006-03-08
How does a beginner using the Ubuntu 5.10 install disks set-up a dial up connection? Is there an application aside from gnome ppp that will do it already installed with the package?

To my novice eye, it does not look like ppp comes with the installed desktop package even though some instructions for 5.04 ver say this is what you need to do a dial out connection. It does look like you can go and download gnome ppp and a dialer program from the author's website, and I just did it, but there is not a ubuntu 5.10 ver ( yes debian ver which is close I guess) . 

Suggestions??? Thank you.

WG

---

### Post by towsonu2003 on 2006-03-08
[QUOTE=georgewa]
To my novice eye, it does not look like ppp comes with the installed desktop package even though some instructions for 5.04 ver say this is what you need to do a dial out connection. It does look like you can go and download gnome ppp and a dialer program from the author's website, and I just did it, but there is not a ubuntu 5.10 ver ( yes debian ver which is close I guess) . 
[/QUOTE]
check out the second link in my signature. different ways to dial up are towards the bottom of the page. My understanding is that dial up is not a priority for ubuntu (and for many other distros). 
an easy way (if no winmodem) without installing anything is System>Networking>Modem>Properties>Enable this <whatever>>input your isp information>activate

If you've got a winmodem, well, uhm, you're pretty much screwed as a newbie :-# . winmodem information is in that link in my signature as well.

---

