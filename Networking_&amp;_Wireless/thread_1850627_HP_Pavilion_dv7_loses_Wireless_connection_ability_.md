---
title: "HP Pavilion dv7 loses Wireless connection ability after resume from suspend."
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by Kelketek on 2011-09-26
Hello there!

Finally got an account of my own here. I've searched around a bit and have seen a few threads similar to this, but the fixes I was able to find didn't seem to work (though I may have missed one).

Here is the scenario:

1. Computer starts up, connects to wireless network as normal.
2. Close the lid, let the system suspend.
3. Open the lid, the wireless card attempts to reconnect and fails, asking me for the password.

Here is some information on my wireless configuration from lspci -k:

```

0d:00.0 Network controller: Intel Corperation Centrino Wireless-N 1000
        Subsystem: Intel Corperation Centrino Wireless-N BGN
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

```Here is what shows up at the end of dmesg when after the computer wakes:

```

[   92.876220] PM: Finishing wakeup.
[   92.876221] Restarting tasks ... done.
[   92.893978] video LNXVIDEO:00: Restoring backlight state
[   92.946599] video LNXVIDEO:01: Restoring backlight state
[   93.044200] cfg80211: Calling CRDA to update world regulatory domain
[   93.048080] cfg80211: World regulatory domain updated:
[   93.048083] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   93.048085] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.048088] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   93.048090] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   93.048092] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.048094] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   93.048749] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   93.048752] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   93.048806] iwlagn 0000:0d:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   93.048820] iwlagn 0000:0d:00.0: setting latency timer to 64
[   93.048852] iwlagn 0000:0d:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   93.070181] iwlagn 0000:0d:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   93.070183] iwlagn 0000:0d:00.0: Device SKU: 0X9
[   93.070184] iwlagn 0000:0d:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   93.070201] iwlagn 0000:0d:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   93.070299] iwlagn 0000:0d:00.0: irq 50 for MSI/MSI-X
[   93.072631] iwlagn 0000:0d:00.0: loaded firmware version 39.31.5.1 build 35138
[   93.072789] Registered led device: phy0-led
[   93.072814] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   93.072919] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   93.725853] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
[   93.788191] r8169 0000:07:00.0: eth0: link down
[   93.789669] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   93.916604] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   96.299775] wlan0: direct probe to 30:46:9a:1c:8f:c5 (try 1/3)
[   96.498047] wlan0: direct probe to 30:46:9a:1c:8f:c5 (try 2/3)
[   96.697954] wlan0: direct probe to 30:46:9a:1c:8f:c5 (try 3/3)
[   96.897841] wlan0: direct probe to 30:46:9a:1c:8f:c5 timed out
[   98.916820] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[  110.280411] wlan0: direct probe to 30:46:9a:1c:8f:c5 (try 1/3)
[  110.478902] wlan0: direct probe to 30:46:9a:1c:8f:c5 (try 2/3)
[  110.678792] wlan0: direct probe to 30:46:9a:1c:8f:c5 (try 3/3)
[  110.878703] wlan0: direct probe to 30:46:9a:1c:8f:c5 timed out
[  112.889660] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues

```Here is what I have tried:

1. 
```
service network-manager stop && rmmod iwlagn && modprobe iwlagn && service network start
```

2. Added this line to /etc/pm/config.d/coonfig
```
SUSPEND_MODULES="iwlagn"
```I'm quite boggled here, so I welcome any suggestions you may have. Also, does anyone know what those messages in dmesg actually mean? What is the tx fifo queue? I love to learn, so finding out about what all this means would be nice as well :)

---

### Post by nah40 on 2011-09-29
I have the same problem. HP DV6TSE purchased in May.
Installed 11.10 Beta as soon as it came out.
I have searched every forum and tried every suggestion with no success.
I just give up wasting time with this and hope that this is fixed in the official Oneiric release.
The battery life is 50% of what it is in Win7, another big glitch.
After using Ubuntu exclusively for five years, this has forced me back to Windows. And I have to say the Win7 is a pretty good OS.

---

### Post by rsvancara on 2011-10-22
I am having the same problem as well.  I have tried unloading the driver and reloading the driver without any luck.  At this point I am not sure how to resolve the issue other than start digging into the kernel and the driver.

---

### Post by rsvancara on 2011-10-22
Found these articles on google:

This article claims to solve the problem, however I am running 3.0.0.12 kernel

[https://bbs.archlinux.org/viewtopic.php?id=110392](https://bbs.archlinux.org/viewtopic.php?id=110392)

This article is from the kernel wireless mailing list:
[http://comments.gmane.org/gmane.linux.kernel.wireless.general/71729](http://comments.gmane.org/gmane.linux.kernel.wireless.general/71729)

Redhat Bugzilla, but does not appear to be related.  RedHat usually runs an very antiquated kernel.
[https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=724052](https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=724052)

I can revert back to kernel 2.6.38 and everything works like normal. Obviously this is a regression that has been introduced into kernel.

I am running Ubuntu on an HP Pavillion dv7 with Intel Corporation Centrino Wirless-N 1000 running kernel version 3.0.0.12 on Ubuntu 11.10

--Randall
[http://www.knowyourlinux.com]("http://www.knowyourlinux.com")

---

### Post by minimec on 2011-10-28
I own a Lenovo x121e with that same Intel Wireless N 1000 card.

My workaround is to disable the 'n' network using a driver option. It is rather easy to do that on Debian/Ubuntu.

- open a console 
sudo nano /etc/modprobe.d/iwlagn.conf    <-- create and open config file   

- add the option 
options iwlagn 11n_disable=1  <-- add that line to iwlagn.conf

- save with <ctrl>x and 'sudo reboot'

- done. ;)

That workaround solved all connection problems I had with that wifi card in Ubuntu 11.10 'oneiric', using kernel 3.0.0-12-generic. 

Also data transfer rate is more stable and therefore much faster in the end.

---

### Post by biodiesel-bri on 2012-01-10
Your workaround did not work for me on my HP dv7-6b78us, but I dug around and found something that did:

/etc/modprobe.d/iwlagn.conf:
> options iwlagn bt_coex_active=0

I encourage people to comment on the bug report and hopefully this will get properly fixed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614954](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614954)

---

### Post by Kelketek on 2012-01-10
> **biodiesel-bri said:**
> Your workaround did not work for me on my HP dv7-6b78us, but I dug around and found something that did:

/etc/modprobe.d/iwlagn.conf:


I encourage people to comment on the bug report and hopefully this will get properly fixed:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614954](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614954)

This worked! Can you tell me what the consequences of this setting are and how you came to this solution? I don't use Bluetooth that often, so this likely won't bother me much, but I would like to get it fixed, yes.

---

### Post by biodiesel-bri on 2012-01-10
I don't know what the consequences might be to bluetooth.  I just know that it works.  :)

I found it by googling "iwlagn resume" and figured that Launchpad would be a good place to click.  Launchpad often has answers that aren't present on the forums, and by submitting and commenting on bugs you end up having a better chance of someone fixing an issue that doesn't have an easy solution.

---

### Post by biodiesel-bri on 2012-01-10
Also, please mark the thread solved.  It helps people find solutions.  :)

---

### Post by Dans564 on 2012-03-09
Bump...
this doesn't work with the 3.2 kernel :(

---

### Post by biodiesel-bri on 2012-03-10
You should probably post to the bug report I referenced above.  I'm not running the 3.2 kernel.

---

### Post by Kelketek on 2012-06-03
Actually, it does. They've just renamed the kernel module create /etc/modprobe.d/iwlwifi.conf and put in:

options iwlwifi bt_coex_active=0

---

### Post by Kelketek on 2012-06-03
I made a redundant post here. I'd remove it, but I can't figure out how.

---

