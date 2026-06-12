---
title: "repair wireless command"
date: 2006-03-18
forum: Networking &amp; Wireless
---

### Post by sn123 on 2006-03-18
Disclaimer: I am newbie who just made a switch from Windows to Ubuntu so please go easy with responses :)

Problem: I am connected to a pretty flimsy wireless router at home which generally disconnects me twice or thrice in a day, in Win Xp I could right click on the Wireless Connection and choose "Repair" which would get me connected back again. I've been trying to find an equivalent of such a command in Ubuntu without any luck, so the only way to reconnect to internet in Ubuntu is to restart my system :(. Is there any equivalent to the "Repair Wirless" funcy in Ubuntu?

TIA,
S

---

### Post by Zelut on 2006-03-18
Sure there is! :)  You'll find, before long, that after you've past the initial learning curve that things are just simpler in most cases in Linux.

There are two ways I can think of offhand to repair your wireless connection.  First from the command line and second from the GUI.

To repair it from the command line open a terminal.  (Applications > Accessories > Terminal).  Once in the terminal type "sudo dhclient".

From the GUI you'll want to open System > Admin > Networking.  In here you can open properties on the wireless card (just to make sure everything is still set), click OK & OK and it should reconnect you.

Let me know how those work.

---

### Post by sn123 on 2006-03-18
[QUOTE=kuyaedz]Sure there is! :)  You'll find, before long, that after you've past the initial learning curve that things are just simpler in most cases in Linux.

There are two ways I can think of offhand to repair your wireless connection.  First from the command line and second from the GUI.

To repair it from the command line open a terminal.  (Applications > Accessories > Terminal).  Once in the terminal type "sudo dhclient".

From the GUI you'll want to open System > Admin > Networking.  In here you can open properties on the wireless card (just to make sure everything is still set), click OK & OK and it should reconnect you.

Let me know how those work.[/QUOTE]
Thank you! to test them out I'll have to wait till my router disconnects me again ;). I prefer the command line one though imo cause that makes you learn more rather than going through the GUI.

Thanks again,
S

---

