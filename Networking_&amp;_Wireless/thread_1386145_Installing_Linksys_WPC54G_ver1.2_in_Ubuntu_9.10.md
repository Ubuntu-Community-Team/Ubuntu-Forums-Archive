---
title: "Installing Linksys WPC54G ver1.2 in Ubuntu 9.10"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by sanjulive on 2010-01-20
First, what I did wrong :( and lost around 5 hours of my life

I found the post - [http://ubuntuforums.org/showthread.php?t=186538](http://ubuntuforums.org/showthread.php?t=186538) on Google. As the steps mentioned there didn't work, I clicked on another link towards the end of the first page-> [http://www.ubuntuforums.org/showthre...01#post1105101]("http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101").  After spending around 5 hours with the above, I gave up(This is where I started doing things right :D

[SIZE=3]**What I did Right:**[/SIZE]

I found the link [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Followed Point 3 under 
**[SIZE=2]device firmware[/SIZE]**

 [SIZE=2][/SIZE] 
**[SIZE=2]firmware installation ([SIZE=1]which goes like as mentioned below[/SIZE])[/SIZE]**

3. In latest versions of Ubuntu (all flavors) and Debian just need to install the b43-fwcutter package: [B]

sudo apt-get install b43-fwcutter[/B] 
[LIST]
[*]
[LIST]
[*]when you are asked "Fetch and install firmware?" answer "Yes" (just press "Enter) 
[/LIST]
[/LIST]
Bingo My Wireless Card worked in 2 minutes :popcorn:

[SIZE=2]
[/SIZE]

---

### Post by darkknight56 on 2010-02-23
This is great advise and worked for me.  I was switching from a Linksys wireless-b card to a linksys wireless-g card.  The b card worked fine but it (ubuntu 9.10) didn't see or recognize the g card.  I followed this advise and, when done, the g card worked immediately- no problems what-so-ever..

---

### Post by hopeandaprayer on 2010-03-01
Perhaps you can help. I've tried everything, including your fix, with no luck. My card (Linksys WPC54G ver. 1.2) reads the wireless network (from a Thomson router), strong signal strength, appears to validate the WPA passphrase, but it obtain an IP address and the connection attempt fails. Wired is fine, working well; but the wireless connection is driving me crazy. 

Help?

---

### Post by sanjulive on 2010-04-02
I think, you should try WEP and see whether it works

---

