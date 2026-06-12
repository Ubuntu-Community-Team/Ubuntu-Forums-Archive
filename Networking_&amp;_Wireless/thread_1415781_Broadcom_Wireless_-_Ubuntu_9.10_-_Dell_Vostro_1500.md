---
title: "Broadcom Wireless - Ubuntu 9.10 - Dell Vostro 1500"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by masternosaj on 2010-02-25
Hello everyone,

I am having some odd issues with wireless networking on my Dell Vostro 1500.  I have a Dell Wireless 1490 card (which uses a Broadcom chipset).  Let me go through my story.  Please keep in mind that I am new to Ubuntu.

Last night I did a clean install of Ubuntu 9.10 with my laptop connected to a wired connection.  After installation, I installed all system updates and rebooted.  From here, I went into Hardware Drivers and installed the Broadcom STA drivers (the proprietary ones) for my wireless card and rebooted again.  After this, I get nothing from the Wireless card.  It will not display any available networks or let me connect to any hidden ones.

Frustrated (because I have used Ubuntu 9.04 a while with this card), I clean-reinstalled Ubuntu 9.10 again.  This time, I installed the wireless driver first in Hardware Drivers and rebooted.  This time, it worked beautifully.  I was able to connect to my wireless network and all was well, until doing system updates that is.  When I tried to install system updates, I got a few kernel panics (which I did not get the first time I installed updates in 9.10).  After a few lockups/crashes, I finally got all system updates installed.  Upon reboot, no wireless again!

Even more frustrated, I uninstalled the Broadcom driver, rebooted, reinstalled it, rebooted and it worked again, until the next reboot which killed it again.  Is there some system update that is killing my wireless?  

I am currently at work and don't have access to my laptop, but feel free to ask any questions and I will answer as I can.

Thanks!

---

### Post by bkratz on 2010-02-25
> **masternosaj said:**
> Hello everyone,

I am having some odd issues with wireless networking on my Dell Vostro 1500.  I have a Dell Wireless 1490 card (which uses a Broadcom chipset).  Let me go through my story.  Please keep in mind that I am new to Ubuntu.

Last night I did a clean install of Ubuntu 9.10 with my laptop connected to a wired connection.  After installation, I installed all system updates and rebooted.  From here, I went into Hardware Drivers and installed the Broadcom STA drivers (the proprietary ones) for my wireless card and rebooted again.  After this, I get nothing from the Wireless card.  It will not display any available networks or let me connect to any hidden ones.

Frustrated (because I have used Ubuntu 9.04 a while with this card), I clean-reinstalled Ubuntu 9.10 again.  This time, I installed the wireless driver first in Hardware Drivers and rebooted.  This time, it worked beautifully.  I was able to connect to my wireless network and all was well, until doing system updates that is.  When I tried to install system updates, I got a few kernel panics (which I did not get the first time I installed updates in 9.10).  After a few lockups/crashes, I finally got all system updates installed.  Upon reboot, no wireless again!

Even more frustrated, I uninstalled the Broadcom driver, rebooted, reinstalled it, rebooted and it worked again, until the next reboot which killed it again.  Is there some system update that is killing my wireless?  

I am currently at work and don't have access to my laptop, but feel free to ask any questions and I will answer as I can.

Thanks!



Since you are seeing this after updating you may want to look at this thread. It is about a different wireless card but Chili555 in  postings 3 through 5 explains a phenomena seen with Dell systems. I believe it may be worth checking out.

[http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop](http://ubuntuforums.org/showthread.php?t=1414946&highlight=dell-laptop)

---

### Post by masternosaj on 2010-02-25
Thanks, I'll give it a try when I get home.

---

### Post by masternosaj on 2010-02-28
I have not tried what you mentioned, but I did figure out something of interest.  It seems that the wireless is working, however, it appears that Ubuntu does not correctly recognize the position of the wireless radio switch on the side of my laptop.  If I boot with the switch in the off position, and then flip it on when I am on the Ubuntu desktop, all is well.  I am able to see wireless networks and able to connect to my hidden wireless network.

However, if I boot with the switch in the on position, Ubuntu acts as if it is off.  At that point, if I turn the switch off, Ubuntu gives me the option to try to connect to a hidden network or the option to create a new network, however, the device itself is off (because the switch is in the off position) and will not find any network.  It's as if Ubuntu is confused of the switch position.

This situation keeps getting more weird.  What update would have caused this to happen.  I have again done a fresh install of Ubuntu just to try everything one more time, and the exact same thing has happened.  Wireless works perfect before OS updates, and then acts like the above after updates.

Thanks for any more help anyone can provide!

---

### Post by bkratz on 2010-02-28
Please look at chili555's posts 3 and #5 in that thread--he may have already provided a solution. At least it is worth trying, it can't hurt.

---

### Post by masternosaj on 2010-02-28
I should have tried your link sooner, bkratz.  After black-listing the dell-laptop module, it seems to be working fine.  I hope it doesn't affect anything else adversely.  Thanks a million for your help!

---

### Post by bkratz on 2010-02-28
> **masternosaj said:**
> I should have tried your link sooner, bkratz.  After black-listing the dell-laptop module, it seems to be working fine.  I hope it doesn't affect anything else adversely.  Thanks a million for your help!

Please go to the thread tools and mark as [solved] in case it helps someone else.

---

### Post by masternosaj on 2010-02-28
Done, thanks again.

---

### Post by robertuit on 2011-02-25
I had good luck. After I found and loaded all the right networking drivers on my Vostro 1500, the wifi would still not work. I went to devices, and removed all of the networking devices, and restarted Windows. During startup, Windows plug and play found all of the devices, loaded the drivers, and found my network.:D
 
Thanks for the hints!

---

