---
title: "Wireless Card seems to be missing Firmware"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by newcityboy on 2010-12-26
Prior Warning. I am brand spanking new to linux and this level if fiddling with CLI. I don't have access to wired internet, we borrow our net from our next door friends. I just installed 10.10 on my old Dell Insiron E1401. It has a Broadcom 4401 Chipset. I have been chewing on this problem for a few days and my wife finally told me to either ask for help or use fedora instead... (While in my shopping for which distro to use I tested Fedora and suse, but opted to install ubuntu because of the available support.... but after the installation I found that my wireless does not work. I have looked and looked for solutions and have tried every single on that I have come upon.
 
According to lshw -C network 
 
the wireless interface is DISABLED, but I have rebooted into Vista to see if the card is indeed on and it is, checked bios to for good measure and it is at factory default "ON" 
 
Logical name Wlan0
 
Serial 00:16:ce:6c:70:f1
 
Configuration: Broadcast=yes, Driver b43, driver version 2.6.35-22-generic, **Firmware=N/A** Link=yes, Multicast=yes, wireless=IEEE 802.11bg
 
ifconfig does not return me an IP
 
I am a well aware what NA means but the wireless icon on the main screen says that it is missing... I am just at a loss. I will continue to fight this thing to the best of my ability. Most of the solutions that I have come upon have been for the chipset 43xx and none of them have worked on my system. I think that might be why I have looked so long hoping that someone asked the same question as me. I do hate asking a question that someone else has just asked.

---

### Post by mikewhatever on 2010-12-26
Is BCM 4401 the wireless card you have? Search engines seem to thing it's an ethernet card, so I am confused.

---

### Post by amsterdamharu on 2010-12-26
Could you copy and paste the output of this command (you've run it before but didn't just paste the output here for us to have a look at.)

```
sudo lshw -C network
```

---

### Post by amsterdamharu on 2010-12-26
Someone with a simular problem:
[http://ubuntuforums.org/showthread.php?t=1650176](http://ubuntuforums.org/showthread.php?t=1650176)

The driver and firmware for Broadcom 43xx can be downloaded here:
[http://packages.ubuntu.com/maverick/kernel/firmware-b43-lpphy-installer](http://packages.ubuntu.com/maverick/kernel/firmware-b43-lpphy-installer)
The .deb file will try to download something during installation so no point in trying to install that unless you're connected to the internet by cable.
You could copy the deb to your Ubuntu and double click on it to see if it will give you the option to install. Dont install but see if it does give you the option. If it gives you the option it means that all other software needed for the driver is installed.

Next step is to download this file:
[http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)
Copy that to your desktop and run the following commands:
```
cd ~/Desktop
tar xjf broadcom-wl-4.178.10.4.tar.bz2
cd broadcom-wl-4.178.10.4/linux
sudo b43-fwcutter -w "/lib/firmware" wl_apsta.o
```

Then a reboot should do the trick.

---

### Post by newcityboy on 2010-12-26
```
siedentopf@ubuntu:~/Desktop$ tar xjf broadcom-wl-4.178.10.4.tar.bz2
siedentopf@ubuntu:~/Desktop$ cd broadcom-wl-4.178.10.4/linux
siedentopf@ubuntu:~/Desktop/broadcom-wl-4.178.10.4/linux$ 
sudo b43-fwcutter -w "/lib/firmware" wl_apsta.o
[sudo] password for siedentopf: 
sudo: b43-fwcutter: command not found
 

```
 
I had to load the bz2 package twice first time it told me it was corrupted. Second time through I got the command not found. Tried it a few times. I imagin I need to load a tool set of some sort but am not sure where to start.

---

### Post by amsterdamharu on 2010-12-26
Strange that the other person did not get that error. You have to install another package but you haven't mentioned what version of Ubuntu you use.

You can try downloading this package:
[http://packages.ubuntu.com/maverick/b43-fwcutter](http://packages.ubuntu.com/maverick/b43-fwcutter)
click on i386 if you have the maverick 386 version installed and on amd64 if you have the 64 version.

Copy that to your desktop, double click it and click install.

---

### Post by amsterdamharu on 2010-12-26
> The driver and firmware for Broadcom 43xx can be downloaded here:
[http://packages.ubuntu.com/maverick/...pphy-installer]("http://packages.ubuntu.com/maverick/kernel/firmware-b43-lpphy-installer")
The .deb file will try to download something during installation so no  point in trying to install that unless you're connected to the internet  by cable.
You could copy the deb to your Ubuntu and [COLOR=Red]double click on it to see if  it will give you the option to install. Dont install but see if it does  give you the option. [/COLOR]If it gives you the option it means that all other  software needed for the driver is installed.

If you'd done that you should not have the option to install since it depends on b43-fwcutter which is obviously missing from your machine and needs to be installed first.

---

### Post by newcityboy on 2010-12-26
MAv i386 is the version I am using. And I think that I had downloaded the incorrect version of fcutter. I am working on doing it now and it let me install it this time were as last time it didn't. 
 
Ok it ran fcutter and I am doing a reboot now. fingers crossed
 
I now have an established connection. Less than twentyfour hours later I am fixed. amsterdamharu you are great thanks for your help. Now I get to fiddle with it. I couldn't do anything before without the net.

---

### Post by swissman on 2010-12-26
I copied the downloaded package to my desktop, everything ran smoothly in terminal, after reboot, my wireless still could not detect any connections..... please help:sad:
i have hp 2745se, broadcom 4312/// with already activated STA wireless card in additional driver

---

### Post by amsterdamharu on 2010-12-26
swissman:
Can you post the output of the following commands?

```
cat /etc/lsb-release
sudo lshw -C network
```

Do you have a cable Internet available? That would make installing the drivers a lot easier.

---

### Post by IWantFroyo on 2010-12-26
LOL I had this problem.
You probably just need a driver.
System-Administration-Additional Drivers.
Wait...
It will show you some drivers, one of which will be something wireless related.
Now you have to get an Ethernet cable (I know, keep reading) and plug it into another computer. Set it up so the other computer shares the internet by cable, and press activate on the wireless driver. Unplug the Ethernet cable and watch your wifi card detect the networks!

---

### Post by JimmyJamez on 2011-01-05
Hey:  

I had this problem tonight installing 10.10 on my old Compaq laptop.  I'm a total noob to ubuntu.  Just as I was reading this thread the OS figured it out and installed the correct driver.  

Cool!  I'm totally impressed.  

J.

---

