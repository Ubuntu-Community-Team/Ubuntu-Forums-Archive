---
title: "Help! Wired connection won't/takes forever to connect to internet!"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by nbtrap on 2009-03-26
I dual boot between Ubuntu 8.10 and Windows Vista. I am plugged into a public network on a university campus which has always worked fine. This is definitely NOT a problem with the network; my Xbox 360 and other computers have no problem connecting. I am beginning to think it's actually a hardware problem; I have an Intel PRO 100 network adapter.

The problem began yesterday after I mapped an FTP network drive in Vista. After disconnecting, I realized I had no internet connection, even though I was still connected locally. After rebooting and trying a few things, nothing changed; both Ubuntu and Vista automatically connected to my local network but could not access the internet.

But wait! I eventually figured out that if I uninstall and reinstall my network adapter from the Vista device manager or if I ask Windows to diagnose the problem by itself, I am usually able to connect to the internet. But alas! I have to do this after every reboot to establish a connection. By the way, my drivers are DEFINITELY up to date and are NOT the problem.

I didn't have any luck fixing the problem on Ubuntu (which, again, says it is connected to a network, but can't access the internet). THAT IS UNTIL I left my machine on overnight, and when I woke up, my internet connection was miraculously back! Divine Intervention was the only explanation! That is, until I restarted my machine, logged back into Ubuntu and was faced with the same problem.

This did shed some light on the problem, however. I realized that AFTER ABOUT AN HOUR OF INACTIVITY after rebooting IN UBUNTU, MY INTERNET CONNECTION IS RANDOMLY WORKING. I am typing this now in Ubuntu, as I left the computer on for a few hours during class so I could have internet when I got back. But I'm afraid to reboot, lest I lose my connection.

What's more: when I run Ubuntu's hardware testing, it tests the internet connection and tells me I have none even when I do! Also, the network icon on Ubuntu's "dashboard" doesn't look like it used to. When connected to the internet, it used to be two monitors stacked on top of each other with a small orange circle (not exclamation point) in one corner. Now, after I reboot AND EVEN AFTER MY INTERNET CONNECTION IS ESTABLISHED, the icon is just the two monitors and no circle.

What the hell is going on? Here's my ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:1c:c0:27:01:0e  
          inet addr:10.234.18.123  Bcast:10.234.18.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:10332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:4341531 (4.3 MB)  TX bytes:1117056 (1.1 MB)
          Memory:e3100000-e3120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1056 (1.0 KB)  TX bytes:1056 (1.0 KB)

When I type "sudo ifdown eth0," I get:

Ignoring unknown interface eth0=eth0.

When I type "sudo ifup eth0," I get the same message, EVEN THOUGH NETWORK MANAGER CLAIMS TO BE CONNECTED TO  "Auth eth0" AS IT ALWAYS HAS!

My /etc/network/interfaces only contains 2 lines:

auto lo
iface lo inet loopback


Does anyone have any idea what I can do? Does this seem like a hardware problem? If so, how/where/to whom do I go to repair/replace my network adapter? Please let me know if you need any more information. Thanks.

-Nathan

---

### Post by khelben1979 on 2009-03-26
I don't know what you should do, but replacing your network adapter to something better sounds like a good idea! I think different solutions from D-Link would work good with linux, however, if you're looking for some high quality stuff, then go for Belkin.

Look [here]("http://catalog.belkin.com/IWCatSectionView.process?Section_Id=200340") for some wireless networking stuff from Belkin. They can be a little expensive sometimes, then again, you get what you pay for.

---

### Post by nbtrap on 2009-03-26
Thanks for the advice, but I am not using wireless. I am plugged directly into the wall as I always have been. Well, technically it's plugged into a switch and then the wall, but the switch is definitely not the problem either. Anyone else have any ideas?

---

### Post by LiamWilson on 2009-03-26
It ay sound like a stupid answer, but try taking the power cable out of the back of the router (While it's still plugged in) Wait 3-5 seconds, and then plug it back in. It works wonders.

If you still get no improvement, while the 'connecting' icon in the top right is rotating, hover the mouse over the icon until it doesn't connect, and then what does it get up to before it doesn't connect?

---

### Post by khelben1979 on 2009-03-26
> **LiamWilson said:**
> It ay sound like a stupid answer, but try taking the power cable out of the back of the router (While it's still plugged in) Wait 3-5 seconds, and then plug it back in. It works wonders.

I need to turn off and on my ADSL modem which I have 8-9 times before the Linux system is able to use the modem. It isn't a good brand and it's a bit old. So your recommendation works here also. Been doing it for a long time, it's a pain but I can live with it.

---

### Post by nbtrap on 2009-03-26
I don't have a router; I am using a public network and am plugged directly into the wall.

I've found a little bit of a work around to the problem, though I'm still nowhere near satisfied:

When I finally DID get a good connection, I wrote down all the address numbers. Now after I reboot, I can manually type change the IP address, subnet mask &c. to what they were when the connection worked, and my connection is instantly restored. But this produces even more problems.

First of all, I can't figure out a way to make the system automatically connect with the manually configured settings on startup; I have to tell it to stop using whatever settings it uses every time. Also, I still don't understand why all of a sudden this was a problem to begin with. WHY DID THE AUTOMATIC CONNECTION RANDOMLY STOP WORKING IN THE FIRST PLACE?! I don't want to have to manually configure this every time I log on. And what happens when I take my computer home over summer? I hope to God this is a hardware problem that can be resolved by simply replacing the adapter. I should find out tomorrow.

In the meanwhile, anyone else have any ideas?

---

### Post by khelben1979 on 2009-03-26
In Debian I do this when I have unplugged/plugged in the network cable:

```
cd /etc/init.d
sudo network restart
```

It uses [DHCP]("http://en.wikipedia.org/wiki/Dhcp") over here.

---

### Post by nbtrap on 2009-03-27
Thanks for all your help, but I haven't resolved the problem.

I HAVE discovered that temporary fix I mentioned above, and that will have to do until I can replace my network adapter. Thanks again.

Regards,

-Nathan

---

