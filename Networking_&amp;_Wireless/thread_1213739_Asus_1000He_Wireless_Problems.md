---
title: "Asus 1000He Wireless Problems"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by fiendishfish on 2009-07-15
Hi,

I have installed eeebuntu on my Asus 1000HE netbook, but guessed that this would be the best place to post, as it's almost the same. Basically, I am having trouble connecting to wireless; My wireless card IS being detected, and it's a Atheros AR928X.

Now, let me explain:

Firstly, I have tried several programs to connect to wireless, such as: wifi-radar, knetworkmanager network-manager-gnome and with the CLI, and I think I can safely say it must be a problem with DHCP. However, other wireless boxes on the network (Windows) connect fine.

At first, I ran 'sudo iwconfig wlan0 essid "lollercaust"' (or without quotes) and iwconfig reiterated the details of the node, with the 'Access Point: Not-Associated' rubbish. So, then I ran 'sudo ifconfig wlan0 up' just to be sure, and then ATTEMTED to configure DHCP.



```

ME~$ sudo dhclient wlan0

wmmaster0: unknown hardware address type 801
wmmaster0: unknown hardware address type 801

Listening on LPF/wlan0/<MAC ADDR WAS HERE>
Sending on LPF/wlan0/<MAC ADDR WAS HERE>
Sending on Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
(Carries on for ~6 more lines)

No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

I am running the '2.6.26-2-686' 'Netbook' kernel, and am using the ath9k module for my Wireless card, and as I said, I cannot understand this issue. Because firstly, it works on family's Windows boxen, and also on the Windows partition on my netbook.

Thanks!

---

