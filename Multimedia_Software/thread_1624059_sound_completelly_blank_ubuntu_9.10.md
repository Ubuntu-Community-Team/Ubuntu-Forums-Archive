---
title: "sound completelly blank ubuntu 9.10"
date: 2010-11-17
forum: Multimedia Software
---

### Post by psihokiller4 on 2010-11-17
I was lead from here

[http://ubuntuforums.org/showthread.php?t=1307019&page=12](http://ubuntuforums.org/showthread.php?t=1307019&page=12)

and I still have a problem:
my sound is completelly blank
yesterday it worked now it doesn't work at all
I've installed trough synaptic:
playonlinux
eternallands

and some plugings for running radio file from internet on rhythmbox --> it own recommended me witch plugings so I don't remember any more

this are the changes when it stopped working at all


so here's some info:

```

military@military-PC-linux:~$ uname -a
Linux military-PC-linux 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux


military@military-PC-linux:~$ uname -r
2.6.31-14-generic


military@military-PC-linux:~$ speaker-test

speaker-test 1.0.20

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 192 to 2097152
Period size range from 64 to 699051
Using max buffer size 2097152
Periods = 4
was set period_size = 524288
was set buffer_size = 2097152
 0 - Front Left
Time per period = 11.321309
 0 - Front Left
Time per period = 10.997721
 0 - Front Left
Time per period = 11.320510
 0 - Front Left
Time per period = 11.317018
 0 - Front Left
Time per period = 11.317355
 0 - Front Left
Time per period = 11.001519
 0 - Front Left
^Z 
[1]+  Stopped                 speaker-test


military@military-PC-linux:~$ lspci | grep audio
02:00.1 Audio device: ATI Technologies Inc HD48x0 audio


military@military-PC-linux:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
02:00.1 Audio device: ATI Technologies Inc HD48x0 audio
military@military-PC-linux:~$ sudo lshw -class multimedia
[sudo] password for military: 
  *-multimedia            
       description: Audio device
       product: HD48x0 audio
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:17 memory:fbcfc000-fbcfffff
  *-multimedia
       description: Audio device
       product: 82801JI (ICH10 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:fbff8000-fbffbfff
military@military-PC-linux:~$ sudo apt-get update && sudo apt-get install lshw -y
Ign http://deb.playonlinux.com karmic Release.gpg
Hit http://archive.ubuntu.com karmic Release.gpg                               
Ign http://archive.ubuntu.com karmic/main Translation-en_US                    
Ign http://deb.playonlinux.com karmic/main Translation-en_US         
Hit http://ppa.launchpad.net karmic Release.gpg                      
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://archive.canonical.com karmic Release.gpg                  
Ign http://archive.canonical.com karmic/partner Translation-en_US    
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US    
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US
Ign http://archive.ubuntu.com karmic/universe Translation-en_US
Hit http://archive.ubuntu.com karmic Release                         
Hit http://ppa.launchpad.net karmic Release                          
Hit http://archive.canonical.com karmic Release                      
Get:1 http://deb.playonlinux.com karmic Release [1,723B]            
Ign http://deb.playonlinux.com karmic/main Packages                 
Hit http://archive.ubuntu.com karmic/main Packages                  
Ign http://deb.playonlinux.com karmic/main Packages                  
Hit http://ppa.launchpad.net karmic/main Packages                    
Hit http://archive.canonical.com karmic/partner Packages             
Hit http://archive.ubuntu.com karmic/restricted Packages             
Hit http://archive.ubuntu.com karmic/multiverse Packages                       
Hit http://archive.ubuntu.com karmic/restricted Sources                        
Hit http://archive.ubuntu.com karmic/main Sources                              
Hit http://deb.playonlinux.com karmic/main Packages                            
Hit http://ppa.launchpad.net karmic/main Sources                               
Hit http://archive.canonical.com karmic/partner Sources              
Hit http://archive.ubuntu.com karmic/universe Sources
Hit http://archive.ubuntu.com karmic/multiverse Sources
Hit http://archive.ubuntu.com karmic/universe Packages
Fetched 1B in 0s (1B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lshw is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


military@military-PC-linux:~$ 

```I'm kinda still newb so I'd need help

---

### Post by psihokiller4 on 2010-11-17
ok I sloved it my self now thanks to sticky guide

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

alsamixer was muted ;)

---

