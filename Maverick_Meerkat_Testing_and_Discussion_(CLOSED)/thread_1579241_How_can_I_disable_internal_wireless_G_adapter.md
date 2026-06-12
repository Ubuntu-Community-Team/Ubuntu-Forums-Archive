---
title: "How can I disable internal wireless G adapter?"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2010-09-21
Hi,

I have a Toshiba laptop with internal miniPCI wireless G adapter Atheros AR-5001 (driver module ath5k).  I suspect that it affects the bit rate of my external Linksys WPC300N-V1 wireless N PCMCIA card (Broadcom STA driver module wl). Currently I use Maverick Meerkat, 2.6.35-22 generic kernel.

In Windows 7, I disabled the driver of Atheros 5001 and the link speed of the Linksys card is 50-130 Mbps.  However, in Ubuntu the bit rate or link speed of the Linksys card is only 2 Mbps. When I first blacklisted the ath5k driver and immediately pulled the cable (eth0 disabled), the link speed of Linksys card immediately went to 53 Mbps but after rebooting, it fell back to 2 Mbps.  I even commented out the lines for the Atheros adapter in /etc/udev/rules.d/70-persistent-net.rules then rebooted but the speed of the Linksys card is still 2 Mbps!

I even changed the DNS settings in my DD-WRT'ed Netgear WNR834B v2 wireless N router but the above speed is still only 2 Mbps.  I believe DNS resolution is not a problem because it only takes 5-6 seconds for the Linksys wireless icon to show up on the menu bar. Wired connection (eth0) speed remains at 100 Mbps.

I would appreciate your help, and look forward to hearing from you soon.

:confused:

---

### Post by Iowan on 2010-09-21
Moved to Maverick Meerkat Testing and Discussion

---

### Post by iClouseau88 on 2010-09-21
Thank you Iowan for moving this thread to its new location, and thank you cariboo907 for suggesting that I may want to try static DNS. Problem solved after I switched from DHCP to static IP, etc. as summarized below:

1. Comment out the line(s) with Atheros AR-5001 legacy wireless G device in /etc/udev/rules.d/70-persistent-net.rules:

```
# PCI device 0x168c:0x001c (ath5k)
[COLOR="Blue"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}
[COLOR="Blue"]#[/COLOR]=="00:16:e3:5f:55:1f", ATTR{dev_id}=="0x0", ATTR{type}=="1", 
[COLOR="Blue"][/COLOR][COLOR="Blue"]#[/COLOR]KERNEL=="wlan*", NAME="wlan0"
```

2. Blacklist ath5k which comes from #lspci -v and #lsmod:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```

blacklist.conf shows:
```
#this blacklists the ath5k driver of internal Atheros AR-5001 miniPCI adapter to avoid interference with bandwidth or speed of external wireless N cards.  Do NOT blacklist [COLOR="Blue"]yenta_cardbus[/COLOR] otherwise your PCMCIA wireless adapter will not work!

blacklist [COLOR="Blue"]ath5k[/COLOR]
```

Save and close blacklist.conf

3. Right click Network Manager icon and select Edit Connection

4. Select Wireless tab > Wireless Connection 1 > Edit 

5. Enter password to authenticate

6. IP v4 settings tab > Method=Manual
 
7. Addresses: Add > Enter IP address, netmask, default gateway (these 3 from router config page) > Enter IP addresses of DNS servers and search domain (these last items from ISP)

8. Apply and reboot.  The link speed of my wireless connection immediately jumped from 2 Mbps to 14 Mbps, which is not too bad!

PS: After pulling the cable, I got 40 Mbps.  After another reboot, it's 53 Mbps!

:P

---

### Post by Reiger on 2010-09-21
Add the ath5k driver to /etc/modprobe.d/blacklist ?
Use: ifconfig <device> down ?
Use: modprobe -r ath5k ?

---

### Post by iClouseau88 on 2010-09-22
Hi everyone,

I was happy with the initial results so didn't want to do anything else.  Then I thought about trying to get speed increase beyond 40-50 Mbps...

Since I was thinking perhaps the legacy hardware was using obsolete drivers, may be I should install [COLOR="Blue"]linux-backports-modules-wireless-maverick-generic[/COLOR].  Two packages were installed by the system:

1. [COLOR="Blue"]linux-backports-modules-wireless-2.6.35-22-generic (2.6.35-22.12)[/COLOR]

2. [COLOR="Blue"]linux-backports-modules-wireless-maverick-generic (2.6.35.22.23)[/COLOR]

What a disaster!  After reboot, the speed fell back to 2 Mbps!

So I uninstalled the above packages but still got 2 Mbps after rebooting.  Then rebooted into Recovery kernel, still got 2 Mbps.  Then rebooted into recovery kernel again but chose "Repair broken packages".  Now after reboot I got 40-50 Mbps once again!

What else should I do to increase link speed besides physically removing the built-in adapter?

Thanks in advance.

---

