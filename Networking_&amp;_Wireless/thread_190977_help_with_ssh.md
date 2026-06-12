---
title: "help with ssh"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by Lhoward on 2006-06-06
I have a new metrix mark 11 ap. I was hoping it was plug and play. It is not I do not know what I an doing. Metrix flashed the eeprom with Pyramid Linux. I found a getting things set up paper. It talks about going on line "**The web interface is available through SSL**" what is this and were do I find it. In another part it has "After enabling the web interface (log in over SSH and type "startssl") you have access to a variety of configuration tools and information screens???????  Help    :confused: Please show me were look.
Thanks Larry H

---

### Post by goodmaj on 2006-06-07
I have never set up a Matrix AP, but based on what I see on their web site,  this is what I guess you need to do.

1) Connect to the AP with an Ethernet cable. (You may need a crossover if you are not going throough a hub).

2) ssh into the Matrix using the username, password and default ip address which should be in the instructions that came with it.

For example, from a terminal session type ssh admin@192.168.1.1 (where admin is the username and 192.169.1.1 is the ip address of the Matrix box).  After giving the password you should be able to issue the startssl command.  Then you will be able to access the GUI from your browser at [http://192.168.1.1](http://192.168.1.1) or whatever the correct ip address is for the Matrix.

Good Luck.

---

### Post by goodmaj on 2006-06-07
Since it is a SSL interface you probably need to type https:// instead of just http://

---

