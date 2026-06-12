---
title: "cannot get online"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by stef-l on 2009-10-26
Running 9.04, browser = opera 10.  Have installed a new wireless router this morning (BT HOmeHub2, replacing BiPAC 5200G).  Windows works fine connecting wirelessly to the internet but ubuntu will not work.  Network Manager has not been available for a long time (since upgrade from 8.10 I think).  Have followed several posts advising on how to install/ reinstall it but to no avail.  So in ubuntu I have no connection and cannot download anything!  The two little monitor icons have always had a red cross.  Tick says ntweorking and wireless are enabled, but connection information says 'no valid connections found' and edit connections doesn't offer a dialogue box at all.

I'm trying really hard to stick with linux but this is sorely trying me I've spent 3 hours so far to no avail, so any help will be appreciated.  Is there any way to try & connect using commands in terminal so I can be online, & then perhaps someone could tell me how to get network manager back and take me from there?

---

### Post by t0mppa on 2009-10-27
Ok, if you can see the icon with the two little monitors, then Network Manager is there. What is more likely to be happening here is that you're having some driver issues. So, why don't you open up a terminal and run **lshw -C network** for starters to give us an idea of what we're dealing with.

---

### Post by stef-l on 2009-10-27
Now the little computer icons have disappeared!  I don't know what I did that made them vanish.  Have tried moving the router to near the computer so that I can connect with an ethernet cable but this hasn't made any difference, ie no connection makes itself.  

Have also tried to do an upgrade to 9.10 via a cdrom on the grounds that this might give me an OS with Network Manager, but the upgrade did not work - the upgrade couldn't read all the files it wanted on the cd.

Have checked in windows device manager and all the cards are working ok; they worked fine with the old router.  

Am having to send messages in windows and then have to reboot to linux to try things out!  But suggestions are appreciated and I will try everything.

Will respond to your request for info but obviously cannot copy a linux readout to a windows email

Thanks

stef-l

---

### Post by t0mppa on 2009-10-27
> **stef-l said:**
> Will respond to your request for info but obviously cannot copy a linux readout to a windows email

In that case you can run **lshw -C network > network.txt**, which will save the output to a file named *network.txt*. After that you can mount one of your Windows partitions and copy it over to be able to access it in Windows easily.

---

### Post by stef-l on 2009-10-27
Hello!  I think this is what you asked me to send:

root@stef:/home/steflewicki# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 90
       serial: 00:0b:6a:a1:92:08
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=32 link=no maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: wlan0
       version: 00
       serial: 00:60:b3:1c:9e:46
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=32 module=acx multicast=yes wireless=IEEE 802.11b+/g+
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:15:47:5d:11:1a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Thanks

---

### Post by t0mppa on 2009-10-27
Ok, looks like everything is in order there. Your wireless chip appears to be a little old though and the newest information (which is a couple of years old, so no idea if it's reliable) I could find about it suggests that you'd need to remove Network Manager and/or to install some firmware for it to work (see the driver [Wiki page]("http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu") and the Ubuntu [help page]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111") for more info).

Anyway, you can test if your wireless can pick up wireless networks by running **sudo iwlist scan**. If it does, you can try creating a connection [manually]("http://ubuntuforums.org/showthread.php?t=571188").

The wired connection should be a bit easier to troubleshoot. See if you can get a connection by [manually editing the configuration files]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html") and then restarting networking with **sudo /etc/init.d/networking restart**.

If you can get neither one to work, then run **dmesg** from the terminal and post it here, in case it has some clues for what's going wrong.

---

### Post by stef-l on 2009-10-31
Have been away, sorry.  Major problems mean total reinstall of everything on my desktop.  Now have clean dual boot of Windows XP and Ubuntu 9.10.  Still able to get online in XP and not in Ubuntu.  Still need help.  I'm finding it very frustrating.

There is now a NM icon.  I have ticked 'enable networking'  I have entered details in 'network connections' buit there is no connection.  This means I cannot try out any of the suggestions I've found in other forums.iwconfig says 'no wireless extensions'

lshw -C network says the network is 'unclaimed'

I'd be very grateful for help setting up the connection.  I have this weekend to sort everything out and then I'm back at work and just likely to give up

Thanks

---

### Post by normanp on 2009-10-31
> **stef-l said:**
> Have been away, sorry.  Major problems mean total reinstall of everything on my desktop.  Now have clean dual boot of Windows XP and Ubuntu 9.10.  Still able to get online in XP and not in Ubuntu.  Still need help.  I'm finding it very frustrating.

There is now a NM icon.  I have ticked 'enable networking'  I have entered details in 'network connections' buit there is no connection.  This means I cannot try out any of the suggestions I've found in other forums.iwconfig says 'no wireless extensions'

lshw -C network says the network is 'unclaimed'

I'd be very grateful for help setting up the connection.  I have this weekend to sort everything out and then I'm back at work and just likely to give up

Thanks

You might have been better off with 9.04 judging by posts here (still seems available at [http://releases.ubuntu.com/releases/9.04/](http://releases.ubuntu.com/releases/9.04/))

---

### Post by t0mppa on 2009-10-31
Ok, unclaimed means that it's not getting associated with a driver. Check **lsmod | grep acx_pci** to see if the driver module is loaded. If you get no output, it wasn't found and you can try doing **sudo modprobe acx_pci**. If the driver has been left behind from the Karmic kernels though, then things get a bit more complicated as you'll have to download and build it yourself.

Since I don't have this card myself, I'm afraid I don't know all the intrinsics, but can help with the general steps to take. Also, [this thread]("http://ubuntuforums.org/showthread.php?t=324148") on the tips & tutorials forum seems to be a possible alternative solution.

---

### Post by stef-l on 2009-10-31
well it looks like I'm stuffed - FATAL: module acx_pci not found.  I have managed, temporarily, to make a wired ethernet connection, if that will help.  I'm not terribly confident with complicated linux instructions but am willing to try

Thanks

---

### Post by t0mppa on 2009-10-31
Then it sounds like the driver was cut out of Karmic. And of course I forgot to post the link to the [build instructions]("http://acx100.sourceforge.net/wiki/ACX"). Looking at the contents, not sure if it's any simpler than NDISwrapper route described in the other thread.

---

### Post by stef-l on 2009-10-31
Right - I tried the thread you gave me a link to, but this produced errors after a few stages.  I tried as far as I thought it was worth, but as you can see from the  terminal log, I failed.

stef@stef-desktop:~$ sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.8
[sudo] password for stef: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "ndiswrapper-utils-1.8"
Couldn't find any package whose name or description matched "ndiswrapper-utils-1.8"
The following NEW packages will be installed:
  ndiswrapper-common 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.7kB of archives. After unpacking 98.3kB will be used.
Writing extended state information... Done
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main ndiswrapper-common 1.54-2ubuntu1 [21.7kB]
Fetched 21.7kB in 0s (25.2kB/s)         
Selecting previously deselected package ndiswrapper-common.
(Reading database ... 114723 files and directories currently installed.)
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.54-2ubuntu1_all.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.54-2ubuntu1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

stef@stef-desktop:~$ cd
stef@stef-desktop:~$ mkdir linksys
stef@stef-desktop:~$ cd linksys
stef@stef-desktop:~/linksys$ wget [http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip](http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip)
--2009-10-31 19:10:42--  [http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip](http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip)
Resolving downloads.linksysbycisco.com... 213.120.161.203, 213.120.161.195
Connecting to downloads.linksysbycisco.com|213.120.161.203|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19045881 (18M) [application/zip]
Saving to: `wpc54gv2_driver_utility_v2.02.zip'

100%[======================================>] 19,045,881   764K/s   in 25s     

2009-10-31 19:11:07 (751 KB/s) - `wpc54gv2_driver_utility_v2.02.zip' saved [19045881/19045881]

stef@stef-desktop:~/linksys$ unzip wpc54g_v2_driver_utility_v2.0.zip
unzip:  cannot find or open wpc54g_v2_driver_utility_v2.0.zip, wpc54g_v2_driver_utility_v2.0.zip.zip or wpc54g_v2_driver_utility_v2.0.zip.ZIP.
stef@stef-desktop:~/linksys$ 
stef@stef-desktop:~/linksys$ unzip wpc54g_v2_driver_utility_v2.0.zip
unzip:  cannot find or open wpc54g_v2_driver_utility_v2.0.zip, wpc54g_v2_driver_utility_v2.0.zip.zip or wpc54g_v2_driver_utility_v2.0.zip.ZIP.
stef@stef-desktop:~/linksys$ mv tnet1130.sys TNET1130.sys
mv: cannot stat `tnet1130.sys': No such file or directory
stef@stef-desktop:~/linksys$ sed -e 's/tnet1130.sys/TNET1130.sys/' LSTINDS.INF > LSTINDS.new&& mv LSTINDS.new LSTINDS.INF
sed: can't read LSTINDS.INF: No such file or directory
stef@stef-desktop:~/linksys$ sudo ndiswrapper -i lsbcmnds.inf
Error: ndiswrapper-utils-1.9 not installed!
stef@stef-desktop:~/linksys$ sudo ndiswrapper -i LSTINDS.INF
Error: ndiswrapper-utils-1.9 not installed!
stef@stef-desktop:~/linksys$ sudo modprobe ndiswrapper
stef@stef-desktop:~/linksys$ wget [http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip](http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip)
--2009-10-31 19:13:49--  [http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip](http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip)
Resolving downloads.linksysbycisco.com... 213.120.161.195, 213.120.161.203
Connecting to downloads.linksysbycisco.com|213.120.161.195|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19045881 (18M) [application/zip]
Saving to: `wpc54gv2_driver_utility_v2.02.zip.1'

100%[======================================>] 19,045,881   824K/s   in 23s     

2009-10-31 19:14:12 (821 KB/s) - `wpc54gv2_driver_utility_v2.02.zip.1' saved [19045881/19045881]

stef@stef-desktop:~/linksys$ wget [http://downloads.linksysbycisco.com/downloads/wpc54g_driver_utility.zip](http://downloads.linksysbycisco.com/downloads/wpc54g_driver_utility.zip)
--2009-10-31 19:15:26--  [http://downloads.linksysbycisco.com/downloads/wpc54g_driver_utility.zip](http://downloads.linksysbycisco.com/downloads/wpc54g_driver_utility.zip)
Resolving downloads.linksysbycisco.com... 213.120.161.203, 213.120.161.195
Connecting to downloads.linksysbycisco.com|213.120.161.203|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-10-31 19:15:27 ERROR 404: Not Found.

stef@stef-desktop:~/linksys$ sudo ndiswrapper -i lsbcmnds.inf
Error: ndiswrapper-utils-1.9 not installed!
stef@stef-desktop:~/linksys$ sudo ndiswrapper -i LSTINDS.INF
Error: ndiswrapper-utils-1.9 not installed!
stef@stef-desktop:~/linksys$ sudo modprobe ndiswrapper
stef@stef-desktop:~/linksys$ sudo aptitude install ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
The following NEW packages will be installed:
  ndiswrapper-utils-1.9 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.5kB of archives. After unpacking 127kB will be used.
Writing extended state information... Done
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main ndiswrapper-utils-1.9 1.54-2ubuntu1 [36.5kB]
Fetched 36.5kB in 0s (74.9kB/s)            
Selecting previously deselected package ndiswrapper-utils-1.9.
(Reading database ... 114734 files and directories currently installed.)
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up ndiswrapper-utils-1.9 (1.54-2ubuntu1) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

stef@stef-desktop:~/linksys$ cd
stef@stef-desktop:~$ mkdir linksys
mkdir: cannot create directory `linksys': File exists
stef@stef-desktop:~$ cd linksyswget [http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip](http://downloads.linksysbycisco.com/downloads/wpc54gv2_driver_utility_v2.02.zip)
bash: cd: linksyswget: No such file or directory
stef@stef-desktop:~$ unzip wpc54g_v2_driver_utility_v2.0.zip
unzip:  cannot find or open wpc54g_v2_driver_utility_v2.0.zip, wpc54g_v2_driver_utility_v2.0.zip.zip or wpc54g_v2_driver_utility_v2.0.zip.ZIP.
stef@stef-desktop:~$ mv tnet1130.sys TNET1130.sys
mv: cannot stat `tnet1130.sys': No such file or directory
stef@stef-desktop:~$ sed -e 's/tnet1130.sys/TNET1130.sys/' LSTINDS.INF > LSTINDS.new&& mv LSTINDS.new LSTINDS.INF
sed: can't read LSTINDS.INF: No such file or directory
stef@stef-desktop:~$ sudo ndiswrapper -i lsbcmnds.inf
couldn't open lsbcmnds.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
stef@stef-desktop:~$ sudo ndiswrapper -i LSTINDS.INF
couldn't open LSTINDS.INF: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
stef@stef-desktop:~$ sudo modprobe ndiswrapperecho "ndiswrapper" | sudo tee -a /etc/modules
FATAL: Module ndiswrapperecho not found.
stef@stef-desktop:~$ 

The build instructions are far too complicated for me to fathom, I'm afraid.  I imagine the best move would just be to buy a more up to date card which would be supported?  Does this make sense, and if so, what should I look for?

Thanks

---

### Post by stef-l on 2009-10-31
Have just noticed that the linksys files that it claims cannot be found when downloaded seem to have appeared in my homefolder.  Is that right, and if so is there any way of telling the installer in the terminal that they are there? if that makes sense

stef-l

---

### Post by t0mppa on 2009-11-01
> **stef-l said:**
> 
2009-10-31 19:11:07 (751 KB/s) - `wpc54gv2_driver_utility_v2.0[COLOR="Red"]2[/COLOR].zip' saved [19045881/19045881]

stef@stef-desktop:~/linksys$ unzip wpc54g_v2_driver_utility_v2.0.zip
unzip:  cannot find or open wpc54g_v2_driver_utility_v2.0.zip, wpc54g_v2_driver_utility_v2.0.zip.zip or wpc54g_v2_driver_utility_v2.0.zip.ZIP.

You just mistyped the file name a bit, see that missing 2. On the terminal you can use tab whenever typing file names and it will automatically fill in the rest, once there are no other possibilities. So, just type a few letters in and then try tab, if it doesn't fill up, then type a bit further and so on. That way you always know you'll have the file name right, when the system fills in the rest for you.

> **stef-l said:**
> The build instructions are far too complicated for me to fathom, I'm afraid.  I imagine the best move would just be to buy a more up to date card which would be supported?  Does this make sense, and if so, what should I look for?

Thanks

Yeah, the terminal commands can be a bit intimidating for people not accustomed to using command line, but they are really fairly simple once you get used to them. And buying a new card is one viable course of action, should be able to catch one fairly cheap these days. Most of the new cards work out of the box these days on Linux.

The trouble with choosing one is that there are fewer chip manufacturers than card manufacturers and the latter usually don't state anywhere which chip they used for their card. And the chip used is the only relevant info, as that's what determines which drivers support it. [Ubuntu Wiki]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") provides a list of manufacturers that you can use to check the cards your local vendor is offering against. Atheros, Intel and Broadcom chipsets are the most common and thus ones that you're bound to find help on the forums for, should some trouble arise.

---

### Post by fabiodasoghe on 2009-11-15
If this can still help, there's a post about compiling the driver yourself that doesn't seem too much complicated: [http://ubuntuforums.org/showthread.php?t=1321303&highlight=acx+100+karmic](http://ubuntuforums.org/showthread.php?t=1321303&highlight=acx+100+karmic)

I'm going to try it myself, I'll tell if it worked (I'm not a Linux guru).

Cheers,

Fabio

---

