---
title: "Network Confusion??? Needs Explanation..."
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by iarms76 on 2010-03-15
Hello Guys!  Can anyone help me out in understanding the behaviour of my network connection? I'm using ubuntu 9.10

I have managed to configure my wired network connection in our office and my  ZTEMF 627 modem  both are working fine. 

Then I've decided to replace the default network manager with WICD,  my connection with our office network works fine too but i' can't make my usb modem work with the manager. so I've  decided to remove wicd and reinstall the default network manager. 

My computer's network connection still works fine and i can connect my usb modem. I can connect to the net whichever connection i choose, however my network manager inspite of the fact that i can connect to our office network it has a message saying that device not managed?  Can someone  explain this to me? 

Thanks.  I'ts really bad to be a newbie!!!:oops:

---

### Post by Iowan on 2010-03-15
> **iarms76 said:**
>  I'ts really bad to be a newbie!!!:oops: It's still a step up from "wannabee".
Check contents of */etc/network/interfaces* - It is normally empty (aside from the two lines defining "lo"). If not, you can "comment out" the other lines and reboot. If the problem persists (or gets worse) you can "uncomment" the lines and (hopefully) be back where you started (at least this round...)
At least on previous versions, Network Manager would not manage - or even acknowledge - interfaces defined in */etc/network/interfaces*. In fact, the easiest way to have two active interfaces (since NM would only manage one at a time) was to let NM manage one, and define the other in *interfaces*. There's some question as to whether it still works that way...

---

