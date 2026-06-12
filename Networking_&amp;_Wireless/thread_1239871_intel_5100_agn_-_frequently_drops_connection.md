---
title: "intel 5100 agn - frequently drops connection"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by ghosthand on 2009-08-14
I'm running ubuntu 9.04 and have downloaded the latest firmware/micro-code for this card per this thread:
[http://ubuntuforums.org/showpost.php?p=7415234&postcount=3](http://ubuntuforums.org/showpost.php?p=7415234&postcount=3)

This micro-code actually lets me connect via wpa2 now, but this card will pretty consistently drop the connection and stop working under heavy transfer load.  Here is  a typical log from kern.log:

Aug 10 19:45:29 blacksnake kernel: [438310.152133] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
Aug 10 19:45:30 blacksnake kernel: [438310.652917] iwlagn: Error sending REPLY_RXON: time out after 500ms.
Aug 10 19:45:30 blacksnake kernel: [438310.652926] iwlagn: Error setting new RXON (-110)
Aug 10 19:45:30 blacksnake kernel: [438310.652940] wlan0: direct probe to AP 00:14:d1:c6:c8:e0 try 1
Aug 10 19:45:30 blacksnake kernel: [438310.853075] wlan0: direct probe to AP 00:14:d1:c6:c8:e0 try 2
Aug 10 19:45:30 blacksnake kernel: [438311.052421] wlan0: direct probe to AP 00:14:d1:c6:c8:e0 try 3
Aug 10 19:45:30 blacksnake kernel: [438311.253307] wlan0: direct probe to AP 00:14:d1:c6:c8:e0 timed out
Aug 10 19:45:40 blacksnake kernel: [438320.652961] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
Aug 10 19:45:40 blacksnake kernel: [438321.152091] iwlagn: Error sending REPLY_RXON: time out after 500ms.
Aug 10 19:45:40 blacksnake kernel: [438321.152101] iwlagn: Error setting new RXON (-110)
Aug 10 19:45:45 blacksnake kernel: [438325.976166] iwlagn: Error sending REPLY_RXON: time out after 500ms.
Aug 10 19:45:45 blacksnake kernel: [438325.976175] iwlagn: Error setting new RXON (-110)
Aug 10 19:45:46 blacksnake kernel: [438326.477065] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
Aug 10 19:45:46 blacksnake kernel: [438326.977051] iwlagn: Error sending REPLY_RXON: time out after 500ms.
Aug 10 19:45:46 blacksnake kernel: [438326.977061] iwlagn: Error setting new RXON (-110)
Aug 10 19:45:47 blacksnake kernel: [438327.477264] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
Aug 10 19:45:47 blacksnake kernel: [438327.977190] iwlagn: Error sending REPLY_RXON: time out after 500ms.
Aug 10 19:45:47 blacksnake kernel: [438327.977200] iwlagn: Error setting new RXON (-110)
Aug 10 19:45:51 blacksnake kernel: [438331.977052] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
Aug 10 19:45:52 blacksnake kernel: [438332.477044] iwlagn: Error sending REPLY_RXON: time out after 500ms.
Aug 10 19:45:52 blacksnake kernel: [438332.477049] iwlagn: Error setting new RXON (-110)
Aug 10 19:45:57 blacksnake kernel: [438337.477136] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
Aug 10 19:45:57 blacksnake kernel: [438337.977294] iwlagn: Error sending REPLY_RXON: time out after 500ms.
Aug 10 19:45:57 blacksnake kernel: [438337.977303] iwlagn: Error setting new RXON (-110)
Aug 10 19:46:02 blacksnake kernel: [438342.977067] iwlagn: Error sending REPLY_SCAN_CMD: time out after 500ms.
Aug 10 19:46:03 blacksnake kernel: [438343.477054] iwlagn: Error sending REPLY_RXON: time out after 500ms.
Aug 10 19:46:03 blacksnake kernel: [438343.477063] iwlagn: Error setting new RXON (-110)
Aug 10 19:46:03 blacksnake kernel: [438343.477077] iwlagn: No space for Tx
Aug 10 19:46:03 blacksnake kernel: [438343.477082] iwlagn: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
Aug 10 19:46:07 blacksnake kernel: [438347.977659] iwlagn: No space for Tx
Aug 10 19:46:07 blacksnake kernel: [438347.977671] iwlagn: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
Aug 10 19:46:07 blacksnake kernel: [438347.977694] iwlagn: No space for Tx

Pretty much just keeps repeating those last couple of lines over and over.  Anyone else seen this problem?  I can get the card working again by disabling wifi in the networkmanager and then re-enabling it, but it is a pain.  I've briefly looked at the compat-wireless project over at the intel wireless drivers page [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
but I didn't see a version that looked compatible with the default jaunty kernel of 2.6.28.  Any help, tips or pointers would be appreciated.

---

### Post by ghosthand on 2009-08-15
Well I went ahead and tried the compat-wireless process with the 'bleeding edge' version found here.

[http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge](http://linuxwireless.org/en/users/Download#Where_to_download_bleeding_edge)

The installation was pretty simple, rebooted and the drivers started working after a little messing around.  I have not had any disconnects since installing the new drivers last night, so maybe this has been fixed.

---

### Post by Leslie Viljoen on 2009-11-25
Bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352228](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352228) in case anyone wants to follow along.

---

### Post by bellen blazen on 2009-12-13
I still have this problem and have filed another bug report.  I found a quick but unfortunate workaround in a Fedora mailing list which is to place the following option:
options iwlagn 11n_disable=1 11n_disable50=1
in /etc/modprobe.d/options.conf, thereby disabling 802.11n :(, but it seems to work.
The bug posted above, for 5300 agn, is confirmed yet still unresolved.
I'm very surprised that such a common network adapter is so buggy in Ubuntu or Linux for that matter.

---

### Post by lightning9 on 2009-12-19
Hello,
if anybody's interested, I had the same issue and got this to work on my 8530w (Intel 5300 chipset).
I compiled and installed compat-wireless-2009-12-11.tar.bz2 from [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/) and it now works flawlessly with my 5GHz N AP. However, unfortunately, the darn led starts blinking again so you have to create a file such as /etc/modprobe.d/iwlcore.conf containing "options iwlcore led_mode=1" to stop it. The other fix of creating an /etc/network/if-up.d script doesn't work because the /sys/class/leds/iwl-phy0 device (?) no longer exists.
YMMV 
Good luck,
lightning9

---

