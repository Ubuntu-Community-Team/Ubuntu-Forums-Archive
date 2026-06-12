---
title: "stopped wireless adapter - now its gone!"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by HankB on 2008-12-13
Hi folks,
I stopped the Intel 2200 WiFi adapter built into wife's Thinkpad T42 (<Fn><F5>) to see if I could get a broadcom based Wireless N PC card working.  The N card did not come up with either STA or B42 drivers so I removed it and now cannot get the built in adapter working.

I have booted XP to confirm that the card is turned on, and it is.

<Fn><F5> seems to do nothing.

"ifup wlan0" reports "Ignoring unknown interface wlan0=wlan0"

"ifconfig wlan0 up" reports "ERROR while getting interface flags: No such device."

"/etc/init.d/networking stop;/etc/init.d/networking start"
does nothing.

I tried modprobing ipw2200 as the most likely driver and that produces missing symbol errors leading me to believe that something important got removed when I disabled one of the proprietary drivers. I thought I could work around that by booting the older kernel (2.6.27-7) but that panics "unable to mount root."

I've done the Windows thing and rebooted several times with no luck. I can't find anything in the menus that helps and I'm out of command line tricks.

Any suggestions short of a reinstall on how to restore operation of the built in adapter?

thanks,
hank

Well, never mind. This was a wubi install and the result of one of the later operations left the drive/file so scrambled that after fsck, the only thing remaining in the root directory was lost+found. The host XP install also experienced some file corruption but remained bootable after several passes at chkdsk. I'll remove the wubi install and do a proper (disk partition) install and won;t try to install the Broadcom based wireless card again!

---

