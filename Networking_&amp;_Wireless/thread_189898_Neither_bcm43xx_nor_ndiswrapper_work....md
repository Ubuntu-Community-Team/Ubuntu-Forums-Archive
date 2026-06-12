---
title: "Neither bcm43xx nor ndiswrapper work..."
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by jstroot on 2006-06-05
Hi all, 
I have followed the tutorials to a T, and they both come to the same conclusion.

The system sees the card, the applets (Network Manager, Netapplet) see the card, AND they see the networks! When I try to connect to a network, it acts like the little train that COULDN'T.

Any ideas are appreciated.

jstroot

---

### Post by DeadlyMuffin on 2006-06-05
I have the same problem, I have a BCM4318 on a Inspiron B130. I blacklisted bcm43xx and installed ndiswrapper. Ndiswrapper says the hardware is present, I can even pick up other networks with the utilities or iwlist scan, but I can't connect to anything to save my life.

Also, interestingly enough, my wireless card is showing up as eth1, not wlan0 which is what I've always gotten with ndiswrapper before (other computers)

---

### Post by jawrat on 2006-06-05
Guys, try setting a static IP address...there was some weird message in the syslog that tipped me off and mine's working now.  

Dell 5150 / TrueMobile 1300 (Broadcom 4306)

---

### Post by DeadlyMuffin on 2006-06-06
I've tried static and dynamic. No go.

---

### Post by notoriousdbp on 2006-06-06
It took me ages but this is what I did to get mine working.  I have a Broadcom 4318 in an Acer Aspire 3002.

1) Installed ndisgtk, ndiswrapper-source and ndiswrapper-utils

2) Following advice from various other forums, blacklisted the bcm43xx

3) used the gui version of ndiswrapper to install the windows driver (bcmwl5.inf) which I had copied to a USB flash drive.  The orange light on my laptop (an acer thing I'm sure) started falshing straight away

4) opened up a text editor and edited /etc/modules to say ndiswrapper at the bottom so it started the driver on boot

5) installed network-manager

6) opened up a text editor and edited /etc/network/interfaces and commented out the lines which referred to eth1 following advice from other forums (this is so network-manager will see the ndiswrapper driver, trust me on that one)

7) Rebooted and wahey we were finally in business.  I'm writing this now in Dapper on said laptop using said wireless internet connection.  Hope this helps everyone.

---

### Post by maddbaron on 2006-06-06
we have the same laptop!!! yes!...ok can someone tell me step by step what to do so i can do steps 1 thru 6?

---

### Post by H.E. Pennypacker on 2006-06-06
[QUOTE=maddbaron]we have the same laptop!!! yes!...ok can someone tell me step by step what to do so i can do steps 1 thru 6?[/QUOTE]

I'll let you know as soon as I can figure out what "commenting out" means in his step 6.  I have no idea what it means to comment out things and what it involves. 

As soon as I figure this out, I'll guide you through the steps.  Follow as many steps as you can beginning with the first one before anything.  Then, once I am ready, I'll guide you through the rest.

---

### Post by crag277 on 2006-06-06
[QUOTE=H.E. Pennypacker]I'll let you know as soon as I can figure out what "commenting out" means in his step 6.  I have no idea what it means to comment out things and what it involves. 

As soon as I figure this out, I'll guide you through the steps.  Follow as many steps as you can beginning with the first one before anything.  Then, once I am ready, I'll guide you through the rest.[/QUOTE]

For that particular file all you need to do is put a '#' in front of the lines you want to comment out.  Same as '//' in C++.  So you should put a # in front of every line referring to eth1.

Now I have to try this with my 4318...  (Compaq V2000z, Turion, ATI)

---

### Post by Slicedbread on 2006-06-06
I cant even get my wifi light to turn on or scan even though the driver is installed on my 4318.

---

### Post by maddbaron on 2006-06-06
[QUOTE=H.E. Pennypacker]I'll let you know as soon as I can figure out what "commenting out" means in his step 6.  I have no idea what it means to comment out things and what it involves. 

As soon as I figure this out, I'll guide you through the steps.  Follow as many steps as you can beginning with the first one before anything.  Then, once I am ready, I'll guide you through the rest.[/QUOTE]


THANKS!!

but i dont know how to start i click terminal then i am lost as to what to type

the 1st two steps are out of my league(I'm a lowly linux newbie :(  )

---

### Post by crag277 on 2006-06-07
[QUOTE=maddbaron]THANKS!!

but i dont know how to start i click terminal then i am lost as to what to type

the 1st two steps are out of my league(I'm a lowly linux newbie :(  )[/QUOTE]

"sudo gedit /etc/network/interfaces"

"sudo" - gives you temporary super user (root) privileges.  Needed to changes certain files.  You'll probably have to type in your password.

"gedit" - gnome text editor

"/etc/network/interfaces" - the path of the file.  Unlike Windows, not all files in Linux need extensions.  This opens the file called "interfaces" located on your hard drive at ./etc/network

That opens up a nice friendly GUI text editor where you can make the changes.  Click save when you're done and you should be all set...with that file at least.

---

### Post by crag277 on 2006-06-07
By the way...      I posted step by step what I did to get my 4318 working in another thread.

[http://ubuntuforums.org/showpost.php?p=1105667&postcount=218](http://ubuntuforums.org/showpost.php?p=1105667&postcount=218)

---

### Post by pdfcomp on 2006-06-09
New guy in.  Thanks for the instructions.  My son has an Acer Aspire 3003 he had not had luck with getting wireless to work.  It has same Broadcom wireless nic.  I followed the instructions on ndiswrapper, except I downloaded the driver from ACER.  My only problem now is if I enable any wireless security on my router (D-Link DI-624), I cannot connect with the laptop.  I have tried WEP with both ascii and hex keys.  Any suggestions?

---

### Post by maddbaron on 2006-06-09
[QUOTE=crag277]"sudo gedit /etc/network/interfaces"

"sudo" - gives you temporary super user (root) privileges.  Needed to changes certain files.  You'll probably have to type in your password.

"gedit" - gnome text editor

"/etc/network/interfaces" - the path of the file.  Unlike Windows, not all files in Linux need extensions.  This opens the file called "interfaces" located on your hard drive at ./etc/network

That opens up a nice friendly GUI text editor where you can make the changes.  Click save when you're done and you should be all set...with that file at least.[/QUOTE]

ok i have a problem. i tried running your steps again and when i do step one I get a blank gedit file. is something missing?

---

### Post by denisesballs on 2006-06-09
Everything here works fine. I get both my devices in Network Manager, but when I click the wireless, it just hangs and hangs. Anyone have any idea why?

---

### Post by crag277 on 2006-06-09
[QUOTE=maddbaron]ok i have a problem. i tried running your steps again and when i do step one I get a blank gedit file. is something missing?[/QUOTE]

Yes.  Sorry.  In step 1 I made a typo.  The first step should be: "sudo gedit /etc/modprobe.d/blacklist"

As far as the other problems I wish I could help.  I don't have alot of experience with this.  All I know for sure is that even different computer with the same Broadcom chipset can behave very differently, and it seems very rarely correctly.  Good luck.

---

### Post by maddbaron on 2006-06-09
i got it. i followed something from the newbie forums and it works like a charm even tho i cant see my ip address or my wireless strength icon lol.

---

### Post by grandadjim on 2006-06-10
I had same trouble with my Belkin but this link if followed exactly cured my wireless woes! note even the capitalisation of th word Worktop is essential when typing code!
[http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear)
Rgds James

---

### Post by grandadjim on 2006-06-10
Sorry I meant to say capitalisation of the word Desktop

---

### Post by Blind-Summit on 2006-06-10
I tried this as I have had no luck with the countless outher 43xx broadcom posts. Again, this failed to work for me. Adding the blacklist flag caused my system to not boot. I found out that some errors were showing up regarding some firmware files???

Anyway - I removed the blacklist and I may try renaming the file instead. I also did the commenting out, but that didn't help either.

This is impossible and driving me mad here!

---

