---
title: "Old Clamshell black screen"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by bigred3373 on 2007-04-23
I have installed edgy on my laptop clamshell indigo 366 mhz 10gb 350 mb when edgy loads i get the ding to tell me i am at the desktop but montior stays black  any body have this problem its s a tough notebook and runs well considering its 800x600 screen . It is an ATI, RageM3 vram 8mb ATI (0x1002) 32 bit color thanks

---

### Post by bapoumba on 2007-04-23
What ubuntu version did you install ? If GNOME (ie ubuntu), you may have more luck with xfce (xubuntu) which is much lighter.
[http://psychocats.net/ubuntu/xubuntu]("http://psychocats.net/ubuntu/xubuntu")

---

### Post by bigred3373 on 2007-04-23
> **bapoumba said:**
> What ubuntu version did you install ? If GNOME (ie ubuntu), you may have more luck with xfce (xubuntu) which is much lighter.
[http://psychocats.net/ubuntu/xubuntu]("http://psychocats.net/ubuntu/xubuntu")

Going with Dapper i mad e the mistake of putting edgy in sorry

---

### Post by bapoumba on 2007-04-23
> **bigred3373 said:**
> Going with Dapper i mad e the mistake of putting edgy in sorry
Still, these different ubuntu flavors exist with dapper ;)
I have an old computer which runs fine with xfce.
Check the bottom of the link, there are even lighter distributions.

---

### Post by bigred3373 on 2007-04-23
okay will give it a go thanks :):KS 8) ](*,) :mrgreen:
I have to install dapper agian then i can install xfce but i cant see nothing will be hard to do with montior specs not right

---

### Post by bapoumba on 2007-04-23
> **bigred3373 said:**
> okay will give it a go thanks :):KS 8) ](*,) :mrgreen:
I have to install dapper agian then i can install xfce but i cant see nothing will be hard to do with montior specs not right
well, just install xubuntu-desktop.

---

### Post by bigred3373 on 2007-04-23
i still need the settings for monitor would yo uknow these i cant install nothing until i have a screen  anyone?

---

### Post by Neecapp on 2007-04-23
Does the screen work at all?

If so, the v-sync and horiz-sync are off in xorg.conf.

If the monitor doesn't work at all... it is probably just unplugged within the laptop.. usually right below the screen.. or under the keyboard where it plugs into the mobo.

---

### Post by bigred3373 on 2007-05-11
yes the montior works and yes i know the vert and refresh is out i need to set them HOW? at what numbers

---

### Post by bapoumba on 2007-05-12
have you tried 
```
sudo dpkg-reconfigure xserver-xorg
```

---

