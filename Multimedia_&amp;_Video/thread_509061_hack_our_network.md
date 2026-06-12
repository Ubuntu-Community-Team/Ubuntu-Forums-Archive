---
title: "hack our network"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by supremedialect on 2007-07-25
hi. im pretty much new to this whole Linux world. using Ubuntu now migrated from fedora. and i have a very dumb question.

i live in a art studio building that provides free internet. its just a line that runs to my room. my ip address is  209.253.x.x its funny i can ping it from anywhere you might be able to also
well on to the question what kind of network is this i can see some other computers on the network some of them have samba shares, i dont think we are behind any router im really confused i get my ip via dhcp. 

and another question i notice that in the building the network cables are in visible sight on the ceiling since it is a old historical building i guess thats the only option so i follow these cables which end up behind  a closed door. and i look up and notice cameras all connected to the network cables

1 is there a way i can ping these thing or identify them with ubuntu?
2 is there a way i can see what they see i've visited johnny i have stuff website  but no luck using google.
any one understand what im trying to say or do?

---

### Post by zanglang on 2007-07-25
Are you sure you really want do that? Invasion of privacy is no small thing you know. ;)

To check if you're on a LAN, right-click on your Network Manager applet (you use Feisty, right?) and select 'Connection Info'. Note the IP listed there. Now go to [http://whatismyip.com](http://whatismyip.com) and check if it's the same. If it is not, 209.253.x.x is your WAN (internet) IP, not your computer's private IP.

For 2, I'll put this bluntly... take a look at Ethereal/Wireshark. The rest is up to you. :)

---

### Post by supremedialect on 2007-07-25
thank you, i think i'm on a WAN 209.253.x.x comes up for both.
 i have tried ethereal but very confused the only data i really get is someones windows machine on this network scanning ip's im guessing its a virus
but yeah any more helpful info would be great

---

### Post by lisati on 2007-07-25
> **zanglang said:**
> Are you sure you really want do that? Invasion of privacy is no small thing you know. ;)

To check if you're on a LAN, right-click on your Network Manager applet (you use Feisty, right?) and select 'Connection Info'. Note the IP listed there. Now go to [http://whatismyip.com](http://whatismyip.com) and check if it's the same. If it is not, 209.253.x.x is your WAN (internet) IP, not your computer's private IP.

For 2, I'll put this bluntly... take a look at Ethereal/Wireshark. The rest is up to you. :)

Aahhh knowledgable people can find out what kind of ADSL router I have!

---

### Post by supremedialect on 2007-07-25
yeah but as far as invasion of privacy its not really invading anyones privacy the cameras are in the hallways where it is public, there are cameras in any rooms only in the hall and the entrance

---

### Post by supremedialect on 2007-07-25
is there any programs like angry ip scan that i can install from the add/remove software menu?

---

