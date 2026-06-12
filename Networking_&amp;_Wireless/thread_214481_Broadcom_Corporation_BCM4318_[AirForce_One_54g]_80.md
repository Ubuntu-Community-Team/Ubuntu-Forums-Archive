---
title: "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller  rev2"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by FooAtari on 2006-07-12
Hi Folks!

Too much information can be a bad thing, and I am so confused that I am unsure where to start.

I have installed various distros of linux a couple of times, but haven't learned a whole lot while doing so, especially when it comes to Wireless connections, or anything else for that matter...

As you can see from above I have a Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) card or ASUS WL 138-G V2.

So far I have established that the card is recognised and the driver, bcm43xx is loading at start-up, i think.

When I try and activate the card i get the following error:

[i]**Could not enable the interface eth1**

Check that the settings are correct for this network and that the computer is correctly connected to it.[/i]

When I run iwconfig from Terminal I get this:

[I]lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"flat"  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.[/I]


So i am unable to activate the card and have no connection, because the card isn't activated, right?

But the system see's the card and the driver is loaded.

Where do i go from here?

There is a ton of information on the internet regarding native support and using Ndiswrapper.  Some sites even say the card is unsupported, but this information is perhaps out of date.

There is so much information that i am completely confused and lost as to what my next step should be.  I am able to connect just now via LAN connection, but having a cable dragged across the flat is not pleasing the girlfriend!

HELP!

Thanks very much.

---

### Post by MarkSheely on 2006-07-12
This thread here seems to be most helpful to bcm4318 users.  

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

There's a lot of information in that thread if you run into any more problems.

--Mark

---

### Post by FooAtari on 2006-07-13
Thank's ill give that one a go.

One question if someone could answer it, can anyone tell me if there is any advantage or disadvantage to using native (is that the right word) drivers over Ndiswrapper or Ndiswrapper over native!

Thanks

---

### Post by krazyd on 2006-07-13
I have the exact same card, and I would definitely recommend ndiswrapper over the native bcm43xx driver at this stage.
I have had both drivers working, and while both fail to correctly report to network manager the signal strength (it always shows 100%), the bcm43xx driver also has far less range than its windows counterpart - it has to be right next to the access point to work. Ndiswrapper on the other hand works as well as in XP. :) By the way, while many guides on this forum recommend installing the latest version of ndiswrapper from source, I used the version in the repos and it worked fine.

I'm not sure why the signal strength doesn't work properly. If anyone knows, please let me know! :)

Also, install network manager as soon as you have ndiswrapper installed. It will automatically configure WPA/WEP etc. if you need it, and is generally very handy for wireless.

Do you have this card with a notebook? If so, what type (if you don't mind me asking :))?

---

### Post by FooAtari on 2006-07-13
Nah, its a PCI Adapter.  I was actually thinking about sticking it on ebay and picking something else up if there are better supported cards.

Recommendations welcome!

Got a good guide I can follow? The one above seems to be without Ndiswrapper.

---

### Post by Max Roswell on 2006-07-13
Hey, that thread (the one that MarkSheely posted) just got my 4318 working, lickety-split.  It uses Ndiswrapper, but it's as easy as downloading an archive, unzipping it, and running a script.  Highly recommended.

---

