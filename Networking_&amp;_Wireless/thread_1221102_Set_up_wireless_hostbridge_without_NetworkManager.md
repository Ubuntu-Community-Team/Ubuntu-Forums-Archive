---
title: "Set up wireless host/bridge without NetworkManager"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by igitur on 2009-07-23
Hi,

I need help in setting up my PC as a wireless host.

But first some details:

I access the internet from my PC on a very flaky PPPoE connection. It drops several times a day. For this reason I prefer not to use NetworkManager as it doesn't support auto-reconnect. See [http://brainstorm.ubuntu.com/idea/3447/](http://brainstorm.ubuntu.com/idea/3447/)  

wicd isn't an option because it doesn't support PPPoE. So I prefer traditional ifup / ifdown and /etc/network/interfaces .

Now... I've got a USB wireless thingy with an RaLink RT2500 chipset. I want to set up my PC as a wireless host and then use my laptop or Nokia 5800 as wireless client to connect through my PC to the internet. It will be an ad hoc connection. The chipset doesn't support access points.

When I did try out NetworkManager, this was easy.  With the NetworkManager applet, I left-clicked the tray icon, create new network, typed in an SSID and that was that.  My laptop / Nokia could find the network and browse the internet.

How do I do the same with traditional networking?  Some forums say I have to install DHCP, bridge-utils and other stuff. I didn't install any of that, yet my setup worked fine with NetworkManager.  Does NetworkManager have built-in DHCP and bridging software?

When I *did* install DHCP and bridge-utils everything got messed up. I could setup my wlan0 interface with iwconfig and/or in my interfaces file, but as soon as I setup my br0 (bridging) interface, I lost all internet connectivity and couldn't recover it without first removing br0 from /etc/network/interfaces and rebooting. No, /etc/init.d/networking restart didn't work. br0 also messes up pppoeconf because pppoeconf doesn't find my PPPoE on eth0 anymore.

So I'm really scared of using anything bridge-utils related and if there's an easier way (like it seems NetworkManager might be doing) I'd prefer that way.

Ok, let's hope my post gets noticed in all the noise.

regards,
Francois

---

### Post by superprash2003 on 2009-07-23
basically you are trying to setup ICS ( Internet connection sharing ) take a look at this [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) .. dhcp is not a must since you could use static ip..

---

### Post by igitur on 2009-07-25
Wow, that was easy. Thanks.

---

