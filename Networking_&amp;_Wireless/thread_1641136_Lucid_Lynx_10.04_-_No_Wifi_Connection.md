---
title: "Lucid Lynx 10.04 - No Wifi Connection"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by Sky Aisling on 2010-12-08
&#65279;[SIZE=4]Hello, 
I have installed XUbuntu 10.04 but cannot connect to WiFi.
 Here is what I know so far:

[U]Hardware and Software configuration:
 
[/U][B]Compaq Presario 2100US
 XUbuntu 10.04 (installed Dec. 2010 from Live CD dated Oct. 2010)
 Kernel 2.6.32-21-generic
 Gnome 2.30
 RAM Memory: 938.7 MiB
 Processor: Celeron
 Disk Space Avail 23.2 GiB
 
Wireless Card: MSI Wireless 11G CardBus CB54G2
 *MSI Driver rt2500pci located in system (see below)
 No wifi 'on' 'off' hardware switch on machine
 

[/B]Prior to the install of Xunbuntu 10.04 (Lucid Lynx) the machine carried MSXP.
 The wireless card came with the machine. The machine used a cable connection by previous owner. 

Connection's been working fine in Ubuntu Jaunty Jackelope and Puppy Linux.

Wireless card appears to be functioning. The system scans for the network, shows that connection is established by both icon in tray and message saying that a connection is made. The card shows both green lights active. The light that indicates a connection is on and randomly flickers.

Tested Firefox for connection. Firefox is not receiving anything from the system.

***Note:** please skip to: [http://ubuntuforums.org/showthread.php?t=1641136&page=2](http://ubuntuforums.org/showthread.php?t=1641136&page=2) and skip the rest of this page.  I have got the network manager functioning enough to say that I have a 'connection' but still cannot connect to server.  Any help from that point on is appreciated.  Thank you*

NetWork Connections
 wireless: linksys - mode ad hoc - MTU auto
 wireless: security - none (I borrow from a neighbor's wifi)
 IPv4: auto(DHCP)
 IPv6: Ignore

*Driver rt2500pci located in /sys/module/rt2500pci/drivers/
 (There is a 'config' file in this directory)

Help menu in 10.04 is listed as help menu for 9.04 so don't know if applicable to 10.04 debugging. 

When 'troubleshooting' wireless connections, I did a ***sudo lshw -C network* **command on terminal. The results ***do not* **show 'Claimed, Unclaimed, Enabled or Disabled as help menu indicates.  The line that would show that information (*-network) doesn't have 'Claimed, Unclaimed, Enabled or Disabled'. I can send image of this query. 

I have tried two other wifi cards with similar results, no connection.

Any help appreciated. 

Please give commands for terminal. I'm new to using the terminal and need to have you tell me the commands. 

**Note:** if this issue is a Lynx only issue then I can install Meerkat if it does not have the same issue and will properly connect.  Which system I install makes no difference to me.
 
Thank you for taking time to help,

Sky

PS - Ignore the signature information below.  It's outdated.  I'll get in and change after I do this post. :)
[/SIZE]

---

### Post by grahammechanical on 2010-12-08
Type in a terminal

```
nm-tool
```

Look through the list of devices. Look for wlan0 and see what its State is. Is it connected? 

Look for list of Wireless Access Points. These will be all the wireless networks that are in range. This indicates that Ubuntu has recognized your wireless device and is using it.

Look for IPv4 settings. Do you see some numbers alongside similar to 192.168.1.65? Do you see similar numbers alongside DNS?

You may be connecting to the router/modem but going no further. It may not be a problem with the operating system and they way it uses wireless.

Regards.

---

### Post by Sky Aisling on 2010-12-08
Thank you, grahammechanical

grahammechanical writes:

[I] 		Type in a terminal

[/I]   	*Code:*
 	*nm-tool* 
Response: [I]The program 'nm' can be found in the following packages:
* binutils
*binutils-multiarch
Try: sudo apt-get install <selected package>

[/I]Do I do the sudo apt-get install?

---

### Post by Sky Aisling on 2010-12-08
Never mind, did install and now have information:

State: wlan0  'disconnected'.

Default: no

No Wireless Access Points Listed

---

### Post by Sky Aisling on 2010-12-08
Note: There is also a **device eth0** listed.

State: unavailable
 
Default: no

Capabilities:

   Carrier Detect: **yes***
   Speed: 10/Mb/s

Wired Properties

    Carrier: off

*Perhaps this is what is showing 'connected' in the system tray?

---

### Post by Sky Aisling on 2010-12-08
grahammechanical writes:

[I]Look for IPv4 settings. Do you see some numbers alongside similar to 192.168.1.65? Do you see similar numbers alongside DNS?

[/I]No
Using Terminal Screen:
On terminal screen there is HW Address: 00:19:DB:0C:FB:66

No 
Using right click of wifi icon in system tray under edit connection

---

### Post by Sky Aisling on 2010-12-08
Here is copy of **nm tool** information 
Plus
Here is copy of **sudo lshw -C network** information


                                       [SIZE=2]NetworkManager Tool
[/SIZE]         [LEFT][SIZE=2]State: disconnected[/SIZE][/LEFT]
        [LEFT][SIZE=2]- Device: eth0 -----------------------------------------------------------------[/SIZE][/LEFT]
    [LEFT][SIZE=2]  Type:              Wired[/SIZE][/LEFT]
    [LEFT][SIZE=2]  Driver:            natsemi[/SIZE][/LEFT]
    [LEFT][SIZE=2]  State:             unavailable[/SIZE][/LEFT]
    [LEFT][SIZE=2]  Default:           no[/SIZE][/LEFT]
    [LEFT][SIZE=2]  HW Address:        00:0B:CD:54:41:1A[/SIZE][/LEFT]
        [LEFT][SIZE=2]  Capabilities:[/SIZE][/LEFT]
    [LEFT][SIZE=2]    Carrier Detect:  yes[/SIZE][/LEFT]
    [LEFT][SIZE=2]    Speed:           10 Mb/s[/SIZE][/LEFT]
        [LEFT][SIZE=2]  Wired Properties[/SIZE][/LEFT]
    [LEFT][SIZE=2]    Carrier:         off[/SIZE][/LEFT]
            [LEFT][SIZE=2]- Device: wlan0 ----------------------------------------------------------------[/SIZE][/LEFT]
    [LEFT][SIZE=2]  Type:              802.11 WiFi[/SIZE][/LEFT]
    [LEFT][SIZE=2]  Driver:            rt2500pci[/SIZE][/LEFT]
    [LEFT][SIZE=2]  State:             disconnected[/SIZE][/LEFT]
    [LEFT][SIZE=2]  Default:           no[/SIZE][/LEFT]
    [LEFT][SIZE=2]  HW Address:        00:19:DB:0C:FB:66[/SIZE][/LEFT]
        [LEFT][SIZE=2]  Capabilities:[/SIZE][/LEFT]
        [LEFT][SIZE=2]  Wireless Properties[/SIZE][/LEFT]
    [LEFT][SIZE=2]    WEP Encryption:  yes[/SIZE][/LEFT]
    [LEFT][SIZE=2]    WPA Encryption:  yes[/SIZE][/LEFT]
    [LEFT][SIZE=2]    WPA2 Encryption: yes[/SIZE][/LEFT]
        [LEFT][SIZE=2]  Wireless Access Points [/SIZE][/LEFT]
            [LEFT][SIZE=2]sky@sky-Presario2100:~$ sudo lshw -C network[/SIZE][/LEFT]
    [LEFT][SIZE=2][sudo] password for sky: [/SIZE][/LEFT]
    [LEFT][SIZE=2]  *-network               [/SIZE][/LEFT]
    [LEFT][SIZE=2]       description: Ethernet interface[/SIZE][/LEFT]
    [LEFT][SIZE=2]       product: DP83815 (MacPhyter) Ethernet Controller[/SIZE][/LEFT]
    [LEFT][SIZE=2]       vendor: National Semiconductor Corporation[/SIZE][/LEFT]
    [LEFT][SIZE=2]       physical id: 12[/SIZE][/LEFT]
    [LEFT][SIZE=2]       bus info: pci@0000:00:12.0[/SIZE][/LEFT]
    [LEFT][SIZE=2]       logical name: eth0[/SIZE][/LEFT]
    [LEFT][SIZE=2]       version: 00[/SIZE][/LEFT]
    [LEFT][SIZE=2]       serial: 00:0b:cd:54:41:1a[/SIZE][/LEFT]
    [LEFT][SIZE=2]       size: 10MB/s[/SIZE][/LEFT]
    [LEFT][SIZE=2]       capacity: 100MB/s[/SIZE][/LEFT]
    [LEFT][SIZE=2]       width: 32 bits[/SIZE][/LEFT]
    [LEFT][SIZE=2]       clock: 33MHz[/SIZE][/LEFT]
    [LEFT][SIZE=2]       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/SIZE][/LEFT]
    [LEFT][SIZE=2]       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10MB/s[/SIZE][/LEFT]
    [LEFT][SIZE=2]       resources: irq:10 ioport:2400(size=256) memory:d0004000-d0004fff memory:54000000-5400ffff(prefetchable)[/SIZE][/LEFT]
    [LEFT][SIZE=2]  *-network[/SIZE][/LEFT]
    [LEFT][SIZE=2]       description: Wireless interface[/SIZE][/LEFT]
    [LEFT][SIZE=2]       product: RT2500 802.11g Cardbus/mini-PCI[/SIZE][/LEFT]
    [LEFT][SIZE=2]       vendor: RaLink[/SIZE][/LEFT]
    [LEFT][SIZE=2]       physical id: 1[/SIZE][/LEFT]
    [LEFT][SIZE=2]       bus info: pci@0000:02:00.0[/SIZE][/LEFT]
    [LEFT][SIZE=2]       logical name: wlan0[/SIZE][/LEFT]
    [LEFT][SIZE=2]       version: 01[/SIZE][/LEFT]
    [LEFT][SIZE=2]       serial: 00:19:db:0c:fb:66[/SIZE][/LEFT]
    [LEFT][SIZE=2]       width: 32 bits[/SIZE][/LEFT]
    [LEFT][SIZE=2]       clock: 33MHz[/SIZE][/LEFT]
    [LEFT][SIZE=2]       capabilities: pm bus_master cap_list ethernet physical wireless[/SIZE][/LEFT]
    [LEFT][SIZE=2]       configuration: broadcast=yes driver=rt2500pci latency=64 multicast=yes wireless=IEEE 802.11bg[/SIZE][/LEFT]
    [LEFT][SIZE=2]       resources: irq:11 memory:50000000-50001fff[/SIZE][/LEFT]
    [LEFT][SIZE=2]sky@sky-Presario2100:~$[/SIZE] [/LEFT]

---

### Post by grahammechanical on 2010-12-08
I find what you are reporting as strange. In your first post you say that the wireless card seems to be functioning. From the information that you give I would agree with you. I asked you to run nm-tool as a means of confirming that wireless was working as it should but it seems that you did not have network manager installed.

Have you rebooted? You could try that and then experiment with left and right clicking the network manager icon.

There have been improvements from 9.04 to 10.10 but much of the information in the guides is still useful. Especially the commands. The icons and the dialogs boxes have changed their look. More wireless devices are recognized at installation. If you can upgrade to 10.10 I would suggest it. Try a Live CD first. See, If you can get Internet access that way before you install. Some who post on this forum claim that wireless networking under 10.10 is faulty. I do not agree. But then I do not have any problems with it.

Regards.

Sorry, I have only just now seen your recent posts as I posted this one of mine.

---

### Post by grahammechanical on 2010-12-08
May I quote the Wireless Trouble Shooting guide?

> Use the lshw command. As explained under lshw, if there is a line saying configuration: ...driver=... in the description of the wireless card, this indicates the driver is installed.You have > configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1   So, I guess that you have a driver installed.

This is the link to the trouble shooting guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

I am now getting out of my depth. Perhaps someone more knowledgeable will notice this thread and offer advice.

Regards.

oops. I was looking at the wired connection. This is for wireless > configuration: broadcast=yes driver=rt2500pci  So, you must have driver installed. I did say I was out of my depth.

---

### Post by Sky Aisling on 2010-12-08
Rebooted 10.04.

Right Click system tray connection icon 

*Enable Networking* checked
*Enable Wireless* checked
*Enable Notifications* checked
*Connection Information* grayed out
*Edit Connections* available
[I]About

[/I]Left Click system tray connection icon
[I]
Wired Networks[/I] grayed out
*Wireless Networks* grayed out
*VPN Connections* available
*Connect to Hidden Wireless Network* available
*Creat New Wireless Network* available

Note: system did not search for a connection on this boot as it has done in the past.
Icon tray indicates no connection.  Previously, there has been a search for a connection then a connection made according to the icon and screen message.

---

### Post by Sky Aisling on 2010-12-08
I 'edited' the wireless system called 'linksys' and now I have a 'connection' showing in the system tray icon and a screen message saying that connection is established.

Here is what I changed from original:

Wireless 
SSID: linksys   
Mode: Ad-hoc  (was 'infrastructure')
BSSID:  blank
MAC address: blank
MTU: automatic

IPv4 Settings
Method: Shared to other computers (was automatic DHCP)
Available to all users blank

Still unable to connect to Firefox.  'Server not found'.

---

### Post by Sky Aisling on 2010-12-08
_Active Network Connections_
(from left click on system tray connection icon)

*Interface:* 802:ll Wifi (wlan0)
*Hardware Address:* there are numbers here but I won't list them
*Driver:* rt2500pci
*Speed:* Unknown
*Security:* none

*IP Address:*  there are numbers here but this is an unsecured line so I don't think I should list any numbers here.  right?
*Broadcast Address:* numbers here
*Subnet Mask:* numbers here

---

### Post by Sky Aisling on 2010-12-08
Using Terminal entry **nm-tool**:

Device: **wlan0 [linksys]**
.
.
State: connected
.
.Wireless access Points (* = current AP)
*linksys:  Ad-Hoc, numbers here, Freq 2412 MHz, Rate 0 Mb/s Strength 255

Note: under wireless properties the WEP, WPA and WPA2 Encryption are set to 'yes'. ?

Is any of this helpful?

Thank you

---

### Post by Sky Aisling on 2010-12-08
Thank you, []("http://ubuntuforums.org/member.php?u=1087323")grahammechanical.

I have a feeling we are getting close.  
However, as you say let's see if others notice this and can offer other suggestions.
:)
I will go back to the tutorials and troubleshooting for more clues.

Again, thank you for your time.

Sky

---

### Post by Sky Aisling on 2010-12-08
Hummm?  I am reading in [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Connections)
that sometimes the power manager causes problems.  I note that in the example given that the power manager is 'off'.  Perhaps I need to turn off the power manager and reboot.   

How do I turn off the power manager?

---

### Post by bmengineer on 2011-07-10
Hey Sky

I'm having a very similar problem to what you described and was wondering how you ended up getting it to work?
Thanks

---

### Post by Sky Aisling on 2011-07-10
bmengineer,

First of all, welcome to the forum.  :)

Gosh! it has been so long since I wrote this thread.  Let me see...ah yes, I remember. Lucid 10.04 was way to much for that old Compaq.  I took Lucid 10.04 off and installed Puppy Linux 431 and all has been well since.

I am running Lucid 10.04 on a ZaReason Big Lap laptop which is capable of running the OS with no issues what-so-ever.  

You'll have to be more specific when you post a question, bmengineer.  The folks who can help need to know things like what make and model machine you have, how much RAM, what is the name of your wireless card, things like that.  :)

Sky

---

### Post by Benitez on 2011-07-19
Hello everyone!

I am having a very similar issue to what other posters have put on this thread. 

I am attempting to connect an older laptop to my network wirelessly; the computer and Ubuntu 10.04 can see the network with no problem, but the system will not connect to it.

Connecting to the network through ethernet works beautifully, and I have no problems getting a connection. It is simply the wireless that is giving me problems.

The home network consists of the following:

```
DSL Modem -> Router -> VoIP -> Computer
```

The following specifications for the devices are as follows:
[LIST]
[*]Modem: ZyXEL P-660ER
[*]Router: Netgear MR814v3
[*]VoIP: Vonage VDV22-VD
[*]Computer: Intel Core running Windows 7
[*]Laptop: Dell Latitude C610 with Ubuntu 10.04
[/LIST]

All devices have been upgraded with the latest firmware available to this date.

I presume that any and all issues that I have are likely due to the Netgear MR814v3 that provides the wireless, but I'm not sure why the Ubuntu laptop sees the network, but does not connect to it.

I will post my output below for **iwconfig**, **dhclient**, **nm-tool**, etc. :)

---

### Post by Benitez on 2011-07-19
OK, back again. Gonna start posting up what I have gotten from **iwconfig**, **nm-tool**, etc.:

**iwconfig** output when wireless is not connected:

(NOTE: I don't understand why that garbled text comes up for the ESSID. I presume that is the standard text(?) that comes up when it cannot connect to a network. When my network card attempts to connect to 'MyPrivateNetwork', the aforementioned name is used and comes up for the ESSID)
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"f2\x0D\xB71X\xA3Z%]\x05\x17X\xE9^\xD4\xAB\xB2\xCD\xC6\x9B\xB4T\x11\x0E\x82tA!=\xDC\x87"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=45/70  Signal level=-57 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:30
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

```


**nm-tool** output when not connected. 'MyPrivateNetwork' is of course, the network I am attempting to connect to. I have also XX'd out the last three sets of hex digits for the output.
```
- Device: eth1 (wireless) ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        00:02:2D:XX:XX:XX

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    MyPrivateNetwork:         Infra, 00:0F:B5:XX:XX:XX, Freq 2442 MHz, Rate 11 Mb/s, Strength 65 WPA
```

**sudo lshw -C network** output. I have XX'd out the last few hex digits myself in the output.
```
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:XX:XX:XX
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.0.5 latency=32 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec80(size=128) memory:f8fffc00-f8fffc7f memory:1c000000-1c01ffff(prefetchable)
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:5
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=yes multicast=yes wireless=IEEE 802.11b

```

Output from my Netgear MR814v3 Wireless Setup Page:
```
Wireless Network
===================
Name (SSID): 'MyPrivateNetwork'
Region: United States
Channel: 7

Security Options
===================

Security: WPA-PSK

Security Encryption
===================

Passphrase: ********************
Key Lifetime: 120 minutes

```

I would appreciate any other bit of help or any advice. I have also looked at the Wireless Troubleshooting guide, and have gotten no results. :confused:

Will post up more after I attempt to connect my network to an older wireless DSL/Router combo and post the output. 

Thanks again to everyone for the help!

---

### Post by Sky Aisling on 2011-07-19
**Benitez**,
A quick question.
Is your 10.04 installed as a *full* install or are you running from a Live CD or other type of installation?

---

### Post by Benitez on 2011-07-19
> **Sky Aisling said:**
> **Benitez**,
A quick question.
Is your 10.04 installed as a *full* install or are you running from a Live CD or other type of installation?

Bah! I forgot to mention that! #-o

In short, yes, this is a full install of Ubuntu 10.04 LTS.

This laptop previously had **[Lubuntu]("http://lubuntu.net/")** installed onto it. I tried to fix the issue on Lubuntu itself using Network Manager, but I couldn't. I then went to Synaptic and added/installed 'ubuntu-desktop' with all the packages it had. I also gave the laptop all the updates possible. There are a few packages that couldn't be updated (nothing that I know related to network stuff though), but I seem to have the full GNOME Desktop Environment in my laptop.

I did try to change the mode on NetworkManager from 'Infrastructure' to 'Ad-Hoc'; it did seem to connect for a while, but after I restarted the laptop, it would not connect for me again. Not sure exactly why it worked that one time and not after that. 

I am still frustrated, as my girlfriend's Windows 7 laptop can connect to the network with absolutely no problem at all. Even with that, my Android phone can't see the network anymore either. Perhaps, my Netgear router is just too old? :confused: I'd prefer to not have to get rid of it, since it seems to do the job just fine, but if it has to come down to that... *sigh*

Thanks anyway, Sky. Do you know what else I can try before posting up with any other info?

---

### Post by Sky Aisling on 2011-07-19
**Benitez** writes:

> Do you know what else I can try before posting up with any other info?I wish I did, but, no...

[FONT=Helvetica, Arial, sans-serif]interestingly [/FONT], I had the same situation with the NetworkManager changing from *infrastructure* to *Ad-Hoc*.  Thot I had the problem solved then it reverted back to no connection as soon as I went out of the browser.

We need some network nerds to step up and help here.

---

### Post by Benitez on 2011-07-19
> **Sky Aisling said:**
> 
[FONT=Helvetica, Arial, sans-serif]interestingly [/FONT], I had the same situation with the NetworkManager changing from *infrastructure* to *Ad-Hoc*.  Thot I had the problem solved then it reverted back to no connection as soon as I went out of the browser.

We need some network nerds to step up and help here.

I concur with your posting. I am wondering if it might just be some obscure networking bug also in the software. Then again, I wouldn't know how to begin to troubleshoot such an issue...

I feel like this problem should go on its own separate thread, if at least to prevent people from glossing it over due to the **[SOLVED]** tag it has.

I'm wondering if I can get the laptop to connect with an older combination Westell 327W combination DSL/Wireless Router modem that I had when I was using another ISP. I was able to have the laptop connect to that one with absolutely no problem.

I'm not sure if it's even a radio frequency interference issue either, since the Westell modem was in the exact same location as the current position, and I was able to use the laptop to get wireless access with no problem. Once again, the fact that my girlfriend's Win7 laptop gets signal throughout the house also leads me to believe it might be something stranger going on. 

Also, **BUMP** for great justice (and some assistance).

Thanks anyway! :D

---

### Post by Sky Aisling on 2011-07-19
I'll see if I can change the [SOLVED] label.

**Edit:**  Looks like it worked.  Now, maybe more folks who wander the aisles of *unsolved* mysteries will notice and respond.   :)

---

### Post by Sky Aisling on 2011-07-19
**Benitez**,

I sent you private message.  Did you receive?  Thanks...

---

### Post by Benitez on 2011-07-22
OK, so I made a few changes to the physical network. 

I got rid of the Netgear MR814v3 and the ZyXEL P660R modem, and replaced both successfully with a new Westell modem. 

I was able to get it working with other devices (e.g., my girlfriend's laptop and also my Android phone), but I am still having no success having the laptop connect to this new Westell modem. :confused:

The stats of the new combined DSL Modem/Wireless Router is:
Router: Westell D90-327W15-06 Rev. G (fully updated firmware)

Surprisingly, I am getting some other output that is puzzling me; I am beginning to wonder if it's something to do with Network Manager, simply because it sees the network I wish to connect to, but on Network Manager the specified network is greyed out.

When I look at the output of **nm-tool**, I get the following:
```
- Device: eth1 (Wireless)------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        00:02:2D:XX:XX:XX

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    MyNetwork:         Infra, 00:12:0E:XX:XX:Xx, Freq 2457 MHz, Rate 54 Mb/s, Strength 100 WPA2
```

Looking at the AP number, I see that the first three bytes are 00:12:0E; if I understand that this number is equivalent to the MAC address of the wireless router I'm trying to connect to, then it is incorrect. The first three bytes of the correct MAC address for the modem are 00:18:3A; that already tells me something is likely wrong.

What's more interesting is the output for **iwconfig**:
```
eth1      IEEE 802.11b  ESSID:"MyNetwork"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=33/70  Signal level=-69 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:58
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Even though **nm-tool** says that the wireless signal strength is 100 (percent?), **iwconfig** is reporting the link quality of 33/70. Perhaps I'm mistaking the two, or it may actually be relevant. I can't really say. *sigh*

I'm at a loss of what else to do. I even attempted to use an old Notebook adapter (a Linksys WPC54GS ver. 2) to connect to the wireless network, but no luck with that either. :( I'm seriously wondering if maybe something in the software got corrupted or not, but I can't be too sure, nor do I know how else to begin troubleshooting.

Any ideas, or suggestions? Anyone?

P.S.: Including a picture of the network I'm trying to connect to. To the right of the mouse is my network. The network I'm trying to connect to is greyed out.

---

### Post by Sky Aisling on 2011-07-22
**Benitez,**

What is make, model, specs of your laptop?

Grasping at straws here until we can get more assistance.
Have you read this post of a few hours ago:
[http://ubuntuforums.org/showthread.php?t=1807528&highlight=network+manager+wifi](http://ubuntuforums.org/showthread.php?t=1807528&highlight=network+manager+wifi)

---

### Post by Benitez on 2011-07-22
I was looking at the output of **sudo lshw -C network**:
```
  *-network
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 2
       resources: irq:5
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 link=yes multicast=yes wireless=IEEE 802.11b
```

I realized three things:
[LIST=1]
[*]My laptop is using a Lucent/Agere firmware, as seen in the last line of the output shown above.
[*]The first thing I did when I connected my computer and updated from the 'original' install of **Lubuntu** was to both install **ubuntu-desktop** and also to update anything that was out of date.
[*]I looked at my message outputs to see if anything strange would come up. I kept getting a strange kernel message in file **messages** regarding the Lucent/Agere firmware. The output I kept getting was:
```
Laptop kernel: [85177.858015] eth1: Lucent/Agere firmware doesn't support manual roaming
```
[*]Googling up said message gives me the following Ubuntu Forums link regarding said error message **[update has broken wireless connection]("http://ubuntuforums.org/showthread.php?t=1257291")**

Basically, the link states that an update to one of the files may likely impair the ability to connect to a wireless network. Someone in the forums suggests rolling back the driver, or adding some lines to a file to make it work. See link **[here]("http://ubuntuforums.org/showpost.php?p=10397774&postcount=18")** by the poster to see his solution.
[/LIST]

Going to attempt to see if either of the two solutions work. Wish me luck, everyone! :D

*EDIT:* Apparently, adding the lines to the **interfaces** file did not do anything. I simply removed the lines and rebooted the computer. I am back again with a laptop that cannot connect wirelessly to my wireless router. Still, it was worth a try.

---

### Post by Benitez on 2011-07-22
> **Sky Aisling said:**
> **Benitez,**

What is make, model, specs of your laptop?

Please see the file "LaptopInfo.pdf" attached below for detailed information on my laptop. A quick output of it gives me that this laptop is a Dell Latitude C610.

> **Sky Aisling said:**
> Have you read this post of a few hours ago:
[http://ubuntuforums.org/showthread.php?t=1807528&highlight=network+manager+wifi](http://ubuntuforums.org/showthread.php?t=1807528&highlight=network+manager+wifi)
Gonna start going through the commands, and will post up the output in subsequent posts.

Again, thanks for the heads up.

---

### Post by Benitez on 2011-07-22
Everyone please bear with me and be patient. There will be a LOT of raw output in this post.

I will be following the same instructions given by user **chili555** on the post entitled **["Help! Totally unable to connect to wifi with acer notebook"]("http://ubuntuforums.org/showthread.php?t=1807528")**.

Following the output of **[this]("http://ubuntuforums.org/showpost.php?p=11063298&postcount=2")** post, I get the following:

Output of **lspci -nn | grep 0280** and **rfkill list all**:

```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Now going to attempt to install some firmware (likely the Broadcom 43xx LP-PHY installer) as suggested on **[this]("http://ubuntuforums.org/showpost.php?p=11065025&postcount=4")** post of the same thread.

*EDIT:* I could not install the package **firmware-b43-lpphy-installer** because the package needs to have at minimum Maverick (Ubuntu 10.10), and I am using Lucid (Ubuntu 10.04 LTS). ](*,)

Maybe all my problems might be fixed if I just install Maverick, or even maybe even Natty (Ubuntu 11.04)?

---

### Post by chili555 on 2011-07-22
Please see:>  Device: eth1 (Wireless)------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        00:02:2D:XX:XX:XX

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    [COLOR="Red"]WPA Encryption:  yes[/COLOR]
Compare to:> Wireless Access Points 
    MyNetwork:         Infra, 00:12:0E:XX:XX:Xx, Freq 2457 MHz, Rate 54 Mb/s, Strength 100 [COLOR="Red"]WPA2[/COLOR]Not all older cards do WPA2. Can you change your router to WPA?

Is the internal card defective or what?

---

### Post by Sky Aisling on 2011-07-23
**Benitez,**

What is the content of your **/etc/resolvconf** file?

---

### Post by Benitez on 2011-07-23
> **chili555 said:**
> Please see:Compare to:Not all older cards do WPA2. Can you change your router to WPA?

Is the internal card defective or what?
Alright, I was able to change the mode to WPA only. The wireless router has a mode for both WPA/WPA2 and combined. Just to be sure, I changed it to just plain WPA.

I still cannot connect for the life of me.

This card shouldn't be defective, since it was able to get access both on regular WEP and on WPA when I used the old settings. I just don't know why it refuses to work now. :confused:

> **Sky Aisling said:**
> **Benitez,**

What is the content of your **/etc/resolvconf** file?

Output of the **/etc/resolvconf** file:
```
*** /etc/resolvconf: directory ***
username@host:~$ cd /etc/resolvconf/
username@host:/etc/resolvconf$ ls
update-libc.d
username@host:/etc/resolvconf$ ls -a
.  ..  update-libc.d
username@host:/etc/resolvconf$ cd update-libc.d/
username@host:/etc/resolvconf/update-libc.d$ ls
avahi-daemon

```

Gonna try again, but I will try using the external wireless card this time (Linksys WPC54GS ver.2). Any other output I can try?

---

### Post by Sky Aisling on 2011-07-23
**Benitez,**

Do you have a use for avahi-daemon?  [http://avahi.org/](http://avahi.org/)

You might try removing it. 

```
sudo apt-get remove avahi
```**Edit:**

(Avahi can be re-installed through Synaptic Package Manager;  **System/Administration/Synaptic Package Manager ** quick search *avahi*.)

---

### Post by Sky Aisling on 2011-07-24
Sky Aisling wrote[B]:

[/B]> Benitez,

What is the content of your /etc/resolvconf file?Here is Wiki's description of /etc/resolv.conf and /etc/resolvconf  
[COLOR=Red]Note:[/COLOR] these are two different files.  This isn't a typo *resolv[COLOR=Red].[/COLOR]conf* and *resolvconf*.

Wiki's description of /etc/resolv.conf:

[http://en.wikipedia.org/wiki/Resolv.conf](http://en.wikipedia.org/wiki/Resolv.conf)

Wiki's description of /etc/resolvconf:

[http://en.wikipedia.org/wiki/Resolvconf](http://en.wikipedia.org/wiki/Resolvconf)

[COLOR=Red]Note[/COLOR] the last 2 paragraphs in Resolvconf description:

[I]"When resolvconf is properly installed, the resolv.conf file at is replaced by a symbolic link to /etc/resolvconf/run/resolv.conf and the resolver instead uses the dynamically generated linked file.

The resolvconf program is only necessary when a system has multiple programs that need to dynamically modify the nameserver information. In a simple system where the nameservers do not change often or are only changed by one program, the resolv.conf configuration file is adequate."

[/I]Perhaps there is an issue with the running of /etc/resolveconf?

---

### Post by Benitez on 2011-08-03
Hey everyone! Back now... Umm, sorry for not getting back to you guys recently; I've been damned busy the last week or so. Gonna get back on the updates and all...

> **Sky Aisling said:**
> **Benitez,**

Do you have a use for avahi-daemon?  [http://avahi.org/](http://avahi.org/)

You might try removing it. 
Umm... I'm not sure that I need it. For that matter though, I'm not sure whether I'll need to remove it too or not (I'll explain below).

> **Sky Aisling said:**
> Sky Aisling wrote[B]:

[/B]Here is Wiki's description of /etc/resolv.conf and /etc/resolvconf  
[COLOR=Red]Note:[/COLOR] these are two different files.  This isn't a typo *resolv[COLOR=Red].[/COLOR]conf* and *resolvconf*.

Wiki's description of /etc/resolv.conf:

[http://en.wikipedia.org/wiki/Resolv.conf](http://en.wikipedia.org/wiki/Resolv.conf)

Wiki's description of /etc/resolvconf:

[http://en.wikipedia.org/wiki/Resolvconf](http://en.wikipedia.org/wiki/Resolvconf)

[COLOR=Red]Note[/COLOR] the last 2 paragraphs in Resolvconf description:

[I]"When resolvconf is properly installed, the resolv.conf file at is replaced by a symbolic link to /etc/resolvconf/run/resolv.conf and the resolver instead uses the dynamically generated linked file.

The resolvconf program is only necessary when a system has multiple programs that need to dynamically modify the nameserver information. In a simple system where the nameservers do not change often or are only changed by one program, the resolv.conf configuration file is adequate."

[/I]Perhaps there is an issue with the running of /etc/resolveconf?
Umm... I don't think it may have something to do with **resolvconf** anymore; however, it could be that what I did below could have changed the program.

Alright, now to the nitty gritty... 

[SIZE="3"]**I FIXED IT!**[/SIZE]

I'm not sure how I did it, but the wireless works on my laptop now. I'll try to post what I did in order to get better documentation for future reference.

Firstly, I updated my install (from my administrator account) of Lucid Lynx using **Update Manager**; apparently there was an update to the linux kernel amongst the other updates. I'm not sure if this could have something to do with it. I then reset the laptop, and logged back on to my administrator account.

Upon logging back in, it looks like **Password Manager** asked me for the password to connect to my network. I was able to do so, and I made sure to click on "Automatically log me on for all users" or an option to that effect (I clicked on this option, as I remember that I needed to do something like this on a previous installation of Ubuntu to get the wireless working for all users).

I was able to get wireless access through the administrator account on the laptop. I went to a few websites, and confirmed that I could get downloads and uploads. I then logged out and restarted the laptop; I logged into the secondary account on the laptop. The secondary account is more limited so other users cannot make unauthorized changes.

Upon logging into the secondary account, **Network Manager** was able to connect to my network with little to no problem automagically! :KS I logged on to a few websites, and was able to connect, download, and upload with absolutely no problem. 

Just in case, I logged off, restarted the laptop, went back to the administrator account, connected to the network, restarted the laptop once more, and logged back into the secondary account. The secondary account is able to connect to the network without requiring a password.

*It is safe to conclude that the laptop can now connect to my wireless network with no fuss!*

Before I log off completely, I have a few questions for some of the folks following this thread, as I'd like to not leave any loose ends, so here goes:
[LIST=1]
[*]What exactly did I do to fix the situation??? For all intents and purposes, I'm going to attribute this either to (a) witchcraft and sorcery :-P, or (b) the update overwrote some configuration file and fixed it somehow.
[*]Is there a logfile or set of files that I can attach to here that may help indicate what the problem was? I'd really like to understand exactly what it was that was wrong, in case this happens again. I also presume it's best to learn what you're doing, and not just say "It's fixed!" and remain uninquisitive as to what caused the problem.
[*]My suspicions are that the "Password Manager" needed to be activated. If that's the case, I would like to know if all Ubuntu flavors use that, or if only certain ones use said program. This leads to the following question below...
[*]I wish to turn the box into a **[Lubuntu]("http://lubuntu.net/")** box (as it was before) and remove **ubuntu-desktop**; if I remove **ubuntu-desktop**, is it likely to undo my settings, and thus cause **Network Manager** to no longer connect to my network?
[/LIST]

I'd like to thank EVERYONE that was able to give me an assist on this thread. Thank you all so, so, SO MUCH for your help! I hope to return the favor, pay it forward, and more importantly, learn more about Linux/Ubuntu! :)

---

### Post by Sky Aisling on 2011-08-03
**Benitez**, Congratulations!

I too want to hear the answers to your last questions.
I am currently playing with editing the grub configuration file.
Considering perhaps an IRQ problem.
[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)


**EDIT:**
Looks Like it's a lucky day for both of us, Benitez!  I too have **SUCCESS!**.
I did it with the help from this thread: 
[http://ubuntuforums.org/archive/index.php/t-411324.html](http://ubuntuforums.org/archive/index.php/t-411324.html)
which pointed me to this thread:
[https://help.ubuntu.com/community/DebuggingIRQProblems](https://help.ubuntu.com/community/DebuggingIRQProblems)
I booted the system with the *pci=noacpi* boot parameter.
See instructions in the documentation.
So far, so good...

---

