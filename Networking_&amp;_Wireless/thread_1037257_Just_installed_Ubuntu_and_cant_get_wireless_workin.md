---
title: "Just installed Ubuntu and cant get wireless working"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by kakarotman on 2009-01-11
So i just installed Ubuntu (i use grub to boot PclinuxOS and vista to) and it recognizes my wireless driver. At least at least i assume so because it says that it is active. But i dont know how to get it so search for a wireless connection and connect to it. Do i have to use ndiswrapper to use my wireless driver or is that just to get linux to recognize my driver. Please help it really sucks not have wireless with Linux.

---

### Post by flintflake on 2009-01-11
You should be able to use the network-manager to see/connect to any wireless connection if your card is configured correctly.  Post your iwconfig and lshw -C network output....

---

### Post by kakarotman on 2009-01-11
josh@Josh:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

josh@Josh:~$ lshw -C
Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.13)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

---

### Post by kakarotman on 2009-01-11
It does not show any wireless connections it just shows one wired wich says eth0

---

### Post by flintflake on 2009-01-11
It appears that your wireless card isn't configured.  Hopefully someone can help you further.   I'm still a rookie myself.

---

### Post by kakarotman on 2009-01-11
K thanks.

---

### Post by davidcaiazzo on 2009-01-11
Few things first. Did your wireless card work on the live cd? What kind of wireless card do you have? If you don't know what kinda computer are you useing make and model please.

---

### Post by kevdog on 2009-01-11
You need to tell us way more about your hardware.  Please post the following:

lshw -C network
lspci -nnm (if pci device) or lsusb -v (if usb device)
uname -r (Kernel Version)
Ubuntu Install Version if possible (Hardy, Intrepid)

Thanks.

---

### Post by kakarotman on 2009-01-11
This is what laptop i have toshiba satellite A215-S5837 and here is the info asked for.
josh@Josh:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:35:97:63
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:de:0c:ff:11:23
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
josh@Josh:~$ lspci -nnm
00:00.0 "Host bridge [0600]" "ATI Technologies Inc [1002]" "RS690 Host Bridge [7910]" "Toshiba America Info Systems [1179]" "Device [ff00]"
00:01.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS690 PCI to PCI Bridge (Internal gfx) [7912]" "" ""
00:05.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS690 PCI to PCI Bridge (PCI Express Port 1) [7915]" "" ""
00:06.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS690 PCI to PCI Bridge (PCI Express Port 2) [7916]" "" ""
00:07.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS690 PCI to PCI Bridge (PCI Express Port 3) [7917]" "" ""
00:12.0 "SATA controller [0106]" "ATI Technologies Inc [1002]" "SB600 Non-Raid-5 SATA [4380]" -p01 "Toshiba America Info Systems [1179]" "Device [ff00]"
00:13.0 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI0) [4387]" -p10 "Toshiba America Info Systems [1179]" "Device [ff00]"
00:13.1 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI1) [4388]" -p10 "Toshiba America Info Systems [1179]" "Device [ff00]"
00:13.2 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI2) [4389]" -p10 "Toshiba America Info Systems [1179]" "Device [ff00]"
00:13.3 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI3) [438a]" -p10 "Toshiba America Info Systems [1179]" "Device [ff00]"
00:13.4 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI4) [438b]" -p10 "Toshiba America Info Systems [1179]" "Device [ff00]"
00:13.5 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB Controller (EHCI) [4386]" -p20 "Toshiba America Info Systems [1179]" "Device [ff00]"
00:14.0 "SMBus [0c05]" "ATI Technologies Inc [1002]" "SBx00 SMBus Controller [4385]" -r14 "Toshiba America Info Systems [1179]" "Device [ff00]"
00:14.1 "IDE interface [0101]" "ATI Technologies Inc [1002]" "SB600 IDE [438c]" -p8a "Toshiba America Info Systems [1179]" "Device [ff00]"
00:14.2 "Audio device [0403]" "ATI Technologies Inc [1002]" "SBx00 Azalia (Intel HDA) [4383]" "Toshiba America Info Systems [1179]" "Device [ff08]"
00:14.3 "ISA bridge [0601]" "ATI Technologies Inc [1002]" "SB600 PCI to LPC Bridge [438d]" "Toshiba America Info Systems [1179]" "Device [ff00]"
00:14.4 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "SBx00 PCI to PCI Bridge [4384]" -p01 "" ""
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
01:05.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "RS690M [Radeon X1200 Series] [791f]" "Toshiba America Info Systems [1179]" "Device [ff00]"
0e:00.0 "Ethernet controller [0200]" "Realtek Semiconductor Co., Ltd. [10ec]" "RTL8101E/RTL8102E PCI Express Fast Ethernet controller [8136]" -r01 "Toshiba America Info Systems [1179]" "Device [ff00]"
14:00.0 "Ethernet controller [0200]" "Atheros Communications Inc. [168c]" "AR242x 802.11abg Wireless PCI Express Adapter [001c]" -r01 "Askey Computer Corp. [144f]" "Device [7128]"
1a:04.0 "CardBus bridge [0607]" "Texas Instruments [104c]" "PCIxx12 Cardbus Controller [8039]" "Toshiba America Info Systems [1179]" "Device [ff00]"
1a:04.1 "FireWire (IEEE 1394) [0c00]" "Texas Instruments [104c]" "PCIxx12 OHCI Compliant IEEE 1394 Host Controller [803a]" -p10 "Toshiba America Info Systems [1179]" "Device [ff00]"
1a:04.2 "Mass storage controller [0180]" "Texas Instruments [104c]" "5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [803b]" "Toshiba America Info Systems [1179]" "Device [ff00]"
1a:04.3 "SD Host controller [0805]" "Texas Instruments [104c]" "PCIxx12 SDA Standard Compliant SD Host Controller [803c]" -p01 "Toshiba America Info Systems [1179]" "Device [ff00]"
josh@Josh:~$ uname -r
2.6.27-7-generic
josh@Josh:~$

---

### Post by kakarotman on 2009-01-11
this is the iso name i installed: ubuntu-8.10-desktop-i386

---

### Post by kevdog on 2009-01-11
This is your card:
AR242x 802.11abg

Its an atheros chipset -- same as a 5007.

You need the atheros ath5k driver to make this thing go.

8.10 is Intrepid Ibex

Do the following:

sudo apt-get install linux-backports-modules-intrepid

This should install the ath5k driver for you.
You might need to 
sudo modprobe ath5k
after the install.

Then repost 
lshw -C network

---

### Post by kakarotman on 2009-01-11
This is every thing that i did and what happened and i am pretty sure it did not work unless i did some thing wrond or there is some thing else i have to do.

josh@Josh:~$ sudo apt-get install linus-backports-modules-intrepid
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linus-backports-modules-intrepid
josh@Josh:~$ sudo modprobe ath5k
FATAL: Module ath5k not found.
josh@Josh:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:35:97:63
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:90:76:fc:33:ce
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
josh@Josh:~$

---

### Post by kakarotman on 2009-01-11
i said linus instead of linux probably bad right?

---

### Post by kakarotman on 2009-01-11
even when i typed it in correctly it said the same thing that that last file could not be found do i have to like get that file or some thing?

---

### Post by kevdog on 2009-01-11
Ok try this

sudo aptitude install linux-backports-modules-intrepid-generic

What error are you getting -- you need to be very specific or nobody can help you!! We can't read your screen or see what you are doing.

---

### Post by kakarotman on 2009-01-11
i type the first command: (sudo apt-get install linux-backports-modules-intrepid)
and i get this:

Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package linus-backports-modules-intrepid

---

### Post by kakarotman on 2009-01-11
So i tried the new command and it gave me this:

josh@Josh:~$ sudo aptitude install linux-backports-modules-intrepid-generic
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "linux-backports-modules-intrepid-generic"
Couldn't find any package whose name or description matched "linux-backports-modules-intrepid-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

---

### Post by kevdog on 2009-01-11
Can you post your /etc/apt/sources.list?

I don't think all of your repositories are enabled.

---

### Post by kakarotman on 2009-01-11
I am very new to linux and i have no idea how to do or what you just said.

---

### Post by ajcham on 2009-01-11
> **kakarotman said:**
> I am very new to linux and i have no idea how to do or what you just said.

```
less /etc/apt/sources.list
```
to view the file in a terminal

or
```
gedit /etc/apt/sources.list
```
to open it in a text editor

then post the contents.

---

### Post by kakarotman on 2009-01-11
This is what i got:

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by kevdog on 2009-01-11
Here is what you want to do:

Open the file as root to edit:

gksu gedit /etc/apt/sources.list

Find the two lines:

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

Remove the # sign in front of the two lines.

Save and exit.

Then run at the terminal

sudo aptitude update

Then 

sudo aptitude install linux-backports-modules-intrepid

Your original repository list excluded the backports repository, so by removing the # (comment) character, you added them to the possible repository list.

---

### Post by ajcham on 2009-01-11
Nvm

---

### Post by ajcham on 2009-01-11
> **kevdog said:**
> Your original repository list excluded the backports repository, so by removing the # (comment) character, you added them to the possible repository list.

[s]You don't need the backport repo, and I would advise against enabling it unless absolutely necessary.

The file needed is in archive.ubuntu.com/main, currently he has **us**.archive.ubuntu.com/main[/s]

My mistake - although I don't have backports enabled, I do have intrepid-proposed enabled in Synaptic, which is why the file was being shown in the Main repo.

---

### Post by kakarotman on 2009-01-11
Are you trying to get some thing from the internet?? becasue i thought i was trying to get internet. So if i dont have internet then why are all those urls in there?? here is what i got though:

josh@Josh:~$ sudo aptitude update
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/main Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/restricted Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/universe Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-backports/multiverse Translation-en_US
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done           

josh@Josh:~$ sudo aptitude install linux-backports-modules-intrepid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "linux-backports-modules-intrepid"
Couldn't find any package whose name or description matched "linux-backports-modules-intrepid"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

josh@Josh



It might help if i knew what you are trying to do. There is some software that i need to get my wireless driver working right?

---

### Post by ajcham on 2009-01-11
> **kakarotman said:**
> Are you trying to get some thing from the internet?? becasue i thought i was trying to get internet.

Sorry, yes, Apt is trying to get the files from the Internet to install them, which of course won't work.  Are you able to hook the computer up to a wired connection for the time being?

---

### Post by kakarotman on 2009-01-11
no but i can download files here in windows and transfer them there

---

### Post by ajcham on 2009-01-11
> **kakarotman said:**
> no but i can download files here in windows and transfer them there

We may be able to do that. First, could you check which kernel you are running:
```
uname -a
```

---

### Post by kakarotman on 2009-01-11
Linux Josh 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

---

### Post by ajcham on 2009-01-11
> **kakarotman said:**
> Linux Josh 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

In that case, the file you need is detailed here: [http://packages.ubuntu.com/intrepid/linux-backports-modules-2.6.27-7-generic](http://packages.ubuntu.com/intrepid/linux-backports-modules-2.6.27-7-generic).  You'll want a deb file to install - I'm still trying to find where you download it.

---

### Post by cptrohn on 2009-01-11
I am having the exact same problem in 8.04.1 Is there a way I can do this in Hardy Heron?

---

### Post by ajcham on 2009-01-11
> **cptrohn said:**
> I am having the exact same problem in 8.04.1 Is there a way I can do this in Hardy Heron?

Please create a new thread for your question, and people can help you there.

---

### Post by kakarotman on 2009-01-11
when i go to that link there are like 4 downloading options which one do i want?

  dpkg (>= 1.10.24) 
Debian package management system 

 linux-image-2.6.27-7-generic 
Linux kernel image for version 2.6.27 on x86/x86_64 


amd64 1,170.0 kB 4504 kB [list of files] 


i386 1,142.3 kB 3652 kB [list of files]

---

### Post by cptrohn on 2009-01-11
> **ajcham said:**
> Please create a new thread for your question, and people can help you there.

I did 30 minutes ago, 5 hours ago and last night. 

Never mind.

---

### Post by kevdog on 2009-01-11
No wired connection is going to be tough.  There is another way however.  Way back when people used to use a patched version of madwifi to get this chipset installed.  I believe it still may work.  It also requires some dependencies, however I believe they are contained within the installation cd rom.

So here is what to do, boot up and stick the install cd in the drive

sudo apt-cdrom add
sudo aptitude update

Then 
sudo aptitude install build-essential linux-headers-`uname -r`

You then want to download the patched madwifi driver set from here:
[http://www.mediafire.com/?mjokzl02dxu](http://www.mediafire.com/?mjokzl02dxu)

I usually dont make people download things from untrusted sources, however in this case its a problem.  Anyway download that file anyway you can and bring into the Ubuntu install.  Place it in your home directory.

Then
cd ~
tar zxvf madwifi-hal-0.10.5.6.tar.gz
cd madwifi-hal-0.10.5.6
make
sudo make install

Then please post info regarding
modinfo ath_pci

Thanks.

---

### Post by ajcham on 2009-01-11
> **kakarotman said:**
> when i go to that link there are like 4 downloading options which one do i want?


The link was just for information, I was still trying to find the file.

And here it is…
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.27/](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-2.6.27/)
You want the second option on that list: linux-backports-modules-2.6.27-7-generic_2.6.27-7.4_i386.deb

If that works, and you get your Ubuntu box online, be sure to install **linux-backports-modules-generic** as described earlier ASAP - otherwise an update to the kernel could kill your wifi again.

---

### Post by kakarotman on 2009-01-12
The thing involving the old cd did not work. there were errors all over. 

So i installed that thing and entered those commands from earlier and here it is:

josh@Josh:~$ sudo aptitude install linux-backports-modules-intrepid-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  linux-backports-modules-intrepid-generic 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2856B of archives. After unpacking 32.8kB will be used.
Writing extended state information... Done
Selecting previously deselected package linux-backports-modules-intrepid-generic.
(Reading database ... 100768 files and directories currently installed.)
Unpacking linux-backports-modules-intrepid-generic (from .../linux-backports-modules-intrepid-generic_2.6.27.7.11_i386.deb) ...
Setting up linux-backports-modules-intrepid-generic (2.6.27.7.11) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

josh@Josh:~$ sudo modprobe ath5k
josh@Josh:~$ sudo modprobe ath5k
josh@Josh:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:35:97:63
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 3a:56:2a:e0:14:8b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
josh@Josh:~$ 


Now what?? (the internet to my knowledge did not work)

(I am going to bed now but will check and try to continue to get this to work tomorrow. So if you guys are up for helping me tommorrow you could if you want)

---

### Post by kevdog on 2009-01-12
ajcham -- Nice link

Lets check a few thing:

modinfo ath5k

Just want to see if the module is installed first before going off the deep end.

---

### Post by kakarotman on 2009-01-12
Holy cow i have internet!

josh@Josh:~$ modinfo ath5k
filename:       /lib/modules/2.6.27-7-generic/updates/ath5k.ko
version:        0.6.0 (EXPERIMENTAL)
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     2F67A74BCD5DA26389BC553
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000014sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000011sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000207sv*sd*bc*sc*i*
depends:        led-class,lbm_cw-mac80211,lbm_cw-cfg80211
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
josh@Josh:~$ 

Ok now what do i need to not do to make it ever stop working?

---

### Post by ajcham on 2009-01-12
> **kakarotman said:**
> Ok now what do i need to not do to make it ever stop working?

You've installed linux-backports-modules-intrepid-generic - this is a metapackage that will update the backports modules automatically when you update your kernel, so as long as you don't uninstall it you should be OK.

[QUOTE=kevdog]ajcham -- Nice link[/QUOTE]
Thanks - funnily though, I've now discovered that the very same package is also on the Intrepid CD ([CDROM]/pool/main/l/linux-backports-modules-2.6.27), so he could have got from there also! Never mind, glad it got sorted.

---

### Post by kakarotman on 2009-01-12
Thank you so much every one!!!!

---

