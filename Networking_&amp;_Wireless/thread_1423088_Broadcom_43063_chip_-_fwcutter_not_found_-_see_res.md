---
title: "Broadcom 4306/3 chip - fwcutter not found - see result in comment."
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by Captain_MDS on 2010-03-06
I did a full install of 9.10 on my Dell Inspirion 1200 laptop & use a Dell 1350 card, after several posts and replies I went to  [http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices) and followed the instructions for Ubuntu/Debian. This is the result I get....

mike@mike-laptop:~$ sudo apt-get install b43-fwcutter
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter
mike@mike-laptop:~$ 

I followed this procedure before installation (live CD) and it successfully found and installed the firmware. Apparently it was saved in live CD. What do I need to do?
Thanks,
Captain_MDS

---

### Post by bkratz on 2010-03-06
> **Captain_MDS said:**
> I did a full install of 9.10 on my Dell Inspirion 1200 laptop & use a Dell 1350 card, after several posts and replies I went to  [http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices) and followed the instructions for Ubuntu/Debian. This is the result I get....

mike@mike-laptop:~$ sudo apt-get install b43-fwcutter
[sudo] password for mike: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package b43-fwcutter
mike@mike-laptop:~$ 

I followed this procedure before installation (live CD) and it successfully found and installed the firmware. Apparently it was saved in live CD. What do I need to do?
Thanks,
Captain_MDS

didn't totally understand the posting. Did you get the b43-fwcutter installed? If so, you need to have a wired connection, reboot and follow what is shown here in the second section.

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Captain_MDS on 2010-03-06
No, I didn't get fwcutter installed, the screen shot posted above is what happened. fwcutter "not found". Like I said, I was able to download it using the "livecd" but it won't download after I did the install to my laptop. I really want to get wireless working as my first impression of Ubuntu is good.

---

