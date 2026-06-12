---
title: "Sharing out a 3G cell connection through the RJ45 port"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by frisket on 2011-02-04
I can't find an answer to this, probably because no-one else has ever tried it :-) It's been more than a decade since I had to get this down and dirty with networking :-) and as a result I have forgotten most of what I once knew.

Requirement: I have to give a training course in a room with no network connection of any type. Students will all have wifi-enabled laptops, but none will have 3G dongles.

What I have: 
[LIST]
[*]an Ubuntu 10.4 Dell Latitude D610 laptop with an Ethernet port; 
[*]a HTC Hero which works nicely as a 3G connection when cabled to the laptop via USB, but which is not capable of running Froyo; and 
[*]an old WiFlyer pocket wifi AP router (eg [http://www.mobiletechreview.com/tips/WiFlyer.htm](http://www.mobiletechreview.com/tips/WiFlyer.htm))
[/LIST]
I want to set the laptop so that it will forward the Internet connection from the phone (coming in on the USB port), out of the Ethernet port and into the WiFlyer, which will broadcast to the users. It will be slow, of course, but better than nothing.

The WiFlyer has an Ethernet port, its own OS, DHCP server, and works fine when connected to a wired source (it even has a phone dialer to let you wirelessly share a 56Kbit/s phone connection :-)

For unrelated reasons I don't want to root the phone, and it's too old anyway, so using it as an AP with Froyo is not an option.

The last time I did anything vaguely like this was back in the days of pre-wireless dial-up, when I configured an old desktop running Red Hat 4 to perform demand-dial for the house (wired) LAN :-)

What do I need to do with the network settings so that the laptop forwards the connection out the Ethernet port?

I'm currently connected through the phone, so here is the output of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:14:22:c8:86:25  
          inet6 addr: fe80::214:22ff:fec8:8625/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48850 (48.8 KB)  TX bytes:110829 (110.8 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:19:17:d7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:134 errors:1 dropped:4 overruns:0 frame:0
          TX packets:243 errors:0 dropped:4 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14801 (14.8 KB)  TX bytes:38269 (38.2 KB)
          Interrupt:17 Base address:0xa000 Memory:dfbff000-dfbfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51464 (51.4 KB)  TX bytes:51464 (51.4 KB)

usb0      Link encap:Ethernet  HWaddr b6:7a:5f:68:a6:3d  
          inet addr:192.168.100.100  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::b47a:5fff:fe68:a63d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1319 errors:6 dropped:0 overruns:0 frame:6
          TX packets:1309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1056824 (1.0 MB)  TX bytes:284842 (284.8 KB)

---

### Post by frisket on 2011-02-19
> **frisket said:**
> I can't find an answer to this, probably because no-one else has ever tried it :-)

This appears to be impossible to do.

---

### Post by Jive Turkey on 2011-02-19
I just implemented something like this.  It was easier than I thought it would be.  The main difference with my setup is that I used a usb wifi adapter attached to a headless server that connects to my neighbor's router and shares the net to my LAN.
like this:

**internet**<--wireless-->**usbwlan0**<---->**headless server**<--wired-->**router**<--wired&wireless-->**multiple computers**

Yours should be even easier read this:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

You should be able to use the method titled:"GUI Method via Network Manager."

---

### Post by PaulReaver on 2011-02-19
I've done this as well..... kinda...

I share the 3G connection with only a laptop wifi card to my wii, ps3, psp, 360 and netbook all at the same time.... there might be limitations on the amount of connections this way though.

if you have a atheros ath5k wifi card it can be done with hostapd, dhcp and some firewall rules...

look here
[http://www.net42.co.uk/os/linux/sharing_3g_with_hostapd.html](http://www.net42.co.uk/os/linux/sharing_3g_with_hostapd.html)

and I can also do it with my netbook with a Broadcom BCM4312 (using the sta drivers) via network manager...pointy clicky :)

I'm not sure they strictly apply to your situation....

---

### Post by false truths on 2011-02-19
I'm not going to be much help, mainly because I have never attempted anything like this in Ubuntu before, but I know a couple of things from doing something like this with Windows that may help you. First of all, a CAT5 cable won't handle the connection. To use a computer as a network gateway it has to be using a CAT6. Also, I don't know how well this will apply to Ubuntu, but in Windows, when you're using a computer as a network gateway, you cannot use that computer for anything else because the gateway takes realtime priority and disables everything else. You may want to consider borrowing a Windows laptop to broadcast the connection from, and try using it as a network gateway.

Sorry I'm not much help, the last time I attempted anything like this was over 2 years ago, when I used a Windows XP laptop to broadcast a router signal from the very edge of another router's signal range, effectively doubling the signal width in one direction. Unfortunately, I've forgotten all the steps I took to make it work.

---

### Post by inobe on 2011-02-19
alright, i didn't read the lot of it, but got what i needed.

heres the deal, no file sharing from host system, but they can certainly share your internet.

first thing you will need, your cell phone hooked up and connected.

router must be already configured, connection from laptop ethernet to routers "wan" port.

now go into settings, select the eth device connected to routers wan, and do.

[IMG]http://aslakjohansen.files.wordpress.com/2009/10/screenshot-editing-share-connection.png?w=379&h=503[/IMG]

you will need to restart network services or reboot, do the same for router afterwards.

everyone should have internet that connects to the router.

edit: never seen a router such as that, i would bend and buy regular router, i don't even know if that thing has a ethernet wan?

---

### Post by frisket on 2011-02-20
> **Jive Turkey said:**
> I just implemented something like this.  It was easier than I thought it would be.  The main difference with my setup is that I used a usb wifi adapter attached to a headless server that connects to my neighbor's router and shares the net to my LAN.
like this:

**internet**<--wireless-->**usbwlan0**<---->**headless server**<--wired-->**router**<--wired&wireless-->**multiple computers**

Yours should be even easier read this:
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

You should be able to use the method titled:"GUI Method via Network Manager."

That's what I thought, but apparently not. See more at [http://ubuntuforums.org/showthread.php?t=1691366](http://ubuntuforums.org/showthread.php?t=1691366)

---

### Post by frisket on 2011-02-20
> **false truths said:**
> I'm not going to be much help, mainly because I have never attempted anything like this in Ubuntu before, but I know a couple of things from doing something like this with Windows that may help you. First of all, a CAT5 cable won't handle the connection. To use a computer as a network gateway it has to be using a CAT6.

That's what I'm using, fortunately.

> Also, I don't know how well this will apply to Ubuntu, but in Windows, when you're using a computer as a network gateway, you cannot use that computer for anything else because the gateway takes realtime priority and disables everything else. You may want to consider borrowing a Windows laptop to broadcast the connection from, and try using it as a network gateway.

Quite the opposite. The reason I'm using linux is precisely because you *can* continue to use the machine :-) I can't imagine the horrors of trying to do this under Windows, with no proper access to the OS. It's bad enough under Linux when the documentation is all about edge cases and special parameters, but at least I know it's possible, having done the same with dial-up a long time ago...

> Sorry I'm not much help, the last time I attempted anything like this was over 2 years ago, when I used a Windows XP laptop to broadcast a router signal from the very edge of another router's signal range, effectively doubling the signal width in one direction. Unfortunately, I've forgotten all the steps I took to make it work.

No problem...my brain is in the same position :-)

---

### Post by frisket on 2011-02-20
> **inobe said:**
> alright, i didn't read the lot of it, but got what i needed.

heres the deal, no file sharing from host system, but they can certainly share your internet.

If I can get the connection working, I can configure Apache on the resulting LAN.

> first thing you will need, your cell phone hooked up and connected.

router must be already configured, connection from laptop ethernet to routers "wan" port.

Should the router be configured with a fixed IP address, given that I am not running DHCP on the laptop to give it one? And what address block should that be in?

> now go into settings, select the eth device connected to routers wan, and do.

The doc at [https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20via%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29](https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20via%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29) clearly implies that you should not do this when there is a connection active on the port.

In any case, as I reported in [http://ubuntuforums.org/showthread.php?t=1691366](http://ubuntuforums.org/showthread.php?t=1691366), all that happens is NetworkManager pops up the "eth0 Connected" message...and then "Disconnected"...and then "Connected"...and then "Disconnected"...etc.

> you will need to restart network services or reboot, do the same for router afterwards.

Natch

> everyone should have internet that connects to the router.

Is this a general policy or a political wish? :-)

> edit: never seen a router such as that, i would bend and buy regular router, i don't even know if that thing has a ethernet wan?

Yes, absolutely, that's why I have it. [http://www.mobiletechreview.com/tips/WiFlyer.htm](http://www.mobiletechreview.com/tips/WiFlyer.htm)
A regular router offers no advantage here.

---

### Post by inobe on 2011-02-20
> **frisket said:**
> If I can get the connection working, I can configure Apache on the resulting LAN.



Should the router be configured with a fixed IP address, given that I am not running DHCP on the laptop to give it one? And what address block should that be in?



The doc at [https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20via%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29](https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20via%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29) clearly implies that you should not do this when there is a connection active on the port.

In any case, as I reported in [http://ubuntuforums.org/showthread.php?t=1691366](http://ubuntuforums.org/showthread.php?t=1691366), all that happens is NetworkManager pops up the "eth0 Connected" message...and then "Disconnected"...and then "Connected"...and then "Disconnected"...etc.



Natch



Is this a general policy or a political wish? :-)



Yes, absolutely, that's why I have it. [http://www.mobiletechreview.com/tips/WiFlyer.htm](http://www.mobiletechreview.com/tips/WiFlyer.htm)
A regular router offers no advantage here.


hey man, whatever works for you :tongue:

what i described is how i had it set up for several months, everyone leeched from cell phones evdo connection, till i was able to get internet services due to my new location.

> Sharing out a 3G cell connection through the RJ45 port

if you want to manually assign addresses and tinker with apache, have at it :)

---

### Post by headvampyre@hotmail.co.uk on 2011-02-20
Couldnt you configure a squid proxy server and configure it only to use the 3G connection inbound and use the RJ45(Cat5/5e) port for outbound? Shouldnt be a massive job :)

---

### Post by penseBien2 on 2011-02-20
> **frisket said:**
> If I can get the connection working, I can configure Apache on the resulting LAN.



Should the router be configured with a fixed IP address, given that I am not running DHCP on the laptop to give it one? And what address block should that be in?



The doc at [https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20via%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29](https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI%20Method%20via%20Network%20Manager%20%28Ubuntu%209.10%20and%20up%29) clearly implies that you should not do this when there is a connection active on the port.

In any case, as I reported in [http://ubuntuforums.org/showthread.php?t=1691366](http://ubuntuforums.org/showthread.php?t=1691366), all that happens is NetworkManager pops up the "eth0 Connected" message...and then "Disconnected"...and then "Connected"...and then "Disconnected"...etc.



Natch



Is this a general policy or a political wish? :-)



Yes, absolutely, that's why I have it. [http://www.mobiletechreview.com/tips/WiFlyer.htm](http://www.mobiletechreview.com/tips/WiFlyer.htm)
A regular router offers no advantage here.
You can just give your Router static IP to the Ubuntu laptop, Use the method of sharing internet connection as described above.

---

### Post by frisket on 2011-02-21
Fixed. It turned out that 10.4 appears to have installed both dnsmasq *and* dnsmasq-base by default, so dnsmasq had to be removed and masquerading enabled manually. I have updated the wiki at [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) to reflect this. Thanks for all the suggestions.

---

