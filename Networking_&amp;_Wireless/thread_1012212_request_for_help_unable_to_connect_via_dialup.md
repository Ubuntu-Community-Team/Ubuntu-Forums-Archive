---
title: "request for help: unable to connect via dialup"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by DDBrewer on 2008-12-15
I am new to Linux and Ubuntu.  I recently took a Pentium IV PC in very good condition running Vista, and successfully installed Ubuntu 8.04 to the whole disk (no partition with Vista). My final task is to get the internal modem working (I’m preparing this machine for someone who has dialup internet access only).  

I’ve been unable to connect to the internet with the modem, and I’m posting to seek help.  I’ve searched this board for relevant threads and followed various instructions for configuring and running the modem.  Here’s what I’ve done:

I know the phone jack and dialup ISP both work – I’ve used both with a Win XP machine’s internal modem (with very quick configuration).  

I first ran scanModem and found the necessary precompiled drivers (hsfmodem_7.68.00.14full_i386.deb) at linuxant.com.  I downloaded, extracted, and installed the drivers.

I tried the Network Admin, wvdialconf/wvdial, and pppconfig/pon approaches described at [https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f5120acdc3ef62fe7d37bfd3f0c9157ebe9c8ef") and [http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html]("http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html").  

When I tried to connect with the Network Admin approach (using the network connection icon at the upper right of the Ubuntu desktop >> Dial-up connections >> Connect to ppp0 via Modem), nothing happens.  

When I tried connecting via “sudo wvdial” in the terminal, I got this error message:
~$ sudo wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
&#61672; Configuration does not specify a valid login name.

The login name is accurate, because I used it successfully on the system running XP.  

When I tried to connect via pon (after configuring with pppconfig), I got this error message:
Dec 15 12:40:16 carolyn-desktop pppd[6450]: pppd 2.4.4 started by carolyn, uid 1000
Dec 15 12:40:17 carolyn-desktop chat[6452]: Can't get terminal parameters: Input/output error
Dec 15 12:40:17 carolyn-desktop pppd[6450]: Connect script failed
Dec 15 12:40:18 carolyn-desktop pppd[6450]: Exit.

This is apparently the same problem that responder #11 in this thread ([http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html]("http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html")) had, but apparently there was no further discussion of his problem.  

I am at a loss for what to do.  I can provide full output from the scanModem run and wvdialconf if that would help with diagnosis.  I’d prefer a GUI for connecting because the person who will use this system has limited computer skills/experience.  I was able to download gnome-ppp (apparently not in the Ubuntu repository) but couldn’t get it to be installed or operate.  

The system is perfect except for this dialup problem.  Any help or advice would be much appreciated.

Thank you!

---

