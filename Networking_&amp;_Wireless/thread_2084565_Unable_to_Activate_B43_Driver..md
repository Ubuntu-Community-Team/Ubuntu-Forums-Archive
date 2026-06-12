---
title: "Unable to Activate B43 Driver."
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by Stoowyguy on 2012-11-15
I am positive that my Chipset can use the B43 Driver. I am running Ubuntu 12.04 on Kernel 3.2.0-33. I am currently, unfortunaly running the brcmsmac driver.. When I try to run "modprobe -r brcmsmac bcma" to disable the current wireless driver, it does. But then when i go to replace it with the b43, which i already installed using the fwcutter-installer by typing "modprobe b43" it doesn't do anything. It doesn't work. So, can someone please help me get the b43 driver to work..

---

### Post by chili555 on 2012-11-15
> I am positive that my Chipset can use the B43 Driver. However, maybe it's not the optimum driver. Let's see what the chipset actually is:```
lspci -nn | grep 0280
```

---

### Post by Stoowyguy on 2012-11-15
02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)

---

### Post by BertN45 on 2012-11-15
The synaptic package manager says for the b43-installer for the b43 driver:

Installer package for firmware for the b43 driver
This package installs the firmware needed for usage of the b43 kernel driver.
Supported chipsets:
 - BCM4306/3
 - BCM4311
 - BCM4318
 - BCM4321
 - BCM4322 (only 14e4:432b)

---

### Post by Stoowyguy on 2012-11-15
So, basically, what your saying is that my device is not supported for the fw-cutter, and that I should probably just use Compat-Wireless instead?

---

### Post by wildmanne39 on 2012-11-15
Hi, kernel 3.1+ supports b43 but I will let my good friend chilli555 help you since he was here first.

---

### Post by Stoowyguy on 2012-11-15
I am accepting help from anyone who has it.. Now my dilemma is that I have the b43 driver working via Compat-Wireless but when I type airmon-ng (a command from aircrack-ng) it says that it is next to the driver that it is [phy 0] can someone explain to me what that it is because if i can get rid of it I think that I should.

---

### Post by chili555 on 2012-11-15
I know nothing about aircrack. If that's your objective here, I think there are other better places to ask about it.

The best driver for your device to connect to the internet and do boring things like download mp3s and email Mom is the Broadcom STA driver:```
sudo apt-get install bcmwl-kernel-source
```Reboot.

---

### Post by Stoowyguy on 2012-11-15
Do you think that there is a way to disable wlan0 from the network manager but not from like functioning? if that makes sence... For example use the adapter in terminal but not have it be functioning in the background on network manager?

---

### Post by chili555 on 2012-11-15
> **Stoowyguy said:**
> Do you think that there is a way to disable wlan0 from the network manager but not from like functioning? if that makes sence... For example use the adapter in terminal but not have it be functioning in the background on network manager?I'm not sure it does make sense. You don't want NM to control it but you want to control it from the command line? Isn't it running and connected in either case?

---

### Post by BertN45 on 2012-11-15
Basically your wifi hardware is not supported by the b43 driver. It does not mention your chipset and you tried it and it did not work. If you have a working driver stick to that or try the "additional drivers" using the Dash, which installs drivers written by the manufacturers. Broadcom has such a wifi driver there and you could try to use that one.

---

### Post by Stoowyguy on 2012-11-15
I figured it out, you just have to stop the Network-Manager service... The reason I am doing these type of things is just for a specific program... When I have Network-Manager running in the background I run into all different kinds of problems...

---

