---
title: "Marvell chipset WG311v3"
date: 2006-05-12
forum: Networking &amp; Wireless
---

### Post by deadlycow21 on 2006-05-12
Hello all,

I have a WG311v3 that didn't even work to well while in windows... (xD)
I attempted to use both ndiswrapper and ndisgtk with this... ndisgtk was very nice, I liked the GUI which is good for a newb who only knows how to use the fortune command in the terminal :mrgreen: . Anyways... when i install the driver with ndisgtk the card will show up in the "Networking" but, after configuring (putting in WEP key and selecting DCHP) and activating everything goes berzerk [-( . I press a key and it will execute that command a bunch of times (alt-f4 is dangerous to say the least) randomly... when i restart the computer it won't start up (frozen at configuring network interfaces). But, if before shutting down the computer i disable the WiFi card and enable my direct connection it starts up fine. When I boot in recovery mode, i see the problem. It says that i can't find SSID or something and keeps repeating the same error over and over again with a different random number in the [098098.89089] part....

What should i do... any other drivers/utils that i should try :confused: 


-jacob

btw, this happens with NDISwrapper too ](*,)

---

### Post by deadlycow21 on 2006-05-15
[QUOTE=deadlycow21]Hello all,

I have a WG311v3 that didn't even work to well while in windows... (xD)
I attempted to use both ndiswrapper and ndisgtk with this... ndisgtk was very nice, I liked the GUI which is good for a newb who only knows how to use the fortune command in the terminal :mrgreen: . Anyways... when i install the driver with ndisgtk the card will show up in the "Networking" but, after configuring (putting in WEP key and selecting DCHP) and activating everything goes berzerk [-( . I press a key and it will execute that command a bunch of times (alt-f4 is dangerous to say the least) randomly... when i restart the computer it won't start up (frozen at configuring network interfaces). But, if before shutting down the computer i disable the WiFi card and enable my direct connection it starts up fine. When I boot in recovery mode, i see the problem. It says that i can't find SSID or something and keeps repeating the same error over and over again with a different random number in the [098098.89089] part....

What should i do... any other drivers/utils that i should try :confused: 


-jacob

btw, this happens with NDISwrapper too ](*,)[/QUOTE]


just upgraded to dappler... this does not appear to help.......

---

### Post by deadlycow21 on 2006-05-16
[QUOTE=deadlycow21]just upgraded to dappler... this does not appear to help.......[/QUOTE]

ok, dappler does not appear to freeze up the computer the way it did in breezy, it will eventually skip the "network interfaces" start up part :mrgreen: and it will not do the weird typing thing... but, it will not allow me to access the internet... any help? i need to get this server set up

---

### Post by jimbo7 on 2006-08-10
Hi guys. Check out my mini wiki on how to install the WG311v3 Driver on Debian, i hope it can be helpful. And feel free to contribute to make it better!

[WG311v3 WIKI]("http://www.jimbo7.com/wiki/index.php?title=WG311v3")

---

