---
title: "Trouble with wireless"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by PercZ on 2009-02-22
Hey!
I have a problem with connecting to wireless on my laptop HP Presario CQ50.
After installing ubuntu, I tried to open Network-Manager, but I was not able no find it. It should be placed in System > Administration.
So, I downloaded WICD manager, and it works. But still, this manager cant find any wireless networks.
Does anyone has a clue what's going on?
Thanks for help ;)
[SIZE="1"]...and sorry for mistakes.[/SIZE]

---

### Post by PercZ on 2009-02-22
Bump

---

### Post by superprash2003 on 2009-02-22
in your terminal type **sudo iwlist scanning** and post output here..

---

### Post by PercZ on 2009-02-22
superprash2003, 


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by lastfrontier on 2009-02-22
also post iwconfig and ifconfig out put here so we can see this also this should tell us if you wireless card is powered up/turned on

---

### Post by PercZ on 2009-02-22
ifconfig:  (I wrote sudo ifconfig)

eth0      Link encap:Ethernet  HWaddr 00:1d:72:68:a7:0b  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe68:a70b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:929 errors:0 dropped:0 overruns:0 frame:0
          TX packets:814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:858712 (858.7 KB)  TX bytes:210585 (210.5 KB)
          Interrupt:221 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:770 (770.0 B)  TX bytes:770 (770.0 B)


iwconfig: (I wrote sudo iwconfig)

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.



;)

---

### Post by lastfrontier on 2009-02-22
there is no wireless card is what it looks like to me i mean i am sure it is in the comp but i dont think the comp knows it try this **lshw -C network** show the out put of this mabey also **sudo lspci -VV **this should help alot

---

### Post by lastfrontier on 2009-02-22
dose this computer have an ethernet port you can plug into because if it dose then there should be under ifconfig eth1 and eth0 but i only see one that is why i think your comp dose not see the the wireless card



eth0      Link encap:Ethernet  HWaddr 00:**:**:**:**:**  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:**:**:**:**:**  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe5c:47cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3404 errors:0 dropped:0 overruns:0 frame:5803
          TX packets:3014 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3712069 (3.5 MB)  TX bytes:552534 (539.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:0.0.0.0  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9400 (9.1 KB)  TX bytes:9400 (9.1 KB)

be back in 15 min need to go to the store please post those thing this will tell us if you even have a wireless card be right back

---

### Post by PercZ on 2009-02-22
BTW, I also run Windows XP on this laptop, and there's no problem with wireless and wired internet. Only here, on Ubuntu (Wired works on Ubuntu)

lshw -C network:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:68:a7:0b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.7 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e2:2e:69:36:91:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


sudo lspci -VV:

lspci: invalid option -- 'V'
Usage: lspci [<switches>]

Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file



;)

---

### Post by lastfrontier on 2009-02-22
i should have told you to run this as superuser it would have given a bit more info (sudo lshw -C network) here is what i was looking for the bold print. your print out dose not show that the card has wireless capability i suggest you start to look for a missing driver did the install go ok ? is this a dual boot computer ? i am also not sure why it says unclaimed never seen that before...

terminal-junky@terminal-junky:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1d:72:0d:99:b8
       width: 64 bits
       clock: 33MHz
       **capabilities: bus_master cap_list ethernet physical**
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1e:4c:5c:47:cc
       width: 32 bits
       clock: 33MHz
       **capabilities: bus_master cap_list ethernet physical wireless**
       configuration: broadcast=yes driver=wl ip=192.168.2.6 latency=0 module=wl multicast=yes wireless=IEEE 802.11
terminal-junky@terminal-junky:~$

---

### Post by PercZ on 2009-02-22
Well, as I said before, I have Windows XP and Linux Ubuntu here on computer. On XP, there's no problem with connection. Here on ubuntu, wired connection is OK, wireless not. 
I have Support for Atheros 802.11 wireless LAN cards driver, installation was automatic and okay when I booted ubuntu first time.
How to run sudo lshw -C network as super user?

;)

---

### Post by Shady2175 on 2009-02-22
I am wondering as well after reading some threads about wirless connections to the internet.. aren't wireless cards suppose to automatically search for a signal? I run XP on my laptop and desktop both.. both of which use wireless cards. I got Ubuntu to install on my desktop but would not in any way find an internet connection. I'm confused on alot of this stuff..lol

---

### Post by lastfrontier on 2009-02-22
i have had a few start up problems with some wirless cards but i have not found any so far that will not work i think you need to look up your card and see if any one else has had this same problem i will look also and see what i can find.

---

### Post by lastfrontier on 2009-02-22
i think this is what you are looking for i hope this solves your problem dont let this startup problem get you down i think you will find linux to be refreshing also very important make sure that your wireless card is on the best way to do this is to go into the bios and turn it on on boot up..

read this 

[http://www.pclinuxos.com/forum/index.php?topic=48393.0](http://www.pclinuxos.com/forum/index.php?topic=48393.0)

---

### Post by PercZ on 2009-02-22
Thanks for that, it might work =)
I'll report when/if I solve in the afternoon, I'm in a  hurry for work at the moment.

---

### Post by siabost on 2009-02-23
Hi,

Try the following link - even if you're not going to use a windows driver along with ndiswrapper, it still full of clear useful info including what "UNCLAIMED" means.

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

Best of luck.;)

---

### Post by PercZ on 2009-02-23
A post of CtrlAltDel:

"Hi there Jason,

To install the ndiswrapper way you must first have the windows driver for your card..  You'll need a .inf and .sys file..  Copy these somewhere to your /home folder..

Then enter the PCC > Network/Internet > Remove Network Interface..

Repeat this until the Atheros Card is no longer installed..

Then Setup A New Network Interface > Wireless > Ndiswrapper

Browse for your driver in your /home folder and install..

You'll now be able to scan for channels hopefully.."




How can I get .inf and .sys file from driver installation?

I went to BIOS to boot options and there was "run network adapter on boot" disabled, I enabled it, but it's still not working.

EDIT2: I became confused by so many forums and help links...What should I do first, and than next?

---

### Post by siabost on 2009-02-23
Hi,

You can get .inf & .sys files from the original installation disk that came with the card. Normally there will be an "installation" or "driver" folder (ignore any .exe files as these are purely for Windows installation).

Usually there are folders for the different varieties of windows - I normally pick the XP but others may work too). The .inf & it's related .sys usually sit side by side in the folder.

If you don't have the disk, & as you have a wired connection, you should be able to download it direct from the manufacturer's website and select the bits you want.

Best

---

### Post by PercZ on 2009-02-23
Hi!
I succeed getting .sys and .inf files, but...

CtrAltDel said:  "Then enter the PCC > Network/Internet > Remove Network Interface..."  [Fifth post](www.pclinuxos.com/forum/index.php?topic=48393.0)

Where is this "PCC"?

---

### Post by PercZ on 2009-02-23
Hey, I was just checking the Add/Remove software option in Ubuntu and I saw ndiswrapper wireless drivers.
I knew this is something what needs to solve my problem, so I installed it, inserted first .inf file from Windows driver, it was error, and than I tried second and it worked...but when I click REFRESH button in WICD manager still cant find any wireless networks. 
Is there something I forgot to do before installing wireless driver?
Thanks for help =)

EDIT:
I think this is the why its not working...because I dont know where is PCC, I cant continue:

"Then enter the PCC > Network/Internet > Remove Network Interface..

Repeat this until the Atheros Card is no longer installed..

Then Setup A New Network Interface > Wireless > Ndiswrapper

Browse for your driver in your /home folder and install.."


Where is PCC?

---

### Post by PercZ on 2009-02-24
Bump...Guys, I really need to know where is "PCC"
Thanks :P

---

### Post by siabost on 2009-02-25
Afraid I'm a bit new at this too... but in the absence of more expert advice, here's my story:
Ubuntu 8.04LTS with new Belkin Wireless PCI card.

Fitted PCI card & when I ran > lshw in Accessories/Terminal it came back with > *network UNCLAIMEDwhere my wireless card should have been. I understand this means no driver was claiming it i.e. loading to operate it.
Installed ndiswrapper. Copied XP Windows .inf & .sys file to a folder I created to keep them cosy & installed them via ndiswrapper (it also told me "hardware yes").

Now I had been messing around with Network Manager, lost it & could not get it back. So I installed WICD.
As with your situation, with correct driver installed WICD didn't pick up network.

Now that you have driver installed run in Terminal:> lshw -C Network
Look for the "Logical name" of your wireless network (this reference should no longer be "UNCLAIMED"). This is likely to be "wlan0" & your wired connection "eth0".

In WICD (not sure where as I only used WICD briefly)there will be a menu to set the connection. In mine I noticed that against the Wired connection was entered "eth0" & against the Wireless connection it was blank. I entered the "Logical name" mentioned above, "wlan0" in my case & ticked (I think) a box to enable the connection. Okayed the settings and my network could be seen.

If this works you will need to set your security settings with the "settings" button next to your connection before connecting. 

This should work for you but alas for me...

In the end I couldn't get my security settings to work & ended up reinstalling Ubuntu (using the "manual" partitioning option) and only formatting the / (root) partition. That reinstated Gnome-network-manager, I loaded ndiswrapper, then the drivers, enabled my network (right-click Network Manager Icon), selected my now visible wireless network, enetered my pass phrase & HALLELUJAH I was on!

Good Luck.:guitar:

EDIT: To get the connection to connect to wireless on boot-up I had to go to (Pref or Administration) Menu/Network Tools, click on my network & when asked allow Network Manager access to "Keyring" to retrieve security details. It now connects on boot & seems to be working perfectly. NOTE: I know you are using WICD but the process should be similar.

---

### Post by PercZ on 2009-02-26
Log:

WARNING: you should run this program as super-user.
PCI (sysfs)  
SCSI                      
  *-network        
       description: Ethernet interface
       product: MCP78S [GeForce 8200] Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:68:a7:0b
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.2.102 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:53:5c:75:04:a9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


I'm a n00b in Linux...what exactly should I do now? Network is still UNCLAIMED...in WICD I cant see any menu to set a connection...Please, explain more particular, thanks =)

---

### Post by siabost on 2009-02-26
Hi,

For comparison this is what I was getting from lshw when I had my problem:
> *-network:0 UNCLAIMED
description: Ethernet controller
product: Belkin
vendor: Belkin
physical id: 4
bus info: pci@0000:01:04.0
version: 20
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=64 maxlatency=64 mingnt=32

You have "width" at 64bits.

If you are running Ubuntu 8.10 64bit (rather than 32bit, which I run with 8.04) make sure that you have selected the 64bit .inf file in ndiswrapper and not the standard 32bit.

Make sure also that you have copied both .inf & it's .sys file (they normally have same name) into the same folder. They have to be together for ndiswrapper to work.

Remember to delete your existing driver in ndiswrapper before installing another.

See how that goes.

---

### Post by PercZ on 2009-02-26
Siabost, 

"If you are running Ubuntu 8.10 64bit (rather than 32bit, which I run with 8.04) make sure that you have selected the 64bit .inf file in ndiswrapper and not the standard 32bit."

I have two .inf files, only one is the right one, they are from 32-bit Windows, how can I change that in ndiswrapper? I have 32-bit Ubuntu.
When I click Configure Network in ndiswrapper, it pops up a window saying than it could not find a network config tool.

"Make sure also that you have copied both .inf & it's .sys file (they normally have same name) into the same folder. They have to be together for ndiswrapper to work."

I have =)

---

### Post by siabost on 2009-02-26
Hi,

This may be a little different in Ubuntu 8.10 but deleting a wrong .inf file should be straightforward (it is easy in 8.04).

Under System/Administration/Windows Wireless Drivers in the window that appears you will see both wireless drivers in the pane to the left. Highlight the one you want to get rid of & click the "remove" button. After this is done click "close" & reboot.

Configure your network via WICD as the "configure Network" button in ndiswrapper may look for Network Manager Tools which Synaptic will probably have removed in the process of installing WICD.

Alternatively try reinstalling Gnome-network-manager until you get your wireless network up and running: then you would need to go to System/Administration/Network Tools to get you going.

That's what I had to do.

NOTE: I am assuming you have the Graphical Front End for ndiswrapper installed - if not it is ndisgtk in System/Administration/Synaptic Package Manager.

Good luck.

---

### Post by PercZ on 2009-02-27
Hi!
I just saw that this wireless button on my laptop lights red, it should be BLUE to enable wireless. But when I press it, its nothing, remains red.
In Windows XP, when I press once its RED and it wont find any wireless networks, when I press once more, its BLUE and it detects wireless. 
Here on ubuntu is not working. 
Does this info tell you anything?

---

### Post by AvengerX9 on 2009-02-27
I have the same problem I think :)

---

### Post by siabost on 2009-03-01
Hi,

I'm afraid I can't help with the wireless on/off button - I've never had one! Someone else will have to help there...

However, I wouldn't have thought it would stop the wireless driver loading at boot. If you're still getting the "UNCLAIMED" message against your wireless network card when you run lshw in Terminal then your first problem will be getting a driver to load.

After that the button may be a problem... I don't know...

---

### Post by PercZ on 2009-03-03
Strange, I guess I'll have to use wired =P
Thx for help =)

---

### Post by wwkeyboard on 2009-04-16
Ok, with this one I'm not trying to be funny. The wireless button seems shut off the wireless link through hardware somehow. When I'm connected to an access point and push the button I will be disconnected. It will remain this way(through reboots), with no word out of the drivers or dmesg that anything is amiss, until I press the button again. My system (CQ50-115nr) is working fine with the madwifi drivers. If your system is not I would recommend that you press the wireless button ONCE and try you system again. If it does not work after you have pushed the button once, push it again and forget I said anything, but for the love of god keep track of how many times you have pushed it. 

* Yes, this kill about two hours of my time. The machine ran fine for about 6 months until my dog ran across the keyboard, leading to this discovery of mine. I just want to make sure this information gets out there somewhere.

---

