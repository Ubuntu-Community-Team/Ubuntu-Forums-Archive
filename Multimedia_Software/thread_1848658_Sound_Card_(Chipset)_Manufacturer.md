---
title: "Sound Card (Chipset) Manufacturer"
date: 2011-09-22
forum: Multimedia Software
---

### Post by DaimyoKirby on 2011-09-22
So I was reading the [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449"), but I didn't really get how I was supposed to find my sound card (chipset) manufacturer.

Can anyone explain/give me a step-by-step guide on how to find it?

---

### Post by BicyclerBoy on 2011-09-23
You could post the results from
aplay -l
aplay -L
uname -r
Ubuntu distro..

And if it is a laptop please make that model very well known.
Laptops cause the most h/w problems. Every model has different jack/speaker/mic wiring.

---

### Post by DaimyoKirby on 2011-09-23
Ok, here goes;

```
alden@alden-laptop:~$ aplay -l
aplay: device_list:240: no soundcards found...
```

```
alden@alden-laptop:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
```

```
alden@alden-laptop:~$ uname -r
2.6.38-11-generic
```

I'm running Ubuntu 11.04 on an HP Pavilion dv6000.

The reason I'm trying to find this is to follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=205449") to solve [this problem]("http://ubuntuforums.org/showthread.php?t=1845700").

---

### Post by BicyclerBoy on 2011-09-23
Problem is worse...

lspci | grep Audio

Have you been trying to upgrade alsa from a script or some instructions ?

The best advice is do not touch alsa.
Wait for instructions from "Lidex" (You killed Kenny you bar..ds)

---

### Post by .... on 2011-09-23
Does aplay also show no soundcards when your sound is working?

---

### Post by DaimyoKirby on 2011-09-23
BicyclerBoy -
using that command outputted something the first time I did it, but I restarted my computer to see if I could get the sound working to test ....'s question, and didn't bother writing it down; and now it doesn't output anything.
I'm not sure, but I think this might be what you're talking about: I used the appropriate codes on [this help document]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure").

.... -
I can't seem to get the sound working, so I won't know until it starts working again.


I have a theory, and I want some input -
Just today my computer, upon booting, my laptop automatically ran some disk checks, and when the login screen appeared, the sound was working (it stopped a little while later when I was watching a youtube video).
I want to test if that fixes it, so do either of you (or anyone else who reads this post) happen to know a way to have the computer check its disks?

---

### Post by BicyclerBoy on 2011-09-24
Your PC checked its disks..

To check any disk/partition it must be unmounted (just like windows), when this is the system disk you must boot from some other image (like Live CD/DVD)

It is not going to fix the sound card error..

That ubuntu alsa upgrade looks credible..
But it looks to me that you **must re-run** the script after every kernel update.
This would explain some of your problems (if audio was working after you first ran the script).
I am fairly sure you can re-run the script multiple times.

Does it complete without errors ?

I would guess there are interesting error messages in kernel.log etc..

run from terminal
dmesg | grep HDA

---

### Post by .... on 2011-09-24
Please run alsa-info.sh script so we know what we're dealing with. See instructions here: [http://ubuntuforums.org/showpost.php?p=11280000&postcount=112](http://ubuntuforums.org/showpost.php?p=11280000&postcount=112)

---

### Post by DaimyoKirby on 2011-09-24
BicyclerBoy -
Yeah, it appears to have completed without any errors:
```
alden@alden-laptop:~$ sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r) libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop  linux-image-`uname -r` linux-alsa-driver-modules-$(uname -r)  libasound2; killall pulseaudio; rm -r ~/.pulse*
[sudo] password for alden: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 4E9F485BF943EF0EABA10B5BD225991A72B194E5
gpg: requesting key 72B194E5 from hkp server keyserver.ubuntu.com
gpg: key 72B194E5: "Launchpad Ubuntu Audio Dev team PPA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Ign http://ubuntu.osuosl.org natty InRelease
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://ubuntu.osuosl.org natty-updates InRelease                           
Ign http://ubuntu.osuosl.org natty-security InRelease                          
Ign http://dl.google.com stable InRelease                                      
Hit http://extras.ubuntu.com natty Release.gpg                                 
Ign http://archive.canonical.com maverick InRelease                            
Hit http://ubuntu.osuosl.org natty Release.gpg                                 
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://ubuntu.osuosl.org natty-updates Release.gpg                         
Get:2 http://dl.google.com stable Release [1,347 B]                            
Hit http://ubuntu.osuosl.org natty-security Release.gpg                        
Hit http://extras.ubuntu.com natty Release                                     
Hit http://archive.canonical.com maverick Release.gpg                          
Hit http://ubuntu.osuosl.org natty Release                                     
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ubuntu.osuosl.org natty-updates Release                             
Get:3 http://dl.google.com stable/main i386 Packages [1,178 B]                 
Hit http://ubuntu.osuosl.org natty-security Release                            
Hit http://archive.canonical.com maverick Release                              
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://ubuntu.osuosl.org natty/main Sources                                
Hit http://ubuntu.osuosl.org natty/restricted Sources                          
Hit http://ubuntu.osuosl.org natty/universe Sources                            
Hit http://ubuntu.osuosl.org natty/multiverse Sources                          
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ubuntu.osuosl.org natty/main i386 Packages                          
Hit http://ubuntu.osuosl.org natty/restricted i386 Packages                    
Hit http://ubuntu.osuosl.org natty/universe i386 Packages                      
Hit http://ubuntu.osuosl.org natty/multiverse i386 Packages                    
Ign http://ubuntu.osuosl.org natty/main TranslationIndex                       
Hit http://archive.canonical.com maverick/partner Sources                      
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty Release.gpg                                 
Ign http://ubuntu.osuosl.org natty/multiverse TranslationIndex                 
Ign http://ubuntu.osuosl.org natty/restricted TranslationIndex                 
Ign http://ubuntu.osuosl.org natty/universe TranslationIndex                   
Hit http://ubuntu.osuosl.org natty-updates/main Sources                        
Hit http://ubuntu.osuosl.org natty-updates/restricted Sources                  
Hit http://ubuntu.osuosl.org natty-updates/universe Sources                    
Hit http://ubuntu.osuosl.org natty-updates/multiverse Sources                  
Hit http://ubuntu.osuosl.org natty-updates/main i386 Packages                  
Hit http://ubuntu.osuosl.org natty-updates/restricted i386 Packages            
Hit http://ubuntu.osuosl.org natty-updates/universe i386 Packages              
Hit http://archive.canonical.com maverick/partner i386 Packages                
Ign http://archive.canonical.com maverick/partner TranslationIndex             
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ubuntu.osuosl.org natty-updates/multiverse i386 Packages            
Ign http://ubuntu.osuosl.org natty-updates/main TranslationIndex               
Ign http://ubuntu.osuosl.org natty-updates/multiverse TranslationIndex         
Ign http://ubuntu.osuosl.org natty-updates/restricted TranslationIndex         
Ign http://ubuntu.osuosl.org natty-updates/universe TranslationIndex           
Hit http://ubuntu.osuosl.org natty-security/main Sources                       
Hit http://ubuntu.osuosl.org natty-security/restricted Sources                 
Hit http://ubuntu.osuosl.org natty-security/universe Sources                   
Hit http://ubuntu.osuosl.org natty-security/multiverse Sources                 
Hit http://ubuntu.osuosl.org natty-security/main i386 Packages                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ubuntu.osuosl.org natty-security/restricted i386 Packages           
Hit http://ubuntu.osuosl.org natty-security/universe i386 Packages             
Hit http://ubuntu.osuosl.org natty-security/multiverse i386 Packages           
Ign http://ubuntu.osuosl.org natty-security/main TranslationIndex              
Ign http://ubuntu.osuosl.org natty-security/multiverse TranslationIndex        
Ign http://ubuntu.osuosl.org natty-security/restricted TranslationIndex        
Ign http://ubuntu.osuosl.org natty-security/universe TranslationIndex          
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.canonical.com maverick/partner Translation-en_US            
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://archive.canonical.com maverick/partner Translation-en               
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en       
Ign http://ppa.launchpad.net natty/main Translation-en_US    
Ign http://ppa.launchpad.net natty/main Translation-en       
Ign http://ppa.launchpad.net natty/main Translation-en_US    
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en       
Ign http://ppa.launchpad.net natty/main Translation-en_US    
Ign http://ppa.launchpad.net natty/main Translation-en       
Ign http://ubuntu.osuosl.org natty/main Translation-en_US    
Ign http://ubuntu.osuosl.org natty/main Translation-en       
Ign http://ubuntu.osuosl.org natty/multiverse Translation-en_US
Ign http://ubuntu.osuosl.org natty/multiverse Translation-en
Ign http://ubuntu.osuosl.org natty/restricted Translation-en_US
Ign http://ubuntu.osuosl.org natty/restricted Translation-en 
Ign http://ubuntu.osuosl.org natty/universe Translation-en_US
Ign http://ubuntu.osuosl.org natty/universe Translation-en   
Ign http://ubuntu.osuosl.org natty-updates/main Translation-en_US
Ign http://ubuntu.osuosl.org natty-updates/main Translation-en
Ign http://ubuntu.osuosl.org natty-updates/multiverse Translation-en_US
Ign http://ubuntu.osuosl.org natty-updates/multiverse Translation-en
Ign http://ubuntu.osuosl.org natty-updates/restricted Translation-en_US
Ign http://ubuntu.osuosl.org natty-updates/restricted Translation-en
Ign http://ubuntu.osuosl.org natty-updates/universe Translation-en_US
Ign http://ubuntu.osuosl.org natty-updates/universe Translation-en
Ign http://ubuntu.osuosl.org natty-security/main Translation-en_US
Ign http://ubuntu.osuosl.org natty-security/main Translation-en
Ign http://ubuntu.osuosl.org natty-security/multiverse Translation-en_US
Ign http://ubuntu.osuosl.org natty-security/multiverse Translation-en
Ign http://ubuntu.osuosl.org natty-security/restricted Translation-en_US
Ign http://ubuntu.osuosl.org natty-security/restricted Translation-en
Ign http://ubuntu.osuosl.org natty-security/universe Translation-en_US
Ign http://ubuntu.osuosl.org natty-security/universe Translation-en
Ign http://deb.playonlinux.com natty InRelease
Hit http://deb.playonlinux.com natty Release.gpg
Hit http://deb.playonlinux.com natty Release
Hit http://deb.playonlinux.com natty/main i386 Packages
Ign http://deb.playonlinux.com natty/main TranslationIndex
Ign http://deb.playonlinux.com natty/main Translation-en_US                    
Ign http://deb.playonlinux.com natty/main Translation-en                       
Fetched 2,723 B in 7s (349 B/s)                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-base is already the newest version.
alsa-utils is already the newest version.
libasound2 is already the newest version.
linux-sound-base is already the newest version.
ubuntu-desktop is already the newest version.
gdm is already the newest version.
linux-image-2.6.38-11-generic is already the newest version.
linux-alsa-driver-modules-2.6.38-11-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libgfortran3 xulrunner-2.0 python-numeric python-utidylib python-gtkmozembed
  libtidy-0.99-0 python-numpy python-tz xulrunner-2.0-mozjs python-feedparser
  python-rsvg python-dateutil libblas3gf liblapack3gf python-evolution
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgfortran3 xulrunner-2.0 python-numeric python-utidylib python-gtkmozembed
  libtidy-0.99-0 python-numpy python-tz xulrunner-2.0-mozjs python-feedparser
  python-rsvg python-dateutil libblas3gf liblapack3gf python-evolution
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 8 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/40.2 MB of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 190972 files and directories currently installed.)
Preparing to replace linux-alsa-driver-modules-2.6.38-11-generic 2.6.38-11.201108241605 (using .../linux-alsa-driver-modules-2.6.38-11-generic_2.6.38-11.201108241605_i386.deb) ...
Unpacking replacement linux-alsa-driver-modules-2.6.38-11-generic ...
Preparing to replace linux-image-2.6.38-11-generic 2.6.38-11.48 (using .../linux-image-2.6.38-11-generic_2.6.38-11.48_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.38-11-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
Preparing to replace alsa-base 1.0.24+dfsg-0ubuntu1 (using .../alsa-base_1.0.24+dfsg-0ubuntu1_all.deb) ...
Unpacking replacement alsa-base ...
Preparing to replace alsa-utils 1.0.24.2-0ubuntu6 (using .../alsa-utils_1.0.24.2-0ubuntu6_i386.deb) ...
Unpacking replacement alsa-utils ...
Preparing to replace gdm 2.32.1-0ubuntu3.2 (using .../gdm_2.32.1-0ubuntu3.2_i386.deb) ...
Unpacking replacement gdm ...
Preparing to replace libasound2 1.0.24.1-0ubuntu5 (using .../libasound2_1.0.24.1-0ubuntu5_i386.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace linux-sound-base 1.0.24+dfsg-0ubuntu1 (using .../linux-sound-base_1.0.24+dfsg-0ubuntu1_all.deb) ...
Unpacking replacement linux-sound-base ...
Preparing to replace ubuntu-desktop 1.220 (using .../ubuntu-desktop_1.220_i386.deb) ...
Unpacking replacement ubuntu-desktop ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for python-support ...
Setting up linux-image-2.6.38-11-generic (2.6.38-11.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.38-11.48 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.38-11.48 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
 * dkms: running auto installation service for kernel 2.6.38-11-generic         
 *       nvidia-current (270.41.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up gdm (2.32.1-0ubuntu3.2) ...
Setting up libasound2 (1.0.24.1-0ubuntu5) ...
Setting up linux-sound-base (1.0.24+dfsg-0ubuntu1) ...
Setting up linux-alsa-driver-modules-2.6.38-11-generic (2.6.38-11.201108241605) ...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
Setting up alsa-base (1.0.24+dfsg-0ubuntu1) ...
Setting up alsa-utils (1.0.24.2-0ubuntu6) ...
Setting up ubuntu-desktop (1.220) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

This is what *dmesg | grep HDA* outputted:```
alden@alden-laptop:~$ dmesg | grep HDA
alden@alden-laptop:~$ 
```
Nothing...So did I do something wrong, or what?

.... -
The information is located [here]("http://www.alsa-project.org/db/?f=9528147923483eacf425b0993616b037329c3ad7").
Output:```
alden@alden-laptop:~$ wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
--2011-09-24 08:24:08--  http://www.alsa-project.org/alsa-info.sh
Resolving www.alsa-project.org... 77.48.224.243
Connecting to www.alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-09-24 08:24:11--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to www.alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,247      57.9K/s   in 0.5s    

2011-09-24 08:24:14 (57.9 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1519: No soundcards found...
cat: /tmp/alsa-info.0x7pvhELCK/alsactl.tmp: No such file or directory
Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=9528147923483eacf425b0993616b037329c3ad7

Please inform the person helping you.
```

---

### Post by BicyclerBoy on 2011-09-24
HP are notoriously bad with model names/numbers.

So is this HP DV6000 a sandybridge i3 i5 i7 CPU/GPU ?
Or a AMD fusion A8 APU ?

You seem to be running the nvidia driver 270?

Maybe you better post:
lspci

If it is sandybridge then you must use a later kernel. At least 2.6.39.
To get sandybridge graphics working well need kernel 3.0.xx.

---

### Post by DaimyoKirby on 2011-09-24
.... -
For some reason my sound started working again, and when I ran aplay -l, it returned this:
```
alden@alden-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

BicyclerBoy -
```
alden@alden-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

Also, just so you both know, in [my original post]("http://ubuntuforums.org/showthread.php?t=1845700") about my problem, a forum staff member had another idea, so I'm going to also be checking his suggestions when my sound stops working again; I will, of course, still be checking into your suggestions still as well - the more leads I can follow, the likelier I will be to solve the problem.

Once again, thank you to both of you for the effort you're putting into helping me solve my problem.

---

### Post by BicyclerBoy on 2011-09-25
You should run the alsa info script while the going's good.

The nVidia MCP67 - MCP7A chipset audio seems to have had most than their fair share of problems.

If the audio stops again you can try to modprobe the drivers.

modprobe snd_hda_codec_nvhdmi  (might now be called snd_hda_nvidia)
modprobe snd_hda_intel

Try the 2nd line only & see if audio starts working.

Chgeck for errors in 
dmesg | tail

---

### Post by .... on 2011-09-25
I'm wondering if this has something to do with MSI (message signaled interrupts). They should be disabled on nvidia chipsets.

---

### Post by DaimyoKirby on 2011-09-25
BicyclerBoy -
Here is the output when I ran the 2nd line (modprobe_snd_hda_intel), and then the error check afterwards.
```
alden@alden-laptop:~$ modprobe snd_hda_intel
alden@alden-laptop:~$ dmesg | tail
[ 1628.427022] ALSA hda_codec.c:1471 hda_codec_cleanup_stream: NID=0x10
[ 1635.335540] ALSA hda_intel.c:1755 azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1635.335554] ALSA hda_codec.c:1408 hda_codec_setup_stream: NID=0x12, stream=0x5, channel=0, format=0x4011
[ 1635.335559] ALSA hda_codec.c:1408 hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[ 1635.335596] ALSA hda_intel.c:1755 azx_pcm_prepare: bufsize=0x10000, format=0x4011
[ 1635.335603] ALSA hda_codec.c:1408 hda_codec_setup_stream: NID=0x12, stream=0x5, channel=0, format=0x4011
[ 1635.335607] ALSA hda_codec.c:1408 hda_codec_setup_stream: NID=0x10, stream=0x5, channel=0, format=0x4011
[ 1643.041505] ALSA hda_codec.c:1471 hda_codec_cleanup_stream: NID=0x10
[ 1643.041520] ALSA hda_codec.c:1471 hda_codec_cleanup_stream: NID=0x12
[ 1643.041577] ALSA hda_codec.c:1471 hda_codec_cleanup_stream: NID=0x10
```

.... -
How do I check for that?

---

### Post by BicyclerBoy on 2011-09-26
Use of msi can be suppressed in the grub boot command options.
The keyword msi can be used with modprobe options..

If the nVidia chipset did not support msi I would have thought there would be more wrong than just audio codec.
I can't find any evidence that nVidia chipset does or does not need the msi=0 option..
But the alsa source code contains this:
```

+	/* NVidia chipsets seem to cause troubles with MSI */
+	if (chip->driver_type == AZX_DRIVER_NVIDIA) {
+		printk(KERN_INFO "hda_intel: Disable MSI for Nvidia chipset\n");
+		chip->msi = 0;

-------
 	SND_PCI_QUIRK_MASK(PCI_VENDOR_ID_HP, 0xfff0, 0x3620,
 		      "HP dv6", STAC_HP_DV5),
+	SND_PCI_QUIRK(PCI_VENDOR_ID_HP, 0x3061,
+		      "HP dv6", STAC_HP_DV5), /* HP dv6-1110ax */



```

Sorry, I don't know what to make of those errors..

This link is shows the same errors & the same h/w.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/525191](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/525191)
It had no resolution.

---

### Post by DaimyoKirby on 2011-09-26
So...you're saying my sound is dead/won't ever work properly again?

---

### Post by lidex on 2011-09-27
As stated previously, it would be helpful to get alsa-info when sound is working. Do you dual-boot? Is sound absent after suspend/hibernate? Try a suspend/resume cycle when it's down.

Your sound module is not loading (snd-hda-intel). Try it this way:
```
sudo modprobe snd-hda-intel
```
Try reloading alsa:
```
sudo alsa force-reload
```

---

