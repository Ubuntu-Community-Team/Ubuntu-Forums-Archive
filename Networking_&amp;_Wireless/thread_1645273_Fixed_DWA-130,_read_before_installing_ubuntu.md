---
title: "Fixed DWA-130, read before installing ubuntu"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by ShootEmUp on 2010-12-14
[Original Thread Here]("http://ubuntuforums.org/showthread.php?t=1645262")

First off the DWA-130 XP (vista and 7 drivers do not work with ndiswrapper) 64bit drivers are NOT compatible with 64bit Ubuntu (stupid D-link), You have to do a 32bit install to use ndiswrapper with this.

Step 1. Install Ubuntu, Read elsewhere for help with this
Step 2. Get ndiswrapper [Read Here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installation")> 2.1. Installing Packages (With Internet access on the Ubuntu computer)
If you already have Internet access via some other method while logged into Ubuntu:

1. Ensure the multiverse and universe repositories are enabled; see AddingRepositoriesHowto

2. Install the ndisgtk package from the Ubuntu repositories.

sudo apt-get install ndisgtk
If you don't know how to install applications then you can read this guide.

2.2. Installing Packages (With Internet access on another computer)
Download the files below according to the release you have:

2.2.1. Currently Supported Releases
For 10.04 Lucid Lynx
[http://packages.ubuntu.com/lucid/misc/ndiswrapper-common](http://packages.ubuntu.com/lucid/misc/ndiswrapper-common)
[http://packages.ubuntu.com/lucid/ndiswrapper-utils-1.9](http://packages.ubuntu.com/lucid/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/lucid/ndisgtk](http://packages.ubuntu.com/lucid/ndisgtk)
For 9.10 Karmic Koala
[http://packages.ubuntu.com/karmic/misc/ndiswrapper-common](http://packages.ubuntu.com/karmic/misc/ndiswrapper-common)
[http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/karmic/net/ndisgtk](http://packages.ubuntu.com/karmic/net/ndisgtk)
For 9.04 Jaunty Jackalope
[http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common)
[http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/jaunty/net/ndisgtk](http://packages.ubuntu.com/jaunty/net/ndisgtk)
For 8.10 Intrepid Ibex
[http://packages.ubuntu.com/intrepid/misc/ndiswrapper-common](http://packages.ubuntu.com/intrepid/misc/ndiswrapper-common)
[http://packages.ubuntu.com/intrepid/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/intrepid/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/intrepid/net/ndisgtk](http://packages.ubuntu.com/intrepid/net/ndisgtk)
For 8.04 Hardy Heron
[http://packages.ubuntu.com/hardy/misc/ndiswrapper-common](http://packages.ubuntu.com/hardy/misc/ndiswrapper-common)
[http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/hardy/net/ndisgtk](http://packages.ubuntu.com/hardy/net/ndisgtk)
For 6.06 Dapper Drake
[http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils)
[http://packages.ubuntu.com/dapper/net/ndisgtk](http://packages.ubuntu.com/dapper/net/ndisgtk)
 For advanced users: There is a known bug in these Debian packages, detailed in this thread. If you are having issues after installing from these packages, the kernel module may not have installed, so you may get the error FATAL: Module ndiswrapper not found when you run modprobe ndiswrapper in the terminal. To avoid this problem, it's best to compile from the source available at [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/). This is fairly simple but requires the build-essential package to be installed. You can install this offline using apt-cdrom from the command line or the synaptic package manager with the ubuntu install CD.

Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order:


sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils-*.deb
sudo dpkg -i ndisgtk_*.deb
 The commands listed above are a general example of how to install a .deb package from the command line. You need to be in the directory where the files were copied to. If you are new to the terminal, consider reading BasicCommands.

2.3. Installing Packages (Without Internet access)
Without an Internet connection, you can still install ndiswrapper-utils from the Desktop CD. If you installed from that, the repository in which ndiswrapper-utils is found is on the CD, but not within the live session. You need to boot into your new Ubuntu installation and then reinsert the Desktop CD. You will be asked if you want to add the packages on the CD to your list of repositories.
If you installed using the Dapper Alternate CD, those packages except ndisgtk are included on it.

Put the CD into the drive, click System > Administration > Synaptic Package Manager and search for ndis. If you don't know how to install applications, read this guide.

Step 3. Blacklist other wireless drivers
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
Add these lines to /etc/modprobe.d/blacklist

```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist r8192s_usb
```

Reboot

Step 4. Download DWA-130 windows drivers
[Download Here]("http://www.dlink.com/products/default.aspx?pid=DWA-130&tab=3")
I personally had revE, download your revisions drivers (don't worry, it's a zip file)
Extract, look inside for the XP/2000 32bit drivers (should be WinXP2000, if not don't worry)

Step 5. Install drivers via ndiswrapper
Go to System-Administration-Windows Wireless Drivers
Click "Install New Driver", select the XP/2000 32bit drivers (from where you extracted them at)
Click Install

Step 6. Connect to internet
Now if Gnome network manager has detected your wireless, you should be able to just connect at this point
If not Reboot

Step 7. Enjoy!

Problems: None that I know of yet, let me know If you do

Hope this helps!

Feedback
> **bkratz said:**
> I have been using the DWA 130 for several years. Mine is the version A. There are actually five versions available, some of which actually have a Linux driver available on the D-Link website and ndiswrapper would not be needed. The user should verify which version he/she has before proceeding. I did not have to blacklist any drivers at all.

Thank you for your feedback, I say to blacklist the drivers because they can interfere (not always, but can) with ndiswrapper.
And yes revC has linux drivers available (sorry forgot to mention it).

---

### Post by bkratz on 2010-12-14
I have been using the DWA 130 for several years. Mine is the version A. There are actually five versions available, some of which actually have a Linux driver available on the D-Link website and ndiswrapper would not be needed. The user should verify which version he/she has before proceeding. I did not have to blacklist any drivers at all.

---

### Post by ShootEmUp on 2010-12-14
> **bkratz said:**
> I have been using the DWA 130 for several years. Mine is the version A. There are actually five versions available, some of which actually have a Linux driver available on the D-Link website and ndiswrapper would not be needed. The user should verify which version he/she has before proceeding. I did not have to blacklist any drivers at all.

Thank you for your feedback, I say to blacklist the drivers because they can interfere (not always, but can) with ndiswrapper.
And yes revC has linux drivers available (sorry forgot to mention it).

---

### Post by dbrannon79 on 2011-01-08
> **ShootEmUp said:**
> Thank you for your feedback, I say to blacklist the drivers because they can interfere (not always, but can) with ndiswrapper.
And yes revC has linux drivers available (sorry forgot to mention it).


I have the Dlink DWA-130 rev E, following your steps and the only thing I can tell is that under "Windows Wireless Drivers" it shows hardware present.  but does not show up any networks in the wireless manager.  I am using a Acer Travelmate 5720 laptop. any ideas?

Thanks

---

### Post by ShootEmUp on 2011-01-10
> **dbrannon79 said:**
> I have the Dlink DWA-130 rev E, following your steps and the only thing I can tell is that under "Windows Wireless Drivers" it shows hardware present. but does not show up any networks in the wireless manager. I am using a Acer Travelmate 5720 laptop. any ideas?
 
Thanks
 
dbrannon79, check your drivers to make sure they are XP 32bit drivers, also be sure to blacklist all the drivers listed above. Remember I couldn't get it working on 64bit (didn't try much, so you still might be able to make it work), so make sure your running 32bit. You might want to get on the IRC channels, here [https://wiki.ubuntu.com/IRC/ChannelList](https://wiki.ubuntu.com/IRC/ChannelList).
It also seems that you have built in wireless on your laptop. you may want to try it first.

---

### Post by pavchag on 2011-02-21
Please help, I have been following these instructions and
the wireless adapter seems to be showing up in the network
manager and my home wifi network also, but i can not connect 
to the network.
Thanks

---

### Post by bkratz on 2011-02-21
what type of encryption are you using?  I did have to make sure mine was WPA2/AES (only) not mixed mode to make mine work.

---

### Post by gambekar on 2011-02-25
Hey I'm stil having trouble connecting to the internet even though I followed the instructions above. It show that my hardware is present in the Windows Wireless Drivers screen. I installed the XP 32-bit driver and it still won't let me connect to any of the wi-fi networks in my house. They both have WPA & WPA2 encryption. 

Please help.

Thanks

---

### Post by Alek86 on 2011-02-25
Hi
I am brand new to ubuntu and I have been trying to get this working.  I am looking for a little clarification.  I have done my best to follow the instructions and I still cannot find the wireless network.  Do you mean that the dwa-130 will not work with the 64 version of ubuntu os and that I have to use the 32 version of the os to use this device?  
Thanks

---

### Post by mdwy62 on 2011-03-14
ndiswrapper and the winxp driver worked for me without blacklisting to get 802.11g performance. I could not get it to operate under the 802.11n protocol, despite have a dlink n router.

---

### Post by JSchultheis on 2011-09-19
> **bkratz said:**
> I have been using the DWA 130 for several years. Mine is the version A. There are actually five versions available, some of which actually have a Linux driver available on the D-Link website and ndiswrapper would not be needed. The user should verify which version he/she has before proceeding. I did not have to blacklist any drivers at all.

Hello! ):P

I have DWA-130, seems to be version A1, (Marvell W8360USB, USB-ID 07d1:3b11) and seem to be stuck.

In the download from Dlink website link that ShootEmUp posted, for the version (that would be 'A'), I find only a setup.exe file.
In the download for the "DWA-130_REVE", I find several folders, each contain various files and drivers. 

I think I am at the point that my solution will be to find the proper '.inf' file, then install it for my DWA-130 to work.


```
jeremy@poslaptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 07d1:3b11 D-Link System DWA-130 802.11n Wireless N Adapter(rev.A1) [Marvell W8360USB]
Bus 001 Device 002: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jeremy@poslaptop:~$  
```

Also, I can't seem to find any linux files on the Dlink website.
Wat do? :KS


PS: I am dual boot with XP and have complete access to all Windows files; can I just copy it over? Where from?:-k

---

### Post by bkratz on 2011-09-19
> **JSchultheis said:**
> Hello! ):P

I have DWA-130, seems to be version A1, (Marvell W8360USB, USB-ID 07d1:3b11) and seem to be stuck.

In the download from Dlink website link that ShootEmUp posted, for the version (that would be 'A'), I find only a setup.exe file.
In the download for the "DWA-130_REVE", I find several folders, each contain various files and drivers. 

I think I am at the point that my solution will be to find the proper '.inf' file, then install it for my DWA-130 to work.


```
jeremy@poslaptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 07d1:3b11 D-Link System DWA-130 802.11n Wireless N Adapter(rev.A1) [Marvell W8360USB]
Bus 001 Device 002: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
jeremy@poslaptop:~$  
```Also, I can't seem to find any linux files on the Dlink website.
Wat do? :KS


PS: I am dual boot with XP and have complete access to all Windows files; can I just copy it over? Where from?:-k


sorry, but heading out to work right now, but will help later, if needed.  I used ndiswrapper and the inf and sys files attached to the PM I am about to send you. These are 32 bit versions from xp.

---

### Post by JSchultheis on 2011-09-19
Update:
I created a folder on the Desktop named Dlink, loaded with two files: mrvw245.inf and MRVW245.sys
In terminal: ```
cd Desktop/Dlink
``` then ```
$ sudo ndiswrapper -i mrvw245.inf
```I think it said something like "installed", I have since rebooted and don't remember the exact wording... :panywho:

```
lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=DarkRed]Bus 001 Device 003: ID 07d1:3b11 D-Link System DWA-130 802.11n Wireless N Adapter(rev.A1) [Marvell W8360USB][/COLOR]
Bus 001 Device 002: ID 0930:6544 Toshiba Corp. Kingston DataTraveler 2.0 Stick (2GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
ndiswrapper -l
[COLOR=DarkRed]mrvw245 : driver installed
    device (07D1:3B11) present[/COLOR]
``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
``````
sudo dhclient wlan0
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device

```So it appears that I have installed the driver... but what now?

---

### Post by JSchultheis on 2011-09-22
bump?

---

### Post by bkratz on 2011-09-23
> **JSchultheis said:**
> bump?



here is a good ndiswrapper tutorial. Ndisgtk makes things easy.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by JSchultheis on 2011-09-23
Thank you bkratz.

I will follow that trail and do the best that I can.

---

### Post by JSchultheis on 2011-09-23
Somehow, by following that link, I finally got to the point where I had:
System> Administration> Windows Wireless Drivers
(I mainly got there by clicking the 'mirrors', then double clicking the downloaded files, one at a time)

From there, with 'Windows Wireless Drivers' window open, which is actually titled "Wireless Network Drivers", the mrvw245 file was listed. I highlighted that file and hit 'remove driver'.

I then clicked install driver, navigated over to the folder in which I had put both the .inf file and .sys file, and selected the .inf file.

At that point the little light on the stick started to flash!\\:D/ 

I disconnected the ethernet, and selected the triangle in the top status bar. It showed me a list of wireless networks. From there I found my own, entered the regular ol' info, and I was on my way!!  


Thanks for sticking with me bkratz. Hopefully I can pass on some help too!
Plus 2 beans to you my friend! :biggrin:

---

