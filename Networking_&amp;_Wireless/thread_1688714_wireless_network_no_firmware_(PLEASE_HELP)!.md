---
title: "wireless network no firmware (PLEASE HELP)!"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by heathmc on 2011-02-15
hey, i have an old dell d505 i put ubuntu on a usb and booted it up but i cant connect to wireless networks. 
i can connect to a wired network
i tried system-admin-addisonial driver
but nothing
please help asap!
thanks
ps i am BRAND new to ubuntu so please layman terms and step by step thanks

---

### Post by heathmc on 2011-02-15
hey, i have an old dell d505 i put ubuntu on a usb and booted it up but i cant connect to wireless networks. 
i can connect to a wired network
i tried system-admin-addisonial driver
but nothing
please help asap!
thanks
ps i am BRAND new to ubuntu so please layman terms and step by step thanks

---

### Post by TBABill on 2011-02-15
Please open terminal....go to Applications>Accessories>Terminal and type in ```
lspci
``` That's "LSPCI" in lowercase. When it returns its results, just paste it back here so we can see what type card you are working with. Then we can troubleshoot from there and possibly need you to take some more steps to provide additional information.

---

### Post by heathmc on 2011-02-15
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
01:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

-----------------------------------------------------------------------------------------------------------------------------
that is what i got

---

### Post by TBABill on 2011-02-15
Ok, when you went to SYSTEM>>ADMINISTRATION>>ADDITIONAL DRIVERS, were you connected via ethernet? If not, can you connect and run all updates first? Then go to terminal again and enter ```
sudo apt-get install b43-fwcutter
```AFTER you do that, then go to System>>Administration>>Additional Drivers and select the b43 driver, click through the prompts then restart and see if it works.

Edit: your wireless card is a Broadcom BCM4306 and it uses the b43 driver. The steps above get the firmware installed, then the driver installed. One thing you may need to do if you get an error trying to get the firmware is enable non-free repositories. You can open Synaptic, then click settings/repositories and enable the non-free repos so you can get the firmware. You may not need to do this...just give it a shot and see how it goes first.

---

### Post by heathmc on 2011-02-15
i followed your step and when i went to system admin add drivers it still said no porpitary drivers 
and what did you mean by "updates" i did go to tremial and enter something lie sudo apt-get updates earlier today....

---

### Post by TBABill on 2011-02-15
Ok, probably easier to just stick to the terminal for now. ```
sudo apt-get update && sudo apt-get upgrade
``` After that, just ```
sudo apt-get install b43-fwcutter
``` After that is done, then can you go see if it shows any drivers available? Is your wireless device turned on?

---

### Post by Mariane on 2011-02-15
How are you trying to connect to the wireless? 

I have always found wifi-radar a good help. You can install it by typing: 

```

sudo apt-get install wifi-radar

```

And then if you can't find it in the menus launch it by typing: 

```

sudo wifi-radar

```

I hope it helps

Mariane

---

### Post by heathmc on 2011-02-15
i did what you said but still nothing, during the update it said that their some errors but it continued it asked me to restart so i did.... i am currently just running it should i install it then try or what?

---

### Post by SoftwareExplorer on 2011-02-16
What happens if you try running, in a terminal 
```
sudo apt-get install firmware-b43-installer
```
and then restarting (assuming it doesn't give you errors)?
You'll need to be connected to the internet, maybe with a Ethernet cable.

---

### Post by heathmc on 2011-02-17
hey, i am currently away from my laptop so i can't run anything yet, i will post my results asap. also if this works will i be able to delete xp and install ubuntu as my only os without doing all this over again?

---

### Post by TBABill on 2011-02-17
If you do an install, then format your hard drive to reinstall Ubuntu then you will have to do it again. You'll probably find it necessary to do a similar configuration on any distro you install that does not have the Broadcom driver already available on the disk to work out of the box.
 
Here's an easy way if you already plan to wipe the drive and start over. Personally I'd keep XP just in case I need it in the future, but that's a personal thing. What you can do is install 10.10 and its installer asks if you want to install non-free things during installation. Click that block and it should do the rest for you so you don't have to do all this.

---

### Post by heathmc on 2011-02-18
softwareexplorer, here is what i got when i did what you said
ubuntu@ubuntu:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer
ubuntu@ubuntu:~$

---

### Post by SoftwareExplorer on 2011-02-19
You probably don't have the software source (repository as it is called) with that package enabled. 

To enable it, go to System > Administration > Update Manager. 
In the lower left corner, there will be a Settings button (click it).
In the window that comes up, click the Ubuntu software Tab.
Check the Software restricted by copyright or legal issues (multiverse).
Click Close. 
You will be asked if you want to reload the software list. Click reload.

Now try running the command that I told you before and it should try to download and install the firmware.

---

### Post by heathmc on 2011-02-20
hey, i have a dell d505 i have the b43 wireless driver installed and activated but it still says "firmware missing" why?
thanks

---

### Post by thefasterblueone on 2011-02-20
post results.

```
sudo lshw -C network
```

---

### Post by heathmc on 2011-02-20
hey, i got it to work, and i connected to my network but i can't get online? any ideas?

---

### Post by lisati on 2011-02-20
Threads merged

---

