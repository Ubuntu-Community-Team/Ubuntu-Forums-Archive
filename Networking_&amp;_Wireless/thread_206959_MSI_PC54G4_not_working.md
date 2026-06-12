---
title: "MSI PC54G4 not working"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by wpshope on 2006-06-30
Hi all. 

I've installed an MSI PC54G4 wlan card on my machine. Can't get it to work. I've checked the forums and it tells me that rt2500 is installed in ubuntu already and should show the ra0 interface. Thing is, ra0 is not showing up on my system at all. I' ve already tried downloading and compiling rt2500 source code. Still doesn't doesn't work.

Any ideas?

Thanks :)

---

### Post by skaramanger on 2006-07-04
HI wpshope,

I've got a MSI54G installed and working ok (wep only).  Need some specs on your system, any messages? run sudo make, sudo make install?  Breezy 5.10 running 2.6.12-10-k7


[QUOTE=wpshope]Hi all. 

I've installed an MSI PC54G4 wlan card on my machine. Can't get it to work. I've checked the forums and it tells me that rt2500 is installed in ubuntu already and should show the ra0 interface. Thing is, ra0 is not showing up on my system at all. I' ve already tried downloading and compiling rt2500 source code. Still doesn't doesn't work.

Any ideas?

Thanks :)[/QUOTE]

---

### Post by wpshope on 2006-07-05
Hi skaramanger,

That sounds great! Which driver are you using? I've got the one from the ralink website which I got from the ndiswrapper list for the pciid 1814:0301.

So far when running sudo make and sudo make install rt2500-1.1.0-b4 no errors come up. Everything seems to be fine. The thing is when running iwconfig I only get:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

and nothing for wifi on the networking window in gnome.

I obviously am doing something wrong or perhaps missing a step.  My unit has: Gigabyte i-DNA GA-k8n51gmf-9 - motherboard
2.6.12-10-k7 - kernel
Breezy Badger

What do you think?

Thanks for the reply :smile:

---

