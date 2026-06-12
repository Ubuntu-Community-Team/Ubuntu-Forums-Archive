---
title: "Cannot enable radio on my Intel Centrino Laptop"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by noneofthem on 2006-06-06
Hi there!

I have got a huge problem here. Everything in my system is working perfectly except the wireless network. After reading lots of threads and tutorials here I am still stuck without wireless LAN. I hope someone can help me.

I am using Kubuntu 6.06 LTS on my Intel Centrino 1.6 GHz laptop. When I check in KNetworkmanager the network card shows up and "sudo iwconfig eth1" also shows it as present, but the radio is off and I am unable to turn it on.

Anyone got any suggestions?

Thanks a million!

Amir

---

### Post by nikolokolus on 2006-06-06
this may sound trite, but have you tried to use your laptop's hotkeys to cycle the wireless card?  I don't know which laptop you have but most (all?) have some key combination to turn the wireless radio on/off and should work under Ubuntu (at least they do on my dell 700m, which uses a "centrino" setup).

---

### Post by noneofthem on 2006-06-06
Hey Man!

Thanks for your answer. Well. My laptop does not have such a button. I know the wireless network card is working properly as it did in XP and SUSE. But I cannot get it to work under Kubuntu for some strange reason. Not even the LiveCD seems to work.

Any more suggestions?

Thanks!

Amir

---

### Post by noneofthem on 2006-06-06
I am still hoping for an answer to my problem.

Any hints would be more than welcome...

Thanks

Amir

---

### Post by jml on 2006-06-06
This may also sound like a stupid suggestion, but even though the wireless card'slight is off, did you try to use it?  On my hp laptop, the wifi card's light only comes on during data transmission and reception.  Its off at other times.  In fact, I accidently turned the darn thing off once and it took me nearly a day to figure out what I did.  Here is a link to Ubuntu's troubleshooting guide.  Hope it will be of help.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Joe

---

### Post by noneofthem on 2006-06-07
Hey!

Thanks for that hint. But I already checked that as well. No idea what I can do now. I will keep checking other threads. Until then I hope to get the "great hint" from someone in here..

Thanks

Amir

---

### Post by menajemh on 2006-06-08
hi there. i'm new in linux. just installed ubuntu in my dell 6000 with same configurations as yours and i'm having exactly the same problem. the wifi does not work and func F2 does not turn it on. i went to the bios configuration and there shows that wifi is on by default. don't know what to do. now we are 2 and in future maybe more. i think has to be something with the drivers. or ubuntu burned my centrino pci during installation.:-k

---

### Post by menajemh on 2006-06-08
i found the solution. i started playing with the network configurations. go to the top left of the screen and double click the network icon. the name has to be eth1. then click configure and configure your wireless device and your ethernet. i stated playing there and deactivated the ethernet and activated it back with the wire plugged to the laptop and the router. finally, the ethernet has to be activated. check that the wireless configurations are in order. meaning, that u have the access point choosed correctly and the wep password if u have one. after that go back to the top left of the desktop and a new icon should be there. that is the wireless signal icon. under connection is green. no connection is white with an orange line on the bottom. double click and check that the name of connection is eth1. it should show u the signal strength on the bottom of that window. if does not try pressing the func key and F2 to turn on the wireless, even if u don't see the green light that shows the wifi is on, don't worry, it works anyways, just  there's no controler for the led. if u see signal but the internet does not connect try to restart the explorer or restart the computer. do not forget the make the tests unpluggin the wire, i forgot that detail. hope i was clear enought, my english is not good.

---

