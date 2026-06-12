---
title: "Orange Israel 3G, Connects then Hangs up"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by thelonecabbage on 2010-01-29
I'm tying to connect to Orange, the ZTE MF637 identifies and works (after usb_modeswitch and a little wait)

but it won't connect. 

the /var/log/messages is

Jan 29 15:09:13 Spud pppd[4732]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Jan 29 15:09:13 Spud pppd[4732]: pppd 2.4.5 started by root, uid 0
Jan 29 15:09:13 Spud pppd[4732]: Using interface ppp0
Jan 29 15:09:13 Spud pppd[4732]: Connect: ppp0 <--> /dev/ttyUSB2
Jan 29 15:09:13 Spud pppd[4732]: CHAP authentication succeeded
Jan 29 15:09:13 Spud pppd[4732]: CHAP authentication succeeded
Jan 29 15:09:20 Spud pppd[4732]: Modem hangup
Jan 29 15:09:20 Spud pppd[4732]: Connection terminated.
Jan 29 15:09:21 Spud pppd[4732]: Exit.

does anyone have any recommendations?

---

### Post by pdc on 2010-01-29
I have an MF636 modem, and I couldn't get it to connect on network manager, and used wvdial;

I used a wvdial.conf adapted from one George Vita quoted

and i have taken the liberty of pasting in what i believe are orange israel's apn settings 

[http://modmyi.com/wiki/index.php/Carrier_APN_Settings#Orange__.28Israel.29](http://modmyi.com/wiki/index.php/Carrier_APN_Settings#Orange__.28Israel.29)

> 
[Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = orange
Password = orange
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","internet"
Phone = *99#
Stupid Mode = 1


if you wish to see if this works, install wvdial by

> sudo apt-get install wvdial

then paste the above commands into the empty file 

> sudo gedit /etc/wvdial.conf

paste the above, save and exit

load wvdial from the terminal

> sudo wvdial

and hopefully it connects; control-c disconnects

and you need to be a member of the dialout and dip groups

(hopefully you already are)

this tells you how to check and add

[http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

---

### Post by thelonecabbage on 2010-01-30
ok, so a bit better.  I'm able to connect, and to load pages (similar instructions at [www.linuxguide.org.il]("http://www.linuxguide.org.il/ubuntu/%D7%9E%D7%95%D7%93%D7%9D_%D7%A1%D7%9C%D7%95%D7%9C%D7%90%D7%A8%D7%99_%D7%91%D7%90%D7%95%D7%91%D7%95%D7%A0%D7%98%D7%95") also worked although I had to add fixed DNS addresses.  WVDial fetched the DNS address correctly.

**Both, have ridiculously bad speed.**  I run ping in the background and watch it load a page.  With NO network activity except the ping, I get 300-500ms ping times to google.  As soon as open a web page, it slows down to 4-8 seconds, ping time.  

I suspected it was some kind of concurrency issue with PPP.   

But then I used an ssh tunnel to download a largish file off of a remote server.  Which would certainly only use one socket.  The average speed was 4KB/s.  

Any Ideas?

---

### Post by pdc on 2010-01-30
no; I can only try to offer some assistance to connect;

so the /etc/wvdial.conf file that I suggested worked for you?

I guess others observing might suggest it was a "network" issue with your 3G provider? 

However I guess one could suggest that the baud rate in the script

> Baud = 460800

be increased by some multiples of this; it works fine for me but I have seen others suggest 2x or 4x or whatever

---

### Post by thelonecabbage on 2010-01-31
PDC!  Thankyou!

I set the baud x10, and that completely fixed it.

It now measures faster than my Cable modem! (with lower latency)

---

### Post by pdc on 2010-01-31
delighted to hear it works well! 

enjoy

---

