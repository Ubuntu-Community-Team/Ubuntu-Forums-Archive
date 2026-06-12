---
title: "B43 legacy card error"
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by CHPbuntu on 2012-07-27
I have an XP era HP laptop (specs: 1G RAM, 20Gig. HD, CD reader/writer/DVD drive, Broadcom Wireless card, ATI graphics) with Ubuntu Oneric that I recently changed the DE on from XFCE and Unity to LXDE and Unity. This morning, I turned it on and received this error after the normal text (checking battery state and such) appeared on the screen: 

"initctl error event failed"
I then booted the memory test, then the recovery mode. From recovery mode,I tried the resume normal boot option, and got the same error as before. I rebooted, and booted normally which gave me the same initctl error. I went to a login shell and tried to start the lightdm service after logging in, but still no success. After another reboot, I booted normally, and thisis what I see:

*Starting NTP server ntpd                                                                         [OK]
*Starting bluetooth                                                                               [OK]
*PulseAudio configured for per-user sesions 
                                         saned disabled; edit /etc/default/saned
                                                                                *Checking battery state...
[     30.888341] b43legacy-phy0 ERROR: MAC suspend failed                                         [OK]

and at the end of all this is a blinking cursor as if it is waiting for me to do something.
I am not sure what to do, any help will be much appreciated.

---

### Post by chili555 on 2012-07-27
> "initctl error event failed"And then:> [ 30.888341] b43legacy-phy0 ERROR: MAC suspend failed [OK]I'm not at all sure one has anything to do with the other. Generally, wireless issues continue past the boot process, the device is inoperative and the *dmesg* log contains the error description. 

You might blacklist b43legacy temporarily and reboot. See what the final message is before failure and Google from there. ```
sudo su
echo "blacklist b43legacy" >> /etc/modprobe.d/blacklist.conf
exit
```If it still hangs on boot, you know it isn't a b43legacy problem.

If it still hangs and there is some other error, I suggest you ask in General Help.

---

