---
title: "Broadcom BCM4311/Precise Pangolin/iMac5,2 driver install issues"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by purplepolkadotgirl on 2013-04-13
First, some info and outputs!

Machine: iMac5,2 (from 2006...dude. I know.) [http://www.everymac.com/systems/apple/imac/specs/imac-core-2-duo-1.83-17-inch-specs.html](http://www.everymac.com/systems/apple/imac/specs/imac-core-2-duo-1.83-17-inch-specs.html)

Wireless:
```
andrea@Frankenmac:~$ lspci -v | grep Broadcom
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
```

Interface: ```
andrea@Frankenmac:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:e3:40:fc:26  
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e3ff:fe40:fc26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26448 errors:0 dropped:0 overruns:0 frame:1
          TX packets:18324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32206133 (32.2 MB)  TX bytes:1673777 (1.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:324 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49296 (49.2 KB)  TX bytes:49296 (49.2 KB)

andrea@Frankenmac:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

Modules: ```
andrea@Frankenmac:~$ lsmod
Module                  Size  Used by
bnep                   17791  2 
rfcomm                 38104  0 
bluetooth             189585  10 bnep,rfcomm
parport_pc             32115  0 
ppdev                  12850  0 
snd_hda_codec_idt      60238  1 
snd_hda_intel          32983  3 
snd_hda_codec         116477  2 snd_hda_codec_idt,snd_hda_intel
coretemp               13362  0 
isight_firmware        12594  0 
kvm_intel             127736  0 
snd_hwdep              13277  1 snd_hda_codec
wl                   3032548  1 
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
kvm                   365556  1 kvm_intel
snd_rawmidi            25426  1 snd_seq_midi
i915                  474913  3 
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         47459  1 i915
drm                   240232  4 i915,drm_kms_helper
snd                    62675  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17394  0 
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
microcode              18396  0 
cfg80211              181041  1 wl
applesmc               18947  0 
lpc_ich                16993  0 
i2c_algo_bit           13317  1 i915
apple_bl               13426  0 
lib80211               14041  1 wl
video                  19117  1 i915
input_polldev          13649  1 applesmc
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 46054  0 
hid                    82511  2 hid_generic,usbhid
firewire_ohci          36110  0 
firewire_core          61957  1 firewire_ohci
crc_itu_t              12628  1 firewire_core
sky2                   53629  0 
```

Network configuration: ```
andrea@Frankenmac:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:16 memory:90200000-90203fff
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 22
       serial: 00:19:e3:40:fc:26
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full ip=192.168.1.115 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:90100000-90103fff ioport:1000(size=256) memory:90700000-9071ffff

```

Ubuntu:```
andrea@Frankenmac:~$ lsb_release -d
Description:    Ubuntu 12.04.2 LTS

```

Kernel: ```
andrea@Frankenmac:~$ uname -mr
3.5.0-27-generic i686

```

Restart: ```
 andrea@Frankenmac:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                  [ OK ] 

```

Found [this]("http://ubuntuforums.org/showthread.php?t=2126408") thread, which outlines the same DKMS: reinstall process hangup I went through, but I run into issues when I try to follow the advice there, specifically this:
```
andrea@Frankenmac:~$ sudo apt-get remove --purge bcmwl-kernel-source
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```
...which is of course the configure command that hangs. Thoughts?

***edit***
```
andrea@Frankenmac:~$ sudo dpkg --configure -a
[sudo] password for andrea: 
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.5.0-27-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-27-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.5.0-27-generic
Building for architecture i686
Building initial module for 3.5.0-27-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-27-generic/updates/dkms/

depmod....

DKMS: install completed.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

```

There's where it's hanging.

---

### Post by praseodym on 2013-04-13
Execute:

```
sudo dpkg --configure -a
```
and install the package "linux-firmware-nonfree". Reboot then

---

### Post by purplepolkadotgirl on 2013-04-13
```
andrea@Frankenmac:~$ sudo dpkg --configure -a
[sudo] password for andrea: 
dpkg: error: dpkg status database is locked by another process

```

At least it's a new error?

---

### Post by purplepolkadotgirl on 2013-04-13
Got it unlocked with the advice from [this]("http://ubuntuforums.org/showthread.php?t=1015279") thread, but it's still hanging on the configure.

```

andrea@Frankenmac:~$ sudo rm /var/lib/dpkg/lock
andrea@Frankenmac:~$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.5.0-27-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-27-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.5.0-27-generic
Building for architecture i686
Building initial module for 3.5.0-27-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-27-generic/updates/dkms/

depmod....

DKMS: install completed.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.


```

---

### Post by purplepolkadotgirl on 2013-04-13
Restarted, tried again:
```
andrea@Frankenmac:~$  sudo apt-get --purge remove bcmwl-kernel-source
[sudo] password for andrea: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
andrea@Frankenmac:~$ sudo rm /var/lib/dpkg/lock
andrea@Frankenmac:~$ 
andrea@Frankenmac:~$ 
andrea@Frankenmac:~$  sudo apt-get --purge remove bcmwl-kernel-source
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
andrea@Frankenmac:~$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.5.0-27-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.5.0-27-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.5.0-27-generic
Building for architecture i686
Building initial module for 3.5.0-27-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-27-generic/updates/dkms/

depmod....

DKMS: install completed.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.


```

---

### Post by purplepolkadotgirl on 2013-04-14
Just found a command that seems to have done something instead of just giving an error:
```
andrea@Frankenmac:~$ sudo dpkg -r bcmwl-kernel-source
(Reading database ... 170997 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-27-generic

```

Trying ```


sudo dpkg --configure -a
```

---

### Post by purplepolkadotgirl on 2013-04-14
New Output:

```

andrea@Frankenmac:~$ sudo dpkg --configure -a
andrea@Frankenmac:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Is sudo dpkg --configure -a not supposed to show any output? I'm really used to an error, so I don't know what's normal.

---

### Post by Hadaka on 2013-04-14
Hi, lets take a look and see if you have
any thnig left from that package in your
modules..please do..
```
lsmod | grep wl
```
thanks

---

### Post by purplepolkadotgirl on 2013-04-14
Things I've done now:```
andrea@Frankenmac:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
and
```
andrea@Frankenmac:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
andrea@Frankenmac:~$ sudo rm -rf /var/lib/apt/lists/lock
andrea@Frankenmac:~$ sudo apt-get update
Hit http://archive.ubuntu.com precise Release.gpg
Get:1 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://archive.ubuntu.com precise-backports Release.gpg                
Hit http://archive.ubuntu.com precise-security Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]
Hit http://archive.ubuntu.com precise Release                                 
Get:3 http://archive.ubuntu.com precise-updates Release [49.6 kB]
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://extras.ubuntu.com precise/main Sources        
Hit http://ppa.launchpad.net precise/main i386 Packages  
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://extras.ubuntu.com precise/main i386 Packages  
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise-backports Release  
Hit http://archive.ubuntu.com precise-security Release
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://archive.ubuntu.com precise/restricted Sources              
Hit http://archive.ubuntu.com precise/universe Sources
Hit http://archive.ubuntu.com precise/multiverse Sources
Hit http://archive.ubuntu.com precise/main i386 Packages              
Hit http://archive.ubuntu.com precise/restricted i386 Packages        
Hit http://archive.ubuntu.com precise/universe i386 Packages
Hit http://archive.ubuntu.com precise/multiverse i386 Packages        
Hit http://archive.ubuntu.com precise/main TranslationIndex           
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://archive.ubuntu.com precise/universe TranslationIndex
Get:4 http://archive.ubuntu.com precise-updates/main Sources [377 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_US                   
Ign http://ppa.launchpad.net precise/main Translation-en_US                  
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en
Get:5 http://archive.ubuntu.com precise-updates/restricted Sources [5,467 B]
Get:6 http://archive.ubuntu.com precise-updates/universe Sources [83.4 kB]
Get:7 http://archive.ubuntu.com precise-updates/multiverse Sources [6,562 B]
Get:8 http://archive.ubuntu.com precise-updates/main i386 Packages [610 kB]
Get:9 http://archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]
Get:10 http://archive.ubuntu.com precise-updates/universe i386 Packages [196 kB]
Get:11 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com precise-backports/main Sources                   
Hit http://archive.ubuntu.com precise-backports/restricted Sources             
Hit http://archive.ubuntu.com precise-backports/universe Sources               
Hit http://archive.ubuntu.com precise-backports/multiverse Sources             
Hit http://archive.ubuntu.com precise-backports/main i386 Packages             
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages         
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex          
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex      
Hit http://archive.ubuntu.com precise-security/main Sources                    
Hit http://archive.ubuntu.com precise-security/restricted Sources              
Hit http://archive.ubuntu.com precise-security/universe Sources                
Hit http://archive.ubuntu.com precise-security/multiverse Sources              
Hit http://archive.ubuntu.com precise-security/main i386 Packages              
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages        
Hit http://archive.ubuntu.com precise-security/universe i386 Packages          
Hit http://archive.ubuntu.com precise-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://archive.ubuntu.com precise-backports/main Translation-en            
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en      
Hit http://archive.ubuntu.com precise-backports/universe Translation-en        
Hit http://archive.ubuntu.com precise-security/main Translation-en             
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en         
Fetched 1,352 kB in 7s (185 kB/s)                                              
Reading package lists... Done

```

so far so good...using [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers") page to get a driver set up.

---

### Post by Hadaka on 2013-04-14
Hi, the page you refered to is not the correct
driver for your card. Please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
sudo apt-get autoremove
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall linux-firmware-nonfree
sudo modprobe b43
```
that should get your wireless working.

---

### Post by purplepolkadotgirl on 2013-04-14
Hey, sorry about that, just saw the other two posts... don't know why I didn't see them on my earlier refreshes... anyway, here's where I am:
```
andrea@Frankenmac:~$ lsmod | grep wl
wl                   3032548  1 
cfg80211              181041  1 wl
lib80211               14041  1 wl

```
Then I tried your second command and I get this:
```
andrea@Frankenmac:~$ sudo modprobe -r wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.


```

---

### Post by Hadaka on 2013-04-14
Hi,ok..lets take a look at...
```
cat /etc/modules
ls /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf | grep blacklist
```
thanks.

---

### Post by purplepolkadotgirl on 2013-04-14
```
andrea@Frankenmac:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
andrea@Frankenmac:~$ ls /etc/modprobe.d
alsa-base.conf          blacklist-firewire.conf     blacklist-rare-network.conf
blacklist               blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist-ath_pci.conf  blacklist-modem.conf        dkms.conf
blacklist.conf          blacklist-oss.conf          vmwgfx-fbdev.conf
andrea@Frankenmac:~$ cat /etc/modprobe.d/blacklist.conf | grep blacklist
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
andrea@Frankenmac:~$ 

```

---

### Post by Hadaka on 2013-04-14
ok,thanks, please do..
```
sudo rm /etc/modprobe.d/dkms.conf 
```
then COPY and paste the commands one at a time from post #10
of this thread.
thanks.

---

### Post by purplepolkadotgirl on 2013-04-14
oookay, so my wireless is working, but this doesn't seem right:

```
andrea@Frankenmac:~$ sudo rm /etc/modprobe.d/dkms.conf
[sudo] password for andrea: 
andrea@Frankenmac:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmwl-kernel-source
andrea@Frankenmac:~$ sudo modprobe -r wl
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module wl not found.
andrea@Frankenmac:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dkms
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 348 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 170931 files and directories currently installed.)
Removing dkms ...
Processing triggers for man-db ...
andrea@Frankenmac:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-generic
andrea@Frankenmac:~$ sudo apt-get install --reinstall linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-firmware-nonfree is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andrea@Frankenmac:~$ sudo modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
andrea@Frankenmac:~$ 

```

So I'll mark this solved, but I really have no idea what just happened, and I didn't think to check to see if the wireless was working before running those commands. Thank you, though! :D

---

### Post by Hadaka on 2013-04-14
Hi, to touch on a few points, here is what happened.
you loaded broadcom-kernel-source which is the incorrect
driver for your card. then. in an attempt to remove it..part
of a dpkg for it got hung up. the correct dirver for your card
is ...linux-firmware-nonfree. which uses module b43. there is
still something hung up and i dont recall how to release it.

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release. andrea@Frankenmac:~$
glad its working,hope it holds.

---

### Post by Hadaka on 2013-04-14
ok, i found the problem..you have a file called "blacklist"
in /etc/modprobe.d with no ".conf" extension. and one that
does....read below
```

andrea@Frankenmac:~$ cat /etc/modules # /etc/modules: kernel modules to load at boot time. # # This file contains the names of kernel modules that should be loaded # at boot time, one per line. Lines beginning with "#" are ignored.  lp andrea@Frankenmac:~$ ls /etc/modprobe.d alsa-base.conf          blacklist-firewire.conf     blacklist-rare-network.conf blacklist               blacklist-framebuffer.conf  blacklist-watchdog.conf blacklist-ath_pci.conf  blacklist-modem.conf        dkms.conf blacklist.conf          blacklist-oss.conf          vmwgfx-fbdev.conf 
```
to delete please do..
```
sudo rm /etc/modprobe.d/blacklist
```
that will stop that error warning.
as you can see it was telling us exactly what the problem was...but i didnt see it because "blacklisted" files live in /etc/modprobe.d
*->WARNING: All config files need .conf: /etc/modprobe.d/blacklist <-*
thanks.

---

### Post by purplepolkadotgirl on 2013-04-15
Awesome! Thank you. :D

---

