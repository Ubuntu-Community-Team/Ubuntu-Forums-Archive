---
title: "moving from dhcp to static ip, advice please"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by surfmonkee on 2011-07-19
home network =

ps3 lan, psp wan, xp desktop lan, netbook W7 wan, fujitsu laptop ubuntu wan for surfing but often lan for large files, android 2.1 phone wan, mac sawtooth G3 (rarley) lan. near future, tablet wan, crappy ancient laptop xp lan rarely.

next week i am having 6TB DS211j NAS (omg cant wait)

I think, from what i have been reading, that moving to a static ip for each device will be better suited.

I manage the belkin router from the ubuntu latop and wondered what the best way to proceed is, which first, what order etc etc.

I can understand what needs to be done, i have the primary dns and ip numbers and mac address for every device ( the network is mac filtered)

so how would you begin...... a peice of paper and some drawings i have ready to plan it out......

the reason i choose to change from dhcp to static is because of the arrival of the DS112j.  from my understanding this device would benefit from never having its ip changed on the network.  There have been times when the ip has changed on some of the devices in the past when the belkin has suffered a power failure or reset.

:guitar:

---

### Post by jmoorse on 2011-07-19
You don't need to put everything on static IPs, only the NAS.

Just make sure you assign it an IP outside of your range of DHCP addresses.

---

### Post by surfmonkee on 2011-07-19
my router does not support static ip AND dhcp together, it is either or

and as i said, there have been occasions when the ip address has changed, even tho the lease time is set to 'forever'

 this is a disaster for the ps3 on DMZ and the machine running utorrent which has ports open for a specific ip number.... 


i need static ip across my network for sure.but where to start?

---

### Post by jmoorse on 2011-07-19
You don't set static on the router, only on the NAS.  Don't change anything on the router.

If a device is set for DHCP it will broadcast for an IP, in which case the DHCP server on the router will respond.  If a device has a static IP it will not broadcast for an IP.  Make sense?

---

### Post by jmoorse on 2011-07-19
> **surfmonkee said:**
> my router does not support static ip AND dhcp together, it is either or

and as i said, there have been occasions when the ip address has changed, even tho the lease time is set to 'forever'

 this is a disaster for the ps3 on DMZ and the machine running utorrent which has ports open for a specific ip number.... 


i need static ip across my network for sure.but where to start?

Ok, in that case feel free to assign static IPs all around.  I didn't want to imply there is anything wrong with statics.  There is just more work involved :)  

You can also check to see if your router supports DHCP reservations.  Those are pretty sweet.

Yes, I always begin my network designs with pen and paper.  In your case this will help so that you have an IP <> Device reference and don't create duplicate IPs (yes, I have done that more than once before)

---

### Post by surfmonkee on 2011-07-19
> **surfmonkee said:**
> 

and as i said, there have been occasions when the ip address has changed, even tho the lease time is set to 'forever' this is a disaster for the ps3 on DMZ and the machine running utorrent which has ports open for a specific ip number.... 




see above :popcorn:


**I WANT** to change to static ip ok, and seek advice on the best way to go about it with so many devices, thanks for your input but its not what i wanted, have a nice day

i have found this now, so i shall go and read....

[www.homenethelp.com/web/howto/static-ip-address.asp](www.homenethelp.com/web/howto/static-ip-address.asp)

---

