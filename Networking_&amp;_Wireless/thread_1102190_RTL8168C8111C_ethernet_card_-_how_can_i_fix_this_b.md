---
title: "RTL8168C/8111C ethernet card - how can i fix this bug?"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by dmurat on 2009-03-21
Hi there,
I installed Ubuntu 8.10 two months ago but found out that I cannot access the internet due to a bug. Now I installed Ubuntu 9.04 Alpha 5 but this bug still doesnt seem to be solved.
After a fresh install, I cant access the internet. This bug is already posted here:

[https://bugs.launchpad.net/ubuntu/+bug/208012](https://bugs.launchpad.net/ubuntu/+bug/208012)

But I cant even apply the solution. When I come to the step, "sudo make clean modules", I face some errors:

```
dmurat@dmurat-ubuntu:/usr/src/r8168-8.011.00$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/usr/src/r8168-8.011.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Leaving directory `/usr/src/r8168-8.011.00/src'
make -C src/ modules
make[1]: Entering directory `/usr/src/r8168-8.011.00/src'
make -C /lib/modules/2.6.28-8-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.28-8-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.28-8-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/r8168-8.011.00/src'
make: *** [modules] Error 2
dmurat@dmurat-ubuntu:/usr/src/r8168-8.011.00$ apt-get build essential
E: Invalid operation build

```

I searched the internet and the forums but none of the solutions seem to work for me =(( I opened several threads earlier, unfortunately no useful solutions were provided
PLEASE help. I ve been using Fedora for 2 months and I m bored...want to switch back to Ubuntu.

How can I fix this issue(considering that I have no internet access when Ubuntu is running)? Any help would be appreciated.

Thanks...

---

### Post by dmurat on 2009-03-21
By the way, on that computer, only Ubuntu 9.04 is installed, no other OS s. 
Here is the output of ifconfig and lpsci, thought it might help:

```
dmurat@dmurat-ubuntu:/usr/src/r8168-8.011.00$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:c8:e1:ea  
          UP BROADCAST RUNNING MULTICAST  MTU:64  Metric:1
          RX packets:2238 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:211408 (211.4 KB)  TX bytes:2551 (2.5 KB)
          Interrupt:252 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```


```
dmurat@dmurat-ubuntu:/usr/src/r8168-8.011.00$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

---

### Post by dmurat on 2009-03-21
how can I fix this driver issue? any ideas?

---

### Post by narr on 2009-03-21
Sorry, I don't have a solution, but I have the same problem. I assume that we just need to adjust the makefile, but I'm not sure how....

---

### Post by dmurat on 2009-03-22
does anyone know how can "make clean modules" problem can be fixed? is it the make file causing errors?

---

### Post by narr on 2009-03-22
I can compile it now, but WTF?!

Don't do ```
sudo make clean modules
``` but do ```
sudo -s
make clean modules
```

I have no idea about Makefiles, but for me it seems like this is a bug. It is about this line in the makefile
```
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD)/src modules

```
If you try to build it using sudo, the resulting command is ```
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/src modules

```


But this seems to be wrong. If you do it using ```sudo -s```, the resulting command is ```
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/path/to/extracted/archive/r8168-8.011.00/src modules

```
So it seems like the $(PWD) should give the current path, but in the sudo version it just gives nothing, so the result is ```SUBDIRS=/src``` instead of ```SUBDIRS=/path/to/extracted/archive/r8168-8.011.00/src```

Well, but my network still doesn't work - but maybe it helps you :)

Edit: Click [here]("http://paste.pocoo.org/show/109069/") for the console output - lines 1-17 using sudo, rest using `sudo -s`

Edit 2: Or is this because of some difference between `sudo XYZ` and running the command as root? I thought that was the same?

---

### Post by chili555 on 2009-03-22
> dmurat@dmurat-ubuntu:/usr/src/r8168-8.011.00$ apt-get build essential
E: Invalid operation buildThis should be:```
[COLOR="Red"]sudo[/COLOR] apt-get [COLOR="Red"]install[/COLOR] build[COLOR="Red"]-[/COLOR]essential
```I think you will need this before you can compile the module. It is a meta-package consisting of libc6-dev, libc-dev, g++ (better or equal to version 4.4.3.1), make and dpkg-dev. Without an internet connection, you can probably go to another computer and download them to a USB stick from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by dmurat on 2009-03-22
> **chili555 said:**
> This should be:```
[COLOR="Red"]sudo[/COLOR] apt-get [COLOR="Red"]install[/COLOR] build[COLOR="Red"]-[/COLOR]essential
```I think you will need this before you can compile the module. It is a meta-package consisting of libc6-dev, libc-dev, g++ (better or equal to version 4.4.3.1), make and dpkg-dev. Without an internet connection, you can probably go to another computer and download them to a USB stick from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

thanks chili but the dependencies of build-essential have also several dependencies. even more, those dependencies also have dependencies and grows like a tree. it seems that such a recursion will mix up everything if i try to download them all manually.

is there a way to get all the debs needed to do apt-get build-essential in one step?

for example, from another computer running ubuntu, can i do something that will put build-essential and its dependencies and their dependencies in a folder as debs? or something like that?

thanks

---

### Post by dmurat on 2009-03-22
well i kind of fixed all the dependencies but the g++-4.3_4.3.3-5ubuntu4_i386.deb

i cant install it when i type sudo dkpg -i g++-4.3_4.3.3-5ubuntu4_i386.deb
it says 

dpkg-deb: 'g++-4.3_4.3.3-5ubuntu4_i386.deb' is not a debian format archive
dpkg-deb: error processing g++-4.3_4.3.3-5ubuntu4_i386.deb (--install)

though i downloaded it from the address you gave.
how can i fixed this?

---

### Post by chili555 on 2009-03-22
It looks like  g++-4.3_4.3.3-5ubuntu4_i386.deb is for Jaunty and you are running Intrepid (8.10). Please try this: [http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-defaults/g++_4.3.1-1ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-defaults/g++_4.3.1-1ubuntu2_i386.deb)

---

### Post by dmurat on 2009-03-22
> **chili555 said:**
> It looks like  g++-4.3_4.3.3-5ubuntu4_i386.deb is for Jaunty and you are running Intrepid (8.10). Please try this: [http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-defaults/g++_4.3.1-1ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gcc-defaults/g++_4.3.1-1ubuntu2_i386.deb)

thanks chili, i tried it and at least the deb package isnt corrupt.
but i face such an error: 

breaks existing package 'libgcc1'

what can i do :)

---

### Post by chili555 on 2009-03-22
> what can i doI don't know what you did, but I cried!

I just read a post that suggests that your install CD contains *build-essential*! Please drop that CD in the drive and do:```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```Then try the code at post #1 again but instead of 'sudo' do:```
sudo su
make clean
make modules
```Continue on without sudo.

Now, please don't make me cry again!!!

---

### Post by dmurat on 2009-03-22
here is the output. 

```
Mounting CD-ROM...
Identifying.. [148b6f5b3b53d9f27452fdd1d89d45d4-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090225.1)'
Copying package lists...gpgv: Signature made Wed 25 Feb 2009 07:44:02 PM EET using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090225.1)]/ jaunty main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.
W: Skipping non-exisiting file /cdrom/dists/jaunty/main/binary-i386/Packages
W: Skipping non-exisiting file /cdrom/dists/jaunty/restricted/binary-i386/Packages
dmurat@dmurat-ubuntu:~$ sudo aptitude update
Writing extended state information... Done
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090225.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Alpha i386 (20090225.1) jaunty/restricted Translation-en_US
Err http://tr.archive.ubuntu.com jaunty Release.gpg                          
  Could not resolve 'tr.archive.ubuntu.com'
Err http://tr.archive.ubuntu.com jaunty/main Translation-en_US               
  Could not resolve 'tr.archive.ubuntu.com'
Err http://tr.archive.ubuntu.com jaunty/restricted Translation-en_US         
  Could not resolve 'tr.archive.ubuntu.com'
Err http://tr.archive.ubuntu.com jaunty/universe Translation-en_US           
  Could not resolve 'tr.archive.ubuntu.com'
Err http://tr.archive.ubuntu.com jaunty/multiverse Translation-en_US         
  Could not resolve 'tr.archive.ubuntu.com'
Err http://tr.archive.ubuntu.com jaunty-updates Release.gpg                  
  Could not resolve 'tr.archive.ubuntu.com'
Err http://tr.archive.ubuntu.com jaunty-updates/main Translation-en_US       
  Could not resolve 'tr.archive.ubuntu.com'
Err http://tr.archive.ubuntu.com jaunty-updates/restricted Translation-en_US 
  Could not resolve 'tr.archive.ubuntu.com'
Err http://tr.archive.ubuntu.com jaunty-updates/universe Translation-en_US   
  Could not resolve 'tr.archive.ubuntu.com'
Err http://tr.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US 
  Could not resolve 'tr.archive.ubuntu.com'
Err http://security.ubuntu.com jaunty-security Release.gpg                   
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/main Translation-en_US        
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/restricted Translation-en_US  
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/universe Translation-en_US    
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com jaunty-security/multiverse Translation-en_US  
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done  

```

i really appreciate your effort but nothing seems to work for me :( i guess i am CURSED!! :D
i ll just have to stick with Fedora 10

thanks a lot!

---

### Post by chili555 on 2009-03-22
> Err [http://tr.archive.ubuntu.com](http://tr.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US This just means it can't find the on-line repositories because you are not on line!

Please proceed with:```
sudo aptitude install build-essential
```

---

### Post by dmurat on 2009-03-22
Thank you very much chili! I still couldnt fix the internet connection problem but at least I was able to install build-essential and load the correct driver.
I guess there is another problem :D but whatever at least I now know that the driver is loaded =))

I cant see the thank button, guess its removed but thanks again!! =)

---

