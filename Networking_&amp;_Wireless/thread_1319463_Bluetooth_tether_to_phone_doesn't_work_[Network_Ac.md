---
title: "Bluetooth tether to phone doesn't work [Network Access Point]"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by farbird on 2009-11-08
[SOLVED]Upgraded to 9.10 for 24 hrs already.

Tried tethering via bluetooth to my android phone... [ which worked in 9.04 ]...

using blueman allowed me to connect to the phone as a network access point..

however, it doesn't get listed as a connection in networkmanager in gnome..

and ifconfig will show that a new connection "bnep0" is present but it doesnt get a DHCP assigned IP..

Only after I type "sudo ifup bnep0", it does get a DHCP assigned IP and the interet tethering worked but still no connection shows up in the gnome network manager...

Anyone encountering same issue?

---

### Post by farbird on 2009-11-08
upping thread for help..

I tried adding

iface bnep0 inet dhcp
auto bnep0

into 
/etc/network/interfaces

but that didnt help too.

---

### Post by walmis on 2009-11-09
Which version of blueman do you have?

---

### Post by farbird on 2009-11-09
Problem solved..

I updated my repositories to include the blueman ppa and used the blueman there..

Now connecting to the NAP works.... ie bnep0 gets an ip and is shown correctly in the gnome networkmanager applet..

Why didnt they just include it in karmic default?

---

### Post by nathaner on 2009-12-02
I got this to work without having to touch the terminal in Karmic.  I deleted my phone (WinMo 6.1) from the approved devices in the bluetooth manager and before re-pairing them, I turned on internet connection sharing from the phone.

Then, from the laptop search for the phone and once you input the pin, the bluetooth manager will detect the network connection and prompt to use DHCP.  After you accept all of those settings it works like a charm and shows up in the network manager.

The only critical difference really, is having the network sharing running BEFORE you pair the 2 devices.

---

