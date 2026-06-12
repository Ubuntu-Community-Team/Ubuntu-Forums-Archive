---
title: "More wireless networking woes (broadcom &amp; 11.04)"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by epwolfram on 2011-08-22
Hello I made the mistake of creating a new user account and deleting the old one in Ubuntu.  Now I can't connect to my wireless network.  I think that I have the correct drivers installed, but I am unable to see (discover?) wireless networks and don't even have any wireless options in the upper right corner.  I am pretty frustrated with this.
 
Let me tell you what I know. Please help if you can, or at least point me in the right direction.
 
Laptop: Dell Inspiron 1721
Ubuntu 11.04
Network Controller: Broadcom BCM4311 802.11b/g WLAN
 
How do I set up the ability to see wireless networks?
Is there a way to verify that I have the correct network device drivers installed?

I am a non-experienced linux user, so you will probably have to be specific with descriptions and assume I don't know how to do things.

Thanks for your help.

-Eric

---

### Post by garvinrick4 on 2011-08-22
If no applet try this, if just all greyed out install proper drivers. Install with wired and then remove wire and reboot.
```
nm-applet
```Does it pop up in right hand corner.

#Open Synaptics and check by typing in "bcm" without quotes and check
on driver situation installed. The two marked should be installed click on screenshot.
remove any other bcm installed just want those two.

---

### Post by nm_geo on 2011-08-22
Hi welcome.. [COLOR=RoyalBlue]**Oops you got it garvinrick4**
[/COLOR] 
Open a terminal Ctrl-Alt-t

Copy and paste the following in the terminal

```
lspci -nn | grep 0280
``````
lsmod
``````
sudo lshw -C network
```Copy the results and we will have some place to start.

---

### Post by epwolfram on 2011-08-22
eric@UbuntuLaptop:~$ lspci -nn | grep 0280
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)


eric@UbuntuLaptop:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
b44                    36000  0 
snd_hda_codec_idt      71137  1 
joydev                 17606  0 
snd_hda_intel          33176  2 
ssb                    51945  1 b44
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
radeon                982152  3 
snd_seq_midi_event     14899  1 snd_seq_midi
dell_wmi               12681  0 
sparse_keymap          13898  1 dell_wmi
wl                   2568244  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
dell_laptop            13827  0 
dcdbas                 14438  1 dell_laptop
snd_timer              29602  2 snd_pcm,snd_seq
edac_core              53845  0 
r852                   18246  0 
ttm                    76664  1 radeon
sm_common              16817  1 r852
psmouse                73535  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
nand                   55112  2 r852,sm_common
nand_ids               12723  1 nand
nand_ecc               13230  1 nand
drm_kms_helper         42136  1 radeon
serio_raw              13166  0 
k8temp                 13016  0 
mtd                    27900  2 sm_common,nand
edac_mce_amd           23464  0 
drm                   227534  5 radeon,ttm,drm_kms_helper
snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13400  1 radeon
soundcore              12680  1 snd
sp5100_tco             13744  0 
video                  19438  0 
shpchp                 37297  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lib80211               14991  1 wl
i2c_piix4              13303  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
usbhid                 46956  0 
sdhci_pci              13989  0 
hid                    91020  1 usbhid
crc_itu_t              12707  1 firewire_core
sdhci                  27387  1 sdhci_pci
ahci                   25951  3 
libahci                26642  1 ahci
pata_atiixp            13165  1 


eric@UbuntuLaptop:~$ sudo lshw -C network
[sudo] password for eric: 
  *-network

---

### Post by epwolfram on 2011-08-22
eric@UbuntuLaptop:~$ nm-applet
An instance of nm-applet is already running.

** (nm-applet:1850): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

---

### Post by nm_geo on 2011-08-22
Eric is this all that showed up?

> eric@UbuntuLaptop:~$ sudo lshw -C network
[sudo] password for eric: 
  *-network

That one takes awhile could you run it again and paste the results..

---

### Post by epwolfram on 2011-08-23
oops, I accidentally must have cut it off:

eric@UbuntuLaptop:~$ sudo lshw -C network
^Ceric@UbuntuLaptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:85:33:1d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.100 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:fe5fe000-fe5fffff

---

### Post by nm_geo on 2011-08-23
Ok, I see no b43 and no wireless listed?

```
sudo apt-get install b43-fwcutter 
```

```
sudo apt-get install firmware-b43-installer
```

Those are the wireless driver and firmware I would recommend.

---

### Post by lkjoel on 2011-08-23
If the technique by nm_geo doesn't work after a reboot, could you run the Network Info script (in my signature), and attach the generated file?

---

### Post by epwolfram on 2011-08-23
eric@UbuntuLaptop:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:170
14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by epwolfram on 2011-08-23
NM_GEO I tried running both of those and have no change, still no wireless network options.

---

### Post by lkjoel on 2011-08-23
We need more technical info about your card. It might be too old.
Please run the Network Info script in my signature and attach the generated file.

---

### Post by epwolfram on 2011-08-23
IKJoel, is this enough?

eric@UbuntuLaptop:~$ wget [http://network-info.sourceforge.net/network-info.sh](http://network-info.sourceforge.net/network-info.sh) && bash network-info.sh
--2011-08-22 23:25:24--  [http://network-info.sourceforge.net/network-info.sh](http://network-info.sourceforge.net/network-info.sh)
Resolving network-info.sourceforge.net... 216.34.181.96
Connecting to network-info.sourceforge.net|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7197 (7.0K) [application/x-sh]
Saving to: `network-info.sh'

100%[======================================>] 7,197       --.-K/s   in 0.04s   

2011-08-22 23:25:24 (157 KB/s) - `network-info.sh' saved [7197/7197]

[sudo] password for eric: 
Checking for sudo    ...     [  OK  ]
Checking for ifconfig ...     [  OK  ]
Checking for iwconfig ...     [  OK  ]
Checking for iwlist  ...     [  OK  ]
Checking for lshw    ...     [  OK  ]
Checking for nm-tool ...     [  OK  ]
Checking for uname   ...     [  OK  ]
Checking for cat     ...     [  OK  ]
Checking for rfkill  ...     [  OK  ]
Checking for lspci   ...     [  OK  ]
Checking for lsb_release ...     [  OK  ]
Checking for lsmod   ...     [  OK  ]
Checking for lsusb   ...     [  OK  ]
Checking for dmesg   ...     [  OK  ]
Gathering information...
[                                                                               [======                                                                         [============                                                                   [==================                                                             [========================                                                       [==============================                                                 [====================================                                           [==========================================                                     [================================================                               [======================================================                         [============================================================                   [==================================================================             [========================================================================       [============================================================================== [===============================================================================[===============================================================================[====================================================================================================
Information has been gathered into NETWORK-INFO.txt

---

### Post by lkjoel on 2011-08-23
Sorry, I wasn't clear enough. Please attach the NETWORK-INFO.txt file (which is located in your home directory).

---

### Post by epwolfram on 2011-08-23
IKJoel, I've had it running on this machine earlier today.

"**NETWORK-INFO.txt**:
		Your file of 142.7 KB bytes exceeds the forum's limit of 19.5 KB for this filetype. 	"

---

### Post by epwolfram on 2011-08-23
Is there another way to send it?

---

### Post by Actonix on 2011-08-23
You might have a common problem to do with proprietary drivers and/or the card being blacklisted


- open the '*Synaptic Package Manager*' and search for 'bcm' and uninstall the 'bcm-kernel-source' package


- make sure the 'firmware-b43-installer' and the 'b43-fwcutter' packages are installed, installing should take care of configuring your device



Open a terminal up and type:- "cat /etc/modprobe.d/* | grep bcm"  ... to see if **bcm43xx** is *blacklisted*,     

... if it is, type "cd /etc/modprobe.d/"
[FONT=Verdana]...[/FONT] and in there type "sudo gedit blacklist.conf"  

... put a  hash "#" in front of the line: blacklist bcm43xx

... save the file and reboot and hopefully your sorted unless you need to make changes to suit your particular setup which you can do from Connections or Network Manager


---edited---

Whooops, did not see that you were in good hands, my bad, gl (y)

---

### Post by epwolfram on 2011-08-23
Does this mean it IS blacklisted?

eric@UbuntuLaptop:~$ cat /etc/modprobe.d/* | grep bcm
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist bcm43xx
blacklist bcm43xx

---

### Post by lkjoel on 2011-08-23
OK that's a bug in the script. I'll fix it now.

---

### Post by nm_geo on 2011-08-23
Eric the firmware was not correct however there may be a different problem too.

```
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 [COLOR=Red]firmware-b43-lpphy-installer[/COLOR]
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

You chipset needs 

[COLOR=Black]**firmware-b43-installer**[/COLOR]

follow lkjoel suggestions.

---

### Post by lkjoel on 2011-08-23
Fixed. Please re-download and run the script, and attach the generated file (should be NETWORK-INFO.txt.gz)

---

### Post by epwolfram on 2011-08-23
[B]Same thing man..

NETWORK-INFO.txt[/B]:
		Your file of 155.6 KB bytes exceeds the forum's limit of 19.5 KB for this filetype.

---

### Post by epwolfram on 2011-08-23
no, wait this might be it?

**network-info.sh.2**:
		Invalid File

---

### Post by lkjoel on 2011-08-23
Sorry, not the NETWORK-INFO.txt file, but the NETWORK-INFO.txt.**gz** file.

EDIT:
Please run this Terminal command:
```
rm -rf network-info.sh
wget http://network-info.sourceforge.net/network-info.sh && bash network-info.sh

```
Then attach the NETWORK-INFO.txt.**gz** file.

---

### Post by epwolfram on 2011-08-23
Sorry, I don't have a file of that name.. search comes up empty

---

### Post by epwolfram on 2011-08-23
eric@UbuntuLaptop:~$ wget [http://network-info.sourceforge.net/network-info.sh](http://network-info.sourceforge.net/network-info.sh) && bash network-info.sh
--2011-08-22 23:46:03--  [http://network-info.sourceforge.net/network-info.sh](http://network-info.sourceforge.net/network-info.sh)
Resolving network-info.sourceforge.net... 216.34.181.96
Connecting to network-info.sourceforge.net|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7222 (7.1K) [application/x-sh]
Saving to: `network-info.sh.2'

100%[==========================================================>] 7,222       --.-K/s   in 0s      

2011-08-22 23:46:04 (85.9 MB/s) - `network-info.sh.2' saved [7222/7222]

[sudo] password for eric: 
Checking for sudo    ...     [  OK  ]
Checking for ifconfig ...     [  OK  ]
Checking for iwconfig ...     [  OK  ]
Checking for iwlist  ...     [  OK  ]
Checking for lshw    ...     [  OK  ]
Checking for nm-tool ...     [  OK  ]
Checking for uname   ...     [  OK  ]
Checking for cat     ...     [  OK  ]
Checking for rfkill  ...     [  OK  ]
Checking for lspci   ...     [  OK  ]
Checking for lsb_release ...     [  OK  ]
Checking for lsmod   ...     [  OK  ]
Checking for lsusb   ...     [  OK  ]
Checking for dmesg   ...     [  OK  ]
Gathering information...
[                                                                                                   [======                                                                                             [============                                                                                       [==================                                                                                 [========================                                                                           [==============================                                                                     [====================================                                                               [==========================================                                                         [================================================                                                   [======================================================                                             [============================================================                                       [==================================================================                                 [========================================================================                           [==============================================================================                     [====================================================================================               [===================================================================================================[====================================================================================================
Information has been gathered into NETWORK-INFO.txt

---

### Post by epwolfram on 2011-08-23
nm_geo, I think I have the b43 firmware installed.

-Eric

---

### Post by epwolfram on 2011-08-23
Ok, here is the networkinfo.txt.gz file.

---

### Post by nm_geo on 2011-08-23
> **epwolfram said:**
> nm_geo, I think I have the b43 firmware installed.
 
-Eric
 
You have STA (wl) wireless driver installed and that causes blacklist issues with b43 & ssb. Since your ethernet driver is b44 you must have the ssb module to make it operate properly. 
 
When you try to install the STA (wl) it creates a file that blacklists b43 & ssb. For some reason the ssb module can work around the blacklist but b43 can not. So you need to de-activate/remove the STA (wl) driver and comment out the blacklist of b43 and ssb.
 
Then make sure you have b43-fwcutter and firmware-b43-installer installed..
 
This link should help read message 51 through resolution.
[http://ubuntuforums.org/showthread.php?t=1816276&page=68](http://ubuntuforums.org/showthread.php?t=1816276&page=68)

---

### Post by lkjoel on 2011-08-23
I can't see your wireless device anywhere. Your system is clearly not recognizing it.

Follow nm_geo's advice.

---

### Post by epwolfram on 2011-08-23
Ok, the problem is still unresolved... but I think we are getting closer.  Thanks for your help so far.

Here is where we are at:

This gets my wireless running temporarily:
sudo modprobe b43


When I follow your instructions in the other thread, I get here:


eric@UbuntuLaptop:~$ cd /etc/modprobe.d
eric@UbuntuLaptop:/etc/modprobe.d$ ls
alsa-base.conf          blacklist-firewire.conf     blacklist-rare-network.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist-bcm43.conf    blacklist-modem.conf        libpisock9.conf
blacklist.conf          blacklist-oss.conf
eric@UbuntuLaptop:/etc/modprobe.d$ sudo rm broadcom-sta-common.conf
[sudo] password for eric: 
rm: cannot remove `broadcom-sta-common.conf': No such file or directory
eric@UbuntuLaptop:/etc/modprobe.d$ ^C
eric@UbuntuLaptop:/etc/modprobe.d$

---

### Post by epwolfram on 2011-08-23
OK, tried this:


eric@UbuntuLaptop:/etc/modprobe.d$ sudo rm blacklist-bcm43.conf 
eric@UbuntuLaptop:/etc/modprobe.d$ ls
alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf
blacklist-ath_pci.conf   blacklist-modem.conf         libpisock9.conf
blacklist.conf           blacklist-oss.conf
blacklist-firewire.conf  blacklist-rare-network.conf
eric@UbuntuLaptop:/etc/modprobe.d$

---

### Post by epwolfram on 2011-08-23
WICKED!!!  I am typing this message over my wifi.. after a reboot!

---

### Post by nm_geo on 2011-08-23
> **epwolfram said:**
> WICKED!!!  I am typing this message over my wifi.. after a reboot!

You are the man Eric ...
Excellent.

If you get a chance do the 

```
sudo lshw -C network
```

and post

---

### Post by epwolfram on 2011-08-23
Here you go:


[sudo] password for eric: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:85:33:1d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:21 memory:fe5fe000-fe5fffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:c8:19:8c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-11-generic firmware=410.2160 ip=192.168.1.102 link=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by epwolfram on 2011-08-23
Thanks again for your help, without you guys I'd back on Vista!

---

### Post by nm_geo on 2011-08-23
> **epwolfram said:**
> Thanks again for your help, without you guys I'd back on Vista!

No problem at all.. We enjoy helping out.  Is your nm-applet working correctly?  If not let me know we might have a fix for that too.

---

### Post by epwolfram on 2011-08-24
...hmm I am not sure.  I don't see anything title "Network Manager."  How can I find that?

---

