---
title: "internet connection dies after a while"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by strattonbrazil on 2006-06-15
I have a Toshiba Tecra S2, which I installed Ubuntu 6.06 on.  The OS detected my wireless Centrino perfectly and runs fine.  I then switched my default connection to the eth0 for my ethernet connection in the wall being a little faster.  

It seems though that after the computer has been on a while or something, the connection stops working.  I still have ip addresses for both of them, but nothing works in the browser.  Using a different computer, I see the internet is still working fine.  

Sometimes when I'm using eth0 it'll jump over to eth1 for wireless and I don't understand why it just doesn't pick the default and switch to wireless only when it doesn't work.

---

### Post by kuppas on 2006-06-15
It seems that You have configured two network interface and your application (like browser) can't figureout which one to use.  You need to set the connection priority to solve this problem.

The connection priority depens on the speed of the network card. If the wired network card speed is 100Mbps and wireless 10Mbps then wired one will be selected. To setup the priority of the network connection manualy then you can set the METRIC value.  The lower METRIC value has higher precedence over the others.

-Kuppa

---

### Post by YuRaider on 2006-06-17
Same problem here!

My Scientific Atlanta WebStar 2000 cable modem works perfectly when connected through my ethernet adapter, but when I try to connect it via the USB interface, it only works for about 2 minutes or so, and then it stops! The modem keeps sending one packet per second, but recieves nothing...

The weird thing is - everything worked great in Breezy Badger, and this only happens in Dapper Drake!

PS I really need to connect it through USB 'cause I use my ethernet adapter to connect my 2 PCs...

---

### Post by strattonbrazil on 2006-06-18
Well, I don't believe switching is the actual problem.  I'm convinced it's something wrong with the Ubuntu machine.  If I externally switch off the wifi, the ethernet will work fine for a while.  Then all of the sudden, it just stops working.  I get zero bandwidth.  The Debian computer downstairs is fine and so is the Windows machine.  I didn't have this problem on my laptop running Windows, Debian, or SUSE Linux.  It's really frustrating, because it's so off-and-on.

---

### Post by bright_music on 2006-06-19
I have the same problem!!!

But it stays on just for few seconds!!!

WHAT IS THAT???

best!

---

### Post by hotice3100 on 2006-07-10
I had the same problem.  I followed the instructions found in the link below and everything worked fine again.

[http://www.ubuntuforums.org/showthread.php?t=186430]("http://www.ubuntuforums.org/showthread.php?t=186430")

---

### Post by strattonbrazil on 2006-08-21
I followed those instructions and they might have helped a little, but my connection still dies after a few minutes.  Then I have to do a 'sudo ifdown eth0' and 'sudo ifup eth0' to bring it back up.  Any where else I can go?

---

### Post by mastergunner on 2006-12-27
Stratton did you get your modem to work on USB cause I am having the same prob. I can not get onto the internet at all and I have the sam modem as you.

---

### Post by dstath on 2008-01-08
I have a similar problem with another USB modem. 
Internet works for a few seconds and then stops. 

see [here]("http://ubuntuforums.org/showpost.php?p=4093248&postcount=32") for a complete description.

I intent to try the fix that hotice3100 suggests tonight.

---

### Post by elvinatom on 2008-01-08
I had nic problems with ubuntu for the longest time. i got a whole bunch of 3com/d-link/noname nics (all suposedly supported by linux) and not for the heck of it i could configure ubuntu (workstation or server) to run ANY of those as a primary or secondary card.  The card is detected and configured and just dosen't see my static cable modem.  if i put a router in between it connects for a little while then dies (then had to revive it with "/etc/init.d/networking restart", which sometimes kept me from rebooting, but sometimes just locked up the system).  if i use the and of the cards for file sharing i lock up my system after a few MBs of transfer.

I had this problem on 2 brand new AMDs and one old IBM-box.  I just can't imagine it to be a hardware, configuartion issue.  Oh, i had one system where the onboard nic did the same thing under suse (with a via rhine) - that makes 4 systems.  Now i just hook up all pcs with the on-board nic only and my via rhine works fine under winxp.

Kinda strange that there are hardly any threads abouts this in the linux community.

---

### Post by dstath on 2008-01-08
I tried the blacklist fix mentioned above without success. I can ping e.g. google.com, both by name and by IP address, imideately after i connect to the web but a few seconds later ping returns nothing.

---

