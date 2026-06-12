---
title: "Headphone Jack Suddenly Stopped Working"
date: 2015-05-13
forum: Multimedia Software
---

### Post by dawer2 on 2015-05-13
So I put my comp on suspend today and then when I resumed, my headphone jack suddenly stopped working. I don't have a mic to to test if the mic jack works. 

I went through a bunch of forums first and then somehow I lost my little speaker icon and it would fail to initialize pulse audio daemon. 

After going through the troubleshooting guides I managed to get it back and the speaker works again but still no sound from the headphones. I checked alsa mixer and tried pauvucontrol and all the sound levels seem normal enough. It definitely detects when I plug in my headphone too. 
The code that got it back to partialy-working ie speakers only was 
> sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`


It was written in one of the guides to use this command and post the results 
cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; pacmd list-sinks; aplay -l; sudo alsa force-reload;  ubuntu-support-status ; sudo lshw -C sound

Here are my results

> dawer@dawer-P750ZM:~$ cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; pacmd list-sinks; aplay -l; sudo alsa force-reload;  ubuntu-support-status ; sudo lshw -C sound
Advanced Linux Sound Architecture Driver Version k3.16.0-37-generic.
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7410000 irq 52
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7080000 irq 17
  1:        : sequencer
  2: [ 0]   : control
  3: [ 0- 0]: digital audio playback
  4: [ 0- 0]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 0]: hardware dependent
  7: [ 1]   : control
  8: [ 1- 3]: digital audio playback
  9: [ 1- 7]: digital audio playback
 10: [ 1- 0]: hardware dependent
 33:        : timer
00-00: HDA Codec 0
01-00: HDA Codec 0
00-00: ALC892 Analog : ALC892 Analog : playback 1 : capture 1
00-01: ALC892 Digital : ALC892 Digital : playback 1
01-03: HDMI 0 : HDMI 0 : playback 1
01-07: HDMI 1 : HDMI 1 : playback 1
Client info
  cur  clients : 2
  peak clients : 2
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for dawer: 
rm: cannot remove ‘/etc/asound.conf’: No such file or directory
rm: cannot remove ‘/home/dawer/.pulse’: No such file or directory
rm: cannot remove ‘/home/dawer/.asound*’: No such file or directory
rm: cannot remove ‘/home/dawer/.pulse-cookie’: No such file or directory
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [63.5 kB]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [202 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [2,564 B] 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [115 kB]    
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5,161 B] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [516 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [9,238 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [277 kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [505 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [9,256 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [278 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [12.1 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Fetched 2,007 kB in 3s (652 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
No candidate version found for libsdl1.2debian-pulseaudio
No candidate version found for libsdl1.2debian-pulseaudio
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                         
H/W path           Device     Class          Description
========================================================
                              system         P750ZM (Not Applicable)
/0                            bus            P750ZM
/0/0                          memory         64KiB BIOS
/0/14                         processor      Intel(R) Core(TM) i7-4790K CPU @ 4.
/0/14/15                      memory         256KiB L1 cache
/0/14/16                      memory         1MiB L2 cache
/0/14/17                      memory         8MiB L3 cache
/0/19                         memory         24GiB System Memory
/0/19/0                       memory         8GiB SODIMM DDR3 Synchronous 1600 M
/0/19/1                       memory         DIMM [empty]
/0/19/2                       memory         8GiB SODIMM DDR3 Synchronous 1600 M
/0/19/3                       memory         8GiB SODIMM DDR3 Synchronous 1600 M
/0/100                        bridge         4th Gen Core Processor DRAM Control
/0/100/1                      bridge         Xeon E3-1200 v3/4th Gen Core Proces
/0/100/1/0                    display        NVIDIA Corporation
/0/100/1/0.1                  multimedia     NVIDIA Corporation
/0/100/14                     bus            Intel Corporation
/0/100/16                     communication  Intel Corporation
/0/100/1a                     bus            Intel Corporation
/0/100/1b                     multimedia     Intel Corporation
/0/100/1c                     bridge         Intel Corporation
/0/100/1c.2                   bridge         Intel Corporation
/0/100/1c.2/0                 generic        Realtek Semiconductor Co., Ltd.
/0/100/1c.3                   bridge         Intel Corporation
/0/100/1c.3/0                 bridge         ASMedia Technology Inc.
/0/100/1c.3/0/3               bridge         ASMedia Technology Inc.
/0/100/1c.3/0/3/0  wlan0      network        Wireless 7265
/0/100/1c.3/0/7               bridge         ASMedia Technology Inc.
/0/100/1c.3/0/7/0  eth0       network        RTL8111/8168/8411 PCI Express Gigab
/0/100/1d                     bus            Intel Corporation
/0/100/1f                     bridge         Intel Corporation
/0/100/1f.2                   storage        Intel Corporation
/0/100/1f.3                   bus            Intel Corporation
/0/1               scsi0      storage        
/0/1/0.0.0         /dev/sda   disk           500GB Samsung SSD 850
/0/1/0.0.0/1       /dev/sda1  volume         441GiB EXT4 volume
/0/1/0.0.0/2       /dev/sda2  volume         23GiB Extended partition
/0/1/0.0.0/2/5     /dev/sda5  volume         23GiB Linux swap / Solaris partitio
/0/2               scsi1      storage        
/0/2/0.0.0         /dev/sdb   disk           1TB HGST HTS721010A9
/0/2/0.0.0/1       /dev/sdb1  volume         931GiB Windows NTFS volume
total 0
crw-rw----+  1 root audio 116, 33 May 13 21:37 timer
crw-rw----+  1 root audio 116,  6 May 13 21:37 hwC0D0
crw-rw----+  1 root audio 116,  2 May 13 21:37 controlC0
crw-rw----+  1 root audio 116,  7 May 13 21:37 controlC1
drwxr-xr-x   2 root root       80 May 13 21:37 by-path
drwxr-xr-x   3 root root      280 May 13 21:37 .
crw-rw----+  1 root audio 116, 10 May 13 21:37 hwC1D0
crw-rw----+  1 root audio 116,  9 May 13 21:56 pcmC1D7p
crw-rw----+  1 root audio 116,  8 May 13 21:56 pcmC1D3p
crw-rw----+  1 root audio 116,  5 May 13 21:56 pcmC0D1p
crw-rw----+  1 root audio 116,  3 May 13 21:56 pcmC0D0p
crw-rw----+  1 root audio 116,  4 May 13 21:56 pcmC0D0c
crw-rw----+  1 root audio 116,  1 May 13 22:09 seq
drwxr-xr-x  18 root root     4200 May 13 22:10 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
00:14.0 USB controller [0c03]: Intel Corporation Device [8086:8cb1]
00:16.0 Communication controller [0780]: Intel Corporation Device [8086:8cba]
00:1a.0 USB controller [0c03]: Intel Corporation Device [8086:8cad]
00:1b.0 Audio device [0403]: Intel Corporation Device [8086:8ca0]
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:8c90] (rev d0)
00:1c.2 PCI bridge [0604]: Intel Corporation Device [8086:8c94] (rev d0)
00:1c.3 PCI bridge [0604]: Intel Corporation Device [8086:8c96] (rev d0)
00:1d.0 USB controller [0c03]: Intel Corporation Device [8086:8ca6]
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:8cc4]
00:1f.2 SATA controller [0106]: Intel Corporation Device [8086:8c82]
00:1f.3 SMBus [0c05]: Intel Corporation Device [8086:8ca2]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:13d8] (rev a1)
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbb] (rev a1)
03:00.0 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. Device [10ec:5250] (rev 01)
04:00.0 PCI bridge [0604]: ASMedia Technology Inc. Device [1b21:1182]
05:03.0 PCI bridge [0604]: ASMedia Technology Inc. Device [1b21:1182]
05:07.0 PCI bridge [0604]: ASMedia Technology Inc. Device [1b21:1182]
06:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 48)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 8087:0a2a Intel Corp. 
Bus 003 Device 003: ID 5986:066d Acer, Inc 
Bus 003 Device 002: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 003 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
/usr/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  dawer      3943 F.... pulseaudio
                     dawer     10528 F.... pulseaudio
/dev/snd/controlC1:  dawer      3943 F.... pulseaudio
                     dawer     10528 F.... pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*
[    0.000000] AGP: No AGP bridge found
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000] found SMP MP-table at [mem 0x000fd8e0-0x000fd8ef] mapped at [ffff8800000fd8e0]
[    0.000000] No NUMA configuration found
[    0.000000] AGP: No AGP bridge found
[    0.202237] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.282610] pnp: PnP ACPI: found 8 devices
[    0.457392] audit: initializing netlink subsys (disabled)
[    0.457400] audit: type=2000 audit(1431567435.436:1): initialized
[    0.462513] libphy: Fixed MDIO Bus: probed
[    0.475139] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.475215] hub 1-0:1.0: USB hub found
[    0.491161] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.491230] hub 2-0:1.0: USB hub found
[    0.491485] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.491555] hub 3-0:1.0: USB hub found
[    0.493737] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.493803] hub 4-0:1.0: USB hub found
[    1.020808] ima: No TPM chip found, activating TPM-bypass!
[    1.021344] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.043866] sdhci-pci 0000:03:00.0: SDHCI controller found [10ec:5250] (rev 1)
[    1.043951] mmc0: no vqmmc regulator found
[    1.043952] mmc0: no vmmc regulator found
[    1.352931] usb 2-1: New USB device found, idVendor=8087, idProduct=8001
[    1.353138] hub 2-1:1.0: USB hub found
[    1.653339] usb 1-1: New USB device found, idVendor=8087, idProduct=8009
[    1.653479] hub 1-1:1.0: USB hub found
[    1.999111] usb 3-2: New USB device found, idVendor=1c7a, idProduct=0603
[    2.342645] usb 3-6: New USB device found, idVendor=5986, idProduct=066d
[    2.509769] lp: driver loaded but no devices found
[    2.569695] snd_hda_intel 0000:00:1b.0: irq 52 for MSI/MSI-X
[    2.569760] snd_hda_intel 0000:01:00.1: Disabling MSI
[    2.569765] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    2.587955] iwlwifi 0000:06:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    2.598363] audit: type=1400 audit(1431567438.066:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=540 comm="apparmor_parser"
[    2.598369] audit: type=1400 audit(1431567438.066:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=540 comm="apparmor_parser"
[    2.598676] audit: type=1400 audit(1431567438.070:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=540 comm="apparmor_parser"
[    2.606393] sound hdaudioC0D0: autoconfig: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:line
[    2.606396] sound hdaudioC0D0:    speaker_outs=1 (0x14/0x0/0x0/0x0/0x0)
[    2.606398] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    2.606399] sound hdaudioC0D0:    mono: mono_out=0x0
[    2.606400] sound hdaudioC0D0:    dig-out=0x1e/0x0
[    2.606401] sound hdaudioC0D0:    inputs:
[    2.606403] sound hdaudioC0D0:      Mic=0x18
[    2.606404] sound hdaudioC0D0:      Internal Mic=0x12
[    2.606406] sound hdaudioC0D0:      Line=0x1a
[    2.615625] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    2.615678] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    2.615726] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    2.615782] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[    2.620801] audit: type=1400 audit(1431567438.090:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=614 comm="apparmor_parser"
[    2.620805] audit: type=1400 audit(1431567438.090:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=614 comm="apparmor_parser"
[    2.620807] audit: type=1400 audit(1431567438.090:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=614 comm="apparmor_parser"
[    2.621106] audit: type=1400 audit(1431567438.090:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=614 comm="apparmor_parser"
[    2.621109] audit: type=1400 audit(1431567438.090:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=614 comm="apparmor_parser"
[    2.621265] audit: type=1400 audit(1431567438.090:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=614 comm="apparmor_parser"
[    2.627882] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    2.634034] intel_rapl: Found RAPL domain package
[    2.634036] intel_rapl: Found RAPL domain core
[    2.634037] intel_rapl: Found RAPL domain dram
[    2.638971] usb 3-7: No LPM exit latency info found, disabling LPM.
[    2.639797] usb 3-7: New USB device found, idVendor=8087, idProduct=0a2a
[    2.641693] nouveau: probe of 0000:01:00.0 failed with error -22
[    2.937209] usb 3-10: New USB device found, idVendor=046d, idProduct=c52b
[    2.958191] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:066d)
[    2.988484] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input19
[    2.988539] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input20
[    3.246857] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    3.246881] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    3.246890] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    3.246903] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    3.246911] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    3.246947] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    3.246955] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    3.246963] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    3.516116] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    3.516155] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    3.629885] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[   32.687243] audit_printk_skb: 153 callbacks suppressed
[   32.687245] audit: type=1400 audit(1431567468.119:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2505 comm="apparmor_parser"
[   32.687249] audit: type=1400 audit(1431567468.119:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2505 comm="apparmor_parser"
[   32.687431] audit: type=1400 audit(1431567468.119:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2505 comm="apparmor_parser"
sudo: /etc/init.d/sl-modem-daemon: command not found
    Release Date: 03/25/2015
    Manufacturer: Notebook                        
    Product Name: P750ZM                          
    Serial Number: Not Applicable                  
    Manufacturer: Notebook                        
    Product Name: P750ZM                          
    Serial Number: Not Applicable                  
    Manufacturer: Notebook                        
    Serial Number: None                            
    Port Type: Serial Port 16550A Compatible
    Manufacturer: Intel
    Serial Number: Not Specified
    Manufacturer: Samsung
    Serial Number: 98EE791C
    Manufacturer: [Empty]
    Serial Number: [Empty]
    Manufacturer: Samsung
    Serial Number: 98EE7942
    Manufacturer: Samsung
    Serial Number: 98EE7922
snd_seq_dummy          12762  0 
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  3 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
snd_seq_device         14497  4 snd_seq,snd_rawmidi,snd_seq_dummy,snd_seq_midi
usbhid                 52616  0 
hid                   110426  3 usbhid,hid_logitech_dj
btusb                  32497  0 
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    68972  1 snd_hda_codec_realtek
bluetooth             446409  22 bnep,btusb,rfcomm
snd_hda_intel          30469  10 
snd_hda_controller     30228  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              15047  2 snd,snd_hda_codec
Welcome to PulseAudio! Use "help" for usage information.
>>> 2 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9050
    volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_01_00.1>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "1"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xf7080000 irq 17"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.id = "0fbb"
        device.string = "hdmi:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "HDA NVidia Digital Stereo (HDMI)"
        alsa.mixer_name = "Nvidia GPU 71 HDMI/DP"
        alsa.components = "HDA:10de0071,15587500,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
    active port: <hdmi-output-0>
  * index: 1
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: 0:  20% 1:  20%
            0: -41.40 dB 1: -41.40 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 1
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC892 Analog"
        alsa.id = "ALC892 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf7410000 irq 52"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "8ca0"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC892"
        alsa.components = "HDA:10ec0892,15587500,00100302"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-speaker>
>>> **** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-controller snd-hda-codec snd-hwdep snd-pcm snd-timer (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-controller snd-hda-codec snd-hwdep snd-pcm snd-timer).
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-hda-codec-hdmi snd-hda-codec-realtek snd-hda-codec-generic snd-hda-intel snd-hda-controller snd-hda-codec snd-hwdep snd-pcm snd-timer.
Support status summary of 'dawer-P750ZM':

You have 1809 packages (89.3%) supported until May 2019 (5y)
You have 41 packages (2.0%) supported until May 2017 (3y)
You have 51 packages (2.5%) supported until February 2016 (9m)
You have 81 packages (4.0%) supported until February 2015 (9m)

You have 1 packages (0.0%) that can not/no-longer be downloaded
You have 43 packages (2.1%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details
  *-multimedia            
       description: Audio device
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:17 memory:f7080000-f7083fff
  *-multimedia
       description: Audio device
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:52 memory:f7410000-f7413fff
dawer@dawer-P750ZM:~$ 



---

### Post by dawer2 on 2015-05-13
update: I hadn't thought to check before but it seems the sound through hdmi also stopped working, as well as youtube in hdmi (was working fine all day).

---

