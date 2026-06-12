---
title: "3Com 3CRWE62092B PCMCIA WiFi Card Not Working Under 6.06 (Worked Fine under 5.10)"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by svet-am on 2006-06-09
Here are the specs on my laptop:

IBM ThinkPad T21 (PIII SpeedStep 1.0GHz/512MB PC100 SDRAM/60GB HDD)

The only PCMCIA card I am using is the 3Com 3CRWE62092B (M/N: SL-1110).  As far as I can tell, this card is true PCMCIA, not CardBus.

To make a long story short, this card worked *PERFECT* out of the box under 5.10.  It was able to find my access point, get an IP address via DHCP, and then browse around just fine.  The networking applet under 5.10 even worked very swell in allowing me to switch between my wired ethernet (eth0) and my wireless ethernet (eth1) on the fly.

When 6.06 came out, I immediately downloaded an ISO and installed it as a clean install on the ThinkPad.  Upon final reboot, eth0 works fine, but I could not get eth1 to work properly.  In the network configuration applet I "deactivated" eth0 and "activated" eth1 and this only served to crash the network control applet.  Further, after this, I could no longer activate eth0.  Attempting to deactivate eth1 and activate eth0 would crash the network applet.  The only way to make eth0 work properly was a full reboot.

I did some Google searching and found a few issues related islsm_pci, etc and its conflicts with prism54.  That didn't sound quite like my problem (since this card uses the atmel firmware) but I tried it anyway and it didn't help.

Knowing that everything was perfect under 5.10, I installed 5.10 and verified that all of my gear still functions properly -- it does.  Then, instead of re-installing a clean install, I did a "upgrade" install from 5.10 to 6.06.  The thinking here was that 6.06 would not overwrite and pre-created networking scripts and that everthing should work after the upgrade.  Alas, this was not the case and after rebooting following the upgrade, I was in exactly the same place as following the clean install of 6.06.

Any attempts to activate eth1 and then make it the default gateway device simply crash the networking applet.

As an aside, I saw some mention in Google that Flight 5 (I think) required an install of the package 'atmel-firmware' via Synaptic in order to make atmel-based cards work properly.  As of now, I do not see this package in any of the repositories (including multiverse and universe).

What is the properly method for getting this card working?  Is it supported anymore?  Thanks!

---

### Post by bobleo on 2006-06-10
I have the same issue, but with a different PCMCIA card. (Orinoco Gold 128 / Lucent Technologies).  Everything work perfect under 5.10 then I did the upgrade to 6.06, and my WiFi does not get an IP address via DHCP.  I see my SSID and the card is active, it is like the key does not work so I can not get an Address via DHCP.  I HOT PLUG the card and some times it work fine for a wile then it does not?  I have an IBM T20.

I wounder is 6.06 is fully baked?  If anybody can let us know what has changed from 5.10 to 6.06 for PCMCIA WiFi support I would appriciate it.

BTW, I have tried WiFi-Radar, ndis wrappers, etc. with no luck.

---

### Post by schneo on 2006-06-19
I have exactly the same problems but with a "dexlan" (the brand of the pcmcia) on a Acer Aspire1300 laptop which worked fine under Breezy. 
(The only difference is that the "hotplug" doesn't work on my laptop)

I'll be glad to have a solution too !  ](*,)

---

### Post by erganondorf on 2006-07-02
That is exactly what is happening to me with my laptop. My wi-fi adapter is a 3Com 3CRWE154G72. It used to work out of the box flawlessly with Breezy 5.10,  but not under Dapper 6.06. It used to appear as eth1 (eth0 being the wire LAN adapter). Now eth1 has vanished and appears as eth2. It may be configured, activated and deactivated. Configuration files look correct but... it does not work. Any cure, please?.
Thanks in advence from Eric.

---

### Post by fascik on 2006-07-07
I have the same :-( But my 3CRWE62092B sometimes works but only with static IP and with WEP key. When I setup DHCP and turnoff WEP key wireless can't connect to AP.

---

### Post by linuxpro on 2006-07-13
I got the same problem here, everything worked fine using 5.10, after upgrading to 6.06 nothing wireless works. It fails when trying to configure the wep key returning "Set Encode" (8B2A) : Unknown error 524. 

GRRRR   :evil:

---

### Post by lyman on 2006-08-08
I have the same problem with Compaq Evo N600c and 3CRWE62092B.

---

### Post by Kinux on 2006-09-20
I have the same problem.

So, nobody in Ubuntu world have any idea what went wrong in 6.06 and 6.06-1?

We have to buy new cards or get back to 5.10 ?! I searched all the net for keywords that have any connection to Atmel, or at76c50x or 3CRWE62092B to no avail.

Wireless assistant can see my AP, I don't have a WEP key, and it don't get an IP and times out.

It seems that when something works in Linux, we don't have to take it as granted for next versions.:sad:

---

### Post by fascik on 2006-09-20
Yes. I bought "no-name" PCMCIA card with RTL8180 chipset. But don't sell 3COM, I hope it'll work ;-)

---

### Post by Propwash on 2006-10-22
I have a Toshiba Satellite 4090XDVD (old thing I know) with a 3COM 3CRWE62092B Wireless card as well.  Everything worked fine under 5.10 and still works under an upgraded 6.06.  The only odd thing is that the laptop sometimes loses connectivity with the wireless router.  It stills says connected and the signal strength is onver 90% but it doesn't seem to receive.  Simply pushing the card antenna in and letting it out restores the connection.  I haven't found a lasting fix.  Otherwise everything works.  If any of you having trouble with this card and 6.06 want to compare settings let me know.

---

### Post by fascik on 2006-10-26
Ubuntu 6.10 is out... someone try to run 3Com 3CRWE62092B? I hope it'll work on 6.10 :)

---

### Post by Propwash on 2006-11-02
I was running 5.10 - everything worked.  Upgraded to 6.06 and had some intermittent problems with the ethernet connection. I didn't find a fix although I understand some of the wireless code was moved between these revisions - there are other network problems of similar ilk on the forums.  Upgraded to 6.10 and everything is fine again.  It seems that whatever was odd about the 3Com card and the kernel in 6.06 is now better in 6.10.

---

