---
title: "Wireless File Transfer Speeds SAGA"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by pelmenept on 2009-07-10
I have been ubuntu user for more than 2 years already, and have no plans on coming back to windows. I have always loved the way linux offers the solutions to everyday tasks, but one "feature" is becoming more and more unbearable. My wireless transfer speeds on "N" network between two ubuntu machines never reach speeds higher than 1.3 megabytes a second.

 The hardware:
Desktop pc:
amd cpu,
Wireless "N" network card based on ralink chip, and with rt2860 driver, downloaded and compiled from ralink website.

Laptop:
Dell Inspiron 1400, Intel wireless card 54G.

Router:
Dlink dir-655.

Some tests:
I have tried to do a number of tests using file transfers (including big files and a lot of small ones) between theses two machines. Both machines connect wirelessly.

Using SAMBA and NFS sharing. I have been able to achieve speeds of 1.3 megabytes never faster, and in 70% of the time slower. Overall averages usually around 600 kbytes a sec. In order to be sure, I installed FTP server on one of the machines and repeated test - achieved speeds of 1.3 mbytes a sec again.

CONCERN:
First of all I realize network is operating in both modes (N and G, with wpa2), and surely speeds will never reach top values, also that wireless cards are different and in no way I will achieve "N" speeds. 

So. basically, I DO NOT THINK THAT 1.3 mbytes a sec is a good speed for internal wireless network. Using my Internet connection I am ALWAYS getting 1 mbytes a sec speeds.

At the end, if using your help I will be able to archive 40-50% speeds of 54G I will consider my goal is complete and my wireless network is as efficient as it can be. (so the speed of 2-3 mbytes a second will satisfy me) 

PLEASE:
- If you have same problem, but are not able to bring any valuable input do not post something like: "I have same problem, anyone?" or "Bump". Hopefully this will make this thread cleaner.
- On the other hand if YOUR wireless network is able to push 2-4 mbytes a second around, between two linux machines. (not both of them need to be connected wirelessly, but at least one, and not necessarily ubuntu) I ENCOURAGE YOU TO POST and share your experience.
- Do not post this: "This is how it is supposed to be, this speed is normal for Wireless network". THIS IS NOT TRUE. Once my friend came to me with his windows machine and was able to push HUGE amount of data to my samba server MUCH faster than I can with my ubuntu machine.
- Do not post this: "Your router sucks, try different ones". I have already done that. Tested with Linksys 54G ver 8, and DD-WRT installed on it. Interestingly but results are identical.
- Or this: "check your hard drive performance". - really.... ???

Otherwise your input is valued. I also think my problem may relate to a number of posts around the forum, mentioning slow SAMBA transfer speeds even on wired connections, something like 5 mbytes a second on 1 gigabit lan. Although I experience slow speeds with all protocols, I do not think other people tried with NFS and FTP. I bet they will be getting similar results. Which may lead to a conclusion of kernel bug on network module bug. 

I am also very surprised than there are not that many of similar posts, I just don't believe that little number of people are having similar issues, but believe they just keep quiet.

Hopefully this thread will help solve once and for all those network problems.

thank you.

---

### Post by cariboo on 2009-07-10
I'm running a mix of Jaunty and Karmic. With the two wireless device I use all the time, plus one I use for testing I never seem to get less than 2MB/sec transfer rates.

[list=1]
[*] Home built Media center pc atom cpu based, D-Link WUA-1340 - USB
[*] HP ze5400 with Prism 2.5 chipset
[*] Staples store brand, ZyDas zd1211 chipset - USB
[/list]

I have a Linksys wrt54GS in the house and a SMC Barricade converted to an access point in my shop average transfer rates between the three devices and any of the wired systems on the network is 2.6mbps

The only device I had to do anything for was the D-Link USB device. For some reason Jaunty network-manager sees it as unmanaged. I solved the problem by purging network-manager-gnome and installing gnome-network-admin

---

### Post by pelmenept on 2009-07-10
Thank you for the reply caribo.

After reading your post, i decided i will try to connect one of my machines using cable. So I was suspecting laptop. After connecting it to the router, I was able to transfer files from desktop (wireless) to now wired laptop at 5.5 to 7.5 mbytes per second speeds....wow. what an improvement.

But surely this setup will not work, and I need my laptop connnected wirelessly, and clearly the problem is in the driver or card.

on laprop I have intel 3945 i think, it is using iwl3945 driver. Any suggestions on what should I change it ?

thanks

---

### Post by anand on 2009-07-30
Is your computer with the RT2860 card actually connecting at ~300mbps?  I have a desktop that also has a RT2860 card and I can't get it to connect at anything over 54mbps in Jaunty.  Back when I had Windows on the machine, it'd connect at around 270mbps fine with the exact same card and router, so I think something in the Linux driver is holding it back.  You can use "iwconfig" from a shell window to see what speed it is connected at.

I never had any running using the Windows driver via ndiswrapper though, otherwise I'd go with that option.  54mbps is enough to saturate my Internet connection but it does slow down file transfers on my local network alot.

---

### Post by yossisynett on 2009-11-07
I'm experiencing similar problems. I've got two computers both running Ubuntu 9.10 (Karmic). On one I've got a Broadcom BCM4306 54 b/g. On the other I've got an Intel Wireless 2100 b card. I appreciate therefore that the max speed that I should be able to reach is 11 Mbits or 1.3 MBytes per second but the maximum speed I can actually reach is about 300 KBytes/s. Incidentally I see the same low speed why trying to transfer between either of the two linux machines and a windows box with a 54G wireless card in it that's also on my network. I've tried disabling IPV6 on the two linux boxes since I heard that this might cause a problem and in fact this did allow me to reach the max speed a lot faster. But nonetheless the max speed is still a quarter of what it should be.

My router is a Linksys WRT54G running openwrt firmware with a 2.4 kernel. I'm still waiting for the 2.6 kernel's Broadcom driver to be stable enough to work on my router since I'm hoping this might help but I doubt it.

---

