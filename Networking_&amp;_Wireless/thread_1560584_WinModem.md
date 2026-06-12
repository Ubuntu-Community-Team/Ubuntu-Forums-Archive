---
title: "WinModem"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by X5-655 on 2010-08-25
I'm guessing I'm sol.  I'll probably never use the modem anyway, but I dislike having no drivers for all the hardware.  x86_64 installation..

```
 Only plain text email is forwarded by the  Discuss@Linmodems.org List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.32-24-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: http://www.linux.org/groups/index.html.
They will know your Country's modem code, which may be essential for dialup service.
Responses from Discuss@Linmodems.org are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org 
--------------------------  System information ----------------------------
CPU=x86_64,  Ubuntu ,  ALSA_version=1.0.23
Linux version 2.6.32-24-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010
 scanModem update of:  2010_05_29

Distrib_ID=Ubuntu
DistribCodeName=lucid
AptRepositoryStem=http://us.archive.ubuntu.com/ubuntu/


The dkms driver upgrade utilities are installed,


Some modem drivers can only be used in 32 bit modem on x86_64 systems,
while some others are competent on x86_64 Systems.  Cases are:
1) http://linmodems.technion.ac.il/bigarch/archive-seventh/msg03119.html 
for the snd-hda-intel audio+modem driver. Also applicable to AC97 modem controllers.
In both cases, 32 bit libraries must be installed to support the slmodemd helper having a precompiled 32 bit component.
2) For USB modems using the slusb.ko driver. 32 bit libraries must be installed to support the slmodemd helper having a precompiled 32 bit component
3) The hsfmodem and hcfpcimodem drivers for Conexant chipsest modes are x86_64 competent.
4) agrsm packages for LSI/AgereSystems softmodems are not competent on x86_64 systems.

 There are no blacklisted modem drivers in /etc/modprobe*  files 

 Potentially useful modem drivers now loaded are:
       snd_hda_intel           

Attached USB devices are:
 ID 0bda:0159 Realtek Semiconductor Corp. 
 ID 064e:a102 Suyin Corp. 
If a cellphone is not detected, see http://ubuntuforums.org/archive/index.php/t-878554.html
A sample report is:  http://linmodems.technion.ac.il/bigarch/archive-nineth/msg00578.html

If a USB modem or cellphone is attached and was not detected, please
provide available information in your request to discuss@linmodems.org

Candidate PCI devices with modem chips are:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
High Definition Audio cards can host modem chips.

For candidate card in slot 00:14.2, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:14.2	1002:4383	103c:363f	Audio device: ATI Technologies Inc SBx00 Azalia 

 Modem interrupt assignment and sharing: 
 16:     119458       7537   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, hda_intel
 --- Bootup diagnostics for card in PCI slot 00:14.2 ----
[    0.342763] pci 0000:00:14.2: reg 10 64bit mmio: [0xf0400000-0xf0403fff]
[    0.342806] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.342810] pci 0000:00:14.2: PME# disabled
[   11.198181] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.198481] HDA Intel 0000:00:14.2: setting latency timer to 64
[   11.455912] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input11
[   11.490590] input: HDA ATI SB Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[   11.490732] input: HDA ATI SB HP Out at Ext Rear Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input13

 The PCI slot 00:14.2 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to discuss@linmodems.org
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf0400000 irq 16

 PCI slot 00:14.2 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.32-21-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.32-24-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.32-24-generic/updates/alsa/snd-hda-intel.ko
 The modem codec file for the HDA card is: /proc/asound/card0/codec#1
--------------------------------------------------------
Codec: LSI ID 1040
Address: 1
MFG Function Id: 0x2 (unsol 1)
Vendor Id: 0x11c11040
Subsystem Id: 0x103c137e
Revision Id: 0x100200
Modem Function Group: 0x1

 The audio card hosts a softmodem chip:  0x11c11040

The softmodem chip 11c11040 is hosted on the Subsytem of the High Definition Audio card,
and is supported by the AgereSystems/LSI driver pair agrmodem + agrserial, which is provided by 
the most current package agrsm-11c11040-version at http://linmodems.technion.ac.il/packages/ltmodem/11c11040/ 

If not a Conexant modem, the driver agrsm with its dependent drivers:

----------
provide audio + modem support with the modem chip residing on the subsystem.
Any particular card can host any one of several soft modem chips. 

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:14.2:
	Modem chipset  detected on
NAME="Audio device: ATI Technologies Inc SBx00 Azalia "
CLASS=0403
PCIDEV=1002:4383
SUBSYS=103c:363f
IRQ=16
HDA2=00:14.2
SOFT=1002:4383.HDA
HDAchipVendorID=11c1
CHIP=0x11c11040
IDENT=agrsm
Driver=agrsm
package=agrsm-11c11040

 For candidate modem in:  00:14.2
   0403 Audio device: ATI Technologies Inc SBx00 Azalia 
      Primary device ID:  1002:4383
    Subsystem PCI_id  103c:363f 
    Softmodem codec or chipset from diagnostics: 0x11c11040
                               from    Archives: 
                        The HDA card softmodem chip is 0x11c11040
      

Support type needed or chipset:	agrsm


      
 There is no agrsm software support for x86_64 systems, through the modem may be 
 supported on Intel/i386 installations, which do more slowly servce x86_64 processors.
 

The AgereSystems/LSI agrsm code supports compiling of a agrmodem + agrserial driver pair.
There are a few different chipsets which use this driver pair, but they use different code resources:
Chipsets			KV*	PackageNames (most current as of November 2009)
----------------------------------------------------------------------------------------------
11c1:048c and 11c1:048f         2.6.29	agrsm048pci-2.1.60_20100108_i386.deb or agrsm048pci-2.1.60_20100108.tar.gz
11c1:0620                       2.6.31  agrsm06pci-2.1.80_20100106_i386.deb or agrsm06pci-2.1.80~20100106.tar.gz !!
11c11040 (on HDA audio cards)   2.6.31  agrsm-11c11040_20091225_i386.deb or agrsm-11c11040-2.1.80~20091225.tar.bz2  !!
   All available at: http://linmodems.technion.ac.il/packages/ltmodem/11c11040/   
Additionally there are;
automation & testing                    agrsm-tools_0.0.1_all.deb or agrsm-tools-0.0.1-2.noarch.rpm
General background                      agrsm_howto.txt 
------------------------------------------------------------------------------------------------
* KV == latest kernel release with a reported success 
!! Latest update with major credit to  Nikolay Zhuravlev
   But see conflict issue: http://linmodems.technion.ac.il/bigarch/archive-nineth/msg02753.html 
   For the 11c11040 chip with kernels 2.6.31 and later a change in a modules loading settingmay be necessary.
   Within the file /etc/modprobe.d/alsa-base.conf  (or equivalent for your Distro), change the phrase:
      options snd-hda-intel power_save=10
   to:
      options snd-hda-intel power_save=0
   or the agrsm drivers will not function. For Ubuntu related systems this can be done with:
   $ sudo gedit /etc/modprobe.d/alsa-base.conf

Report from  Bjorn Wielens:
Please note- trying to load the modules on a OpenSuSE 11.2 system gives
 an error about the module_version symbol. Using:
# modprobe --force agrmodem
# modprobe --force agrserial 
is necessary to load the drivers, and does not appear to cause ill effects.


All of the above packages are dkms competent.  This means that if your Linux distros dkms package
is previously installed, if provides for future updates matching forthcoming kernels.

-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.4.3
             and the compiler used in kernel assembly: 4.4.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.4
   linuc_headers base folder /lib/modules/2.6.32-24-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at http://packages.ubuntu.com
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through http://packages.ubuntu.com
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

For guidance on FAX usage, get from http://linmodems.technion.ac.il/packages/  get faxing.tar.gz
It has samples for a modem using port /dev/ttySL0, which must be changed to match your modem's port.

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 wlan0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base.conf:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base.conf:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem.conf:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem.conf:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

```

---

### Post by varunendra on 2010-08-25
Sorry, I couldn't follow you.

If it is a support question, please summarize your problem & ask directly what you want to ask. I think whatever you've posted as 'code' should only be a reference to your question and you should also explain what it actually is.

Again, sorry for being a dumb-***, but I think doing above would get you better response for what you want to accomplish.

---

### Post by dineshs on 2010-08-25
Winmodems are not generally supported by linux.To try make it work the first step is to install scanmodem tool and see the ModemData.txt for details (such as modem chipset).I think this is what X5-655 has posted.
[http://linmodems.technion.ac.il/#scanModem](http://linmodems.technion.ac.il/#scanModem)

---

### Post by X5-655 on 2010-08-25
Yea, I posted the ScanModem output from my laptop, as it was posted by Ubuntu to try..

But the line that gets to me is that there's no agrmodem/agrserial for x86_64, and was hoping someone knew of a workaround, or if i was reading that output incorrectly.

---

### Post by dineshs on 2010-08-26
> These files are frightening for a newcomer, so if you do not understand them, send the file ModemData.txt and only that file to our discussion list  and volunteers will help you.
From [http://linmodems.technion.ac.il/#linmodems](http://linmodems.technion.ac.il/#linmodems)

---

### Post by peyre on 2010-11-05
Sorry I'm coming into this months late, but I had my first crack at an Agere Winmodem just today and managed to get it to work.  Hopefully this is of help to someone:

I had to do a whole bunch of stuff to get it to work, and I'm not sure exactly what I did and exactly what was necessary and what wasn't.  But here's what I know of what I did.

This was in Lubuntu 10.04.

I installed KPPP, martian-modem, and martian-modem-source.  martian is a LinModem project designed to support Agere Winmodems.

I also installed gnome-ppp, but it was useless: it kept hanging when I tried to detect the modem.  I eventually removed it altogether.

**This is the confusing stuff in the middle where I'm not sure just what I did:**
1. I ran sudo martian_modem, which I think started martian running.
2. At one point I ran sudo m-a a-i martian-modem and sudo m-a -f get martian-modem, which I think told me what device the modem was assigned to: /dev/ttySM0.
3. At another point I ran sudo apt-get update and sudo apt-get -s install linux-kernel-devel.
4. At yet another point I ran sudo apt-get install module-assistant.

At the end, I installed hwinfo, which I think installs the Hardware Drivers utility (installed on Ubuntu and Xubuntu by default) that controls third-party and proprietary drivers.  When I ran that utility, I saw my modem in there and active, as the Agere 164x dsp driver.

KPPP doesn't have an option for /dev/ttySM0, so I then linked it to /dev/modem:
  **sudo ln -s /dev/ttySM0 /dev/modem**

I was now able to select /dev/modem and get KPPP to recognize it.  Woohoo!

NOTE:  That command, sudo ln -s /dev/ttySM0 /dev/modem, doesn't stick when you close down your computer.  Next time you boot up and want to use the modem, you have to run it again.  I wrote that up in a text file on my Desktop so I wouldn't have to search for it next time.

---

