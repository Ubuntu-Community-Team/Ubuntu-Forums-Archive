---
title: "Can't connect to wireless network. Help!!!"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by mrs081608 on 2009-04-17
Hi
I just bought a Dell Inspiron 910 and it has a 802.11g mini card installed. I cannot connect to a wireless network and I am getting really frustrated. I am new to the whole wireless thing, so when I read through the forums for help I felt like I was reading a foreign language. I feel like I made a huge mistake purchasing a laptop with this operating system. Can anyone help me with this problem?
Thanks

---

### Post by Daisuke_Aramaki on 2009-04-17
> **mrs081608 said:**
> Hi
I just bought a Dell Inspiron 910 and it has a 802.11g mini card installed. I cannot connect to a wireless network and I am getting really frustrated. I am new to the whole wireless thing, so when I read through the forums for help I felt like I was reading a foreign language. I feel like I made a huge mistake purchasing a laptop with this operating system. Can anyone help me with this problem?
Thanks


is it a netbook? what wireless card does it have? 802.11g is the protocol. hope its not from broadcom. its woeful at best. anyway you need to find out what wireless card it comes with, execute the following command in a terminal and post the output here

```
lspci
```

---

### Post by mrs081608 on 2009-04-17
Ok, I ran the command and this is the output:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
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
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

---

### Post by Daisuke_Aramaki on 2009-04-17
> **mrs081608 said:**
> Ok, I ran the command and this is the output:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
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
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382
02:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
02:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
**03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)**
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

As suspected its from Broadcom. anyway refer this thread, there is a how to for broadcom 43xx series. but its a little bit outdated. So read through carefully.

[http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

Also have a look at linuxwireless page

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

Also look for Restricted Drivers listing under System->Preferences or Administration or something like that and click on Hardware Drivers and see if you can search for bcm4312 or something along those lines. But I think as per the first link i have provided, you can download the driver and build it as it is suggested.

---

### Post by dazedandconfused on 2009-04-17
Try this

[http://onlyubuntu.blogspot.com/2008/10/how-to-setup-broadcom-wireless-bcm4312.html](http://onlyubuntu.blogspot.com/2008/10/how-to-setup-broadcom-wireless-bcm4312.html)

---

### Post by carml on 2009-04-17
Ok man,if I'm not wrong the Broadcom card as others products is supported through the madwifi drivers,which are opensource,or through ndiswrapper and the driver for windows.Just make a search on Google for madwifi driver if you want to use those,because ath the moment I don't remember wher they are located.Maybe you can find something on System->Administration->Synaptic Package Manager looking for madwifi;or you can look on Google for the drivers for your wireless card and use those driver.
It's up to you,just tell me which ones you want to use and I'll try to assist you :).

---

### Post by mrs081608 on 2009-04-17
I tried everything that was posted here and I am more lost than ever!
Thank anyway

---

### Post by carml on 2009-04-17
Ok if you look for Broadcom wireless card on the net or you can look on a PC with Windows and Broadcom,you'll have at your hand the driver you need to use ndiswrapper.Just do what I'm suggesting you,because me too I use ndiswrapper to use my wireless card and I assure you it works well enough. :)

---

### Post by mrs081608 on 2009-04-17
I am very sorry, but I don't understand any of this. I tried googling it, but it keeps bringing back to these ubuntu forums that I can't understand a word of. I am ready to just call it quits and buy a new computer that does not have ubuntu.

---

### Post by carml on 2009-04-17
Ok I'll try to be more clear:look on Google for "Broadcom Corporation BCM4312" driver for Windows and download them.After you've done all,I'll say you the next passage to do. :)

---

### Post by mrs081608 on 2009-04-17
Ok, I downloaded the driver, but it still does not work.

---

### Post by carml on 2009-04-17
Now go to System->Administration->Synaptic package manager and look for ndiswrapper,you'll be prompted for your password,you have also to install all of them,you should find something similar to the screenshot below.
Right click on the little square and select "mark for installation".
Once you've done I'll tell you how to go on. :)

---

### Post by mrs081608 on 2009-04-17
OK, I did that part.

---

### Post by carml on 2009-04-17
Now:
1. first of all unzip to a handy place,such as your desktop,the driver you downloaded before;
2. go to System->Administration->Hardware Driver and disable the entry(if both) Hal and wireless support,then reboot,they should similar to the ones into the screenshot,with the difference that mine are already not in use;
3. once you logged in,go to System->Administration and look for the entry Windows wireless driver,it should be there if you installed those packages;
4. left click on Windows wireless driver,insert your password if requested;
5. left click on Install new driver and within that window look for a .inf file in the directory (or folder using Windows terminology) whose name is the name of your unzipped driver,then once you found it click on install.

If all is done correctly,you should be able to use your wireless card now. :)

---

### Post by mrs081608 on 2009-04-17
Could not find windows wireless driver.

---

### Post by carml on 2009-04-17
Did you install:
ndisgtk;
ndiswrapper-common;
ndiswrapper-utils?
If you go to System-Admnistration->Synaptic package manager you'll find all of them.

---

### Post by mrs081608 on 2009-04-17
I couldn't find ndisgtk. I did find the other two though.

---

### Post by carml on 2009-04-17
Look for it on Google,download and doubleclick on the .deb file to install.

---

### Post by mrs081608 on 2009-04-17
Thanks for all your help, but I give up. I am apparently not meant to use this operating system.

---

### Post by carml on 2009-04-17
No need to give up, we can perfom our task also without that package,ndisgtk it's only a gui to ndiswrapper itself,so if you unzipped the driver onto your desktop it will be a children play to go on. :)
If you don't it,unzip the driver to your desktop,don't give up there only one step to perform. :):)

---

### Post by mrs081608 on 2009-04-17
I don't even know how to unzip the driver to my desktop.

---

### Post by carml on 2009-04-17
Where did you downloaded it? If you use Firefox you can see where it stores your downloads by opening Firefox,going to the second entry in the menù,select Preferences Main.There you should notice an entry named Download and below that a entry named Save files on:there you'll find the file.Copy it to your desktop,then right click it and choose unzip here.
Once you've done I'll tell what to do next. :)

---

### Post by carml on 2009-04-17
In the case you'll com to this page again,just go to Applications->Accessories->Terminal then type ndiswrapper and follow the help you'll see,you should type ndiswrapper -i an type che correct path to the unzipped driver to install it,then press ENTER and you've all done. :)

---

### Post by mrs081608 on 2009-04-18
I tried that and I am still not having any luck. I have never been this frustrated before!

---

### Post by adm1968 on 2009-04-18
[I]Just a comment: the amount of people willing to help in this forum is simply stunning. I am sure many of us have felt as frustrated as you are now at some point before.
Don't give up, Linux may sometimes be tricky, but it pays to be patient. Good luck[/I]

---

