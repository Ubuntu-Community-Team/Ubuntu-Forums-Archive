---
title: "Acer Aspire One network issue"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by tribaldata on 2009-08-27
I'm using an Aspire One with the following network config.

Network card: AR24x 802.11abg Wireless PCI Express Adapter
Driver: ath5k_pci

I got a issue with moving our streaming media from my ubuntu server the Acer machine will hang the transfer, i have to manually kill the transfer, i tried going with gFTP and using a SSH2 sessions as a type of tunnel and i'm having the same issue.

So for the testing purpose i booted up my WinXP machine and tried the transfer using Samba or a SSH with WinSCP and it works perfectly.

So i'm pretty sure that my problem reside in the network drivers used by my Acer One machine.

So far i tried all the drivers available to me, the madwifi, madwifi-trunk, ath5k_pci and ath_pci. All are giving me the same issue.](*,)

Anyone found a stable driver which support moving files around.:confused:

I find it a shame to have to boot up WinXP to access my Ubuntu server...

Thanks for the help

BTW> I still need to test the Acer with lan cable to verify if a direct connection will also create this. Will be doing this tonight.

---

### Post by tribaldata on 2009-08-27
Yeah :D

I fixed my problem, a friend of mine had the same issue with the same computer.

He told me to try the notebook remix version,, i deleted all my partition a tried out the notebook remix version and now all my deownloads are stable :)

---

### Post by tribaldata on 2009-08-28
:(

Ok now i'm sad....

After further testing i believe i was celebrating to quickly...

Samba transfer are working but any streaming will freeze the computer.
By streaming in mean streaming a movie from my network or youtube in Firefox, all this will froze the machine.
 Once it freeze, it's total freeze of the netbook with a blinking CapsLock light. The only way to get out of that is to hit the power button for a 10 seconds period.

Once again i believe network drivers are an issue...

Anyone have an idea a what log files to check or any other bright ideas.

thanks

---

### Post by rafemonkey on 2009-09-23
Hey, I'm having the same issue. Trying to move a large number of files over a wireless connection the aspire one always hangs at some point in the transfer. (Usually after several gigabytes...) I'm pretty sure that this is an issue with the atheros driver, since I've tried mounting the remote filesystem both with samba and NFS and have tried various combinations of nautilus and cp to move the files, always with the same result. For your info, I have 9.04 with backports installed. (with all the updates as of 9-22-09 installed)

Did you ever try the wired connection? I just dug out an old cable and I'm going to give it a shot in a bit.

---

### Post by rafemonkey on 2009-09-23
I just moved about 10 gigs over a wired connection with no problem. That's 3 or 4 times the amount I can move over wireless before it hangs. I think this must be a problem with the wireless driver (or maybe the hardware?)

My Acer has an Atheros AR242x (rev 01).

---

### Post by rafemonkey on 2009-09-23
Well, here's why it doesn't work:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/238903]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/238903")

No fix though. :(

---

### Post by Xyphoid on 2009-09-24
I have the same problem on my Acer One 150.

I tried Karmic Koala (just the live CD. I didn't install) and the wifi signal seemed a little better than Jaunty. I haven't tried to copy large files over wifi yet.

Hope it's fixed in Karmic...

---

### Post by tribaldata on 2009-09-29
Well it seem we all reached the same conclusion, 

If i try to move files with a RJ-45 connected i do not get freeze and everything seem to be running fine, if i try the wireless after a one Gb or so the system will freeze.

So i believe we need to patiently wait for the new Karmic coming out on the 29th of October and hope for the best. 

As a test i believe i tried each and every drivers available for my wireless card and all of them have failed and lock the system. So if anyone have a drivers who work for them please let me know so i could try it :)

My wireless card is the following
Network card: AR24x 802.11abg Wireless PCI Express Adapter

---

