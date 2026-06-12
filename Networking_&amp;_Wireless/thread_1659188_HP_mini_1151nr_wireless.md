---
title: "HP mini 1151nr wireless"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by test_tube_baby on 2011-01-03
I have a HP mini 1151nr netbook and today i installed ubuntu netbook remix 10.10

it won't connect to the internet because it cannot identify my wireless driver, and i cannot install it because i can't connect it to the internet.

how do i go about this? i am a proper newbie at this

---

### Post by dr3@m3r on 2011-01-05
I also am about to experience this problem, seeing as my mom just gave me her 1151nr, verizon 3g netbook, and i am looking to have my wireless on it, not the 3g. In depth instrutions would be nice, cause i am a total noob to linux so far.

thx in advance

---

### Post by PatchesTheCaveman on 2011-01-05
I assume you found the driver in System > Administration > Additional Drivers but can't install it without Internet?

If you can't plug into a wired Ethernet connection (most routers have plugs in the back that let you plug your computer in), if you tell me the driver listed in the Additional Drivers screen I can give you the download links which you can then transfer over via flash drive and install.

---

### Post by test_tube_baby on 2011-01-10
Really? Will that work? I just uninstalled ubuntu but will install the netbook remix version again and get back to you about which drivers I need..

quick question, where do you get them from?

> **PatchesTheCaveman said:**
> I assume you found the driver in System > Administration > Additional Drivers but can't install it without Internet?

If you can't plug into a wired Ethernet connection (most routers have plugs in the back that let you plug your computer in), if you tell me the driver listed in the Additional Drivers screen I can give you the download links which you can then transfer over via flash drive and install.

---

### Post by Bucky Ball on 2011-01-10
If that's using Broadcom wireless card (and many HP machines do) I advise you try 10.04 LTS. 10.10 is having problems with Broadcom at the moment (killing wireless config). Before anyone get's excited, this is only on ***some*** machines with *most* Broadcom cards. Many are in the process of sorting this problem.

Also, if you are attempting to dual-boot with Windows, think again. 10.10 has a problem with side-by-side installs and wipes Windows. Again, only on *some* machines.

Check this:

[http://ubuntuforums.org/showthread.php?t=1653568](http://ubuntuforums.org/showthread.php?t=1653568)

That is about the problems with the current 10.10 kernel 2.6.35-24.

To new users: Latest is NOT always the greatest. 10.04 LTS is out since April 2010, has much longer support than 10.10, and will be a smoother ride. ;)

---

### Post by test_tube_baby on 2011-01-10
Is there a link to download the netbook remix 10.04 version? I can't find it anywhere. Will the netbook remix version support the Broadcom wireless?

> **Bucky Ball said:**
> If that's using Broadcom wireless card (and many HP machines do) I advise you try 10.04 LTS. 10.10 is having problems with Broadcom at the moment (killing wireless config). Before anyone get's excited, this is only on ***some*** machines with *most* Broadcom cards. Many are in the process of sorting this problem.

Also, if you are attempting to dual-boot with Windows, think again. 10.10 has a problem with side-by-side installs and wipes Windows. Again, only on *some* machines.

Check this:

[http://ubuntuforums.org/showthread.php?t=1653568](http://ubuntuforums.org/showthread.php?t=1653568)

That is about the problems with the current 10.10 kernel 2.6.35-24.

To new users: Latest is NOT always the greatest. 10.04 LTS is out since April 2010, has much longer support than 10.10, and will be a smoother ride. ;)

---

### Post by Bucky Ball on 2011-01-10
Torrent is the most reliable way:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

The regular ISO can be downloaded from the link below. You'll find it down the page a way under 10.04 LTS as:

[ubuntu-10.04.1-netbook-i386.iso.torrent]("http://releases.ubuntu.com/lucid/ubuntu-10.04.1-netbook-i386.iso.torrent")

(Don't click this link here as it won't work)

---

### Post by test_tube_baby on 2011-01-11
I just installed Ubuntu netbook remix 10.04 

I try to install proprietary wireless drivers (Broadcom STA)]
It fails to install.

What do I do?

> **Bucky Ball said:**
> Torrent is the most reliable way:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

The regular ISO can be downloaded from the link below. You'll find it down the page a way under 10.04 LTS as:

[ubuntu-10.04.1-netbook-i386.iso.torrent]("http://releases.ubuntu.com/lucid/ubuntu-10.04.1-netbook-i386.iso.torrent")

(Don't click this link here as it won't work)

---

### Post by Bucky Ball on 2011-01-11
Plug in an ethernet cable and try again (if you haven't already).

Make sure you do update from System >Administration >Update Manager.

The b43 works better for some. It is generally one or the other. To install that, try:

System >Administration >Synaptics. Look for and install:

firmware-b43-installer
b43-fwcutter

---

### Post by test_tube_baby on 2011-01-11
The thing is, I dunno why but I get no response from the ethernet cable, I dunno why that won't work on ubuntu it works fine on my other win7 computers.

So I have to do this without the internet, or via usb from another computer (windows 7 based)..

Any help?

> **Bucky Ball said:**
> Plug in an ethernet cable and try again (if you haven't already).

Make sure you do update from System >Administration >Update Manager.

The b43 works better for some. It is generally one or the other. To install that, try:

System >Administration >Synaptics. Look for and install:

firmware-b43-installer
b43-fwcutter

---

### Post by Bucky Ball on 2011-01-11
Cool:

Try this first. Reboot with the cable in. If you are running and plug it in in your situation it probably won't pick up. You possibly need to restart networking. No success there, then:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access")

Tells you how to get either without internet there. STA you can get from the install CD, b43 you need a machine with access to the internet (not the machine you're working on obviously) to download drivers and firmware, put on a dongle and transfer to the problem machine. If STA doesn't work go for b43. Once you're online you can take your choice. b43 has always worked best for me (when I was using a HP). ;)

Sounds like you have the equipment to do this. Good luck and let us know. ;)

---

### Post by test_tube_baby on 2011-01-11
Thanks BuckyBall, worked like a charm!

p.s. I like the name BuckyBall, read about those in Stephen Hawking's Grand Design.

Regards.
Test Tube Baby

> **Bucky Ball said:**
> Cool:

Try this first. Reboot with the cable in. If you are running and plug it in in your situation it probably won't pick up. You possibly need to restart networking. No success there, then:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA%20-%20No%20Internet%20access")

Tells you how to get either without internet there. STA you can get from the install CD, b43 you need a machine with access to the internet (not the machine you're working on obviously) to download drivers and firmware, put on a dongle and transfer to the problem machine. If STA doesn't work go for b43. Once you're online you can take your choice. b43 has always worked best for me (when I was using a HP). ;)

Sounds like you have the equipment to do this. Good luck and let us know. ;)

---

### Post by Bucky Ball on 2011-01-11
\\:D/Excellent news!!! Glad I could help. :)

Welcome and enjoy the OS, the learning curve, don't hesitate to start a new thread for any other probs/questions, and please mark thread as 'solved' using 'thread tools'. ;)

Good luck with it all.

---

