---
title: "Need a second wifi connection"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by CosmoSmallpiece on 2011-01-11
If anyone has experience with getting the TP-LINK841N usb adapter working on ubuntu, and/or getting two wireless links working on ubuntu, I would be most appreciative of any information.

I use ubuntu 10.04 with a relatively old but good laptop.  It has an 802.11b/g internal wifi card which works well with ubuntu. It shows up as eth1 in 'ifconfig'. The laptop also has a hard wired port, eth0.

In addition to my normal home wifi connection, I have been using eth0 (wired point to point) to get a remote desktop of my windows 7 box on my laptop, using rdesktop.  It works well, I can browse the net and have a reasonably fast remote windows desktop all on my laptop -   but I need to sit next to the windows box!!

I would like to be able to use a second wireless link, point to point (ad-hoc) to replace the ethernet cable.  I have done this using my internal wifi card - it works but not as fast.  I would prefer to keep my internal slower (802.11g) card for my internet connection as I do now, and use a new 802.11n wifi (adhoc) for the rdp to the windows box.  

To this end I bought a pair of usb adapters, TP-LINK841N.  One went into the windows box, the other plugged into a spare usb port on the lappie.  The windows end works (I can see the card in the network settings page etc ) but my ubuntu laptop does not see the new USB wifi adapter at the other end.
  
Actually, my  laptop internal card connects to the new adapter on the windows box but i then lose my internet connection because the point to point link is using my old original adapter, not the new one.

I believe that if ubuntu recognised the new wifi adapter, I would have another 'eth2' entry appear in 'ifconfig'.  Note that the normal wifi internet connection is on 192.168.2.xx (local wifi lan) and my new ad-hoc point to point connection for rdp is on 192.168.3.xx and I have a route set up for it.
If I use ndiswrapper for the new usb wifi adapter, I think I will stuff up my working wifi (internal card).

I cant be the first person to want to have two wifi network links but there's not a lot of information out there on this specific need.

The important point is that the ad-hoc link between windows and laptop needs to be as fast as possible for rdp, hence the need for a new 300Mbs wifi adapter.
If I can get this working, I will essentially be able to administer my windows box from wherever I happen to be in the house, from my lappie.
I would also settle for just getting the lappie wifi upgraded (via the new usb adapter)and use the rdp session on the windows box to get to the internet if I have to - because I think windows will run several wifi adapters at once (because they write the drivers for windows only dont they)

So if anyone has experience getting the TP-LINK841N usb adapter working on ubuntu, and/or getting two wireless links working on ubuntu, I would be most appreciative of any information.

---

### Post by grahammechanical on 2011-01-11
I am confused. That is not unusual for me. So, do not expect much help. Sympathy and an attempt to help you think in a different direction. May be.

My built in wireless adapter is listed as wlan0 but it is actually plugged into an internal ethernet slot. I think that wireless or wired are actually ethernet type of devices. I am not sure about USB.

If I understand correctly, you want to use one wireless adapter to connect to the modem and another wireless adapter to connect to another computer. I cannot tell you how to do this but I guess that the key lies in how you set up each wireless connection.

If I was trying to do this and getting information from the motherboard user guide, then I would setup the connection using the internal device (eth0 in your case, wlan0 in my case) in Infrastructure mode. Then I would set up the external device (eth1 in your case, wlan1 in my case, I guess) in Ad-hoc mode.

I am also guessing that each wireless adapter would need to be tuned in, as it were, to the particular transmissions of the wireless devices that you want them to connect to. This, I again guess, would be done through setting the particular IP address of the modem in the configuration of eth0 (internal adapter) and the particular IP address of the Windows machine in the configuration of eth1 (external adapter). Or, should that be MAC addresses?

Every wireless adapter detects the transmissions (broadcast) of every wireless device within range. How do we make the adapter in one computer connect to the particular device that we want it to? This is the issue. I think.

Regards.

These are just my thoughts on this.

Regards.

---

