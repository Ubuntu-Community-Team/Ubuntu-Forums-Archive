---
title: "Problem with both wired and wireless connection in fresh Ubuntu 10.04 installation"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by nkhaja on 2010-06-09
Hello friend,

I have recently installed Ubuntu on my Dell Vostro 1000 laptop.
Ubuntu is neither getting connected using wired nor using wireless in my laptop.

My Wireless radio led is being off always. I 'm unable to figure out a way to turn it on.

My laptop also has windows vista basic installed. 
I think the network manager hasn't configured my Network adapter drivers properly.

But before installing I just tried Ubuntu using CD without really installing. At that time everything was fine.

I am a beginner. Please help me.

---

### Post by pytheas22 on 2010-06-09
Does your laptop have a switch or hotkey (like Fn+F2) for toggling the wireless on and off?  If so, nothing happens when you press it?

You might also want to check your BIOS settings.  In many cases there are different options there for configuring the wireless radio; playing with them may provide a solution to your problem.

If none of the above helps, please open a terminal from the Applications>Accessories menu, run the following commands and post the output here:
```

dmesg | grep -e eth -e wlan -ie radio
lspci -nn
lshw -C Network
sudo iwlist scan
```

Since you currently don't have any Internet access on Ubuntu, you can save the output to a text file (Applications>Accessories>Text Editor) and copy it over to another computer using a USB key in order to post it here.

---

### Post by nkhaja on 2010-06-10
Thank you Pytheas22. 

My system is working fine now. I m able to connect both with wireless and wired.

---

### Post by Iowan on 2010-06-10
Did you do anything in particular to solve the problem - or did it just start working? 
IF problem is fixed, you can mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

