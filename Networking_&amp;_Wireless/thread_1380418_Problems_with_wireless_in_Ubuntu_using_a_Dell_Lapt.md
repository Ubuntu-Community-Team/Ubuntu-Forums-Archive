---
title: "Problems with wireless in Ubuntu using a Dell Laptop"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by RD2009 on 2010-01-13
Hi Folks,
 
I'm new to Ubuntu but from what I have seen so far I am impressed! However, I have just started using Ubuntu 9.10 on my Dell Inspiron 1545 laptop. It seems to run ok unti I want to use the internet - the problem is that I cannot access a wireless internet connection on the Ubuntu system (the main operating system on my laptop is Windows Vista and wireless internet works fine on this). When I connect via an ethernet cable using the same router I do get internet working in Ubuntu - so my question is why isn't it working when I want to set up a wireless internet connection? The details of my hardware/software are as follows;
 
I am using a Dell Inspiron 1545 laptop 
I am running Ubuntu 9.10
My router is a Belkin 54g wireless router
 
Thanks
 
Ron

---

### Post by bkratz on 2010-01-13
> **RD2009 said:**
> Hi Folks,
 
I'm new to Ubuntu but from what I have seen so far I am impressed! However, I have just started using Ubuntu 9.10 on my Dell Inspiron 1545 laptop. It seems to run ok unti I want to use the internet - the problem is that I cannot access a wireless internet connection on the Ubuntu system (the main operating system on my laptop is Windows Vista and wireless internet works fine on this). When I connect via an ethernet cable using the same router I do get internet working in Ubuntu - so my question is why isn't it working when I want to set up a wireless internet connection? The details of my hardware/software are as follows;
 
I am using a Dell Inspiron 1545 laptop 
I am running Ubuntu 9.10
My router is a Belkin 54g wireless router
 
Thanks
 
Ron



What we really need to know is the type of wireless card. A lot of Dells use a relabeled Broadcom.

Go to the terminal
Applications>>Accessories>>Terminal

and type in 

lspci

(that is LSPCI in lowercase)
copy/paste the output back here.

---

### Post by RD2009 on 2010-01-13
thanks.  Here is what I got;
 
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ubuntu@ubuntu:~$

---

### Post by bkratz on 2010-01-13
So it is the Atheros AR5001 which I know nothing about, but will some searching to see what I can find.

---

### Post by bkratz on 2010-01-13
Found a quick one that looks promising

[http://ubuntuforums.org/showthread.php?t=1379448&highlight=AR5001](http://ubuntuforums.org/showthread.php?t=1379448&highlight=AR5001)

Will look more

---

### Post by bkratz on 2010-01-13
Look at post 38 before you do anything with ndiswrapper.

[http://ubuntuforums.org/showthread.php?t=1309072&page=4](http://ubuntuforums.org/showthread.php?t=1309072&page=4)

The whole thread is pretty good and current

---

### Post by RD2009 on 2010-01-13
Thanks bkratz.  I'll see what I can come up with...

---

### Post by homeuser1 on 2010-01-13
Post the output of "rfkill list"

This is what it should look like. 

dell@dell-laptop:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

I used to have a "yes" on the hard block which was keeping my wireless from working.  I'm not exactly sure what I changed, but I did toggle back and forth on the wireless settings between Application and the [Fn/F2]/[Application] and Disable.  I'm not sure what it was on initially, but I put it on Application, saved and rebooted and now I'm back in business.  I also have the boot post on minimal.  I went back into bios and selected the [Fn/F2]/Application and I still have my wireless connection.  So, maybe just fiddling around with these settings unblocked something.  For whatever reason, I can't get a hard block back on anymore.  I have a dell-laptop D630.

UPDATE:
Well, it appears that editing the bios isn't what fix the above problem.  Restarting to get into the bios is what really changes the "hard blocked" from a yes to a no.  It appears my problem occurs when I close the laptop.  When I open it back up and log in, the wireless connection is disable.  Back to the drawing board for me.

UPDATE:
Well, just re-installed 9.04 and I now I can close and open my laptop and stay connected! Yeah!

---

