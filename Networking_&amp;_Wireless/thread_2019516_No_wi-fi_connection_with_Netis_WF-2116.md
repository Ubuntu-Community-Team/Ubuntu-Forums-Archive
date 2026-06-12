---
title: "No wi-fi connection with Netis WF-2116"
date: 2012-07-07
forum: Networking &amp; Wireless
---

### Post by Randymanme on 2012-07-07
> **haqking said:**
> drivers and guides here [http://www.netis-systems.com/download.asp?pdtid=142](http://www.netis-systems.com/download.asp?pdtid=142)

Hello,  
  

  I went to the link and got WF-2116_Linux.rar, but I have no idea how to install it.  I have a hard enough time trying to install tar balls as it is (sometimes I do get them installed  more or less by accident).  But this tar ball is a situation where there is at least one  tar ball inside of a tar ball.  Will someone take me by the hand and direct me step-by-step what to do?
  

  My most viable options are a.) return this adapter to the retailer and exchange it for one that does work with Linux right out of the box, or b.)  take my computer and adapter to the Build-Your-Own-Computer section of the store, and ask someone there to install  WF-2116_Linux.rar and while they're at it, show me how to do it also.
  

  I've been hanging around various Linux forums too long to not  remedy this situation at my own keyboard.  Even if I'm getting the directions from someone else.
  

  I downloaded the .rar package with Windows and tried to install it with Precise (after using Precise to fetch it out of Windows), Precise won't open a .rar out of the box.  I've tried opening and extracting it with Windows and then fetching the folders with Precise, but I still wasn't able to compile.
  

  I could go on and on about a couple of other things I've tried (as a result of googling).
  

  I've done a lot of googling trying to arrive at a solution to my problem.  Oh!  I need to tell you what the problem is.  About a week ago, I purchased a Netis WF-2116 wi-fi adapter.  But it only connects Windows, not Linux.  [Actually, it initially (even using the installation disk) just barely connected Windows (i.e.  just the first and smallest bar of the wireless icon).   
  

  Since I only use Windows when I really have to (like now), I've tried different combinations of  Windows installations.  The one I like best is to have Windows as a guest on Virtualbox with Linux as host.  I had hoped that I could connect a Windows guest to the wi-fi adapter, but that didn't work.   
  

  Another combination of Linux-Windows I've tried is Linux as guest on virtual machine with Windows hosting.  So I just happened to have an Ubuntu (Natty) derivative (Ultimate Edition Oz Unity 2  Onyx 64) as a guest on Virtualbox for occasions when I have to use Windows.  So I fired up Virtualbox and Onyx 64.  Lo and behold,  Onyx 64 connected to the wi-fi network – 100 percent.  And not only that, but when Onyx 64 came in !00 percent, Windows also shot up to 100 percent.
  

   I've floundered around google and landed at [https://launchpad.net/ubuntu/+source/linux-meta/3.2.0.18.18](https://launchpad.net/ubuntu/+source/linux-meta/3.2.0.18.18), and “linux-backports-modules-cw-3.3-precise-generic” binary package in Ubuntu Precise amd64, and [linux-backports-modules-cw-3.3-precise-generic_3.2.0.23.25_amd64.deb]("http://launchpadlibrarian.net/101224352/linux-backports-modules-cw-3.3-precise-generic_3.2.0.23.25_amd64.deb") to no avail.
  

  At one point I made a liveUSB with Startup Disk Creator of Ultimate Edition 3.2 (with persistence file).  I found by google, “new fedora virtio-win-0.1-22.iso drive (february 2012),”  at [http://alt.fedoraproject.org/pub/alt...st/images/bin/]("http://alt.fedoraproject.org/pub/alt/virtio-win/latest/images/bin/")  (courtesy of **[spirit]("http://forum.proxmox.com/members/2793-spirit?")** 
  [IMG]http://forum.proxmox.com/images/statusicon/user-offline.png[/IMG] Senior Member, at  [http://forum.proxmox.com/threads/8540-new-fedora-virtio-win-0-1-22-iso-drive-%28february-2012%29](http://forum.proxmox.com/threads/8540-new-fedora-virtio-win-0-1-22-iso-drive-%28february-2012%29)).  Downloaded, and burned it to a CD, put the CD in the DVD drive after booting Ultimate Edition 3.2 on liveUSB, so that I could present some windows wireless drivers to the Windows Wireless Drivers app for installation.  
  

  Well there appears to be at least hundreds, if not thousands, of them.  And I have no clue what to select.
  I'll be googling that while awaiting a hoped for response.
  

  Any and all help will be much appreciated.  Thanks.

---

### Post by chili555 on 2012-07-07
Wow. There is a whole lot of information there! The first thing is that the file extracts to a driver for rtl8192cu devices. In Ubuntu 12.04, it is already covered by installed drivers. Before we turn ourselves inside out compiling what we probably already have, let's see what exactly you have. Please insert the device and run and post:```
lsusb
lsmod | grep 8192
dmesg | grep 8192
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Randymanme on 2012-07-07
Thank you very much.

randymanme@randymanme-EL1358G:~$ lsusb  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 003: ID 046d:08c9 Logitech, Inc. QuickCam Ultra Vision  
 Bus 001 Device 004: ID 0bda:8178 Realtek Semiconductor Corp.  
 Bus 001 Device 005: ID 1a40:0201 Terminus Technology Inc. Hub  
 Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical  
 randymanme@randymanme-EL1358G:~$ lsmod | grep 8192  
 rtl8192cu             103297  0  
 rtl8192c_common        75767  1 rtl8192cu  
 rtlwifi               111202  1 rtl8192cu  
 mac80211              506816  3 rtl8192cu,rtl8192c_common,rtlwifi  
 randymanme@randymanme-EL1358G:~$ dmesg | grep 8192  
 [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88019fc00000 s83072 r8192 d23424 u524288  
 [    0.000000] pcpu-alloc: s83072 r8192 d23424 u524288 alloc=1*2097152  
 [   24.378741] rtl8192cu: MAC address: 08:10:76:2c:57:f9  
 [   24.378747] rtl8192cu: Board Type 0  
 [   24.397116] usbcore: registered new interface driver rtl8192cu  
 [   25.867255] rtl8192cu: MAC auto ON okay!  
 [   25.901150] rtl8192cu: Tx queue select: 0x05  
 [   25.902292] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin  
 [   25.970078] vesafb: mode is 2048x1536x32, linelength=8192, pages=0  
 randymanme@randymanme-EL1358G:~$

---

### Post by chili555 on 2012-07-07
> ID [COLOR="Red"]0bda:8178[/COLOR] Realtek Semiconductor Corp. And, as we expected:> $ lsmod | grep 8192
[COLOR="Red"]rtl8192cu[/COLOR] 103297 0
rtl8192c_common 75767 1 rtl8192cu
rtlwifi 111202 1 rtl8192cu
mac80211 506816 3 rtl8192cu,rtl8192c_common,rtlwifi And it finds and loads the needed firmware:> rtl8192c_common: Loading firmware file rtlwifi/rtl8192cufw.bin And does it create a wireless interface, wlan0 perhaps?```
iwconfig
```Does it scan and see your network?```
sudo iwlist wlan0 scan
```When you click the Network Manager icon, does it see your network? Does it connect?

---

### Post by Randymanme on 2012-07-07
> **chili555 said:**
> And, as we expected:And it finds and loads the needed firmware:And does it create a wireless interface, wlan0 perhaps?```
iwconfig
```Does it scan and see your network?```
sudo iwlist wlan0 scan
```When you click the Network Manager icon, does it see your network? Does it connect?

Thank You.

randymanme@randymanme-EL1358G:~$ iwconfig  
 wlan2     IEEE 802.11bgn  ESSID:off/any   
           Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr=2347 B   Fragment thr:off  
           Power Management:off  
            
 lo        no wireless extensions.  
 


 eth0      no wireless extensions.  
 


 randymanme@randymanme-EL1358G:~$ sudo iwlist wlan0 scan  
 [sudo] password for randymanme:  
 wlan0     Interface doesn't support scanning.  
 


 randymanme@randymanme-EL1358G:~$  
 ---------------------------------------------------------------------

When I click on the network manager?  One of three things happen depending on which OS I'm on.  With Windows, the indicator light blinks (which I take to mean that it's connected and transmitting).  With Precise, the light comes on, but does not blink (which I take to mean that a connection is almost there, but not quite -- so, yes, it does see the network).  

With Linux Mint Debian Edition 201204, the network manager gui does list the three neartest and strongest wi-fi networks, but the indicator light never comes on (I interpret that to mean that it sees the networks, but cannot possibly connect so no effort made).  With Pinguy 12.04 (as well as with several live CDs I've tried, like Linux Mint 13 Maya Xfce, Sabyon 5.3, OpenSuse 12.1 Gnome, etc.), the indicator light doesn't come on nor does it list any networks -- completely dead.

Whatever day it was, earlier this week, when the storm tore through Central Ohio (where I'm at) and 11 other states, it tore up a lot of property, trees, fixtures, et al.  Tens of thousands of persons are still without electric power here.  Internet sevices for me and most folks in my area just got back on yesterday.  But during the four days it was out, I could connect to several networks, as they were (more like the router signals), but without actually connecting to a DNS server.  Empty signals.  

So what I describe happens when I click on the network manager icons happened during the internet outage as well, except for one instance: a Linux Mint 13 Maya Cinnamon live CD did connect. But hasn't again.

Thank you for your responses and for the information  along with them.

---

### Post by chili555 on 2012-07-07
> randymanme@randymanme-EL1358G:~$ iwconfig
[COLOR="Red"]wlan2 [/COLOR]IEEE 802.11bgn ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm
Retry long limit:7 RTS thr=2347 B Fragment thrff
Power Managementff
Errmm, let's see:```
sudo iwlist wlan[COLOR="Red"]2[/COLOR] scan
```What it does in Windows is unimportant; we're trying to fix Ubuntu.> (I interpret that to mean that it sees the networks, but cannot possibly connect so no effort made). You will not know until you make the effort. I interpret the lack of a light as some drivers implement the light correctly and some don't. Some drivers light the light, some blink the light and some do nothing. If you see networks, click yours and see if you are challenged for an encryption password.

If you are attempting to connect with Ubuntu, let's concentrate our efforts and diagnostics there, please.

It is unusual to have wlan2 instead of wlan0. I assume you've had or have other wireless devices present. Yes?> With Precise, the light comes on, but does not blink (which I take to mean that a connection is almost there, but not quite -- so, yes, it does see the network).Click on it and connect, please!!!

---

### Post by Randymanme on 2012-07-08
[SIZE=2]> **chili555 said:**
> Errmm, let's see:```
sudo iwlist wlan[COLOR=#ff0000]2[/COLOR] scan
```What it does in Windows is unimportant; we're trying to fix Ubuntu. [/SIZE] 
 

 [SIZE=2]Sorry about that.  I was assuming that that extraneous info might provide some insight to someone who might be familiar with more than one (or all) the OSes I commented on. I recall reading a thread in which both Pinguy and Clem posted.  Texstar responded to one of my threads in another forum.  I never know who all might be browsing in their spare time looking to help some noobie like me.  But, of course, since this is Ubuntu Forums, I'll concentrate on Precise.[/SIZE]
 

 [SIZE=2]> **Randymanme said:**
>  . . . the network manager gui does list the three neartest and strongest wi-fi networks, but the indicator light never comes on (I interpret that to mean that it sees the networks, but cannot possibly connect so no effort made)[/SIZE]
 

 [SIZE=2]> **chili555 said:**
> Errmm, let's see:```
sudo iwlist wlan[COLOR=#ff0000]2[/COLOR] scan
```You will not know until you make the effort. [/SIZE]
 

 [SIZE=2]Sorry about the way I phrased that.  I was talking about the network manager gui “not responding” as programmed – not to myself.  With Precise, when I click on the network manager icon, a box pops out with nine headings, some grayed-out and some not grayed-out.  Of the nine selections, the first two, “Wired Network disconnected” and “Wireless Networks disconnected” are grayed-out as is the eighth one.[/SIZE]  By " . . . no effort made . . .,"  I mean that when the box pops out, [SIZE=2]“Wired Network disconnected” may be the only of the headings not grayed-out, with everything pertaining to wireless disabled.[/SIZE]
 

 [SIZE=2]Since I believe in the probability of the evolution of silicon-based intelligence, I sometimes allude to computers or apps as though they might have some form of  sentience.  [Wouldn't it be nice to have a Cameron Phillips?][/SIZE]
 

 [SIZE=2]> **chili555 said:**
> Errmm, let's see:```
sudo iwlist wlan[COLOR=#ff0000]2[/COLOR] scan
```I interpret the lack of a light as some drivers implement the light correctly and some don't. Some drivers light the light, some blink the light and some do nothing.
[/SIZE]
 

 [SIZE=2]Thank you for that information (in response to some of my extraneous information).  It'll come to my mind in some other context, and may be useful.[/SIZE]
 

 [SIZE=2]> **chili555 said:**
> Errmm, let's see:```
sudo iwlist wlan[COLOR=#ff0000]2[/COLOR] scan
```It is unusual to have wlan2 instead of wlan0. I assume you've had or have other wireless devices present[/SIZE]
 

 [SIZE=2]Yes; this Netis is the third wireless adapter I've had in as many weeks.  First, I bought a Tenda 322U with a data transfer rate of  300MB/s.  It worked with all my OSes right out of the box; but never at more than 35 percent signal strength.  And the signal would sometimes fade in and out – which wasn't good for downloading large files, like, say, updating a fresh install.[/SIZE]
 

 [SIZE=2]So I perused the retailer's inventory online and decided on what I wanted to get to replace the Tenda.  But when I got to the store, what I wanted to get wasn't actually on the shelf.   So I settled for something else for a little more money that had an antenna.  I don't remember the exact name, but I think it was a Hawking, 150 MB/s.  So when I got home, the antenna was missing out of the box.  I plugged it in anyway and ran the software, but nothing happened.[/SIZE]
 

 [SIZE=2]I surmised that I need to have an adapter with at least 300 MB/s; probably and preferably a PCI card at 450 MB/s – which I was planning on getting when I returned the Hawking.  To tell you the truth, outside of the facts that this one has a data transfer rate of 300 MB/s and was $10 cheaper, I bought this one instead  because it *looks *more capable than the previous ones I've had. (Yes, I know about deceptive looks).[/SIZE]
 

 [SIZE=2]> **chili555 said:**
> Errmm,If you see networks, click yours and see if you are challenged for an encryption password.. Yes? Click on it and connect, please!!! [/SIZE] 
 

 [SIZE=2]Hhhmmm, I suppose this is enlightening in a backhanded sort of way -- to find out how dumb I must look on these here forums.  [/SIZE] 
 

 [SIZE=2]Of course I click on my network and give the encryption password and click on “connect.”  How else would I have connected with Black Opal on Virtualbox, or have connected to wi-fi networks with four other Linux OSes with the Tenda adapter?  And when I click on the network manager icon and then click on the 4th heading, “Create New Wireless Network . . .,”  I type in the SSID, then click the Wireless Security tab and type in the encryption phrase.  Then when I click the “Create” button, the network manager icon shows movement to (I've always assumed) indicate that there's computing going on.[/SIZE]
 

 [SIZE=2]Where I'm living, this is an apartment complex with free wi-fi (there is a router in each building).  Each building is a network; the name of the apartment complex coupled with each building's  chronological number is each network's SSID.  The street coupled with the address of the building is the encryption phrase.  [/SIZE] 
 

 [SIZE=2]So I've connected with several other buildings in addition to my own, both with my computer as well as with my Android.  And with my Android, I've connected with business networks all down the street.  And, yes, with the Android, you do have to touch the “connect” button before the smartphone will connect to a wi-fi network.[/SIZE]
 

 [SIZE=2]*Trust me on this: not clicking my network and then not clicking the connect button are definitely not the problems here.*[/SIZE]
 

 [SIZE=2]But, still, thank you for your trouble-shooting, brain-storming, and suggestions.  Thank You for your time and consideration.  You're appreciated – even if you do think I'm too dumb to click “connect.”[/SIZE]
 

 [SIZE=2]Cheers  
[/SIZE]

---

### Post by Randymanme on 2012-07-08
Good morning,

I apologize for getting a little short with you over the 
click-on-the-button suggestion.

I just read [http://ubuntuforums.org/showthread.php?t=2011852&page=4](http://ubuntuforums.org/showthread.php?t=2011852&page=4)  **[B]Wireless connection problems**.

[/B]From here on out, looking for a button to click or physically push will always be my first choice/suggestion.


It is not, however, a valid suggestion for this thread.  Nothing has changed.  

I wonder how difficult it would be to make a "fix-it" widget sort of like the Gnome 2 or Mate "Force Quit" menu applet?


Thank you very much.

---

### Post by chili555 on 2012-07-08
> (I interpret that to mean that it sees the networks, but cannot possibly connect so no effort made).I apologize if I misinterpreted your statement. "No effort made" seemed to suggest that you didn't click the icon and see any networks. Sorry if I misinterpreted what you said. It is very hard to correctly guess what level of Linux expertise, particularly in networking, that a new poster has.```
sudo iwlist wlan2 scan
```Does it scan?> It is not, however, a valid suggestion for this thread. I don't believe I ever suggested it was.> “Create New Wireless Network . . .,” I type in the SSID, then click the Wireless Security tab and type in the encryption phrase. Then when I click the “Create” button, the network manager icon shows movement to (I've always assumed) indicate that there's computing going on.That is the procedure to create an ad hoc computer-to-computer network. I doubt that's what you intend. Please remove all of those entries and make sure the mode is set to Infrastructure. Please see attached. Restart Network Manager:```
sudo service network-manager restart
```Now does NM see your network?

---

### Post by Randymanme on 2012-07-08
Hello,

Your perseverance and consideration are much appreciated by me.  Thank you.

Does it scan?


randymanme@randymanme-EL1358G:~$ sudo iwlist wlan2 scan  
 [sudo] password for randymanme:  
 wlan2     Scan completed :  
           Cell 01 - Address: 00:13:F7:FA:13:E8  
                     Channel:11  
                     Frequency:2.462 GHz (Channel 11)  
                     Quality=59/70  Signal level=-51 dBm   
                     Encryption key:on  
                     ESSID:"columbuspark38"  
                     Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s  
                     Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s  
                               36 Mb/s; 48 Mb/s; 54 Mb/s  
                     Mode:Master  
                     Extra:tsf=0000003fb40c9aca  
                     Extra: Last beacon: 112ms ago  
                     IE: Unknown: 000E636F6C756D6275737061726B3338  
                     IE: Unknown: 010582848B962C  
                     IE: Unknown: 03010B 
                     IE: Unknown: 2A0103 
                     IE: IEEE 802.11i/WPA2 Version 1  
                         Group Cipher : CCMP  
                         Pairwise Ciphers (1) : CCMP  
                         Authentication Suites (1) : PSK  
                     IE: Unknown: 32080C1218243048606C  
 

 randymanme@randymanme-EL1358G:~$ 

--------------------------------------------------------------------------
Back in post #6, you mention:
[SIZE=2]     Quote:
                                                                      Originally Posted by **chili555**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=12084335#post12084335")                 
                 [I]Errmm, let's see:     Code:
     sudo iwlist wlan[COLOR=#ff0000]2[/COLOR] scan 
It is unusual to have wlan2 instead of wlan0. I assume you've had or have other wireless devices present

[/I]
                                 
[/SIZE][SIZE=2]Should I change that from wlan2 to wlan0?  Would that matter or change anything?
------------------------------------------------------------------------------
[/SIZE]     Quote:
                                                 “Create New Wireless Network . . .,” I type in the SSID, then click  the Wireless Security tab and type in the encryption phrase. Then when I  click the “Create” button, the network manager icon shows movement to  (I've always assumed) indicate that there's computing going on.                                 
That is the procedure to create an ad hoc computer-to-computer  network. I doubt that's what you intend. Please remove all of those  entries and make sure the mode is set to Infrastructure. Please see  attached. Restart Network Manager:     Code:
     sudo service network-manager restart 
Now does NM see your network?     
------------------------------------------------------------------------------------------------
randymanme@randymanme-EL1358G:~$ sudo service network-manager restart  
 network-manager stop/waiting  
 network-manager start/running, process 2635  
  randymanme@randymanme-EL1358G:~$ 


Yes it sees my network and some others.  I clicked the “create new network” heading and made it a point to choose “infrastructure.”  And the network icon showed that it connected.  But it wasn't connected.  Update manager, Synaptic Package Manager, sudo apt-get update, and Firefox all failed.
 
Nevertheless, we're making progress.  Thanks.

---

### Post by chili555 on 2012-07-08
> I clicked the “create new network” headingOnce again, that is the procedure to set up an ad hoc computer-to-computer arrangement. That is *NOT* what you want. I think you want to connect computer to router. Please remove all those settings. With a clean slate and no human intervention, if NM sees your network, it ought to try for a connection and ask for your WPA2 password.> Should I change that from wlan2 to wlan0? Would that matter or change anything?Probably not. If you are concerned, we can change it, but I doubt it has any effect on your ability to connect.> And the network icon showed that it connected. But it wasn't connected. If you can do that again, let us see:```
ifconfig
iwconfig
```Thanks.

10.42.43.xxx

---

### Post by Randymanme on 2012-07-08
> **chili555 said:**
> Thanks.

10.42.43.xxx


 I don't know what that means.  
 

  I put “10.42.43.xxx” in the Ubuntu Forums search box and all I got were two hits – one of them this thread, and the other at [http://forums.fedoraforum.org/archive/index.php/t-246679.html](http://forums.fedoraforum.org/archive/index.php/t-246679.html).  The last post on the Fedora Forums thread,  
 

 droidhacker
 11th June 2010, 07:13 PM
 Networkmanager itself sets the 169 address -- it does this when the DHCP server ***FAILS*** to provide an address.

Seems that there's a communications issue -- the encryption key is probably not working out, and being an adhoc network (that's what I read from this -- you're using networkmanager to CREATE a wireless network), it assumes that the key is good and that the dhcp server isn't responding.
 ----------------------------------------------------------------------------------------------------------------------------
 

 Seems to suggest that perhaps there might be a PBKC.
 

 I want to further clarify that I've only tried to create an ad hoc connect twice – 2 times.  Once for you.
 The reason I haven't been trying to create ad hoc network connections is because doing so requires more information than I have, have had, or am willing to find (see screenshot).  And  because I know from personal experience that infrastructure is what's always worked in the past and I only need to have two pieces of information: the SSID and the WPA & WPA2 pass phrase.
 

 Btw, the screenshot is of Black Opal on Virtualbox using the Snipping Tool.  I haven't figured out how to make screenshots of the NM box with Ubuntu (Unity) or Ubuntu 2D; I know I could do it with Mate, but up until now, I haven't any need of Mate on Precise.  (Plus, since I don't yet get internet with Precise, I can't get Mate anyway.)  It wouldn't help to install Precise on Window's Virtualbox it would connect to the network.  Or maybe it wouldn't – like you've said, I won't know until I try.  Maybe it wouldn't.
 

 I've been  copying and pasting your suggestion to Windows Documents, then booting into Precise, et al.
 

 The only reason I didn't throw-in-the-towel, today, and return the adapter to the retailer (and make a formal complaint about it carry hardware that doesn't support Linux) is out of respect for you – the time, effort, and consideration that you've put into helping me.
 

 If this is a PBKC, I can just give up and hope to do better in the future.  But, on the other hand, if you're willing to keep bearing with me, I'm willing to keep going until a solution is found that I'm able to implement.  
 

 In the meantime, I'll try out your last suggestions and install Precise to Vbox on Windows.
 

 Cheers

---

### Post by chili555 on 2012-07-09
> if you're willing to keep bearing with me, I'm willing to keep going until a solution is found that I'm able to implement.Always.

The whole point I'm trying to make is that I suspect you do *NOT* want an ad-hoc network. I hope I never suggested that you do. I think you want a computer to router network. If I am correct in my assumption, then please *REFRAIN* from this:> &#8220;Create New Wireless Network . . .,&#8221; 

If, instead, as I suspect, you want a computer to router connection, do nothing in Network Manager. Nothing. It is set up to prefer computer to router connections and requires nothing on the part of users aside from selecting which available network we wish to join. Please see attached. Once we select the network, if encryption is present, we are challenged for and supply the key and connect. My point in all this is that for a normal computer to router connection, no settings in NM are required. If you have them, delete them. I firmly believe that your addition of extra settings is telling the system that you want an ad-hoc network.> I don't know what that means. 10.42.43.xx or some close variation is the IP address that gets used when there is an ad-hoc network. I asked that when you saw:> And the network icon showed that it connected. But it wasn't connected. ...that you provide us with *ifconfig* and *iwconfig* so we could examine the IP address. You did not.> and return the adapter to the retailer (and make a formal complaint about it carry hardware that doesn't support Linux)Why?? It grabs a driver, rtl8192cu and you see networks:> With Precise, the light comes on, but does not blink (which I take to mean that a connection is almost there, but not quite -- so, **yes, it does see the network**). Isn't it doing all we expect? If we can get NM set right, or, as I suspect, *UN*set, I see no reason it can't connect.

---

### Post by Randymanme on 2012-07-20
[SIZE=2]Hello, [/SIZE]
 
[SIZE=2]Since I last posted here, I accidentally deleted an important folder; and, then, lost everything else trying to get the one folder back.  Using Testdisk (on RescueSystem CD) and Fixparts (after temporarily installing it to a live CD),  I did manage to get back Ubuntu /home.  [/SIZE] 
 
[SIZE=2]Because Ubuntu has been my primary OS, Ubuntu /home is where all my files are centralised.  As long I get Ubuntu /home back, I can live with having lost everything else.  Plus, just for the record, I have a copy of one of the other OS's /home folder in Ubuntu /home.[/SIZE]
 [SIZE=2]
I had begun composing this reply about a week ago, but got interrupted, so to speak.  The Ubuntu /home that I got back was/is one that existed *before *I had begun composing a reply for this thread.  So I'm starting over.[/SIZE]
 
[SIZE=2]I took the Netis adapter back to the retailer.  That particular retailer doesn't accept returns unless the associate working the Returns Counter thinks the returnee has a legitimate reason for doing so.  My reason was regarded as “legit” and I was directed to the Knowledge Bar.  The Knowledge Bar at that particular store is set up like bar except all they serve is knowledge and/or technical support.  [/SIZE] 
 
[SIZE=6][SIZE=2]When my turn came and I bellied up to the bar, the gentleman attending to me allowed me to go to [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?action=print](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?action=print) on his computer.  We commpared what was listed with what the store had on its shelves and in my price-range.  I decided on an ASUS PCE-N15 PCI-E Adapter.[/SIZE][/SIZE]
 
[SIZE=2]Now technically – and the gentleman the Knowledge Bar did point this out to me – my selection is not on the list, but the  ASUS PCE-N15 PCI Adapter is on the list.  My computer is a small form factor model and, so, needs the  ASUS PCE-N15 PCI-E(xpress).[/SIZE]
 
[SIZE=2]When I got it home, it didn't work – not at first.  The installation disc includes a Linux Readme that says right up front:[/SIZE]
 [SIZE=2]*--------------------------------------------------------*[/SIZE]
 [SIZE=2]*Release Date: 2011-0117, ver 0006  *[/SIZE]
 [SIZE=2]*RTL8192CE Linux driver *[/SIZE]
    [SIZE=2]*--This driver supports RealTek rtl8192CE/8188CE PCI Wireless LAN NIC for *[/SIZE]
 
      [SIZE=2]*2.6 kernel: *[/SIZE]
      [SIZE=2]*Fedora Core, Debian, Mandriva, Open SUSE, Gentoo,  *[/SIZE]
      [SIZE=2]*Ubuntu 7.10/8.04/8.10/9.04/9.10/10.04/10.10,  *[/SIZE]
      [SIZE=2]*moblin(V2), android-x86_090916, etc. *[/SIZE]
 
      [SIZE=2]*2.4 kernel: *[/SIZE]
       [SIZE=2]*Redhat 9.0/9.1*[/SIZE]
 

 [SIZE=2]For lack anything else to do (because I still don't know how to compile from source), I rounded up all live CDs I could find with a 2.6 kernel and began booting them to see if one would connect on its own.  [/SIZE] 
 
[SIZE=2]I hit pay dirt with Linux Mint 11 Katya.  Even before all the desktop icons materialised (Mint Menu being the last one to pop up), there was a black balloon saying that wireless networks were  available.  I connected to mine, verified it and double-clicked “Install.”[/SIZE]
 
[SIZE=2]So the solution (short of me learning to compile from source) is obtain a copy (or at least know the URL) of a list of Linux supported hardware and use in making a purchase.  I should have done that up front instead of guessing and hoping that something would work out-of-the-box.[/SIZE]
 [SIZE=2]
I suppose I'll start another thread (if I don't find out through my own internet searching first) asking how to compile from source.[/SIZE]
 
> **chili555 said:**
> Always.

Thank you very much.  Your help is much appreciated and is *ubuntu*.  

Even though I bailed out and returned the adapter, I still learned some things here that I carry with me and that will help me later.  And maybe much later, I'll be able to assist someone else.

Cheers

P.S.  I don't understand why an adapter may not work or not work very well at first, but then begin working well later.  Could it be  that at first it hadn't yet been integrated into the platform, but works later because the platform has been altered into a new platform, as it were, that includes the new adapter?

Earlier in this thread, in my first post, I mention having   ' . . .made a liveUSB with Startup Disk Creator of Ultimate Edition 3.2 (with persistence file) . . ..'  I recall that after I shut it down with restart and took out the flashdrive, I selected Ubuntu from the grub menu to boot.  As Ubuntu was booting, Ultimate Edition's  boot splash briefly appeared.  Was that something that was left over in ram and carried over to the next software using ram?  Could wi-fi connectivity carry over in the same way?

---

### Post by chili555 on 2012-07-20
> So the solution (short of me learning to compile from source) is obtain a copy (or at least know the URL) of a list of Linux supported hardware and use in making a purchase. I should have done that up front instead of guessing and hoping that something would work out-of-the-box.Yes, indeed! Here are some starting places:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

[https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux](https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux)

[http://linuxhcl.com/](http://linuxhcl.com/)

I started in Linux in 2001 when it was actually hard. I decided early on to buy equipment that was Linux-friendly. For instance, it was so nice to buy a printer, hook it to the USB port and print a test page in all of ten minutes. I urge everyone to do the same.> Release Date: 2011-0117, ver 0006
RTL8192CE Linux driver
--This driver supports RealTek rtl8192CE/8188CE PCI Wireless LAN NIC forDepending on what Ubuntu version you installed, the driver is already in place; probably what's missing is firmware. Ubuntu is rigid about *NOT* including proprietary bits in what is supposed to be open source software. Mint is a bit more relaxed.> chili@LAPTOP60:~$ modinfo rtl8192ce
filename:       /lib/modules/3.2.0-26-generic-pae/updates/cw-3.3/rtl8192ce.ko
[COLOR="Red"]firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin[/COLOR]
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
<snip>Undoubtedly, the firmware is on the CD and could be copied over to make your device work in Ubuntu.> I suppose I'll start another thread (if I don't find out through my own internet searching first) asking how to compile from source.If you PM me the link, I'll be glad to help. As you see above, it's probably not the driver you needed, but the firmware. However, the knowledge to compile is worthwhile in any case.

I'm glad it's working in any event. Have fun!

---

