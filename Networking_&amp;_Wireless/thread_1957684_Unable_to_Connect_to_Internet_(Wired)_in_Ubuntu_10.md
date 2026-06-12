---
title: "Unable to Connect to Internet (Wired) in Ubuntu 10.04 LTS"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by OrchidStar on 2012-04-12
I just setup dual boot with Ubuntu 10.04 LTS on my Windows 7 machine. I can connect to the internet just fine when I boot to Windows; however, when I boot to Ubuntu I can't connect to the internet via a wired connection. I went into the console window and typed ifconfig -a to see if my Ethernet card was visible but it wasn't. I also tried setting up a connection via Network Connections -> Wired to set up a wired connection but it's not taking. I can't seem to pin point the problem. My DHCP is setup on my Ubuntu system.
 Any ideas?

---

### Post by dandnsmith on 2012-04-13
I suggest you post the outputs from
a) lshw -C network
b) lspci -v
to give more relevant information on what is there (from ubuntu's point of view)

---

### Post by OrchidStar on 2012-04-13
lspci Output:


00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, fast devsel, latency 0
                  Capabilities: <access denied>
   
  00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
                  Flags: bus master, fast devsel, latency 0
                  Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
                  I/O behind bridge: 00003000-00003fff
                  Memory behind bridge: e1400000-e14fffff
                  Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
                  Capabilities: <access denied>
                  Kernel driver in use: pcieport
                  Kernel modules: shpchp
   
  00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, fast devsel, latency 0, IRQ 11
                  Memory at e15b0000 (64-bit, non-prefetchable) [size=16]
                  Capabilities: <access denied>
   
  00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
                  Subsystem: Dell Device 047e
                  Flags: bus master, fast devsel, latency 0, IRQ 5
                  Memory at e1500000 (32-bit, non-prefetchable) [size=128K]
                  Memory at e1580000 (32-bit, non-prefetchable) [size=4K]
                  I/O ports at 4040 [size=32]
                  Capabilities: <access denied>
   
  00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, medium devsel, latency 0, IRQ 16
                  Memory at e1570000 (32-bit, non-prefetchable) [size=1K]
                  Capabilities: <access denied>
                  Kernel driver in use: ehci_hcd
   
  00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, fast devsel, latency 0, IRQ 22
                  Memory at e1560000 (64-bit, non-prefetchable) [size=16K]
                  Capabilities: <access denied>
                  Kernel driver in use: HDA Intel
                  Kernel modules: snd-hda-intel
   
  00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
                  Flags: bus master, fast devsel, latency 0
                  Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
                  Capabilities: <access denied>
                  Kernel driver in use: pcieport
                  Kernel modules: shpchp
   
  00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
                  Flags: bus master, fast devsel, latency 0
                  Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
                  I/O behind bridge: 00002000-00002fff
                  Memory behind bridge: e0a00000-e13fffff
                  Prefetchable memory behind bridge: 00000000e0000000-00000000e09fffff
                  Capabilities: <access denied>
                  Kernel driver in use: pcieport
                  Kernel modules: shpchp
   
  00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, medium devsel, latency 0, IRQ 17
                  Memory at e1550000 (32-bit, non-prefetchable) [size=1K]
                  Capabilities: <access denied>
                  Kernel driver in use: ehci_hcd
   
  00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4) (prog-if 01)
                  Flags: bus master, fast devsel, latency 0
                  Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
                  Capabilities: <access denied>
   
  00:1f.0 ISA bridge: Intel Corporation Device 1c4c (rev 04)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, medium devsel, latency 0
                  Capabilities: <access denied>
                  Kernel modules: iTCO_wdt
   
  00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04) (prog-if 01)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
                  I/O ports at 4090 [size=8]
                  I/O ports at 4080 [size=4]
                  I/O ports at 4070 [size=8]
                  I/O ports at 4060 [size=4]
                  I/O ports at 4020 [size=32]
                  Memory at e1540000 (32-bit, non-prefetchable) [size=2K]
                  Capabilities: <access denied>
                  Kernel driver in use: ahci
                  Kernel modules: ahci
   
  00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
                  Subsystem: Dell Device 04ad
                  Flags: medium devsel, IRQ 11
                  Memory at e1530000 (64-bit, non-prefetchable) [size=256]
                  I/O ports at 4000 [size=32]
                  Kernel modules: i2c-i801
   
  01:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
                  Subsystem: Dell Device 2126
                  Flags: bus master, fast devsel, latency 0, IRQ 16
                  Memory at d0000000 (64-bit, prefetchable) [size=256M]
                  Memory at e1420000 (64-bit, non-prefetchable) [size=128K]
                  I/O ports at 3000 [size=256]
                  Expansion ROM at e1400000 [disabled] [size=128K]
                  Capabilities: <access denied>


lshw output:
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:e1500000-e151ffff memory:e1580000-e1580fff ioport:4040(size=32)

---

### Post by OrchidStar on 2012-04-13
lspci Output:


00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, fast devsel, latency 0
                  Capabilities: <access denied>
   
  00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
                  Flags: bus master, fast devsel, latency 0
                  Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
                  I/O behind bridge: 00003000-00003fff
                  Memory behind bridge: e1400000-e14fffff
                  Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
                  Capabilities: <access denied>
                  Kernel driver in use: pcieport
                  Kernel modules: shpchp
   
  00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, fast devsel, latency 0, IRQ 11
                  Memory at e15b0000 (64-bit, non-prefetchable) [size=16]
                  Capabilities: <access denied>
   
  00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
                  Subsystem: Dell Device 047e
                  Flags: bus master, fast devsel, latency 0, IRQ 5
                  Memory at e1500000 (32-bit, non-prefetchable) [size=128K]
                  Memory at e1580000 (32-bit, non-prefetchable) [size=4K]
             

                  Capabilities: <access denied>
   
  00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04) (prog-if 20)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, medium devsel, latency 0, IRQ 16
                  Memory at e1570000 (32-bit, non-prefetchable) [size=1K]
                  Capabilities: <access denied>
                  Kernel driver in use: ehci_hcd
   
  00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, fast devsel, latency 0, IRQ 22
                  Memory at e1560000 (64-bit, non-prefetchable) [size=16K]
                  Capabilities: <access denied>
                  Kernel driver in use: HDA Intel
                  Kernel modules: snd-hda-intel
   
  00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
                  Flags: bus master, fast devsel, latency 0
                  Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
                  Capabilities: <access denied>
                  Kernel driver in use: pcieport
                  Kernel modules: shpchp
   
  00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
                  Flags: bus master, fast devsel, latency 0
                  Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
                  I/O behind bridge: 00002000-00002fff
                  Memory behind bridge: e0a00000-e13fffff
                  Prefetchable memory behind bridge: 00000000e0000000-00000000e09fffff
                  Capabilities: <access denied>
                  Kernel driver in use: pcieport
                  Kernel modules: shpchp
   
  00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04) (prog-if 20)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, medium devsel, latency 0, IRQ 17
                  Memory at e1550000 (32-bit, non-prefetchable) [size=1K]
                  Capabilities: <access denied>
                  Kernel driver in use: ehci_hcd
   
  00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4) (prog-if 01)
                  Flags: bus master, fast devsel, latency 0
                  Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
                  Capabilities: <access denied>
   
  00:1f.0 ISA bridge: Intel Corporation Device 1c4c (rev 04)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, medium devsel, latency 0
                  Capabilities: <access denied>
                  Kernel modules: iTCO_wdt
   
  00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04) (prog-if 01)
                  Subsystem: Dell Device 04ad
                  Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
                 

                Memory at e1540000 (32-bit, non-prefetchable) [size=2K]                  Capabilities: <access denied>
                  Kernel driver in use: ahci
                  Kernel modules: ahci
   
  00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
                  Subsystem: Dell Device 04ad
                  Flags: medium devsel, IRQ 11
                  Memory at e1530000 (64-bit, non-prefetchable) [size=256]
                  

                  Kernel modules: i2c-i801
   
  01:00.0 VGA compatible controller: ATI Technologies Inc Device 68f9
                  Subsystem: Dell Device 2126
                  Flags: bus master, fast devsel, latency 0, IRQ 16
                  Memory at d0000000 (64-bit, prefetchable) [size=256M]
                  Memory at e1420000 (64-bit, non-prefetchable) [size=128K]
             

                  Expansion ROM at e1400000 [disabled] [size=128K]
                  Capabilities: <access denied>


lshw output:
  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:e1500000-e151ffff memory:e1580000-e1580fff ioport:4040(size=32)

---

### Post by OrchidStar on 2012-04-13
I've been reading more about this elsewhere and I am thinking that since my Ethernet Controller is an Intel Corporation Device 1502 it does not automatically work with Ubuntu. I was told elsewhere to download and extract the e1000-1.6.2.tar.gz, then create a DKMS config file, then create a DKMS module. I have instructions on how to create the DKMS config file which I did but then when I try to create a DKMS module it says that DKMS is not installed on my system. Does that sound right?  I figured that since I extracted the e1000-1.6.2.tar.gz file itwould have DKMS.

---

### Post by dandnsmith on 2012-04-14
I should have suggested:
a) sudo lshw -C network
b) sudo lspci -v

as some of the bits of interest have been suppressed.

BTW I don't think you got the lshw command parameters correct, as the output isn't focussed.

---

### Post by chili555 on 2012-04-14
The module e1000 is installed by default in 10.04. If it isn't driving your card, something else is wrong. Let's do some diagnostics. Please run and post:```
lspci -nn | grep 0200
sudo modrobe e1000
dmesg | grep e1000
```Any error or warning messages are important; please post them.

The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by OrchidStar on 2012-04-16
Chili555 here is my output after typing the commands you gave me.

lspci -nn | grep 0200
00:19.0 Ethernet Controller [0200]:Intel Corporation Device [8086:1502] (rev04)

sudo modrobe e1000
No output displayed.

dmesg | grep e1000
No output displayed.

---

### Post by chili555 on 2012-04-16
Your device is driven by the module e1000e, not e1000. They are similar but don't cover the same devices.

e1000e drives your device in later Ubuntu versions including 11.10. You could upgrade to 11.10, wait until 12.04LTS comes out in a few days or you could go back to Intel's site and download and compile e1000e.> when I try to create a DKMS module it says that DKMS is not installed on my system. Does that sound right?Correct. However, when you get an ethernet connection you can certainly install it.```
sudo apt-get install dkms
```Note that to compile this, you'll need to install build-essential and linux-headers-generic.

There may be some other sneaky tricks we can try. What is your preference?

[http://www.intel.com/support/network/sb/CS-032514.htm](http://www.intel.com/support/network/sb/CS-032514.htm)

---

### Post by OrchidStar on 2012-04-16
Thanks for your response and feedback. I would like to stick to using the 10.04LTS version for now.

In Ubuntu, I put the e1000e-1.6.2 driver in my /usr/src directory.  I did not do anything to it besides untar it. I read a bit through the README file but I was uncertain as to what to do. I also was able to acquire the dkms-2.2.03 file and placed it also in my /usr/src directory. I figured I would manually place it on  my system since I can't issue the apt-get install dkms command. I believe that 2.2.03 is the right version. In regards to the linux-headers I have a few in my /usr/src directory. 
I am not certain which to do first.

---

### Post by chili555 on 2012-04-16
> In regards to the linux-headers I have a few in my /usr/src directory. Let's check the installed status of _both_ build-essential and linux-headers-generic:```
sudo dpkg -s build-essential
sudo dpkg -s linux-headers-generic
```I don't think /usr/src is the correct place for the files e1000e and dkms. You might just drag and drop them to your desktop. As for the dkms .deb file, simply do:```
sudo dpkg -i Desktop/dkms*.deb
```After you are sure about both build-essential and linux-headers-generic, right-click the e1000e package and select *Extract Here*. Then in a terminal, do:```
cd Desktop/e1000e-1.10.6/src
sudo su
make
make install
modprobe e1000e
exit
```Do you mind if I look over your dkms instructions before you proceed? Can you give me a link?

---

### Post by OrchidStar on 2012-04-16
I just looked over the link you mentioned in your post and it makes more sense.  I'll compile the e1000e.

---

### Post by OrchidStar on 2012-04-16
Here is the link [http://www.ponap.com/ubuntu-server-10-04-3-lts-ethernet-controller-intel-corporation-device-1502-rev-04/](http://www.ponap.com/ubuntu-server-10-04-3-lts-ethernet-controller-intel-corporation-device-1502-rev-04/)

I know that these instructions are for an ubuntu server but I figure it should be the same. I'll check on the headers and the build-essentials.

---

### Post by chili555 on 2012-04-16
Looks very good to me. I see the dkms.conf file depends on finding the files in /usr/src so you'd better leave them there. Also, be sure to change the version number as needed to 1.10.6 in the dkms.conf file.

---

### Post by OrchidStar on 2012-04-16
Thanks, glad to know that it looks right.

Here is my output...apparently I don't have build-essentials installed. 

sudo dpkg -s build-essential
Package `build-essential' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


sudo dpkg -s linux-headers-generic
Package: linux-headers-generic
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 32
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-meta
Version: 2.6.32.38.44
Depends: linux-headers-2.6.32-38-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic kernel headers
 available.

---

### Post by chili555 on 2012-04-16
It's required to compile. It's actually a meta package which depends on the actual parts: make, g++, etc. It will be tedious but do-able to get and install each from here: [http://packages.ubuntu.com/lucid/build-essential](http://packages.ubuntu.com/lucid/build-essential)

Get and install all the 'depends' if not already installed. Check as above:```
sudo dpkg -s make
```As you may percieve, -s is for *status*. After you download the parts of build-essential, install each with:```
cd Desktop  <---or wherever you downloaded them
sudo dpkg -i <some_package>
```Post back if you get stuck; I'll be here for about two hours.

---

### Post by OrchidStar on 2012-04-16
Just a thought...I have the same version of Ubuntu running on a Virtual Box on a Windows machine. Is there a way  that I can tar the build-essentials files up off that Ubuntu machine and then load them up on my dual-boot machine?

---

### Post by chili555 on 2012-04-16
> I have the same version of Ubuntu running on a Virtual Box on a Windows machine.Can you find the .debs?```
sudo updatedb
locate make | grep deb
```If so, and I doubt they are there, then copy the debs to a USB key and rock on. The /usr/bin/make part is not nearly enough.

Rinse and repeat for all the parts of build-essential.

You might look in /var/cache/apt/archives/.

---

### Post by OrchidStar on 2012-04-16
Comes to think of it instead of individually installing I was wondering if I can just download the build-essentials off of the [http://packages.ubuntu.com/lucid/amd64/build-essential/download](http://packages.ubuntu.com/lucid/amd64/build-essential/download) called build-essential-11.4build1_amd64.deb? Then add it to my /var/cache/apt/archives folder? Would that work?

---

### Post by OrchidStar on 2012-04-16
I was able to find the build-essentials_11.4build1_amd64.deb in my VirtualBox in the /var/cache/apt/archives folder. Does this deb have all of the files I am supposed to download?

---

### Post by chili555 on 2012-04-16
> **OrchidStar said:**
> I was able to find the build-essentials_11.4build1_amd64.deb in my VirtualBox in the /var/cache/apt/archives folder. Does this deb have all of the files I am supposed to download?No. When you try to install it, which you must do, it will not do so; it will complain that it needs make, g++, libc6-dev and dpkg-dev. Go get them. 

Just sticking it in apt archives does not actually install it.

---

### Post by OrchidStar on 2012-04-16
Sorry for my abrupt response here's what I found in my VirtualBox. It looks like I have them. Does this all look right? Thank you.

locate make | grep deb
/var/cache/apt/archives/qt4-qmake_4%3a4.6.2-0ubuntu5.3_amd64.deb

locate g++ | grep deb
/var/cache/apt/archives/g++-4.4_4.4.3-4ubuntu5.1_amd64.deb
/var/cache/apt/archives/g++_4%3a4.4.3-1ubuntu1_amd64.deb

locate libc6-dev | grep deb
/var/cache/apt/archives/libc6-dev_2.11.1-0ubuntu7.10_amd64.deb

locate dpkg-dev | grep deb
/var/cache/apt/archives/dpkg-dev_1.15.5.6ubuntu4.5_all.deb


locate build-essential | grep deb
/var/cache/apt/archives/build-essential_11.4build1

---

### Post by OrchidStar on 2012-04-16
> **chili555 said:**
> 

Just sticking it in apt archives does not actually install it.


Good to know. Thanks

---

### Post by chili555 on 2012-04-16
> here's what I found in my VirtualBox. It looks like I have them. Does this all look right? Perfect! I assume they are going to a 64-bit system. If so, let's go!

---

### Post by OrchidStar on 2012-04-16
I hope this is not a problem (crossing-fingers) but I read that it would be okay to dual boot Ubuntu 10.04 LTS 64-bit on a 32-bit Windows system. Is this not so? I am sure it would be better to run it on a 64-bit platform because that is what it is made for but I thought I would give it a try.

---

### Post by chili555 on 2012-04-16
> Is this not so?I dunno; me no speaka da windooz. If it starts and runs without drama, I'd guess it's fine. All I was getting at was install 64-bit packages on 64-bit systems; don't try to mix and match and be aware of which you have, which it seems you are.

I asked my wife if she thought she had a 32-bit or a 64-bit system. She said I was cheap and selfish and she reckoned she had a 2-bit system!

---

### Post by OrchidStar on 2012-04-17
I uploaded the build-essentials, dpkg-dev, libc6, libc6-dev, qt4-qmake,  g++, gcc  deb files but continue to have trouble installing them.  I see  dependency issues which is preventing package installation.  

Here is the output when I try to install the following package[FONT=&quot]:
  
[/FONT]  sudo dpkg -i dpkg-dev_1.15.5.6ubuntu4.5_all.deb
   (Reading database ... 123153 files and directories currently installed.)
   Preparing to replace dpkg-dev 1.15.5.6ubuntu4.5 (using dpkg-dev_1.15.5.6ubuntu4.5_all.deb) ...
   Unpacking replacement dpkg-dev ...
   dpkg: dependency problems prevent configuration of dpkg-dev:
    dpkg-dev depends on xz-utils; however:
     Package xz-utils is not installed.
    dpkg-dev depends on patch (>= 2.2-1); however:
     Package patch is not installed.
   dpkg: error processing dpkg-dev (--install):
    dependency problems - leaving unconfigured
   Processing triggers for man-db ...
   Errors were encountered while processing:
    dpkg-dev
   

To my understanding the dpkg-dev deb file comes with the xz-utils. Not sure what is going on.Do I need to upload that independently? Thanks.

---

### Post by chili555 on 2012-04-17
> Do I need to upload that independently? Yep; and apparently, patch.

---

### Post by dandnsmith on 2012-04-19
> **OrchidStar said:**
> I hope this is not a problem (crossing-fingers) but I read that it would be okay to dual boot Ubuntu 10.04 LTS 64-bit on a 32-bit Windows system. Is this not so? I am sure it would be better to run it on a 64-bit platform because that is what it is made for but I thought I would give it a try.

If the machine is 64-bit, then you can separately choose whether to run 32-bit or 64-bit Windows and Ubuntu - just don't try to use the ubi installation for this method!

---

### Post by OrchidStar on 2012-04-20
Thanks Chili555 for your help.  I had to move on to doing the install on another computer with a ethernet card that Ubuntu recognized. It's all setup now  :) Despite not getting this resolved because of time, I sure learned a lot from this post. Thanks again!

---

