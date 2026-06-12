---
title: "Wireless card won't transmit"
date: 2006-04-01
forum: Networking &amp; Wireless
---

### Post by travelerjjm on 2006-04-01
I have an Atheros AR5212 card in my laptop. It is miniPCI. The card is recognized. It finds the AP and gets the right ESSID. I can put the card in Monitor mode (promiscuous mode) and snarf packets.  No problem. What I cannot seem to do is send any packets.

The output of iwconfig shows a link quality of 0/94 -- not too good...

The laptop's led is red. I think it should be blue if wifi is working correctly. The led is blue when I start the boot process, then it goes red. The dmesg output looks reasonable, no HAL errors. 

In device manager net.interface_up is false; does not sound right either. 

The problems seem to exist whether or not I try to use WEP. Maybe I need to set WEP on or off. I tried setting the mode to 3 which I read somewhere set the card to WEP mode, but no help. (My ap is a Netgear with only WEP).

Any ideas?

Thanks,
--john

---

### Post by travelerjjm on 2006-04-09
OK. I fixed it. I had to do two things:
1) tell the HAL to turn the card on by setting net.interface_up to true.
2) turn off eth0. It is strange but if when I did "ifconfig eth0 down" the wireless card started to work flawlessly. I know that seems strange, but it worked.

---

### Post by jml on 2006-04-09
Not strange, just poorly documented.  I find that many Linux based distros have trouble getting wireless to work if eth0 is still activated.  Even if it is not connected, the active interface seems to interfere with the wireless connection.  In my laptop, I have had to create several different profiles to accomodate the various connection options (wired, encrypted wireless, unencrypted wireless.)  In my case I had to switch from Ubuntu to Mandriva 2006 for WPA connectivity since despite all of the great suggestions on this forum, I was not able to get it to work in Ubuntu.

Joe

---

