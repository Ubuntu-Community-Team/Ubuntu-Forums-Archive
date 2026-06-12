---
title: "Atheros AR8151 ethernet not working"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by scenered on 2010-05-07
Installed 10.04 on an Acer TimelineX 3820TG but can't get the ethernet to work.

```
$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:3000(size=128)
```Tried to add atl1e to /etc/modules with no luck.

The driver from [http://partner.atheros.com/Download.aspx?id=125](http://partner.atheros.com/Download.aspx?id=125) won't work either (error in script on make).

Any suggestions?

---

### Post by chili555 on 2010-05-07
It makes perfectly for me. You need build-essential and linux headers-generic. You also need to precede to 'make' with 'sudo su.'

---

### Post by scenered on 2010-05-07
I got the  linux headers-generic installed.
And the driver should already be in the kernel:
/lib/modules/2.6.32-22-generic/kernel/drivers/net/atl1e/atl1e.ko

What driver are you using for the AR8151?

---

### Post by chili555 on 2010-05-07
> What driver are you using for the AR8151?I do not have the device; I was merely pointing out that the version you can download from Atheros will make correctly. 

I believe the pci.id for your device is 1969:1073. Verify with:```
lspci -nn
```If so, your device is not supported in the built-in version of atl1e, but is in the version you can build from what you downloaded:```
# modinfo atl1e
filename:       /lib/modules/2.6.32-22-generic/kernel/drivers/net/atl1e/atl1e.ko
version:        1.0.1.9
license:        GPL
author:         Atheros Corporation, <xiong.huang@atheros.com>, Jie Yang <jie.yang@atheros.com>
description:    Atheros Gigabit Ethernet driver
srcversion:     D92F5696BBDCDFE391F4C3F
alias:          pci:v00001969d00002062sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="Red"]1969[/COLOR]d0000[COLOR="Red"]1073[/COLOR]sv*sd*bc*sc*i*
--- snip ---

```Post back if you get stuck.

---

### Post by scenered on 2010-05-07
Yes, it says 1969:1073:

lspci -nn
03:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)


When I run make (as root) from the downloaded driver src folder I get this error:

/bin/sh: Syntax error: "(" unexpected
make: *** [default] Error 2

---

### Post by chili555 on 2010-05-07
> **scenered said:**
> Yes, it says 1969:1073:

lspci -nn
03:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)


When I run make (as root) from the downloaded driver src folder I get this error:

/bin/sh: Syntax error: "(" unexpected
make: *** [default] Error 2The correct Makefile is in the directory above. I notice that untarring the tar.gz splatters stuff all over the /home directory; bad practice, in my opinion. Let's try this:```
mkdir AR81Family
mv AR81Family-Linux-v1.0.1.9.tar.gz AR81Family
cd AR81Family
tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz
sudo su
make install
modprobe atl1e
exit
```As I said before, you must have *build-essential* installed.

---

### Post by scenered on 2010-05-07
Thanks. There I got it ok!

---

### Post by audiocrush on 2010-06-03
Hello guys

I have the same problem, but on the link you posted in post#1 the package is corrupt.

when untaring I always get an error...

can you please upload the package somewhere?

I am very new to linux and I don't have much experience in installing packages from source. Can you help me with that?
(I have the same notebook.. an acer aspire timelineX 3820TG)
ahm.. can you check if the sound is working for you properly?
If I plug in external speakers the sound disapears... if I unplug them I can hear everything through the internal speakers ö_ö it is confusing me x] on fedora core everything works fine :/

greetings from germany

joe

---

### Post by chili555 on 2010-06-03
> I have the same problem, but on the link you posted in post#1 the package is corrupt.

when untaring I always get an error...
It's not corrupt for me. Did you follow the instructions I posted just above? It works perfectly.

---

### Post by audiocrush on 2010-06-03
I always get this error:

```
audiocrush@debistorm:~/Downloads/AR81Family$ tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz
atl1e.7
atl1e.spec
at_osdep.h
copying
dkms.conf
ldistrib.txt
Makefile
pci.updates
readme
release_note.txt
src/
src/atl1c_hw.c
src/atl1c.h
src/atl1e_hw.h
src/at_common_main.c
src/atl1e_param.c
src/kcompat.c
src/at_common.h
src/Module.symvers
src/atl1c_main.c
src/Module.markers
src/modules.order
src/atl1c_hw.h
src/atl1e_hw.c
src/atl1e_main.c
src/atl1e_ethtool.c
src/atl1c_param.c
src/atl1c_ethtool.c
src/at_osdep.h
src/kcompat_ethtool.c
src/Makefile
src/kcompat.h
src/atl1e.h

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Beende mit Fehlerstatus aufgrund vorheriger Fehler

```

*edit*

OH w0000t?!
I ignored this echo of the terminal and continued with sudo make install and it worked ._.
without the need of a restart ö_ö
I'm heavily impressed of ubuntu :D
thank you man :D

but now I have one additional question:
can you imagine why my sound is not working anymore when i plug in external speakers?

and when i unplug them i can hear the system sounds again...

---

### Post by chili555 on 2010-06-03
And then what happens when you do:```
sudo su
make install
modprobe atl1e
exit
```Does it install and create an interface and connect and download torrents?

---

### Post by audiocrush on 2010-06-03
I made an edit in my previous posting :D
I didn't recognize that a second page appeared xD

> OH w0000t?!
I ignored this echo of the terminal and continued with sudo make install  and it worked ._.
without the need of a restart ö_ö
I'm heavily impressed of ubuntu :grin:
thank you man :grin:

but now I have one additional question:
can you imagine why my sound is not working anymore when i plug in  external speakers?

and when i unplug them i can hear the system sounds again...

---

### Post by chili555 on 2010-06-03
> can you imagine why my sound is not working anymore when i plug in external speakers?

and when i unplug them i can hear the system sounds again... That's an area outside my limited expertise. I suggest you ask on General Help.

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Glad your ethernet is working! Have fun.

---

### Post by audiocrush on 2010-06-03
thanks man ^-^

---

### Post by justin.tan on 2010-06-16
Hello guys

I have the same problem and compile the ethernet driver correctly, but it does not work.

Any other's who have the same ethernet solved the problem,could you show your method to this problem?

---

### Post by Elysius on 2010-07-04
When I install a fresh copy of ubuntu and install the Atheros Family drivers, all works perfectly. But when ubuntu is being updated (new kernel, from the updates) it doesn't work any more.

I figured, I had to use 'modprobe' the driver into the kernel. But that doesn't seem to do anything. Does anyone have any suggestions?

---

### Post by thenextdon13 on 2010-07-04
I believe this is a correct statement:

The module/driver has to be built against whatever version of the kernel you are currently running.

That means that each time ubuntu downloads a new kernel update, you will need to rebuild and reinstall the module/driver


hth

---

### Post by Elysius on 2010-07-05
So I just need to do the following? Because that doens't do anything. :o

```

[FONT=monospace]sudo su
make install
modprobe atl1e

```

I thought modprobe should be sufficient, because the atheros drivers is already installed, right? That will stay installed when you update a new kernel.


[/FONT]

---

### Post by athost on 2010-07-05
Thank you, indeed. Works fine.

---

### Post by athost on 2010-07-06
The module from last kernels works fine.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/)

---

### Post by Elysius on 2010-07-07
I'm still on 2.6.32.x, just updated it with the normal update manager.
Then how come mine doens't work anymore? Is there any way to re-install or re-active the driver?

---

### Post by mgt_cole on 2010-07-12
> **scenered said:**
> Installed 10.04 on an Acer TimelineX 3820TG but can't get the ethernet to work.

```
$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:3000(size=128)
```Tried to add atl1e to /etc/modules with no luck.

The driver from [http://partner.atheros.com/Download.aspx?id=125](http://partner.atheros.com/Download.aspx?id=125) won't work either (error in script on make).

Any suggestions?


Hi,

I just installed with 10.04 and I encounter the same problem you have.  My system network module is Atheros AR8151 as I checked from Win 7 and ubuntu could not detect it.  And I don't have Internet connection when I boot up with Ubuntu.   How am I going to update the software/system?

Thank you.

---

### Post by Algot Runeman on 2010-08-06
New Acer Aspire 5820T
Dual boot Windows 7 and Kubuntu 10.04

As described above, no ethernet (okay in Win7)
Downloaded driver file from Acer site.
Installed build-essentials but not linux headers-generic (note missing hyphen after linux)
  did:
sudo apt-get install linux-headers-generic

  the kernel and the generic headers downloaded (kernel matched what I had as reported with uname -a)

After that the sudo su/make install/modprobe worked after one failed (stalled) restart and and one good restart.

Thanks for the good information. Has a bug report been filed?

Conversely, my wifi is working, so that might be the solution for the question of how to get the download for linux.

---

### Post by worldsayshi on 2010-08-25
Have the same machine and had the same problem. Solved it by building and installing the driver stated above. Installing build-essential was a bit hairy since there was no connection. I used [keryx]("https://help.ubuntu.com/community/InstallingSoftware#Use Keryx") to download the package to a usb drive in win 7 and then installed it back in Ubuntu.

Some notes:
* To install build-essential: Start keryx in ubuntu. Create a new project. Ddecline updating package list from the servers. Then you may have to go Project->Update Status. Then quit and go back to win. There you use keryx to download build-essential to your project, which can then be installed when back in ubuntu by going Project->Install Packages.
* Don't use keryx to download ubuntu updates (if you can avoid it). Sometimes keryx is messing up the dependencies - ending up not being able to run installations when back in Ubuntu.
* Once internet connection has been established using the new driver, some proprietary drivers become available. Activating the graphics driver caused the screen to go black after reboot for me, be careful with this one. I had to reinstall Ubuntu all over. (Does anyone know any thread discussing this?)
* The driver will have to, as stated, be reactivated when some updates are installed. You might have to run:
```
sudo modprobe -r atl1e
sudo modprobe atl1e

``` To first remove and then add the driver again.

---

### Post by vc0489 on 2010-09-06
Hi, I'm having the same problem with the Atheros AR8151 ethernet not working. My laptop is an Acer Aspire 5745G and I just installed Ubuntu 10.04.

I've first tried to install the driver but then found out that build-essentials is not installed.

Since I don't have any internet (wireless isn't working either) I've followed the instructions by worldsayshi and tried to install build-essentials using Keryx but I'm stuck. Ok so I've created a new project in Ubuntu but when I open it in Win7 I can't see build-essentials anywhere. Can anyone give me a helping hand?

Thanks a lot

---

### Post by dineshs on 2010-09-06
Can you try #7 in [this thread]("http://ubuntuforums.org/showthread.php?t=1555540&highlight=build-essential") to install build-essential?

---

### Post by EXCiD3 on 2010-09-06
> **vc0489 said:**
> Hi, I'm having the same problem with the Atheros AR8151 ethernet not working. My laptop is an Acer Aspire 5745G and I just installed Ubuntu 10.04.

I've first tried to install the driver but then found out that build-essentials is not installed.

Since I don't have any internet (wireless isn't working either) I've followed the instructions by worldsayshi and tried to install build-essentials using Keryx but I'm stuck. Ok so I've created a new project in Ubuntu but when I open it in Win7 I can't see build-essentials anywhere. Can anyone give me a helping hand?

Thanks a lot

Did you tell Keryx to download the latest package lists?

---

### Post by iykrichie on 2011-01-29
my latop's ethernet is an atheros and after I installed 10.04 I got it to work without problem having followed the post on this link [http://tuxthink.blogspot.com/2010/08...roller-on.html](http://tuxthink.blogspot.com/2010/08...roller-on.html) 

but I got some updates regrettably now its back to no wired network I have tried doing the same procedure again and it still didnt work on Kernel Linux 2.6.32-28 generic but if I boot into the previous kernel Linux 2.6.32-21 generic it works well.



*-network UNCLAIMED 
description: Network controller
product: Broadcom Corporation
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory:f0500000-f0503fff
*-network UNCLAIMED
description: Ethernet controller
product: AR8152 v1.1 Fast Ethernet
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:04:00.0
version: c1
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list
configuration: latency=0

---

### Post by mosaic2s on 2011-04-16
> **chili555 said:**
> The correct Makefile is in the directory above. I notice that untarring the tar.gz splatters stuff all over the /home directory; bad practice, in my opinion. Let's try this:```
mkdir AR81Family
mv AR81Family-Linux-v1.0.1.9.tar.gz AR81Family
cd AR81Family
tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz
sudo su
make install
modprobe atl1e
exit
```As I said before, you must have *build-essential* installed.


I downloaded later version. Works fine as per method above.
Restarted comp and got the hardware address and eth is working.
thanks.

---

### Post by mosaic2s on 2011-05-01
> **chili555 said:**
> The correct Makefile is in the directory above. I notice that untarring the tar.gz splatters stuff all over the /home directory; bad practice, in my opinion. Let's try this:```
mkdir AR81Family
mv AR81Family-Linux-v1.0.1.9.tar.gz AR81Family
cd AR81Family
tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz
sudo su
make install
modprobe atl1e
exit
```As I said before, you must have *build-essential* installed.

I did that too. Works fine. Have to repeat once update of the kernel happens.
Thanks.

---

### Post by ishouvik on 2011-06-24
When I try install the tar.gz file I get some errors. Please tell me how to fix it. I am quite new in Ubuntu.

---

### Post by chili555 on 2011-06-24
> **ishouvik said:**
> When I try install the tar.gz file I get some errors. Please tell me how to fix it. I am quite new in Ubuntu.Can you confirm that you have linux-headers-generic and build-essential installed? What are the errors? Can you copy and paste them to a text document so you can post them here?

---

### Post by Przemekc1 on 2011-07-14
What should I do when after typing make install I'm getting something like this:

> /home/przemekc2/AR81Family# make install
make -C ./src/ install
make[1]: Entering directory `/home/przemekc2/AR81Family/src'
Makefile:105: *** Linux kernel source not configured - missing autoconf.h.  Stop.
make[1]: Leaving directory `/home/przemekc2/AR81Family/src'
make: *** [install] Error 2


---

### Post by chili555 on 2011-07-14
> **Przemekc1 said:**
> What should I do when after typing make install I'm getting something like this:Can you confirm that you have linux-headers-generic and build-essential installed?

---

### Post by Przemekc1 on 2011-07-14
When I'm typing 
> sudo apt-get install linux-headers-generic
sudo apt-get install build-essential
it says that it is installed

---

### Post by chili555 on 2011-07-14
Which version of the AR81 driver are you trying to compile? What is your kernel version; not really Dapper, I hope:```
uname -r
```

---

### Post by Przemekc1 on 2011-07-14
Version: ARFamily-Linux-v1.0.1.9.tar.gz

after uname -r:
> 2.6.39-10-generic

Ubuntu 11.04

---

### Post by chili555 on 2011-07-14
I have been playing with this for a while now. I can get rid of this error:> Makefile:105: *** Linux kernel source not configured - missing autoconf.h. Stop.Then when I try 'make' two more errors are thrown out. After an hour, I gave up.

I downloaded compat-wireless: [http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball](http://wireless.kernel.org/en/users/Download#Directly_downloading_the_tarball)

I extracted it and then:```
cd Desktop/compat
```Press Tab and let the rest fill in for you. Of course, substitute your downloaded location if not desktop.```
./scripts/driver-select [COLOR="Red"]atl1e[/COLOR]
```I assume you are trying to build atl1e; if not, please stop and ask.```
make
sudo make install
sudo modprobe atl1e
```I built the driver with no errors or warnings on my Natty system.

---

### Post by TXbirder on 2011-07-17
Can you simplify the instructions, please?  I do not understand half of what has been said above.  I have a new Acer Aspire 1830.  Internet access is OK with WiFi but unavaliable via Ethernet.  

John

---

### Post by chili555 on 2011-07-18
> **TXbirder said:**
> Can you simplify the instructions, please?  I do not understand half of what has been said above.  I have a new Acer Aspire 1830.  Internet access is OK with WiFi but unavaliable via Ethernet.  

JohnI suggest you check your device ID first and be sure you need atl1e. Open a terminal and run and post:```
lspci -nn | grep 0200
```Post the result and we'll make sure that atl1e is the driver you need. The pipe symbol | is on the right side of my US keyboard on the same key with \. 

Make sure you have installed the build tools. Open a terminal and do:```
sudo apt-get install build-essential linux-headers-generic
```Download the package I referred to above. Please see attached. Where-ever the file ends up on your computer, drag and drop it to your desktop. Right-click the tar.bz2 file and select Extract Here. A folder will be created called compat-wireless-something. It doesn't really matter what it is, we will use a Linux trick to fill it in. Back to the terminal and do:```
cd Desktop/compat
```Press Tab and let the rest fill in for you. Now do:
```
./scripts/driver-select atl1e
make
sudo make install
sudo modprobe atl1e

```Your wired ethernet should now be working.

---

### Post by TXbirder on 2011-07-19
john@john-laptop:~$ lspci -nn | grep 0200
01:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
john@john-laptop:~$

---

### Post by chili555 on 2011-07-19
> Atheros Communications AR8151 v1.0 Gigabit Ethernet [[COLOR="Red"]1969:1073[/COLOR]] (rev c0)Your device is driven by the module atl1[COLOR="Red"]c[/COLOR]. Please be careful, the module name is lower-case of ATL1C. Specify atl1c in driver-select and proceed as I outlined.

---

### Post by TXbirder on 2011-07-20
When I open a terminal and enter the first item 

**s****udo apt-get install build.**......etc

the terminal gives me**   [sudo] password for john:** 

   but the keyboard is dead.  I am unable to enter my password.
I closed the terminal and tried again.  Same result.

The keyboard works fine otherwise but is dead on the terminal after that entry.

John

---

### Post by chili555 on 2011-07-20
For security reasons, Ubuntu doesn't echo back your password or even ****. Just type it in and press Enter. If it is incorrect, you'll get something like:```
chili@LAPTOP40:~$ sudo synaptic
[sudo] password for chili: 
Sorry, try again.
[sudo] password for chili: 
```If it's correct, you'll get execution of the requested command and then returned to the command prompt:> chili@LAPTOP40:~$

---

### Post by TXbirder on 2011-07-21
Sorry- I know this is getting tiresome.  I got the following on the terminal  (see bottom) but am unable to find any file or folder it created.  I have used **Search for files....** and got a blank.
John


john@john-laptop:~$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21-generic linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev linux-headers-2.6.32-33
  linux-headers-2.6.32-33-generic patch xz-utils
Suggested packages:
  debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc
  libstdc++6-4.4-dbg libstdc++6-4.4-doc diffutils-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev
  linux-headers-2.6.32-33 linux-headers-2.6.32-33-generic patch xz-utils
The following packages will be upgraded:
  linux-headers-generic
1 upgraded, 10 newly installed, 0 to remove and 427 not upgraded.
Need to get 19.1MB of archives.
After this operation, 112MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libstdc++6-4.4-dev 4.4.3-4ubuntu5 [1,522kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main g++-4.4 4.4.3-4ubuntu5 [5,756kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main g++ 4:4.4.3-1ubuntu1 [1,450B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main xz-utils 4.999.9beta+20091116-1 [233kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main patch 2.6-2ubuntu1 [121kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main dpkg-dev 1.15.5.6ubuntu4.5 [654kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main build-essential 11.4build1 [7,278B]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main fakeroot 1.14.4-1ubuntu1 [101kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-headers-2.6.32-33 2.6.32-33.70 [9,924kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-headers-2.6.32-33-generic 2.6.32-33.70 [799kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-headers-generic 2.6.32.33.39 [4,566B]
Fetched 19.1MB in 59s (322kB/s)                                                
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 122124 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.3-4ubuntu5_amd64.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.3-4ubuntu5_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.3-1ubuntu1_amd64.deb) ...
Selecting previously deselected package xz-utils.
Unpacking xz-utils (from .../xz-utils_4.999.9beta+20091116-1_amd64.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.5.6ubuntu4.5_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4build1_amd64.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_amd64.deb) ...
Selecting previously deselected package linux-headers-2.6.32-33.
Unpacking linux-headers-2.6.32-33 (from .../linux-headers-2.6.32-33_2.6.32-33.70_all.deb) ...
Selecting previously deselected package linux-headers-2.6.32-33-generic.
Unpacking linux-headers-2.6.32-33-generic (from .../linux-headers-2.6.32-33-generic_2.6.32-33.70_amd64.deb) ...
Preparing to replace linux-headers-generic 2.6.32.21.22 (using .../linux-headers-generic_2.6.32.33.39_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Processing triggers for man-db ...
Setting up xz-utils (4.999.9beta+20091116-1) ...
Setting up patch (2.6-2ubuntu1) ...
Setting up dpkg-dev (1.15.5.6ubuntu4.5) ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up linux-headers-2.6.32-33 (2.6.32-33.70) ...
Setting up linux-headers-2.6.32-33-generic (2.6.32-33.70) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-33-generic /boot/vmlinuz-2.6.32-33-generic

Setting up linux-headers-generic (2.6.32.33.39) ...
Setting up libstdc++6-4.4-dev (4.4.3-4ubuntu5) ...
Setting up g++-4.4 (4.4.3-4ubuntu5) ...
Setting up g++ (4:4.4.3-1ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.

Setting up build-essential (11.4build1) ...
john@john-laptop:~$

---

### Post by chili555 on 2011-07-21
Go back to post #38. did you download the file I suggested to your desktop? If not, please do so and then proceed as outlined there. Post back if you get stuck. I am anxious to help you get going.

---

### Post by TXbirder on 2011-07-21
OK.  I started again.  Terminal gave me this:

john@john-laptop:~$ sudo apt-get install build-essential linux-headers-generic
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21-generic linux-headers-2.6.32-21
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 427 not upgraded.
john@john-laptop:~$ 

Then I searched for files named ** build-essential,  linux headers generic, inux-headers-2.6.32-21-generic linux-headers-2.6.32-21, **with no success.  I searched in Home Folder, Desktop, Documents, Downloads, Recent Documents- no luck.

John

---

### Post by chili555 on 2011-07-21
You don't have to search for them or find them or use them or install them again. They are tools that are needed for compiling the driver. They are properly installed and ready to go as is. Please proceed as above:> Download the package I referred to above. Please see attached. Where-ever the file ends up on your computer, drag and drop it to your desktop. Right-click the tar.bz2 file and select Extract Here. A folder will be created called compat-wireless-something. It doesn't really matter what it is, we will use a Linux trick to fill it in. Back to the terminal and do:
```
cd Desktop/compat

```
Press Tab and let the rest fill in for you. Now do:
```
./scripts/driver-select atl1e
make
sudo make install
sudo modprobe atl1e
```

Your wired ethernet should now be working. 

---

### Post by TXbirder on 2011-07-21
Sorry.  Didn't realize I had to go elsewhere to find and download this package.

In Downloads:     /home/john/Downloads/compat-wireless-2.6.tar.bz2

Extracted.  On terminal did:  cd Desktop/compat

john@john-laptop:~$ cd Desktop/compat
bash: cd: Desktop/compat: No such file or directory
john@john-laptop:~$ cd Desktop/compat
bash: cd: Desktop/compat: No such file or directory
john@john-laptop:~$ cd Desktop/compat
bash: cd: Desktop/compat: No such file or directory
john@john-laptop:~$ 

It apparently is not extracting properly.  I extracted twice.
John

---

### Post by chili555 on 2011-07-21
My tutorial said that wherever the file ends up, drag and drop it to your desktop. You evidently omitted that step. Please try:```
cd Downloads/compat
```Now press Tab and let the remainder fill in automatically. Press Enter. Now proceed:```
./scripts/driver-select atl1e
make
sudo make install
sudo modprobe atl1e
```

---

### Post by TXbirder on 2011-07-24
Not on line.
john@john-laptop:~$ cd Desktop/compat-wireless-2011-07-20\ \(2\)/./scripts/driver-select atl1e
bash: cd: Desktop/compat-wireless-2011-07-20 (2)/./scripts/driver-select: Not a directory
john@john-laptop:~$ 
john@john-laptop:~$ cd Desktop/compat-wireless-2011-07-20\ \(2\)/./scripts/driver-select atl1e
bash: cd: Desktop/compat-wireless-2011-07-20 (2)/./scripts/driver-select: Not a directory
john@john-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
john@john-laptop:~$ sudo make install
[sudo] password for john: 
make: *** No rule to make target `install'.  Stop.
john@john-laptop:~$ ./scripts/driver-select atl1e
bash: ./scripts/driver-select: No such file or directory
john@john-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
john@john-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
john@john-laptop:~$ sudo modprobe atl1e
john@john-laptop:~$

---

### Post by chili555 on 2011-07-24
> cd Desktop/compat-wireless-2011-07-20\ \(2\)This process will have problems with a file with a (2) in the name. Look on your desktop, right-click the file and rename it to compat.

Now go back to the terminal and do:```
cd Desktop/compat
./scripts/driver-select atl1e
make
sudo make install
sudo modprobe atl1e
```Incidentally, when you encounter any error (not warnings), all subsequent steps will result in errors, too. Stop and ask at the very first error.

---

### Post by TXbirder on 2011-07-24
Stiil no ethernet.
Do I need to perform the actions in the final lines of the terminal response?


  	 	 	 	 	 	  cd Desktop/compat ./scripts/driver-select atl1e make sudo make install sudo modprobe atl1e ohn@john-laptop:~$ cd Desktop/compat  
 john@john-laptop:~/Desktop/compat$ ./scripts/driver-select atl1e  
 Processing new driver-select request... 
 Backing up makefile: Makefile.bk  
 Backup exists: Makefile.bk  
 Backing up makefile: drivers/net/Makefile.bk  
 Backup exists: Makefile.bk  
 Backup exists: Makefile.bk  
 john@john-laptop:~/Desktop/compat$ make 
 ./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h  
 make -C /lib/modules/2.6.32-21-generic/build M=/home/john/Desktop/compat modules  
 make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'  
   LD      /home/john/Desktop/compat/compat/built-in.o  
   CC [M]  /home/john/Desktop/compat/compat/main.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.33.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.35.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.36.o  
   CC [M]  /home/john/Desktop/compat/compat/kfifo.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.37.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.38.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.39.o  
   CC [M]  /home/john/Desktop/compat/compat/kstrtox.o  
   LD [M]  /home/john/Desktop/compat/compat/compat.o  
   CC [M]  /home/john/Desktop/compat/compat/compat_firmware_class.o  
   LD      /home/john/Desktop/compat/drivers/net/atl1e/built-in.o  
   CC [M]  /home/john/Desktop/compat/drivers/net/atl1e/atl1e_main.o  
   CC [M]  /home/john/Desktop/compat/drivers/net/atl1e/atl1e_hw.o  
   CC [M]  /home/john/Desktop/compat/drivers/net/atl1e/atl1e_ethtool.o  
   CC [M]  /home/john/Desktop/compat/drivers/net/atl1e/atl1e_param.o  
   LD [M]  /home/john/Desktop/compat/drivers/net/atl1e/atl1e.o  
   LD      /home/john/Desktop/compat/built-in.o  
   Building modules, stage 2.  
   MODPOST 3 modules  
   CC      /home/john/Desktop/compat/compat/compat.mod.o  
   LD [M]  /home/john/Desktop/compat/compat/compat.ko  
   CC      /home/john/Desktop/compat/compat/compat_firmware_class.mod.o  
   LD [M]  /home/john/Desktop/compat/compat/compat_firmware_class.ko  
   CC      /home/john/Desktop/compat/drivers/net/atl1e/atl1e.mod.o  
   LD [M]  /home/john/Desktop/compat/drivers/net/atl1e/atl1e.ko  
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'  
 john@john-laptop:~/Desktop/compat$ sudo make install  
 

 Your old wireless subsystem modules were left intact:  
 

 kernel/net/mac80211/mac80211.ko  
 kernel/net/wireless/cfg80211.ko  
 kernel/net/wireless/lib80211.ko  
 kernel/drivers/net/wireless/adm8211.ko  
 kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko 
 kernel/drivers/net/wireless/at76c50x-usb.ko 
 kernel/drivers/net/wireless/ath/ath.ko  
 kernel/drivers/net/wireless/ath/ath5k/ath5k.ko 
 kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
 kernel/drivers/net/wireless/b43/b43.ko  
 kernel/drivers/net/wireless/b43legacy/b43legacy.ko 
 kernel/drivers/net/b44.ko  
 kernel/drivers/net/usb/cdc_ether.ko  
 kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
 kernel/drivers/net/wireless/ipw2x00/ipw2100.ko 
 kernel/drivers/net/wireless/ipw2x00/ipw2200.ko 
 kernel/drivers/net/wireless/iwlwifi/iwl3945.ko 
 kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 
 kernel/drivers/net/wireless/iwlwifi/iwlcore.ko 
 kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko 
 kernel/net/wireless/lib80211_crypt_ccmp.ko 
 kernel/net/wireless/lib80211_crypt_tkip.ko 
 kernel/net/wireless/lib80211_crypt_wep.ko 
 kernel/drivers/net/wireless/libertas/libertas.ko 
 kernel/drivers/net/wireless/libertas/libertas_cs.ko 
 kernel/drivers/net/wireless/libertas/libertas_sdio.ko 
 kernel/drivers/net/wireless/libertas/libertas_spi.ko 
 kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko 
 kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko 
 kernel/drivers/net/wireless/ipw2x00/libipw.ko 
 kernel/drivers/net/wireless/mac80211_hwsim.ko 
 kernel/drivers/net/wireless/mwl8k.ko  
 kernel/drivers/net/wireless/orinoco/orinoco_cs.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_pci.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_plx.ko 
 kernel/drivers/net/wireless/orinoco/orinoco.ko 
 kernel/drivers/net/wireless/p54/p54common.ko 
 kernel/drivers/net/wireless/p54/p54pci.ko 
 kernel/drivers/net/wireless/p54/p54spi.ko 
 kernel/drivers/net/wireless/p54/p54usb.ko 
 kernel/drivers/net/usb/rndis_host.ko  
 kernel/drivers/net/wireless/rndis_wlan.ko 
 kernel/drivers/net/wireless/rt2x00/rt2400pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2500pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2500usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt2800usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt61pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt73usb.ko 
 kernel/drivers/net/wireless/rtl818x/rtl8180.ko 
 kernel/drivers/net/wireless/rtl818x/rtl8187.ko 
 kernel/drivers/net/wireless/orinoco/spectrum_cs.ko 
 kernel/drivers/ssb/ssb.ko  
 kernel/drivers/net/wireless/libertas/usb8xxx.ko 
 kernel/drivers/net/usb/usbnet.ko  
 kernel/drivers/net/wireless/wl12xx/wl1251.ko 
 kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko 
 

 Your old ethernet subsystem modules are left intact:  
 

 kernel/drivers/net/atlx/atl1.ko  
 kernel/drivers/net/atlx/atl2.ko  
 kernel/drivers/net/atl1e/atl1e.ko  
 kernel/drivers/net/atl1c/atl1c.ko  
 

 Your old bluetooth subsystem modules were left intact:  
 

 kernel/drivers/bluetooth/bcm203x.ko  
 kernel/drivers/bluetooth/bluecard_cs.ko 
 kernel/net/bluetooth/bluetooth.ko  
 kernel/net/bluetooth/bnep/bnep.ko  
 kernel/drivers/bluetooth/bpa10x.ko  
 kernel/drivers/bluetooth/bt3c_cs.ko  
 kernel/drivers/bluetooth/btmrvl.ko  
 kernel/drivers/bluetooth/btmrvl_sdio.ko 
 kernel/drivers/bluetooth/btsdio.ko  
 kernel/drivers/bluetooth/btusb.ko  
 kernel/drivers/bluetooth/btuart_cs.ko  
 kernel/net/bluetooth/cmtp/cmtp.ko  
 kernel/drivers/bluetooth/dtl1_cs.ko  
 kernel/net/bluetooth/hidp/hidp.ko  
 kernel/drivers/bluetooth/hci_vhci.ko  
 kernel/drivers/bluetooth/hci_uart.ko  
 kernel/net/bluetooth/l2cap.ko  
 kernel/net/bluetooth/rfcomm/rfcomm.ko  
 kernel/net/bluetooth/sco.ko  
 

 make -C /lib/modules/2.6.32-21-generic/build M=/home/john/Desktop/compat modules  
 make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'  
   Building modules, stage 2.  
   MODPOST 3 modules  
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'  
 make -C /lib/modules/2.6.32-21-generic/build M=/home/john/Desktop/compat "INSTALL_MOD_DIR=updates"  \  
 		modules_install  
 make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'  
   INSTALL /home/john/Desktop/compat/compat/compat.ko  
   INSTALL /home/john/Desktop/compat/compat/compat_firmware_class.ko  
   INSTALL /home/john/Desktop/compat/drivers/net/atl1e/atl1e.ko  
   DEPMOD  2.6.32-21-generic  
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'  
 Updating Ubuntu's initramfs for 2.6.32-21-generic under /boot/ ...  
 Will now run update-grub to ensure grub will find the new initramfs ...  
 Generating grub.cfg ...  
 Found linux image: /boot/vmlinuz-2.6.32-21-generic  
 Found initrd image: /boot/initrd.img-2.6.32-21-generic  
 Found memtest86+ image: /boot/memtest86+.bin  
 Found Windows Vista (loader) on /dev/sda1  
 Found Windows 7 (loader) on /dev/sda2  
 done  
 depmod will prefer updates/ over kernel/ -- OK!  
 

 Currently detected wireless subsystem modules:  
 

 kernel/net/mac80211/mac80211.ko  
 kernel/net/wireless/cfg80211.ko  
 kernel/net/wireless/lib80211.ko  
 kernel/drivers/net/wireless/adm8211.ko  
 kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko 
 kernel/drivers/net/wireless/at76c50x-usb.ko 
 kernel/drivers/net/wireless/ath/ath.ko  
 kernel/drivers/net/wireless/ath/ath5k/ath5k.ko 
 kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
 kernel/drivers/net/wireless/b43/b43.ko  
 kernel/drivers/net/wireless/b43legacy/b43legacy.ko 
 kernel/drivers/net/b44.ko  
 kernel/drivers/net/usb/cdc_ether.ko  
 kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
 kernel/drivers/net/wireless/ipw2x00/ipw2100.ko 
 kernel/drivers/net/wireless/ipw2x00/ipw2200.ko 
 kernel/drivers/net/wireless/iwlwifi/iwl3945.ko 
 kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 
 kernel/drivers/net/wireless/iwlwifi/iwlcore.ko 
 kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko 
 kernel/net/wireless/lib80211_crypt_ccmp.ko 
 kernel/net/wireless/lib80211_crypt_tkip.ko 
 kernel/net/wireless/lib80211_crypt_wep.ko 
 kernel/drivers/net/wireless/libertas/libertas.ko 
 kernel/drivers/net/wireless/libertas/libertas_cs.ko 
 kernel/drivers/net/wireless/libertas/libertas_sdio.ko 
 kernel/drivers/net/wireless/libertas/libertas_spi.ko 
 kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko 
 kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko 
 kernel/drivers/net/wireless/ipw2x00/libipw.ko 
 kernel/drivers/net/wireless/mac80211_hwsim.ko 
 kernel/drivers/net/wireless/mwl8k.ko  
 kernel/drivers/net/wireless/orinoco/orinoco_cs.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_pci.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_plx.ko 
 kernel/drivers/net/wireless/orinoco/orinoco.ko 
 kernel/drivers/net/wireless/p54/p54common.ko 
 kernel/drivers/net/wireless/p54/p54pci.ko 
 kernel/drivers/net/wireless/p54/p54spi.ko 
 kernel/drivers/net/wireless/p54/p54usb.ko 
 kernel/drivers/net/usb/rndis_host.ko  
 kernel/drivers/net/wireless/rndis_wlan.ko 
 kernel/drivers/net/wireless/rt2x00/rt2400pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2500pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2500usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt2800usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt61pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt73usb.ko 
 kernel/drivers/net/wireless/rtl818x/rtl8180.ko 
 kernel/drivers/net/wireless/rtl818x/rtl8187.ko 
 kernel/drivers/net/wireless/orinoco/spectrum_cs.ko 
 kernel/drivers/ssb/ssb.ko  
 kernel/drivers/net/wireless/libertas/usb8xxx.ko 
 kernel/drivers/net/usb/usbnet.ko  
 kernel/drivers/net/wireless/wl12xx/wl1251.ko 
 kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko 
 

 Currently detected ethernet subsystem modules:  
 

 kernel/drivers/net/atlx/atl1.ko  
 kernel/drivers/net/atlx/atl2.ko  
 updates/drivers/net/atl1e/atl1e.ko  
 kernel/drivers/net/atl1c/atl1c.ko  
 

 Currently detected bluetooth subsystem modules:  
 

 kernel/drivers/bluetooth/bcm203x.ko  
 kernel/drivers/bluetooth/bluecard_cs.ko 
 kernel/net/bluetooth/bluetooth.ko  
 kernel/net/bluetooth/bnep/bnep.ko  
 kernel/drivers/bluetooth/bpa10x.ko  
 kernel/drivers/bluetooth/bt3c_cs.ko  
 kernel/drivers/bluetooth/btmrvl.ko  
 kernel/drivers/bluetooth/btmrvl_sdio.ko 
 kernel/drivers/bluetooth/btsdio.ko  
 kernel/drivers/bluetooth/btusb.ko  
 kernel/drivers/bluetooth/btuart_cs.ko  
 kernel/net/bluetooth/cmtp/cmtp.ko  
 kernel/drivers/bluetooth/dtl1_cs.ko  
 kernel/net/bluetooth/hidp/hidp.ko  
 kernel/drivers/bluetooth/hci_vhci.ko  
 kernel/drivers/bluetooth/hci_uart.ko  
 kernel/net/bluetooth/l2cap.ko  
 kernel/net/bluetooth/rfcomm/rfcomm.ko  
 kernel/net/bluetooth/sco.ko  
 

 Now run:  
 

 ***sudo make unload to unload all: wireless, bluetooth and ethernet modules  ***
 ***sudo make wlunload to unload wireless modules  ***
 ***sudo make btunload to unload bluetooth modules  ***
  
 ***Run sudo modprobe driver-name to load your desired driver.  ***
 ***If unsure reboot.  ***
 

 john@john-laptop:~/Desktop/compat$ sudo modprobe atl1e

---

### Post by chili555 on 2011-07-24
Please reboot and run and post:```
ifconfig
dmesg | grep atl1
```Thanks.

---

### Post by TXbirder on 2011-07-24
john@john-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 4c:0f:6e:10:1a:6e  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4e0f:6eff:fe10:1a6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:487626 (487.6 KB)  TX bytes:78978 (78.9 KB)

john@john-laptop:~$ dmesg | grep atl1

---

### Post by chili555 on 2011-07-25
> **chili555 said:**
> Your device is driven by the module atl1[COLOR="Red"]c[/COLOR]. Please be careful, the module name is lower-case of ATL1C. Specify atl1c in driver-select and proceed as I outlined.@TXbirder-

I'm very sorry; I made a mistake. Please go back to the terminal and do:
```
cd Desktop/compat
./scripts/driver-select atl1[COLOR="Red"]c[/COLOR]
make
sudo make install
sudo modprobe atl1[COLOR="Red"]c[/COLOR]
```I apologize for my mis-step.

---

### Post by TXbirder on 2011-07-27
Stiil no Ethernet connection.  I tried the Win7 side and Ethernet works fine there.


  	 	 	 	 	 	  john@john-laptop:~$ cd Desktop/compat  
 john@john-laptop:~/Desktop/compat$ ./scripts/driver-select atl1c  
 Backup exists: Makefile.bk  
 Old build found, going to clean this up first...  
 make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'  
   CLEAN   /home/john/Desktop/compat  
   CLEAN   /home/john/Desktop/compat/.tmp_versions  
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'  
 Restoring Makefiles...  
 Restored makefile: ./drivers/net/Makefile (and removed backup)  
 Restored makefile: ./Makefile (and removed backup)  
 Backing up makefile: Makefile.bk  
 Backing up makefile: drivers/net/Makefile.bk  
 Backup exists: Makefile.bk  
 Backup exists: Makefile.bk  
 john@john-laptop:~/Desktop/compat$ make 
 ./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h  
 make -C /lib/modules/2.6.32-21-generic/build M=/home/john/Desktop/compat modules  
 make[1]: Entering directory `/usr/src/linux-headers-2.6.32-21-generic'  
   LD      /home/john/Desktop/compat/compat/built-in.o  
   CC [M]  /home/john/Desktop/compat/compat/main.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.33.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.35.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.36.o  
   CC [M]  /home/john/Desktop/compat/compat/kfifo.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.37.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.38.o  
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.39.o  
   CC [M]  /home/john/Desktop/compat/compat/kstrtox.o  
   LD [M]  /home/john/Desktop/compat/compat/compat.o  
   CC [M]  /home/john/Desktop/compat/compat/compat_firmware_class.o  
   LD      /home/john/Desktop/compat/drivers/net/atl1c/built-in.o  
   CC [M]  /home/john/Desktop/compat/drivers/net/atl1c/atl1c_main.o  
   CC [M]  /home/john/Desktop/compat/drivers/net/atl1c/atl1c_hw.o  
   CC [M]  /home/john/Desktop/compat/drivers/net/atl1c/atl1c_ethtool.o  
   LD [M]  /home/john/Desktop/compat/drivers/net/atl1c/atl1c.o  
   LD      /home/john/Desktop/compat/built-in.o  
   Building modules, stage 2.  
   MODPOST 3 modules  
   CC      /home/john/Desktop/compat/compat/compat.mod.o  
   LD [M]  /home/john/Desktop/compat/compat/compat.ko  
   CC      /home/john/Desktop/compat/compat/compat_firmware_class.mod.o  
   LD [M]  /home/john/Desktop/compat/compat/compat_firmware_class.ko  
   CC      /home/john/Desktop/compat/drivers/net/atl1c/atl1c.mod.o  
   LD [M]  /home/john/Desktop/compat/drivers/net/atl1c/atl1c.ko  
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-21-generic'  
 john@john-laptop:~/Desktop/compat$ sudo make install

---

### Post by chili555 on 2011-07-27
That's a perfect compile! Please run and post:```
sudo modprobe atl1c
ifconfig
dmesg | grep atl
```Thanks.

---

### Post by TXbirder on 2011-07-27
ohn@john-laptop:~$ sudo modprobe atl1c
[sudo] password for john: 
john@john-laptop:~$ sudo modprobe atl1c
john@john-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 4c:0f:6e:10:1a:6e  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4e0f:6eff:fe10:1a6e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:509298 (509.2 KB)  TX bytes:75734 (75.7 KB)

john@john-laptop:~$ dmesg | grep atl

---

### Post by chili555 on 2011-07-27
> john@john-laptop:~$ lspci -nn | grep 0200
01:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [[COLOR="Red"]1969[/COLOR]:[COLOR="Red"]1073[/COLOR]] (rev c0)```
$ modinfo atl1c | grep 1073
alias:          pci:v0000[COLOR="Red"]1969[/COLOR]d0000[COLOR="Red"]1073[/COLOR]sv*sd*bc*sc*i*
```The module atl1c is definitely correct for your device. We know it built correctly, because you loaded it without any warning or error: > $ sudo modprobe atl1c
[sudo] password for john:
john@john-laptop:~$However, no wired ethernet interface eth0 is created. Something else is going on. Let's check for messages against the bus number. Please run and post:```
dmesg | grep 01:00
```Also check in the computer's BIOS to be sure that the ethernet card is not disabled.

---

### Post by TXbirder on 2011-07-28
john@john-laptop:~$ dmesg | grep 01:00
[    0.947082] pci 0000:01:00.0: reg 10 64bit mmio: [0xd3400000-0xd343ffff]
[    0.947097] pci 0000:01:00.0: reg 18 io port: [0x2000-0x207f]
[    0.947197] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.947205] pci 0000:01:00.0: PME# disabled

---

### Post by TXbirder on 2011-07-28
The only possible relevant items I find in BIOS are :
under the heading Main-  Network Boot  [Enabled]
under the heading Boot Priority-   
1.  IDEO: ST9250315AS
                                                          2. Network Boot : Atheros Boot Agent
                                                          3:  USB
                                                          4.  etc.........
                                                           5. etc...........
Nothing indicates if the Atheros Boot Agent is on or off.
John

---

### Post by chili555 on 2011-07-28
TXbirder, you're killing me! I saw this: [https://bbs.archlinux.org/viewtopic.php?id=88466](https://bbs.archlinux.org/viewtopic.php?id=88466)> I was able to get eth0 to show up, and get my wired connection working.  I think the problem was, in the BIOS, I had bluetooth disabled.  Even though my ethernet was enabled, that small bluetooth change did the trick.You might check that although I think the possibility is slight.> under the heading Boot Priority-
1. IDEO: ST9250315AS
2. Network Boot : Atheros Boot Agent
3: USB
4. etc.........
5. etc...........
Nothing indicates if the Atheros Boot Agent is on or off.Can you highlight Atheros Boot Agent and press Enter? Are there other possibilities?

Let's do a full diagnostic look-see. Please reboot so that we have a clean slate and do:```
sudo modprobe atl1c > birder.txt
dmesg >> birder.txt
lsmod >> birder.txt
modinfo atl1c >> birder.txt
zip birder.zip birder.txt
```You will find the file birder.zip in your user directory. Please attach it to your reply using the paperclip tool at the top of the reply box. Thanks.

---

### Post by TXbirder on 2011-07-29
john@john-laptop:~$ sudo modprobe atl1c > birder.txt
john@john-laptop:~$ dmesg >> birder.txt
john@john-laptop:~$ lsmod >> birder.txt
john@john-laptop:~$ modinfo atl1c >> birder.txt
john@john-laptop:~$ zip birder.zip birder.txt
updating: birder.txt (deflated 74%)
john@john-laptop:~$ 

Before I can find birder.zip I must figure out where "user directory" is.
John

---

### Post by chili555 on 2011-07-29
> I must figure out where "user directory" is.It is /home/john-laptop. If you are using the latest version of Ubuntu, click Home Folder or if an earlier version, Places > Home Folder.

---

### Post by TXbirder on 2011-07-29
john@john-laptop:~$ sudo modprobe atl1c > birder.txt
john@john-laptop:~$ dmesg >> birder.txt
john@john-laptop:~$ lsmod >> birder.txt
john@john-laptop:~$ modinfo atl1c >> birder.txt
john@john-laptop:~$ zip birder.zip birder.txt

---

### Post by chili555 on 2011-07-29
You have this device:> john@john-laptop:~$ lspci -nn | grep 0200
01:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [[COLOR="Red"]1969:1073[/COLOR]] (rev c0) Your version of atl1c, it's driver, is:> filename:       /lib/modules/2.6.32-33-generic/kernel/drivers/net/atl1c/atl1c.ko
version:        1.0.0.1-NAPI
license:        GPL
description:    Atheros 1000M Ethernet Network Driver
author:         Jie Yang <jie.yang@atheros.com>
srcversion:     D9FBC84DA38EA0DA7672633
alias:          pci:v00001969d00001062sv*sd*bc*sc*i*
alias:          pci:v00001969d00001063sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.32-33-generic SMP mod_unload modversions Notice that your pci.id 1969:1073 is not listed. Also, the driver version is kernel/drivers/net. I just compiled atl1c from the compat-wireless package and here is what I got:> $ modinfo atl1c
filename:       /lib/modules/2.6.38-10-generic/[COLOR="Red"]updates/drivers/net[/COLOR]/atl1c/atl1c.ko
version:        1.0.1.0-NAPI
license:        GPL
description:    Atheros 1000M Ethernet Network Driver
author:         Jie Yang <jie.yang@atheros.com>
srcversion:     8221527AF07DC6582859663
alias:          pci:v00001969d00001083sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="Red"]1969[/COLOR]d0000[COLOR="Red"]1073[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00001969d00002062sv*sd*bc*sc*i*
alias:          pci:v00001969d00002060sv*sd*bc*sc*i*
alias:          pci:v00001969d00001062sv*sd*bc*sc*i*
alias:          pci:v00001969d00001063sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686Notice, also, that the compat-wireless driver installed in [COLOR="Red"]**updates**[/COLOR]/drivers/net.

I believe that the compile did not go perfectly. Let's try again. Please do:```
cd Desktop/compat 
./scripts/driver-select restore 
./scripts/driver-select atl1c
make
sudo make install
modinfo atl1c 
```Now does the driver list your device 1969:1073? Did it install in updates/drivers/net? If so, your ethernet should now finally be working.

---

### Post by TXbirder on 2011-07-31
p { margin-bottom: 0.08in; }  ohn@john-laptop:~$ cd Desktop/compat  
 john@john-laptop:~/Desktop/compat$ ./scripts/driver-select restore  
 Old build found, going to clean this up first... 
 make[1]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic' 
   CLEAN   /home/john/Desktop/compat 
   CLEAN   /home/john/Desktop/compat/.tmp_versions 
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic' 
 Restoring Makefiles... 
 Restored makefile: ./drivers/net/Makefile (and removed backup) 
 Restored makefile: ./Makefile (and removed backup) 
 john@john-laptop:~/Desktop/compat$ ./scripts/driver-select atl1c 
 Processing new driver-select request... 
 Backing up makefile: Makefile.bk 
 Backup exists: Makefile.bk 
 Backing up makefile: drivers/net/Makefile.bk 
 Backup exists: Makefile.bk 
 Backup exists: Makefile.bk 
 john@john-laptop:~/Desktop/compat$ make 
 ./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h 
 make -C /lib/modules/2.6.32-33-generic/build M=/home/john/Desktop/compat modules 
 make[1]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic' 
   LD      /home/john/Desktop/compat/compat/built-in.o 
   CC [M]  /home/john/Desktop/compat/compat/main.o 
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.33.o 
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.35.o 
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.36.o 
   CC [M]  /home/john/Desktop/compat/compat/kfifo.o 
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.37.o 
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.38.o 
   CC [M]  /home/john/Desktop/compat/compat/compat-2.6.39.o 
   CC [M]  /home/john/Desktop/compat/compat/kstrtox.o 
   LD [M]  /home/john/Desktop/compat/compat/compat.o 
   CC [M]  /home/john/Desktop/compat/compat/compat_firmware_class.o 
   LD      /home/john/Desktop/compat/drivers/net/atl1c/built-in.o 
   CC [M]  /home/john/Desktop/compat/drivers/net/atl1c/atl1c_main.o 
   CC [M]  /home/john/Desktop/compat/drivers/net/atl1c/atl1c_hw.o 
   CC [M]  /home/john/Desktop/compat/drivers/net/atl1c/atl1c_ethtool.o 
   LD [M]  /home/john/Desktop/compat/drivers/net/atl1c/atl1c.o 
   LD      /home/john/Desktop/compat/built-in.o 
   Building modules, stage 2. 
   MODPOST 3 modules 
   CC      /home/john/Desktop/compat/compat/compat.mod.o 
   LD [M]  /home/john/Desktop/compat/compat/compat.ko 
   CC      /home/john/Desktop/compat/compat/compat_firmware_class.mod.o 
   LD [M]  /home/john/Desktop/compat/compat/compat_firmware_class.ko 
   CC      /home/john/Desktop/compat/drivers/net/atl1c/atl1c.mod.o 
   LD [M]  /home/john/Desktop/compat/drivers/net/atl1c/atl1c.ko 
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic' 
 john@john-laptop:~/Desktop/compat$ sudo make install 
  Your old wireless subsystem modules were left intact: 
  
 Your old wireless subsystem modules were left intact: 
  
 kernel/net/mac80211/mac80211.ko 
 kernel/net/wireless/cfg80211.ko 
 kernel/net/wireless/lib80211.ko 
 kernel/drivers/net/wireless/adm8211.ko 
 kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko 
 kernel/drivers/net/wireless/at76c50x-usb.ko 
 kernel/drivers/net/wireless/ath/ath.ko 
 kernel/drivers/net/wireless/ath/ath5k/ath5k.ko 
 kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
 kernel/drivers/net/wireless/b43/b43.ko 
 kernel/drivers/net/wireless/b43legacy/b43legacy.ko 
 kernel/drivers/net/b44.ko 
 kernel/drivers/net/usb/cdc_ether.ko 
 kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
 kernel/drivers/net/wireless/ipw2x00/ipw2100.ko 
 kernel/drivers/net/wireless/ipw2x00/ipw2200.ko 
 kernel/drivers/net/wireless/iwlwifi/iwl3945.ko 
 kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 
 kernel/drivers/net/wireless/iwlwifi/iwlcore.ko 
 kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko 
 kernel/net/wireless/lib80211_crypt_ccmp.ko 
 kernel/net/wireless/lib80211_crypt_tkip.ko 
 kernel/net/wireless/lib80211_crypt_wep.ko 
 kernel/drivers/net/wireless/libertas/libertas.ko 
 kernel/drivers/net/wireless/libertas/libertas_cs.ko 
 kernel/drivers/net/wireless/libertas/libertas_sdio.ko 
 kernel/drivers/net/wireless/libertas/libertas_spi.ko 
 kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko 
 kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko 
 kernel/drivers/net/wireless/ipw2x00/libipw.ko 
 kernel/drivers/net/wireless/mac80211_hwsim.ko 
 kernel/drivers/net/wireless/mwl8k.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_cs.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_pci.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_plx.ko 
 kernel/drivers/net/wireless/orinoco/orinoco.ko 
 kernel/drivers/net/wireless/p54/p54common.ko 
 kernel/drivers/net/wireless/p54/p54pci.ko 
 kernel/drivers/net/wireless/p54/p54spi.ko 
 kernel/drivers/net/wireless/p54/p54usb.ko 
 kernel/drivers/net/usb/rndis_host.ko 
 kernel/drivers/net/wireless/rndis_wlan.ko 
 kernel/drivers/net/wireless/rt2x00/rt2400pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2500pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2500usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt2800usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt61pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt73usb.ko 
 kernel/drivers/net/wireless/rtl818x/rtl8180.ko 
 kernel/drivers/net/wireless/rtl818x/rtl8187.ko 
 kernel/drivers/net/wireless/orinoco/spectrum_cs.ko 
 kernel/drivers/ssb/ssb.ko 
 kernel/drivers/net/wireless/libertas/usb8xxx.ko 
 kernel/drivers/net/usb/usbnet.ko 
 kernel/drivers/net/wireless/wl12xx/wl1251.ko 
 kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko 
  
 Your old ethernet subsystem modules are left intact: 
  
 kernel/drivers/net/atlx/atl1.ko 
 kernel/drivers/net/atlx/atl2.ko 
 kernel/drivers/net/atl1e/atl1e.ko 
 kernel/drivers/net/atl1c/atl1c.ko 
  
 Your old bluetooth subsystem modules were left intact: 
  
 kernel/drivers/bluetooth/bcm203x.ko 
 kernel/drivers/bluetooth/bluecard_cs.ko 
 kernel/net/bluetooth/bluetooth.ko 
 kernel/net/bluetooth/bnep/bnep.ko 
 kernel/drivers/bluetooth/bpa10x.ko 
 kernel/drivers/bluetooth/bt3c_cs.ko 
 kernel/drivers/bluetooth/btmrvl.ko 
 kernel/drivers/bluetooth/btmrvl_sdio.ko 
 kernel/drivers/bluetooth/btsdio.ko 
 kernel/drivers/bluetooth/btusb.ko 
 kernel/drivers/bluetooth/btuart_cs.ko 
 kernel/net/bluetooth/cmtp/cmtp.ko 
 kernel/drivers/bluetooth/dtl1_cs.ko 
 kernel/net/bluetooth/hidp/hidp.ko 
 kernel/drivers/bluetooth/hci_vhci.ko 
 kernel/drivers/bluetooth/hci_uart.ko 
 kernel/net/bluetooth/l2cap.ko 
 kernel/net/bluetooth/rfcomm/rfcomm.ko 
 kernel/net/bluetooth/sco.ko 
  
 make -C /lib/modules/2.6.32-33-generic/build M=/home/john/Desktop/compat modules 
 make[1]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic' 
   Building modules, stage 2. 
   MODPOST 3 modules 
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic' 
 make -C /lib/modules/2.6.32-33-generic/build M=/home/john/Desktop/compat "INSTALL_MOD_DIR=updates"  \ 
         modules_install 
 make[1]: Entering directory `/usr/src/linux-headers-2.6.32-33-generic' 
   INSTALL /home/john/Desktop/compat/compat/compat.ko 
   INSTALL /home/john/Desktop/compat/compat/compat_firmware_class.ko 
   INSTALL /home/john/Desktop/compat/drivers/net/atl1c/atl1c.ko 
   DEPMOD  2.6.32-33-generic 
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-33-generic' 
 Updating Ubuntu's initramfs for 2.6.32-33-generic under /boot/ ... 
 Will now run update-grub to ensure grub will find the new initramfs ... 
 Generating grub.cfg ... 
 Found linux image: /boot/vmlinuz-2.6.32-33-generic 
 Found initrd image: /boot/initrd.img-2.6.32-33-generic 
 Found linux image: /boot/vmlinuz-2.6.32-21-generic 
 Found initrd image: /boot/initrd.img-2.6.32-21-generic 
 Found memtest86+ image: /boot/memtest86+.bin 
 Found Windows Vista (loader) on /dev/sda1 
 Found Windows 7 (loader) on /dev/sda2 
 done 
 depmod will prefer updates/ over kernel/ -- OK! 
  
 Currently detected wireless subsystem modules: 
  
 kernel/net/mac80211/mac80211.ko 
 kernel/net/wireless/cfg80211.ko 
 kernel/net/wireless/lib80211.ko 
 kernel/drivers/net/wireless/adm8211.ko 
 kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko 
 kernel/drivers/net/wireless/at76c50x-usb.ko 
 kernel/drivers/net/wireless/ath/ath.ko 
 kernel/drivers/net/wireless/ath/ath5k/ath5k.ko 
 kernel/drivers/net/wireless/ath/ath9k/ath9k.ko 
 kernel/drivers/net/wireless/b43/b43.ko 
 kernel/drivers/net/wireless/b43legacy/b43legacy.ko 
 kernel/drivers/net/b44.ko 
 kernel/drivers/net/usb/cdc_ether.ko 
 kernel/drivers/misc/eeprom/eeprom_93cx6.ko 
 kernel/drivers/net/wireless/ipw2x00/ipw2100.ko 
 kernel/drivers/net/wireless/ipw2x00/ipw2200.ko 
 kernel/drivers/net/wireless/iwlwifi/iwl3945.ko 
 kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 
 kernel/drivers/net/wireless/iwlwifi/iwlcore.ko 
 kernel/drivers/net/wireless/iwmc3200wifi/iwmc3200wifi.ko 
 kernel/net/wireless/lib80211_crypt_ccmp.ko 
 kernel/net/wireless/lib80211_crypt_tkip.ko 
 kernel/net/wireless/lib80211_crypt_wep.ko 
 kernel/drivers/net/wireless/libertas/libertas.ko 
 kernel/drivers/net/wireless/libertas/libertas_cs.ko 
 kernel/drivers/net/wireless/libertas/libertas_sdio.ko 
 kernel/drivers/net/wireless/libertas/libertas_spi.ko 
 kernel/drivers/net/wireless/libertas_tf/libertas_tf.ko 
 kernel/drivers/net/wireless/libertas_tf/libertas_tf_usb.ko 
 kernel/drivers/net/wireless/ipw2x00/libipw.ko 
 kernel/drivers/net/wireless/mac80211_hwsim.ko 
 kernel/drivers/net/wireless/mwl8k.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_cs.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_nortel.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_pci.ko 
 kernel/drivers/net/wireless/orinoco/orinoco_plx.ko 
 kernel/drivers/net/wireless/orinoco/orinoco.ko 
 kernel/drivers/net/wireless/p54/p54common.ko 
 kernel/drivers/net/wireless/p54/p54pci.ko 
 kernel/drivers/net/wireless/p54/p54spi.ko 
 kernel/drivers/net/wireless/p54/p54usb.ko 
 kernel/drivers/net/usb/rndis_host.ko 
 kernel/drivers/net/wireless/rndis_wlan.ko 
 kernel/drivers/net/wireless/rt2x00/rt2400pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2500pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2500usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt2800usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko 
 kernel/drivers/net/wireless/rt2x00/rt61pci.ko 
 kernel/drivers/net/wireless/rt2x00/rt73usb.ko 
 kernel/drivers/net/wireless/rtl818x/rtl8180.ko 
 kernel/drivers/net/wireless/rtl818x/rtl8187.ko 
 kernel/drivers/net/wireless/orinoco/spectrum_cs.ko 
 kernel/drivers/ssb/ssb.ko 
 kernel/drivers/net/wireless/libertas/usb8xxx.ko 
 kernel/drivers/net/usb/usbnet.ko 
 kernel/drivers/net/wireless/wl12xx/wl1251.ko 
 kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko 
  
 Currently detected ethernet subsystem modules: 
  
 kernel/drivers/net/atlx/atl1.ko 
 kernel/drivers/net/atlx/atl2.ko 
 kernel/drivers/net/atl1e/atl1e.ko 
 updates/drivers/net/atl1c/atl1c.ko 
  
 Currently detected bluetooth subsystem modules: 
  
 kernel/drivers/bluetooth/bcm203x.ko 
 kernel/drivers/bluetooth/bluecard_cs.ko 
 kernel/net/bluetooth/bluetooth.ko 
 kernel/net/bluetooth/bnep/bnep.ko 
 kernel/drivers/bluetooth/bpa10x.ko 
 kernel/drivers/bluetooth/bt3c_cs.ko 
 kernel/drivers/bluetooth/btmrvl.ko 
 kernel/drivers/bluetooth/btmrvl_sdio.ko 
 kernel/drivers/bluetooth/btsdio.ko 
 kernel/drivers/bluetooth/btusb.ko 
 kernel/drivers/bluetooth/btuart_cs.ko 
 kernel/net/bluetooth/cmtp/cmtp.ko 
 kernel/drivers/bluetooth/dtl1_cs.ko 
 kernel/net/bluetooth/hidp/hidp.ko 
 kernel/drivers/bluetooth/hci_vhci.ko 
 kernel/drivers/bluetooth/hci_uart.ko 
 kernel/net/bluetooth/l2cap.ko 
 kernel/net/bluetooth/rfcomm/rfcomm.ko 
 kernel/net/bluetooth/sco.ko 
  
 Now run: 
  
 sudo make unload to unload all: wireless, bluetooth and ethernet modules 
 sudo make wlunload to unload wireless modules 
 sudo make btunload to unload bluetooth modules 
  
 Run sudo modprobe driver-name to load your desired driver. 
 If unsure reboot. 
  
 john@john-laptop:~/Desktop/compat$ modinfo atl1c 
 filename:       /lib/modules/2.6.32-33-generic/updates/drivers/net/atl1c/atl1c.ko 
 version:        1.0.1.0-NAPI 
 license:        GPL 
 description:    Atheros 1000M Ethernet Network Driver 
 author:         Jie Yang <jie.yang@atheros.com> 
 srcversion:     8221527AF07DC6582859663 
 alias:   **       pci:v00001969d00001083sv*sd*bc*sc*i* **
 **alias:          pci:v0000[COLOR=#800000]1969d00001073[/COLOR]sv*sd*bc*sc*i* **
 **alias:          pci:v00001969d00002062sv*sd*bc*sc*i* **
 **alias:          pci:v00001969d00002060sv*sd*bc*sc*i* **
 **alias:          pci:v00001969d00001062sv*sd*bc*sc*i* **
 **alias:          pci:v00001969d00001063sv*sd*bc*sc*i* **
 **depends:         **
 vermagic:       2.6.32-33-generic SMP mod_unload modversions  
 john@john-laptop:~/Desktop/compat$

I REBOOTED AND NOW THE ETHERNET WORKS!  THANK YOU FOR YOUR AMAZING PATIENCE.
What, if anything, should I do about these:

 sudo make unload to unload all: wireless, bluetooth and ethernet modules 
 sudo make wlunload to unload wireless modules 
 sudo make btunload to unload bluetooth modules 
  

John

---

### Post by chili555 on 2011-07-31
> What, if anything, should I do about these:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules
Nothing. You rebooted and you're all set. I'm very glad it's working.

Please make a note for the future. Whenever a newer kernel version, or linux-image as it's known in Ubuntu, is installed by Update Manager, you'll need to build this driver for the later kernel:```
cd Desktop/compat
./scripts/driver-select restore 
./scripts/driver-select atl1c
make
sudo make install
modinfo atl1c
```Later versions of Ubuntu, 11.04, for example, have this built in.

Have fun!

---

### Post by coolfiretech on 2011-08-29
I'm hoping that someone can help me a little further with this issue.  This solution in #6 works:

> Code:
mkdir AR81Family
mv AR81Family-Linux-v1.0.1.9.tar.gz AR81Family
cd AR81Family
tar zxvf AR81Family-Linux-v1.0.1.9.tar.gz
sudo su
make install
modprobe atl1e
exit

However, sometimes after an unexpected reboot, e.g. power failure, I have to repeat this process.  It doesn't happen everytime.  Can any suggest why this happens, and how to prevent it.

Thanks for any help.

---

### Post by wildmanne39 on 2011-08-29
Hi, the only time you should have to redo it is when you have an upgrade to your kernel, and that is normal because it is compiled.
Thank you

---

### Post by coolfiretech on 2011-08-29
This has happened twice and I'm fairly sure the kernel was not upgraded.  I will check to see if that is the case for sure.  This box is acting as a file server for a small business so I will have to wait till after hours.

Thanks again.

---

### Post by chili555 on 2011-08-29
The next time it happens, you might see if this does the trick:```
sudo modprobe atl1e
```If so, all that's happening is that the module is not loading automatically. Load it with:```
sudo su
echo atl1e >> /etc/modules
exit
```

---

### Post by coolfiretech on 2011-08-29
Thanks for the suggestion. It sounds good, but if that is the case, what would cause the module not to load automatically?  Once this happens, the network adapter is "unclaimed" even after reboot until the driver is re-installed or, if you are correct, the module is manually loaded.  Since this is a headless server and I am off-site this is a major inconvience when it happens.

---

### Post by chili555 on 2011-08-29
To be very honest, I have no idea. It happens sometimes and seems more frequent with some drivers than others. atl1e is somewhat rare, so I have no idea if it's an inherent fault in atl1e. In almost all such cases, 98%, I'd estimate, /etc/modules takes care of it.

---

### Post by coolfiretech on 2011-08-30
Once again, chili555, thanks for your response.  That being the case, maybe I’d be better off putting in a more common network card with known drivers and disabling the Etheros on the motherboard.

---

### Post by chili555 on 2011-08-30
> **coolfiretech said:**
> Once again, chili555, thanks for your response.  That being the case, maybe I’d be better off putting in a more common network card with known drivers and disabling the Etheros on the motherboard.That seems like a cumbersome alternative to just adding the declaration to /etc/modules. Doesn't it work as expected?

---

### Post by coolfiretech on 2011-08-31
Oh, I misunderstood your other post.  I will try that first.  Thanks again.

---

### Post by MJ1234 on 2012-01-08
Thanks a lot chili555.
I have just bought a Packard Bell EasyNote NX69 NX69 HR 010FR. It has:
Atheros Communications Device [1969:1083] (rev c0)

Wifi was working but not ethernet.
It works also in this case with your fix with atl1c.

---

### Post by neildaemond on 2012-01-10
> **scenered said:**
> 

The driver from [http://partner.atheros.com/Download.aspx?id=125](http://partner.atheros.com/Download.aspx?id=125) won't work either (error in script on make).

Any suggestions?

I just encountered this same problem and the above link is giving me "
**Bad Request (Invalid Hostname)"**

---

### Post by chili555 on 2012-01-10
> **neildaemond said:**
> I just encountered this same problem and the above link is giving me "
**Bad Request (Invalid Hostname)"**What card do you have? The correct drivers are installed by default in Ubuntu 11.10.```
lspci -nn | grep 0200
uname -r
```

---

### Post by neildaemond on 2012-02-04
Thanks Chili, Time was of the essence so I ended up switching out the motherboard and now I can't remember what the hardware was. Next time I run into this kind of problem, I'll try Ubuntu 11.10 and up~

---

### Post by vincentrou on 2012-06-11
Thanks for the tip on compat-wireless, chili555 !

I manage to make my atheros ethernet card (1969:1091 - AR8161) works with a 3.2 linux kernel by using alx driver :
[http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx)

You have to use this tarball to compile the alx driver :
[www.orbit-lab.org/kernel/compat-wireless-2.6/2012/03/compat-wireless-2012-03-12-p.tar.bz2&#65279;](www.orbit-lab.org/kernel/compat-wireless-2.6/2012/03/compat-wireless-2012-03-12-p.tar.bz2&#65279;)

---

