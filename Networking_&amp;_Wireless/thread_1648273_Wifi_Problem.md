---
title: "Wifi Problem"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by Eddie2103 on 2010-12-18
I installed kubuntu from a usb with unetbootin and installed it on Wednesday. it is a dualboot MS windows Vista business sp2 on one partition and Kubuntu 10.10 on another and I have a Airport Extreme with 802.11n and my wireless card has 802.11n my problem is that wireless works well in windows but when I use kubuntu it picks it up as Wired and It says Disconnected. What can I do?

~~EDIT~~
Windows Vista Is 32bit and kubuntu is 64bit

---

### Post by Eddie2103 on 2010-12-19
Bump anyone have an answer

---

### Post by spiky001 on 2010-12-19
Dose wired work? post ifconfig

---

### Post by Eddie2103 on 2010-12-19
Damn I can't upload it. I do it in kubuntu I put it in OPEN OFFICE then external hdd than I tried to open it in windows but it does not open it shows the file association crap it is driving me as crazy as hell   ](*,)

---

### Post by Eddie2103 on 2010-12-19
Why the hell won't somebody answer me it is driving me crazy

---

### Post by Eddie2103 on 2010-12-20
bump if someone finds a solution to the problem I will install Ubuntu on every damn computer that I own

---

### Post by spiky001 on 2010-12-20
Dose wired work?

---

### Post by Eddie2103 on 2010-12-20
> **spiky001 said:**
> Dose wired work?

No

Sorry I forgot to to tell you that

---

### Post by grahammechanical on 2010-12-20
I am not familiar with kubuntu. I cannot accurately describe the steps you need to take. Do you see on the top panel an icon that looks as if it represents networking. If so, what information do you see if you left click and if you right click?

Also are you using a laptop or a desktop? It makes a difference. With laptops Windows sometimes switches off the wireless adapter in hardware when it shutsdown. Sometimes users forget to activate the wireless adapter on laptops by pressing the FN-function key combination. We need information from your machine. What information does the Operating system give you that will help us help you. Or better still will help you help yourself.

Regards.

---

### Post by Eddie2103 on 2010-12-20
> **grahammechanical said:**
> I am not familiar with kubuntu. I cannot accurately describe the steps you need to take. Do you see on the top panel an icon that looks as if it represents networking. If so, what information do you see if you left click and if you right click?

Also are you using a laptop or a desktop? It makes a difference. With laptops Windows sometimes switches off the wireless adapter in hardware when it shutsdown. Sometimes users forget to activate the wireless adapter on laptops by pressing the FN-function key combination. We need information from your machine. What information does the Operating system give you that will help us help you. Or better still will help you help yourself.

Regards.

When I left or right click nothing happens. when I hover over it it shows wired and disconnected

---

### Post by Eddie2103 on 2010-12-21
Answers anyone I am going crazy

---

### Post by spiky001 on 2010-12-21
Can you boot into live cd see if it works when running off cd

---

### Post by Eddie2103 on 2010-12-21
I used live usb because my computer has no combo drive and it did not work

---

### Post by spiky001 on 2010-12-22
post the output ot ```
lspci
```

---

### Post by thefix0r on 2010-12-22
I wish I had the answer, but from what you said, looks like Kubuntu doesnt have the proper drivers for your wireless card, I would seek knowledge about changing the driver, possible madwifi

---

### Post by Eddie2103 on 2010-12-22
> **spiky001 said:**
> post the output ot ```
lspci
```

How do I post it

@ thefix0r Do I download drivers for madwifi since my wireless card doesn't have drivers for linux

---

### Post by spiky001 on 2010-12-22
open office can save docs in microsoft format check file formats

---

### Post by spiky001 on 2010-12-22
Have a read through here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Eddie2103 on 2010-12-24
> **spiky001 said:**
> open office can save docs in microsoft format check file formats

I got it I think

Noah@noah-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:2e:bc:08:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5616 (5.6 KB)  TX bytes:5616 (5.6 KB)
Noah@noah-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:2e:bc:08:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5616 (5.6 KB)  TX bytes:5616 (5.6 KB)



I am reading the link and will try it in a few seconds

---

### Post by Eddie2103 on 2010-12-29
The one above me is ifconfig
I cannot post ispci because it says it is not a proper command

---

### Post by PatchesTheCaveman on 2010-12-29
The correct command is:
```
lspci -v
```

With an L not an I.  Adding the *-v* will give us a little more information about any drivers you already have installed.

---

### Post by Eddie2103 on 2011-01-22
I Solved It Yesterday :P

---

### Post by Zilvermeeuw on 2011-01-23
How?

---

### Post by Eddie2103 on 2011-01-23
My Friend said to uninstall the network manager and reboot and it worked

---

