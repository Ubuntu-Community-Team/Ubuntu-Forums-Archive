---
title: "First Boot problem with Twinhan CI 1030, ok on 2nd?"
date: 2008-11-08
forum: Multimedia Software
---

### Post by ajpalm on 2008-11-08
Hi Guys,

Been using MythTV for a while and love it. But I've got a problem. I have a Twinhan VP1030-CI card and while it detects and works with myth for some strange reason it only works after the first warm reboot. From a cold start, the card fails to get a frontend setup under the /dev/dvb/adapater0, but a warm reboot and it does.

ie cold boot
frontend@htpc:/dev/dvb/adapter0$ ls
demux0  dvr0  net0
frontend@htpc:/dev/dvb/adapter0$

warm reboot
frontend@htpc:/dev/dvb/adapter0$ ls
ca0  demux0  dvr0  frontend0  net0
frontend@htpc:/dev/dvb/adapter0$

Using mythbuntu 8.10 and tried mythdora 4 & 5.

I've attached the dmesg logs. I hope someone who knows more than me can point me in the right direction to correct this.

Thanks in advance.

---

### Post by ajpalm on 2008-11-08
attachment failed, try again

---

### Post by Saiph on 2008-11-08
I had the same problem, i changed the eeprom, everything work right. After second restart my computer freeze. 
Solution: changed eeprom( something rewrote byte in eeprom again(restart to XP? (i dont know)). I rewrote byte back and its all righ again. :)
Problem solved Here: 
[http://ubuntuforums.org/showthread.php?p=6078962#post6078962](http://ubuntuforums.org/showthread.php?p=6078962#post6078962)

---

