---
title: "Wireless connection is off and there is no switch for wireless"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by aria john on 2011-09-04
I am having a problem in Ubuntu 10.04 64 bit: there is no mechanical switch for Wireless in my Toshiba L635 laptop. 
On windows 7 I turn the wireless On by using the function and F8 buttons (Fn and F8 )
But unfortunately on Ubuntu this function ( function F8 ) is not working, so the wireless is always off and I don't know how to turn it on.

Any ideas how to solve this problem ?

---

### Post by LinuxFanBoi on 2011-09-04
On my Dell laptop, I can enter the CMOS and set the function key to require the 'Fn" key to be pressed in combination or not.  You might try to see if this can make the wireless on/off key function the primary function of that key.

My other suggestion is to boot into windows if you have it, and turn it on there and see if that resolves the issue; though I wouldn't blame you for not having windows installed.

---

### Post by aria john on 2011-09-04
Hi,

Yes I have them both installed (ubuntu and windows)
on windows 7, it is always on unless I turned it off
but on Ubuntu it is always off ,
can u please tell me how to turn it on using the terminal, do u know the command ?

---

### Post by aria john on 2011-09-04
I need the command that let me turn the wireless on using the function and f8 if you can please (:

---

### Post by wildmanne39 on 2011-09-04
Hi, please run these commands in the terminal and post the results here:
```
iwconfig
```
```
lspci -nn | grep 0280
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by northd_tech on 2011-09-04
It might not hurt to post the results of these commands too:

```
nm-tool
tail /var/log/wicd/wicd.log
ifconfig

```

---

### Post by aria john on 2011-09-05
> **wildmanne39 said:**
> Hi, please run these commands in the terminal and post the results here:
```
iwconfig
```
```
lspci -nn | grep 0280
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you
Hi wildmanne39:


#aria@aria-laptop:~$ iwconfig
lo        no wireless extensions.

aria@aria-laptop:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
aria@aria-laptop:~$ rfkill list all
aria@aria-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1
nls_cp437               6351  1
vfat                   10866  1
fat                    55350  1 vfat
usb_storage            50377  1
binfmt_misc             7960  1
ppdev                   6375  0
joydev                 11104  0
fbcon                  39270  71
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0
vgastate                9857  1 vga16fb
snd_hda_intel          25805  2
snd_hda_codec          85759  1 snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0
snd_seq_oss            31191  0
snd_seq_midi            5829  0
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  324711  3
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62851  0
drm_kms_helper         30742  1 i915
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   198886  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
psmouse                65040  0
serio_raw               4918  0
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29319  2 i915
lp                      9336  0
parport                37160  2 ppdev,lp
ahci                   38030  2

---

### Post by aria john on 2011-09-05
> **northd_tech said:**
> It might not hurt to post the results of these commands too:

```
nm-tool
tail /var/log/wicd/wicd.log
ifconfig

```
Hi northd_tech

#aria@aria-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

aria@aria-laptop:~$ tail /var/log/wicd/wicd.log
tail: cannot open `/var/log/wicd/wicd.log' for reading: No such file or directory
aria@aria-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6456 (6.4 KB)  TX bytes:6456 (6.4 KB)

---

### Post by wildmanne39 on 2011-09-05
Hi, you do not have the driver loading, it looks like you have not installed it or the firmware so run this command please:
```
sudo apt-get install b43-fwcutter
```
Then unplug your wired connection and restart your computer and it should connect if it does not post back here if it does would you please use thread tools and mark the thread solved and also click on my membership application if you would like to support me in becoming an ubuntu member.
Thank you

---

### Post by aria john on 2011-09-05
> **wildmanne39 said:**
> Hi, you do not have the driver loading, it looks like you have not installed it or the firmware so run this command please:
```
sudo apt-get install b43-fwcutter
```
Then unplug your wired connection and restart your computer and it should connect if it does not post back here if it does would you please use thread tools and mark the thread solved and also click on my membership application if you would like to support me in becoming an ubuntu member.
Thank you
Hi
I wrote the command you posted
that's what I got:
#Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package b43-fwcutter

---

### Post by wildmanne39 on 2011-09-05
Hi, ok I have seen that before we should be able to fix it by doing this.

After you finish downloading the file disconnect your wired connection then run the commands.

Down load the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
run these commands one at a time.
Thank you

---

### Post by aria john on 2011-09-05
> **wildmanne39 said:**
> Hi, ok I have seen that before we should be able to fix it by doing this.

After you finish downloading the file disconnect your wired connection then run the commands.

Down load the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
run these commands one at a time.
Thank you
ok look what hapened, i wrote the commands, but when i wrote: "sudo rmmod -f b43 "
i got
#ERROR: Removing 'b43': No such file or directory

then I continued and wrote the command after, "sudo rmmod -f ssb", i got:
# ERROR: Removing 'ssb': No such file or directory

and then i wrote you last command: "sudo modprobe b43", i got nothing

Then after that I rewrote the command "sudo rmmod -f b43" and the 2 commands after, but i got nothing this time, I mean i didn't get an Error like the first time I wrote the commands

I know i am bothering you, and i appreciate your help (:

---

### Post by wildmanne39 on 2011-09-05
Hi, no you are not bothering me I am here to help.

The reason those commands did not show anything is that they were not there, that is ok those commands are there just in case those modules are present.

You did remove them so we need to reload them like this.
```
sudo modprobe ssb
sudo modprobe b43
```
make sure your wire connection is disconnected first and after you run the commands go to the top right corner of the screen and click on the internet icon and make sure wireless is enabled and it should ask you for your password if it does not work post back and we will go from there.
Thank you

---

### Post by aria john on 2011-09-05
> **wildmanne39 said:**
> Hi, no you are not bothering me I am here to help.

The reason those commands did not show anything is that they were not there, that is ok those commands are there just in case those modules are present.

You did remove them so we need to reload them like this.
```
sudo modprobe ssb
sudo modprobe b43
```
make sure your wire connection is disconnected first and after you run the commands go to the top right corner of the screen and click on the internet icon and make sure wireless is enabled and it should ask you for your password if it does not work post back and we will go from there.
Thank you
ok i did that, but still having "No network devices available" , and i am trying to click (Fn and F8 ) but nothing happened

---

### Post by wildmanne39 on 2011-09-05
Hi, all right lets see what is going on now that you loaded the driver.
```
rfkill list all
```
```
sudo lshw -C network
```
```
nm-tool
```
```
iwconfig
```
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
```
dmesg | egrep 'b43|firm'
```
and post the results here.
Thank you

---

### Post by aria john on 2011-09-05
> **wildmanne39 said:**
> Hi, all right lets see what is going on now that you loaded the driver.
```
rfkill list all
```
```
sudo lshw -C network
```
```
nm-tool
```
```
iwconfig
```
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
```
dmesg | egrep 'b43|firm'
```
and post the results here.
Thank you
ok (after the last command i got nothing),

#aria@aria-laptop:~$ rfkill list all
aria@aria-laptop:~$ sudo lshw -C network
[sudo] password for aria:
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:d5400000-d543ffff ioport:3000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d4400000-d4403fff
aria@aria-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

aria@aria-laptop:~$ iwconfig
lo        no wireless extensions.

aria@aria-laptop:~$ dmesg | grep wlan0
aria@aria-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

aria@aria-laptop:~$ dmesg | egrep 'b43|firm'

---

### Post by wildmanne39 on 2011-09-05
Hi, you do not have a working wired connection do you? 
Thank you

---

### Post by aria john on 2011-09-05
"wired connection" no, but i have wireless connection

---

### Post by wildmanne39 on 2011-09-05
Hi, a good friend of mine is going to take over I have been up all night and I need to get a little rest.

---

### Post by nm_geo on 2011-09-05
> **aria john said:**
> "wired connection" no, but i have wireless connection

Hi aria john

wildmanne is going to have to get some rest and I told him I would give this a look ..

do this for me so I know what kernel and version you are running ..

```
cat /etc/lsb-release; uname -r
```There is a driver that works with your card but it may not be in the kernel you have.
Here is what I have found so far.
[http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211)

---

### Post by aria john on 2011-09-05
> **nm_geo said:**
> Hi aria john

wildmanne is going to have to get some rest and I told him I would give this a look ..

do this for me so I know what kernel and version you are running ..

```
cat /etc/lsb-release; uname -r
```There is a driver that works with your card but it may not be in the kernel you have.
Here is what I have found so far.
[http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211)
Hi , ok, that's what i got:
#DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
2.6.32-33-generic

---

### Post by praseodym on 2011-09-05
Hi,

under "System-Settings-Hardware drivers" you should be able to install the Broadcom-STA-driver" via wired connection. This device 14e4:4727 doesnt work with the free b43 driver.

---

### Post by nm_geo on 2011-09-05
+1 I would agree if the STA (wl) driver works it is easier than getting the 
**  Getting the driver **

 **  brcmsmac/brcmfmac **

 The [COLOR=#000055][FONT=monospace]brcm80211[/FONT][/COLOR] drivers have been included in the kernel since 2.6.37. Since the release of 2.6.39, they have been renamed to [COLOR=#000055][FONT=monospace]brcmsmac[/FONT][/COLOR] (for PCI cards) and [COLOR=#000055][FONT=monospace]brcmfmac[/FONT][/COLOR] (for SDIO). 
These drivers should be automatically loaded during startup and no further action should be required of the user. 


I just upgraded my kernel on Lucid to see if the driver was located in it.
2.6.38-10-generic #46~lucid1-Ubuntu SMP Wed Jul 6 18:40:11 UTC 2011 i686 GNU/Linux

here is the modinfo brcm80211

```
modinfo brcm80211
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/staging/brcm80211/brcm80211.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     0039D58F094F7B0F75BAA6B
alias:          pci:v0000**14E4**d0000**4727**sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,cfg80211
staging:        Y
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
parm:           msglevel:int
parm:           phymsglevel:int

```

It is in the 2.6.38 Lucid kernel

---

### Post by aria john on 2011-09-05
> **nm_geo said:**
> +1 I would agree if the STA (wl) driver works it is easier than getting the 
**  Getting the driver **

 **  brcmsmac/brcmfmac **

 The [COLOR=#000055][FONT=monospace]brcm80211[/FONT][/COLOR] drivers have been included in the kernel since 2.6.37. Since the release of 2.6.39, they have been renamed to [COLOR=#000055][FONT=monospace]brcmsmac[/FONT][/COLOR] (for PCI cards) and [COLOR=#000055][FONT=monospace]brcmfmac[/FONT][/COLOR] (for SDIO). 
These drivers should be automatically loaded during startup and no further action should be required of the user. 


I just upgraded my kernel on Lucid to see if the driver was located in it.
2.6.38-10-generic #46~lucid1-Ubuntu SMP Wed Jul 6 18:40:11 UTC 2011 i686 GNU/Linux

here is the modinfo brcm80211

```
modinfo brcm80211
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/staging/brcm80211/brcm80211.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     0039D58F094F7B0F75BAA6B
alias:          pci:v0000**14E4**d0000**4727**sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
depends:        mac80211,cfg80211
staging:        Y
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
parm:           msglevel:int
parm:           phymsglevel:int

```

It is in the 2.6.38 Lucid kernel
ok so how do I upgrade my kernel without a wireless connection ?

---

### Post by aria john on 2011-09-05
> **praseodym said:**
> Hi,

under "System-Settings-Hardware drivers" you should be able to install the Broadcom-STA-driver" via wired connection. This device 14e4:4727 doesnt work with the free b43 driver.
Hi,
I tried to connect a DSL cable to the laptop, but it is not showing it as well, I mean after I connected the cable nothing appeared in the "network connections" ... still having "No Network connection"

---

### Post by praseodym on 2011-09-06
Do you have your install-CD/DVD? The needed packages for the driver can be installed from there, they are named **dkms**, **patch**, **fakeroot**, and **bcmwl-kernel-source**. Then activate the driver.

---

### Post by aria john on 2011-09-06
> **praseodym said:**
> Do you have your install-CD/DVD? The needed packages for the driver can be installed from there, they are named **dkms**, **patch**, **fakeroot**, and **bcmwl-kernel-source**. Then activate the driver.
Hi,
I downloaded "Ubuntu 10.04" from Ubuntu website and burned it to a CD then I installed it on my laptop, is this what you mean by install CD ?

---

### Post by praseodym on 2011-09-06
Errr, no, no need to install the whole system, but anyway: On CD/DVD there are folders:

```
~/pool/main/
```
in alphabetical order. The named packages are in the folders with their first letter. Just double click them one by one (this installs them) and activate the Broadcom-STA driver in "System-Settings-Hardware drivers.

Or you insert the CD, add it to the synaptic package manager by accepting and install these packsges with synaptic

---

### Post by aria john on 2011-09-06
> **praseodym said:**
> Errr, no, no need to install the whole system, but anyway: On CD/DVD there are folders:

```
~/pool/main/
```
in alphabetical order. The named packages are in the folders with their first letter. Just double click them one by one (this installs them) and activate the Broadcom-STA driver in "System-Settings-Hardware drivers.

Or you insert the CD, add it to the synaptic package manager by accepting and install these packsges with synaptic
(I didn't install the whole system) (I was asking you if this is the install CD) ... anyways I clicked on the file named dkms in the CD but I got this error:

Status: Error: Dependency is not satisfiable: patch

---

### Post by aria john on 2011-09-06
> **praseodym said:**
> Errr, no, no need to install the whole system, but anyway: On CD/DVD there are folders:

```
~/pool/main/
```
in alphabetical order. The named packages are in the folders with their first letter. Just double click them one by one (this installs them) and activate the Broadcom-STA driver in "System-Settings-Hardware drivers.

Or you insert the CD, add it to the synaptic package manager by accepting and install these packsges with synaptic
oops sorry, 
now I installed them
what should I do next ?

---

### Post by praseodym on 2011-09-06
Go to Hardware drivers in "System->Settings->" and activate the broadcom-STA driver [COLOR="Red"]after[/COLOR]:

```
sudo depmod -a
```

---

### Post by aria john on 2011-09-06
"activate the Broadcom-STA driver in "System-Settings-Hardware drivers."

the problem is that I am not connected to the internet on Ubuntu, so when I click on "Hardware Drivers" it says: "Downloading package indexes failed, please check your network status" 
since there is no network connection ...

---

### Post by praseodym on 2011-09-06
You installed all 4 packages? If so, reboot, and try again.

---

### Post by aria john on 2011-09-06
> **praseodym said:**
> You installed all 4 packages? If so, reboot, and try again.
Hi !!! yes it worked after I restarted the system :D thank you
but excuse me ... I am installing the driver as you told me , but what is its function ? since the wireless connection in on now 
s: (I am new to Ubuntu ... )

---

### Post by praseodym on 2011-09-06
This is a non-free (in licence terms) driver from Broadcom. This driver is needed for this device. The licence free driver b43 doesnt work with this card, so it has to be installed afterwards. Otherwise the card is not working.

---

### Post by aria john on 2011-09-06
I am sorry, but still confused :S , I didn't understand : what does it do ? The wireless connection is on before I install it.

---

### Post by praseodym on 2011-09-06
Ok, the driver was already installed and the rebooting did the trick.

Check:

```
lspci -nnk | grep -iA2 net
iwconfig
lsmod
dmesg | grep wl
sudo iwlist scan
rfkill list
```

---

### Post by aria john on 2011-09-06
yes it is installed (: i just saw it
thank you
---
that's what I got after I wrote your commands:

#aria@aria-laptop:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
	Kernel driver in use: wl
	Kernel modules: wl
aria@aria-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:2  Signal level:185  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

aria@aria-laptop:~$ dmesg | grep wl
[   22.266435] wl: module license 'MIXED/Proprietary' taints kernel.
[   22.270104] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.270112] wl 0000:02:00.0: setting latency timer to 64
aria@aria-laptop:~$ sudo iwlist scan
[sudo] password for aria:
lo        Interface doesn't support scanning.

eth0      Scan completed :
          Cell 01 - Address: 00:24:01:1B:BF:65
                    ESSID:"aria"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-65 dBm  Noise level:-92 dBm
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B000103104700100E12912E6DE3B462AAF90024011BBF6510210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D33303010080002008E
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1C:F0:E4:7F:53
                    ESSID:"dlink"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-78 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD750050F204104A000110103B000103104700100843EF7DA5D8DBDBBFEE001CF0E47F53104400010210210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D33303010080002008E1041000100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 74:EA:3A:F5:5E:9A
                    ESSID:"saad"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:1/5  Signal level:-87 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD850050F204104A0001101044000102103B000103104700100000000000001000000074EA3AF55E9A1021000754502D4C494E4B10230009544C2D57523834314E10240007362E302F372E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:18:39:AA:B8:38
                    ESSID:"nader"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-83 dBm  Noise level:-93 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:24:01:82:77:18
                    ESSID:"Blink2e508"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-72 dBm  Noise level:-90 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 00:21:29:EF:67:07
                    ESSID:"hm"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

----------

Should I do something now ? or that's it ?

---

### Post by wildmanne39 on 2011-09-06
Hi, I am glad you have it working and I am sorry I went down the wrong path, I looked up the information for that card but I could not find it for that exact one, I must have looked in the wrong place or just missed it.

Thank you praseodym for correcting my mistake.

---

### Post by praseodym on 2011-09-06
You are connected now?

```
lsmod

```
is missing. Please also show:

```
iwlist chan
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/udev/rules.d/70-persietent-net.rules
ping -c 4 213.95.41.11.
```
No wired connection? Try the module for the ethernet card:

```
sudo modprobe -v atl1c
```

---

### Post by praseodym on 2011-09-06
@wildmanne39:

A good starting point fpr Broadcom devices is this page:

[http://linuxwireless.org/en/users/Drivers/b43#Supported_devices](http://linuxwireless.org/en/users/Drivers/b43#Supported_devices)

which card works with the b43 driver and which doesnt.

---

### Post by wildmanne39 on 2011-09-06
Hi praseodym, yep I just went there and I looked there yesterday I just missed it, I did not go to be the night before I was at the hospital until sunrise yesterday morning with my daughter and I tried to sleep and couldn't, I sure must not have been at my best.
Thank you

---

### Post by aria john on 2011-09-06
p { margin-bottom: 0.08in; }  Yes I am connected, I now - FINALLY- typing on firefox on Ubuntu :D -

#aria@aria-laptop:~$ lsmod 
 Module                  Size  Used by 
 nls_iso8859_1           4633  0  
 nls_cp437               6351  0  
 vfat                   10866  0  
 fat                    55350  1 vfat 
 usb_storage            50377  0  
 nls_utf8                1421  1  
 isofs                  33399  1  
 binfmt_misc             7960  1  
 ppdev                   6375  0  
 joydev                 11104  0  
 fbcon                  39270  71  
 tileblit                2487  1 fbcon 
 font                    8053  1 fbcon 
 bitblit                 5811  1 fbcon 
 softcursor              1565  1 bitblit 
 vga16fb                12757  0  
 vgastate                9857  1 vga16fb 
 lib80211_crypt_tkip     8676  0  
 snd_hda_intel          25805  2  
 snd_hda_codec          85759  1 snd_hda_intel 
 snd_hwdep               6924  1 snd_hda_codec 
 snd_pcm_oss            41394  0  
 snd_mixer_oss          16299  1 snd_pcm_oss 
 snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
 snd_seq_dummy           1782  0  
 snd_seq_oss            31191  0  
 snd_seq_midi            5829  0  
 snd_rawmidi            23420  1 snd_seq_midi 
 snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi 
 snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
 i915                  324711  3  
 snd_timer              23649  2 snd_pcm,snd_seq 
 snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
 drm_kms_helper         30742  1 i915 
 uvcvideo               62851  0  
 snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 videodev               40518  1 uvcvideo 
 v4l1_compat            15495  2 uvcvideo,videodev 
 soundcore               8052  1 snd 
 snd_page_alloc          8500  2 snd_hda_intel,snd_pcm 
 v4l2_compat_ioctl32    11892  1 videodev 
 wl                   1964968  0  
 drm                   198886  4 i915,drm_kms_helper 
 i2c_algo_bit            6024  1 i915 
 video                  20623  1 i915 
 output                  2503  1 video 
 psmouse                65040  0  
 serio_raw               4918  0  
 lib80211                6151  2 lib80211_crypt_tkip,wl 
 intel_agp              29319  2 i915 
 lp                      9336  0  
 parport                37160  2 ppdev,lp 
 ahci                   38030  3  
 aria@aria-laptop:~$ iwlist chan 
 lo        no frequency information. 
  
 eth0      no frequency information. 
  
 aria@aria-laptop:~$ cat /var/lib/NetworkManager/NetworkManager.state 
  
 [main] 
 NetworkingEnabled=true 
 WirelessEnabled=true 
 WWANEnabled=true 
 aria@aria-laptop:~$ cat /etc/udev/rules.d/70-persietent-net.rules 
 cat: /etc/udev/rules.d/70-persietent-net.rules: No such file or directory 
 aria@aria-laptop:~$ ping -c 4 213.95.41.11. 
 ping: unknown host 213.95.41.11.

---------
what should I do now ?

---

### Post by praseodym on 2011-09-06
Damn ;-) typo again:

```
cat /etc/udev/rules.d/70-persi[COLOR="Red"]s[/COLOR]tent-net.rules #and additionally
uname -a
```
Do you want to use wired, too? Did the module **atl1c** work?

---

### Post by aria john on 2011-09-06
p { margin-bottom: 0.08in; }  ok , how do I configure the wired connection ? what is atl1c ? 

#

aria@aria-laptop:~$ cat /etc/udev/rules.d/70-persistent-net.rules 
 # This file maintains persistent names for network interfaces. 
 # See udev(7) for syntax. 
 # 
 # Entries are automatically added by the 75-persistent-net-generator.rules 
 # file; however you are also free to add your own entries. 
  
 # PCI device 0x14e4:0x4727 (wl) 
 SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e8:39:df:01:8d:78", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0" 
 aria@aria-laptop:~$ uname -a 
 Linux aria-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 x86_64 GNU/Linux

---

### Post by praseodym on 2011-09-06
Try to install the module by hand:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/2010/09/compat-wireless-2010-09-09.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
[COLOR="Red"]./scripts/driver-select atl1c[/COLOR]
make
sudo make install
```
and reboot (with cable). Checks after that:

```
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
route -n
cat /etc/resolv.conf
```

[COLOR="Lime"]Remark for other users[/COLOR]: If the Broadcom-STA driver is used, then the compat-wireless package [COLOR="Red"]must not[/COLOR] be installed completely ([COLOR="Red"]red[/COLOR] command line absolutely valid), because of the lib80211-subsystem drivers being updated, too, which leads to the fact, that the STA-driver doesnt work anymore; even if you compile the STA driver by hand from [here]("http://www.broadcom.com/support/802.11/linux_sta.php"). The same for the backport-modules for _all Ubuntu variants_, which are based on compat-wireless.

[COLOR="Lime"]Second remark[/COLOR]: For Lucid Lynx 10.04 I linked an older compat-wireless file for this installation, for Natty or newer Ubuntu versions the actual driver package can be used.

---

### Post by aria john on 2011-09-06
look what happened , I wrote the code, then the internet connection was disabled (due to bad connection here),
how do I know that it is installed ?

look at the code:

#
   	 	 	 	p { margin-bottom: 0.08in; }  aria@aria-laptop:~$ sudo apt-get install --reinstall linux-headers-generic build-essential dkms 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following extra packages will be installed: 
   dpkg-dev g++ g++-4.4 libstdc++6-4.4-dev xz-utils 
 Suggested packages: 
   debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc 
   libstdc++6-4.4-dbg libstdc++6-4.4-doc 
 The following NEW packages will be installed: 
   build-essential dpkg-dev g++ g++-4.4 libstdc++6-4.4-dev xz-utils 
 0 upgraded, 6 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded. 
 Need to get 5,756kB/8,250kB of archives. 
 After this operation, 26.2MB of additional disk space will be used. 
 Do you want to continue [Y/n]? Y 
 Abort.

---

### Post by aria john on 2011-09-06
I tried again after I installed some packages from the install CD (as you told me before) and I got:

#
aria@aria-laptop:~$ sudo apt-get install --reinstall linux-headers-generic build-essential dkms
[sudo] password for aria: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev xz-utils
Suggested packages:
  debian-keyring debian-maintainers
The following NEW packages will be installed:
  build-essential dpkg-dev xz-utils
0 upgraded, 3 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/970kB of archives.
After this operation, 2,654kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package xz-utils.
(Reading database ... 123288 files and directories currently installed.)
Unpacking xz-utils (from .../xz-utils_4.999.9beta+20091116-1_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.5.6ubuntu4.5_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4build1_amd64.deb) ...
Preparing to replace dkms 2.1.1.2-2ubuntu1 (using .../dkms_2.1.1.2-2ubuntu1_all.deb) ...
Unpacking replacement dkms ...
Preparing to replace linux-headers-generic 2.6.32.33.39 (using .../linux-headers-generic_2.6.32.33.39_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Processing triggers for man-db ...
Setting up xz-utils (4.999.9beta+20091116-1) ...
Setting up dpkg-dev (1.15.5.6ubuntu4.5) ...
Setting up build-essential (11.4build1) ...
Setting up dkms (2.1.1.2-2ubuntu1) ...

Setting up linux-headers-generic (2.6.32.33.39) ...

---

### Post by aria john on 2011-09-06
and that's what i got after I did what you wrote:
#
  	 	 	 	p { margin-bottom: 0.08in; }  aria@aria-laptop:~$ lspci -nnk | grep -iA2 net 
 01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1) 
 02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01) 
 	Kernel driver in use: wl 
 	Kernel modules: wl 
 aria@aria-laptop:~$ lsmod 
 Module                  Size  Used by 
 nls_utf8                1421  1  
 isofs                  33399  1  
 binfmt_misc             7960  1  
 ppdev                   6375  0  
 joydev                 11104  0  
 fbcon                  39270  71  
 tileblit                2487  1 fbcon 
 font                    8053  1 fbcon 
 bitblit                 5811  1 fbcon 
 softcursor              1565  1 bitblit 
 vga16fb                12757  0  
 vgastate                9857  1 vga16fb 
 snd_hda_intel          25805  2  
 snd_hda_codec          85759  1 snd_hda_intel 
 snd_hwdep               6924  1 snd_hda_codec 
 snd_pcm_oss            41394  0  
 snd_mixer_oss          16299  1 snd_pcm_oss 
 snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss 
 snd_seq_dummy           1782  0  
 snd_seq_oss            31191  0  
 snd_seq_midi            5829  0  
 snd_rawmidi            23420  1 snd_seq_midi 
 snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi 
 snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
 snd_timer              23649  2 snd_pcm,snd_seq 
 snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
 i915                  324711  3  
 lib80211_crypt_tkip     8676  0  
 uvcvideo               62851  0  
 drm_kms_helper         30742  1 i915 
 videodev               40518  1 uvcvideo 
 v4l1_compat            15495  2 uvcvideo,videodev 
 v4l2_compat_ioctl32    11892  1 videodev 
 wl                   1964968  0  
 lib80211                6151  2 lib80211_crypt_tkip,wl 
 snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 drm                   198886  4 i915,drm_kms_helper 
 i2c_algo_bit            6024  1 i915 
 psmouse                65040  0  
 serio_raw               4918  0  
 soundcore               8052  1 snd 
 snd_page_alloc          8500  2 snd_hda_intel,snd_pcm 
 intel_agp              29319  2 i915 
 video                  20623  1 i915 
 output                  2503  1 video 
 lp                      9336  0  
 parport                37160  2 ppdev,lp 
 ahci                   38030  3  
 aria@aria-laptop:~$ ifconfig -a 
 eth0      Link encap:Ethernet  HWaddr e8:39:df:01:8d:78   
           inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0 
           inet6 addr: fe80::ea39:dfff:fe01:8d78/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:608 errors:0 dropped:0 overruns:0 frame:481 
           TX packets:641 errors:6 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:688692 (688.6 KB)  TX bytes:107600 (107.6 KB) 
           Interrupt:17  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B) 
  
 aria@aria-laptop:~$ cat /etc/udev/rules.d/70-persistent-net.rules 
 # This file maintains persistent names for network interfaces. 
 # See udev(7) for syntax. 
 # 
 # Entries are automatically added by the 75-persistent-net-generator.rules 
 # file; however you are also free to add your own entries. 
  
 # PCI device 0x14e4:0x4727 (wl) 
 SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e8:39:df:01:8d:78", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0" 
 aria@aria-laptop:~$ route -n 
 Kernel IP routing table 
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
 192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 eth0 
 169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
 0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0 
 aria@aria-laptop:~$ cat /etc/resolv.conf 
 # Generated by NetworkManager 
 domain lan 
 search lan 
 nameserver 192.168.0.1 
 -----------

should I do something else now????

---

### Post by praseodym on 2011-09-06
Did you install the driver? Continue line by line with the "wget"-command

---

### Post by aria john on 2011-09-06
the 3rd command didn't work, look what I got:
#
~$ tar jxvf compat-wireless-2.6.tar.bz2
tar: compat-wireless-2.6.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

---

### Post by praseodym on 2011-09-06
Maybe an incomplete download. Here it worked with "wget". Try alternatively this direct link:

[http://www.orbit-lab.org/kernel/compat-wireless-2.6/2010/09/compat-wireless-2010-09-09.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2010/09/compat-wireless-2010-09-09.tar.bz2)

save it in your /home-directory, try to unpack it with Right-Klick->"Unpack here" and continue with the "cd"-command line.

---

### Post by aria john on 2011-09-06
ok ... 
look now:
#
~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
	Kernel driver in use: wl
	Kernel modules: wl
~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
joydev                 11104  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25805  2 
snd_hda_codec          85759  1 snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  324711  3 
lib80211_crypt_tkip     8676  0 
drm_kms_helper         30742  1 i915
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
psmouse                65040  0 
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
serio_raw               4918  0 
snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   198886  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  1 i915
output                  2503  1 video
intel_agp              29319  2 i915
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e8:39:df:01:8d:78  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ea39:dfff:fe01:8d78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:517 errors:0 dropped:0 overruns:0 frame:1671
          TX packets:516 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:578593 (578.5 KB)  TX bytes:60232 (60.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21576 (21.5 KB)  TX bytes:21576 (21.5 KB)

~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e8:39:df:01:8d:78", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain lan
search lan
nameserver 192.168.0.1

---

### Post by praseodym on 2011-09-06
Did you load the module by hand:

```
sudo modprobe -v atl1c
sudo depmod -a
sudo service network-manager restart
```
Checks:
```
lsmod
dmesg | grep atl1c
ifconfig -a
modinfo atl1c | grep 2060
```
Tried to reboot?

---

### Post by aria john on 2011-09-06
Yes I did by hand (downloaded it and continued with the cd command line - as you wrote) (if this is what you mean by "by hand" )

I did as you told me before (plug the cable then reboot ... and check)

now for the new check:

#
~$ lsmod
Module                  Size  Used by
atl1c                  32975  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
joydev                 11104  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25805  2 
snd_hda_codec          85759  1 snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  324711  3 
lib80211_crypt_tkip     8676  0 
drm_kms_helper         30742  1 i915
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
psmouse                65040  0 
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
serio_raw               4918  0 
snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   198886  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  1 i915
output                  2503  1 video
intel_agp              29319  2 i915
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
~$ dmesg | grep atl1c
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e8:39:df:01:8d:78  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ea39:dfff:fe01:8d78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3981 errors:0 dropped:0 overruns:0 frame:19988
          TX packets:3883 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3832117 (3.8 MB)  TX bytes:569637 (569.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29856 (29.8 KB)  TX bytes:29856 (29.8 KB)

~$ modinfo atl1c | grep 2060

---

### Post by praseodym on 2011-09-07
Ok, obviously this didnt work. Lets try a newer version. Uninstall the other one:

```
cd compat*
sudo make uninstall
./scripts/driver-select restore 
make clean
``` and delete the folder.

Lets try the newest driver:

```
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2        
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install
```
Reboot and check again. Direct link:

[http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

---

### Post by aria john on 2011-09-07
ok:
#
~$ tar jxvf compat-wireless-2.6.tar.bz2
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

______
should I do it manually like you told me before ?

---

### Post by aria john on 2011-09-07
by the way, I had a problem (not a problem, but it is annoying me), every few minutes a window appears and says:
"Enter password to unlock your login keyring.
The password you use to log in to your computer no longer matches that of your login keyring "
what is login keyring, I changed my password few days ago, but I wrote the previous password and it worked, I don't know what's this about ...
but every time I try to access a wireless connection, this window appears

---

### Post by praseodym on 2011-09-07
Yes, try the download and the unpacking by hand again.

For the keyring: Go to "Passwords & Keys"->Right klick on "Password:login" in the rider "Passwords" and choose "Change Password". There you change the old PW to the new Login-PW. Login again after that.

---

### Post by aria john on 2011-09-07
look, isn't this the same file that we deleted it before ? "compat-wireless-2.6.tar.bz2" ? I think it is the same file, no ?

---

### Post by praseodym on 2011-09-07
The other one was named compat-wireless-2010-09-09.tar.bz2 it was an older version, which I wanted to try for 10.04, it should have worked better, but obviously it didnt. Try the newer one with the new installation procedure.

---

### Post by aria john on 2011-09-07
I downloaded it from "http://www.orbit-lab.org/kernel/compat-wireless-2.6/ "
but when extracting it, I am getting the same error as before:
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Exiting with failure status due to previous errors

----------
any idea about this ?

---

### Post by aria john on 2011-09-07
oopss, sorry sorry , that was another file s:
I was looking in the home folder not in the Downloads folder,
ok

---

### Post by aria john on 2011-09-07
look now:
#

~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
joydev                 11104  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25805  2 
snd_hda_codec          85759  1 snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62851  0 
lib80211_crypt_tkip     8676  0 
soundcore               8052  1 snd
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
psmouse                65040  0 
i915                  324711  3 
drm_kms_helper         30742  1 i915
wl                   1964968  0 
serio_raw               4918  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
drm                   198886  4 i915,drm_kms_helper
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
intel_agp              29319  2 i915
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
~$ dmesg | grep atl1c
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e8:39:df:01:8d:78  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ea39:dfff:fe01:8d78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:503 errors:0 dropped:0 overruns:0 frame:119
          TX packets:527 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:532099 (532.0 KB)  TX bytes:57686 (57.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

~$ modinfo atl1c | grep 2060

---

### Post by praseodym on 2011-09-07
Try:

```
sudo depmod -a
sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
sudo modprobe -v atl1c
sudo service network-manager restart
```
Check:
```
cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a
lsmod
dmesg | grep atl
```

---

### Post by aria john on 2011-09-07
ok:

#

~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e8:39:df:01:8d:78", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr e8:39:df:01:8d:78  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ea39:dfff:fe01:8d78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:420 errors:0 dropped:0 overruns:0 frame:279
          TX packets:404 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:388705 (388.7 KB)  TX bytes:46450 (46.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

~$ lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
joydev                 11104  0 
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25805  2 
snd_hda_codec          85759  1 snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  324711  3 
snd_timer              23649  2 snd_pcm,snd_seq
lib80211_crypt_tkip     8676  0 
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         30742  1 i915
snd                    71283  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   198886  4 i915,drm_kms_helper
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
psmouse                65040  0 
serio_raw               4918  0 
i2c_algo_bit            6024  1 i915
video                  20623  1 i915
output                  2503  1 video
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl
intel_agp              29319  2 i915
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
~$ dmesg | grep atl

---

### Post by aria john on 2011-09-07
could you please give a brief an explanation when you write a code, I am just copying it as it is,
or please give me a key about how you find a solution for a given problem, where do you search ?
what astonished me is that your join date is August 2011!!! I am trying to understand the situation ...

---

### Post by praseodym on 2011-09-07
The problm is: The BIOS recognizes the card (see: "lspci") but the driver doesnt work. Did you check the BIOS-settings, if the card is listed there (disabled, or sth.)? Can you reset the BIOS-settings to manufacturer default settings?

For the other info: e.g. [here]("http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3208747"). I am a supporter in the german ubuntuusers.de forum.

The code was to backpup the file and create a new one. But obviously the card is not detected in any way (even without driver the card should be listed in the "70-..."-file). Therefore it can be broken or not being enabled in the BIOS settings. Normally wired connection gets the "eth0"-interface, not wireless (the Broadcom-STA-driver renames the wireless interface to **eth1**, other drivers use **wlan0**.

---

### Post by aria john on 2011-09-07
Nothing understood,anyways forget about wired connection, wireless is enough, I was trying to catch some information , but it seems I am doing it the wrong way
so could you please give me a website or name of a book where I could start to understand all these stuff ? I am new to Ubuntu

---

### Post by kenyard on 2011-09-07
i have the exact same card as you Network controller [0280]: Broadcom Corporation Device [14e4:4727]

took me around 3 days to get going in a way i wanted. glad u got that working at least
kernel 3.1.0 i tried and couldnt get going so if you are gonna upgrade u cud run into issues again which is annoying.

besides that what it looked like is you are missing rfkill, which is very handy for this.
it lists all the connections.

rfkill list (lists all network connections, for your problem 2 different drivers could be loaded and trying to both use the ethernet causing issues, this was my issue for my wireless)

post the result of rfkill list. it may help resolve stuff if it doesn nothing you may have to install it.

sudo apt-get rfkill (this command would install it, you may have to upgrade your list of modules first, not sure how offhand)

the error you are having seems pretty annoying. the worst is its generally something stupidly simple with just a single command will resolve it

---

### Post by aria john on 2011-09-07
#
sudo apt-get rfkill
 
E: Invalid operation rfkill

--------------------------

---

