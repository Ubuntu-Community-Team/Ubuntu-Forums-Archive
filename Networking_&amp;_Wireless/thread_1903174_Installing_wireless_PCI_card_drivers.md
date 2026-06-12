---
title: "Installing wireless PCI card drivers"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by zachapre on 2012-01-01
Just installed Ubuntu 11.10 on my desktop but don't have wireless internet access. It came with a cd to install drivers. i insert the cd, open it, double click autorun.exe and nothing happens. how do i install the drivers? this is linux-compatible but i'm BRAND NEW to linux ubuntu and don't know what im doing :confused:

---

### Post by westie457 on 2012-01-01
Hello welcome to the Forum.

You are trying to install Windows drivers to a Linux system, In about 95% of cases these drivers will never work.

Open a terminal by pressing Ctrl+Alt+T and run these commands one at a time ```
uname -a

lspci -vnn

lsmod


```

In the terminal highlight the output and paste into a New Reply between [Code] tags by clicking the # and pasting between the sets of brackets

Thank you.

---

### Post by zachapre on 2012-01-01
This wireless card is Linux compatible. When exploring the files on the installation CD it has a Windows, Linux, and Mac folder.
Heres my results from terminal....

[preston@preston-ubuntu:~$ uname -a
Linux preston-ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
preston@preston-ubuntu:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0040] (rev 18)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0042] (rev 18) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at fb800000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at cc00 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fbdfa000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at fbdf8000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at fbdf4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fbe00000-fbefffff
    Prefetchable memory behind bridge: 00000000faf00000-00000000faffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: c0000000-c01fffff
    Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06) (prog-if 20 [EHCI])
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fbdf2000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Memory behind bridge: fbf00000-fbffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b06] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at c880 [size=8]
    I/O ports at c800 [size=4]
    I/O ports at c480 [size=8]
    I/O ports at c400 [size=4]
    I/O ports at c080 [size=16]
    I/O ports at c000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: medium devsel, IRQ 10
    Memory at fbdf0000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 06) (prog-if 85 [Master SecO PriO])
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at b880 [size=8]
    I/O ports at b800 [size=4]
    I/O ports at b480 [size=8]
    I/O ports at b400 [size=4]
    I/O ports at b080 [size=16]
    I/O ports at b000 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: bus master, fast devsel, latency 0, IRQ 40
    I/O ports at d800 [size=256]
    Memory at fafff000 (64-bit, prefetchable) [size=4K]
    Memory at faff8000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at fbee0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

02:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368] (prog-if 85 [Master SecO PriO])
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7636]
    Flags: bus master, fast devsel, latency 0, IRQ 18
    I/O ports at ec00 [size=8]
    I/O ports at e880 [size=4]
    I/O ports at e800 [size=8]
    I/O ports at e480 [size=4]
    I/O ports at e400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron

03:00.0 Unclassified device [0080]: Ralink corp. Wireless PCI Adapter RT2400 / RT2460 [1814:0101]
    Subsystem: Ralink corp. Device [1814:2561]
    Flags: slow devsel, IRQ 16
    Memory at f9ff8000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel modules: rt2400pci

ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c61] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)
    Subsystem: Intel Corporation Device [8086:8086]
    Flags: bus master, fast devsel, latency 0

preston@preston-ubuntu:~$ lsmod
Module                  Size  Used by
forcedeth              67563  0 
btrfs                 648895  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    75303  0 
qnx4                   17677  0 
hfsplus                88963  0 
hfs                    54782  0 
minix                  36322  0 
ntfs                  101885  0 
vfat                   17585  0 
msdos                  17332  0 
fat                    61475  2 vfat,msdos
jfs                   186662  0 
xfs                   831526  0 
reiserfs              248828  0 
nls_utf8               12557  1 
isofs                  40253  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2400pci              19257  0 
i915                  566711  3 
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
rt2x00pci              14578  1 rt2400pci
drm_kms_helper         42558  1 i915
rt2x00lib              50325  2 rt2400pci,rt2x00pci
psmouse                73882  0 
mac80211              310872  2 rt2x00pci,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
mei                    41480  0 
drm                   236330  4 i915,drm_kms_helper
eeprom_93cx6           12725  1 rt2400pci
serio_raw              13166  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
ppdev                  17113  0 
parport_pc             36962  1 
parport                46562  3 lp,ppdev,parport_pc
joydev                 17693  0 
hid_logitech           17677  0 
ff_memless             13097  1 hid_logitech
r8169                  52788  0 
pata_jmicron           12747  1 
usbhid                 47198  1 hid_logitech
hid                    95463  2 hid_logitech,usbhid
]

---

### Post by chipbuster on 2012-01-01
Looks like your wireless card is using a RaLink chipset. I'll not say too much more about the wireless problems, since there are others on this forum that are WAAAYYY more qualified than me, but as far as software goes in general, Linux does not run .exe files. These are Windows executables. Sometimes, executables in Linux don't have file suffixes at all.


There are two (well three) primary install methods for software on Linux. One is to get it through what's called a repository. An example of this option is if you open up the Ubuntu Software Center. The software in the repository is kept and maintained by the Ubuntu developers, and is usually good to go: you hit install, it installs.

The second method is through what's called a software package. These are a lot like the .exe's of Windows, but they're designed to run on Linux systems. Since you're using Ubuntu, you'll use .deb packages--these are made for Debian, another Linux system that Ubuntu is built on.

The third is where things might get hairy. Software is written in programming languages, but machines can't really understand the language. It has to be "compiled" into a language the machine can understand. A lot of times, software developers will just distribute the source code, since compiling from source allows them to not worry as much about different flavors of Linux. This is the method that my RaLink drivers came in, and it may end up being what you need to do.

So yeah, chip's really quick, really bad intro to Linux software. Welcome to Linux :)

---

### Post by zachapre on 2012-01-01
> **chipbuster said:**
> Looks like your wireless card is using a RaLink chipset. I'll not say too much more about the wireless problems, since there are others on this forum that are WAAAYYY more qualified than me, but as far as software goes in general, Linux does not run .exe files. These are Windows executables. Sometimes, executables in Linux don't have file suffixes at all.


There are two (well three) primary install methods for software on Linux. One is to get it through what's called a repository. An example of this option is if you open up the Ubuntu Software Center. The software in the repository is kept and maintained by the Ubuntu developers, and is usually good to go: you hit install, it installs.

The second method is through what's called a software package. These are a lot like the .exe's of Windows, but they're designed to run on Linux systems. Since you're using Ubuntu, you'll use .deb packages--these are made for Debian, another Linux system that Ubuntu is built on.

The third is where things might get hairy. Software is written in programming languages, but machines can't really understand the language. It has to be "compiled" into a language the machine can understand. A lot of times, software developers will just distribute the source code, since compiling from source allows them to not worry as much about different flavors of Linux. This is the method that my RaLink drivers came in, and it may end up being what you need to do.

So yeah, chip's really quick, really bad intro to Linux software. Welcome to Linux :)

All that being said, how do i install it and get it working? Thank you  for the installation method but how do i actually go about all this?

---

### Post by chipbuster on 2012-01-01
That's going to depend on how your drivers came packaged.

You said on the CD, there were three folders: Linux, Mac, and Windows. When you look in the Linux folder, what type of file do you see? Is it a .tar.gz or a .tar.bz2?

---

### Post by zachapre on 2012-01-01
> **chipbuster said:**
> That's going to depend on how your drivers came packaged.

You said on the CD, there were three folders: Linux, Mac, and Windows. When you look in the Linux folder, what type of file do you see? Is it a .tar.gz or a .tar.bz2?

When i open the "linux" folder theres a module and WPA_suplicant .... theres various files in each folder.
there's files with the suffix: .txt .c .h .bin .conf .reg .mak .patch 


I found this readme file, but i can't make sense of what it is saying...

Build Instructions:  
====================

1> $tar -xvzf RT61_Linux_STA_Drv_x.x.x.x.tar.gz
    go to "./RT61_Linux_STA_Drv_x.x.x.x/Module" directory.
    
2> $cp Makefile.4  ./Makefile       # [kernel 2.4]
    or
   $cp Makefile.6  ./Makefile       # [kernel 2.6]
    or
   $cp Makefile.RTL865x ./Makefile  #  big endian platform
   
3> [kernel 2.4]
    $chmod 755 Configure
    $make config         # config build linux os version

4> $make all            # compile driver source code
4.1> $make install

5> $cp rt2561.bin /etc/Wireless/RT61STA/	# copy firmware
   $cp rt2561s.bin /etc/Wireless/RT61STA/
   $cp rt2661.bin /etc/Wireless/RT61STA/

6>  $dos2unix rt61sta.dat
    $cp rt61sta.dat  /etc/Wireless/RT61STA/rt61sta.dat       
    # !!!check if it is a binary file before loading !!!  
    
7> $load                
    #[kernel 2.4]
    #    $/sbin/insmod rt61.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt61.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

        
Note: Script functionality:
load            load module to kernel
unload          unload module from kernel
Configure       retrieve linux version 


=======================================================================
CONFIGURATION:  
====================
RT61 driver can be configured via following interfaces, 
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file,
     (iv)RaConfig61

i)  iwconfig comes with kernel.  
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)copy configuration file "rt61sta.dat" to /etc/Wireless/RT61STA/rt61sta.dat.
iv) RaConfig61 is utility for rt61.
           
Configuration File : rt61sta.dat
---------------------------------------
# Copy this file to /etc/Wireless/RT61STA/rt61sta.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi -b rt61sta.dat" to modify settings according to your need.
# 
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"
# for more information refer to the Readme file.

---

### Post by chipbuster on 2012-01-01
Ah boy.


Okay, what you have there are the source files (third installation method I mentioned) for the driver. I hope you're ready to start getting into the underbelly of Linux, because the only way to get that working is to use the command line to compile from source. The readme is a set of instructions telling you exactly how you need to configure this particular set of software. 

Unfortunately, this driver is designed for the 2.4 and 2.6 Linux kernels--if you're running Oneric, you'll be using the 3.0 kernel. This MIGHT not be an issue, as I was able to install my RaLink driver on the 3.0 kernel, and it was also designed for the 2.4/2.6. However, I'm afraid I won't be able to help you much more with specifics--we'll have to wait for one of the Linux gurus to show up. 

For now, what I'd recommend you do is copy the "Linux" folder from the CD over to your desktop. From there, go to command line and run the following:

> 
cd ~/Desktop
tar -xvzf RT61_ <TAB>_


Note that where I have underlined _<TAB>_. This is not an actual text entry, but you pushing the TAB button. In the default linux command line, this will intelligently complete whatever you are typing. In this case, it should fill out the name of the driver's archive without you having to type the whole thing out word-for-word. (the files are stored in a tarball, which is roughly the equivalent of a .zip file). These commands should extract the source files and prepare them for compiling. To check that it works, simply type in > ls. You should see two entries that are relevant: one that has a ".tar.gz" filetype and one that has no filetype. The one with the filetype is the original tarball archive, the one without one is the folder that the code was extracted to.

Sorry I can't help you more :\

Could we get someone who's actually good with this stuff in here? I'd continue, but I'm afraid of telling Zachapre to compile the software incorrectly and potentially break the system.

---

### Post by coffeecat on 2012-01-02
> **chipbuster said:**
> but I'm afraid of telling Zachapre to compile the software incorrectly and potentially break the system.

I have no recent experience of Ralink cards, but let's get back to basics:

> **zachapre said:**
> 
preston@preston-ubuntu:~$ lsmod

Module                  Size  Used by

rt2400pci              19257  0 

rt2x00pci              14578  1 rt2400pci

rt2x00lib              50325  2 rt2400pci,rt2x00pci


@zachapre, I've snipped out the irrelevent bits of your lsmod output. What is left shows that you have the Linux kernel driver for your Ralink RT2400 card already in memory. There should be no need to install anything at all. Ralink drivers come in the box with Ubuntu, although some Ralink chipsets can be problematic - I don't know about your particular one.

Two questions: have you clicked on the network manager icon near the top right of the screen to see if your system can see your wireless network? If it can, simply click on your network where listed and type in your passkey at the prompt.

Second. Post the output of this terminal command:

```
sudo lshw -C network
```

---

### Post by zachapre on 2012-01-02
I have tried configuring a wireless network both through the icon at the top of the screen and in the system settings. Nothing is there for wireless other than the option to fill in an entire wireless profile, which i have tried and nothing happens: and doesn't give me the option to connect.

Outcome of > sudo lshw -c network

> preston@preston-ubuntu:~$ sudo lshw -c network
[sudo] password for preston: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 6c:62:6d:c1:dc:d5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.1.77 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:d800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff memory:fbee0000-fbefffff
preston@preston-ubuntu:~$ 


I don't have a clue to what that means... i just need to know what to do lol

---

### Post by zachapre on 2012-01-02
> **chipbuster said:**
> Ah boy.


Okay, what you have there are the source files (third installation method I mentioned) for the driver. I hope you're ready to start getting into the underbelly of Linux, because the only way to get that working is to use the command line to compile from source. The readme is a set of instructions telling you exactly how you need to configure this particular set of software. 

Unfortunately, this driver is designed for the 2.4 and 2.6 Linux kernels--if you're running Oneric, you'll be using the 3.0 kernel. This MIGHT not be an issue, as I was able to install my RaLink driver on the 3.0 kernel, and it was also designed for the 2.4/2.6. However, I'm afraid I won't be able to help you much more with specifics--we'll have to wait for one of the Linux gurus to show up. 

For now, what I'd recommend you do is copy the "Linux" folder from the CD over to your desktop. From there, go to command line and run the following:



Note that where I have underlined _<TAB>_. This is not an actual text entry, but you pushing the TAB button. In the default linux command line, this will intelligently complete whatever you are typing. In this case, it should fill out the name of the driver's archive without you having to type the whole thing out word-for-word. (the files are stored in a tarball, which is roughly the equivalent of a .zip file). These commands should extract the source files and prepare them for compiling. To check that it works, simply type in . You should see two entries that are relevant: one that has a ".tar.gz" filetype and one that has no filetype. The one with the filetype is the original tarball archive, the one without one is the folder that the code was extracted to.

Sorry I can't help you more :\

Could we get someone who's actually good with this stuff in here? I'd continue, but I'm afraid of telling Zachapre to compile the software incorrectly and potentially break the system.

I tried running the command, and nothing happened. When i did the second line and hit tab nothing filled in or anything at all.

---

### Post by chipbuster on 2012-01-02
mmkay, well ignore my stupid butt xD

I managed to totally miss an entry from one of your commands that shows that your drivers are actually already installed and running (presumably they were already on your system). 

The lshw command outcome shows that your computer can't "see" the wireless card at all, even though you have the drivers running.

---

### Post by zachapre on 2012-01-02
> **chipbuster said:**
> mmkay, well ignore my stupid butt xD

I managed to totally miss an entry from one of your commands that shows that your drivers are actually already installed and running (presumably they were already on your system). 

The lshw command outcome shows that your computer can't "see" the wireless card at all, even though you have the drivers running.

So then, what do i do?
Ive been looking around on ubuntu documentation and found this link: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I tried all that stuff, and i haven't really gotten anywhere. I installed the drivers on my windows desktop and i copied the .inf files over to my ubuntu set up. I used ndiswrapper to install driver and it worked, but says hardware isn't present....

---

### Post by coffeecat on 2012-01-02
> **zachapre said:**
> I used ndiswrapper to install driver and it worked, but says hardware isn't present....

Please do not use ndiswrapper. You'll just complicate things. But note what it says: "hardware isn't present". Note also what chipbuster mentioned, that your wireless device is missing from the output of lshw. It shouldn't be if lspci is seeing it.

I suggest you run these commands again to see if both, one or neither are now seeing your wireless device. **Please** take note of case - Linux is case-sensitive. You made an error with the lshw command I gave you. Run these commands:

```
lspci | grep -i Wireless
sudo lshw -C network
```

---

### Post by zachapre on 2012-01-02
I did those commands. here's the outcome:
> preston@preston-ubuntu:~$ lspci | grep -i Wireless
03:00.0 Unclassified device [0080]: Ralink corp. Wireless PCI Adapter RT2400 / RT2460
preston@preston-ubuntu:~$ sudo lshw -C network
[sudo] password for preston: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 6c:62:6d:c1:dc:d5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw ip=192.168.1.77 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:d800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff memory:fbee0000-fbefffff
preston@preston-ubuntu:~$ 


---

### Post by coffeecat on 2012-01-02
To be honest, I'm puzzled. Your latest output confirms that the wireless card is being listed in lspci, but not in lshw. It should show in both.

Do you have Windows installed on that machine? Is the card detected in Windows?

---

### Post by chipbuster on 2012-01-02
CoffeeCat: This article briefly mentions in passing that showing on an lspci but not an lshw indicates that there's a hardware issue, but it seemed really brief and not at all insistent, so I'm not sure if that's the issue here.

[ http://www.bit-tech.net/bits/2008/04/25/working-with-wireless-in-linux/2]("http://www.bit-tech.net/bits/2008/04/25/working-with-wireless-in-linux/2")

If it doesn't show up in Windows, we'll probably know what the issue is.

---

### Post by zachapre on 2012-01-03
> **coffeecat said:**
> To be honest, I'm puzzled. Your latest output confirms that the wireless card is being listed in lspci, but not in lshw. It should show in both.

Do you have Windows installed on that machine? Is the card detected in Windows?

No, windows is not installed, as i built my desktop from scratch. And i am very puzzled as well. I do have 64-bit currently, but i am reinstalling with the 32-bit version of ubuntu.

---

### Post by chili555 on 2012-01-03
> 03:00.0 Unclassified device [0080]: Ralink corp. Wireless PCI Adapter RT2400 / RT2460 [[COLOR="Red"]1814:0101[/COLOR]]
Subsystem: Ralink corp. Device [1814:2561]
Flags: slow devsel, IRQ 16
Memory at f9ff8000 (32-bit, non-prefetchable) [size=32K]
Capabilities: <access denied>
Kernel modules: rt2400pciThe installed driver rt2400pci is correct for your device:```
$ modinfo rt2400pci 
filename:       /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
license:        GPL
description:    Ralink RT2400 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     80765ECA1183287BBE41E8D
alias:          pci:v0000[COLOR="Red"]1814[/COLOR]d0000[COLOR="Red"]0101[/COLOR]sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6
vermagic:       3.0.0-14-generic SMP mod_unload modversions 686 
```Let's see if there are messages telling us why it isn't working. Please run and post:```
dmesg | grep rt2
```Thanks.

---

### Post by zachapre on 2012-01-03
> CoffeeCat: This article briefly mentions in passing that showing on an lspci but not an lshw indicates that there's a hardware issue, but it seemed really brief and not at all insistent, so I'm not sure if that's the issue here.

[http://www.bit-tech.net/bits/2008/04/25/working-with-wireless-in-linux/2](http://www.bit-tech.net/bits/2008/04/25/working-with-wireless-in-linux/2)

If it doesn't show up in Windows, we'll probably know what the issue is.

That link must not work on 11.10 ubuntu, i tried a few things and the commands were invalid.

Any ideas of what to do?

---

### Post by zachapre on 2012-01-03
> **chili555 said:**
> The installed driver rt2400pci is correct for your device:```
$ modinfo rt2400pci 
filename:       /lib/modules/3.0.0-14-generic/kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
license:        GPL
description:    Ralink RT2400 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     80765ECA1183287BBE41E8D
alias:          pci:v0000[COLOR="Red"]1814[/COLOR]d0000[COLOR="Red"]0101[/COLOR]sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6
vermagic:       3.0.0-14-generic SMP mod_unload modversions 686 
```Let's see if there are messages telling us why it isn't working. Please run and post:```
dmesg | grep rt2
```Thanks.

Tried it and this is the outcome:
```
preston@preston-linux:~$ dmesg | grep rt2
[   16.379962] rt2400pci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.386016] phy0 -> rt2400pci_validate_eeprom: Error - Invalid EEPROM data detected.
[   16.386022] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   16.386259] rt2400pci 0000:03:00.0: PCI INT A disabled
[   16.386269] rt2400pci: probe of 0000:03:00.0 failed with error -22

```

Gave me errors, don't know what any of this means :p

---

### Post by zachapre on 2012-01-03
```
preston@preston-linux:~$ modinfo rt2400pci
filename:       /lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rt2x00/rt2400pci.ko
license:        GPL
description:    Ralink RT2400 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     80765ECA1183287BBE41E8D
alias:          pci:v00001814d00000101sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2x00pci,eeprom_93cx6
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
```

Don't know if this means anything...

---

### Post by ratcheer on 2012-01-03
If you still need help with the Ralink wireless card, I should be able to assist. My PC has a different Ralink card and I have to manually compile the driver. Yours should be fairly similar.

Tim

PS - Finish working with chili555, first. He is very good at this, too.

---

### Post by ratcheer on 2012-01-03
I don't think I can help. The RalinkTech web site shows neither Linux firmware nor driver for the RT2400. I hope chili555 can get you going with the Linux kernel driver.

Tim

---

### Post by chili555 on 2012-01-03
> phy0 -> rt2400pci_validate_eeprom: Error - Invalid EEPROM data detected.Here, probably, is the fault. It also suggests why the device shows as Unclassified device. Please see this thread. Can you move and especially firmly seat the device in its PCI slot?

[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5487](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5487)> Solved it. Before returning the card to Best Buy, I tried it in another PCI slot. This time lspci identified it as some kind of random IBM piece of hardware. I put it back in the slot it was in before. Now it comes up as an RT2561/RT61, uses the rt61pci driver, and everything works immediately. :) 

---

### Post by zachapre on 2012-01-04
> **ratcheer said:**
> I don't think I can help. The RalinkTech web site shows neither Linux firmware nor driver for the RT2400. I hope chili555 can get you going with the Linux kernel driver.

Tim

This is the company's site: [http://www.sabrent.com/downloads.php](http://www.sabrent.com/downloads.php)

when searching PCI-G802 it gives you drivers for: linux, mac, and windows and the manual.

---

### Post by zachapre on 2012-01-04
> **chili555 said:**
> Here, probably, is the fault. It also suggests why the device shows as Unclassified device. Please see this thread. Can you move and especially firmly seat the device in its PCI slot?

[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5487](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5487)


Looked at threads, he seamed to have some of the same exact errors i was getting. i opened up my case, took it out, examined it, examined pci slot...nothing wrong. Put it back in, it's firmly seated in the slot and everything.

It does say in readme file (from driver cd) that i need to compile some sort of config file...but i haven't a clue of how to do that, even with the instructions...if anyone out there knows how to do that i can give you my teamviewer code and you take control of my computer and compile the file/run commands.

---

### Post by zachapre on 2012-01-04
Would i have better luck with the 32 bit version or a different distro of linux? How about mint or fedora? 11.04 natty narwhal?

---

### Post by chili555 on 2012-01-04
I'd certainly try. Burn the 32-bit CD for Ubuntu 11.10 and try it. The same commands as above will tell you what you need to know.

Did you try a different PCI slot?

---

### Post by zachapre on 2012-01-04
> **chili555 said:**
> I'd certainly try. Burn the 32-bit CD for Ubuntu 11.10 and try it. The same commands as above will tell you what you need to know.

Did you try a different PCI slot?

Ok, but won't i still have to compile that configuration file...i have no idea about what to do for that :/

and there's only one pci slot, 2 pci express, and 1 other type of pci slot...so i only have one slot to work with for this standard-sized pci card.

---

### Post by chili555 on 2012-01-05
rt2400pci and rt61pci. whichever it needs, are included in 11.10 by default, so no compiling is needed.

---

### Post by zachapre on 2012-01-05
> **chili555 said:**
> rt2400pci and rt61pci. whichever it needs, are included in 11.10 by default, so no compiling is needed.

Well then, what should i do? 

I am installing the 32 bit version...can you give me step-by-step instructions on what i should do?

---

### Post by coffeecat on 2012-01-05
If I may add a comment again. I've been following this thread but not commenting because you are in good hands with chili555.

There is strong evidence that you have a hardware fault. Not certain, but likely. If so, all the driver compiling and installing that you can think of will not help. As chili555 says, the kernel modules (drivers) you need for that wireless chipset are included, so there is nothing to install.

Since you don't have a second PCI slot in that machine, do you have access to another machine in which you can test your Ralink PCI card? It is possible that the card itself is faulty, or it is possible that the PCI slot is faulty.

---

### Post by chili555 on 2012-01-05
> **zachapre said:**
> can you give me step-by-step instructions on what i should do?See if the card runs as expected; it should work out of the box. If not, check for errors or other problems with:```
dmesg | grep -e rt2 -e rt6
```> you are in good hands with chili555.Thank you; I appreciate your confidence.> it is possible that the PCI slot is faulty. Yes, or perhaps the card itself.

---

### Post by zachapre on 2012-01-05
> **chili555 said:**
> See if the card runs as expected; it should work out of the box. If not, check for errors or other problems with:```
dmesg | grep -e rt2 -e rt6
```Thank you; I appreciate your confidence.Yes, or perhaps the card itself.

Yes, I know I am in good hands with chilli555, he is very informative and helpfulll, and i appreciate it very much!

Ran the code....
```
[    8.467690] rt2400pci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.473421] phy0 -> rt2400pci_validate_eeprom: Error - Invalid EEPROM data detected.
[    8.473424] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[    8.473441] rt2400pci 0000:03:00.0: PCI INT A disabled
[    8.473444] rt2400pci: probe of 0000:03:00.0 failed with error -22

```

I don't have access to another machine with a standard pci slot. my whole family has laptops.

How will i know if the slot is faulty? I bought nice mobo, it's brand new (only had it for a few weeks) its an MSI h55-e33 with 8gb ddr3 ram & i3 processor.

If card/pci slot is damaged: can anyone recommend a card or usb device that is known to work for sure on ubuntu 11.10? In case it is the pci slot...would want to go with usb, pci express gen1 x1 or pci express gen2 x16 (as those are the only available interface ports for a wifi card/usb adapter).

Thank you, everyone for helping me with this! I am learning a lot about linux and ubuntu! :) 
I would never get help or support like this from Windows!

---

### Post by chili555 on 2012-01-05
> rt2400pci [COLOR="Red"]0000:03:00.0[/COLOR]: PCI INT A -> GSI 16 (level, low) -> IRQ 16There is the identifier of the slot. You might run:```
dmesg | grep 03:00
```See if there are any interesting messages aside from these. You might try again with the card removed. My money, so far, is on the card being defective.

Do you have any other PCI cards, even sound or ethernet or whatever that you could try in the slot and check dmesg?

USB wireless dongles are cheap and easy to find; I'd certainly start there. You can do some cross-matching at, for example, newegg.com. Look for wireless cards, on the left side select PCI-E x16 or x1 and see what comes up that's affordable. Then check the forum for reports on getting it working.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&N=-1&isNodeId=1&Description=wireless+adapter+for+desktop](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&N=-1&isNodeId=1&Description=wireless+adapter+for+desktop)

We'll be glad to help in any way we can.

---

### Post by zachapre on 2012-01-07
[http://www.newegg.com/Product/Product.aspx?Item=33-166-055&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=6#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=33-166-055&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=6#scrollFullInfo)

This should work great. Several reviews say it works with linux and ubuntu right out of the box. i have a 30% promo code on top of this, that makes it around $8 with free shipping!

---

### Post by chili555 on 2012-01-08
Based on other posts about this device on the forum, I believe it uses the driver r8712u that's included in 11.10 by default. I think you'll be all set.

---

### Post by zachapre on 2012-01-08
Ok, cool. So i just plug it in and something will pop up? Or, how do i get it to work once i plug it in?

---

### Post by zachapre on 2012-01-08
How about this one?

[http://www.newegg.com/Product/Product.aspx?Item=33-166-056&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=hackintosh&Page=2#scrollFullInfo](http://www.newegg.com/Product/Product.aspx?Item=33-166-056&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Keywords=hackintosh&Page=2#scrollFullInfo)

Its supposed to be faster. Is this the r8712u driver as well?

---

### Post by chili555 on 2012-01-08
> Ok, cool. So i just plug it in and something will pop up?Yep. The Network Manager icon will pop out a balloon that announces there are networks available. You click on it, select yours, supply the WPA2 password and you're all set. The ethernet should be disconnected first.> How about this one?

[http://www.newegg.com/Product/Produc...scrollFullInfo](http://www.newegg.com/Product/Produc...scrollFullInfo)

Its supposed to be faster. Is this the r8712u driver as well? Yes, indeed.

---

### Post by zachapre on 2012-01-08
Ok, i have a WEP password though, will it still work?

---

### Post by chili555 on 2012-01-08
> **zachapre said:**
> Ok, i have a WEP password though, will it still work?Certainly. It will, instead, pop up a request for your WEP password.

WEP is fairly easy to crack. If you have the option; that is, if you control the router and if all the devices in your network support WPA2, please consider moving to WPA2.

---

### Post by zachapre on 2012-01-08
> WEP is fairly easy to crack. If you have the option; that is, if you control the router and if all the devices in your network support WPA2, please consider moving to WPA2.

Yes, I know and I will look into it, thanks!

I will report back once i receive my wifi adapter!

Thank you chili555 and everyone else for all your help!

---

