---
title: "Wind mobile Huawei E181 USB broadband not working."
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by PepeLapiu on 2010-10-19
Okay, Ijust installed 10.10 on a my new Aspire One Acer netbook and I got a mobile broadband USB stick from Wind mobile.

The stick is activated because it works on my 20 GB Windoze 7 O.S. but it doesn't work at all on my 140 GB Ubuntu O.S. 
Both systems are on the same machine so I know it's not a hardware problem either.

Here's what happens:
I log on to Ubuntu, plug in the stick and I select the "New mobile broadband GSM connection" in the network connections menu.

From there I selected my country (Canada) and my mobile provider (Wind Mobile) than I selected my plan (Mobile Broadband) and my APN (broadband.windmobile.ca).

Then the stick blinks slowly and the network icon looks forever for a connection but no matter how long I wait no connection ever establishes. My roomate has it working on his HP laptop Ubuntu but no luck on mine. The stick just keeps blinking, a steady light indicates a connection. 

Any solutions or ideas?

Thanx,
PepeLapiu :)

---

### Post by pdc on 2010-10-19
tell us what lsusb says;


and 

> dmesg | grep tty (copy and paste that one)

if you don't get ttyUSB0 (or ttyACM0) you will need

usb_modeswitch

a good way to install it is to install the sakis3g package;

it does all your connecting for you;

[http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_installation)

here is a how-to

---

### Post by PepeLapiu on 2010-10-21
here are the results:

```
pepelapiu@pepelapiu-AO532h:~$ dmesg | grep tty 
[    0.000000] console [tty0] enabled
[   15.951812] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[   15.952175] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[   15.952447] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB2
pepelapiu@pepelapiu-AO532h:~$ sudo bash
[sudo] password for pepelapiu: 
root@pepelapiu-AO532h:~# apt-get install ppp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ppp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 52 not upgraded.
root@pepelapiu-AO532h:~# cd /usr/bin
root@pepelapiu-AO532h:/usr/bin# wget 'http://www.sakis3g.org/versions/latest/sakis3g.gz'
--2010-10-20 22:09:16--  http://www.sakis3g.org/versions/latest/sakis3g.gz
Resolving www.sakis3g.org... 62.169.195.82
Connecting to www.sakis3g.org|62.169.195.82|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.sakis3g.org/versions/latest/i386/sakis3g.gz [following]
--2010-10-20 22:09:17--  http://www.sakis3g.org/versions/latest/i386/sakis3g.gz
Reusing existing connection to www.sakis3g.org:80.
HTTP request sent, awaiting response... 200 OK
Length: 200217 (196K) [application/x-gzip]
Saving to: `sakis3g.gz.1'

100%[============================================================================>] 200,217     50.0K/s   in 4.1s    

2010-10-20 22:09:22 (47.1 KB/s) - `sakis3g.gz.1' saved [200217/200217]

root@pepelapiu-AO532h:/usr/bin# echo "dda70fd95fb952dbb979af88790d3f6e  sakis3g.gz" | md5sum -c
sakis3g.gz: OK
root@pepelapiu-AO532h:/usr/bin# You should see: sakis3g.gz: OK
You: command not found
root@pepelapiu-AO532h:/usr/bin# gunzip sakis3g.gz
root@pepelapiu-AO532h:/usr/bin# chmod +x sakis3g
root@pepelapiu-AO532h:/usr/bin# 

```

Still stick not working. I'm going to restart and see if that changes anything.

---

### Post by PepeLapiu on 2010-10-21
Nope, still not working. what's next?

---

