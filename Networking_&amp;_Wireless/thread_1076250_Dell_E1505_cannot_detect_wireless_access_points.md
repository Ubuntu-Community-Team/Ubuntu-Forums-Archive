---
title: "Dell E1505 cannot detect wireless access points"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by dwhitney67 on 2009-02-21
In the wee hours of this morning, I noticed that my Ubuntu 8.04 system no longer was connected to my wireless access point.  When I clicked on the Gnome Network Manager applet, not a single access point was listed... normally there are at least 10 available.

My other notebook, which is a different brand and runs Fedora 9, is happily connected to my access point, so I know the issue is not my wireless router.

For grins, I updated my 8.04 system to 8.10 to see if that would make a difference, but still no joy.

Can someone help me with this issue??

Below are the command-line responses from the typical commands that one issues in these cases...

For 'lspci':
```

...
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

For 'iwconfig':
```

lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

eth0      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
[Yes, eth0 has always been my wireless handle; not wlan0 like on most other systems.]

For 'iwlist scanning':
```

lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth0      No scan results

```
The LED indicator for my wifi chipset is lit on my system, thus giving me the impression the correct driver(s) is installed.  The driver name 'bcm43xx' is in the /etc/modprobe.d/blacklist file;  I'm not sure if this is correct or not.  Regardless I do not have this driver on my system.

Included below is a snapshot of the drivers as reported by the system.

---

### Post by JamieKitson on 2009-02-21
Have you tried the STA driver?

---

### Post by dwhitney67 on 2009-02-21
Yes, I tried just now.  Still no joy.

---

### Post by dwhitney67 on 2009-02-21
Well, I go the wifi working again.  I came across a message in /var/log/messages indicating that my firmware would not be supported beyond July 2008.  Yet this firmware worked through last night.

Anyhow, the message provided a [website]("http://linuxwireless.org/en/users/Drivers/b43#devicefirmware") where I went to obtain the latest version of the firmware.

After following the instructions, and rebooting my system, then sprinkling pixie dust (see notes below) on the notebook, the wireless interface started working again.


Concerning the pixie dust... I turned OFF the "enable wireless" setting using the NetworkManager applet, waited a few moments, and switched it back ON.  Then I had to enable the wireless chipset using the Fn-F2 keys on my keyboard.

As for the wireless connection, it is slow as heck, probably comparable to a 14.4 dial-up modem.  Hopefully the "geniuses" at Ubuntu, with their packaging skills, will be able to sort this issue out soon with another update.

P.S.  I was able to rename my interfaces to their common names, eth0 and wlan0.  I edited /etc/udev/rules.d/70-persisten-net.rules.

---

### Post by dwhitney67 on 2009-02-21
Well, I may have "celebrated" too soon.  I logged into my daughter's account, and no wireless is available.  Even the NetworkManager applet is not available.

When I created a Network Monitor applet, it did not even show the wlan0 interface.

So here I am again, posting about my woes with wireless and Ubuntu.

Does anyone know how to install the NetworkManager applet onto the panel?  And probably more importantly, why regular, non-privileged users, cannot see the wlan0 interface.

---

