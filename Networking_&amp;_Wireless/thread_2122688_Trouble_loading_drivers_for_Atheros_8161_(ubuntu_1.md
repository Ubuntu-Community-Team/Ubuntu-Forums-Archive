---
title: "Trouble loading drivers for Atheros 8161 (ubuntu 12.10)"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by johncroc on 2013-03-05
Hello all,
I am trying to get ubuntu 12.10 to see my on-board NIC.  After much searching (not to mention wailing and gnashing of teeth) I found [this]("http://ubuntuforums.org/showthread.php?p=12206393").  I followed the instructions as best I could, with adjustments for my version of ubuntu.  My machine is set up as a dula-boot (Win7 and Ubuntu).

An "arch" gets me "x86-64" and "uname -r" results in "3.5.0-17-generic"

As directed by chili555, in the post referenced above, I gathered all the packages using the Windows side of my machine, flipped over to the Ubuntu side executed "sudo dpkg -i *.deb" and got the following:
john@sahara:~/Desktop$ sudo dpkg -i *.deb
[sudo] password for john: 
(Reading database ... 142367 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu2 (using build-essential_11.5ubuntu3_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dpkg-dev 1.16.1.2ubuntu7 (using dpkg-dev_1.16.7ubuntu6_all.deb) ...
Unpacking replacement dpkg-dev ...
Preparing to replace g++ 4:4.6.3-1ubuntu5 (using g++_4.7.2-1ubuntu2_amd64.deb) ...
Unpacking replacement g++ ...
Preparing to replace gcc 4:4.6.3-1ubuntu5 (using gcc_4.7.2-1ubuntu2_amd64.deb) ...
Removing old gcc doc directory.
Unpacking replacement gcc ...
Preparing to replace libc6-dev:amd64 2.15-0ubuntu10.2 (using libc6-dev_2.15-0ubuntu20_amd64.deb) ...
Unpacking replacement libc6-dev:amd64 ...
Selecting previously unselected package linux-headers-3.5.0-25-generic.
Unpacking linux-headers-3.5.0-25-generic (from linux-headers-3.5.0-25-generic_3.5.0-25.39_amd64.deb) ...
Selecting previously unselected package linux-headers-generic.
Unpacking linux-headers-generic (from linux-headers-generic_3.5.0.25.31_amd64.deb) ...
Preparing to replace make 3.81-8.1ubuntu1 (using make_3.81-8.2ubuntu2_amd64.deb) ...
Unpacking replacement make ...
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.7 (>= 4.7.2-1~); however:
  Package g++-4.7 is not installed.


dpkg: error processing g++ (--install):
 dependency problems - leaving unconfigured
Setting up gcc (4:4.7.2-1ubuntu2) ...
Setting up libc6-dev:amd64 (2.15-0ubuntu20) ...
dpkg: dependency problems prevent configuration of linux-headers-3.5.0-25-generic:
 linux-headers-3.5.0-25-generic depends on linux-headers-3.5.0-25; however:
  Package linux-headers-3.5.0-25 is not installed.


dpkg: error processing linux-headers-3.5.0-25-generic (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.5.0-25-generic; however:
  Package linux-headers-3.5.0-25-generic is not configured yet.


dpkg: error processing linux-headers-generic (--install):
 dependency problems - leaving unconfigured
Setting up make (3.81-8.2ubuntu2) ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on g++ (>= 4:4.4.3); however:
  Package g++ is not configured yet.


dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Setting up dpkg-dev (1.16.7ubuntu6) ...
Errors were encountered while processing:
 g++
 linux-headers-3.5.0-25-generic
 linux-headers-generic
 build-essential
john@sahara:~/Desktop$ 

It looks to me like I'm still having "version" issues with the packages, but these were the closest I could come in my searching.  Can anyone help me?  

John

P.S. An lspci gets me this:
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation H77 Express Chipset LPC Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 7 Series/C210 Series Chipset Family 4-port SATA Controller [IDE mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.5 IDE interface: Intel Corporation 7 Series/C210 Series Chipset Family 2-port SATA Controller [IDE mode] (rev 04)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)

---

### Post by chili555 on 2013-03-06
I suggest you try downloading and installing *ONLY* this: [http://packages.ubuntu.com/quantal/linux-image-3.5.0-25-generic](http://packages.ubuntu.com/quantal/linux-image-3.5.0-25-generic)```
sudo dpkg -i Desktop/linux-image*.deb
```Be sure to get the 64-bit (amd64) version. If it all goes without error, reboot and your ethernet should be working.

---

### Post by johncroc on 2013-03-06
SWEET!!!

I'm at work right now, but will attempt this when I get home.

Very sincere "Thank you" for your reply.

John

---

### Post by johncroc on 2013-03-06
I was so excited about the possibility of getting the network working that I ran home for lunch to try your suggestion.

I'm afraid I have bad news and maybe an even bigger pickle:  I got the Linux image file you suggested, installed it using "sudo dpkg -i Desktop/linux-image*.deb" I looked carefully at the output and it seemed to complete with no errors.  I went into the network configuration (upper right corner icon) and it still didn't see my NIC, so I restarted ubuntu thinking maybe that's what was required for the change I made, to be implemented.  Now my wireless keyboard and mouse no longer work in ubuntu.  They work when I flip over to the windows side (that's how I'm typing this message) and they work prior to Ubuntu booting (that's how I can choose ubuntu from my boot menu).
 
Help!

John [COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]

---

### Post by chili555 on 2013-03-06
I am not very familiar with mice and keyboards. You might see what driver is loaded under an old kernel and compare it to the new one:```
lsusb
```You might also try looking for errors. When you reboot into the old kernel, the message log for the previous (new kernel) boot is stored here:```
less /var/log/dmesg.0
```Use the arrow keys to scroll back and forth to look for errors, warnings, etc. Get out of 'less' with q.

Does it help to unplug and replug the devices so you can troubleshoot?

---

### Post by johncroc on 2013-03-07
Since this has become a "Why does my Logitech wireless KB & M work fine when I boot 3.5.0-17-generic, but not at all when I boot 3.5.0-25-generic?" question, I'm going to ask that in the appropriate forum.  Thank you Chilli555 for your help.  I will come back to this thread when I get my HIDs working in 3.5.0-25-generic.

---

### Post by chili555 on 2013-03-07
> **johncroc said:**
> Since this has become a "Why does my Logitech wireless KB & M work fine when I boot 3.5.0-17-generic, but not at all when I boot 3.5.0-25-generic?" question, I'm going to ask that in the appropriate forum.  Thank you Chilli555 for your help.  I will come back to this thread when I get my HIDs working in 3.5.0-25-generic.I'll look forward to it!

---

### Post by johncroc on 2013-03-10
I'm re-animating this thread because my keyboard-issue thread in the hardware forum has received no replies.  Since the change to the "3.5.0-25-generic" kernel produced a new problem (for which I haven't been able to find a solution), I'm wondering if the smart play is to pursue a network solution that is based on the "3.5.0-17-generic" kernel.

By the way, I tried the diagnostic things chili555 suggested and I only see that the "registration" of the kbm receiver occurs when I boot the old kernel but not when I boot the new one.  No error in the new kernel...just not there at all.  Weird, because it sees my webcam (semi-exotic peripheral), but not my keyboard (fundamental peripheral).  The keyboard issue smells like a kernel "bug" to me and I don't want to get hung up on a possible "bug" that will eventually solve itself.

So, chili555, or anyone else who may have input; is there a way to solve my Atheros 8161 driver issue without upgrading the "-25" kernel?

---

### Post by chili555 on 2013-03-10
You can download the necessary bits and pieces and install it in -17. It will be very difficult without an internet connection. *VERY!* 

Do you have wireless?

---

### Post by johncroc on 2013-03-10
I do not have wireless, but in following your similar thread ([here]("http://ubuntuforums.org/showthread.php?p=12206393")) I became quite adept at downloading on the Windows side, booting Ubuntu, mounting my "windows drive" in Ubuntu, dragging files to my desktop, and running dpkg in a terminal window.

By the way, although an absolute greenhorn here in the Linux world, I am a 30 year veteran of the IT world (albeit almost exclusively on the "Windows" side).  So I'm probably more able to trudge through a set of difficult instructions than many.

I'm ready.  Fire away!  :-)

---

### Post by chili555 on 2013-03-10
> **johncroc said:**
> I do not have wireless, but in following your similar thread ([here]("http://ubuntuforums.org/showthread.php?p=12206393")) 
I'm ready.  Fire away!  :-)It's just as (??) simple as posts #4 and 6 at the link you gave. The only change I'd make is to download and compile this: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2)

Otherwise, it's all the same. As always, post back if you get stuck.

---

### Post by johncroc on 2013-03-12
-- Oops.  Didn't refresh my browser and only now saw chili's reply.  Will give it a go. --

(clueless message deleted)

---

### Post by johncroc on 2013-03-12
How/Where do I get the specific packages for 3.5.0-17-generic?  The packages I've already downloaded are for -25  and I don't see anywhere on the page (where I got them) that enables me to download the -17 packages.

---

### Post by chili555 on 2013-03-12
> **johncroc said:**
> How/Where do I get the specific packages for 3.5.0-17-generic?  The packages I've already downloaded are for -25  and I don't see anywhere on the page (where I got them) that enables me to download the -17 packages.Which specific packages do you need?

---

### Post by johncroc on 2013-03-12
> **chili555 said:**
> Which specific packages do you need?

I assume I need the packages that correspond to the ones you recommended in post #6 of this [thread]("http://ubuntuforums.org/showthread.php?p=12206393").

---

### Post by chili555 on 2013-03-13
> **johncroc said:**
> I assume I need the packages that correspond to the ones you recommended in post #6 of this [thread]("http://ubuntuforums.org/showthread.php?p=12206393").All the build-essential stuff will be the same between -17 and -25. The linux-headers can be found here: [http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17-generic](http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17-generic) as well as here [http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17](http://packages.ubuntu.com/quantal/linux-headers-3.5.0-17) ; you need both.

---

### Post by johncroc on 2013-03-14
So, I d/l'd the headers files, and attempted "sudo dpkg -i *.deb" and got what you see below.  Seeing that there was a dependency problem I checked to make sure g++-4.7~ was in the Desktop folder.  It was; so I tried to install it individually with "sudo dpkg -i g++_4.7.2-1ubuntu2_amd64.deb" and you can see what happened.  It seems to be telling me that it can't install the package because the package isn't installed yet.  I'm sure I'm misreading it.  Can you tell what's going on, and how I can fix it?

john@sahara:~$ cd Desktop
john@sahara:~/Desktop$ sudo dpkg -i *.deb
[sudo] password for john: 
(Reading database ... 151726 files and directories currently installed.)
Preparing to replace build-essential 11.5ubuntu3 (using build-essential_11.5ubuntu3_amd64.deb) ...
Unpacking replacement build-essential ...
Preparing to replace dpkg-dev 1.16.7ubuntu6 (using dpkg-dev_1.16.7ubuntu6_all.deb) ...
Unpacking replacement dpkg-dev ...
Preparing to replace g++ 4:4.7.2-1ubuntu2 (using g++_4.7.2-1ubuntu2_amd64.deb) ...
Unpacking replacement g++ ...
Preparing to replace gcc 4:4.7.2-1ubuntu2 (using gcc_4.7.2-1ubuntu2_amd64.deb) ...
Removing old gcc doc directory.
Unpacking replacement gcc ...
Preparing to replace libc6-dev:amd64 2.15-0ubuntu20 (using libc6-dev_2.15-0ubuntu20_amd64.deb) ...
Unpacking replacement libc6-dev:amd64 ...
Preparing to replace linux-headers-3.5.0-17 3.5.0-17.28 (using linux-headers-3.5.0-17_3.5.0-17.28_all.deb) ...
Unpacking replacement linux-headers-3.5.0-17 ...
Selecting previously unselected package linux-headers-3.5.0-17-generic.
Unpacking linux-headers-3.5.0-17-generic (from linux-headers-3.5.0-17-generic_3.5.0-17.28_amd64.deb) ...
Preparing to replace make 3.81-8.2ubuntu2 (using make_3.81-8.2ubuntu2_amd64.deb) ...
Unpacking replacement make ...
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.7 (>= 4.7.2-1~); however:
  Package g++-4.7 is not installed.


dpkg: error processing g++ (--install):
 dependency problems - leaving unconfigured
Setting up gcc (4:4.7.2-1ubuntu2) ...
Setting up libc6-dev:amd64 (2.15-0ubuntu20) ...
Setting up linux-headers-3.5.0-17 (3.5.0-17.28) ...
Setting up linux-headers-3.5.0-17-generic (3.5.0-17.28) ...
Setting up make (3.81-8.2ubuntu2) ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on g++ (>= 4:4.4.3); however:
  Package g++ is not configured yet.


dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Setting up dpkg-dev (1.16.7ubuntu6) ...
Errors were encountered while processing:
 g++
 build-essential
john@sahara:~/Desktop$ ls
build-essential_11.5ubuntu3_amd64.deb
dpkg-dev_1.16.7ubuntu6_all.deb
dpkg.txt
dpkg.txt~
g++_4.7.2-1ubuntu2_amd64.deb
gcc_4.7.2-1ubuntu2_amd64.deb
libc6-dev_2.15-0ubuntu20_amd64.deb
linux-headers-3.5.0-17_3.5.0-17.28_all.deb
linux-headers-3.5.0-17-generic_3.5.0-17.28_amd64.deb
lspci.txt
make_3.81-8.2ubuntu2_amd64.deb
Pkgs
john@sahara:~/Desktop$ sudo dpkg -i g++_4.7.2-1ubuntu2_amd64.deb
(Reading database ... 160289 files and directories currently installed.)
Preparing to replace g++ 4:4.7.2-1ubuntu2 (using g++_4.7.2-1ubuntu2_amd64.deb) ...
Unpacking replacement g++ ...
dpkg: dependency problems prevent configuration of g++:
 g++ depends on g++-4.7 (>= 4.7.2-1~); however:
  Package g++-4.7 is not installed.


dpkg: error processing g++ (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 g++
john@sahara:~/Desktop$ ^C
john@sahara:~/Desktop$

---

### Post by chili555 on 2013-03-17
> Package g++-4.7 is not installed.Then go get it: [http://packages.ubuntu.com/quantal/g++-4.7](http://packages.ubuntu.com/quantal/g++-4.7)

---

### Post by johncroc on 2013-03-26
I'm back from being out of town...
As you suggested, I re-downloaded g++-4.7 and attempted the install.  As you can see I seem to be caught in a "catch-22"...I can't install g++-4.7 because libstdc isn't installed, and I can't install libstdc because g++-4.7 isn't installed.
> 
john@sahara:~$ cd Desktop


john@sahara:~/Desktop$ sudo dpkg -i g++*.deb


(Reading database ...
 161045 files and directories currently installed.)


Preparing to replace g++ 4:
4.7.2-1ubuntu2 (using g++_4.7.2-1ubuntu2_amd64.deb) ...


Unpacking replacement g++ ...


Preparing to replace g++-4.7 4.7.2-2ubuntu1 (using g++-4.7_4.7.2-2ubuntu1_amd64.deb) ...


Unpacking replacement g++-4.7 ...


dpkg: dependency problems prevent configuration of g++-4.7:


 g++-4.7 depends on libstdc++6-4.7-dev (= 4.7.2-2ubuntu1); however:


  Package libstdc++6-4.7-dev is not configured yet.


dpkg: 
error processing g++-4.7 (--install):
 
dependency problems - leaving unconfigured
dpkg: 
dependency problems prevent configuration of g++:


 g++ depends on g++-4.7 (>= 4.7.2-1~); however:


  Package g++-4.7 is not configured yet.


dpkg:
 error processing g++ (--install):


 dependency problems - leaving unconfigured
Processing triggers for man-db ...


Errors were encountered while processing:
 g++-4.7
 g++


john@sahara:~/Desktop$ 




So I then I tried to install libstdc and got this:


> john@sahara:~/Desktop$ sudo dpkg -i libstdc*.deb


(Reading database ...
 161045 files and directories currently installed.)


Preparing to replace libstdc++6-4.7-dev 4.7.2-2ubuntu1 (using libstdc++6-4.7
dev_4.7.2-2ubuntu1_amd64.deb) ...


Unpacking replacement libstdc++6-4.7-dev ...


dpkg: dependency problems prevent configuration of libstdc++6-4.7-dev:


 libstdc++6-4.7-dev depends on g++-4.7 (= 4.7.2-2ubuntu1); however:


  Package g++-4.7 is not configured yet.


dpkg:
 error processing libstdc++6-4.7-dev (--install):


 dependency problems - leaving unconfigured


Errors were encountered while processing:
 libstdc++6-4.7-dev
john@sahara:~/Desktop$ 


I have no idea how to get myself out of this.
 
Thanks for all your help.

John

---

### Post by chili555 on 2013-03-26
I suggest you try to install them both at once:```
sudo dpkg -i g++*.deb libstdc*.deb
```Please let us know how this goes.

---

### Post by johncroc on 2013-03-26
You were right!  And I am happy to tell you and everyone who may encounter this post in their search for a solution to the Atheros 8161 / 8165 wired network adapter issue, that I am posting this from Firefox in Ubuntu ! ! ! ! !  (I can barely type because I'm dancing a jig across my study floor)

Thank you chili555.  You Rock.

---

### Post by chili555 on 2013-03-26
> **johncroc said:**
> You were right!  And I am happy to tell you and everyone who may encounter this post in their search for a solution to the Atheros 8161 / 8165 wired network adapter issue, that I am posting this from Firefox in Ubuntu ! ! ! ! !  (I can barely type because I'm dancing a jig across my study floor)

Thank you chili555.  You Rock.Woo hoo! Glad it's working! Have fun.

When update manager offers you a gazillion updates, one will be linux-image-3.5.0-25 or -26 or so. You will be happy to know *alx* is included by default.

---

### Post by johncroc on 2013-03-27
So...
once I had everything up and running, Software Updater had lot's to say about what I should do next.  I let it run all the updates (232 of them) and now my kernel version is 3.5.0-26, my keyboard and mouse work (thank the gods), but my network does not.  When I look in network settings it says the cable is unplugged (it's not).
 
Can I just run the "compat-wireless...deb" again and see if it comes back?  Or is there another tack I should take?

John

---

### Post by chili555 on 2013-03-27
Is the driver alx loaded?```
lsmod | grep alx
```If not, load it:```
sudo modprobe alx
```Are there any interesting messages in the log?```
dmesg | grep -e alx -e eth0
```

---

### Post by johncroc on 2013-03-27
Below are the results of those commands.  It looks to me like the alx driver is loaded, and the only thing funny in the log is the IPv6 stuff.  But I may just not understand what I'm looking at.

john@sahara:~$ lsmod | grep alx 
alx                    68240  0 
mdio                   13808  1 alx 
john@sahara:~$ 
john@sahara:~$ 
john@sahara:~$ 
john@sahara:~$ dmesg | grep -e alx -eeth0 
[    2.143501] alx 0000:03:00.0:alx(c8:60:00:9d:22:4f): Qualcomm Atheros Ethernet Network Connection 
[    2.461318] alx 0000:03:00.0: irq 46for MSI/MSI-X 
[    2.461324] alx 0000:03:00.0: irq 47for MSI/MSI-X 
[    2.461328] alx 0000:03:00.0: irq 48for MSI/MSI-X 
[    2.461333] alx 0000:03:00.0: irq 49for MSI/MSI-X 
[    2.461337] alx 0000:03:00.0: irq 50for MSI/MSI-X 
[    2.461341] alx 0000:03:00.0: irq 51for MSI/MSI-X 
[    2.461345] alx 0000:03:00.0: irq 52for MSI/MSI-X 
[    2.461349] alx 0000:03:00.0: irq 53for MSI/MSI-X 
[    2.461353] alx 0000:03:00.0: irq 54for MSI/MSI-X 
[    2.462439] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 
[    2.463013] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready 
john@sahara:~$

---

### Post by chili555 on 2013-03-28
I see nothing too alarming here, except this:> john@sahara:~$ lsmod | grep alx
alx 68240 0
[COLOR="#FF0000"]mdio[/COLOR] 13808 1 alx What is an* mdio*, we wonder.```
$ modinfo mdio
filename:       /lib/modules/3.5.0-26-generic/kernel/drivers/net/mdio.ko
license:        GPL
author:         Copyright 2006-2009 Solarflare Communications Inc.
description:    [COLOR="#FF0000"]Generic support for MDIO-compatible transceivers[/COLOR]
srcversion:     5237BB23FAD5E08B8AADDE9
depends:        
intree:         Y
vermagic:       3.5.0-26-generic SMP mod_unload modversions 
```The module alx depends only on a module named compat. As you see above mdio has no 'depends.' Is your ethernet card attached to an ordinary router, switch or...what?

What does this tell us?```
nm-tool
cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by johncroc on 2013-03-28
Yes. I am wired to a normal router/switch.  A Cisco E4200, to be exact.  It is a router with a built-in 4-port 10/100 switch and also functions as a 802.11 B/G/N wireless AP for the other devices in my home.

Results of nm-tool:
> NetworkManager Tool 


State: disconnected 


- Device: eth0----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            alx 
  State:             unavailable 
  Default:           no 
  HW Address:        C8:60:00:9D:22:4F 


  Capabilities: 
    Carrier Detect:  yes 


  Wired Properties 
    Carrier:         off 




and results of "cat /var/log/syslog | grep etwork |tail -n20"
> Mar 28 13:07:43 saharaNetworkManager[1215]:    SCPlugin-Ifupdown: (38025008) ...get_connections (managed=false): return empty list. 
Mar 28 13:07:43 saharaNetworkManager[1215]:    Ifupdown: get unmanaged devices count: 0 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> modem-manager is now available 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> monitoring kernel firmwaredirectory '/lib/firmware'. 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> WiFi enabled by radio killswitch;enabled by state file 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> WWAN enabled by radio killswitch;enabled by state file 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> WiMAX enabled by radio killswitch;enabled by state file 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> Networking is enabled by statefile 
Mar 28 13:07:43 saharaNetworkManager[1215]: <warn> failed to allocate link cache:(-10) Operation not supported 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> (eth0): carrier is OFF 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> (eth0): new Ethernet device(driver: 'alx' ifindex: 2) 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> (eth0): exported as/org/freedesktop/NetworkManager/Devices/0 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> (eth0): now managed 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> (eth0): device state change:unmanaged -> unavailable (reason 'managed') [10 20 2] 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> (eth0): bringing up device. 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> (eth0): preparing device. 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> (eth0): deactivating device(reason 'managed') [2] 
Mar 28 13:07:43 saharaNetworkManager[1215]: <info> Added default wired connection'Wired connection 1' for/sys/devices/pci0000:00/0000:00:1c.4/0000:03:00.0/net/eth0 
Mar 28 13:07:43 saharaNetworkManager[1215]: <warn> /sys/devices/virtual/net/lo:couldn't determine device driver; ignoring... 
Mar 28 13:07:43 saharaNetworkManager[1215]: <warn> /sys/devices/virtual/net/lo:couldn't determine device driver; ignoring...  


---

### Post by chili555 on 2013-03-28
> device state change:unmanaged -> unavailable (reason 'managed') May we see:```
cat /etc/network/interfaces
```Thanks.

---

### Post by johncroc on 2013-03-28
Of course you may...
> # interfaces(5) file used by ifup(8)and ifdown(8) 
auto lo 
iface lo inet loopback 

Does this imply that it thinks I have a loopback plug, plugged into my NIC, or that I have the port in the switch set up as a loopback?  I can assure you that I do not.  This machine is dual-boot and the NIC/cable/switch combination is completely functional on the Windows side.

---

### Post by chili555 on 2013-03-29
> **johncroc said:**
> Of course you may...


Does this imply that it thinks I have a loopback plug, plugged into my NIC, or that I have the port in the switch set up as a loopback?  I can assure you that I do not.  This machine is dual-boot and the NIC/cable/switch combination is completely functional on the Windows side.It means there is a dummy interface that the system uses for networking internally. Every Linux system has it, even if it's never connected to the internet and is used by Grandma to play solitaire or to run autocad. In other words, it may safely be ignored in the sense that what's in the file belongs in the file and nothing that doesn't belong and that would inhibit Network Manager is in there.

Whew!> Wired Properties
Carrier: off > Mar 28 13:07:43 saharaNetworkManager[1215]: <info> (eth0): carrier is OFF We wonder why the driver doesn't see a carrier since it works in Windows implying the switch and the cable are sound. I wonder if there is a setting in the BIOS about ethernet. We have actually seen other devices that were essentially shut down by Windows and couldn't restart in a dual-boot setting. Here, for example: [http://www.linuxquestions.org/questions/linux-networking-3/realtek-8139-8168-8169-on-2-6-21-3-or-newer-593495/](http://www.linuxquestions.org/questions/linux-networking-3/realtek-8139-8168-8169-on-2-6-21-3-or-newer-593495/)

I am a little suspicious because I have worked on other cases and haven't seen this behavior yet.

---

### Post by johncroc on 2013-03-29
It's easy enough to check the Windows "wake-on-lan" setting and try changing it.  I will go home at lunchtime and give it a go.

Either way I'll let you know and if something else occurs to you, let me know and I'll try/check that at lunch as well.

John

---

### Post by johncroc on 2013-03-29
duplicate post...

---

### Post by johncroc on 2013-03-29
> It means there is a dummy interface that the system uses for networking internally.
I understand.  Windows has a similar internal loopback.


> We wonder why the driver doesn't see a carrier since it works in Windows implying the switch and the cable are sound. I wonder if there is a setting in the BIOS...

I am a little suspicious because I have worked on other cases and haven't seen this behavior yet.

Went home and checked the NIC configuration.  There were 3 different flavors of Wake-on-LAN settings.  Tried all 8 permutations...no joy.

However, I forgot to check if there was something related in my BIOS settings.  Will do that later, around 4:00p mst.

---

### Post by johncroc on 2013-03-29
Checked the BIOS for NIC related settings.  Found a setting called "Network Stack," which was disabled.  Enabled it and found several other choices that were available when "Network Stack" was enabled; all having to do with IPv4 and IPv6.  Tried all permutations.  None affected the network availability in Ubuntu.

There was something you were confused by and we never really followed up on it[COLOR=#000000]:
[/COLOR]> [COLOR=#000000]john@sahara:~$ lsmod | grep alx [/COLOR]
[COLOR=#000000]alx 68240 0 [/COLOR]
[COLOR=#000000]mdio 13808 1 alx
[/COLOR][COLOR=#000000]

[/COLOR]So what else can we try, or what other info would be helpful to you in helping me get connected?

---

### Post by chili555 on 2013-03-29
I don't have any idea what *mdio* is for or does. This is the first I've ever encountered it. You might unload it and see what, if anything, happens:```
sudo modprobe -r mdio
```Did it produce an error or warning? Did *alx* go away as well?```
lsmod | grep alx
```Did anything change here?```
dmesg | tail -n10
nm-tool
```We are looking for carrier:on at which point, I assume, you'd connect..

We might also try blacklisting it:```
sudo su
echo "blacklist mdio" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and then check:```
dmesg | grep alx
nm-tool
```I assume you are booting into Ubuntu directly from Windows. Is there any change if you cold boot straight to Ubuntu?

We can also try the compat-wireless package which includes *alx*, despite its wireless label. Installing it without internet access is difficult but achievable. By chance, do you have or can you borrow wireless?

---

### Post by johncroc on 2013-03-30
> [FONT=Verdana][SIZE=2]I assume you are booting into Ubuntu directly from Windows. Is there any change if you cold boot straight to Ubuntu?[/SIZE][/FONT]
[COLOR=#222222][FONT=Verdana][SIZE=2]I am not booting ubuntu "from windows."  I am booting from the “GNU GRUB Ver2.00-7 ubuntu11” boot manager. So generally I am cold booting to GNU GRUB and then choosing Ubuntu.  Not sure how to bypass the boot manager once it's there and truly boot straight into Ubuntu, although it IS on it's own physical disk (SSD), so I suppose I could just physically disconnect the other devices leaving only that one.[/SIZE][/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana][SIZE=2]When I tried to unload mdio:[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]```

john@sahara:~$sudo modprobe -r mdio

```[/SIZE][/FONT][/COLOR]```
[COLOR=#222222][FONT=Verdana][SIZE=2]FATAL:Module mdio is in use. 
[/SIZE][/FONT][/COLOR]
```[COLOR=#222222][FONT=Verdana][SIZE=2]

Then I attempted toblacklist mdio:
```
john@sahara:~$ sudo su
```[/SIZE][/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana][SIZE=2]root@sahara:/home/john#echo "blacklist mdio">>/etc/modprobe.d/blacklist.conf[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]root@sahara:/home/john#exit[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]exit[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]john@sahara:~$ 
[/SIZE][/FONT][/COLOR]
```[COLOR=#222222][FONT=Verdana][SIZE=2]

Nothing looked different when I rebooted so I did an lsmod and I got this:
```
john@sahara:~$ lsmod | grep alx
```[/SIZE][/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana][SIZE=2]alx68240 0[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]mdio13808 1 alx[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]john@sahara:~$ 
[/SIZE][/FONT][/COLOR]
```[COLOR=#222222][FONT=Verdana][SIZE=2] 

Apparently my blacklist didn't work, becauseit looks like it still loaded.

So then I did a dmesg and nm-tool to be able to report what they returned:
```
john@sahara:~$dmesg | tail -n10
```[/SIZE][/FONT][/COLOR]```

[COLOR=#222222][FONT=Verdana][SIZE=2][3.548129] input: HDA Intel PCH HDMI/DP,pcm=3 as/devices/pci0000:00/0000:00:1b.0/sound/card0/input8[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2][3.548305] input: HDA Intel PCH Line as/devices/pci0000:00/0000:00:1b.0/sound/card0/input9[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2][3.548360] input: HDA Intel PCH Front Mic as/devices/pci0000:00/0000:00:1b.0/sound/card0/input10[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2][3.548389] input: HDA Intel PCH Rear Mic as/devices/pci0000:00/0000:00:1b.0/sound/card0/input11[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2][3.548482] input: HDA Intel PCH Front Headphone as/devices/pci0000:00/0000:00:1b.0/sound/card0/input12[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2][3.548518] input: HDA Intel PCH Line Out Side as/devices/pci0000:00/0000:00:1b.0/sound/card0/input13[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2][3.548544] input: HDA Intel PCH Line Out CLFE as/devices/pci0000:00/0000:00:1b.0/sound/card0/input14[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2][3.548632] input: HDA Intel PCH Line Out Surround as/devices/pci0000:00/0000:00:1b.0/sound/card0/input15[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2][3.548667] input: HDA Intel PCH Line Out Front as/devices/pci0000:00/0000:00:1b.0/sound/card0/input16[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2][4.911347] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 3 ep 0 withno TDs queued?[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]john@sahara:~$[/SIZE][/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana][SIZE=2]john@sahara:~$nm-tool[/SIZE][/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana][SIZE=2]NetworkManagerTool[/SIZE][/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana][SIZE=2]State:disconnected[/SIZE][/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana][SIZE=2]-Device: eth0-----------------------------------------------------------------[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]Type:Wired[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]Driver:alx[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]State:unavailable[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]Default:no[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]HWAddress: C8:60:00:9D:22:4F[/SIZE][/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana][SIZE=2]Capabilities:[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]CarrierDetect: yes[/SIZE][/FONT][/COLOR]


[COLOR=#222222][FONT=Verdana][SIZE=2]WiredProperties[/SIZE][/FONT][/COLOR]
[COLOR=#222222][FONT=Verdana][SIZE=2]Carrier:off[/SIZE][/FONT][/COLOR]




[COLOR=#222222][FONT=Verdana][SIZE=2]john@sahara:~$[/SIZE][/FONT][/COLOR]

```

I have compat-wireless on the machine already (that's how we got it working in the first place, before "updates" screwed it up), so it should be an easy matter to simply rerun that as I did before.  I will try that next and report back.

---

### Post by johncroc on 2013-03-30
That worked!
I recompiled the alx driver (old compile was under kernel -17, now I'm on -26).
I unloaded all wireless, bluetooth, and ethernet modules (sudo make unload)
then I loaded the newly compiled alx module (sudo modprobe alx)

and voila`  I'm on the internet again, typing this post!

Thank you chili555 for teaching me SO much about how to troubleshoot this problem and what to look for, etc.

John

---

### Post by chili555 on 2013-03-30
> I have compat-wireless on the machine already (that's how we got it working in the first place, before "updates" screwed it up), so it should be an easy matter to simply rerun that as I did before. I will try that next and report back. Wait!

You will need to download and transfer the additional package appropriate to your running kernel version:```
uname -r
```For example,on my machine, I get:```
chili@Think410:~$ uname -r
3.5.0-26-generic
```So I would need the package linux-backports-modules-cw-3.6-[COLOR="#FF0000"]3.5.0-26-generic[/COLOR]. Before you proceed, check to see if it's already installed:```
sudo dpkg -s linux-backports-modules-cw-3.6-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

At the GRUB menu, can you select your earliest kernel version (-17??) and does alx work?> I am not booting ubuntu "from windows."I simply meant restarting from Windows to Ubuntu as opposed to cold booting directly to Ubuntu. You are doing as I suggest, although it seems to help nothing. Can you tell I'm grasping at straws??

---

### Post by chili555 on 2013-03-30
> **johncroc said:**
> That worked!
I recompiled the alx driver (old compile was under kernel -17, now I'm on -26).
I unloaded all wireless, bluetooth, and ethernet modules (sudo make unload)
then I loaded the newly compiled alx module (sudo modprobe alx)

and voila`  I'm on the internet again, typing this post!

Thank you chili555 for teaching me SO much about how to troubleshoot this problem and what to look for, etc.

JohnAwesome!!!!!!!!!! Glad it's finally working.

---

