---
title: "DVD Play Back Totum/Fiesty"
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by SillyRabbit74 on 2007-10-13
Hi There,

Pretty new to the Ubuntu world, so, I thought I would ask for a little help with this issue I am having trying to install the necessary plug-ins for DVD play back in Totum for Fiesty.

Here are the commands I have run and the error I receive...It looks like "E: Package libdvdcss2 has no installation candidate" is the problem? Well, that and my present lack of skills with trouble shooting these issue :-k . Any insights would be greatly appreciated. :

dannyboy@dannyboy-laptop:~$ gksudo aptitude install totem-xine libdvdcss2 vlc mplayer w32codecs gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse banshee libxine-extracodecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No candidate version found for libdvdcss2
No candidate version found for w32codecs
The following NEW packages will be automatically installed:
  boo jackd libartsc0 libavcodec0d libavformat0d libcdaudio1 libdc1394-13 
  libdvbpsi4 libdvdnav4 libfaac0 libfaad2-0 libfreebob0 libggi-target-x 
  libggi2 libgii1 libgii1-target-x libgsm1 libipod-cil libipoddevice0 
  libipodui-cil libiso9660-4 libjack0.100.0-0 liblame0 libmjpegtools0c2a 
  libmms0 libmono-cairo2.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil libmono1.0-cil 
  libmp4v2-0 libmpcdec3 libnjb5 libpostproc0d libquicktime0 libsdl-image1.2 
  libsgutils1 libsoundtouch1c2 libswfdec0.3 libtar libvcdinfo0 libvlc0 
  libwavpack1 libwxbase2.6-0 libwxgtk2.6-0 libxine1-ffmpeg libxosd2 
  libxvidcore4 mplayer-skins sg3-utils videolan-doc vlc-nox 
The following packages have been kept back:
  hpijs hplip hplip-data 
The following NEW packages will be installed:
  banshee boo gstreamer0.10-plugins-bad 
  gstreamer0.10-plugins-bad-multiverse 
  gstreamer0.10-plugins-ugly-multiverse jackd libartsc0 libavcodec0d 
  libavformat0d libcdaudio1 libdc1394-13 libdvbpsi4 libdvdnav4 libfaac0 
  libfaad2-0 libfreebob0 libggi-target-x libggi2 libgii1 libgii1-target-x 
  libgsm1 libipod-cil libipoddevice0 libipodui-cil libiso9660-4 
  libjack0.100.0-0 liblame0 libmjpegtools0c2a libmms0 libmono-cairo2.0-cil 
  libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil libmono1.0-cil 
  libmp4v2-0 libmpcdec3 libnjb5 libpostproc0d libquicktime0 libsdl-image1.2 
  libsgutils1 libsoundtouch1c2 libswfdec0.3 libtar libvcdinfo0 libvlc0 
  libwavpack1 libwxbase2.6-0 libwxgtk2.6-0 libxine-extracodecs 
  libxine1-ffmpeg libxosd2 libxvidcore4 mplayer mplayer-skins sg3-utils 
  videolan-doc vlc vlc-nox 
0 packages upgraded, 61 newly installed, 0 to remove and 3 not upgraded.
Need to get 35.6MB of archives. After unpacking 87.8MB will be used.
Do you want to continue? [Y/n/?] Abort.
dannyboy@dannyboy-laptop:~$ Y
bash: Y: command not found
dannyboy@dannyboy-laptop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
OK

dannyboy@dannyboy-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty Release.gpg                            
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US       
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US   
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/free Translation-en_US       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/non-free Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/free Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/non-free Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/free Packages
  404 Not Found [IP: 193.34.16.167 80]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/non-free Packages
  404 Not Found [IP: 193.34.16.167 80]
Fetched 3B in 1s (2B/s)  
Failed to fetch [http://packages.medibuntu.org/dists/gusty/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gusty/free/binary-i386/Packages.gz)  404 Not Found [IP: 193.34.16.167 80]
Failed to fetch [http://packages.medibuntu.org/dists/gusty/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gusty/non-free/binary-i386/Packages.gz)  404 Not Found [IP: 193.34.16.167 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

dannyboy@dannyboy-laptop:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

---

### Post by linuxwizard on 2007-10-13
Try like this
sudo apt-get install w32codecs

sudo apt-get install libdvdcss2

Or go this way

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb


wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1+build1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1+build1_i386.deb)
sudo dpkg -i w32codecs_20061022-0medibuntu1+build1_i386.deb

---

### Post by SillyRabbit74 on 2007-10-13
Thanks, i will give try!

---

### Post by SillyRabbit74 on 2007-10-13
Wizard, 

I ran the first 2 commands in my terminal session and received the same error as before... "E: Package w32codecs has no installation candidate" and this is the output i received:

dannyboy@dannyboy-laptop:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


dannyboy@dannyboy-laptop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate


dannyboy@dannyboy-laptop:~$ wget -c [http://packages.medibuntu.org/pool/n...uild1_i386.deb](http://packages.medibuntu.org/pool/n...uild1_i386.deb)
--13:27:06--  [http://packages.medibuntu.org/pool/n...uild1_i386.deb](http://packages.medibuntu.org/pool/n...uild1_i386.deb)
           => `n...uild1_i386.deb'
Resolving packages.medibuntu.org... 193.34.16.167, 88.191.13.100, 88.198.37.77, ...
Connecting to packages.medibuntu.org|193.34.16.167|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:27:06 ERROR 404: Not Found.

---

### Post by carlinuxlearner on 2007-10-13
This site is make the link smaller (see how in the link there is "..." that is NOT in the real link) so you have to right click, open it in a new tab (tell it NOT to download it) and copy the url. 

C@RL

---

### Post by SillyRabbit74 on 2007-10-13
Still no luck on this end...

---

### Post by linuxwizard on 2007-10-13
Did you copy & paste both lines ?

wget -c [http://packages.medibuntu.org/pool/f...uild1_i386.deb](http://packages.medibuntu.org/pool/f...uild1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb

---

### Post by rsambuca on 2007-10-13
Try adding the medibuntu repositories, and then install the w32codecs.  [Instructions are here]("http://medibuntu.sos-sts.com/repository.php").  It is just two terminal line commands to copy and paste.

---

### Post by carlinuxlearner on 2007-10-14
Or you can try the instructions in this attachment, they have the CORRECT URLs.

C@RL

---

### Post by SillyRabbit74 on 2007-10-15
Thanks Carl - I will give it a shot!

---

### Post by timcredible on 2007-10-15
fwiw, i would recommend using mplayer instead of totem.  as for getting it to work, look at [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by rsambuca on 2007-10-15
> **timcredible said:**
> fwiw, i would recommend using mplayer instead of totem.  as for getting it to work, look at [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

Just curious - How come?

---

### Post by venturaz on 2007-10-15
[FONT="Comic Sans MS"]Try Smbplayer that worked better for me....:)[/FONT]




[img]http://www.danasoft.com/sig/Penguinscanfly.jpg[/img]

---

### Post by yabbies on 2007-10-15
sillyrabbit be sure you have opened all of your repos.

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by SillyRabbit74 on 2007-10-16
So I know this should be easy but still no luck when trying to play DVDs through Totum.

Totum Error = "There is no plug in handle this movie."

Here is what I cut and paste the two following commands in my terminal window:

echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Below is the output after the commands were run successfully:

dannyboy@dannyboy-laptop:~$ echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list
Password:
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
dannyboy@dannyboy-laptop:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty Release.gpg                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/free Translation-en_US       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/non-free Translation-en_US   
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty Release                     
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release [2197B]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/free Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/non-free Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/free Packages
  404 Not Found [IP: 193.34.16.167 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gusty/non-free Packages
  404 Not Found [IP: 193.34.16.167 80]
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages [13.0kB]
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages [2849B]
Fetched 18.2kB in 1s (9208B/s)
Failed to fetch [http://packages.medibuntu.org/dists/gusty/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gusty/free/binary-i386/Packages.gz)  404 Not Found [IP: 193.34.16.167 80]
Failed to fetch [http://packages.medibuntu.org/dists/gusty/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/gusty/non-free/binary-i386/Packages.gz)  404 Not Found [IP: 193.34.16.167 80]
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
dannyboy@dannyboy-laptop:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dannyboy@dannyboy-laptop:~$ 
dannyboy@dannyboy-laptop:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



Looks to me like w32codecs and libdvdcss2 are already installed...yet still no play back....?
Sure this would be an easy fix for most but I still have a ways to go through the trial and error learning curve - thanks for the help to date!

---

### Post by rsambuca on 2007-10-16
SillyRabbit, your repositories are really messed up.  You have a mixture of Feisty and Gutsy repositories, and some of the Gutsy ones are spelled incorrectly, resulting in errors.  Please post the output of ```
cat /etc/apt/sources.list
```

---

### Post by SillyRabbit74 on 2007-10-16
Rsambuca,

First off, thanks for working with me here. And Secondly, I see what you mean about having some gusty mixed in with my fiesty! Probably need to clean that up. But, first thing first. I have posted the output you requested below. Any thoughts ? SR 



deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gusty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
dannyboy@dannyboy-laptop:~$

---

### Post by rsambuca on 2007-10-16
Are you sure that is the entire output?  You are missing some repositories.  Also, the medibuntu ones are incorrect for Feisty.

---

### Post by SillyRabbit74 on 2007-10-17
Here is the entire output.  Any ideas on how to clean this up ?


:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gusty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
dannyboy@dannyboy-laptop:~$

---

### Post by rsambuca on 2007-10-17
Just go to [this link]("http://www.ubuntu-nl.org/source-o-matic/") to create a new sources list.

---

