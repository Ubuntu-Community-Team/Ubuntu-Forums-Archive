---
title: "problem with amule &amp; router linksys WRV54G"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by giampaolo44 on 2010-10-12
hi,

i've been trying for the past couple of days to configure aMule to work with my router linksys WRV54G, but am encountering problems.
apparently i can't open the router's ports, and i keep getting a low ID.

i followed several how to's, but the problem does not seem to go away.  i tried to configure it both using standard port forwarding and UpNP, with no luck at all.

i'm running ubuntu 10.04, aMule 2.2.6 and my router has a Firmware Version 2.39.2e

could anybody help?

cheers!

---

### Post by giampaolo44 on 2010-10-13
a little addition: the router seems to change by itself the settings i make :confused:
sometimes it deactivates the table rows, or plainly empties them :(

i can't figure this out....

---

### Post by giampaolo44 on 2010-10-15
mmm.... no one spends a couple of cents to help out?

actually i don't get help that often in here :(

so much for the community...

---

### Post by maxino on 2010-10-20
Hi,
I just installed amule on my system and after following the instructions [**_HERE_**]("http://wiki.amule.org/index.php/Firewall") it worked flawlessly (got high ID at once).

My router is a Netgear, but at the link above you can find info about how to set generic Linksys routers (and, specifically, about the WRT54GSV4).

Apparently your router "forgets" the port forwarding settings... of course you did apply and/or save the modifications, didn't you?

Another thing you may try is to backup the new configuration, reset the router, and then restore the settings from the backup.

Buona fortuna,

---

### Post by giampaolo44 on 2010-10-25
thank you so much!
i'll try that right away and let you know :)

btw: yes i saved the configurations :D

---

### Post by giampaolo44 on 2010-10-27
mmm... so far no luck. 

as far as i understand i have to set the pc to use a fixed ip, which i tried in my earlier attempts to set amule, but gave me some  problems.

i'll retry and update...


btw: should i try a "random" ip (i am guessing that choice is for the fourth 1-255 set of ip numbers) or is there a better way to choose it?


yeah, i know, i'm too newbie still, even after more than a year on ubuntu :confused: :(  :P
i'll give myself another year to ](*,) on linux, otherwise i'll move :cry:  back to some :evil:

---

### Post by nerissa22 on 2010-10-27
I am also suffering with same problem...i can not solve this problem till now....i want complete information about this....Please suggest me some discussion topic...

---

### Post by maxino on 2010-10-27
I think the point is that the your router must know the local IP address of the computer (running AMule) to which to forward requests to.

What I did was to configure manually my computer - by setting a fixed IP address, gateway, netmask - rather then using the router's DHCP feature. This way I am sure that the IP address will never change.

Afterward just input such IP address into the right place in your router configuration menu.

---

