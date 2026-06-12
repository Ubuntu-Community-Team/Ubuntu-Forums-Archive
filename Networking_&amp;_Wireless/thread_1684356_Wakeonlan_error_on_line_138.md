---
title: "Wakeonlan error on line 138"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by Linuxson25 on 2011-02-09
Hi

Have a network of 21 Edubuntu pcs, and I teach ICT on them. Using iTalc to communicate with them, but I am having some trouble with the "Start UP" and "Log In" features of this software package. Wakeonlan has been enabled in ALL the computers' BIOS, and I can remotely wake them up with etherwake, but that is only one at a time. So I switched to Wakeonlan...but when I tried using the example given with this package, it gives me an error that reads:

"No such file or directory at /usr/bin/wakeonlan line 138"

I opened up this file in gedit, and had a look at the line in question
It read the following: [http://pastebin.com/FXcmQBTs](http://pastebin.com/FXcmQBTs)

On line 5 of Pastebin is the line in question. Now I changed the attribute/name "filename" to lab001, thinking that this would direct it to that file. I also changed line 2 in this respect...but still no luck. Please, if anyone could help me??? My classes have started already, and it's really annoying having to walk from pc to pc just to switch them on before the lesson


Thanx

---

