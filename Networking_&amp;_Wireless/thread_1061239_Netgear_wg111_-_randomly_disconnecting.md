---
title: "Netgear wg111 - randomly disconnecting"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by antodena on 2009-02-05
Dear all, i've got Ubuntu8.10 installed on my machine and ALL is working very fine for me... it is updated at yesterday and someway it works flawlessy... exept that my internet wireless connection continues to fall down at an apparently random timing.

the only thing i can tell you is that ALWAYS when i try to update the list of programs in the SYNAPTIC package manager it stop to works at ALWAYS the same point...

obviously the connection stops even when i'm doing other things like navigation, email check and installation of packages from the web... but not always... at random...

in fact my installation of  UBUNTU is up to date... because in one way or another i've managed to update all.

when the connection stops, the internet wireless signal from the router seems ok (from the grafical interface) the only strange thing is that ubuntu continues to try to connect but it will not succed... it will continue to ask for the WEP key

if i unattach the dongle from the usb, i wait one minute, then i attach again the key, internet restarts until the next disconnession will happen... or until i start the update on the synaptic software...

can someone explain to me why it happens?

how to solve?

i'm totally new... anyway thanks.

regards.



antonio

---

### Post by Pylon757 on 2009-02-05
Same thing happening to me. I'm using dual-booting Intrepid with XP Home and using a Trendnet TEW-424UB USB adapter connected wirelessly to a D-Link DI-124. I'm using the W2KXP drivers loaded with Ndiswrapper 1.53. At random times the wireless gets disconnected, though the graphical interface would still say it has a signal. Hardware testing shows that I have no connection. Whenever I try to reconnect it apparently fails. Rebooting though restores the connection temporarily.

---

### Post by antodena on 2009-02-06
dear Pylon, yes the problem is very similar. I can tell you though that if i reboot the system the wireless will result totally absent. It's something like that ubuntu cannot find the usb dongle anymore... However if i will shut down, and then power up the system, ubuntu will reagin the wireless connection... but only until it will loose it again. I'm a total newbie in this world, but i can assume that the software that manage wireless connection, cannot regain the control of the dongle when the wireless disconnects.

the most strange thing is that anyway it happens randomly... but if i open the package manager and try to update it will stop at always the same time... (it shows 50 / 57 updates done on the window)

i hope that someone can at least help me understand why it happens, because this is the only last problem i have before i can migrate totally on the ubuntu s.o.

thanks! regards.

---

### Post by antodena on 2009-02-16
dear all!

my problem is solved with a simple trick!

it seems that the problem was caused by the fact that my UBUNTU is installed in ENGLISH language, but the server for the synaptic was set on ITALIAN servers...

i got this solution because i was seeing in "verbose mode" the update process that always stops at the same time... my quote: "but if i open the package manager and try to update it will stop at always the same time... (it shows 50 / 57 updates done on the window)"

it fails everytime on multiple files named "englishtranslation / something" sorry if i cannot remember, im not in front of the sistem now.

anyway, i've set the download from the english servers and all went OK!!! :lolflag:

i think that this problem can be tagged as solved! but i don't know how to!!!

thanks anyway.

regards!


dna

---

