---
title: "Ethernet will NOT work please HELP"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by SLR on 2009-01-01
I am a new linux user with a clean install of Intrepid 8.10 and am having terrible trouble simply trying to get an internet connection through my wired network. I can access the router (airlink101) and see my laptop just fine and I can even connect to anything from the Google.com domain (really weird) but absolutely nothing else. This is driving me absolutely insane, I have scoured the message boards and have found nothing relating to my issue. This is a wired network and I know the cable is good and before I did the clean install I was running Windows XP on the same machine and my connection was fine. Even weirder, I can successfully ping any address but cannot get the web through Firefox and can't even do an Ubuntu update. Two things that may help the troubleshoot: this is NOT an issue with 8.10 because when it didn't work I did a clean install of 8.04 and had the same exact problem, the other thing is that when I ran the command ifconfig eth0 it all looks like it should except there were 1,584 errors under RX packets. Not sure what that means but hopefully it helps. I don't care whether I end up running 8.10 or 8.04 just as long as I can get some internet going. 

PLEASE HELP I am going absolutely nuts with this going on day 4 of hair tearing ](*,). Thank you in advance for any and all help with this issue.

---

### Post by Iowan on 2009-01-01
No guarantees, but a couple of things to try/check:
1. disable IPv6
2. Add pci=noacpi to the kernel line in */boot/grub/menu.lst*

---

### Post by stderr on 2009-01-01
Have you tried swapping your ethernet cable with another one that you know works?

---

### Post by SLR on 2009-01-07
Thank you for your replies
> 
Have you tried swapping your ethernet cable with another one that you know works? 

and yes that was the first thing I tried


and sorry to let everyone down with a non-impressive answer, but I finally resorted to buying a new $13 generic brand PCI wireless card, put it in, reconnected the same ethernet cable, restarted, and walla fixed. Up and running perfectly didn't need to do anything else just pure plug and play. Go figure- ubuntu lives up to my expectations after all \\:D/

---

### Post by Iowan on 2009-01-07
One more thing - I notice your post titles have [SOLVED], but not the thread.  You can mark the thread as [SOLVED] by using the option under the Thread Tools pulldown. Congrats on fixing your problem - by whatever means!

---

