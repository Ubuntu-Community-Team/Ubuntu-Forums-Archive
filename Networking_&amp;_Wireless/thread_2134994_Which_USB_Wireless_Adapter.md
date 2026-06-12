---
title: "Which USB Wireless Adapter??"
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by johncroc on 2013-04-12
Hello fellow Ubuntu-ers,
I am setting up a new machine and need some help.  The machine I am building has no available slots for a wireless network card, so I need a USB solution.  I plan to install 12.10 and am hoping for a wireless USB adapter that will work straight out of the box with no special installs or configuration.  My wireless network uses WPA/PSK TKIP authentication/encryption, so that must be supported and dual-band "N" would be nice, as well.

I've spent a number of hours reading everything I could find on the subject, and have been unable to find an answer that fills me with the confidence I'd like to have before spending my hard earned money.  Everything seems to refer to chipsets and "this works but you have to do this and that;"  I really just want to buy a wireless USB adapter, unwrap it, plug it in, configure the network details, and surf the internet.

Does such a beast exist?

Anxiously awaiting all the good news you are about to bestow on me...
John

---

### Post by ahallubuntu on 2013-04-12
~

---

### Post by johncroc on 2013-04-12
Thank you for your thoughts and suggestions.

I have 12.10 installed on another machine and am loving it.  I may install 12.04 on this one though, because it's the machine that runs my TV and I really don't want to have to re-configure it later on.

As for "N":  I have an "N" AP and have been using N successfully for over a year.  I have a small 2 br apartment and the separation between the AP and this adapter will be around 4 meters with a perpendicular penetration of a single wall; So I'm confident it will work fine.  However, you make a good point about going with "low tech" but reliable solutions (not to mention having redundancy by spending $12).

I have no fears about doing a little bit of tweaking (see my work with chili555 on getting the [Atheros 8161 wired network]("http://ubuntuforums.org/showthread.php?t=2122688&highlight=johncroc") working in my other Ubuntu machine).  I was simply asking for the "no compromises" solution to see if there was one.  And After my experience referenced above, I have deep confidence in the community's support on any problem I encounter.

I have to say that I am a complete convert to Ubuntu.  I have built a 30+ year career in IT with an emphasis on application development and database design...all on DOS/Windows platforms.  I think it's safe to say that there are precious few people on the planet who are more knowledgeable or more comfortable in that environment than I am, and I now DREAD having to reboot and use Windows (and I'm having to do that less and less).  Ubuntu ROCKS!!

---

### Post by ahallubuntu on 2013-04-12
~

---

### Post by johncroc on 2013-04-12
You're right.  And I should have been more clear:  I have been using dual-band N successfully for over a year (I have three Cisco AE2500 dual-band dongles).  However, the ONLY time that I get a benefit from dual (over single) is when I have some GIANT copy I need to do, like backing up my whole internal drive.  The better way to do that is to bring my external USB 3.0 device into the living room and plug it in directly.

Bottom line is single band N is plenty of "pipe" for what I'm going to be doing.

Prompted by your comments above I have been looking at the ultra mini dongles on Amazon.  Many of the reviewers complain about slow and weak connections, even when the device is very near an AP.  I fully recognize that there are many other factors and that these folks and all their neighbors may be on the same channel, or some such, but even reviews by what appear to be IT pros say the same things.  I'm a bit leery of the tiny antenna that must be packed into one of those and since this machine will rarely be moved I'm leaning towards a standard size dongle (presumably with a more robust antenna).  Do you (or anybody reading this thread) have thoughts on who's making standard sized USB dongles with the Realtek 8188 or 8192 (or any other Ubuntu compatible) chipset?

---

### Post by jeffblack18042 on 2013-04-13
TL-wn722n works out of the box with ubuntu 12.10 and xubuntu 12.04
nothing to dl nothing to install
tryed and tryed to install a wna3100 but no luck
swapped out the included antenna for tp-link 8db antenna
looks great taped to my window

---

### Post by ahallubuntu on 2013-04-13
~

---

### Post by kurt18947 on 2013-04-13
I have no experience with 5 ghz. I use N150 devices, they're reasonable cost and adequate for my purposes.  My preferred adapters are RealTek 8192SU based.  I have a Dlink DWA-131 v1 and a TrendNet TEW-649UB - they're twins.  I'd have concerns about buying a new Dlink DWA-131.  There is a thread that mentions a DWA-131 v.B or v.2 which uses a different chipset which is not plug 'n' play.  I also have a generic Ralink RT-5370, bought off Ebay for about $6.  It is plug 'n' play but signal strength is about half of the 8192SU based adapters.  Netgear WNA1100 uses an Atheros 9271 chipset and is plug 'n' play.

---

### Post by johncroc on 2013-04-16
> **jeffblack18042 said:**
> TL-wn722n works out of the box with ubuntu 12.10 and xubuntu 12.04
nothing to dl nothing to install


This sounds like EXACTLY what I was hoping for, PLUS it has an external (detachable) antenna, a bonus I hadn't even considered.  I bought one from Amazon for $18 and will report back when I receive and install it.

Many, many thanks to jeffblack18042 for the adapter suggestion, and also to ahallubuntu for the suggestion to install 12.04 (instead of 12.10).  And to kurt18947 for taking time to respond.  I hope someday, I can be more of a 'giver' and less of a 'taker' in these forums.

---

### Post by johncroc on 2013-04-20
> **jeffblack18042 said:**
> TL-wn722n works out of the box with ubuntu 12.10 and xubuntu 12.04
nothing to dl nothing to install
tryed and tryed to install a wna3100 but no luck
swapped out the included antenna for tp-link 8db antenna
looks great taped to my window

jeffblack18042's suggestion was exactly as advertised:
Unplugged my wired ehternet
Plugged in the TP-Link TL-WN722N
Waited a few seconds
Popup told me "wireless networks found"
Clicked on the wireless icon (upper right-hand corner)
Chose my SSID
Typed in my wireless password
Started surfing the internet

Perfect.  No drivers to install or compile, no settings to tweak, nothing, nada...not even a reboot...pure plug and play.

Changing this thread to [SOLVED].

---

