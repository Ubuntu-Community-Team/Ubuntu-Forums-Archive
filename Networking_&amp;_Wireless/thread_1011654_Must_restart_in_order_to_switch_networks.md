---
title: "Must restart in order to switch networks"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by D.horse on 2008-12-15
Im new.

I use my computer at school and at home.  I have a problem where i need to be in roaming mode when i am at school and i am using a WEP network at home.  So i switch between two profiles.

Well, the problem i am having is that when i switch from the roaming profile to the WEP profile i need to restart my computer before it will actually work.  It will say it is connected but will not let me go to any sites.

This is annoying and i was wondering if there is something i could have done wrong with my network setup that could causes this, or in the mean time while i try and figure it out is there a way for me to reset my connection or something so that i do not need to do a full system restart just to check my email?

If you would like anymore information please let me know and i will post what you need.

NOTE: does not work the other way around, as in switching from the WEP profile to the roaming one works fine

---

### Post by prshah on 2008-12-15
> **D.horse said:**
> 
while i try and figure it out is there a way for me to reset my connection 

for the meantime:

Open a terminal (Applications-Accessories-Terminal) and give the following command to restart networking```
sudo /etc/init.d/networking restart
```

If your home connection is using DHCP, you may also need to give the command```
sudo dhclient wifi0
``` (Replace eth0 with the actual networking interface you are using.)

It's very likely that you will need either the 1st _or_ the 2nd command, and unlikely (but not impossible) you will need both. However you can use both (in any order), neither will cause any problems if it is not applicable.

---

### Post by D.horse on 2008-12-15
Thank you for the reply.

But does anyone have any idea why I need to restart the network for it to work?  Is it possible something is not set up correctly on the router.  Because i do not have this problem with this on my XP machine (can connect to other networks in the APT and back to mine).

NOTE:  While i am new i am learning this OS for fun and like to play around with it so you can say more advanced stuff to check and i will google it to figure out how to do it.

But that would raise the question why dont i just google the issue, and that reason is I tried it and could not find an issue similar to this.

---

