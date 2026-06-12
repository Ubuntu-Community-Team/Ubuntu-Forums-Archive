---
title: "Wireless Stopped working on a new Install After working for 5 hours - weird"
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by markackerman8@gmail.com on 2013-03-28
As I said above it just stopped working for no good reason that I can tell.  Here are some notes that may help some awesome person including the Master Chil555 to help troubleshoot.

In a nutshell -the install went fine for a friend - 12.04 Kubuntu with absolutely no serious hiccups.  I decided to take it outside to polish things off as the wireless was working fine.  It stopped working an hour later - I thought it was just a temporary glitch and decided to install WICD as it is much more user friendly for the new newbie neighbour.  Didn't help.  Some how the wireless has become disabled

Here are my notes so far:
Toshiba satellite amd Athlon X2 - 6-8 years old
*-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:16:44:1e:17:33
       capabilities: ethernet physical wireless
       configuration: broadcast=yes
       driver=rtl8187 driverversion=3.2.0-39-generic f**irmware=N/A **link=no multicast=yes wireless=IEEE 802.11bg

&#8226;  modprobe rtl8187
&#8226; iwconfig
&#8226; sudo iwlist wlan0 scanning
&#8226; sudo ifconfig wlan0 up
&#8227; wlan0: ERROR while getting interface flags: No such device
&#8226; sudo rfkill list all
&#8728; shows NOTHING
&#8226; sudo rfkill unblock all
&#8728; not applicable
&#8226; cat /var/lib/NetworkManager/NetworkManager.state
            [main]
            NetworkingEnabled=true
            WirelessEnabled=true
            WWANEnabled=true
            WimaxEnabled=true
&#8728; but still not working ?????????

-----

dmesg | grep -e rtl -e wlan
[   10.477959] ieee80211 phy0: hwaddr 00:16:44:1e:17:33, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   10.499669] rtl8187: Customer ID is 0x04
[   10.499972] Registered led device: rtl8187-phy0::radio
[   10.500784] Registered led device: rtl8187-phy0::tx
[   10.502479] Registered led device: rtl8187-phy0::rx
[   10.503296] rtl8187: wireless switch is on
[   10.503560] usbcore: registered new interface driver rtl8187
[   22.434712] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.436054] ADDRCONF(NETDEV_UP): wlan0: link is not ready

----------------------
[main]
			NetworkingEnabled=true
			WirelessEnabled=true
			WWANEnabled=true
			WimaxEnabled=true
still not working

-------------------- 
wicd had nothing in prefernces for "Wireless Interface" so I put in wlan0
  - no help
------------------------

there is a switch on the front bottom which is turned on and has a "Yellow" light - I don't know if was ever green but it is in the on position.
As well, WICD has an active option to turn Wireless Off - which suggests it's on, and if I do turn it off it then has the option to turn it ON - but doesn;t help
I will post more as I do more troubleshooting
Thanks again to Chil555

Mark

---

### Post by markackerman8@gmail.com on 2013-03-29
Bump ?? !!

Anyone out there in cyberland with any suggestions - I will try a re-install to see if that fixes it - since I don't have any oher leads.  I will post results.

Thanks in advance to any one that helps this Good Friday Birthday Boy and a perspective new Linix User that this is for.

Cheers, Mark

---

### Post by markackerman8@gmail.com on 2013-03-29
without any further suggestions I thought I would try a re-install

and it worked !

I sure wish I knew what caused the problem, but Oh well at least I can give her back her 8 year old computer working better than the day she bought it HAHA

She will be so Happy with this Kubuntu and my tweaks.

Cool- and Thanks again Chili555 (Bill)

Mark

---

