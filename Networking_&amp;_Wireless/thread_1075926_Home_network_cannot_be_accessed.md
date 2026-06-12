---
title: "Home network cannot be accessed"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by xtiano77 on 2009-02-20
Ubuntu 8.10, 64bit
Inter Dual Core Quad Processor
2GB DDR2
Inter 775 Socket
Two ACER 193W Monitors

I had setup a network between my older computer (Windows XP Professional) and my laptop(Windows Vista Home Premium).  I replaced the Windows XP computer with this computer running Linux.  When I try to access the other computer in the network, it shows me two Network Groups, the one I created and another named "WORKGROUP".  Every time I try to access the network I created, it displays a small alert window saying that the operation is being performed and that I can stop it by clicking cancel.  After waiting for a few seconds, the operation fails and as a result I cannot access the network.  I have already setup permissions on the folders in my "home" so they can be seen from the other computer, but it is still not working.

As always, thanks for your help.

---

### Post by xtiano77 on 2009-02-25
Let me change gears a little bit.  I just installed Ubuntu 8.10 on my laptop and removed Samba from my desktop, so both computers are now running Linux 8.10.  However, now both show two networks, "MCHOME" and "WORKGROUP".  When I click on "MCHOME", I can see the shared folders of each computer, but I cannot see the other computer's shared folders. I tried renaming the wired "Auth0" network on my desktop to "MCHOME" and the wireless "Auth0" on my laptop to "MCHOME" as well, but I still cannot get either computer to see the other.  Also, it seems as if the both computers are still stuck on a Windows network mode.  I say that because the "WORKGROUP" network was the default Windows network on my laptop when I first networked with an older XP computer a while back. I read through the "Network" section of the "Ubuntu 8.04, The Complete Reference", but everything I read seems to relate to networking between a Windows and a Linux box not between two Linux boxes.  Can anyone explain to me what I am missing or at least point me in the right direction? As always, thanks in advance for your help.

---

### Post by jonandrews on 2009-02-25
Have a look at my Ubuntu / XP networking website. I realise that you are now using Ubuntu pc's, but my tutorial 'About Windows Workgroups' may be helpful in figuring out your current problem.

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

### Post by xtiano77 on 2009-02-25
Well, I don't know if this is the correct way of doing things, but it achieved what I was trying to do.  I logged into my wireless router and found the IP addresses for both computers.  Then I went to Nautilus and typed "smb://" + the IP address for the computer I wanted to see and BINGO!, I was able to enter my laptop after typing my password of course.  Then I saved the address as a bookmark and renamed to with my laptop's name.  I am pretty happy with this, but I wonder if there is another more efficient way of doing this?  I just want to say thanks to everyone who tried to help.

---

### Post by xtiano77 on 2009-02-27
I found the answer to the mistery.

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

---

