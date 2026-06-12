---
title: "Go Figure, is this possible?"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by dsimpson on 2009-04-03
Hi, 
I was hoping for help from my post, but was wondering, is the problem with my wireless so complex that there is no fix, or is it because I am not a member of Ubuntu Proper, using rather an alternative variant of Ubuntu. Anyway, if anyone has an idea, the time to spend on my issue, or some suggestion, I am very willing to listen, I just need a starting point.

I have a Belkin_G router connected to my wife's computer via Ethernet, my computer is connected, or is supposed to be, by wireless. It worked out of the box, so to speak, but I recently tried to connect to a Belkin_N wireless usb dongel and it failed. In the process I lost the connection to the old Belkin_G router, which I have since reinstalled. 
    
Now the crazy part, I have 2 HD's on my computer, one with Linuxmint Felicia (my main access) and the 2nd HD with Linuxmint Elyssia, this HD used for storing files and backing up data. I can access the router and consequently the internet through this system fine, but since it is mainly backup, I want to be able to access through my main HD. I can see all the addresses and how it is connected but cannot get that information to the network that is failing. I checked the Hardware Drivers and it says that I have an Athlon Driver installed but no activated, but there seems to be no way to connect or input the information to activate it. I need help in the worse way on this, I am totally stumped (which doesn't take much lol!) Is there a way to reconnect to my router? I am pleading with all you network guru's for you to share your expertise, I thank you in advance for any help you might render. 
    
Here is some system information, maybe it will be of help, if I need to post more please feel free to let me know. 

**ifconfig -a**

ath0      Link encap:Ethernet  HWaddr 00:11:50:d5:8d:2d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

pan0      Link encap:Ethernet  HWaddr f2:1b:26:b8:86:3b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-11-50-D5-8D-2D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18129 errors:0 dropped:0 overruns:0 frame:84438
          TX packets:3157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1571037 (1.5 MB)  TX bytes:145222 (145.2 KB)
          Interrupt:10 

 **iwlist scan**

eaglesoldier: 
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

 **lshw**

eaglesoldier-desktop      
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 639MiB
     *-cpu
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.4.2
          size: 1250MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Rage 128 RF/SG AGP
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=64 mingnt=8
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_listlshw
             configuration: driver=pata_via latency=32 module=pata_via
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=64 module=uhci_hcd
        *-serial UNCLAIMED
             description: SMBus
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@0000:00:07.5
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network UNCLAIMED
             description: Ethernet controller
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications Inc.
             physical id: a
             bus info: pci@0000:00:0a.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=64 maxlatency=28 mingnt=10
  *-scsi
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 9a:e5:2c:ab:9b:e8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

**lspci**

00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:0a.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP

**lsusb**

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 154b:000d PNY 
Bus 001 Device 003: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 001 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



Oh yeah, almost forgot, but to me it appears there might be a conflict on ifconfig -a, as ath0 and wifi0 seem to have the same HWaddress, with the exception of the wifi having a multitude of extra 0's in the address, the rest of the numbers are exactly the same.

---

### Post by dsimpson on 2009-04-11
*BUMP* Hoping for an answer.

---

### Post by t0mppa on 2009-04-11
The good news is that since you're using an Atheros chip, there are native Linux drivers for it, surprisingly Atheros actually lists Linux to be better supported driver-wise than any single Windows version. Also, no need to worry about the overlapping HW addresses, wifi0 is just a clone of ath0 that is needed for things to run properly (will have to ask someone with more expertise, if you want a more detailled answer on why both of them are required).

As to the real problem, iwlist output shows it isn't even trying to scan the wireless interfaces and lshw shows the wireless adapter is unclaimed by any driver. This suggests that fixing the driver issues would probably fix your wireless issues.

I don't have the exactly same chip as yours, but supopsedly the same MadWifi drivers should work on yours as well. Here's a nicely detailed blog entry I found the other day about installing the newest MadWifi: [http://cutec.wordpress.com/2008/08/17/acer-aspire-one-zg5-xubuntu-hardy-8041-and-atheros-wlan/]("http://cutec.wordpress.com/2008/08/17/acer-aspire-one-zg5-xubuntu-hardy-8041-and-atheros-wlan/") The download link in it has expired, since MadWifi changed their address, you can get the package from: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz") It's for XUbuntu, so you'll have to change the mcedit to suit whichever version of Ubuntu you're running (gedit for plain Ubuntu, don't remember all the rest).

Or if you're uncertain about going along with it, since it isn't listed specifically for your system, search these forums for AR2413 solutions, I remember reading a thread about some people managing to get theirs to work with NDISwrapper (which takes Windows drivers and emulates them for Linux).

---

### Post by dsimpson on 2009-04-11
t0mppa,
    Thank you for your suggestions. now comes the questions, is there a way to download the madwifi tar.gz onto a usb memory stick and then transfer to my system (unpack the files) since that is the only way I could download the files. I don't have any internet access to download directly to my system. As I stated, I can download using my 2nd hd or off my wife's computer so I would need to be able to transfer the madwifi files and load onto my computer. The wireless worked perfectly prior to my trying to use the Belkin_N router, that was when I lost computer manager and access through my _g router. I have printed out the instructions on installing wifi and will check to see that I have all dependencies installed to do the needed operations. Thanks again.

---

### Post by t0mppa on 2009-04-11
Sure, you can do that. Ubuntu should mount the USB-stick automatically and create an icon representing it on your desktop when you plug it in.

---

### Post by dsimpson on 2009-04-11
t0mppa,

I downloaded the build essential package needed by using the synaptic "Generate package download script" and placed it in my usb stick but cannot download onto my system. I tried the synaptic "Add downloaded packages" but wasn't able to run the autorun feature which would install the package. According to the link you posted I need the "build essential" package in order to complete the install of the madwifi package. Any Ideas, I am at a loss right now, but will continue to keep trying. Once I can install the dependency package then as you say, I should be able to download and install the madwifi package.

---

### Post by t0mppa on 2009-04-12
Any chance you can get hooked up with a wired connection to internet for installing build-essential? Or use the LiveCD you used to install the systemm with by adding it to Synaptic or apt sources and install build-essential from there?

I have some bad experiences about trying to DL the build-essential package and then install it. It requires quite a bunch of other packages to be DL'ed too and back when I was in a similar situation, I couldn't find same versions of said packages online that I had on my local HDD resulting in any DL'd material refusing to install.

[Here's a thread]("http://ubuntuforums.org/showthread.php?t=1123184") where the OP is trying to install build-essential through the download package-by-package-with-another-computer/OS way for reference, if you have no other choice on the matter.

---

### Post by dsimpson on 2009-04-12
Hi again,
    I will install a network card and see if I can move the router close enough to my computer and move my computer closer and try to reach each other. That will probably be the best idea, thanks for your reply.

Ok, here is an update, downloaded the dependencies, downloaded madwifi-0.9.4 and extracted but when I tried to follow the instructions that you linked to, I was unable to cd to the package and therefore couldn't complete the install process. I extracted using the archive manager, and not using terminal as shown, when I tried to go that route it said xzvf madwifi etc was not a file or folder. was I supposed to put the tar.gz exactly as posted, with the xzvf part and the yaddayadda portion or just put in the name of the downloaded file, which was madwifi-0.9.4.tar.gz. All this is new and confusing to me and I am hesitant to make the changes when they aren't working. As far as cd'ing, is the command CD or cd or Cd, does it make a difference? Anyway I cannot cd into the download as of yet. Wait for more help. Thanks.

---

### Post by dsimpson on 2009-04-13
t0mppa,

I finally figured out how to cd into the madwifi download and did "make", "make install" did "modprobe ath_pci but still no go. I will be trying to make it work but if you can think of anything that I might have missed, please correct me and maybe I can get this up and running again. Thanks

---

### Post by t0mppa on 2009-04-13
That's good. Editing a post doesn't make it pop up as unread, so missed your problems with the terminal commands there. The command is cd, both in lowercase. It's just an abbreviation from change directory. CD or Cd in a terminal will just return "command not found".

Some other terminal commands to help your life with these install things: "ls" will list all files in the directory, "pwd" will show where you are on your file system and pressing the tab key will complete long file names, when there are no other options left, which is very useful since it saves typing and makes sure you don't do typos. And the "tar xzf ..." command is just for extracting the files by using terminal, you can skip that line, if you use the archive manager to extract them.

And the point isn't to "cd into the download", but to change the terminal directory to where you extracted the files from the .tar.bz file.

You downloaded 0.9.4? I haven't used it, the latest version is 0.10.5.6, might want to give that a try. And when reinstalling, make sure you clean the old drivers out first, with the nice scripts in the scripts directory inside the directory where you extracted the tarball.

Like here's an example how it'd work on my system (I downloaded the tarball into a directory called MadWifi inside my home directory): ```
t0mppa@t0mppa:~$ pwd
/home/t0mppa
t0mppa@t0mppa:~$ cd MadWifi/
t0mppa@t0mppa:~/MadWifi$ ls
madwifi-hal-0.10.5.6-current.tar.gz
t0mppa@t0mppa:~/MadWifi$ tar xvf madwifi-hal-0.10.5.6-current.tar.gz
*snip*
lots of files listed being extracted here, since I used the v option for verbose output
*snip*
t0mppa@t0mppa:~/MadWifi$ ls
madwifi-hal-0.10.5.6-current.tar.gz  madwifi-hal-0.10.5.6-r3977-20090408
t0mppa@t0mppa:~/MadWifi$ cd madwifi-hal-0.10.5.6-r3977-20090408/
t0mppa@t0mppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408$ pwd
/home/t0mppa/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408
t0mppa@t0mppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408$ ls
ath            hal              Makefile.kernel  README      svnversion.h
ath_hal        include          Module.markers   README.dfs  THANKS
ath_rate       INSTALL          modules.order    regression  tools
BuildCaps.inc  kernelversion.c  Module.symvers   release.h
contrib        Makefile         net80211         scripts
COPYRIGHT      Makefile.inc     patch-kernel     SNAPSHOT
t0mppa@t0mppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408$ cd scripts
t0mppa@t0mppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408/scripts$ ls
find-madwifi-modules.sh  hal_unmangle.sed         make-release.bash
get_arch.mk              if_ath_hal_generator.pl  update_hal_unmangle
hal_unmangle_log         madwifi-indent
hal_unmangle.objcopy     madwifi-unload
t0mppa@t0mppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408/scripts$ sudo ./madwifi-unload
t0mppa@t0mppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408/scripts$ sudo ./find-madwifi-modules.sh 
t0mppa@t0mppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408/scripts$ cd ..
t0mppa@t0mppa:~/MadWifi/madwifi-hal-0.10.5.6-r3977-20090408$
```

If you still have trouble after trying the newer version, see [this thread]("http://ubuntuforums.org/showthread.php?t=1062962") for a good list of other options to try with your Atheros chip. Apparently the MadWifi drivers don't support all possible Atheros cards, although they do work for most of them.

---

### Post by dsimpson on 2009-04-14
Hi t0mppa,
Sorry I haven't replied sooner, I had to make a trip to the VA medical center in Spokane and that is an all day trip. I checked for your reply as soon as I got home. Thanks for the reply. 
 yes, I saw the difference in the versions of the madwifi and downloaded the latest version. I was able to do the madwifi unload but when it came to doing the find-madwifi-modules.sh $(uname -r) command I got a command not found. I then did make clean, but it didn't remove the driver from hardware drivers, so I went on to "make", then "make install" saw all the files loading and compiling, did modprobe ath_pci. I checked by doing ifconfig, it showed the driver but when I looked in network tools there was no activity and the ath0 and wifi0 were grayed out. I edited the /etc/modules and added ath_pci but that did nothing. I am still trying and tried one of the links that you pointed out, the one with the xubuntu and atheros and downloading the backports for intrepid, I see the driver in hardware drivers and it is shining a brilliant green and activated but there is no working network. I did have wires running all over to connect through ethernet and can do that again to give it another go. Will post any other changes or remedies/problems that I might encounter. Maybe a step by step dialog on how to do the install would help this slow brain of mine.

---

### Post by t0mppa on 2009-04-14
No worries, it's your Wireless that's causing trouble, not mine, so don't have to apologize for not spending 24/7 trying to get it up and running.

The 0.10.5.6 should have a find-madwifi-modules.sh script, see what's in the scripts directory (either with 'ls' command on terminal or navigate there with nautilus) and make sure you didn't mistype the name. Should really find it, since the script itself says: "If you are installing new MadWifi modules, you should consider removing those already installed, or else you may experience problems during operation."

If neither MadWifi or the backpots package driver worked for you, then the next step is to try ndiswrapper. [Here's]("http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_27.html") a link on how to accomplish that.

---

