---
title: "Wireless speeds are really slow with rt2800usb driver"
date: 2013-05-30
forum: Networking &amp; Wireless
---

### Post by josh4789 on 2013-05-30
I used to get decent speeds on windows but now i get speeds that less thatn the 5-6MB downloads i used to get i normally get 300KB maybe up to 1MB every once in a while and the speeds arent consistant at all. Is there any way to fix this problem because i know i used to have faster speeds.

---

### Post by Hadaka on 2013-05-30
Hi, give this a try..
```
sudo modprobe -rfv rt2800usb

sudo modprobe rt2800usb nohwcrypt=1
```
dont boot
see if that helps your speed, 
report back if it helps and we will write it in,
thanks.

---

### Post by josh4789 on 2013-05-30
Okay so it double my speeds with speedtest.net but its still not as fast as it used to be my tests used to give me aywhere between 30 and 40 Megabits now it only gives me about 6 Megabits. its still an improvement over my last speeds though.

---

### Post by Hadaka on 2013-05-30
ok, well thats an improvement...
please do..
```
sudo gedit /etc/modprobe.d/rt2800usb.conf
```
add this one line..
```
options rt2800usb nohwcrypt=1
```
proof read...save and close gedit.
then...edit your wifi connection to and make it look like attached. below
your connection name will of course be different.
[ATTACH=CONFIG]243315[/ATTACH][ATTACH=CONFIG]243316[/ATTACH]
this will further help your speed
after these changes....boot and check your speed
thanks.

---

### Post by josh4789 on 2013-05-30
That actually didnt help with my speed at all its still 6 Megabits. but now when i restarted it was at 6 and not 3

---

### Post by Hadaka on 2013-05-31
ok, slight improvement, not huge but better,
Is there a reason you are using a usb wifi
and not the internal card? and have you recently upgraded
from one os to another ..as in 12.10 to 13.04? and lastly
how old is your computer and how much ram do you have?

---

### Post by josh4789 on 2013-05-31
My dad doesnt like buying computer parts and the computer itself is about 5 years old it has a intel motherboard with a 2.3GHz quad core
i have 4GB ddr2 ram and im using the USB because my old wifi card fried after 7 years of use because it wasnt really compatible with the case so it bent a little which messed it up over time.
EDIT: and no i havent recently upgraded i've used 12.04LTS on my laptop for a long time but i just recently put linux on this computer so i decided to go for the latest ubuntu. I thought i had a spare wireless card because its drivers werent good with windows but i cant find it so im stuck with the usb.

---

### Post by josh4789 on 2013-06-02
Anybody know a way to get this to go faster? This is really bothering me it takes forever to download my games on Steam.

---

