---
title: "Mymote agony"
date: 2010-04-21
forum: Mythbuntu
---

### Post by J0ris on 2010-04-21
Hi, 

I've been trying to set up Mymote on a 9.10 Mythbuntu install. I followed the instructions on [http://mymote.wikispot.org/Manual/Requirements](http://mymote.wikispot.org/Manual/Requirements) as well as a link from that page to [http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2](http://www.mythtv.org/docs/mythtv-HOWTO-6.html#ss6.2) (Modifying access to the MySQL database for multiple systems).

/etc/mysql/my.cnf: Tried both to comment out the binding address and replace it by the actual LAN ip address.

Stopped the backend, then restarted mysql and ran mythtv-setup: nothing to change there since appropriate external ip address was already set.

result of all the proceedings: the backend can no longer connect to the mysql database even though I tried to restore everything to its original settings.

One question though: In the mythtv settings I had everything set up already with an external ip address. Turns out that in the my.cnf file the binding address was still set to the 127.0.0.1 loop. Yet everything was working perfectly before. How is that possible? Two different things?

BTW: on the iphone the backend and the frontend was already recognised before I followed the database related part of the instructions. Turns out I did not only not manage to get mymote working but also managed to stop everything else from working. Quite the result!

Message: help! Any suggestions? Obviously I do not have the required networking and database insights for metocomprehend the instructions.


Thanks beforehand.

---

### Post by sydneysuder on 2010-04-22
I have mymote working on my setup.. sort of... 
it works fine for ONE of my FIVE frontends.

I know that one of the frontends does not have a name that meets the mymote requirements (a valid entry in the DNS) but the others are pretty much identical it just doesn't connect.

---

