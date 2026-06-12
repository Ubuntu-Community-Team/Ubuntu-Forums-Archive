---
title: "Wireless driver causing failure to boot?"
date: 2013-02-19
forum: Networking &amp; Wireless
---

### Post by Gearaddict on 2013-02-19
Hi All - first post...new to Ubuntu and the forum! Apologies if this is covered elsewhere but I could seem to find it by searching...
 
I installed Ubuntu 10.04 on my old Mac Powerbook G4 last night using the below instructions:
 
[http://www.jeremymorgan.com/tutorials/linux/how-to-install-linux-ppc-powerbook-g4/](http://www.jeremymorgan.com/tutorials/linux/how-to-install-linux-ppc-powerbook-g4/)
 
This went fine and all looked good but I couldn't connect to my wireless network. There was a wireless symbol at the top of the screen but when I clicked on it, it stated 'wireless disconnected' and it was greyed out. No wireless networks seemed to be detected. So, I followed the below instructions to install a driver for my wireless card (my settings / specs were exactly the same as those in the instructions):
 
[http://www.jeremymorgan.com/tutorials/linux/how-to-wireless-networking-linux-ppc-powerbook-g4/](http://www.jeremymorgan.com/tutorials/linux/how-to-wireless-networking-linux-ppc-powerbook-g4/)
 
But...when I went to restart the computer it wouldn't reboot. It went through the text screens then instead of the normal slick 'Ubuntu' graphic i got a garbled plain text version of it and the screen went dark and then the computer just sat there.
 
So, in the absence of many other options, I reinstalled Ubuntu from the CD again...this time I got a little icon come up saying there was an updated driver available...when I clicked on this, it seemed to take me through the same process as described in the link above and again when I restarted it wouldn't reboot.
 
ANYway...I'll probably reinstall it again tonight but when I do, can someone advise how I get the wireless working without trashing the installation? Do you think the wireless driver could have caused the above? Seems unlikely to me, to be honest.
 
Thanks in advance for any help!

---

### Post by ajgreeny on 2013-02-19
I can't help specifically with your mac problem, but have to say that there is little point installing 10.04 at this time in its support life.  It will lose any further support from April this year, so sorting out problems for just two months hardly seems worth the work involved.

I suggest you try 12.04 instead which is supported until April 2017 (5 yrs total, one year already gone). It uses the new unity DE which may or may not suit you, but if not there are other options available, and it is quite possible that 12.04 will have newer and better  wireless drivers for your hardware, thus removing the need for the work.

---

### Post by Gearaddict on 2013-02-19
> **ajgreeny said:**
> I can't help specifically with your mac problem, but have to say that there is little point installing 10.04 at this time in its support life. It will lose any further support from April this year, so sorting out problems for just two months hardly seems worth the work involved.
 
I suggest you try 12.04 instead which is supported until April 2017 (5 yrs total, one year already gone). It uses the new unity DE which may or may not suit you, but if not there are other options available, and it is quite possible that 12.04 will have newer and better wireless drivers for your hardware, thus removing the need for the work.
 
Thanks for that - I was installing Ubuntu in an effort to breathe life into an otherwise pretty much obsolete Powerbook G4...so I just need basic wireless access, browsing and email. I just went with 10.04 as it was recommended as stable in that guide I linked to. Would 12.04 be more resource hungry? Since I don't need much functionality I'd rather go with the lightest OS possible in order to improve performance.

---

### Post by ajgreeny on 2013-02-19
In that case try Xubuntu 12.04.  It is supported for another 2 years as opposed to the 4 years of Ubuntu, and will be a faster desktop environment than the unity DE of Ubuntu as well.

All the applications and packages of Ubuntu are available in Xubuntu as well, even if they are not included in the default install, eg gimp, libreoffice, and it is probably my favoured OS now that unity is the default of Ubuntu.

---

### Post by Gearaddict on 2013-02-20
So it turns out the booting problem wasn't to do with the wireless drivers at all - it was just that 10.04 wasn't stable on my system...I have now installed Lubuntu 12.04 and it seems fine.

My problem now is that I can't get the wireless card to work. I have followed instructions around downloading the firmware and drivers etc but the 'wireless' tab in Network Connections is all greyed out. Any ideas as to how I can activate wireless?

Thanks!

---

### Post by chili555 on 2013-02-20
Please open a terminal and run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by Gearaddict on 2013-02-20
> **chili555 said:**
> Please open a terminal and run and post:```
lspci -nn | grep 0280
```Thanks.

so that's weird - when I booted up the pc, I briefly got an alert pop up saying "wireless networks detected, to connect..." and then it vanished. When I go to the wireless tab in network connections, there is nothing...

Anyway, response to the above code is:

0001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

[edit]so I clicked randomly on a blank section of the taskbar between the volume symbol and the time...and lo and behold, up pops a list of available wifi connections...I am now connected! For some reason the wifi symbol is missing from the taskbar...

---

### Post by chili555 on 2013-02-20
I believe the correct driver for your device is b43 and associated firmware. Let's see what is *actually* loaded:```
lsmod | grep -e wl -e b43
dmesg | grep -i -e wl -e b43
```Thanks.

---

