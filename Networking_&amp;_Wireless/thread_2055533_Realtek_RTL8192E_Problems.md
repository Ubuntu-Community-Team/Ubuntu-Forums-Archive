---
title: "Realtek RTL8192E Problems"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by logepoge1 on 2012-09-09
I have a pci card that has a realtek RTL8192E chip. I am sure this has been posted before, but those solutions DO NOT work for mine. I am running Ubuntu 12.04 on a Dell Optiplex GX520 Desktop Computer. There is a 20gb partition for ubuntu and a 50gb partition for windows. I DO NOT USE GRUB. I use the motherboard's boot selector because I honestly dont like grub(sorry). This is the first time I have posted so just tell me what commands I need to run and I will run them and post the output. Currently the only way for me to get internet on this is to share my laptops connection through an ethernet cable. I want wireless on this. NDISWRAPPER shows that the driver is installed and the hardware is detected. So why wont it work. i am new to Unix and Ubuntu. Thanks

---

### Post by logepoge1 on 2012-09-09
Anyone?

---

### Post by logepoge1 on 2012-09-11
bumper

---

### Post by varunendra on 2012-09-12
Ndiswrapper is usually the last resort. According to [this post]("http://ubuntuforums.org/showthread.php?p=11898078"), the native kernel driver can handle the RTL8192E card.

Assuming this is true, I would suggest to remove ndiwrapper and follow the above post to try the native kernel drivers first. If that does not help, then you may follow any of these solved threads:
[http://ubuntuforums.org/showthread.php?t=1606676](http://ubuntuforums.org/showthread.php?t=1606676)
[http://ubuntuforums.org/showthread.php?t=1689148](http://ubuntuforums.org/showthread.php?t=1689148)

Or post back here if having problems following above solutions.

**PS !**
I may or may not be able to reply soon. In that case, if you need further guidance, chili555 (the original troubleshooter in the above two threads) would be your best friend.

---

### Post by Bucky Ball on 2012-09-12
Welcome.

Yea, scrap ndiswrapper. That is largely superseded. Avoid at all costs; can be very problematic and clumsy workaround. 

Sounds like you've imagined this is harder than it is and have read an old how to. This card should work out of the box. Trouble is, with ndiswrapper installed, might take a while to unravel what is already done. The native driver and ndiswrapper's web won't work at the same time, if you can get ndiswrapper working that is.

Usual course of action: plug in an ethernet cable and get your updates. Card should be detected and working after that. That's it. 

Try this: Plug in a cable and get your updates. Check in 'Additional Drivers' (used to be in System>Administration>Additional drivers; I use Xubuntu, not familiar with Unity at all, could be Hardware Drivers). Is there a driver for your card but disabled? You are going to need to uninstall ndiswrapper and disable/blacklist any drivers it has installed to get the native driver working.

---

### Post by remoteconcern on 2012-09-13
Hello. I am also experiencing this problem. 

I'm brand new to Linux, but installed Ubuntu 12.04 yesterday. After a lot of research, I've concluded that the native driver provided leads to serious instabilities with the wifi.

The majority of help threads out there deal with older versions with old versions of the linux kernel, and seem to have good success compiling drivers and installing them that way. However, this doesn't work.

As of now, I haven't found any solution (ndiswrapper didn't  work either, although I understand its not recommended) and I have reverted back to Windows. 

Seems like the wifi card is really problematic.

---

### Post by logepoge1 on 2012-09-21
Ok here is what I am going to do. I am going to remove the pci card. Install Ubuntu 12.04 again(already reformatted that partition) and then I will try the updates through ethernet, then of course plug the card in. Does that sound ok?

---

### Post by Bucky Ball on 2012-09-21
Not sure what your thinking is here.

---

