---
title: "Wireless Issue Lucid Dell Vostro 1500 BCM4328"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by cooch on 2010-07-29
This has been a nagging issue for me since upgrading to Lucid soon after it's release.  I have never been able to get my wireless working consistently.  I have spent countless hours searching forums trying every variation of commands, but can't seem to fix it.

I am running a vostro 1500 with a Broadcom Corporation BCM4328 802.11a/b/g/n.  I have tried Network Manager, WICD, proprietary driver Broadcom STA wireless, and ndiswrapper with bcmwl5.inf.  I can get it running at home with WPA and a series of command prompts, but it doesn't work if I switch to a different location or network configuration.

Help please!

---

### Post by cooch on 2010-08-09
Bump

---

### Post by JRBASTIEN on 2010-08-22
We are in the same boat.  I have the same laptop as you.  Please define what inconsistencies you have and what you tried so far.

Personally, I used to loose the ability to reconnect after a suspend and sometimes even after just a dimmed screen.  I just resolved the suspend issue by forcing the wl0 driver to suspend but I still loose the connection intermittently.

I think my troubles began when I upgraded my wireless router to a N capable device.  I had no such issues when I was only using a G.

Possible solutions:

- Upgrade wifi router's firmware
- Use the Windows XP driver.  I never succeeded to modprobe it on this laptop
- Install the backport modules (should we just install the ones that says wireless?  (see this link [http://mikebeach.org/2010/03/how-to-karmic-koala-and-broadcom-wireless-bcm4312-rev-01/](http://mikebeach.org/2010/03/how-to-karmic-koala-and-broadcom-wireless-bcm4312-rev-01/))
- For the suspend issue use this link and replace your driver name by wl0: [http://ubuntuforums.org/showthread.php?t=1470327](http://ubuntuforums.org/showthread.php?t=1470327)
- Install WICD instead of Network-Manager.  I also tried that and it was working perfectly fine until I started my laptop again a week later and could not get any wifi connection at all.  I removed it and reverted it back to Network-Manager.

Don't try recompiling the STA driver from the Broadcom site. I did it in the past when I was on Karmic but the latest one are now provided with Lucid.

If someone has other ideas, please let us know.

---

### Post by zdenal on 2010-08-25
The problem is in broadcom driver.

Try my HowTo if it helps to you:

[http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx](http://polach.cc/howto-fix-broadcom-wifi-adapter-wpa-network-access-on-ubuntu-10-04-lucid-lynx)

---

### Post by JRBASTIEN on 2010-08-28
Thank you Zdenek for your suggestion.  However, I used to have this same version of this driver on Karmic and also had trouble with it.

It is strange that the latest version does not work at all on your system while it is working inconsistently on mine.  Perhaps, you don't have the exact same wifi adapter as us on the Dell Vostro 1500.  To determine what it is, you can run this command:

lspci | grep -i Network

This should return:

0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

I personally tried to upgrade my router firmware and it is now working flawlessly since 2 days.  I don't know why I did not have the same problem on Windows but apparently the Linux driver was less stable with this version of the firmware.

---

### Post by kitkatbeard on 2010-09-09
Zdenal, this worked for me.  BCM4328 in lucid.  Thanks for the link.

---

