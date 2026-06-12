---
title: "Problems finding/connecting to wireless network"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by PurpleHaze420 on 2009-05-21
Hey,

I'm having difficulties finding and connecting to my wireless network on a fresh install of Ubunto v9.04.

When I click the network icon in the top right hand of the screen I do not get any wireless networks detected so initially I tried going into "Network Connections" and entering the settings manually thinking that this would solve the problem. I have tried all types of security WPA-PSK which it's set on as default, WPA, and even turning the security on my router off, all without any success.

I quickly looked through a couple of threads here to see if there was anything similar to my question but couldent see alot, it dosen't help that i'm a complete noob with linux/ubuntu currently as always been a windows-boy.

I noticed a terminal command in somebodys post "lshw -C network" which I have run and taken a screen-shot of the results. If anybody could please provide any help I would appreciate it, i'm currently back in Windows 7 so that I can use the internet. :/

[IMG]http://img132.imageshack.us/img132/2249/screenshotk.png[/IMG]

---

### Post by superprash2003 on 2009-05-22
have you looked at system->admin->hardware drivers ?? if not , try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by t0mppa on 2009-05-22
The b43-pci-bridge is a problem, you have to get interface associated with a better driver. Give what superprash2003 a try and if you still keep getting the b43-pci-bridge associated as the driver after reboots even after installing something else and blacklisting the ssb module (known issue), then you can fix that with a shell script.

---

