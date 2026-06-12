---
title: "Why are 802.11n cards so badly supported in Linux?"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by tbessie on 2009-11-30
Or at least, in Ubuntu?

I've been trying to get various 802.11n cards working on my ol' Thinkpad x40 (USB and Cardbus connected devices), and both Ralink and Atheros based chipsets fail miserably.  Ralink seem very badly supported, and Atheros are supported up to G speeds, but not N speeds, and N chipsets spontaneously disconnect and reconnect in the ath9k driver.

Ok, I know all of this is free, I ought not to complain.  But Wifi - especially current wifi devices - are the most commonly used, what with the explosion of netbooks, etc.  You'd think more folks'd be spending more time on those devices.

Does anyone know of any 802.11n USB or Cardbus devices that are fully supported by a native driver at full speed with all (or most) features supported, running with WPA2?  I can't seem to find such a beast that doesn't have a host of problems associated with it.  *Especially* not if the device is dual-band (which all seem to be Ralink-chipset based devices at the moment).

- Tim

---

### Post by tbessie on 2009-11-30
By the way, this includes use of ndiswrapper - I've tried using ndiswrapper on 2 separate cards (one USB/Ralink based, one Carbus/Atheros based), and neither worked.

- Tim

---

### Post by bkratz on 2009-11-30
> **tbessie said:**
> Or at least, in Ubuntu?

I've been trying to get various 802.11n cards working on my ol' Thinkpad x40 (USB and Cardbus connected devices), and both Ralink and Atheros based chipsets fail miserably.  Ralink seem very badly supported, and Atheros are supported up to G speeds, but not N speeds, and N chipsets spontaneously disconnect and reconnect in the ath9k driver.

Ok, I know all of this is free, I ought not to complain.  But Wifi - especially current wifi devices - are the most commonly used, what with the explosion of netbooks, etc.  You'd think more folks'd be spending more time on those devices.

Does anyone know of any 802.11n USB or Cardbus devices that are fully supported by a native driver at full speed with all (or most) features supported, running with WPA2?  I can't seem to find such a beast that doesn't have a host of problems associated with it.  *Especially* not if the device is dual-band (which all seem to be Ralink-chipset based devices at the moment).

- Tim




This is why

**802.11n**

 Main article: [IEEE 802.11n-2009]("http://en.wikipedia.org/wiki/IEEE_802.11n-2009")
 802.11n is a recent amendment which improves upon the previous 802.11 standards by adding [multiple-input multiple-output]("http://en.wikipedia.org/wiki/Multiple-input_multiple-output") (MIMO) and many other newer features. The IEEE has approved the amendment with an expected publication in mid October 2009.[[11]]("http://en.wikipedia.org/wiki/IEEE_802.11#cite_note-80211nPR-10") Enterprises, however, have already begun migrating to 802.11n networks based on the [Wi-Fi Alliance's]("http://en.wikipedia.org/wiki/Wi-Fi_Alliance") certification of products conforming to a 2007 draft of the 802.11n proposal.
   Release date Op. Frequency [Throughput]("http://en.wikipedia.org/wiki/Throughput") (typ.) [Net bit rate]("http://en.wikipedia.org/wiki/Net_bit_rate") (max.) [Gross Bit Rate]("http://en.wikipedia.org/wiki/Gross_bit_rate") (max.) Max Indoor Range Max Outdoor Range   September 11, 2009 [[1]]("http://www.reuters.com/article/pressRelease/idUS183099+11-Sep-2009+BW20090911") 
 5 GHz and/or 2.4 GHz 50-144 Mbit/s[*[citation needed]("http://en.wikipedia.org/wiki/Wikipedia:Citation_needed")*] 600 Mbit/s[[12]]("http://en.wikipedia.org/wiki/IEEE_802.11#cite_note-11")  ?? Mbit/s 300 feet/91 meters 600 feet/182 meters

Note:  expected publication in mid October 2009.


That is pretty new

---

### Post by coffeecat on 2009-11-30
> **tbessie said:**
> N chipsets spontaneously disconnect and reconnect in the ath9k driver.

My N AR928X Atheros chipset (using the ath9k driver) became reliable when I installed the linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic packages. Granted, that was connecting to a G router, so I would be interested to hear others' experiences of N Atheros chipsets connecting to an N router with the backports modules installed.

If you look inside one of the backports packages (it might be one of the dependencies pulled in by those two), there are several wireless modules apart from Atheros. I can't remember whether Ralink was in there (on another machine atm so I can't check), but it might be worthwhile to try the backports modules with other chipsets.

---

### Post by tbessie on 2009-11-30
> **bkratz said:**
> This is why

**802.11n**

... snipped ...

Note:  expected publication in mid October 2009.


That is pretty new

Well, yes, but Draft-N devices themselves have been around for quite awhile. :-)

- Tim

---

### Post by tbessie on 2009-11-30
> **coffeecat said:**
> My N AR928X Atheros chipset (using the ath9k driver) became reliable when I installed the linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic packages. Granted, that was connecting to a G router, so I would be interested to hear others' experiences of N Atheros chipsets connecting to an N router with the backports modules installed.

If you look inside one of the backports packages (it might be one of the dependencies pulled in by those two), there are several wireless modules apart from Atheros. I can't remember whether Ralink was in there (on another machine atm so I can't check), but it might be worthwhile to try the backports modules with other chipsets.

Yes, I read about that in another thread.  I'll try that when I get home.  I'd prefer to use the latest and greatest (which seem to be dual-band ralink based devices), but those don't seem to be working deliably lately, backports or not.

I bought a D-Link DWA-652 specifically - after returning a ralink based Linksys USB device - because it seemed to at least work, sometimes. :-)  I'll see if using backports helps, thanks!

- Tim

---

### Post by bean1945 on 2009-11-30
Tim,

I have a D-Link 552  wireless n adaptor installed on my Dell 3000 Desktop and the backport trick did help the signal and speed. ndiswrapper worked but produced an error message and only recognized g. 

You can thank Super Sonic 4 for the suggestion.

Jerry

---

