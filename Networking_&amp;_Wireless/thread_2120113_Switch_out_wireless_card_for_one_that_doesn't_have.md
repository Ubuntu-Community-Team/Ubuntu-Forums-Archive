---
title: "Switch out wireless card for one that doesn't have hardware problems?"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by superchar42 on 2013-02-25
I've got a Dell Inspiron 9300, but I'm not sure if it'll take a new internal wireless card without having stupid hardware breakage. 

I'm getting really frustrated with my wireless connection being dropped all the time and I'm ready to just buy a new internal wireless card. 

Any suggestions? How do I find one that plugs in right? with the same two clip on wire things?

---

### Post by ahallubuntu on 2013-02-25
~

---

### Post by superchar42 on 2013-02-25
oops, I'll edit that, I don't know why I thought it was the 2200 series, anyways lspci -v gives this 
```

 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)


```

I looked at the guide and was thinking about getting something from thinkpenguin - I've never done upgrades like this on a laptop before so I'm totally out of my element.

---

### Post by J_we on 2013-02-27
> **superchar42 said:**
> oops, I'll edit that, I don't know why I thought it was the 2200 series, anyways lspci -v gives this 
```

 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)


```I looked at the guide and was thinking about getting something from thinkpenguin - I've never done upgrades like this on a laptop before so I'm totally out of my element.

Dell is a PITA. The company has started locking down the mini pcie slot so the wifi card from ThinkPenguin may or may not work. If it is an older Dell there is a much higher chance of success. 

The RTL8187 series USB wireless chipsets are the best. They'll work with anything and everything out there. A lot of other USB chipsets won't. You can get this stuff from ThinkPenguin's site too. They have a sizeable selection of hardware. It is the USB G adapter that uses this chipset. There are some other options too like AR9170 (not great) and the AR9271 (not yet, but soon).

---

### Post by pdengale on 2013-02-27
Have you tried disabling Wireless 802.11n?
There is a bug with N and some wifi cards.


It works on my laptop.
If I run on my wifi using N, I get 10mb/s max on the speedtests and disconnects. When N is disabled and I run G, I get 25mb/s and a stable connection.
It's a Sony VAIO S with an Intel® WiFi Link 1000. It's 2 years old.

Best regards
Nikolaj

---

