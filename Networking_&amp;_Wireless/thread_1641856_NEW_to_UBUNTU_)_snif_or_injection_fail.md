---
title: "NEW to UBUNTU :) snif or injection fail?"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by water88 on 2010-12-09
hello,
im new to ubuntu :)
had to develop a simple program for a friend, so i got the ideia to try programming it in unix...used all those functions and lib's i needed with simple commands... very nice, C is not my strong point but... 

ok so, and here i am now... stuck to ubuntu :D
i have the latest 10.10 ubuntu, i was digging around to see what am i getting into.
if linux was supported by most software companies this would be the best OS in the world :P
i mean... what if i need a fireworks, flash, or a film editing software, or "that" game i use to play when my boss is away... :P
well (in some cases) i can find similar softwares, but... its not the same.

anyway back to the point of this thread.
i use to hear a lot about security tools developed for linux, and i was wondering how safe i am on the wireless network i use at home.
what if a psycho can associate with my router and do a mitm attack? :/
i lost MSN hotmail password once... i dont believe it was from a local network attack but anyway...


/\/\/\/\/\/\/\/\/\

about me
__________________________________

problem

\/\/\/\/\/\/\/\/\/


so i wanted to test my wep encryption on my router.
well i came up with this aircrack software.
so i just pluged my TP-link TL-wn722n, and it worked right out of the box.
installed aicrack...
created pseudo monitor interface with airmon.
got airodump getting all the packets from my network (needed to change a -1 return on aicrack-ng pkg).
tested injection... everything is fine...
authenticated sucessfull (!)
and well... tried to get those arp requests with aireplay.
get a ping request (where is...?)
and bang... my wireless card start to inject packets at 500 pps...
airodump getting all the packets...

went to a coffee..

2 hours later, got lots of packets, but 
only 200 arp's, and 100 ACK's.
aircrack didnt had enough iv's to crack.

why is this happening??
any firmware updates that is making wep safer?
i mean... im confused? :s

thanks for your time
see you ;)

---

### Post by water88 on 2010-12-09
well i believe im making sense? :-o

---

### Post by azwar on 2010-12-09
> **water88 said:**
> well i believe im making sense? :-o

To be honest, WEP key is easily get cracked. If your router support WPA2/PSK key then use it.

As far as I'm concern/experience, WPA2/PSK although it's possible to crack with WPA handshake + Dictionary Attack. The chance of it being decrypt almost impossible.

---

### Post by water88 on 2010-12-10
> **water88 said:**
> well i believe im making sense? :-o


well... wpa is still not supported on all mobile devices.

:popcorn:




anyone experienced this problem before?
injection is being done, but only few ARP replies?

;)

---

### Post by azwar on 2010-12-10
> Well... wpa is still not supported on all mobile devices.

Which one you are referring to mobile device in your first post? I only see TL-WN722N (Wireless High Gain USB Adapter)

---

### Post by water88 on 2010-12-10
> **azwar said:**
> Which one you are referring to mobile device in your first post? I only see TL-WN722N (Wireless High Gain USB Adapter)


well... TL-WN722N is my usb wireless adapter...
mobile devices i meant mobile phones...

i believe we should focus on the topic? :wink:

i was testing wep... and got to this problem.
i would be grateful if someone could help me in this matter.

i was wondering if it was a common problem or not,
or if someone have a solution, or could explain to me why is it happening.
that's why i created this topic.


:popcorn:

---

