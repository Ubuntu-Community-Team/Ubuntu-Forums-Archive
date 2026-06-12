---
title: "Broadcom users having WPA login trouble in 9.04"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by promet on 2009-05-26
I have been struggling trying to enable wireless in Jaunty 9.04 since I installed it about two weeks ago.

I have a Linksys WPC54G pcmcia wireless card, which resisted all attempts connecting via WPA.

I went through a variety of solutions, mostly around the ndiswrapper driver. I have now come to the conclusion that ndiswrapper just is not currently working for this card at this stage in 9.04.

I had in the past several releases had great success with ndiswrapper so plowed through trying to find a solution in module combinations, wpa_supplicant.conf, dhclient.conf, etc. But it seems ndiswrapper is the weakest link here.

After near defeat, I discovered a post on "b43-fwcutter" I downloaded the version from the repositories and it worked for me immediatly after I installed it. I didn't even have to reboot.

I did however, have to reverse a lot of changes I had made trying to jury-rig a solution in the files:

/etc/modules
/etc/modprobe.d/blacklist.conf

That way I could prevent "ndiswrapper" from loading, and make sure "b43" and "ssb" loaded as they normally would by default (I had changed this while looking for a solution)

download b43-fwcutter:

```
sudo apt-get install b43-fwcutter
``` [COLOR=Red]when you are asked in the installation dialog "Fetch and install firmware?" answer "Yes" (just press "Enter) [/COLOR]

and just rebooting would probably be the most surefire way to get things running. This all works with Network-Manager-Gnome (nm-applet) as well, without having to fiddle with "wicd", "wifi-radar" etc. 

In my case the b43-fwcutter install augmented the existing b43 allowed the b43 driver to work for my card (note not ALL Broadcom cards are supported - see below) perfectly in a way the "default" b43 driver configuration utterly failed to do. 

If you want to read more in detail about this check out:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

I hope this is of some use, I sure had a heck of a time fiddling with other solutions, so maybe if you have this same card it'll help.

cheers

---

