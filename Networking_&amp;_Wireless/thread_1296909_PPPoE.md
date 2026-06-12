---
title: "PPPoE"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by caligula2 on 2009-10-21
I am trying to set up a modem that I am renting. It's working fine in Windows, but not in Ubuntu.

The way that I set it up in XP was that I went to Network Connections -> Create a new connection -> clicked next 2 times -> Set up my connection manually -> Connect using a broadband connection that requires a user name and password -> i filled in the ISP name -> chose "Anyone's use" -> filled in "User name" "Password" and "Confirm password" and I was done

So basically, what I'm asking is how would I go about doing a similar thing in Ubuntu?

---

### Post by caligula2 on 2009-10-25
bump

also, eth0 doesn't show up in Network Connections anymore.

---

### Post by Radissthor on 2009-10-25
Have you tried the pppoeconf command? It worked for me, though it killed my wireless configuration and I had to edit it manually afterwards, but that's cuz I have to connect to both a wireless and a PPPoE at the same time...

---

### Post by caligula2 on 2009-10-26
every place i look, people say that that has worked for them, but i can't get it to work for me. i even type into the terminal "ifconfig" just to make sure that it is there. i do see it, and it has an ip address and a P-t-P address, but i can't connect to it.

also, i finally figured out how to get my eth0 to show up again in network manager, so i don't need help with that anymore.

---

