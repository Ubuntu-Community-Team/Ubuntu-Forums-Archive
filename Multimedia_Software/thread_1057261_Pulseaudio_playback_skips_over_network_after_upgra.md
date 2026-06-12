---
title: "Pulseaudio playback skips over network after upgrade"
date: 2009-02-01
forum: Multimedia Software
---

### Post by QB89Dragon on 2009-02-01
Hi all,

I'm hoping for some help with this. I have a desktop running 8.10 64 bit, and an eeePC. I use the eee pc to control playback on the desktop by using DAAP through rhythmbox and then pulseaudio over the network to the speakers on the desktop.

When the eee PC was running ubuntu-eee (based on 8.04), this setup worked flawlessly for me and was a joy to use. But I recently upgraded to the 8.10 based eeebuntu-base (which has a similar kernel to ubuntu-eee). And while the upgrade seems to have made a huge improvement to the speed of the eee pc. It is hopelessly lagging and skipping chunks of sound every few seconds when playing back. It is configured identically to the way it was before and nothing has changed on the desktop PC.

I don't think it's a bandwidth issue as it has worked before. Maybe it's a buffer thing. Is this a bug in the newer version of pulseaudio on ubuntu? Or could it be because the new install uses clocksource=hpet in the kernel which may mess with pulseaudio's interrupt timing?

Some help / insights on this would be greatly appreciated!

---

### Post by QB89Dragon on 2009-02-01
More troubleshooting:
Removing clocksource=hpet doesn't affect the original issue, but the computer runs way slower. The speed of the atheros wifi connection is about 12mb/s. I don't know what it was before I upgraded.
Rhythmbox can play a DAAP shared song on the local speakers without skipping.
Playing a locally saved mp3 file to the network speakers via pluseaudio (tried with 3 different players) all have the same issue.

---

### Post by QB89Dragon on 2009-02-01
Any suggestions? Anybody got anything on this??

I've tried changing my /etc/pulse/daemon.conf settings, but it seemed to have no effect and based on what other people are saying - it's something that is quite a fragile setup that can be broken very easily.

---

### Post by Rola on 2009-11-03
same problem here. PIII old box with hardy, every kind of power management shut down (receiver), and eee 1005ha-p with karmic (sender). It's becoming annoying... I've noticed network usage drops to zero when the skips happen. I think it is related to the sender machines though (both eees), but... what is it? network card power management? eee acpi scripts?

---

### Post by Rola on 2009-11-04
> **Rola said:**
> same problem here. PIII old box with hardy, every kind of power management shut down (receiver), and eee 1005ha-p with karmic (sender). It's becoming annoying... I've noticed network usage drops to zero when the skips happen. I think it is related to the sender machines though (both eees), but... what is it? network card power management? eee acpi scripts?

I made some further investigation: 
- Transmitting from a different computer using intel wireless 802.11G and karmic worked flawlessly.
- Transmitting from the eee using wired network worked perfect
- Using Eee's own atheros 802.11N wifi, again skips and finally pulseaudio network crashes on the long run.

So, my best guess is that the wifi card is either not well supported or just creapy cheapo hardware...

---

### Post by Rola on 2009-11-11
Ok. Tried with a Broadcom card, and it's way worse. I have to say, though, that situation with the atheros is better after upgrading kernel (or at least installing backported wireless modules).

---

### Post by Rola on 2009-11-19
Ok. Now I've swapped the card for an Intel 5100, and I must say things are way better, but not perfect. Small audio stutters of one second (as much) appear every two to three minutes. In this case, shutting wlan card power management (iwconfig wlan0 txpower fixed && iwconfig wlan0 power off) doesn't make a difference, but I discovered it can make the atheros a bit more usable when transmitting.

I suppose it must be something about eee acpi scripts. Which ones you use? I use fewts.

---

### Post by robho on 2010-04-29
I just want to point to a bug report which I think describes and explains this problem. It might help other who find this thread and is looking for a solution.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680)

---

### Post by brickZA on 2011-01-10
Just to add more detail on how to fix using info from the bug linked above. If you are running 10.04 (Lucid), you can install Wagner Volanin's patched Network Manger from his PPA [https://launchpad.net/~volanin/+archive/ppa](https://launchpad.net/~volanin/+archive/ppa). This worked for me (Acer Aspire One A110 running 10.04 netbook remix). I can now stream audio smoothly over wifi to my hifi-connected media PC using pulseadio. 

Apparently the Network Manger in 10.10 has a new feature where if you will in the SSID field of an AP, it will disable scanning while connected to that AP. I have not tried that myself, but do report back if it worked for you.

---

