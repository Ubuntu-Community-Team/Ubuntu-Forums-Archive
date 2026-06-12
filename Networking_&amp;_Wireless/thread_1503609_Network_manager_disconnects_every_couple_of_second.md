---
title: "Network manager disconnects every couple of seconds"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by paul.turner on 2010-06-07
I'm completely new to ubuntu here and I have no clue how to get this problem fixed:

Basically upon logging network manager will connect to my network, and most of the time it will only last 20 seconds or so before it disconnects and tries to reconnects, this tends to go on for quite a while.  Logging off and logging on over and over worked once, for this post I opened pages between the 15 seconds that i was connected and after 20 minutes it has remained connected (every time it stays connected for longer than 5 minutes it will never disconnect again)

I followed the HOWTO thread so forgive me if most of this information is useless

[B]
1 ) Machine Brand and Model (Laptop)[/B]: Asus 52jr is the model number
[B]2 ) Wireless Brand, Model and Wireless Chipset:
[/B]03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)is what I found from running lspci
**3 ) check interface:**
```
wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:5c:61:8b  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:fe5c:618b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3251677 (3.2 MB)  TX bytes:851041 (851.0 KB)

```
[B]4 ) check for modules:
[/B]nothing that mentioned wlan dunno what I'm looking for
[B]5 ) Kernel boot messages

[/B]There was at least 5 times this top bit that I copied here after running dmesg
[  196.879423] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  197.185885] wlan0: deauthenticating from 00:23:69:85:70:f4 by local choice (reason=3)
[  197.323188] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  197.409827] jme 0000:05:00.5: irq 35 for MSI/MSI-X
[  197.410242] eth0: Link is down.
[  197.410621] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  197.662441] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  199.759384] wlan0: direct probe to AP 00:23:69:85:70:f4 (try 1)
[  199.763922] wlan0: direct probe responded
[  199.763929] wlan0: authenticate with AP 00:23:69:85:70:f4 (try 1)
[  199.766065] wlan0: authenticated
[  199.766091] wlan0: associate with AP 00:23:69:85:70:f4 (try 1)
[  199.771174] wlan0: RX AssocResp from 00:23:69:85:70:f4 (capab=0x411 status=0 aid=2)
[  199.771179] wlan0: associated
[  199.780704] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  209.788575] wlan0: no IPv6 routers present
[  209.808603] wlan0: deauthenticating from 00:23:69:85:70:f4 by local choice (reason=3)
[  210.000336] ath9k: Two wiphys trying to scan at the same time
[  210.201255] wlan0: deauthenticating from 00:23:69:85:70:f4 by local choice (reason=3)
[  210.401012] wlan0: direct probe to AP 00:23:69:85:70:f4 (try 1)
[  210.599511] wlan0: direct probe to AP 00:23:69:85:70:f4 (try 2)
[  210.604513] wlan0: direct probe responded
[  210.604517] wlan0: authenticate with AP 00:23:69:85:70:f4 (try 1)
[  210.606601] wlan0: authenticated
[  210.606624] wlan0: associate with AP 00:23:69:85:70:f4 (try 1)
[  210.610898] wlan0: RX AssocResp from 00:23:69:85:70:f4 (capab=0x411 status=0 aid=2)
[  210.610903] wlan0: associated
[  210.852502] type=1503 audit(1275886579.226:18):  operation="open" pid=2817 parent=2780 profile="/sbin/dhclient3" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/var/lib/wicd/dhclient.conf"
[  220.654635] wlan0: deauthenticating from 00:23:69:85:70:f4 by local choice (reason=3)
[  220.903299] wlan0: deauthenticating from 00:23:69:85:70:f4 by local choice (reason=3)
[  221.102885] wlan0: direct probe to AP 00:23:69:85:70:f4 (try 1)
[  221.110301] wlan0: direct probe responded
[  221.110305] wlan0: authenticate with AP 00:23:69:85:70:f4 (try 1)
[  221.112400] wlan0: authenticated
[  221.112420] wlan0: associate with AP 00:23:69:85:70:f4 (try 1)
[  221.116635] wlan0: RX AssocResp from 00:23:69:85:70:f4 (capab=0x411 status=0 aid=2)
[  221.116639] wlan0: associated
[  231.181034] wlan0: deauthenticating from 00:23:69:85:70:f4 by local choice (reason=3)
[  231.404365] ath9k: Two wiphys trying to scan at the same time
[  231.404401] wlan0: deauthenticating from 00:23:69:85:70:f4 by local choice (reason=3)
[  231.605162] wlan0: direct probe to AP 00:23:69:85:70:f4 (try 1)
[  231.803670] wlan0: direct probe to AP 00:23:69:85:70:f4 (try 2)
[  231.813658] wlan0: direct probe responded
[  231.813662] wlan0: authenticate with AP 00:23:69:85:70:f4 (try 1)
[  231.815787] wlan0: authenticated
[  231.815821] wlan0: associate with AP 00:23:69:85:70:f4 (try 1)
[  231.819837] wlan0: RX AssocResp from 00:23:69:85:70:f4 (capab=0x411 status=0 aid=2)
[  231.819841] wlan0: associated
[  241.862805] wlan0: deauthenticating from 00:23:69:85:70:f4 by local choice (reason=3)
[  242.111252] ath9k: Two wiphys trying to scan at the same time

[B]6)Network configuration
[/B]  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:5c:61:8b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2a00000-d2a0ffff[B]
7)Scan for networks:
[/B]It displays my wireless among a couple others
[B]8) ubuntu version:
[/B]Description:    Ubuntu 10.04 LTS
**9)****Kernel/architecture (including 32 vs. 64 bit): **
2.6.32-22-generic i686
[B]10)restarting the network
[/B] * Reconfiguring network interfaces...                                                                                                 Ignoring unknown interface wlan0=wlan0.
       [ OK ]

---

### Post by puppywhacker on 2010-06-07
driver you're using is ath9k

error message in dmesg that is most significant is
"deauthenticating from by local choice"

I think this is driver related although I thought that ath9k was pretty stable. the error is printed by the mlme portion of the kernel which I thought was responsible for the lower layer physical wireless connection. As a workaround you could unload your module and load it again,

```
sudo modprobe -r ath9k
sudo modprobe ath9k 
```

good job on the error reporting, it is impressively detailed and still readable.

---

### Post by paul.turner on 2010-06-07
Alright I'll try this when I get back today and update you on how it goes.

---

### Post by paul.turner on 2010-06-07
No dice, still doing it.  Could it be something with my router? (I only ask this because I've used wireless in class with almost no problems)  I've never had a problem with disconnecting on my router before in windows and after 20 mins of disconnecting it sometimes stops and manges to hold a connection SO I'm doubting its my router.

---

### Post by anoop999 on 2010-06-07
I had this problem on my laptop ('deauthenticating by local choice' every few minutes). I did the following:
Install wicd (an alternative network manager, apparently better than GNOME network manager)
Uninstall network-manager (it may have been causing conflicts)

You might need to restart the computer. 
I also uninstalled smartdimmer because there was a rumour that it might be implicated, but I'm not sure if that made any difference.

---

### Post by albywolf on 2010-06-07
I don't know whether it can apply to your case.
Upgrading from 9.04 to 10.04 I started having serious disconnection problems, most probably router related, that kept on losing connection, particularly using torrent clients.
Back with 9.04 I eventually had to abandon Azureus due to Java errors that killed it too often and switch to KTorrent, that did fine.
But on 10.04 it started losing connection.
After changing a lot of ports and lowering max connections with little or no effect, I finally decided to reset the router to default settings (and then I had to memorize some settings again, like router admin password, reserved addresses and WiFi password), but instead of setting again port forwarding and triggering, I simply set UPnP, and now it works almost decently, connection is shaky, with upload speed decent, but variable and low torrent download speed, but at least it doesn't kill my connection anymore.
It looks like I messed things up adding forwarded and triggered ports to ports, that on 9.04 worked fine, but now it looks like UPnP works better, I don't know why, maybe just because it's a very simple and not messy config.
My physical line isn't good, my mom's PC that is connected through WiFi often lost connection even when my wired PC was fine, I still have to check it again, though.

Ah, I didn't change at all Guarddog firewall's settings, but if I'll try again port forwarding and triggering, I'll do it more gradually.

---

### Post by paul.turner on 2010-06-07
> **anoop999 said:**
> I had this problem on my laptop ('deauthenticating by local choice' every few minutes). I did the following:
Install wicd (an alternative network manager, apparently better than GNOME network manager)
Uninstall network-manager (it may have been causing conflicts)

You might need to restart the computer. 
I also uninstalled smartdimmer because there was a rumour that it might be implicated, but I'm not sure if that made any difference.


Going to try this next, any other suggestions?

---

### Post by albywolf on 2010-06-07
> **albywolf said:**
> I don't know whether it can apply to your case.
Upgrading from 9.04 to 10.04 I started having serious disconnection problems, most probably router related, that kept on losing connection, particularly using torrent clients.
Back with 9.04 I eventually had to abandon Azureus due to Java errors that killed it too often and switch to KTorrent, that did fine.
But on 10.04 it started losing connection.
After changing a lot of ports and lowering max connections with little or no effect, I finally decided to reset the router to default settings (and then I had to memorize some settings again, like router admin password, reserved addresses and WiFi password), but instead of setting again port forwarding and triggering, I simply set UPnP, and now it works almost decently, connection is shaky, with upload speed decent, but variable and low torrent download speed, but at least it doesn't kill my connection anymore.
It looks like I messed things up adding forwarded and triggered ports to ports, that on 9.04 worked fine, but now it looks like UPnP works better, I don't know why, maybe just because it's a very simple and not messy config.
My physical line isn't good, my mom's PC that is connected through WiFi often lost connection even when my wired PC was fine, I still have to check it again, though.

Ah, I didn't change at all Guarddog firewall's settings, but if I'll try again port forwarding and triggering, I'll do it more gradually.


Did some further tries and googled around: Just UPnP not always works best, Azureus complained about being firewalled.
Tried port triggering, it made things worse and killed connection again, it looks like it's advised against for torrent as it stresses too much the router.
Tried port forwarding and now it works.

What I saw is that, maybe due to routers' little available memory, it's better, after restoring defaults, to save a very simple config (with the settings that you'd have to set again anyway) and start from it, trying to keep things as simple as possible. This obviously may apply to your case if you have a router problem, but I saw from these experiments that when too many stuff accumulates it's easy that things in home routers go bad: my current settings aren't very different from before, in theory, but applying them starting from a router config as clean as possible changed things.

Edit: for browsing and also for system updates and other downloads and connections not regarding P2P, UPnP worked fine, I was able to update my laptop's Kubuntu while I was browsing with the desktop, it was only P2P that required me to add port forwarding to get full speed. OTOH, port triggering with P2P appeared to be a major connection killer.

---

### Post by paul.turner on 2010-06-07
> **albywolf said:**
> Did some further tries and googled around: Just UPnP not always works best, Azureus complained about being firewalled.
Tried port triggering, it made things worse and killed connection again, it looks like it's advised against for torrent as it stresses too much the router.
Tried port forwarding and now it works.

What I saw is that, maybe due to routers' little available memory, it's better, after restoring defaults, to save a very simple config (with the settings that you'd have to set again anyway) and start from it, trying to keep things as simple as possible. This obviously may apply to your case if you have a router problem, but I saw from these experiments that when too many stuff accumulates it's easy that things in home routers go bad: my current settings aren't very different from before, in theory, but applying them starting from a router config as clean as possible changed things.

Edit: for browsing and also for system updates and other downloads and connections not regarding P2P, UPnP worked fine, I was able to update my laptop's Kubuntu while I was browsing with the desktop, it was only P2P that required me to add port forwarding to get full speed. OTOH, port triggering with P2P appeared to be a major connection killer.

I'm going to leave this for last simply because of that fact that after coming back to my laptop having left it on I'm connected without a single disconnect. (which is the part that pisses me off that something is only going wrong on startup)

---

