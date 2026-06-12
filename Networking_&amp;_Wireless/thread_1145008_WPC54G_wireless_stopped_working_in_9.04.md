---
title: "WPC54G wireless stopped working in 9.04"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by cbraxton on 2009-05-01
I have an old Compaq Evo n600c laptop that was running Xubuntu 7.10. It is using a Linksys WPC54G V2 pcmcia wireless adapter, which worked just fine in 7.10 with ndiswrapper.

Yesterday I updated the system to Xubuntu 9.04. (Did a clean install.) Now everything works *except* the wireless card! (Am using the same ndiswrapper driver.)

The card has partial functionality in that wireless networks are detected and listed. However, any attempt to actually connect does not succeed. What happens is that the connection attempt hangs on "Validating authentication" retries, ultimately timing out and failing. This occurs regardless of whether the wireless network is encrypted or not, and with Network Manager, Wicd, and command-line wireless utilities. (This is a dual-boot system, and the wireless card works OK in Windows.)

Anyone out there manage to get this card working in Ubuntu 9.04?

---

### Post by waltersfield on 2009-05-02
I have the exact same problem! Any fixes or suggestions out there?

---

### Post by noshooz on 2009-05-02
Same here. I have the same card (WPC54G, V3), it doesn't even seem to be recognized by 9.04. No networks even show up. 9.04 recognizes my Sprint USB mobile broadband adapter fine, connects right away. But I'd rather use my much faster home WLAN.

---

### Post by cbraxton on 2009-05-04
I also have a Trendnet TEW-424UBK USB wireless adapter that worked flawlessly with Ubuntu 8.10 right out of the box - no fiddling with ndiswrapper or drivers was needed. Now with Ubuntu 9.04 it no longers works. (I'll post a separate topic on this.) It looks like we may have taken a step backward with wireless functionality in v9.04.

---

### Post by Brad H on 2009-05-07
I have been reading lots of good things about Ubuntu so I downloaded an ISO of 9.04 and ran it on my laptop (Dell 2200).  I have been quite impressed with what I have seen but when I went to go online I was unable to get my wireless connection to work.  I am using a Linksys WPC54G.  I see there are others that are experiencing this difficulty and clearly they are all experienced Unbuntu users.  What's a newbie to do??  Can this be made to work?  Can it work while only running from the CD?  I do not want to do a full install until I am sure that this is going to work for me.
 
Thanks!
 
Brad H

---

### Post by promet on 2009-05-08
Ditto, for an upgrade from 8.10 to 9.04 on a Dell Latitude C640.

Working great in 8.10 with Ndiswrapper, now...not...

Have gone through re-installation of Ndiswrapper drivers, troubleshooting potential driver conflicts and no dice so far...

---

### Post by chi2jjk on 2009-05-26
After a crashed HDD on my wife's laptop, I installed a new one and loaded Ubuntu 9.04.  We are using a WPC54G ver.4 which worked perfectly under Wi..., but I (a Windows technician/admin and Linux newbie who converted my desktop to Fedora [soon to be Ubuntu]) cannot get this to even be recognized by Ubuntu.

Any help is greatly appreciated as I need to keep my wife online in order to sell her on Linux.  Thank you!

---

### Post by dmizer on 2009-05-26
The wpc54g v2 v3 and v4 cards all have different chipsets. So these problems across versions are not likely to be related. To check your chipset, look at the output of:
```
lspci
```

Those of you having problems with the wpc54g v2 cards, try disabling NDISWrapper as there may be a good native driver for this card now. If not, please let me know, or check this howto: [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

Those of you with V3, I believe this card has a Broadcom chipset and should have a good native driver. Remove (uninstall) NDISwrapper, connect to the internet via ethernet cable, let Ubuntu find the Broadcomm drivers, and you should be good to go.

For V4 cards will need to start a new thread as I'm not sure what the chipset is, but I suspect it's also Broadcom, so the above fix may also work for you.

---

### Post by promet on 2009-05-26
Hey [chi2jjk]("http://ubuntuforums.org/member.php?u=323625"),

 				[IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG] 				**Broadcom users having WPA login trouble in 9.04** 			
 			 			 		   		 		 		I have been struggling trying to enable wireless in Jaunty 9.04 since I installed it about two weeks ago.

I have a Linksys WPC54G pcmcia wireless card, which resisted all attempts connecting via WPA.

I went through a variety of solutions, mostly around the ndiswrapper driver. I have now come to the conclusion that ndiswrapper just is not currently working for this card at this stage in 9.04.

I had in the past several releases had great success with ndiswrapper so plowed through trying to find a solution in module combinations, wpa_supplicant.conf, dhclient.conf, etc. But it seems ndiswrapper is the weakest link here.

After near defeat, I discovered a post on "b43-fwcutter" I downloaded the version from the repositories and it worked for me immediatly after I installed it. I didn't even have to reboot.

I did however, have to reverse a lot of changes I had made trying to jury-rig a solution in the files:

/etc/modules
/etc/modprobe.d/blacklist.conf

That way I could prevent "ndiswrapper" from loading, and make sure "b43" and "ssb" loaded as they normally would by default (I had changed this while looking for a solution)

[COLOR=Red]NOTE:[/COLOR] b43-fwcutter only works on [COLOR=Red]some particular[/COLOR] Broadcom chipsets. To check your chipset as just mentioned by dmizer:

```
lscpi -vnn
```

the following chipset info:

```
07:00.0 Network controller [0280]: Broadcom Corporation BCM[COLOR=Red]4318[/COLOR] [AirForce One 54g] 802.11g Wireless LAN Controller [[COLOR=Red]14e4:4318[/COLOR]] ([COLOR=Red]rev 02[/COLOR])
    Subsystem: Linksys Device [1737:0048]
    Flags: bus master, fast devsel, latency 64, IRQ 11
    Memory at 3c000000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

```

[COLOR=Red]NOTE: [/COLOR]The Kernel driver and modules that you see immediatly above are the result [COLOR=Red]after[/COLOR] my installing b43-fwcutter [COLOR=Red]not before[/COLOR]. Just showing the chipset number there.

download b43-fwcutter:

 	Code:
 	sudo apt-get install b43-fwcutter 
 [COLOR=Red]when you are asked in the installation dialog "Fetch and install firmware?" answer "Yes" (just press "Enter) [/COLOR]

and just rebooting would probably be the most surefire way to get things running. This all works with Network-Manager-Gnome (nm-applet) as well, without having to fiddle with "wicd", "wifi-radar" etc. 

In my case the b43-fwcutter install augmented the existing b43 driver and allowed the b43 driver to work for my card (again, please note, not ALL Broadcom cards are supported - see below) perfectly in a way the "default" b43 driver configuration utterly failed to do. 

If you want to read more in detail about this check out:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

I hope this is of some use, I sure had a heck of a time fiddling with other solutions, so maybe if you have this same card it'll help.

cheers

---

