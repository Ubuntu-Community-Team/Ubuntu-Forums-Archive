---
title: "Installing broadcom driver from tar.gz in uberstudent"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by ltnemo2000 on 2012-05-23
When I installed uberstudent, my wireless wouldnt work
my first instinct was to try an ethernet and then run an update.
the ethernet is also not recognized.
so, i downloaded the driver from broadcom as a .tar.gz package
the thing is, now that i have the package, I'm stuck
I have limited coding experience
as i have no internet on my laptop, I can't show you what i get from lspci.

---

### Post by kc1di on 2012-05-23
first you need to untar the file.
Where did you download it to if you internet connection is not working?

if it's to a disk of somesort copy it to a folder in your home partition, Downloads works.

Then navigate to that folder and right click and select open with archive manager (or something like that)

once there click on extract 
When the file is extracted go to the new folder and read both the readme and install files if they are available they will tell you how to install the driver.  you will have to be in a terminal without x running 
believe you can get there by in a terminal typing ```
sudo stop lightdm
```

follow the instructions , 

Good luck

---

### Post by ltnemo2000 on 2012-05-23
I downloaded it from another computer and copied it from a flash drive.
I un-tar'd the file very next thing
after i did that, i have a folder "hybrid-portsc_x86_32-v5..."
inside there's a makefile and two folders but not a readme or any text other than license info anywhere to be found.

---

### Post by kc1di on 2012-05-23
> **ltnemo2000 said:**
> I downloaded it from another computer and copied it from a flash drive.
I un-tar'd the file very next thing
after i did that, i have a folder "hybrid-portsc_x86_32-v5..."
inside there's a makefile and two folders but not a readme or any text other than license info anywhere to be found.

you can download the users manual here.  think it will explain how to install.

[http://www.broadcom.com/support/ethernet_nic/netxtremeii.php]("http://www.broadcom.com/support/ethernet_nic/netxtremeii.php")

---

### Post by chili555 on 2012-05-23
Frankly, compiling a tar.gz from source without any internet connection is a very complex, involved process. For one thing, linux-headers and build-essential are required; no easy matter. I suggest we be certain of the driver needed before you proceed. Even then, it will be fast and easy with an ethernet connection. I suggest we troubleshoot the ethernet as well.> I can't show you what i get from lspci. I'm sorry, we need part of it even if you have to use a pencil. Please run:```
lspci -nn
```Look for the lines with 0200 and 0280 in them; we need the eight character pci.id from each. Here is an example from my computer:> <snip>
00:19.0 Ethernet controller [[COLOR="Red"]0200[/COLOR]]: Intel Corporation 82577LM Gigabit Network Connection [[COLOR="Red"]8086:10ea[/COLOR]] (rev 06)
<snip>
03:00.0 Network controller [[COLOR="Red"]0280[/COLOR]]: Intel Corporation Centrino Advanced-N 6200 [[COLOR="Red"]8086:4239[/COLOR]] (rev 35)
<snip>
Jot down those codes and post them before we turn ourselves inside out installing the *wrong* driver.

---

### Post by ltnemo2000 on 2012-05-24
ok. so here's what i got from tonight's coding.
I found the driver specific to my card AND the readme file
i followed the directions in the readme all the way through and found my card's serial number using lspci
when i finished there were two available drivers i could activate
when i tried to activate the proprietary STA driver, it BASH'd
I also tried the included ubuntu driver I noticed wasn't active
it too BASH'd
so now i'm stuck
thanks

---

