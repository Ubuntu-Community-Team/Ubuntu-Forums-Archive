---
title: "Any programs (with GUI) that list network connections + speeds up + down"
date: 2012-07-13
forum: Networking &amp; Wireless
---

### Post by bzd454 on 2012-07-13
Hi,
     was looking for some program with GUI that would list all the individual connections as well as how much data each of those connections is producing - something like what the Avast ISS firewall shows or the typical programs in Windows like System Explorer iirc. 
 
I found something called Net Activity Viewer and its decent but doesn't show the bandwidth being user per connection.  Really i'm looking for a kind of all-in-one program that shows processes also and few other things, (like the Windows Task Manager on steroids - there are quite a few of these avail on the Windows side and they are very useful).  I looked at Conky a few years ago but it was too complicated for me to install. :(

---

### Post by clappboard on 2012-07-13
In a situation like this it might be best to go into the Ubuntu Software Centre.  It has an excellent search feature.  Try general search terms like network, speed, etc. until you get what you want.
To answer the question though, wireshark may be what you are looking for.  Take some time and look around the repositories.

---

### Post by Kirk Schnable on 2012-07-15
I realize you wanted something with a GUI, but it sounds like you're describing iftop. You can install it from apt, open a terminal, and just type iftop and hit enter. It's not a GUI tool per say, but it does fill a terminal window with info in neatly organized columns. You can see source and destination IP, and upload and download bandwidth rates. 

Kirk

---

### Post by bzd454 on 2012-07-19
> **Kirk Schnable said:**
> I realize you wanted something with a GUI, but it sounds like you're describing iftop. You can install it from apt, open a terminal, and just type iftop and hit enter. It's not a GUI tool per say, but it does fill a terminal window with info in neatly organized columns. You can see source and destination IP, and upload and download bandwidth rates. 

Kirk

thanks.  Wireshark is a bit overkill and i don't see up and down speeds listed.  can't believe there isn't a simple program with GUI though that doesn't need to use the terminal :(

---

