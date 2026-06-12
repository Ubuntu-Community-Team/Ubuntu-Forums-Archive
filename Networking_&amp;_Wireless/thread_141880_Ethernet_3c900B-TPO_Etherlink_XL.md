---
title: "Ethernet 3c900B-TPO Etherlink XL"
date: 2006-03-09
forum: Networking &amp; Wireless
---

### Post by flamarro on 2006-03-09
Hi guys
I used to connect to the internet with a adsl modem usb, wich gave me a lot of troubles to do it, because was an octal a360 ( I'm from portugal my isp is SAPO ) I have installed rp-ppoe and the amedyn drivers. Well, after all the troubles, i had a stable connection wich worked for months.
Now i bought a router, and installed in my machine with a 3com ( 3c900B ) ethernet card.
In XP ( dual boot ) works fine, In Suse (dual boot ) works fine.
In Ubuntu i can't connect to internet. Here i can acess to router but it is always saying that i don't have a dchp client.
i've read some threads here. I've done ifconfig -a and i can see the eth0 lines, wich means the driver is loaded, isn't it? Also, just for confirmation, did modprobe 3c95x, i think is the driver to my card.
I activated the eth0. The funny thing is that i can do apt-get update and upgrade, but i can't use firefox, gaim, thunderbird and all of the other things, only apt ??????
The only thing i didn't do ( i mean, that 've read about ) was edit modules and interfaces.
I'm going to install kubuntu in another partition just to see what happens, if from a fresh instalation the card is detected

PS: Sorry for my english.

---

### Post by flamarro on 2006-03-09
ok, i've instaled kubuntu, and there you go, i'm typing this letters in it.
No problem at all. instaled kubuntu and in the end internet it's working like a charm.
Edited "/etc/network/interfaces" "/etc/modules" like someone said in the forum, nothing. Only when i do dhclient is when i can see doing ifconfig the ethernet card associated with a IP. I acess the router and theres no MAC Adress assign. typing in the console, i can have internet by number but not by name. Why, Is this a DNS problem. Resolv.conf in kubuntu is similar with the one in Ubuntu. Could be a host name problem? is this one relevant? I do not know much of this ip's, dhcp' thing but it's getting me frustrated. As you can see, in the same machine, i have 4 OS's, and the one i have all the things i need installed  (UBUNTU) i can't get it to work.
What could be the problem ??????

---

### Post by flamarro on 2006-03-10
Well,
been searching and at this thread [http://ubuntuforums.org/showthread.php?t=141728](http://ubuntuforums.org/showthread.php?t=141728) there's something similar, isn't it?
Like i did in kubuntu is seems to me that i must do a fresh install of ubuntu to see what happens.
Someone could tell me what are the files relevant to configure internet using a router. I know /etc/network/interfaces, /etc/resolv.conf, edit both using some advices in this forum, but with no sucess.

---

### Post by flamarro on 2006-03-12
ok, i opened and i close it.
Case closed. Restarted with a fresh install of ubuntu. I need it really. I have tried so many things that i was creating a disk of junk really :p

this thread was a monolog really but, well, :rolleyes:
gave it a shoot....

---

