---
title: "ATHEROS DRIVERS FOR WIRELESS CARD wont stick! any suggestions? noob in need of help"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by mplinux on 2009-03-12
Hello,
It's my first time on here. I'm a complete newbie to linux. I just installed ubuntu 8.10 on my system set as dual boot with vista. Everything works like a charm, but my wireless does not work. I have read multiple threads and tried several fixes with no success, please HELP! I want don't want to go back to vista. 

System Description:
Toshiba Satellite L305d-S5893.
AMD 64-bit.
Wireless card: Atheros AR5007EG.

List of attempted fixes per forum recommendations:

1st ATTEMPT:
I Tried installing wcid (wireless connection manager) to see if anything changed and came up with wireless connection. NO FIX although I like the interface. :(

2nd ATTEMPT:
As instructed in instructions on installation guide on I ran ndisgtk and downloaded the 64 bit driver identified on this thread [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828). I ran ndisgtk and added the driver as instructed (64-bit). unactivated the atheros driver on SYSTEM>ADMINISTRATOR>HARDWARE DRIVER. This was done to ensure that only the new driver is running. Restarted the system. still no FIX. :(

3rd ATTEMPT:
I found another thread recommending to check out the release notes for 8.10 that discuss issues with the ath5k wireless drivers and recommended to download "linux-backports-modules-intrepid-generic" package. This supposedly has a updated version of ath5k which it does since under Hardware Driver list a new driver called "support for atheros 5xxx driver" appeared. I activated the driver and removed the other driver using ndisgtk,to ensure that only the new driver is running. RESTARTED the system. Still NO FIX!:(

what should i do next?! any help will be greatly appreciated I really want to learn all about linux and make it my new OS. 
 
FYI: I ran terminal: sudo lshw -c network ///this is what i still get:
 *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

I ran terminal: lspci 
OUTPUT:
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

any suggestions out there will be greatly appreciated?

---

### Post by pewterbot9 on 2009-03-12
I'm a newbie, too, running Ubuntu 8.10 on an Asus Eee PC 1000HA. After mucking about for the past several days, trying things out like yourself, this is what I've concluded:

There is nothing you can do right now, to get the atheros chip to work. But the Ubuntu hackers are working very hard to finally come up with a solution. So it's just a matter of a little more time, before that beneficent breakthrough. Until then:

Purchase a USB wifi adapter that is known to work w/Linux, in robust fashion. I got one off eBay for approx. $20 total. It came w/a mini-DVD that included drivers for Windoze and Linux. You can view it here:

[http://tinyurl.com/ab94yf](http://tinyurl.com/ab94yf)

Now, I have yet to set it up, but will do so tonight, and return with a report.

You might have a linux-compatible wifi USB adapter lying around somewhere, and not even realize it. You might want to search in forums for "linux USB wifi" to see what others suggest.

AFAIC, it's worth an extra $20 to stay offa Windoze.

---

### Post by mplinux on 2009-03-13
FIXED!!! 
Here is what I did per bmartin and other threads tips. 

Prereq:
I had a Clean install of Ubuntu 8.10.

1ST STEP:
Installed NDIS wrapper from Synaptic Package Wrapper(Search for NDISGTK) or Add/Remove Applications (search for ndis) **Because I'm not to familiar with terminal I preferred to download the 
NDIS wrapper Interface**

2ND STEP:
Downloaded the appropriate driver for my 64-bit driver. If you have  32-bit just make sure to download that driver. I grabbed the link from this [**THREAD**]("http://ubuntuforums.org/showthread.php?t=512828")
Click [ here ]("http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz").for 64 bit. 
Click [here]("http://blakecmartin.googlepages.com/ar5007eg-32-0.2.tar.gz").for 32 bit. 
- Opened downloaded File on Desktop --> Extracted files to my home folder.

4TH STEP:
Open NDIS wrapper that I installed earlier by going to SYSTEM>ADMINISTRATION>WINDOWS WIRELESS DRIVERS. 
- SELECTED +Install New Driver
- Located net5211.inf file by going to Ar5007eg folder -->ar5007eg-->net5211.inf
- Select Install

3rd STEP
Go to SYSTEM> ADMINISTRATION> HARDWARE DRIVERS
Deactivate "Support for Atheros 802.11 wireless LAN cards."

4TH STEP
Rebooted and my Wireless Card is now WORKING!! 

**The only problem I had was that Network Manager did not want to accept my password for my router for some reason. I knew it was correct...I decided to try out WICD network manager. Quote:"Wicd is an open source wired and wireless network manager for Linux which aims to provide a simple interface to connect to networks with a wide variety of settings"

5TH
I went to [WICD]("http://wicd.sourceforge.net/download.php") web page.

This is the instructions to download and set up WICD on their website. 

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, **intrepid**).**MAKE SURE YOU REPLACE HARDY with intrepid**. You'll also need to add the key used for signing Wicd by running the following command in a terminal:

    wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 

Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily.


6TH STEP:
REBOOTED Selected my network from WICD tray Icon. Selected network...selected WPA2 for my security settings/set password... and it was like MAGIC!! now I have a fully functional connection!!!

I hope this helps!!! There is hope out there for those of us using the darn Atheros AR5007EG cards!

---

### Post by pewterbot9 on 2009-03-13
I'm also a newbie, and had all sorts of failures trying the various methods to make my atheros wifi work. After much frustration and exhaustion, I broke down and purchased for $20 from eBay, a USB wifi adapter that claims to work with Linux. Comes with a mini-DVD with drivers for both Windoze and Linux. And whaddya know:

It works like a charm, no need to install drivers. So here is where you can get one yerself:


[http://tinyurl.com/cgm95z](http://tinyurl.com/cgm95z)

There are also two other USB wifi adapters highly recommend by a geekster on Youtube:

Ubuntu wireless - 8.04 - what works
[http://www.youtube.com/watch?v=ewaym7rbAUE](http://www.youtube.com/watch?v=ewaym7rbAUE)

Go to his page, you'll see this blurb:

"Wireless without the nonsense for Ubuntu Linux. No headaches, just working wireless - models described are the Edimax EW-7318USG and EW-7318UG - Goto NewEgg.com for both - just use site search. "

Here is an eBay page for the Edimax adapter:

[http://tinyurl.com/c8qpcv](http://tinyurl.com/c8qpcv)

Until the Ubuntu hacker community comeso up with a good driver for the Atheros wifi, why not give yourselves (newbies) a break, and just order one of those adapters? Cheers!

UPDATE: I think the best bet is to go with the Edimax wifi adapter, as it looks like it's the most robust. I justt ordered one. Why? Because the one I have now (described above) is on the weak side...though it works pretty well, at least I now have wifi access. (I did lose connection, but there may be a way to change the settings to connect better, I'm just too much of a newbie right now.) 

Customer reviews of the Edimax adapter, highly favorable, including for Ubuntu:

[http://tinyurl.com/auoncf](http://tinyurl.com/auoncf)

UPDATE 2: Well, my present USB wifi seems to work very well. Seems that what I took for weak reception, was one of my security plugins that I wasn't aware of. And the signal range show just one bar out of four...yet I am connecting at a robust pace. I think it's wrong, it claims I'm at 25%, yet I'm able to load pages and videos, and download, quite fast.

---

