---
title: "Linksys wusb100v2 + keyring?"
date: 2010-10-02
forum: Networking &amp; Wireless
---

### Post by miikku on 2010-10-02
First off, I'm a bit novice with the Ubuntu environment, but I've managed to get my wusb100v2 working with Ubuntu Lucid. Until recently, it's been working fine, but as it's on my parents computer they asked if I could remove the keyring password prompt at startup, which I did through the System > Preferences > Sessions, unchecking all applications related to the gnome-keyring. All was well. Until I rebooted. The keyring prompt didn't appear, which was indeed intended. But I was hoping it would still automatically connect to my router, but nope. So I re-enabled all keyring apps again and rebooted. Now the keyring is running, but it seems that my wlan connection settings was removed, it's not showing in any case.

So, the question would be, is there any way to just revert to the settings I had a couple days ago, as I really don't want to go through all the hassle with installing the usb dongle again, or just to restore the keyring in some way so I get it to connect again?

I'm writing from a laptop atm, so I'll try to copy relevant information:

```
 $ lsusb
Bus 001 Device 001: ID 1737:0078 Linksys
```
ifconfig and iwconfig doesn't show my dongle at all, so I'm guessing that it just isn't initiated the way it was before the keyring fumble. And I facepalmed when I realised I have deleted the old driver folder I used when installing. Anyway, I know I've used the rt3070 driver from Realtek's homepage, and it has worked. When searching for rt3070 it shows rt3070.bin in /lib/firmware and rt3070sta.ko in /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless, so I'm guessing the driver still is installed, but just not initiated in some way.

Please let me know if there is a quick fix to this or if you need more info to help me.

edit:
I forgot to say I also had a RT3070STA.dat file in /etc/Wireless/RT3070STA. A newbie guess would be that I need to use modprobe again, as I can't find in modprobe -l | grep rt3070sta? I can however find rt2870sta and rt2860sta, can this conflict in some way? I have blacklisted rt2870sta in /etc/modprobe.d/blacklist.conf, but not the 2860 one. It seemed to work fine before all this keyring hassle anyway, so I doubt it's an issue.

---

### Post by miikku on 2010-10-02
Bump.

Also, changed Ralink to Realtek. Just got them mixed up, sorry :)

---

### Post by miikku on 2010-10-02
I think I've found the source of the problem.
```
 $ uname -r
2.6.32-25-generic
```
Can I revert to 2.6.32-24 in an easy way? Is this not recommended for some reason? Should I recompile a new kernel as I did when first installing the usb dongle (I hope to avoid this)?

edit:
Ok, so I loaded 2.6.32-24-generic through the grub menu, and everything's working fine. I've stumbled upon quite many threads about losing wireless connections with the new kernel. My guess is that I have to recompile the kernel for every new update to keep my dongle working? And if that's true, I need to get the driver files from Realtek's homepage and keep them for future updates, correct? This way I can just recompile the kernel as I did before whenever there's a new update if I'm not mistaken. Thanks for your time.

---

