---
title: "MA521 How to ndiswrapper for Newbs"
date: 2005-03-14
forum: Networking &amp; Wireless
---

### Post by speedy2782 on 2005-03-14
Alright, So you are new to linux and all of the forums and people that help you assume more than you know. Welcome to  the last 4 days of my life. But my MA521 does work with ubuntu and here is how.

Step #1. 
Download and extract the .zip file.
 From the [www.realtek.com.tw](www.realtek.com.tw) website. Search for rtl8180- as this is the name of  the driver for the chipset on your NETGEAR card. Download the windows xp driver. Filename should be ndis5x-8180.zip. Extract it into simply named folders like "wifi"

Step #2. 
Intall Ndiswrapper. 
 Either Synaptic Package Manger or using bash command #apt-get install ndiswrapper 

Step #3
In the directory you extracted your zip file using the root terminal #sudo ndiswrapper -i /dir/dir/driver/inf 
The dir represents the directory of where the files are located. for me it was
#sudo ndiswrapper -i /home/benjamin/wifi/here/NET8180.inf
Make sure that the name of the file is typed in exactly because it is case sensitive. 
Double check to see if it worked by 
#ndiswrapper -l
Should reveal the name of the driver, say it is present, and say the hardware is present if you have it in you pcmcia slot. If it says invalid driver! you need to ndiswrapper -e the driver and reload it making sure to use the right directory and case.

Step #4
#sudo ndiswrapper -m
this will let the ndiswrapper configure during start up so that your wifi is ready when you start up.

Step #5
#sudo modprobe ndiswrapper
This will tell linux to load the ndiswrapper drivers.

Step #6
#iwconfig
this will reveal your current network connections...wlan0 should show up with information pertaining to the IEEE and ESSID. You are mainly trying to see if wlan0 shows up.
 #ifconfig
This will show if you have connection to an AP (access point) and if you have an ip address. If there is a connection but no ip then run.
#iwconfig wlan0 essid <name of AP> 
This will tell the wlan0 to connect to a certain AP.
#dhclient wlan0
This will tell the wlan0 to search for ip addresses.
Once an ip address is found you are golden.

Let me know if this helps. If you have any other tips for newbs that I forgot (being that I am one) please help out and post any information you can.
Speedy

---

### Post by speedy2782 on 2005-03-14
For some more newb goodness!

Once you have configured your wlan0.

#ifdown eth0

#ifdown wlan0

#ifup wlan0

This will shut down your lan- or eth0
and it will restart your wireless connection and set you all ready. If it doesn't work. 
#dhclient wlan0

More to come...just wait till I try to get an IPOD to work.
Speedy

---

### Post by Mr Black on 2005-03-17
[QUOTE=speedy2782]
Step #2. 
Intall Ndiswrapper. 
 Either Synaptic Package Manger or using bash command #apt-get install ndiswrapper [/QUOTE]

When I tried to install the ndiswrapper via the apt-get command it tells me that the package can't be found.  Am I supposed to download this from somewhere or should it be in the system by default?

---

### Post by speedy2782 on 2005-03-18
You might try to use the synaptic package manager. If you repost the exact message it will help a little bit more. Let me know if that helps.
Ben

---

### Post by Mr Black on 2005-03-18
Yeah, I tried to use the GUI package manager thing but I don't get how it works.  It seems that it only allows you to install packages that you have already downloaded.  The whole issue is that I don't have a network connection thats why I need to get the wireless card working.  

Here is the output I get when running the apt-get command:

[SIZE=2][I]root@ubuntu:/home/jason/Applications/ndiswrapper-1.1 # apt-get install ndiswrapper
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package ndiswrapper[/I][/SIZE]

I'm guessing that you have to download the deb package from somewhere in order to get the thing installed via apt-get or the Synaptic thing.

I googled for ndiswrapper and got the sourceforge page for it.  I looked through that but couldn't find a deb package anywhere all I got was the source code.  So I figured I would just compile the code and be on my way, but I was wrong.  While trying to compile the code I got the following

[SIZE=2][I]root@ubuntu:/home/jason/Applications/ndiswrapper-1.1 # make
make -C driver
make[1]: Entering directory `/home/jason/Applications/ndiswrapper-1.1/driver'
Can't find kernel sources in /lib/modules/2.6.8.1-3-386/build;give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/jason/Applications/ndiswrapper-1.1/driver'
make: *** [all] Error 2[/I][/SIZE]

I'm guessing its having issue finiding the compiler or something.  I have never gotten this error before while running *make* so I don't know what to do. I ran through the documentation for installing the ndiswrapper that came with it but it just refers you to the sourceforge site.  I went there and all it says to do is run *make* and then *make install*.  I'm prety much at the end of my knowledge so any help would be great.

---

### Post by Mr Black on 2005-03-19
Ok, well after playing around with stuff and spending a few hours searching through all of the documentation on the internet about this I finally got it working.  There is an actual page on  [Ubuntu's website](https://www.ubuntulinux.org/support/documentation/howto/ndiswrapper)  that explains how to install ndiswrapper, and then a few people have posted updates on ways they did it.  I used the following way to get everything setup and running:

[I]I suggest this other way...
Posted by 3657 at 2004-12-23 10:15 AM
(Sorry for my basic English)

After examining the Makefile included in the original ndiswrapper-0.12.tar.gz package from ndiswrapper.sf.net, I found that is possible to build .deb packages simply typing "sudo make deb" in the source tree. Follow this steps:

a) Previously, install: build-essentials, fakeroot, linux-headers-2.6 (use Synaptic)

b) Grab the original "ndiswrapper-0.12.tar.gz" from ndiswrapper.sf.net. You could say: "If I can't access to the www, how could I..." yeah, that's right. The sources fit into a floppy or a USB stick, so you can grab it at the Cyber or any Internet access near to you.

c) As ROOT (sudo -s), copy the tar.gz file to /usr/src and : "tar zxvf ndiswrapper-0.12.tar.gz" Enter the directory: "cd ndiswrapper-0.12" and...

d) simply "make deb", the rest is auto. You can find the new home-made packages suited for your system in /usr/src. To install them, type "dpkg -i ndiswrapper*"

This should be redone everytime you upgrade your linux-image package.

See you soon. [/I]

I would just use the newest version, which happen to be 1.1 when I ran through the sourceforge site, instead of downloading the older version that they used in the example. 

Another note is that the *make deb* command should create two deb packages.  You need to install both.  So you can either type out the full name when running the *dpkg* command, and do it for each package, or use the wildcard.  Just make sure that the deb packages are the only  files that start with "ndiswrapper" in the directory.  I had a few other files that started with ndiswrapper and with out thinking I just typed *dpkg -i ndiswrapper** and then it tried to install the other files that weren't packages and it didn't like that.   Since my packages had a - as the next character I just added that before the wildcard (*).  So it was actually *dpkg -i ndiswrapper-**. 

Then I followed the steps below to actually configure ndiswrapper:
[I]
It's not that hard
Posted by 3858 at 2004-12-26 11:20 PM
This HOWTO ignores the nice Network Settings GUI. All you need to do is:

(1) Install ndiswrapper-utils with the Synaptic package manager
(2) Put in the CD with your Windows wireless adapter driver and find the desired .inf file
(3) Open a root terminal window and type "ndiswrapper -i /path/to/driver.inf" (putting in the right path)
(4) Type "modprobe ndiswrapper" and then "dmesg" to see if it worked
(5) Type "ndiswrapper -m" to set up autoloading of the module
(6) Click Computer/SystemConfiguration/Networking and add/configure the wireless connection[/I]

I didn't do step one cause I did it already.  Plus I still haven't figured out how to install local packages (i.e. something not downloaded via the utility) using the Synaptic thing.  I tried using the help in Ubuntu but its pretty limited and it only shows how to install a package thats already in the list.

Also, I didn't use the CD when settup ndiswrapper up cause I already had the newest driver on a USB key that I had downloaded earlier.  I would recommend using the newest driver you can get your hands on. 

After a few minutes of configuring: inputting the Hex version of my WEP Key  and adding my new MAC Address to the filter on my router I was up and running.

---

### Post by jayson23 on 2005-03-22
Thanks for the help - I finally got ndiswrapper to install my .inf file!

I have a Netgear MA521 (with a Realtek 8180 chipset), so I used the net8180.inf file that I got from Realtek, and now I'm getting some positive action: when I type "ndiswrapper -l", it reports "net8180 driver present, hardware present."

unfortunately, that's as far as I can get. "iwconfig" reports no wireless extensions, and I'm not sure where to go from here. I'm SERIOUSLY novice at Linux. I tried looking in the Networking system config in the GUI, but no luck.  Any advice?

---

### Post by Mr Black on 2005-03-23
jayson23, good to hear that you got ndiswrapper setup and working.  When you say that *iwconfig* reports no wireless extentions do you mean at all or just nothing for say eth0?  For example, when I run the command on my system it returns the following...

[SIZE=2][I]jason@ubuntu:~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"***************"
          Mode:Managed  Frequency:2.437GHz  Access Point: **:**:**:**:**:**
          Bit Rate:54Mb/s   Tx-Power:20 dBm   Sensitivity=-120 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:99/100  Signal level:-57 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2130  Invalid misc:1593   Missed beacon:0[/I][/SIZE]

Notice how I have a wlan0 extenstion. Ndiswrapper should have created a new extension for the wireless card when you installed the driver.  If you could post the response you get when entering in the command it always helps.  

I'm guessing since you don't see any wireless extensions that when you go into Computer->System Configuration->Networking GUI you don't get anything in the drop down list while trying to add a new wireless connection right? See attached image screenshot.png to see what I get on my system.  

If you don't have that showing up in the Networking settings then I guess you should double check to make sure you followed every step.  I would also make sure you ran the *modprobe ndiswrapper* command.  That is what inserts  ndiswrapper into the kernel so the system can use it.  

You might also want to try to assign the driver to your actual wireless card manually.  To do this you will need the device ID and driver name.  Then pass them to ndiswrapper. You already have the driver name from using the *ndiswrapper -l* command.  I belive yours was "net8180".  To find the ID of the device first run the *lspci* command.

[SIZE=2][I]jason@ubuntu:~ $ lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS 645xx (rev 51)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
**0000:00:0d.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)**
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) (rev 01)[/I][/SIZE]

Locate your wireless card in the mess of devices that it shoots back.  I bolded mine, but yours will be different cause its a different model.  Make note of the preceeding number and rev code (you will need these to identify it later).  Then run the command again but with the *-n* arguement. 

[SIZE=2][I]jason@ubuntu:~ $ lspci -n
0000:00:00.0 Class 0600: 1039:0648 (rev 51)
0000:00:01.0 Class 0604: 1039:0003
0000:00:02.0 Class 0601: 1039:0963 (rev 25)
0000:00:02.1 Class 0c05: 1039:0016
0000:00:02.5 Class 0101: 1039:5513
0000:00:02.7 Class 0401: 1039:7012 (rev a0)
0000:00:03.0 Class 0c03: 1039:7001 (rev 0f)
0000:00:03.1 Class 0c03: 1039:7001 (rev 0f)
0000:00:03.3 Class 0c03: 1039:7002
0000:00:04.0 Class 0200: 1039:0900 (rev 91)
**0000:00:0d.0 Class 0280: [COLOR=DarkOrange]1814:0201[/COLOR] (rev 01)**
0000:01:00.0 Class 0300: 1002:5961 (rev 01)
0000:01:00.1 Class 0380: 1002:5941 (rev 01)[/I][/SIZE]

Locate the card again using the info from the first time you ran the command.  Then take note of the ID number that comes after the Class ID and before the rev code. I've bolded and highlighted mine in the output above.  This is what you will have to pass to ndiswrapper when assigning the driver. 

Now run the following command: *ndiswrapper -d deviceID driverName* to have ndiswrapper apply the driver to the device.

[SIZE=2][I]jason@ubuntu:~ $ ndiswrapper -d 1814:0201 rt2500
ln: `/etc/ndiswrapper/rt2500/1814:0201.5.conf': File exists
Driver 'rt2500' is used for '1814:0201'[/I][/SIZE]

Your output may look a little different based on whether or not the device is mapped to the driver. Hopefully you can get it working, but if not just post your results and I'll try to help as much as I can.

---

### Post by [pl]ice on 2005-08-29
thnx, 1st time i used ndiswrapper, worked with ma521, but one thing, use the correct drivers ;) i tried with shipped on cd with the card, no use!. funny
bie

---

### Post by newbie9123 on 2006-02-15
I was going nuts until I figured this out.

After locating the proper driver for your wireless card, you have to extract *both* the .inf and the .cat files ... If you only extract the .inf file you will get 'invalid driver'. Over and over again. 

The two files in my case (Linksys WPC54g on ubuntu 5.10) were lsbcmnds.inf and lsbcmnds.cat.

---

### Post by Jakanden on 2006-02-28
I cannot get mine installed because it tells me invalid driver and when I run ndiswrapper -e it tells me not installed and to run ndiswrapper -l /sigh

---

### Post by brimbleshoes on 2006-04-27
> Then I followed the steps below to actually configure ndiswrapper: [I] It's not that hard Posted by 3858 at 2004-12-26 11:20 PM This HOWTO ignores the nice Network Settings GUI. All you need to do is: 
(1) Install ndiswrapper-utils with the Synaptic package manager 
(2) Put in the CD with your Windows wireless adapter driver and find the desired .inf file 
(3) Open a root terminal window and type "ndiswrapper -i /path/to/driver.inf" (putting in the right path) 
(4) Type "modprobe ndiswrapper" and then "dmesg" to see if it worked 
(5) Type "ndiswrapper -m" to set up autoloading of the module 
(6) Click Computer/SystemConfiguration/Networking and add/configure the wireless connection[/I] 

Also, I didn't use the CD when settup ndiswrapper up cause I already had the newest driver on a USB key that I had downloaded earlier. I would recommend using the newest driver you can get your hands on. After a few minutes of configuring: inputting the Hex version of my WEP Key and adding my new MAC Address to the filter on my router I was up and running. 

as root on console be sure to type "modprobe ndiswrapper" then use iwconfig if you want...or  try "kdesu kcontrol" (see below)

Step 6 might be different for some... in kubuntu KDE, go to run command on the K menu and type "kdesu kcontrol" to run as root, go to internet/network --> network settings and configue the wlan0

This worked for me! I have a RealTek 8180 TrendNet wifi card, Breezy, and used the NDIS8180.INF file. Also I used the ndiswrapper from the Breezy install CD. 

I cheered out loud when it worked! I think this is the first Linux forum that has been... well...helpful. 

I love (k)ubuntu Linux! What a great forum. 

If anyone has this wifi card, it does work. I'm a newb, and I got it to work! Now on to getting Eclipse on this box! 

many thanks...

---

### Post by gamma-alpha on 2006-08-31
Hey all,

I followed the instructions above, but my MA521 card (hardware) still isn't detected, though the driver is.  Any ideas?  Would be sincerley appreciated by this newbit!

---

