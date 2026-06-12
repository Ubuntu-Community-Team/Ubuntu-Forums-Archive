---
title: "New to Ubuntu, cannot connect to any internet"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by xrnc on 2010-03-10
Posting from my main computer:

Hello there, I just installed Ubuntu onto my secondary system, a laptop. I cannot seem to figure out how to connect to wireless at all, and even plugging a hardwire in and it doesn't do anything. I'm a complete newbie to this OS so if anybody could help it would be appreciated.

---

### Post by n0dix on 2010-03-10
Did you check NetworkManager tray icon, and select Auto eth0?

---

### Post by hoopoo on 2010-03-10
The same thing happen to me I installed ubuntu 9.10 no internet
then I tyred ubuntu 9.04 and got online.
9.10/9.04 don't have the same drivers.

keep trying you will get it going;)

---

### Post by xrnc on 2010-03-10
> **n0dix said:**
> Did you check NetworkManager tray icon, and select Auto eth0?

I clicked on it, and hit okay. Not sure if there is more to it, though.

---

### Post by xrnc on 2010-03-11
can nobody help me out? i can't even manage to revert back to xp because i accidentally chose to delete it.

---

### Post by mark bower on 2010-03-11
the biggest problem in migrating to Ubuntu (linux) is the hardware.  linux has native support for some drivers, this is best.  secondly, there is something called ndiswrapper which allows one to install and operate off of windows *.inf files.  and lastly, some hardware may never work.  when getting frustrated, blame the manufacturers who do not support hardware for linux as they do for windows.

keep bumping your post, ie, enter "bump" in a separate post.  eventually a guy named chili555 should pick you and try and help you thru the diagnostics which may identify your problem.  it is easier with wireless on a pc since wifi (PCI & USB) hardware can be swapped out.

mark

---

### Post by xrnc on 2010-03-11
fair enough

---

### Post by Naggobot on 2010-03-11
I suggest that you hook up the wire and run update manger. 

system->administration->updatemanager

After that see if you have proprietary drivers available, keep the wire attached while you do this. 

Alternatively boot from live cd with wired network attached and see if you get network. If you get consider reinstal with network attached. 

see my post on
[http://ubuntuforums.org/showthread.php?p=8953587#post8953587](http://ubuntuforums.org/showthread.php?p=8953587#post8953587)

---

### Post by xrnc on 2010-03-12
> **Naggobot said:**
> I suggest that you hook up the wire and run update manger. 

system->administration->updatemanager

After that see if you have proprietary drivers available, keep the wire attached while you do this. 

Alternatively boot from live cd with wired network attached and see if you get network. If you get consider reinstal with network attached. 

see my post on
[http://ubuntuforums.org/showthread.php?p=8953587#post8953587](http://ubuntuforums.org/showthread.php?p=8953587#post8953587)

It attempts to download it but because it doesn't have any internet it won't.... 

Wireless doesn't work, and NEITHER does the hardwire.

---

### Post by seenthelite on 2010-03-12
I have this same issue with the 9.10 installation on one of my Laptops a clean installation with wired connected results in no wired or wireless. But 9.04 and 10.04 work Okay. I have 9.10 installed on that box now and what I done was I found a USB ethernet adaptor,and connected this to the Laptop the adaptor was detected during the installation and then during the installation I received some updates and the latest kernel. When prompted to remove the installation disk and reboot I also removed the ethernet adaptor and connected the wire to the Laptop normally. When I rebooted the wired and wireless were there.
My cards are Atheros AR8131PCI-E for ethernet and Intel Wifi link 5100AGN for wireless.

---

