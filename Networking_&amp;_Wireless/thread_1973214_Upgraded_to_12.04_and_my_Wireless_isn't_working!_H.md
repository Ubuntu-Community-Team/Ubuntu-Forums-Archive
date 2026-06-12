---
title: "Upgraded to 12.04 and my Wireless isn't working! Help please!!"
date: 2012-05-04
forum: Networking &amp; Wireless
---

### Post by delimabs on 2012-05-04
Hello There,

I'm new in the linux/ubuntu world and I was using the ubuntu 11.10. So I upgraded it to the newest one, 12.04 and my wireless is no longer working. I've reading a couple of threads about users who have the same problem, but not of it worked for me.

What can I do?

---

### Post by chili555 on 2012-05-04
May we please have some details? Please open a terminal and run and post:```
lspci -nn | grep 0280
arch
lsusb

```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by delimabs on 2012-05-04
lspci -nn | grep 0280

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e3:4315] (rev 01)

---

### Post by delimabs on 2012-05-04
arch
i686

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root Hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root Hub
Bus 001 Device 002: ID 0c45:6400 Microdia
Bus 007 Device 002: ID 04f3:0234 Elan Microeletronics Corp.

---

### Post by chili555 on 2012-05-04
This person has the same device and you'll need the same fix: [http://ubuntuforums.org/showthread.php?t=1969761&highlight=4315](http://ubuntuforums.org/showthread.php?t=1969761&highlight=4315)

---

### Post by delimabs on 2012-05-04
It didn't work either.

After writing this

sudo apt-get install --reinstall bcmwl-kernel-source

The system downloads a couple of this and I think its normal

Although when I wrote this command

sudo modprobe wl

I got the message "WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release."

Which I thought it'd be ok, but my wireless is always off and the airplane mode is always on, just like before

---

### Post by chili555 on 2012-05-04
> I got the message "WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release."Hmmm. Somebody has been busy. The file should be named /etc/modprobe.d/blacklist.[COLOR="Red"]conf[/COLOR] and not .config. Somebody tried to amend the correct file and made a typing error. Let's see what's in there:```
cat /etc/modprobe.d/blacklist.config
```We'll transfer it to the correct file if we need it. Also post:```
iwconfig
rfkill list all
```Thanks.

---

### Post by delimabs on 2012-05-04
Hey Chilli,

Sorry man! Looks like I had to reboot my pc... Now its working.

Thanks a lot.

I'll try to learn more about linux, commands and things.

xD

---

### Post by chili555 on 2012-05-04
You still ought to fix this:> "WARNING: All config files need .conf: /etc/modprobe.d/blacklist.config, it will be ignored in a future release." I'm glad it's working!

---

### Post by ionFreeman on 2012-05-22
I just had the panicky, "hey, I upgraded and now my wireless isn't working" 12.04 signature experience. I can't wait to see what else this release has for me.

I didn't know I had an airplane mode. I just saw 'System Settings...' on the shutdown menu and decided to poke around. I set Airplane Mode off -- I don't know how it got on, that'd be a weird default -- and nothing happened.

I rebooted, and it worked.

Well, that's one way to make Windows users feel comfortable.

---

