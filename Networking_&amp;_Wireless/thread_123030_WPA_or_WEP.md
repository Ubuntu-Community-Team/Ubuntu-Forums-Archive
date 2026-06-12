---
title: "WPA or WEP??"
date: 2006-01-29
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-01-29
Hi, I'm having real hard time setting up my Cisco Aironet 350 wireless card with WPA, and I think it will work without problems using WEP. So is there a real differance in security between the two?? it's for personal/home use.

---

### Post by Gcool on 2006-01-29
If you have the possibility to choose, go for wpa. Wep is a wireless security, but that's about it. Anyone with the right knowledge and tools can crack it in no time.

Wpa on the other hand, is quite secure (or at least alot better then wep). If you want the exact specifications of both, just search google, and you'll find plenty of articles adressing this issue.

---

### Post by hw-tph on 2006-01-30
I say go for WPA. Configuration using wpasupplicant [isn't that hard](http://prinsig.se/weekee/index.php/Ubuntu#wpa_supplicant). 


Håkan

---

### Post by Jakanden on 2006-01-30
WPA is definitely the way to go. WEP is so unsecure it is not even funny.

---

### Post by ssalman on 2006-01-31
Okay, So WEP is not the way to go! but WPA_Supplicant does not support my card (Aironet350) although the airo.o driver itself is included in the kernel.

I'm wondering is there anybody out there using WEP because he/she was forced to and couldn't get WPA running on thier hardware?

or is there alternative ways I'm not aware of? :confused:

---

### Post by rmduk on 2006-02-02
While WPA is no doubt more secure, don't rule out WEP as a perfectly adaquate solution for a home network.  As long as you use it in conjunction with MAC address filtering then WEP provides more than enough protection for most home users (IMHO).  The MAC address filtering will stop unwanted people using your WiFi network and WEP will stop people reading your WiFi data.  While yes someone could come along with a sniffer and put a lot of effort into breaking in,  the risk of this is low.  Having WEP is like having a good lock on your front door, having WPA is like having a guard dog and a security firm as well.   Both have there places, and uses.

---

### Post by jml on 2006-02-02
I agree that WPA is more secure than WEP.  But the combination of WEP plus MAC address filtering is pretty good as well.  It is possible to spoof a MAC address and hack into a system, but its a lot more difficult.

The bigger issue is your card.  I have an Aironet 350 card as well.  It well built, has a powerful transmitter and is very Linux compatible.  Unfortunately it only supports the 802.11b protocol and in all likely hood does not support WPA at the firmware level.  I have been able to get it to work with Ububtu on unencrypted networks.  I don't have access to a WEP encrypted network to test, but it should work there.  I have never been able to get WPA encrypted wireless working on any of my wireless cards.  Others have, but when I've tried to follow their instructions, I've never been successful.

You might have to consider getting a different card.

Joe

---

### Post by Jakanden on 2006-02-04
[QUOTE=rmduk]While WPA is no doubt more secure, don't rule out WEP as a perfectly adaquate solution for a home network.  As long as you use it in conjunction with MAC address filtering then WEP provides more than enough protection for most home users (IMHO).  The MAC address filtering will stop unwanted people using your WiFi network and WEP will stop people reading your WiFi data.  While yes someone could come along with a sniffer and put a lot of effort into breaking in,  the risk of this is low.  Having WEP is like having a good lock on your front door, having WPA is like having a guard dog and a security firm as well.   Both have there places, and uses.[/QUOTE]

I suggest taking a listen to this podcast about WEP and it might make you re-think WEP as viable. MAC Filtering is not secure at all =)

[http://media.grc.com/sn/SN-011.mp3](http://media.grc.com/sn/SN-011.mp3)

Additioanlly you can read the Log here: [http://www.grc.com/sn/SN-011.htm](http://www.grc.com/sn/SN-011.htm)

---

### Post by ssalman on 2006-02-06
[quote=jml]I don't have access to a WEP encrypted network to test, but it should work there.  I have never been able to get WPA encrypted wireless working on any of my wireless cards.  Others have, but when I've tried to follow their instructions, I've never been successful.[/quote] 
I have a newer Centrino laptop, and I was able to use WPA on SUSE and Ubuntu with little problems. As for the older laptop (with Aironet 350) I can only use unsecured connections, niether WEP nor WPA worked for me. I still think WEP can be done, it's just a matter of me not finding how to do it correctly for this card!!

I've been trying to get information on the card and it looks like with the latest firmware update and driver it can support WPA. But I could not test this.

I think it may be time to buy a newer wifi card!! :-k

---

