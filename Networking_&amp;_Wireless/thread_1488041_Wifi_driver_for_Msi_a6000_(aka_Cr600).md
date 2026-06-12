---
title: "Wifi driver for Msi a6000 (aka Cr600)?"
date: 2010-05-19
forum: Networking &amp; Wireless
---

### Post by TheSpecialEd on 2010-05-19
Hi ya'll, 
um, I havent used linux for sometime now, so im kinda a noob.
But, i decided to try Ubuntu 10.04 and im having a problem. My wireless adapter isnt being recognized, its a Ralink Rt3090, and i have no idea how to install the driver, i tried to use: [http://launchpad.net/~markus-tisoft/+archive/rt3090]("http://launchpad.net/~markus-tisoft/+archive/rt3090") (both the Karmic and Jaunty) but it keeps giving an error message. Any ideas on what to do? 

Ty in advance (:

---

### Post by gordintoronto on 2010-05-19
Here's what to do: tell us what the error message was!

Here's a thread which might help:
[http://ubuntuforums.org/showthread.php?t=1313132](http://ubuntuforums.org/showthread.php?t=1313132)

Google is your friend...

---

### Post by TheSpecialEd on 2010-05-19
Ooh, sorry about that, im usually smart enough to do that, lol... I'v atached a screen shot of the error message.

Thank you for that link, i hope that works.

And i kno that Google is, I usually use it first and ask later, but i did that backwards this time, lol.

---

### Post by TheSpecialEd on 2010-05-20
Good news! :P I figured out the problem and discovered another, but i'll deal with the latter later.
I found out that my account was not a full administrator, and not in the root privileges, so i made it one, and then i ran gksudo nautilus and created etc/Wireless (because i was reading somewhere that people were having issues with the card being recognized, because a .dat file was missing) and then tried to run the .deb Pp2 from the link i posted above, and it ran! and installed the module, rebooted, and now i have my wireless card working.

Ps: your right google is my friend, lmao...

Now i have to find out why i cant sign into sudo, it asks for my account password, and then it wont let me type it in, annoyingness. :(

---

