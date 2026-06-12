---
title: "cant get connected"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by vinney on 2011-03-22
Hi everyone. I'm new to this community as well as to Linux so please bear with me.
I've been given an old Dell Latitude CPX-H500 with 256mb RAM. Very sluggish so a friend suggested I try Linux. This laptop only has a USB wifi adapter which is a Belkin F5D8053 V6. I installed Xubuntu 10.10 from CD but without internet connection. I would like to get online with this if possible, but I must admit to being confused by what I have read so far. Maybe I'm trying to take too much in at once. I will be using this laptop just for communicating with my son over Skype so hopefully nothing too taxing as I cant afford to buy him a better machine just yet. Could someone please help me sort this problem out, but remembering I'm not a techie.
Thank you
p.s obviously using daughters pc to post this

---

### Post by EdwardR on 2011-03-22
When xubuntu starts, do you get a message or a notification in the notification area (the icons at the top right corner of the screen) that additional drivers are available for download?  Do you have a PCMCIA network card for the laptop so that you can connect to the internet with a wired connection (a card like a fat credit card with a connection for an internet cable at one end)? If so, insert the network card into the slot on the side of the computer and connect the internet cable - this should get you connected to the internet after a few seconds.  Then click on the notification to download and install the drivers.  Hopefully after that your wireless will be working.  You might need to right-click on your network icon and disable then re-enable wireless networking to get it started the first time.

---

### Post by vinney on 2011-03-22
Hi, sorry but no card to connect to the internet for this laptop. When it boots up there is no notification at all that additional drivers are needed. Did I screw up the installation?

---

### Post by colio on 2011-03-22
Is there an ethernet adapter in the computer?

---

### Post by Fire_Chief on 2011-03-22
You may want to try this method.
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053")

Cheers!

---

### Post by vinney on 2011-03-22
Thanks for the replies. I have read through the article on the link you gave me. Very confusing. After downloading the driver I need it wants me to install "wine" but every time I search on how to download and install wine I keep getting sent back to the same page that assumes I am already internet connected with the laptop that has Linux installed. I checked under installed software and "wine" is not listed. Also I got a popup on the desktop that informed me "that no proprietary drivers are installed". I am really beginning to wonder if I messed up the install?
Apologies.
I am just very new to Linux and it all seems a bit daunting at first.

---

### Post by EdwardR on 2011-03-22
What happens when you plug in the wireless device to the computer's USB port?  If you left-click on the network icon in the notifications area, do you see any wireless networks or is the text greyed out and saying wireless is disabled?

---

### Post by vinney on 2011-03-23
The words "wireless networks" is in black, but underneath "disconnected" is greyed out.

---

### Post by EdwardR on 2011-03-25
Since it says "disconnected" rather than something like "missing firmware", then it sounds like your wireless driver might be installed.  When you left-click on the network icon, below where it says "Wireless networks" and "disconnected", does it say "Available" and list any networks?  If it does, then look for your network (you may need to click on "More networks") and click it to get on to the network.

---

