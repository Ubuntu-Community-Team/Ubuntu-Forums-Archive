---
title: "belkin f5d6020 v3 and its sporadic behavior"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by jespera on 2006-07-08
so i just installed kubuntu. my cards works out of the box. if i go to the wireless manager my card can find available networks, it can even connect and i can surf the web, then about a 2 minutes later it "drops" and nothing works. no networks available and i have to restart the machine to HOPEFULLY get it to do the same thing????? thoroughly confused. any help would be monumentus to this newb. thanks guys!

---

### Post by ubercat on 2006-07-08
Hi,

There are many reports of disconnects with the Belkin cards, no matter which of the 3 versions. I have version 2 cards, and they lose the ability to connect to their AP constantly. One hack work-around is to run a terminal with a ping set with an interval to keep the card associated. Ex:

ping -i 30 your.mail.server


as this seems to be a time-out issue of some sort.
Sub whatever address or ip you want, as long as it's beyond your gateway. This hack keeps the card associated (connected). 
30 is the interval; a single ping is sent in this example every 30 seconds.

I have this problem under under both Breezy and Dapper. I'm awaiting the arrival of a Cisco Aironet card to determine whether the problem is the Belkin card or another problem. I suspect it's another problem, as many other users with various cards have the same problem.

I can't get the Belkin to work at all under installed xubuntu, but it works with the live CD!

---

### Post by jespera on 2006-07-08
well after looking through the forums, i went to konsole and did the sudo apt-get remove wpasupplicant. and now the card keeps the connection and works fine, now my only problem is it doesn't let me connect to a wep enabled router.

---

