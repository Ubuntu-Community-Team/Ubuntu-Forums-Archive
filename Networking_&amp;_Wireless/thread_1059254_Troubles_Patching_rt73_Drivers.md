---
title: "Troubles Patching rt73 Drivers"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by Carlosmarioagamez on 2009-02-03
[I]Hi all :), i will try too be extremely especific :P
Well, first than all i am using Ubuntu 8.10, my PC is a desktop PC, i bought a wireless card recently (DWA 110 - D-Link - USB), this works perfect using rt73 drivers, those drivers has being installed on /usr/src folder

I am trying to use Aircrack-ng, Airodump-ng, etc, so, i know already that i need switch the device to Monitor mode, reading this [guide]("http://ubuntuforums.org/showthread.php?t=528276") i found [_this site_]("http://www.aircrack-ng.org/doku.php?id=install_drivers"), there is showed a list with supported drivers and how to patch it, i choose [_rt73 guide_]("http://www.aircrack-ng.org/doku.php?id=rt73") cause my card chipset work with it

I follow all the instructions and there is not problem, i reach the point where i need make, make install and modprobe rt73, thats ok till there, the problem is when i try to use aircrack-ng, i put this command line on the terminal and i got this

iwconfig rausb0 mode monitor[/I]

[IMG]http://i40.tinypic.com/wbw9zr.jpg[/IMG]

*So, i assume the drivers was not patched; when i install it, this was downloaded and uncompressed also installed on my home (just for be clear); after restart my machine  got the surprise that my network manager was not working because no wifi was detected, i use wicd, not ubuntu network-manager, so, i check the ifconfig and this was what i got*

[IMG]http://i43.tinypic.com/242g08g.jpg[/IMG]

*So, i have deleted the installation folder and reinstalled the original rt73 drivers and now this work, but i am still unable to use airmon-ng cause this is what i got when i tried to use this*

[IMG]http://i44.tinypic.com/5ydj53.jpg[/IMG]

[I]Somebody can help me with this ?
Thanks in advanced[/I]

---

### Post by cmavr8 on 2009-02-14
You may need to use both drivers.
Original drivers for normal networking, secondary drivers for cracking.

Re-install the secondary drivers, do ifconfig and find out what name your card has with the new drivers.

Then use that name in "iwconfig xxxx mode monitor"

---

### Post by Carlosmarioagamez on 2009-02-14
[I]Thanks for you help dude, but seems like i dont need to patch rt73 drivers for use DWA 110 on monitor mode, i can use this two commands to get this working in the way that i need:

iwconfig wlan0 monitor mode (enable mode monitor)
airmon-ng start wlan0 (enable mode monitor)

After that i am able to use aircrack entire suite \\:D/[/I]

---

