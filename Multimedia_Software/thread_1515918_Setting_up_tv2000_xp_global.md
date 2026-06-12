---
title: "Setting up tv2000 xp global"
date: 2010-06-23
forum: Multimedia Software
---

### Post by nidzo732 on 2010-06-23
Im using ubuntu 10.04 and i have WinFast tv2000 xp global tv card.
I've tried 

# dmesg | grep bttv 
and 
sudo # modprobe bttv

but i can't make it work. I've heard that procedure is the same for any tv2000 xp (rm,deluxe etc.). Please help me. If i solve this and if i find a decent game for linux i could leave windows totaly.

Sorry for bad english, if any.

---

### Post by nidzo732 on 2010-11-06
Bump

---

### Post by JazzAcid on 2011-07-25
&#1053;&#1080;&#1119;&#1086;,
&#1084;&#1086;&#1075;&#1072;&#1086; &#1089;&#1080; &#1085;&#1077;&#1096;&#1090;&#1086; &#1076;&#1088;&#1091;&#1075;&#1086; &#1076;&#1072; &#1085;&#1072;&#1087;&#1080;&#1096;&#1077;&#1096; &#1095;&#1086;&#1074;&#1077;&#1082;&#1091;, &#1086;&#1089;&#1080;&#1084; &#1086;&#1074;&#1086;&#1075; bump. :-)

---

### Post by JazzAcid on 2011-07-25
I have just the same problem. I have no solution... Must admitt, so many problems with Linux, although I have very strong idealistic view against Microsoft monopoly! I dont have nerves for fixing it anymore, Win7 flows just quiet and fast.
Even 11.04 doesnt have answers for basic questins... it's a pity.

---

### Post by AlexVSharp on 2011-07-25
Same problem here. I've tried a couple of suggestions from other threads, namely the ones about TV2000xp cards in general (i.e. "Expert" series), yet I still can't get the "Global" to work. I'm still stuck with no access to video recording whatsoever. :(

---

### Post by nidzo732 on 2011-07-27
Solved, just install linux-firmware-nonfree

---

### Post by JazzAcid on 2011-07-28
> **nidzo732 said:**
> Solved, just install linux-firmware-nonfree


Stvarno nemam pojma kako si uspeo. Ja jednostavno nisam. A prizna&#263;emo, TV kartica je suviše zastupljena da bi OVAKAV problem postojao...

Pozdrav zemlja&#269;e !

---

### Post by nidzo732 on 2011-07-29
> **JazzAcid said:**
> Stvarno nemam pojma kako si uspeo. Ja jednostavno nisam. A prizna&#263;emo, TV kartica je suviše zastupljena da bi OVAKAV problem postojao...

Pozdrav zemlja&#269;e !

Pozdrav i tebi, jesi li u&#269;lanjen na srpski ubuntu forum, tamo su mi dali ovo rešenje.

[http://forum.ubuntu-rs.org](http://forum.ubuntu-rs.org)

---

### Post by Milos_SD on 2011-07-29
Of course it didn't work, when that card is not bttv, but cx88 :)

---

