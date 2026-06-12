---
title: "Internet connection: 'Work Offline' problem"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by ALRock on 2010-10-31
I have the "Work Offline" problem:  when I boot up, the icon on the toolbar tells me I have "No network connection".  This is not quite true, since I can access the first page of any website - only subsequent pages are inaccessible.  I get a message saying that Firefox is offline.  However, when I uncheck "Work Offline" in the File menu, it makes no difference to this behavior.

The problem is on my Ubuntu Dell desktop, which is connected to the internet with cable broadband via a D-Link router (wired connection). It has worked fine up till now.  I use Ubuntu 10.04 and Firefox 3.6.11.  I am writing this on my Ubuntu Dell laptop which is wired to the same router, so I assume the problem is not the router.

I have tried various strategies suggested in threads on these forums, including editing about:config, changing "allow" to "deny" in some lines of /etc/dbus-1/system.d/NetworkManager.conf and changing from Automatic (DHCP) to Automatic (DHCP) Addresses only, but no luck so far.

The contents of ifconfig are:
eth0
Link encap:Ethernet  HWaddr 001:aa0:91:a7:51
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisons: 0 txqueulen: 1000
RX bytes: 0 (0.0 B) TX bytes: 0 (0.0 B)

lo
Link encap:Local network
inet addr: 127.0.0.1  Mask 255.0.0.0
inet6 addr ::1/128 Scope: host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:118 errors:0 dropped:0 overruns:0 frame:0
TX packets: 118 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisons: 0 txqueulen: 1000
RX bytes: 11573 (11.5 KB) TX bytes: 11573 (11.5 KB)

The relevant contents of /etc/network/interfaces are:
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

If I comment out "auto eth0" as well, it makes no difference.  If I uncomment both lines ("auto eth0" and "iface eth0 inet dhcp") then I lose the internet connection altogether.

I feel I have come to the end of my limited knowledge and ideas and I would be grateful for any help.

---

### Post by coffee412 on 2010-10-31
> **ALRock said:**
> I have the "Work Offline" problem:  when I boot up, the icon on the toolbar tells me I have "No network connection".  This is not quite true, since I can access the first page of any website - only subsequent pages are inaccessible.  I get a message saying that Firefox is offline.  However, when I uncheck "Work Offline" in the File menu, it makes no difference to this behavior.

The problem is on my Ubuntu Dell desktop, which is connected to the internet with cable broadband via a D-Link router (wired connection). It has worked fine up till now.  I use Ubuntu 10.04 and Firefox 3.6.11.  I am writing this on my Ubuntu Dell laptop which is wired to the same router, so I assume the problem is not the router.

I have tried various strategies suggested in threads on these forums, including editing about:config, changing "allow" to "deny" in some lines of /etc/dbus-1/system.d/NetworkManager.conf and changing from Automatic (DHCP) to Automatic (DHCP) Addresses only, but no luck so far.

The contents of ifconfig are:
eth0
Link encap:Ethernet  HWaddr 001:aa0:91:a7:51
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisons: 0 txqueulen: 1000
RX bytes: 0 (0.0 B) TX bytes: 0 (0.0 B)

lo
Link encap:Local network
inet addr: 127.0.0.1  Mask 255.0.0.0
inet6 addr ::1/128 Scope: host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:118 errors:0 dropped:0 overruns:0 frame:0
TX packets: 118 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisons: 0 txqueulen: 1000
RX bytes: 11573 (11.5 KB) TX bytes: 11573 (11.5 KB)

The relevant contents of /etc/network/interfaces are:
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

If I comment out "auto eth0" as well, it makes no difference.  If I uncomment both lines ("auto eth0" and "iface eth0 inet dhcp") then I lose the internet connection altogether.

I feel I have come to the end of my limited knowledge and ideas and I would be grateful for any help.

Basic problem is that you are not getting an ipaddress from your cable modem. Check your eth0 setup. Any files that you changed please restore the originals even though you might think there are not mistakes in them they could be fudged up. Then go in and recheck your network settings using the icon on your panel and actually reboot your system.

If you are still having problems I will help you further.

---

### Post by grahammechanical on 2010-10-31
It seems to me and I am no expert, that eth0 is not connected. In the list from ifconfig you should see RUNNING in between BROADCAST and MULTICAST

This information might not be of any help but it might set you in the right direction.

regards

---

### Post by grahammechanical on 2010-10-31
The reason you can connect to the first pages of websites is because they are stored in the firefox cache for quick loading. I think that this is correct.

Have you tried using network manager to disable and then enable networking? You may need a reboot.

Regards.

---

### Post by ALRock on 2010-11-01
It was indeed a cable connection problem.  I was completely fooled by the fact that I could access the initial pages of the websites I tried - thanks for the explanation about that.  Ah well, I suppose I have learned a bit about internet connectivity and a few more Linux commands through this - and I would not have solved it any time soon without all your replies, for which many thanks.

---

