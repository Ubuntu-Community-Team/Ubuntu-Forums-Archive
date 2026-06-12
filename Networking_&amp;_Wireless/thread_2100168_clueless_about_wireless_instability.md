---
title: "clueless about wireless instability"
date: 2012-12-31
forum: Networking &amp; Wireless
---

### Post by chitowner2 on 2012-12-31
Right now i am sitting at my desk. My nook (4.1.2; CM10) is in front of me and my wireless router (Netgear WNDR3400v2 dual-band)is at my elbow. I am watching the wireless signal-strength icon on my nook range from zero to 100% repeatedly over a few minutes, back and forth. 

My nook does not behave this way in other wifi environments, but this is /typical/ behavior here. My wife's nook and our laptops replicate the problem! The router is a few months old. I bought it to replace a TP-Link router of similar function, and before that a series of other "good brand name" routers. _All_ of them have been problematic in wireless mode. I have not altered the firmware.

I have no unusual appliances or other sources of interference in my home and I live in an ordinary suburban neighborhood with no industrial operations nearby, but there is a cell tower I can see out my window.

I have asked around among geek friends and tech-help folks at stores and manufacturers, but nobody has a clue what to look for, or even how to diagnose such a problem. I am wondering if the broader ubuntu/*nix community has any ideas?

Thanx!

---

### Post by ahallubuntu on 2012-12-31
Do you see the same problem on the 5GHZ band or only on 2.4GHZ?  All 802.11n devices have the single band 2.4GHZ radio but a "dual band" device also has a 5GHZ radio (or it may be switchable between 5GHZ and 2.4GHZ).

5GHZ should be subject to far less interference than 2.4GHZ, in general.  Since you already have a dual band router, if you have any devices that can do 5GHZ as well, I'd first check signal strength on that band.

Cell towers shouldn't operate near 2.4GHZ or 5GHZ.  They should operate in the 1.8GHZ range and down between 800MHZ-900MHZ.  At least, that's the bands most cell phones use.  Perhaps they are relaying signals at other frequencies.  I'm not an expert on this.

---

### Post by Hadaka on 2012-12-31
HI, is possible and by possible i mean maybe..might..could be, ya never know.
that you have a digital electric wifi enabled electric meter. and faulty grounding
or malfunctioning meter "might" be transmitting interferance. I can actually see
my meter sampling on some weird channel when i  monitor  a wlan program. Keep
in mind this is just a possibility and you may not even have that type of meter.
go outside and look....if it has a digital display and not the traditional "dial hand"
type dohickeys, it probably is a wifi type meter. again...this is just a shot in the dark
maybe, by your statements that this happens with different routers and both your
machines run just fine outside your home. do a search on chicago wifi electric meters
for more info.

---

### Post by chitowner2 on 2012-12-31
> **ahallubuntu said:**
> Do you see the same problem on the 5GHZ band or only on 2.4GHZ?  All 802.11n devices have the single band 2.4GHZ radio but a "dual band" device also has a 5GHZ radio (or it may be switchable between 5GHZ and 2.4GHZ).

5GHZ should be subject to far less interference than 2.4GHZ, in general.  Since you already have a dual band router, if you have any devices that can do 5GHZ as well, I'd first check signal strength on that band.

Cell towers shouldn't operate near 2.4GHZ or 5GHZ.  They should operate in the 1.8GHZ range and down between 800MHZ-900MHZ.  At least, that's the bands most cell phones use.  Perhaps they are relaying signals at other frequencies.  I'm not an expert on this.


I will see what I can do about selecting band options. I don't think our nooks have an option but the laptops might. Alternately, I am sure I can turn off one or the other band  in the router settings and that may give a clue. I'm thinking to switch off 2.4GHz and see what happens, then try the 5GHz.

---

### Post by chitowner2 on 2012-12-31
> **Hadaka said:**
> HI, is possible and by possible i mean maybe..might..could be, ya never know.
that you have a digital electric wifi enabled electric meter. and faulty grounding
or malfunctioning meter "might" be transmitting interferance. I can actually see
my meter sampling on some weird channel when i  monitor  a wlan program. Keep
in mind this is just a possibility and you may not even have that type of meter.
go outside and look....if it has a digital display and not the traditional "dial hand"
type dohickeys, it probably is a wifi type meter. again...this is just a shot in the dark
maybe, by your statements that this happens with different routers and both your
machines run just fine outside your home. do a search on chicago wifi electric meters
for more info.

The electrical wiring MAY be contributory. I do know that not all the electrical outlets here are "correct", but not sure why it would be a factor, since the one my PC and such are plugged in to seems right. I have checked this, but I will eyeball the meter since I never really looked at it.

---

### Post by ahallubuntu on 2012-12-31
> **chitowner2 said:**
> I will see what I can do about selecting band options. I don't think our nooks have an option but the laptops might. Alternately, I am sure I can turn off one or the other band  in the router settings and that may give a clue. I'm thinking to switch off 2.4GHz and see what happens, then try the 5GHz.

If your router is "simultaneous dual band," it has separate 2.4GHZ and 5GHZ radios - like having two routers almost.  I usually give them different SSID names, so the 2.4GHZ one might be "MyWirelessNetwork" and the 5GHZ one is "MyWirelessNetwork5" so I can tell them apart - and know immediately which devices can do 5GHZ if they can see the "5" network I've named that way.

Yes, I'd guess the nooks can do only 2.4GHZ as well.  Some laptop cards can do either one but many cheaper ones are 2.4GHZ only.

---

### Post by Hadaka on 2012-12-31
Hi, as Ahallubuntu pointed out,2.4 and 5 Ghz "radios", so even if both the computer
and the wireless (radio) router are plugged into an outlet with correct grounding, the
outlets with not correct grounding or reversal of the hot and common wires may be
 causing a problem when the meter wifi samples and transmits electrical usage. The
open copper ground lead pretty much becomes an antenna and can transmit signals
from any incorrect outlet. which is received by your computer equipment. I know this
first hand as back in the day, I used to transmit on SSB ham radio,all my neighbors
complained i was blanking out re-runs of gilligans island (this was before cable), 
finally i discovered the ground wire from the electrical box was disconneted from
the copper ground rod. Once repaired i no longer found burning bags of dog poo
on my porch and was re-invited back to the neighborhood  BBQ's ;) and finally
this is just a maybe for you.

---

