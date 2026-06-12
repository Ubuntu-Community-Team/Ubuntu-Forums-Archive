---
title: "HT Omega Claro II sound card"
date: 2013-02-09
forum: Multimedia Software
---

### Post by Sugetsu on 2013-02-09
**Can't get my HT Omega Claro II sound card to work** 			
 			 			 		   		 		 		Hello, I am  new to the forums. I am a major noob when it comes to linux so please  bear with me. The following is a compilation of everything I have tried  to do in order to get the sound card working: [http://www.htomega.com/claro2.html](http://www.htomega.com/claro2.html)

I just installed Ubuntu 64bit 12.04 precise and I can't get my sound  card to be recognized by the system. After countless hours googling for  solutions I have arrived at a dead end.

At one point I was even able to enable HDMI audio by following the command:
sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install alsa-hda-dkmsToo bad my monitor doesn't have  speakers. This has been one frustrating experience.... No matter what I  do I cant the following to change:

lshw:
*-multimedia:0 UNCLAIMED
                description: Multimedia audio controller
                product: CMI8788 [Oxygen HD Audio]
                vendor: C-Media Electronics Inc
                physical id: 6
                bus info: pci@0000:04:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32 maxlatency=24 mingnt=2
                resources: ioport:e800(size=256)

An old post in this forums seems to indicate that someone was able to  solve the issue by adding the device module to /etc/modules: [http://ubuntuforums.org/showpost.php...68&postcount=3]("http://ubuntuforums.org/showpost.php?p=10328968&postcount=3") ... but of course I haven't the faintest idea on how to do such a thing...

Finally... I was able to upgrade my Alsa drivers from 1.0.24 to 1.0.25 by following the script instructions found here: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577) but still nothing... at least this was a significant step in my quest to solve this issue.

In an act of desperation, I turned to the following sound troubleshoot guide:
[https://help.ubuntu.com/community/So...otingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"). Based on this guide I was instructed to post the output of this diagnostics command: wget -O alsa-info.sh [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && chmod +x ./alsa-info.sh && ./alsa-info.sh. 

Here it is: [http://www.alsa-project.org/db/?f=28...46d37782f0ed81]("http://www.alsa-project.org/db/?f=2809917cb48d4422d536fd1d0946d37782f0ed81")

Can someone here please help me? All I see in the Pulse audio volume control is the Dummy output. =(

Thank you in advance!!!

---

### Post by Sugetsu on 2013-02-09
Update

I decided to upgrade my kernel to the newest stable version following this guide: 
[http://ubuntuforums.org/showthread.php?t=1872537](http://ubuntuforums.org/showthread.php?t=1872537), the system now recognises HDMI audio but my sound card remains UNCLAIMED. Again, my monitor doesn't have speakers.

Could it be that I need to add my sound card's modules to /etc/modules  like old post I posted suggested? I have no idea how to do such a thing!

Please help =(

---

### Post by Sugetsu on 2013-02-09
Bump.

---

### Post by BicyclerBoy on 2013-02-09
Your alsa-info shows 3.2 ? Is this out of date info ?
3.2 is not the latest kernel available for 12.04.

I guessing from your lspci etc that you have some new AMD CPU chipset & some fusion or on-board graphics.

The latest AMD graphics may not work (HDMI audio) with open source radeon driver. There is a supported device matrix on radeon page at freedesktop.org.

An easy way to get a later kernel is via an backports package or using xorg-edgers ppa. The later will get you kernel 3.5 with later alsa kernel module.

If actually required, updating the alsa libraries/utils from git (git build) is very straight forward.

---

### Post by Sugetsu on 2013-02-09
I updated my kernel to 3.7 as stated on my second post. With the new kernel my system recognized my video card's hdmi audio and set it as default. My sound card remains undetected.

I am running a dedicated graphics card: 7850 2gb with 3 monitors. 1 is hooked up through hdmi (the one I am using) the other two through dvi and display port but they are disabled.

Here is the updated Alsa info:
[http://www.alsa-project.org/db/?f=537c1b4dbdbb11cee09b9415b03f427068931337](http://www.alsa-project.org/db/?f=537c1b4dbdbb11cee09b9415b03f427068931337)

Edit: Following the sound troubling shooting guide steps I posted about on my first post I decided to post the full output of the following command line, in order for you guys to get a more accurate assessment of the problem:

```
sugetsu@sugetsu-desktop:~$ cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; aplay -l; sudo alsa force-reload; sudo lshw -C sound

Advanced Linux Sound Architecture Driver Version k3.7.6-030706-generic.
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfcd9c000 irq 45
 1 [U0x46d0x81b    ]: USB-Audio - USB Device 0x46d:0x81b
                      USB Device 0x46d:0x81b at usb-0000:00:12.2-3, high speed
  1:        : sequencer
  2: [ 0-11]: digital audio playback
  3: [ 0-10]: digital audio playback
  4: [ 0- 9]: digital audio playback
  5: [ 0- 8]: digital audio playback
  6: [ 0- 7]: digital audio playback
  7: [ 0- 3]: digital audio playback
  8: [ 0- 0]: hardware dependent
  9: [ 0]   : control
 10: [ 1- 0]: digital audio capture
 11: [ 1]   : control
 33:        : timer
00-00: HDA Codec 0
00-03: HDMI 0 : HDMI 0 : playback 1
00-07: HDMI 1 : HDMI 1 : playback 1
00-08: HDMI 2 : HDMI 2 : playback 1
00-09: HDMI 3 : HDMI 3 : playback 1
00-10: HDMI 4 : HDMI 4 : playback 1
00-11: HDMI 5 : HDMI 5 : playback 1
01-00: USB Audio : USB Audio : capture 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for sugetsu: 
rm: cannot remove `/etc/asound.conf': No such file or directory
rm: cannot remove `/home/sugetsu/.asound*': No such file or directory
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [5,135 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [366 kB]       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B] 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,726 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [78.6 kB]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [573 kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [63.1 kB]      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [9,565 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [180 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [9,435 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [583 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [9,503 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [181 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [10.4 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages         
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,380 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [20.9 kB]  
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [225 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [65.5 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,182 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [233 kB] 
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [67.1 kB]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,371 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Fetched 2,801 kB in 2s (1,054 kB/s)
W: Failed to fetch [http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/bean123ch/burg/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/team-iquik/alsa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
The following packages were automatically installed and are no longer required:
  libsm-dev libcaca-dev libice-dev libslang2-dev libxt-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
No candidate version found for padevchooser
No candidate version found for libsdl1.2debian-pulseaudio
No candidate version found for padevchooser
No candidate version found for libsdl1.2debian-pulseaudio
The following packages will be REMOVED:
  libcaca-dev{u} libice-dev{u} libslang2-dev{u} libsm-dev{u} libxt-dev{u} 
0 packages upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 6,741 kB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 207238 files and directories currently installed.)
Removing libcaca-dev ...
Removing libxt-dev ...
Removing libsm-dev ...
Removing libice-dev ...
Removing libslang2-dev ...
Processing triggers for man-db ...
                                         
H/W path       Device     Class       Description
=================================================
                          system      To Be Filled By O.E.M. (To Be Filled By O.
/0                        bus         A780GXE/128M
/0/0                      memory      64KiB BIOS
/0/4                      processor   AMD Phenom(tm) II X6 1090T Processor
/0/4/5                    memory      768KiB L1 cache
/0/4/6                    memory      3MiB L2 cache
/0/12                     memory      8GiB System Memory
/0/12/0                   memory      2GiB DIMM DDR2 Synchronous 400 MHz (2.5 ns
/0/12/1                   memory      2GiB DIMM DDR2 Synchronous 400 MHz (2.5 ns
/0/12/2                   memory      2GiB DIMM DDR2 Synchronous 400 MHz (2.5 ns
/0/12/3                   memory      2GiB DIMM DDR2 Synchronous 400 MHz (2.5 ns
/0/100                    bridge      RS780 Host Bridge
/0/100/2                  bridge      RS780 PCI to PCI bridge (ext gfx port 0)
/0/100/2/0                display     Advanced Micro Devices [AMD] nee ATI
/0/100/2/0.1              multimedia  Advanced Micro Devices [AMD] nee ATI
/0/100/9                  bridge      RS780/RS880 PCI to PCI bridge (PCIE port 4
/0/100/9/0                storage     ASM1062 Serial ATA Controller
/0/100/a                  bridge      RS780/RS880 PCI to PCI bridge (PCIE port 5
/0/100/a/0     eth0       network     RTL8111/8168B PCI Express Gigabit Ethernet
/0/100/11                 storage     SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mo
/0/100/12                 bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/12.1               bus         SB7x0 USB OHCI1 Controller
/0/100/12.2               bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/13                 bus         SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
/0/100/13.1               bus         SB7x0 USB OHCI1 Controller
/0/100/13.2               bus         SB7x0/SB8x0/SB9x0 USB EHCI Controller
/0/100/14                 bus         SBx00 SMBus Controller
/0/100/14.1               storage     SB7x0/SB8x0/SB9x0 IDE Controller
/0/100/14.3               bridge      SB7x0/SB8x0/SB9x0 LPC host controller
/0/100/14.4               bridge      SBx00 PCI to PCI Bridge
/0/100/14.4/6             multimedia  CMI8788 [Oxygen HD Audio]
/0/100/14.4/7             bus         VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Con
/0/100/14.4/8             multimedia  CX23880/1/2/3 PCI Video and Audio Decoder
/0/100/14.5               bus         SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
/0/101                    bridge      Family 10h Processor HyperTransport Config
/0/102                    bridge      Family 10h Processor Address Map
/0/103                    bridge      Family 10h Processor DRAM Controller
/0/104                    bridge      Family 10h Processor Miscellaneous Control
/0/105                    bridge      Family 10h Processor Link Control
/0/1           scsi0      storage     
/0/1/0.0.0     /dev/sr0   disk        DVD-RAM GSA-H55L
/0/2           scsi2      storage     
/0/2/0.0.0     /dev/sda   disk        160GB ST3160812AS
/0/2/0.0.0/1   /dev/sda1  volume      132GiB EXT4 volume
/0/2/0.0.0/2   /dev/sda2  volume      7628MiB Linux swap volume
/0/2/0.0.0/3   /dev/sda3  volume      9536MiB EXT4 volume
/0/3           scsi3      storage     
/0/3/0.0.0     /dev/sdb   disk        250GB WDC WD2500JD-00H
/0/3/0.0.0/1   /dev/sdb1  volume      232GiB Windows NTFS volume
/0/5           scsi4      storage     
/0/5/0.0.0     /dev/sdc   disk        1TB ST31000524AS
/0/5/0.0.0/1   /dev/sdc1  volume      931GiB Windows NTFS volume
/0/6           scsi6      storage     
/0/6/0.0.0     /dev/sdd   disk        256GB M4-CT256M4SSD2
/0/6/0.0.0/1   /dev/sdd1  volume      100MiB Windows NTFS volume
/0/6/0.0.0/2   /dev/sdd2  volume      238GiB Windows NTFS volume
/0/7           scsi9      storage     
/0/7/0.0.0     /dev/sde   disk        500GB WDC WD5000AAKB-0
/0/7/0.0.0/1   /dev/sde1  volume      465GiB Windows NTFS volume
total 0
crw-rw---T+  1 root audio 116, 33 Feb  9 21:41 timer
crw-rw---T+  1 root audio 116,  1 Feb  9 21:41 seq
crw-rw---T+  1 root audio 116,  4 Feb  9 21:41 pcmC0D9p
crw-rw---T+  1 root audio 116,  5 Feb  9 21:41 pcmC0D8p
crw-rw---T+  1 root audio 116,  6 Feb  9 21:41 pcmC0D7p
crw-rw---T+  1 root audio 116,  2 Feb  9 21:41 pcmC0D11p
crw-rw---T+  1 root audio 116,  3 Feb  9 21:41 pcmC0D10p
crw-rw---T+  1 root audio 116,  8 Feb  9 21:41 hwC0D0
crw-rw---T+  1 root audio 116,  9 Feb  9 21:41 controlC0
crw-rw---T+  1 root audio 116, 11 Feb  9 21:41 controlC1
drwxr-xr-x   2 root root       80 Feb  9 21:41 by-path
drwxr-xr-x   2 root root       60 Feb  9 21:41 by-id
drwxr-xr-x   4 root root      320 Feb  9 21:41 .
crw-rw---T+  1 root audio 116,  7 Feb  9 21:41 pcmC0D3p
crw-rw---T+  1 root audio 116, 10 Feb  9 21:42 pcmC1D0c
drwxr-xr-x  16 root root     4480 Feb  9 21:46 ..
cat: /dev/sndstat: No such file or directory
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
00:09.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4) [1022:9608]
00:0a.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5) [1022:9609]
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 3a)
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:6819]
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Device [1002:aab0]
02:00.0 SATA controller [0106]: ASMedia Technology Inc. ASM1062 Serial ATA Controller [1b21:0612] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
04:06.0 Multimedia audio controller [0401]: C-Media Electronics Inc CMI8788 [Oxygen HD Audio] [13f6:8788]
04:07.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev c0)
04:08.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
Bus 001 Device 003: ID 046d:081b Logitech, Inc. Webcam C310
Bus 003 Device 002: ID 03f0:1104 Hewlett-Packard DeskJet 959c
Bus 004 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 004 Device 003: ID 0461:4d0f Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
/usr/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  sugetsu    1949 F.... pulseaudio
/dev/snd/controlC1:  sugetsu    1949 F.... pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*.
[    0.000000] No AGP bridge found
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] No AGP bridge found
[    0.251759] ACPI: No dock devices found.
[    0.293116] pnp: PnP ACPI: found 13 devices
[    0.901937] audit: initializing netlink socket (disabled)
[    0.901951] type=2000 audit(1360446063.787:1): initialized
[    0.949007] libphy: Fixed MDIO Bus: probed
[    0.949626] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.949627] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    0.958397] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.958495] hub 1-0:1.0: USB hub found
[    0.958609] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.958612] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    0.970404] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.970467] hub 2-0:1.0: USB hub found
[    1.030337] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.030427] hub 3-0:1.0: USB hub found
[    1.090307] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.090390] hub 4-0:1.0: USB hub found
[    1.150281] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.150365] hub 5-0:1.0: USB hub found
[    1.210306] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.210381] hub 6-0:1.0: USB hub found
[    1.270282] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.270355] hub 7-0:1.0: USB hub found
[    1.270450] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.280451] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.438186] ata3: applying PMP SRST workaround and retrying
[    1.438209] ata5: applying PMP SRST workaround and retrying
[    1.438229] ata4: applying PMP SRST workaround and retrying
[    1.662060] ata1: applying PMP SRST workaround and retrying
[    1.731008] usb 1-3: New USB device found, idVendor=046d, idProduct=081b
[    2.287844] usb 4-2: New USB device found, idVendor=04d9, idProduct=1702
[    2.722660] usb 4-3: New USB device found, idVendor=0461, idProduct=4d0f
[    3.174471] usb 3-1: New USB device found, idVendor=03f0, idProduct=1104
[   18.572462] type=1400 audit(1360464082.798:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=452 comm="apparmor_parser"
[   18.572478] type=1400 audit(1360464082.798:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=574 comm="apparmor_parser"
[   18.572762] type=1400 audit(1360464082.798:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=452 comm="apparmor_parser"
[   18.572781] type=1400 audit(1360464082.798:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=574 comm="apparmor_parser"
[   18.572937] type=1400 audit(1360464082.798:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=452 comm="apparmor_parser"
[   18.572959] type=1400 audit(1360464082.798:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=574 comm="apparmor_parser"
[   18.930826] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
[   18.999031] lp: driver loaded but no devices found
[   19.429967] tuner 0-0060: Tuner -1 found with type(s) Radio TV.
[   19.486419] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[   19.486474] snd_hda_intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   19.499382] tda9887 0-0043: tda988[5/6/7] found
[   19.500294] tuner 0-0043: Tuner 74 found with type(s) Radio TV.
[   19.561381] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input6
[   19.561448] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input7
[   19.561488] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input8
[   19.561531] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input9
[   19.561571] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input10
[   19.561609] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card0/input11
[   19.833789] cx88[0]/0: found at 0000:04:08.0, rev: 5, irq: 23, latency: 32, mmio: 0xfd000000
[   20.467170] usbcore: registered new interface driver snd-usb-audio
[   23.058282] type=1400 audit(1360464087.282:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1072 comm="apparmor_parser"
[   23.058502] type=1400 audit(1360464087.282:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1073 comm="apparmor_parser"
[   23.058845] type=1400 audit(1360464087.282:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1076 comm="apparmor_parser"
[   23.058862] type=1400 audit(1360464087.282:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1073 comm="apparmor_parser"
sudo: /etc/init.d/sl-modem-daemon: command not found
/etc/modprobe.d/alsa-base:options snd-hda-intel model=3stack
    Release Date: 05/25/2010
        Serial services are supported (int 14h)
    Manufacturer: To Be Filled By O.E.M.
    Product Name: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    Manufacturer: ASRock
    Product Name: A780GXE/128M
    Serial Number:                       
    Manufacturer: To Be Filled By O.E.M.
    Serial Number: To Be Filled By O.E.M.
    Manufacturer: AMD              
    Serial Number: To Be Filled By O.E.M.
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Manufacturer: Manufacturer2
    Serial Number: SerNum2
    Manufacturer: Manufacturer3
    Serial Number: SerNum3
snd_seq_dummy          12799  0 
snd_hda_codec_hdmi     37116  1 
snd_hda_intel          38509  2 
snd_hda_codec         140413  2 snd_hda_codec_hdmi,snd_hda_intel
snd_usb_audio         136800  1 
snd_hwdep              13669  2 snd_hda_codec,snd_usb_audio
snd_pcm               102478  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        29478  1 snd_usb_audio
snd_seq_midi           13325  0 
snd_rawmidi            30418  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69534  17 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_hwdep,snd_pcm,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         18799  2 snd_hda_intel,snd_pcm
soundcore              12681  1 snd
usblp                  18285  0 
usbhid                 47347  0 
hid                   100624  2 hid_generic,usbhid
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-usb-audio snd-hwdep snd-pcm snd-usbmidi-lib snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-usb-audio snd-hwdep snd-pcm snd-usbmidi-lib snd-rawmidi snd-timer snd-seq-device snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-hdmi snd-hda-intel snd-hda-codec snd-usb-audio snd-hwdep snd-pcm snd-usbmidi-lib snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-allocWARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
.
  *-multimedia            
       description: Audio device
       product: Advanced Micro Devices [AMD] nee ATI
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:45 memory:fcd9c000-fcd9ffff
  *-multimedia:0 UNCLAIMED
       description: Multimedia audio controller
       product: CMI8788 [Oxygen HD Audio]
       vendor: C-Media Electronics Inc
       physical id: 6
       bus info: pci@0000:04:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=24 mingnt=2
       resources: ioport:e800(size=256)
  *-multimedia:1
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: 8
       bus info: pci@0000:04:08.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx8800 latency=32 maxlatency=55 mingnt=20
       resources: irq:23 memory:fd000000-fdffffff
```

---

### Post by BicyclerBoy on 2013-02-09
Your 2nd post did not tell me which kernel version you are actually booted/running.

I would try to install the latest alsa libraries (1.0.26) from git..
You may need utils & firmware packages.
These packages are (relatively) easy to compile & install by following the documentation provided...

If that fails just don't use the discrete soundcard, what's wrong with digital out of mobo soundcard. HDA (HDMI) is better than the soundcard if you have a HT amp (AVR).

---

### Post by Sugetsu on 2013-02-09
> **BicyclerBoy said:**
> Your 2nd post did not tell me which kernel version you are actually booted/running.

I would try to install the latest alsa libraries (1.0.26) from git..
You may need utils & firmware packages.
These packages are (relatively) easy to compile & install by following the documentation provided...

If that fails just don't use the discrete soundcard, what's wrong with digital out of mobo soundcard. HDA (HDMI) is better than the soundcard if you have a HT amp (AVR).

I apologize for not being more specific.

Where do I find the latest alsa drivers? I only managed to install the 1.0.25 because I followed a very detailed guide, I posted that guide in my first post but here is the link again: [http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)

I have no knowledge of how to recompile and install those drivers unless there are very detailed instructions like the ones posted in the guide.

I do not have any way of using HDMI for sound as my monitor does not have speakers. I just used the HDMI connection for video feed. Besides, I can't believe that Ubuntu does not support this popular and high end sound card. There has to be a way to get it working.

---

### Post by BicyclerBoy on 2013-02-10
I never found those old audio troubleshooting guides very useful..

The alsa kernel driver from ubuntu-audio-dev ppa (
ALSA daily build snapshots) achieves the same as updating the kernel to the latest (w.r.t. alsa audio)..

It is/was a great pity that ppa does not have all the alsa packages but it is the kernel component that is the most complicated to install.
I can't find any alsa user-space ppa for 12.04 or later..

I wouldn't bother with the following until you find some evidence that there is some solution. I would search the alsa-dev mailing list archives..or the 1.0.26 release notes.

Discrete soundcards are not very popular..HDMI HDA has better lossless connectivity & audiophiles are focussed on external DACs.

The release notes look very light..
[http://www.alsa-project.org/main/index.php/Changes_v1.0.25_v1.0.26](http://www.alsa-project.org/main/index.php/Changes_v1.0.25_v1.0.26)

[http://www.alsa-project.org/main/index.php/GIT_Server#Read_only_GIT_server](http://www.alsa-project.org/main/index.php/GIT_Server#Read_only_GIT_server)

```
 Read only GIT server

    git clone git://git.alsa-project.org/alsa-driver.git alsa-driver 
    git clone git://git.alsa-project.org/alsa-lib.git alsa-lib 

    git clone git://git.alsa-project.org/alsa-utils.git alsa-utils 
    git clone git://git.alsa-project.org/alsa-firmware.git alsa-firmware 

```

The first 2 packages are most important.
There are build instructions in a readme txt file in the folder created by git clone.
There are required build/toolchain programes.
There is a one-line patch to avoid the stupid (1GB) xml dependency. I'll have to post the link later..

---

### Post by Sugetsu on 2013-02-10
Here is the thing, the ht omega claro 2 isn't a new card, it actually has a few years behind it. I would like to know if this card is officially supported by this OS or if there are other users who have managed to get it working. 

I also would like to try the solution of adding the card module to /etc/modules as stated in this thread:

[http://ubuntuforums.org/showthread.php?p=10328968#post10328968](http://ubuntuforums.org/showthread.php?p=10328968#post10328968)

Can anyone teach me how to what that guy did? I think this could be a very possible solution to my problem, and hopefully Ubuntu developers will take note in the future and add proper support of this sound card.

Thanks.

---

### Post by Sugetsu on 2013-02-10
Update:

I did some further search in regards to modules and the HT omega claro and I found this post on the net: 

[http://www.murga-linux.com/puppy/viewtopic.php?t=32085&sid=545aff9046b5b97f6bdd07b7bdebd4c9](http://www.murga-linux.com/puppy/viewtopic.php?t=32085&sid=545aff9046b5b97f6bdd07b7bdebd4c9)

> The CMI8788 audio chip is supported by the "snd-oxygen" ALSA driver. If alsaconf is failing, set things up manually. 
Open /etc/modprobe.conf in geany, and add these 2 lines - 
Code:
alias snd-card-0 snd-oxygen 
alias sound-slot-0 snd-oxygen

Actually, the second line is just for ALSA-OSS compatibility, it's not essential. 
Now reboot. 
You might still need to run alsamixer (in the console) and press "m" to unmute the master channel.

The only problem is that I don't know if this post is compatible with 12.04. Could anyone confirm, fix or deny this possible solution? I would like to know how to apply it to my system. I am almost certain that this should fix the problem once and for all but I do not want to mess with the system's config unless I am sure of what I am doing.

Thanks.

---

### Post by Yellow Pasque on 2013-02-10
alsaconf isn't used much in these days of pulseaudio, and that solution looks like it wouldn't work (because you have to get the module loaded before you worry about what ALSA index each device has). Since the module is not loading, try to load it manually. What happens then?
```
sudo modprobe -v snd-oxygen
aplay -l
```

---

### Post by Sugetsu on 2013-02-10
This is the output I got:

```

sudo modprobe -v snd-oxygen
[sudo] password for sugetsu: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
insmod /lib/modules/3.7.6-030706-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko 
insmod /lib/modules/3.7.6-030706-generic/kernel/sound/pci/oxygen/snd-oxygen-lib.ko 
insmod /lib/modules/3.7.6-030706-generic/kernel/sound/pci/oxygen/snd-oxygen.ko 
sugetsu@sugetsu-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I restarted the machine and ran alsamixer but everything is still the same.

---

### Post by Yellow Pasque on 2013-02-10
Well, the PCI ID for the Claro II isn't in the latest version of the oxygen driver, so it's not going to work. [https://github.com/tiwai/sound/blob/master/sound/pci/oxygen/oxygen.c](https://github.com/tiwai/sound/blob/master/sound/pci/oxygen/oxygen.c)

Your best bet from here is to contact ALSA devs directly and ask if there are any plans for Claro II support. If you're lucky, the Claro II isn't that different from the original, and simply adding the PCI ID will get most functionality working (don't get your hopes up, though).
[https://lists.sourceforge.net/lists/listinfo/alsa-user](https://lists.sourceforge.net/lists/listinfo/alsa-user)

---

### Post by Sugetsu on 2013-02-10
I am truly shocked, how comes this card is not supported by this OS? This sound card is almost 2 years old now, and it is quite popular in computer stores such as newegg.com: [http://www.newegg.ca/Product/Product.aspx?Item=N82E16829271007](http://www.newegg.ca/Product/Product.aspx?Item=N82E16829271007)

But at least I am hoping that this thread has shed light on this sound card and its incompatibility with linux. I hoping that the forum administrators will notice this serious issue and hopefully take it up with the Alsa development team themselves. 

I honestly do not have the necessary programming skills to communicate this problem effectively with the developers. 

Isn't ubuntu 13.04 coming out very soon? Is there any chance that the admins and devs will address this problem by then?

Edit: By the way, isnt this card essentially a revamped version of the Claro? They both use the same cmedia chip and people report that the claro does work with linux,is there anything that we are overlooking? I know the PCI ID isn't included in the oxygen driver but isnt there a way to fool the system into thinking that it is running the Claro and not the Claro 2?

---

### Post by Yellow Pasque on 2013-02-11
You are the one with the hardware, so you must report the issue. If no one with the card reports the issue, it will continue to be unsupported... (and no, you don't need programming skills to send a message to the alsa user list).

---

### Post by Yellow Pasque on 2013-02-13
For anyone searching on this card, the final verdict is that the card is unsupported right now. [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg29284.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg29284.html)

@Sugetsu: thanks for taking time/effort to clear it up with ALSA devs.

---

### Post by Sugetsu on 2013-02-13
You are welcome. I hope the drivers are released some time soon.

---

### Post by plankieee on 2013-06-03
I think this might be helpful; This is also referenced in a link in regard to the HT Omega Striker Board on a Striker board - i.e., different thread - which also might provide more information. 

[http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen](http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen)

I believe I did contact the HT Omega, technical support, several years ago  and they were helpful
ago this might be worth some effort. The linux driver used to be readily available; but, it seems there is copyright/patent issue on the drivers for recording (i.e., Dolby); but, not playback. Like Xerox of old, and Medicines, with small incremental improvements (Dolby etc) , the effectiveness of the patent protection extends well beyond 20 years. .

---

### Post by wbee on 2013-06-03
If you already have this information,I apologize for being redundant:


[http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen](http://www.alsa-project.org/main/index.php/Matrix:Module-oxygen)

In the terminal,does alsamixer list the CMI8788 option?

I also have 12.04 lts,64bit, and it took me hours(it seemed longer because of the frustration) to get CA1060 to work.

Try this,worst case,you wasted fifteen minutes:

Go to your terminal and open gnome-alsamixer. If you don't have it,the terminal will tell you how to download and install it. Do so. Then,if it does not show already,open Gnome AlsaMixer, and untick ICE 958.

Good luck.:-)

---

### Post by gordintoronto on 2013-06-03
[http://askubuntu.com/questions/192460/how-can-i-enable-my-asus-xonar-dgx-cmi8788-chipset-sound-card](http://askubuntu.com/questions/192460/how-can-i-enable-my-asus-xonar-dgx-cmi8788-chipset-sound-card)

---

### Post by Yellow Pasque on 2013-06-03
The last 3 posts seem to be off-topic (discussing other sound cards that are already supported by the snd-oxygen module).  Why was this thread even bumped?
Unless you're discussing the Claro II, please make a new thread.

---

### Post by gordintoronto on 2013-06-03
> **Temüjin said:**
> The last 3 posts seem to be off-topic (discussing other sound cards that are already supported by the snd-oxygen module).  Why was this thread even bumped?
Unless you're discussing the Claro II, please make a new thread.

The Claro II is one of several identical sound cards. From the lshw in the original post:
product: CMI8788 [Oxygen HD Audio]

---

### Post by Yellow Pasque on 2013-06-03
The CMI87xx cards may have the same chip (family), but they aren't completely identical.  If the Claro II was identical to a currently supported card, adding support for it in the oxygen module would be straightforward. The Claro II is simply unsupported, even in the latest kernel: [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg29284.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg29284.html)
The askubuntu you linked to is about the Xonar DG/DGX needing a 3.5 kernel. That seems irrelevant to this Claro II thread...

Also, the links in comments 18 and 19 contain outdated information, and a user playing with those commands will probably end up without sound on a modern distro with pulseaudio.

---

### Post by Sugetsu on 2013-06-06
Its been more than 3 months and there is still no news from the alsa devs in regards to this matter. I haven't been able to enjoy Ubuntu due to this issue...

---

### Post by godvsnietzsche on 2013-07-08
I, too, have a claro II.  I dual boot with Windows and Ubuntu, but I find myself using Ubuntu less and less due to the lack of support for my sound card.  Any ideas as to why the ALSO devs seem to be neglecting this particular card, and not it's cousins?

---

