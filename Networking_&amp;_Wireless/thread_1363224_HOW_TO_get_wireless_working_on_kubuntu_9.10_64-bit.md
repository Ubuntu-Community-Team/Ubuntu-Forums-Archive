---
title: "HOW TO get wireless working on kubuntu 9.10 64-bit"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by 4uvak91 on 2009-12-24
Hi, 

I have buffalo wli-u2-ag108hp wireless adapater, but I dunno how to get working it on kubuntu...coz I'm without internet connection on kubuntu. So I think I need to download something on my PC, windows 7 and install it through USB on kubuntu then...So can You help me to solve this out, please !


PS. I'm new to kubuntu, but I have used Ubuntu...but it doesn't help I think coz the GUI is totally different...
:confused:

---

### Post by 4uvak91 on 2009-12-25
No one can't help, even give any advice!?

---

### Post by coffeecat on 2009-12-25
Is that a USB device? We need to know the wireless chipset in it. Open a terminal with it plugged in and post the output of:

```
lsusb
```

---

### Post by jmlynn on 2009-12-25
Hi, I installed dual boot on my Dell M90 "transportable" laptop.  First OS is Ubunto 9.10 and second OS is Windows 7.

My Windows 7 boots and works fine with full connection to network and internet.

However, my Ubuntu 9.10, boots and works fine except no WiFi access.
Tried manual IP address with gateway, DNS Wifi Security and password (for the WPA router) specified, but what I got was "device not ready".

Tried lspci | grep 802.11, got the following:
"0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev01)"

Any idea how to get this going?

Appreciate any help I can get!

jml

---

### Post by hachre on 2009-12-25
> **jmlynn said:**
> Hi, I installed dual boot on my Dell M90 "transportable" laptop.  First OS is Ubunto 9.10 and second OS is Windows 7.

My Windows 7 boots and works fine with full connection to network and internet.

However, my Ubuntu 9.10, boots and works fine except no WiFi access.
Tried manual IP address with gateway, DNS Wifi Security and password (for the WPA router) specified, but what I got was "device not ready".

Tried lspci | grep 802.11, got the following:
"0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev01)"

Any idea how to get this going?

Appreciate any help I can get!

jml

You need to connect via Ethernet and open the Hardware Drivers menu in System -> Administration to install the Broadcom STA Driver.

---

### Post by bkratz on 2009-12-25
If you really don't even have a wired connection, you might achieve what you need through this thread

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by 4uvak91 on 2009-12-25
> **coffeecat said:**
> Is that a USB device? We need to know the wireless chipset in it. Open a terminal with it plugged in and post the output of:

```
lsusb
```


Ya it's USB device & and tnx I try it

@bkratz, well yes i have wired connection...but it's in other room so thats why i have wireless connection

---

### Post by 4uvak91 on 2009-12-25
> **coffeecat said:**
> Is that a USB device? We need to know the wireless chipset in it. Open a terminal with it plugged in and post the output of:

```
lsusb
```


```
ubuntu@ubuntu:~$ sudo lsusb
Bus 002 Device 003: ID 0411:00af MelCo., Inc.
Bus 002 Device 002: ID 0c45:62b3 Microdia
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 045e:00dd Microsoft Corp.
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0930:6545 Toshiba Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ubuntu@ubuntu:~$
```

it's that Bus 002 Device 003: ID 0411:00af MelCo., Inc.


One more question, this USB adapter doen't seem to work with win 7 64-bit (i have tried it)...so will it work with 64-bit kubuntu!?

---

### Post by jmlynn on 2009-12-26
I downloaded the latest Broadcom STA driver, unzip it, and ran make.  Got following warning:
"missing MODULE_LICENSE() in /.../Downloads/wl.o"
A few *.0 files were produced.
How do I install it?  I browse the System/Administrator/Hardware Drivers and found nothing

Thanks!

jml

---

### Post by jmlynn on 2009-12-26
I followed the advice to use yum as suggested to install yum.  However, I encountered the following error:
"Couln't find package yum"

I am runing Ubuntu 9.10.

Thanks!

jml

---

### Post by 4uvak91 on 2009-12-26
@ jml, dude why do you write on my topic btw, you have complitely different problem...:confused:

---

### Post by 4uvak91 on 2009-12-26
> **bkratz said:**
> If you really don't even have a wired connection, you might achieve what you need through this thread

[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

but this is for ubuntu, i have kubuntu...does it work on kubuntu!? 
[http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source)

---

### Post by jmlynn on 2009-12-26
Thanks for the help!  I managed to find a ethernet cable and plugged it in and did and update.  Now I got the Broadcom STA driver installed and it works now.  Thanks

---

### Post by focwiz on 2009-12-26
> **jmlynn said:**
> I downloaded the latest Broadcom STA driver, unzip it, and ran make.  Got following warning:
"missing MODULE_LICENSE() in /.../Downloads/wl.o"
A few *.0 files were produced.
How do I install it?  I browse the System/Administrator/Hardware Drivers and found nothing

Thanks!

jml

From the BROADCOM Readme file....

I see this output, is it harmful?  WARNING: modpost: missing MODULE_LICENSE()
No it is not harmful and it is expected and should be ignored.

The readme file has a lot of useful info...RTFM?

---

### Post by bkratz on 2009-12-26
> **4uvak91 said:**
> but this is for ubuntu, i have kubuntu...does it work on kubuntu!? 
[http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source)



Sorry, I was replying to the gentlemen who jumped into your thread and I didn't notice there were two different people involved. I didn't pay enough attention.

---

### Post by bkratz on 2009-12-26
> **4uvak91 said:**
> @ jml, dude why do you write on my topic btw, you have complitely different problem...:confused:




I did a quick google and found that your device apparently uses the RT2870 drivers here is a link you might want to look at and see if it is any help.

[http://ubuntuforums.org/showthread.php?t=1342593&highlight=0411:00af](http://ubuntuforums.org/showthread.php?t=1342593&highlight=0411:00af)


Here is another

[http://ubunturt2870.pbworks.com/FrontPage](http://ubunturt2870.pbworks.com/FrontPage)

Good Luck

---

### Post by 4uvak91 on 2009-12-26
> **bkratz said:**
> I did a quick google and found that your device apparently uses the RT2870 drivers here is a link you might want to look at and see if it is any help.

[http://ubuntuforums.org/showthread.php?t=1342593&highlight=0411:00af](http://ubuntuforums.org/showthread.php?t=1342593&highlight=0411:00af)


Here is another

[http://ubunturt2870.pbworks.com/FrontPage](http://ubunturt2870.pbworks.com/FrontPage)

Good Luck


Is that for me :P?

---

### Post by bkratz on 2009-12-26
> **4uvak91 said:**
> Is that for me :P?



Yes   (as long as you are 4uvak91!)



I found these when I searched for 0411:00af

---

### Post by 4uvak91 on 2009-12-26
> **bkratz said:**
> Yes   (as long as you are 4uvak91!)



I found these when I searched for 0411:00af


Ok, tnx...I'll try it!

---

