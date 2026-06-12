---
title: "Can't see XP printer from Ubuntu machine"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by mousethief on 2010-10-14
I'm a brand-new (as of today) Ubuntu user and I'm trying to set everything up. My problem is I can't see the network printer that is connected to an XP machine on the network.

I can ping the XP machine by IP just fine. 

This is probably really simple but like I said I'm a babe in the woods.

Thanks,
MT

---

### Post by pricetech on 2010-10-14
Start by installing Samba

System - Administration - Synaptic Package Manager

Search for system-config-samba which will install both Samba and a handy configuration tool which will appear under System - Administration - Samba

Match your workgroup with your windows box to help with browsing.

You should be able to find and install the printer then,

ASSUMING the printer will work under Ubuntu.

---

### Post by johnnytm on 2010-10-14
samba is generally installed in ubuntu already. if u go to system-->adiminstration-->printing and press add printer (big green + button) it opens a search window. press network printer, then when the options open choose windows printer via samba and then press the browse button. press the carets beside the network and the machine and the printer should show up. This has always worked for me without ever installing anything additional.

---

### Post by mousethief on 2010-10-15
Thanks pricetech and johnnytm! I installed Samba (it wasn't already installed) and tried to do what johnnytm said. But when I pressed the caret beside the workgroup, it thought for a long  time, then took the carrot away and stopped thinking. I looked from my  Windows XP box, and the network was there and I could cruise around to  the different computers just fine -- so it's not that the network is dead or anything. I tried a couple of the other methods and had a similar lack of success.

pricetech, I don't understand what "Match your workgroup with your windows box" means. Do you mean use the same workgroup name that my windows box is connected to (or belongs to or whatever the right term is)?

I don't see why Ubuntu couldn't talk to a HP psc 1315. It's a pretty run-o-th'-mill printer I'd think. Do I need to download a driver first?

Thanks again,
Mouse ("we're going to lick this thing dammit") thief

---

### Post by pricetech on 2010-10-15
> **mousethief said:**
> pricetech, I don't understand what "Match your workgroup with your windows box" means. Do you mean use the same workgroup name that my windows box is connected to (or belongs to or whatever the right term is)?

That's correct.  It's one of the settings you'll find in Samba configuration.  You can still connect without having the same workgroup name, but it helps when browsing if all the computers are the same.

---

### Post by mousethief on 2010-10-15
You mean when I'm adding a printer, or is there somewhere else to go to change the Samba parameters?

MT

---

