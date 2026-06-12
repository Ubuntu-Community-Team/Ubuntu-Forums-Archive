---
title: "kubuntu 10.10 does not recognise my wireless"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by jktjs on 2011-02-08
I have recently bought a Toshiba Portege R700-15Q and installed kubuntu 10.04. A similar problem happens with kubuntu 10.10 booted from USB stick. I am a long-time linux user but not experienced with fixing problems.

The wireless network is not enabled and it appears that linux does not know that there is a wireless capibility. This is both with and without an ethernet connection at boot. The wireless light on the computer is lit up, but when I go to Manage Connections the wireless and mobile broadband tabs are greyed out so can't be accessed. 

iwconfig gives "no wireless extensions" for lo, eth0 and pan0.

lspci returns "Network controller: Broadcom Cooperation BCM4313 802.11b/g LP-PHY (rev 01)"

lshw -C network returns "*-network UNCLAIMED", along with a block of other information which does not indicate a problem to me.

Any ideas/solutions would be gratefully received.

---

### Post by ryan andrews on 2011-02-09
so dude dont modify your internet settings 
i think lots of peoples have this problem unsolved 
if you modify something without knowing what you are doing i thing you will lose connection in gnome too

i am newbie but its my experience

---

### Post by jktjs on 2011-02-09
The problem occurs "out of the box" and with two kubuntu installations. As far as I know I have not modified any wireless or ethernet settings, simply reported some information. I'm therefore not sure why you wrote such comments.

As before, any help and suggestions will be gratefully received.

---

### Post by jktjs on 2011-02-21
I've worked this one out (finally): it is another case of needing a proprietary driver. Accessed via System -> Hardware drives. Problem solved.

---

