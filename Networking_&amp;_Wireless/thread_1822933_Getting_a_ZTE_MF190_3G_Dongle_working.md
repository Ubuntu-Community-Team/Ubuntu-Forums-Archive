---
title: "Getting a ZTE MF190 3G Dongle working"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by CuervoJoe on 2011-08-11
Hey everyone. I installed Ubuntu 11.04 through Wubi this morning to try it out. I'm very impressed with the OS, but there is one problem. I use a 3G USB modem to access the internet, as my phone line was damaged and will take up to 2 years(!) to repair, so a dongle is my only option. 

When I plug the dongle in, it's a 50-50 chance that it works, however, when it is recognized, I get the folder on my desktop, however the files are all .exes. I've tried adding a mobile broadband connection, but to no luck. It works fine and fast on Win 7. As I said, this is the only internet connection I have. When I ran lsusb the device was in the list, but I can't install the drivers, and so I can't access the internet. 

Is there a solution to this problem? Thanks.

Also, with Wubi, is linux still as secure as it would be in a stand-alone installation, or is it vulnerable to Windows Viruses? By which I mean that, if I clicked on a link to a page with a Windows Virus, would it infect Windows on my PC, as it is still in the same partition?

EDIT: It is now recognized, but only if I first log on to windows and log on to the network first, then it's recognized, but it still won't connect. It tries, then disconnects me.

---

### Post by pdc on 2011-08-11
do you know how to open a terminal?

(accessories and then terminal)

if you type in 

> lsusb    and hit the ENTER key

and copy and paste back what you get

---

### Post by CuervoJoe on 2011-08-12
Thanks for your reply, pdc
When I type in lsusb at the terminal, I get this:

Bus 005 Device 002: ID 15d9:0a4c Trust International B.V.
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 064e:a103 Suyin Corp
Bus 002 Device 002: ID 19d2:0124 ONDA Communication S.p.A
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by pdc on 2011-08-12
> Bus 002 Device 002: ID 19d2:0124 ONDA Communication S.p.A

so likely from this 

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=420&sid=b4217ebdd15c270bbc9f2a461d4236f4](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=420&sid=b4217ebdd15c270bbc9f2a461d4236f4)

that on ubuntu it is switched to being seen as a modem

if you copy and paste

> dmesg | grep tty

into a terminal, if you copy and paste results back ..you should see ttyUSB0 and ttyUSB1 etc

if you see these, the modem should be ready to dial; so if no joy, the other option as a dialler is to install sakis 3g; I have found it works well

you have options for how to run it; I used a graphical mode

[http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_UI](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_UI)

[http://www.sakis3g.org/](http://www.sakis3g.org/)

---

### Post by CuervoJoe on 2011-08-14
Thanks again.

But what is this character? (In between dmesg and grep):
dmesg **|** grep tty

Just want to know so that I can type it in.

---

### Post by pdc on 2011-08-14
that's why I said

> if you **_copy and paste_**

Quote:
dmesg | grep tty 

It's called a pipe command

explained here: look up piping on this page: [http://www.tuxfiles.org/linuxhelp/iodirection.html](http://www.tuxfiles.org/linuxhelp/iodirection.html)

it is 

Shift-\ 

on your keyboard

---

### Post by CuervoJoe on 2011-08-15
> **pdc said:**
> so likely from this 

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=420&sid=b4217ebdd15c270bbc9f2a461d4236f4](http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=420&sid=b4217ebdd15c270bbc9f2a461d4236f4)

that on ubuntu it is switched to being seen as a modem

if you copy and paste



into a terminal, if you copy and paste results back ..you should see ttyUSB0 and ttyUSB1 etc

if you see these, the modem should be ready to dial; so if no joy, the other option as a dialler is to install sakis 3g; I have found it works well

you have options for how to run it; I used a graphical mode

[http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_UI](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_UI)

[http://www.sakis3g.org/](http://www.sakis3g.org/)


I did that, and I did get those results, however, it still disconnects me instantly. I added the PIN to the network configuration screen, and still disconnects me. Would sakis 3g help that?

---

### Post by pdc on 2011-08-15
> Would sakis 3g help that? 

you can but try it;

[http://www.sakis3g.org/#download](http://www.sakis3g.org/#download)

at its rawest, you run it from a terminal;

there is a debug mode; that should describe problems

[http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_troubleshooting](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_troubleshooting)

see debug 1/2 way down page

and sakis oversees his forum

[http://forum.sakis3g.org/smf/index.php](http://forum.sakis3g.org/smf/index.php)

so a very good place to get advice; if you install sakis: it is quick to do; and you should get some good diagnostics;

let us know how it all goes

---

### Post by rport on 2012-05-27
Hello, let me post here how it's been possible for me to get the ZTE MF190 working under SuSE 11.3; maybe it's useful for Ubuntu fellows as well.  The path to success has been a collection of actions gathered from all over the internet; maybe not all of them are necessary.

Step 1:  Download  vodafone-mobile-connect-2.20.01-4.noarch.rpm  from  [https://forge.betavine.net/frs/?group_id=12&release_id=272](https://forge.betavine.net/frs/?group_id=12&release_id=272) .  Installing (# rpm -ivh vodafone-mobile-connect-2.20.01-4.noarch.rpm) will fail until you have first installed python-serial, python-twisted, python-twisted-conch, and python-crypto.  (Get these from your distribution, don't download the .rpm's from anywhere, if at all possible, because every version requires different libraries.)  Now, finally, "rpm -ivh vodafone-mobile-connect-2.20.01-4.noarch.rpm" works
and installs the Vodafone Mobile Connect driver for Linux.  

Step2:  Insert the USB stick.

lsusb will show it:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 003: ID 0c45:6480 Microdia 
Bus 001 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 004: ID 0566:3107 Monterey International Corp. 
Bus 002 Device 006: ID 19d2:0117 ONDA Communication S.p.A. 

It's the thing called  ONDA Communication S.p.A. .  

You will also find these links in /dev/serial/by-id:

ls -l /dev/serial/by-id

lrwxrwxrwx 1 root root 13 May 25 20:28 usb-ZTE_Incorporated_1_1_Surf-stick_MF19001MOD010000-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 May 25 20:28 usb-ZTE_Incorporated_1_1_Surf-stick_MF19001MOD010000-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 May 25 20:28 usb-ZTE_Incorporated_1_1_Surf-stick_MF19001MOD010000-if02-port0 -> ../../ttyUSB2



Step 3:  I found a file

/etc/modprobe.d/blacklist-vmc

having the line:

blacklist onda

and deleted this line.  (Not sure whether this step was really necessary.)

Step 4:  Start the USB stick driver:

/usr/bin/vodafone-mobile-connect-card-driver-for-linux-debug

This produces lots of messages in the command window and opens a menu window.  The driver doesn't recognize the ZTE MF190.  Go to Custom device settings; enter:

Device type:             Serial
Data port device:     ttyUSB2
Control port device:  ttyUSB1 

Speed connection:  I left the default, 115200, unchanged.

Hit OK, it will ask for the USB stick password, then take a while, then open another menu window.  Hit Connect, and, believe it or not, it will connect to the internet.  (If you look into  /etc/resolv.conf  you'll find one or two lines with nameserver addresses that were not there before.)

The crucial trick seemed to get the entries under "Data port device" and "Control port device" right; no other combination worked, and ttyUSB0 seems to be useless.

Good luck!

---

### Post by oldos2er on 2012-05-27
Old thread closed.

---

