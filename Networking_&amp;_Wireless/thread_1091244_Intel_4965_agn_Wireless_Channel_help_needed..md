---
title: "Intel 4965 agn Wireless Channel help needed."
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by heavensfire on 2009-03-09
Hi,

I have a Dell XPS M1330 ordered via Dell australia.

The wireless card is an Intel 4965 agn. The driver is "iwlagn"

I am in Europe at the moment and trying to connect to a wireless network on channel 13. I am unable to see the network.

I have the following lines in my /etc/modprobe.d/options: 

> #Channel 12 and 13 support for wireless
options cfg80211 ieee80211_regdom=EU

I am a bit worried by this output from dmesg though:

>  iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
iwlagn: Copyright(c) 2003-2008 Intel Corporation
iwlagn 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
iwlagn 0000:0c:00.0: setting latency timer to 64
iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[COLOR="Blue"]iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels[/COLOR]


Does this mean my wireless is crippled to use only US-legal channels? (Seems unfair as channel 12 and 13 are legal in Australia)

Is it possibe to update the firmware or eeprom in some way to allow more channels to be tuned?

Is there some other way of testing/getting my wireless hardware capabilities?

Thanks in Advance.

---

### Post by heavensfire on 2009-03-10
Even if someone can just answer this one question that would be a great help:

> **heavensfire said:**
> 
Does this mean my wireless is crippled to use only US-legal channels? (Seems unfair as channel 12 and 13 are legal in Australia)


---

### Post by HeadInTheClouds on 2009-04-25
You could try the last post in this thread:

ubuntuforums.org/archive/index.php/t-87274.html

I am fixing my IBM T400 for the same issue right now - UK based so 13 is fine for me!

I will post my findings

/HITC

---

### Post by HeadInTheClouds on 2009-04-25
You need to edit your options file in /etc/modprobe.d
so run a terminal
then
sudo gedit /etc/modprobe.d/options

add a line: options cfg80211 ieee80211_regdom="EU"
What I cannot tell you is if this line is the same for your adapter, I also has tried the following without sucess (they are different cards - wmaster0 is probably completely wrong!):
options ipw2200 ieee80211_regdom=64
options wmaster0 ieee80211_regdom=64

See:
[https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/227643](https://bugs.launchpad.net/ubuntu/+source/wireless-tools/+bug/227643)
the last post by Jens Gottfried worked (thanks Jens!)
then I did the following to reload the module:
sudo modprobe -r iwlagn && sudo modprobe iwlagn
The wireless then connceted, but I had to logout and in again before Mozilla was prepared to use the new connection (I assume it was still attempting to route via the mobile broad band card I had been using.

---

