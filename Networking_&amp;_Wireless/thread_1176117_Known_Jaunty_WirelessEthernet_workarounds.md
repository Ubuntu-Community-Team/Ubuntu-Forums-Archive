---
title: "Known Jaunty Wireless/Ethernet workarounds"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by dmizer on 2009-06-02
Disclaimer:
The purpose of this thread is to list known Jaunty Jackalope 9.04 networking fixes and workarounds. All discussion about the fix itself should go into their related threads. Please add to this discussion by posting fixes that helped you to get your wireless or wired internet connection working and I will include them in this post as time permits.
[SIZE="5"][COLOR="Red"][LIST]
[*]Please do not post a request for a workaround.
[*]Please do not list any wireless issues here without workarounds.
[/LIST][/COLOR][/SIZE]
[SIZE="3"]**Please post the following wireless card information:**[/SIZE]
I/O bus (PCMCIA, USB, PCI)
Make (Linksys, D-Link, Buffalo, etc)
Model (wpc54g, DWA-642, etc)
Version (if applicable)
Chipset
[INDENT]To determine the chipset, open a terminal and type:
```
lspci &#8211;v | less
```
Then, scroll to find your wireless device and note down its details. For USB devices, type lsusb instead.[/INDENT]

Here are some helpful links to get you online while this thread builds an information base:
-----------------------------------------------------------------
List of supported wireless cards (may have current Jaunty data): [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
Manual network configuration (CLI based): [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
Wireless security (CLI based): [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)
WiFi howto (some information may be out of date): [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
Wireless troubleshooting guide: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
Network manager (includes NM specific troubleshooting): [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7)
-----------------------------------------------------------------

**DHCP Problems**
Here is a link for fixing DHCP issues in Jaunty:
[http://ubuntuforums.org/showthread.php?t=1156441](http://ubuntuforums.org/showthread.php?t=1156441)

**RaLink RT2500**
Card works but browsing is slow. Fix is posted here: [http://ubuntuforums.org/showthread.php?t=1148109](http://ubuntuforums.org/showthread.php?t=1148109)

**D-Link WUA-1340**
USB adapter. Stopped working after updates. Fix in post 2 below.
Thanks Cariboo907

**WiFi Link 5100**
Card works but is unable to connect to WPA. Fix is posted here:
[http://ubuntuforums.org/showpost.php?p=7415234&postcount=3](http://ubuntuforums.org/showpost.php?p=7415234&postcount=3)
Thanks Evil Dax

**Linksys WMP54GS v 1.1**
Chipset: Broadcom BCM4318
Native driver isn't functional. Needs ndiswrapper. Fix outlined in this thread:
[http://ubuntuforums.org/showthread.php?t=1188702](http://ubuntuforums.org/showthread.php?t=1188702)

---

### Post by cariboo on 2009-06-04
I have a usb wireless device that worked initially when Jaunty was first installed, but since updating it stopped working.

The Device - D-Link WUA-1340

Output of lsusb:

```
us 001 Device 003: ID 07d1:3c04 D-Link System WUA-1340

```

Chipset - ralink

Driver - rt73usb

The driver was loaded om boot, but Network Manager said it was unmanaged. To get wireless working, I uninstalled **network-manager-gnome** and isntalled **gnome-network-admin**. This removes the nm-applet from the notification area, and leaves you with a small bar graph to show you, that you are connected.

To set up your wireless connection go to System-->Administration-->Network, next click the unlock button and enter your password when asked. Next select your device from the list and click Properties.

Once in the properties dialog box, enter your essid and whatever else you need, then click OK. The applet will reset your network device and connect to your access point. See screenshots.

Note: this device is connected to my Intel Atom powered media center pc, which streams video and audio from my file server.

---

### Post by Evil Dax on 2009-06-07
Jaunty64, Intel WiFiLink 5100 and WPA2

lspci:
07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

OS:
Jaunty64: 2.6.28-11-generic

Issue:
non-secured and WEP working, while WPA and WPA2 fail to connect

Solution:
download latest microcode from Intel:
[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz")
put the file into /lib/firmware

change modprobe:
```

sudo modprobe -r iwlagn
sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

```

And you can connect to WPA2

---

### Post by dmizer on 2009-06-07
Thanks Evil Dax, I've added that to the first post now.

---

### Post by jimv on 2009-06-10
PROBLEM: 
RTL8185 did not work with WPA in 9.04, worked fine in 8.10 (ndiswrapper driver).  The native driver, RTL8180, will connect to WPA, but it has a poor connection that drops all the time.

WORK-AROUND:
Purchase Intel wifi card off eBay for $11 after checking Linux wifi compatibility list.

BONUS:
Can use native Linux driver instead of Ndiswrapper.

EDIT

The RTL8180 driver with the RTL8185 chipset seems much more stable in the AMD64 version of Ubuntu, but it doesn't report the signal strength correctly.

---

### Post by Curvature_Tensor on 2009-06-11
sudoedit /etc/NetworkManager/nm-system-settings.conf

edit the file to read
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

save and reboot.


Worked for bcm4311 wireless card and Atheros AR242x wireless card.  Also worked for Marvell 88E8038 wired Ethernet port

---

### Post by dmizer on 2009-06-11
> **Curvature_Tensor said:**
> sudoedit /etc/NetworkManager/nm-system-settings.conf

edit the file to read
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

save and reboot.


Worked for bcm4311 wireless card and Atheros AR242x wireless card.  Also worked for Marvell 88E8038 wired Ethernet port

Can you be more specific about the problem that this solves?

---

### Post by juky on 2009-06-12
> 
Originally Posted by Curvature_Tensor View Post
sudoedit /etc/NetworkManager/nm-system-settings.conf

edit the file to read
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

save and reboot.


Worked for bcm4311 wireless card and Atheros AR242x wireless card. Also worked for Marvell 88E8038 wired Ethernet port


> **dmizer said:**
> Can you be more specific about the problem that this solves?

Guess this is a issue what it solves: [http://ubuntuforums.org/showpost.php?p=5976351&postcount=5](http://ubuntuforums.org/showpost.php?p=5976351&postcount=5)

Cheers,
juky

---

### Post by sendblink23 on 2009-06-12
read below sorry Quoted to the wrong person

---

### Post by sendblink23 on 2009-06-12
> **Curvature_Tensor said:**
> sudoedit /etc/NetworkManager/nm-system-settings.conf

edit the file to read
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

save and reboot.


Worked for bcm4311 wireless card and Atheros AR242x wireless card.  Also worked for Marvell 88E8038 wired Ethernet port



I'm having an issue, mine is related to this one since I have "Atheros AR242x wireless card"

It used to be detected automatically, but after updating it just isn't detected at all.

Now here is my issue... after running on Terminal: sudoedit /etc/NetworkManager/nm-system-settings.conf

It open right inside of TERMINAL:
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

Ofcourse I replaced "flase" with "true"
But how do I save it??? I did Ctrl+S nothing happened(to confirm me that I saved it)

Well I rebooted and still the same not detected... so I decided well let just go to the directory manually, I try to open that File: nm-system-settings.conf

here is what happens after clicking Open:

Could not display "etc/NetworkManager/nm-system-settings.conf
There is no application installed for this file type.

Can you help me out, since it is only visible through Terminal, I want to know how to SAVE it after applying the change of *false to *true, so that I can test if it works again my Wireless

THANKS

---

### Post by dmizer on 2009-06-12
sendblink23, use this command instead:
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by sendblink23 on 2009-06-12
> **dmizer said:**
> sendblink23, use this command instead:
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

Thank you ;)

Now I can confirm after Reboot, the wireless got detected back again :)

---

### Post by monkeylytics on 2009-06-14
I upgraded Jaunty, and networking wasn't available for my onboard ethernet on my Asus A8n-sli which is an Nvidia MCP55 setup even though it was working on Intrepid. After struggling for hours to find a solution for Jaunty and my ethernet setup, I remembered that I had the same problem on my upgrade to Intrepid and this did the trick:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836)

This also works for Jaunty (surprising to see the problem persist into Jaunty.)

Steve

---

### Post by AJack10600 on 2009-06-24
You have a 128 bit ASCII WEP key to enter your WLAN but network manager and WICD want Hex code. So your key is rejected and you are promted for a new key again and again. When ticking the see option on the key field, you note that it is full with Hex code. 
 
 
The solution is:
 
Network Manager and WICD want Hex code to entre the WEP encrypted WLAN. As a matter of fact you can convert ASCII to Hex code and vice versa. 
 
So by translating your ASCII key to Hex code and by entering this Hex string in the Key field for your WEP network you get it to work. 
 
A ASCII to HEX Translator can be found in my last post on this thread
[http://ubuntuforums.org/showthread.php?p=7508101#post7508101](http://ubuntuforums.org/showthread.php?p=7508101#post7508101)

---

### Post by njb on 2009-06-29
> **Curvature_Tensor said:**
> sudoedit /etc/NetworkManager/nm-system-settings.conf

edit the file to read
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

save and reboot.


Worked for bcm4311 wireless card and Atheros AR242x wireless card.  Also worked for Marvell 88E8038 wired Ethernet port

Thank You it gave back life to my wired local network

:p NjB :p

---

### Post by Netzilla on 2009-06-29
Original thread:
[http://ubuntuforums.org/showthread.php?t=1199305](http://ubuntuforums.org/showthread.php?t=1199305)

System Info:  
DELL - OptiPlex GX270
Dual-boot

Problem:
On-board NIC (Intel 82540 EM) would not connect to network at all.

Solution:
dmesg conntained the following error message:
```

[    7.448738] e1000: 0000:01:0c.0: e1000_probe: The EEPROM Checksum Is Not Valid

```

Downloaded the current BIOS Upgrade from the DELL website [http://support.dell.com/support/downloads/download.aspx?c=us&cs=555&l=en&s=biz&releaseid=R86320&SystemID=PLX_PNT_CEL_GX270&os=WW1&osl=en&amp;amp;deviceid=162&devlib=0&typecnt=1&vercnt=3&formatcnt=1&fileid=113058](http://support.dell.com/support/downloads/download.aspx?c=us&cs=555&l=en&s=biz&releaseid=R86320&SystemID=PLX_PNT_CEL_GX270&os=WW1&osl=en&amp;amp;deviceid=162&devlib=0&typecnt=1&vercnt=3&formatcnt=1&fileid=113058)

Unfortunately I only found a Win/DOS version of the update.

This fixed the invalid checksum and networking started working again.

---

### Post by mattshow on 2009-07-09
Not sure this is the right thread, but hopefully this can help somebody.

The wireless connection between my Dell Inspiron 1525 laptop and my D-Link DIR-625 wireless router was intermittent. It would work for 5 minutes, then cut out for 2 minutes. I have no idea if this is strictly a Jaunty issue or if affects other Ubuntu versions. The laptop had Vista on it before this, and it connected just fine to the same router. The router was set to use TKIP or AES encyrption, whichever the connecting device supported. 

Here's the wireless card information from lspci:

Broadcom Corporation BCM4312 802.11b/g (rev 01)
Kernel driver in use: wl
Kernel modules: wl

From looking at the dmesg output, it looked like it might be a TKIP problem. So I set the router to only support AES, and now my wireless connection works just fine.

---

### Post by phillw on 2009-07-10
[SIZE=2][FONT=Arial]Realtek RTL8187 - On a Gateway Laptop.

Only proven on above system !!

After mucho messing about with various methods to enable, I was totally confused & did a re-install of Ubuntu 9.04.

WITHOUT the Ethernet cable plugged in.  Imagine my complete and utter shock when the wireless unit popped into life and wanted to connect by WPA or WPA2 (I could only get WEP before) !!

Ok, so the signal reports as weak, but it is steady as a rock, with no drop outs etc - I am one very, very happy little bunny.

I guess it's only of use for those just installing Ubuntu 9.04 as I did it completely from start. But, it may help someone else out there.

Regards,

phillw
[/FONT][/SIZE]

---

### Post by solidus126 on 2009-07-10
HOWTO: Wifi in Ubuntu Netbook Remix for Toshiba NB205

I got the wireless card to work! I had to use Ubuntu Netbook Remix, and have not tested my method using regular Ubuntu or Kubuntu.

After scouring the internet, I found a solution from a post on Ubuntuforums.org. I have since lost the link to the forum post, but still have the link they had posted in the forum:

[http://tjmcgrew.com/](http://tjmcgrew.com/)

Here is an adapted and condensed series of instructions:

1. Install Ubuntu Netbook Remix. I did not really stray from default install options.

2. Do a full system update by going to Administration -> Update Manager. Check for updates first, then install them. You will likely need to reboot your computer... do so. You should see a new option in GRUB, probably kernel 2.6.28-13-generic, which is the one you want to boot back into.

3. Now, go to Administration -> Software Sources. In the Updates tab check "Unsupported updates (jaunty-backports)". I also checked everything in the Ubuntu Software tab with the exception of the Cdrom box, and the two boxes in Third-Party software, but I am fairly certain they are not needed for fixing wifi.

4. Repeat step 2. My reasoning for not doing 3 first is because it seems to download extra fluff and adding excessive GRUB menu entries if you do it out of this order.

5. Issue the following command in a terminal window (found in the Accessories tab)

```
sudo apt-get install linux-backports-modules-jaunty
```

After accepting the request to install the packages, reboot.

6. In my case, after logging in my network was automatically detected and my connection was live!

If anyone has any questions about a step, I am happy to clarify any small detail I may have missed.

---

### Post by Lovecraftian Horror on 2009-07-10
> **solidus126 said:**
> HOWTO: Wifi in Ubuntu Netbook Remix for Toshiba NB205

I got the wireless card to work! I had to use Ubuntu Netbook Remix, and have not tested my method using regular Ubuntu or Kubuntu.

<snip>.

I was able to get WiFi working by following Master_Kernel's compiling guide. I think it's marginally faster, depending on how fast your internet connection is, as it took nearly 3 hours for the kernel to compile.

The two methods are functionally the same- by switching to upstream updates, you've gotten the 2.6.30 kernel that will be in Karmic, once it's officially supported.

---

### Post by phillw on 2009-07-10
> **phillw said:**
> [SIZE=2][FONT=Arial]Realtek RTL8187 - On a Gateway Laptop.

Only proven on above system !!

After mucho messing about with various methods to enable, I was totally confused & did a re-install of Ubuntu 9.04.

WITHOUT the Ethernet cable plugged in.  Imagine my complete and utter shock when the wireless unit popped into life and wanted to connect by WPA or WPA2 (I could only get WEP before) !!

Ok, so the signal reports as weak, but it is steady as a rock, with no drop outs etc - I am one very, very happy little bunny.

I guess it's only of use for those just installing Ubuntu 9.04 as I did it completely from start. But, it may help someone else out there.

Regards,

phillw
[/FONT][/SIZE]


[SIZE=2][FONT=Arial]There must be someone 'up-there' looking after me ....

I've been busy re-installing my sisters' laptop (Yeah... Windows.. no virus protection ..... Was a fairly sick beast)

But :p and it's worth another one :p .....

On her re-installed laptop (guess the O/S maker), her new '3' usb cell-fone type thingy (Huwaie dongle) keeps dropping the connection. 

As my laptop is still in dual boot (to support those who suffer with the operating sytems that others wouldn't touch) it was also doing the same to me.

I forgot to unplug it when I re-booted from Vista to Ubuntu .... OMG ... Ubuntu said hello - I'll use it & it's as stable as heck.

So, whilst I do not do advertising - If you are running Jaunty, and want an 'on the fly' internet connection (I have a laptop) - Go down, get one, buy it for about £30 GBP and then  pay £10 GBP per GB of usage. Turn off your computer, plug it in, turn it back on - and...... It works... str8 out of the Box !!!

Isn't that a refreshing change ?

Between that and a possible really easy way to get RealTek Wireless working - things are looking up !!!

Phill.

):P 
[/FONT][/SIZE]

---

### Post by itsjareds on 2009-07-11
Here's a part-way fix for getting a Netgear WPN111 to connect to a WPA2-secured network:

[HOWTO: WPA2 with NETGEAR WPN111]("http://ubuntuforums.org/showthread.php?t=901818")

The reason this is a part-way fix and not a complete fix is because the connection will drop after an inconsistent amount of time. Right now the thought is that it is a problem with ndiswrapper. Running ndiswrapper -l after the connection drops will not respond in the terminal.

[WPN111 bug discussion thread here.]("http://ubuntuforums.org/showthread.php?t=1192404")

edit: Woah, completely forgot the card info :-\" -
```
I/O Bus: USB
Make: Netgear
Model: WPN111
Version: v1.1 and v2.0
Chipset: Atheros AR2414
```

Thanks.

---

### Post by RavanH on 2009-07-12
dmizer and others,

If you have some time to check out the solution to the rt2500 slow connection problem that i have figured out and posted over on [http://ubuntuforums.org/showthread.php?p=7605785]("http://ubuntuforums.org/showthread.php?p=7605785") , I would be very grateful. 

Is it a valid solution? If there are big (security or other) mistakes in there, please let me know and i will update. 

TIA

---

### Post by jml on 2009-07-21
This is a work around for a specific piece of hardware.

Issue:  System 76's Netbook "Starling" has very limited wireless functionality.  It will only connect when physically close to the AP and has a 100% signal strength.  This is acknowledged by the manufacturer as a "driver issue."  So far it is still unresolved.

Hardware:  Stock, as it comes from System 76.

OS:  Ubuntu NBR 9.04 (also stock, with all updates installed.)

Work Around:  Bypass the internal card by inserting a "Belkin G Wireless USB Network Adapter."  Model F5D7050.  My device was labeled ver. 4122.  Here are the steps:

1. Turn on Starling with the USB wireless adapter plugged in.
2. After boot up and log in at the desktop, a dialog box opens stating that "Authentication required for wireless network." (I use WPA encryption on my network,) click on the connect button.
3. Wait about 30 seconds, during that time the dialog box pops up again, presumably for the internal card. I clicked cancel this time.
4. After about 30 seconds the network manager applet announces that a connection exists.

I confirmed that this does not harm the internal wireless card. I booted the Starling right next to my wireless AP without the USB device plugged in and as long as I maintained 100% signal strength, it worked fine. With my set-up, I get about 10-15 foot range on the internal card. With the USB device plugged in, I can connect out past 40 feet with a signal strength reported as 30%.

That's it. If I were to give up on the internal card for good, I'm sure that there is a way to turn it off in the bios. That would eliminate the second dialog box. But I am still hoping that S76 will come through on the driver. The USB device is a little ungainly given the small size of the Starling.

Joe

---

### Post by ZhuaSD on 2009-07-22
I just upgraded to 9.04 from 8.04, well it was a fresh install to be clear. I always had a buggy ethernet in Ubuntu (it would drop a couple times a day, pretty consistently, and not re-connect).  Here are my specs:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS 



That Realtec card is one I just threw in there, as I was upgrading and also trying to solve this problem once and for all.  But it didn't seem to fix it. My connection still drops sometimes.

My fix was first to edit /etc/network/interfaces as explained in [this post]("http://ubuntuforums.org/showpost.php?p=7364382&postcount=16"), changing 

iface eth0 inet manual

to 

iface eth0 inet dhcp


that got me online at first, after pppoeconf didn't seem to get the job done.  I guess I needed a restart after that, then it picked up.
 
It is important to remember that if 'plog' returns nothing, like this:
```

ZhuaSD@ZhuaSD-desktop:~$ plog
ZhuaSD@ZhuaSD-desktop:~$ 
```

Then a quick poff pon might get things going.  I also think the same is true for pppoeconf, if it can't find your concentrator, it might be because you have an 'unmanaged' connection already.

So, I could then connect manually by turning the connection off and then on, but the network manager still had a red 'x' in it and said the device was not managed.

So to fix that, I followed [this fix]("http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html") to open the right file:

```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```

and changed managed=false to managed=true.

So now my network manager is working, but I still have to poff and then pon when I start up, and the connection still drops sometimes, but a quick poff pon does the trick.

One weird thing is now I am using eth1, not eth0, so that first part of the fix might not matter anymore.  I was testing out the new ethernet card, and didn't disable the on-board NIC at first.  The connection worked at first but then didn't, so I disabled it later.
 
So it is working, at least.  Hope this helps!!  :P

---

### Post by walt.smith1960 on 2009-07-26
I have Jaunty running on 1 notebook, 1 netbook and 1 desktop. I was having problems with the desktop using a Linksys WUSB54gVer4. Using NetworkManager, it would be recognized correctly but was not recognized as even present when awakening from suspend. Unplugging and replugging the USB cable would eventually recogize the device as present but still took some clicking to get a connection. Once I got a connection, it would drop and reconnect frequently.

I installed WiCD. WiCD is not as intuitive to set up but so far seems more stable with this PC/adapter combo. Network Manager works fine on the Notebook (Thinkpad R61i) and Netbook (Asus EeePC 1005HAB). I still have to to do the unplug/replug routine when the desktop machine comes out of suspend. I have to do the unplug/replug dance with a USB HP printer as well so this is likely a Jaunty/PC issue.

edit: The desktop is a Gigabyte AMD MoBo circa 2004/2005

---

### Post by epicoder on 2009-07-27
This is a quick 'n dirty workaround for the Jaunty NetworkManager bug in which it fills the WPA2 password box with hex, I cannot guarantee this will work for everybody.

Launch seahorse (passwords and encryption keys), go to the tab 'Passwords', find 'Network secret for [name of connection]/802-11-wireless-security/psk', deny NetworkManager Applet and nm-connection-editor write and delete access, and always use seahorse to change your password.

Note: **DO NOT** deny nm-connection-editor and NetworkManager Applet read access, or you will not be able to connect whatsoever!

---

### Post by ScottNN on 2009-08-04
Hi,  I tried the workaround for the WiFi Link 5100 and got the following the error...

sudo modprobe iwlagn  lln_disable=1 lln_disable50=1
FATAL: Error inserting iwlagn (/lib/modules/2.6.28-14-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)

Any idea what the problem is?

(I'm new so I'm not too sure how to go about debugging this kind of stuff)

Thanks in advance for any advice.

S

---

### Post by ScottNN on 2009-08-05
Hey,  I have spotted my problem.  Spent so much time on trying to fix this yesterday I failed to see that the actual command used '1' instead of 'l'.

Now that I have ran this command I still cannot connect gain access to the router.  Ubuntu can see the router,  ubuntu connects to the router but the password I have entered is in ASCII.  When I view the password it appears to have been converted to HEX.  How do I resolve this?

Cheers

S

---

### Post by djrudra on 2009-08-06
hi

after trying to solve the problem for the last day and half after fresh installing 9.04 on my erstwhile windows Dell Inspiron 6400 with broadcom 4311 rev 01 wireless

i came upon this:

[http://caytin.wordpress.com/2009/07/21/how-to-broadcom-wireless-in-ubuntu-jaunty-jackalope/](http://caytin.wordpress.com/2009/07/21/how-to-broadcom-wireless-in-ubuntu-jaunty-jackalope/)

that in itself was no help at all.. 

then i came upon this:

[http://ubuntuforums.org/archive/index.php/t-995059.html](http://ubuntuforums.org/archive/index.php/t-995059.html)

there was something there that caught my eye...

something about network manager

so i quickly apt-cache searched it, installed it, restarted it 


SHAZAAAM

hope this helps...

yours,

noob

---

### Post by songmaster on 2009-08-08
I've had significant difficulties getting my HP Pavillion dv7 laptop (ath9k) to stay associated with my Linksys WRT54G AP under Jaunty [Kubuntu]. My current workaround is to turn off Network Manager and connect manually. Although slightly annoying, at least it works and stays associated for several hours. The AP is not configured to use encryption (WEP, WPA or WPA2) and has essid broadcasts turned off. It also runs a DHCP server which gives me my IP address.

Here's what I do, in case it's useful to anyone else (these instructions are not specific to the ath9k, they may work on other systems with similar problems):

First remove any desktop widgets that connect to NetworkManager, they are likely to die at the first step below.

Then open a terminal window (Konsole on kubuntu) and run the commands shown in **bold** below (replace the text in ***bold italic*** with your AP's SSID). You'll get prompted for your password the first time you run sudo:

```
dv7$ **sudo invoke-rc.d NetworkManager stop**
[sudo] password for user:
 * Stopping network connection manager NetworkManager                    [ OK ]
dv7$ **sudo iwconfig wlan0 essid '*YOURSSID*'**
dv7$ **sudo dhclient wlan0**
Internet Systems Consortium DHCP Client V3.1.1                                  
Copyright 2004-2008 Internet Systems Consortium.                                
All rights reserved.                                                            
For info, please visit http://www.isc.org/sw/dhcp/                              

Listening on LPF/wlan0/00:23:xx:xx:xx:xx
Sending on   LPF/wlan0/00:23:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.100 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.100 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1                       
bound to 192.168.1.100 -- renewal in 34171 seconds.
dv7$
```The association with the AP doesn't occur until the dhclient runs above. You can check that it has worked using iwconfig &#8212; you're connected if you see the Access Point's MAC address on the second line of output (although if it failed, you won't have seen the DHCPACK line in the output above either):

```
dv7$ **iwconfig wlan0**
wlan0     IEEE 802.11abgn  ESSID:"<myEssid>"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:13:xx:xx:xx:xx
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
dv7$
```- Andrew

---

### Post by vegesm on 2009-08-12
This fix is for the BCM4312 wireless card(maybe works for other BCM43xx cards). If you can join to the AP with SSID broadcast but not with hidden SSID this will help you:
[http://worldofxor.blogspot.com/2008/12/it-works-broadcom-official-wireless.html](http://worldofxor.blogspot.com/2008/12/it-works-broadcom-official-wireless.html)

---

### Post by BigCityCat on 2009-08-13
I'm posting this as a solution to broadcom 4328 driver issue. I use this on Kubuntu 9.04 with Kde 4.3. It may work on other distros. I don't know.

I am not an expert. I am posting a link from a thread I started where someone helped me fix this. So that the right person gets credit. The link does not have the whole solution. This post will. Only use this if your sure it fits your problem.

[http://ubuntuforums.org/showthread.php?t=1238421](http://ubuntuforums.org/showthread.php?t=1238421)

My dv 9700 laptop did not recognize any wireless. Ndiswrapper could not use any drivers that would work for my system. If you have ndiswrapper you need to purge it before you do this. The broadcom driver for my system does not support Linux as far as I know.

to purge ndiswrapper

> sudo apt-get remove --purge ndis*





here is the next step.

> sudo rmmod wl ssb

> Sudo modprobe wl

> iwconfig

> lsmod | grep b43

> lsmod | grep wl

> Sudo ifup wlan0

> sudo cat /var/log/messages | grep wl

> sudo lshw -c networks








> sudo kate /etc/modules

add the following > wl at the end of the file in kate, and proof read save











> sudo kate /etc/modprobe.d/blacklist.conf



add the following lines to the end of the file, proof read and save

> blacklist ssb
blacklist rmmod wl ssl
blacklist b43legacy
blacklist b43









> sudo rmmod wl ssb

> sudo modprobe wl

> sudo kate /etc/rc.local

add the following lines at the end of the file but before "exit 0"  proof read and save.

> rmmod wl ssb
sleep 3
modprobe wl

restart and see

Now that worked for me. Like I said Chili555 is the one who solved this for me.

---

### Post by chili555 on 2009-08-13
There are one or two misleading things here. Purge ndiswrapper as he said. Then *sudo kate /etc/modules* to add a new line:```
wl
```Not Kate, but kate and not WL, but wl. 

His blacklist.conf is correct.

Evidently, the module *ssb* loads even if it's blacklisted (go figure), so we must *sudo kate /etc/rc.local* to add:```
rmmod wl ssb
sleep 3
modprobe wl 
```Add it right above 'exit 0' As always, proofread carefully, save and close kate. After a reboot, your wireless should work correctly.

NB!!! This works, as far as I know, for the Broadcom 4328 ***only***.

---

### Post by BigCityCat on 2009-08-13
> **chili555 said:**
> There are one or two misleading things here. Purge ndiswrapper as he said. Then *sudo kate /etc/modules* to add a new line:```
wl
```Not Kate, but kate and not WL, but wl. 

His blacklist.conf is correct.

Evidently, the module *ssb* loads even if it's blacklisted (go figure), so we must *sudo kate /etc/rc.local* to add:```
rmmod wl ssb
sleep 3
modprobe wl 
```Add it right above 'exit 0' As always, proofread carefully, save and close kate. After a reboot, your wireless should work correctly.

NB!!! This works, as far as I know, for the Broadcom 4328 ***only***.

Fixed and as always, thanks.

---

### Post by BigCityCat on 2009-08-13
I noticed there is a small issue with the modules blacklisted in blacklist.conf

blacklist rmmod wl ssl

should read 

blacklist rmmod wl ssb

but I actually copied and pasted my file into this solution so that is how it is on my system and it is working. I have no intention on changing it for now.

---

### Post by rtrdom on 2009-08-14
Using both Thinkpad R61i with Intel PRO Wireless 4965 AG or AGN wireless adapter, and a Compaq X1030US with Intel PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04).  I tried several hours to find the problem
with the computers which both would access a NETGEAR Model WPN802 V2 while in Windows (both computers are dual boot because I teach basic Windows to old folk) but would see and NOT access in UBUNTU. Finally solved problem.... I took both computers to other open networks and they
both worked flawlessly in either OS. Took both computers to my encrypted
(WPA2 static IP) network and they worked flawlessly without any adjustment. Problem.... WPN802 V2 is/has going/gone bad. It
has quit working (accepting) from my Ubuntu 9.04 but works with Windows XP.
Another item. An early model of WRE54G was not "syncing" with the access
point, even when reset by directions. 
    Hope this helps someone else.

---

### Post by Feareilo on 2009-08-19
Output of lsusb:

```
Bus 002 Device 012: ID 03eb:7614 Atmel Corp. AT76c505a Wireless Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I don't know what this all means but I'm using an SMC EZ Connect Wireless USB adapter. Model number: SMC2662W.

**Problem:** In Ubuntu 8.04 (Hardy Heron) I couldn't connect through the Network Manager so I used to type this in a terminal:

```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "Networ-name"
sudo iwconfig wlan0 key open PASSWORD
sudo dhclient wlan0
```

However, this didn't work in Ubuntu 9.04 (Jaunty Jackalope).

My wireless card is connected via USB and it has two leds: a red one and a green one. I always use the Internet so I don't see any point in disconnecting it, even when the computer is off. Whenever I turned on the computer, both leds used to turn on in my USB card. That changed with Jaunty. Now only the red one turns on and I can't connect with neither the Network Manager nor the thing I typed in the terminal.

**Partial Solution:** Disconnect the card and reconnect it until the green led turns on too. This way, I now *can* connect to the Internet using the Network Manager.
If anyone knows a better solution please tell me.

EDIT: By the way, I'm dual booting Ubuntu 9.04 and UbuntuStudio 8.04 and this problem only happens with Jaunty.

---

### Post by jbrice on 2009-08-24
Dell Inspiron 1525 - with standard Intel Pro Wireless card 3945ABG - connects to our WPA-secured Netgear router reliably and quickly on system boot. However on resume from suspend, it seems to take a random period of time before it tries to re-connect (which it always succeeds in doing - eventually). This can be almost instantaneous (hurrah!), minutes (oh hurry up!), or lots of minutes (aargh, should have used WinXP).

This PC uses the standard Jaunty install double-booted with WinXP - the latter always connects quickly and reliably with the same router.

Is this a manifestation of any of the problems listed in this thread, or something different?   

James B.

---

### Post by uylug on 2009-08-25
Wireless connection has a high packet loss rate using a TrendNet 424UB v3 on Jaunty using the rtl8187 built in module.

Solution:

Run this command after connecting to WiFi

```
sudo iwconfig *<interface>* retry *<high_value>*
```Like

```
sudo iwconfig wlan0 retry 999999
```

---

### Post by dzuchowski on 2009-08-26
> **Evil Dax said:**
> Jaunty64, Intel WiFiLink 5100 and WPA2

lspci:
07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

OS:
Jaunty64: 2.6.28-11-generic

Issue:
non-secured and WEP working, while WPA and WPA2 fail to connect

Solution:
download latest microcode from Intel:
[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz)
put the file into /lib/firmware

change modprobe:
```

sudo modprobe -r iwlagn
sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

```And you can connect to WPA2

how do you copy the intel microcode from intel link to the /lib /firmware

---

### Post by fidelandche on 2009-08-27
Hi,

  Had a problem with my Gateway ML6226B laptop, limited signal strength which meant the connection would drop a lot if using Transmission at the same time as trying to browse the Internet.

  The wireless card is inbuilt and it is Realtek RTL8187, what I did was put this code in the terminal  and then reboot problems solved. No more dropped connection or slow FF
sudo apt-get install linux-backports-modules-jaunty

---

### Post by T-D on 2009-09-01
Jaunty for AMD64, Asus WL138g V2 PCI wireless card, Broadcom BCM4318 [AirForce One 54g] chip

I followed [this howto](http://ubuntuforums.org/showthread.php?t=285809) (ubuntu forums) to get ndiswrapper installed and working. However, the wireless wouldn't connect to any networks, or even detect them.

Some searching led me to  [this thread](http://ubuntuforums.org/showpost.php?p=5976351&postcount=5) (ubuntu forums). After making those modifications, /var/syslog said I was missing the firmware for my card, so I went [here](http://linuxwireless.org/en/users/Drivers/b43) (linuxwireless.org). My chipset, the BCM4318, was listed as supported, so I installed the firmware per the instructions. It now works happily.

Big thanks to UbuntuForums, LinuxWireless, and Google. I hope this helps somebody.

---

### Post by arnold15 on 2009-09-06
Please help me with my problem.. 
Its about Wireless connection:
[http://ubuntuforums.org/showthread.php?t=1258739](http://ubuntuforums.org/showthread.php?t=1258739)

Thanks!

---

### Post by k33bz on 2009-09-10
> **Curvature_Tensor said:**
> sudoedit /etc/NetworkManager/nm-system-settings.conf

edit the file to read
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

save and reboot.


Worked for bcm4311 wireless card and Atheros AR242x wireless card.  Also worked for Marvell 88E8038 wired Ethernet port

Hi, I have an Atheros AR242x wifi card on my laptop, I first found this post [http://nuclear-imaging.info/site_content/2009/01/30/atheros-5007eg-now-works-in-jaunty-jackalope/]("http://nuclear-imaging.info/site_content/2009/01/30/atheros-5007eg-now-works-in-jaunty-jackalope/") which did not work to get my wifi working. 

So I ran into this post after that, and tried it, but yet to no avail did it work either. I am thinking it might be because I messed up by following the first post I had found. Can anyone help me with this.


SOLVED WITH THIS POST [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html/comment-page-1]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html/comment-page-1")

---

### Post by jtownsend90 on 2009-09-12
I am not sure if this has been resolved, but there is as many of you may know to which the network manager applet does not boot at start up and wont boot with the sudo nm-applet start command nor change the nm-applet defaults so this is probably an old work around but assuming you have the wirless drivers installed then you can add a program to the panel called network viewer or manager or something like that and then change the settings from lo to your wireless device most likly either wlan0 or eth1 then go to system>prefrences it think its called and look for a program call network manager I am sorry for saying "I think" a lot for I am not at an ubuntu system at the moment anyways open that up go to wireless and add a new connection enter your creditentials including SSID and security (if any) and then make sure to check the box that says save to system as well you will be prompt for a password enter your administrative password it will save and you should now be connected to the internet you can check on it by the applet in the top panel you previously added. :) this has worked for me everytime, sometimes if using the virtual drivers under system>administration>hardware then you may have to deactivate and then choose activate again to enable your wireless adapter. just tinker around a bit and you should have wirelell running in no time without the need for network manager applet.

---

### Post by fate12 on 2009-09-15
oops, please delete.

---

### Post by Feareilo on 2009-09-17
> **Feareilo said:**
> Output of lsusb:

```
Bus 002 Device 012: ID 03eb:7614 Atmel Corp. AT76c505a Wireless Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

I don't know what this all means but I'm using an SMC EZ Connect Wireless USB adapter. Model number: SMC2662W.

**Problem:** In Ubuntu 8.04 (Hardy Heron) I couldn't connect through the Network Manager so I used to type this in a terminal:

```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "Networ-name"
sudo iwconfig wlan0 key open PASSWORD
sudo dhclient wlan0
```

However, this didn't work in Ubuntu 9.04 (Jaunty Jackalope).

My wireless card is connected via USB and it has two leds: a red one and a green one. I always use the Internet so I don't see any point in disconnecting it, even when the computer is off. Whenever I turned on the computer, both leds used to turn on in my USB card. That changed with Jaunty. Now only the red one turns on and I can't connect with neither the Network Manager nor the thing I typed in the terminal.

**Partial Solution:** Disconnect the card and reconnect it until the green led turns on too. This way, I now *can* connect to the Internet using the Network Manager.
If anyone knows a better solution please tell me.

EDIT: By the way, I'm dual booting Ubuntu 9.04 and UbuntuStudio 8.04 and this problem only happens with Jaunty.

This workaround only worked on my desktop. It wouldn't solve anything on my laptop. What I did on my laptop was delete Network Manager like this:
```
sudo aptitude remove network-manager
sudo aptitude remove network-manager-gnome
```

And connect the way I used to (detailed on my last post).

Note:
I uninstalled Network Manager on my desktop to see if the laptop fix would work here too. It doesn't. I had to install WICD. I am happy running WICD now.


So in summary:


For my desktop:
If I have NM, disconnecting and reconnecting my USB wireless card works.
Deleting NM and trying to connect via terminal won't work.
Deleting NM and installing WICD works really good.

For my laptop:
Disconnecting and reconnecting USB wireless card won't work.
Deleting NM and installing WICD won't work either.
Deleting NM and deleting WICD (if you have it) and connecting via terminal works.

---

### Post by windom on 2009-09-24
I would like to add my experience. It was posted on another topic. The only reply from the poster was 'Bump'. I'd hate to see it go to waste so I will post a link to it here.

[http://ubuntuforums.org/showthread.php?t=1272010&page=1#9](http://ubuntuforums.org/showthread.php?t=1272010&page=1#9)

It is for a BCM4311. In addition to the client setup one must consider if one did something wrong on the AP in the settings so make sure you check that too. When I used Mac address filtering I would run into trouble when using a new NIC because I would forget to add it to the Mac list. These things happen so be thorough. Use as simple a test environment as possible. You can make things spiffy after finding your solution. If you are using more than one AP in your environment, make sure they are set to different non-overlapping channels i. e. use channels 1, 6, and 11.

Since I posted, I switched over to dhcp from static. Like butter. 

windom

---

### Post by DougieFresh4U on 2009-09-27
> **Curvature_Tensor said:**
> sudoedit /etc/NetworkManager/nm-system-settings.conf

edit the file to read
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

save and reboot.


Worked for bcm4311 wireless card and Atheros AR242x wireless card.  Also worked for Marvell 88E8038 wired Ethernet port
have tried this but can not get it to save :confused:

---

### Post by ennoil on 2009-10-07
With the following wired ethernet:

lspci:
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller (rev 16)
l
shw -class network:
  *-network
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:22:68:63:69:fb
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A latency=0 link=no module=sky2 multicast=yes po
rt=twisted pair speed=100MB/s

The wired connection comes up and down more often than a yo yo. It makes the network unusable. I tried the work around mentioned earlier for a Marvell card but it did not work.
Thanks,
John

---

### Post by manish.rjn on 2009-10-08
> **dzuchowski said:**
> how do you copy the intel microcode from intel link to the /lib /firmware

Problem solved. thanks a lot.
I tried this suggestion and got my problem of secure network connection solved.
For copying I used the terminal with root permission.

The problem I had was-
I could connect to unsecured networks and networks with WEP encription, but not WPA.
wireless card is: intel PRO/Wireless 4965 AG or AGN [Kedron]
I am using Ubuntu 9.04

Now, however, I have to enter the commands everytime I restart to change the modprobe.
any suggestion how to make this automatic or parmanent?

thanks in advance.

---

### Post by ArcaVex on 2009-10-08
Hi, I am using netgear WG111T,  atheros chipset. 

**My Problem**
I installed the two windows drivers with ndiswrapper and connected with KNetworkManager, and it ran fine for about 20 seconds. Then the connection dropped, but stated it was still connected.  Being very inexperienced with Linux wireless i hunted around forums and people suggested WICD was a better network manager. Installed that, connected fine, but after a restart wouldn't connect. It just hung on "validating authentication"  (using WEP). Then once i refreshed the networks the SSID of my home router had vanished.

**My Solution**
Unplug the WG111T until booted up. Plug in the card, open terminal and type:

sudo iwconfig wlan0 essid wapssid     (wapssid = ssid of network you wish to connect to)
sudo iwconfig wlan0 key wepkey       (wepkey = WEP Hex key, not passphrase).
sudo dhclient wlan0

I'd rather type this on the odd occasion when i restart the machine than spend a few hours trying to work out why WICD has a problem with WEP?  Perhaps something todo with using wpa_supplicant?
 
I reccommend using CLI for most things :)

---

### Post by -Oz- on 2009-10-09
I/O bus ( USB)
Make (Tp-Link)
Model ( TL-WN721N )

How on earth do i make it work with my Ubuntu jaunty??? someone plz hellpppppppppp

---

### Post by -Oz- on 2009-10-10
I have installed the drivers with ndiswrapper...and the "ndiswrapper -l" command shows the following output

netathur : driver installed
	device (0CF3:9271) present

but the device isnt working....no lghts blinking....works with windows system. Any help would be appreciated now.

---

### Post by jerk_shop on 2009-10-27
Hi I am new to Ubuntu and especially Linux, well to be specific I have a slow wireless connection on my laptop which is a Dell Inspiron 6400. It has Vista on it and wireless connection works fine and runs normally but when I go to Ubuntu to update things its pretty slow like running at 5kBps. So I was wondering whats wrong I really don't know where to start to be honest. I've been searching for solutions for hours now still no luck here are my details.

I/O bus: Onboard
Make Intel
Model 945
Chipset: Broadcom, I'm not sure

thanks, I'll try to connect this laptop directly to my router see if anything changes.

---

### Post by northd_tech on 2009-10-27
The Broadcom is probably one of the easier/better supported chipsets to setup under Linux (now, but it wasn't that way a year ago).  My HP laptop has the Broadcom 4321AG (but it sometimes reports as a 4328  ).

Use the Synaptic Package manager to install all things "ndiswrapper" in the quick search box. ndiswrapper-1.55 or newer, ndiswrapper-common, ndiswrapperutils, and there is also a GTK GUI for it that you will want to get-  "ndisgtk" as I recall.

[http://packages.ubuntu.com/jaunty/ndisgtk](http://packages.ubuntu.com/jaunty/ndisgtk)

Broadcom has recently released a driver for Linux (in both 32 and 64 bit versions).  It can be found here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I believe that is loadable as a kernel module.  Otherwise, there is a lot of good info at this page:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Their drivers chart/list is at:

[http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)  

----------------------------------------------------------------------------------------------
There are a bunch of threads about Broadcom wireless cards here at this forum:

                         [Broadcom Wireless Setup for Hardy (Step by step)]("http://ubuntuforums.org/showthread.php?t=766560&highlight=Broadcom+4321")
[http://ubuntuforums.org/showthread.php?t=766560&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=766560&highlight=Broadcom)

HOWTO: Broadcom 4318 Wireless Cards
[http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=197102&highlight=Broadcom)

How to install native broadcom drivers for BCM4311, BCM4312, BCM4321, and BCM4322
[http://ubuntuforums.org/showthread.php?t=896713&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=896713&highlight=Broadcom)

Comprehensive ndiswrapper troubleshooting guide
[http://ubuntuforums.org/showthread.php?t=885847&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=885847&highlight=Broadcom)

HOW TO: Configure wireless cards with Broadcom chipsets
[http://ubuntuforums.org/showthread.php?t=25683&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=25683&highlight=Broadcom)

Using the b43 driver instead of the Broadcom STA wireless driver
[http://ubuntuforums.org/showthread.php?t=1071298&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=1071298&highlight=Broadcom)

Broadcom Wireless (im a complete noob to linux and need help)
[http://ubuntuforums.org/showthread.php?t=1202760&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=1202760&highlight=Broadcom)

HowTo: Broadcom BCM43xx in 5 minutes with ndiswrapper/WPA for fresh installs
[http://ubuntuforums.org/showthread.php?t=870086&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=870086&highlight=Broadcom)

Having trouble w/ Broadcom on Hardy? Give this a shot
[http://ubuntuforums.org/showthread.php?t=880218&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=880218&highlight=Broadcom)

Broadcom Wireless for 8.10
[http://ubuntuforums.org/showthread.php?t=963978&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=963978&highlight=Broadcom)

Can't get wireless Broadcom WiFi Adapter to work with Ubuntu 9.04?
[http://ubuntuforums.org/showthread.php?t=1154403&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=1154403&highlight=Broadcom)

I need a driver for my Broadcom Wireless built in system
[http://ubuntuforums.org/showthread.php?t=1122287&highlight=Broadcom](http://ubuntuforums.org/showthread.php?t=1122287&highlight=Broadcom)

[[SOLVED] Broadcom 4312 (BCM4312) ]("http://ubuntuforums.org/showthread.php?t=1010751&highlight=Broadcom+4321")
[http://ubuntuforums.org/showthread.php?t=1010751](http://ubuntuforums.org/showthread.php?t=1010751)

---

### Post by atirox on 2009-10-28
Broadcom BCM4306 Rev 3 Wireless Workaround

Since Broadcom and Linux are one step below arch enemies, Broadcom has yet to release drivers for their very popular BCM4306 series wireless card. Since they won't or don't want to release the drivers, any BCM4306-based card will not work with Linux. This issue is well known, however, for a newbie to the Linux world, such as myself, it can be a very large headache. 

Previous to the steps below, I had gone into the Hardware Drivers page and activated the Broadcom B43 wireless driver. This enabled the card, but for some reason, it wasnt interfacing correctly. I decided to add the NDIS Wrapper Commons and Utils 1.9. This still wouldnt work, so i deactivated the Broadcom B43 wireless driver, as well as all of the NDIS Wrapper packages. Then I tried activating the Broadcom B43 wireless driver again, and for some reason it worked. I assume that when the ndiswrapper commons and utils 1.9 were removed, it also removed some settings that werent allowing the Broadcom B43 wireless driver to work correctly.

Here is the condensed version of how I got my card to work.

1. Open Synaptic Package Manager. Enter password if necessary.
2. Select and install the following packages.
```
ndiswrapper-utils-1.9
ndiswrapper-common
b43-fwcutter
```
3. When installation finishes, remove the three packages that you just installed.
4. Open Hardware Drivers.
5. Activate the Broadcom B43 wireless driver.

This should provide the Broadcom card with the correct firmware, and allow the Linux kernel to use the device.

Please note that I am not a Linux guru, and therefore I cannot provide very good help if someone requires it. I will, however, do the best I can.

---

