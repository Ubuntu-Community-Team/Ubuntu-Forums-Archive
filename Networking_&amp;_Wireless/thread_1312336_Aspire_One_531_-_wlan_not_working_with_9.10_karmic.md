---
title: "Aspire One 531 - wlan not working with 9.10 karmic"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by frankomat on 2009-11-03
Hi all,

I digged through a lot of threads here and also on other sites, but was not able to find something which could help me.

I have an Acer Aspire One 531 Netbook with the Atheros 5001 wireless inside.

I want to try out Ubuntu 9.10 with the live session, so I built a live Ubuntu on a SD-Card, booted from that. Works fine except wireless.

1) The Network symbol on the right top tells me "Wireless is disabled"
2) I am not able to switch the wireless on with pushing the wlan switch on the front of the netbook. The LED stays off. That works with Windows.
3) I tried lsmod and dmesg and I think I see the ath5k driver loaded:

```
ubuntu@ubuntu:~$ lsmod |grep ath
ath5k                 124260  0 
mac80211              181236  1 ath5k
ath                     8060  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath
led_class               4096  2 ath5k,acer_wmi
 
``````
ubuntu@ubuntu:~$ dmesg | grep ath
[    4.599454] device-mapper: multipath: version 1.1.0 loaded
[    4.599463] device-mapper: multipath round-robin: version 1.0.0 loaded
[   55.596242] ath5k 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   55.596292] ath5k 0000:02:00.0: setting latency timer to 64
[   55.596377] ath5k 0000:02:00.0: registered as 'phy0'
[   55.739876] ath: EEPROM regdomain: 0x65
[   55.739885] ath: EEPROM indicates we should expect a direct regpair map
[   55.739896] ath: Country alpha2 being used: 00
[   55.739903] ath: Regpair used: 0x65
[   56.448589] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

```The wireless seems to be a Atheros 5001:
```
ubuntu@ubuntu:~$ lspci | grep -i ath
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```Also ```
sudo modprobe -rf ath5k
```and loading again ```

sudo modprobe ath5k
``` does not help. The driver get loaded and that's it.

What can I do?

I would like to get the wireless running, to be able to switch it on and off via the switch on the netbook.

If would like to install Ubuntu on my hard drive, but would like to be sure that wireless works before.

Many thanks,
frankomat

---

### Post by Civean on 2009-11-09
I have a aspire one 531, and I have the same problem. No wireless.

/Civean

---

### Post by Neilbedwin on 2009-11-09
An easy fix......

Go to /etc/modprobe.d and add the line 'blacklist acer_wmi'

Mine worked fine after that. Don't be tempted to install wicd drivers....it stopped my 3G dongle from working!

---

### Post by Civean on 2009-11-09
In the modprobe folder, there were several config files. I added the "blacklist acer.wmi" line to blacklist.conf, and not the other ones. This did not work, after restarting. Still no wireless :(

By the way, windows XP reports the wireless card as "Atheros AR5007EG".

Help would be appreciated!

---

### Post by Neilbedwin on 2009-11-09
Sorry didn't have my 531 with me when I posted but I have just checked and all I did was add 'blacklist acer_wmi' to blacklist.conf in the /etc/modprobe.d directory and rebooted.

There are a lot of posts about the AAO and 9.10. try a google search....sorry can't be any more help.

---

### Post by Civean on 2009-11-10
Thank you!

When using "acer_wmi", the wireless works perfectly!

However, the trackpad stops working for some minutes after connecting to wifi access points. Not such an issue, though. Again, thank you!

(Summary: To enable wireless in 9.10 karmic koala when using the Acer Aspire One 531h, add "blacklist acer_wmi" to /etc/modprobe.d/blacklist.conf and restart)

---

