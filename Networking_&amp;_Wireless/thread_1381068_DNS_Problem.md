---
title: "DNS Problem"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by Allwynd on 2010-01-14
Excuse me if such thread exists already, i carefully searched the forum so i wont create a second one concerning the following problem:

So i downloaded (on my new fresh Fujitsu SIEMENS Li3710 running Vista the Ubuntu 9.04 distro.. im a complete Linux noob, but i wanted to give it a second try) so i downloaded it and burned it on the fast laptop, so there wont be any errors caused by low memory during burning.. I installed and then i went to the Ubuntu desktop - i had all drivers installed. Everything but Amarok sound worked, i turned off my laptop and went doing my job.. The next time i started up my laptop and went on the desktop .. a tradition is to browse the web, so i did that and i couldnt load a single page, except pages with direct IPs, i had Skype working just fine and i had a friend there running SuSe and asked him for help. We identified it as a DNS problem, but because of my noobness i couldnt deal with it and i HAD TO switch back to windows, wich i regret so much.

I know that im a noob, but if i have an internet running at its best i can look at forums and resolve my other issues, so im asking for a screenshots on DNS settings so i can fix it the next time i install Ubuntu.

Also! I was using cable via PPPoE (and the only terminal command i know is "sudo pppoeconf" :D :D :D ), now im with router, connecting my laptop directly via WI-FI, will i have the same problem and will i have to make settings so i can connect to my router? Because back then i tried to connect to wireless networks and the ones i could connect on XP/Vista/7 i simply couldnt connect on Ubuntu...

I really want some real PC knowledge and to use Linux.. but ;( im too noob. So, please help me on those network issuse.

And excuse me for the long and inaccurate thread. Im truly sorry!!

---

### Post by pricetech on 2010-01-14
Try hard coding your DNS.  Use Open DNS servers:
208.67.222.222  and  208.67.220.220

---

### Post by Allwynd on 2010-01-14
thanks, but:
1. how do i do that?
2. is this setting global? i mean if i do it, will it prompt me for every page i try to open, or once i do it will be fine? :)
thanks in advance

---

### Post by Iowan on 2010-01-14
Noobiness can be fixed...
Does your machine get address from router? (Check via **ifconfig -a ** from a terminal). If you use DHCP, you can use the "prepend" line in */etc/dhcp3/dhclient.conf* to add the aforementioned DNS servers. Use either "sudo nano" or "gksudo gedit" to edit the file.

You can edit */etc/resolv.conf* and input the servers directly, but sometimes the file gets overwritten.

---

### Post by Allwynd on 2010-01-16
thanks, i will give it a try :)

---

