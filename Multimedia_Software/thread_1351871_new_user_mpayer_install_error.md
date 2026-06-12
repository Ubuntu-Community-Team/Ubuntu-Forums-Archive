---
title: "new user mpayer install error"
date: 2009-12-11
forum: Multimedia Software
---

### Post by thumpszilla on 2009-12-11
First off I am using ubuntu 9.10, with a ati radeon x1300 pro on an old compaq system much faster on linux than it was with even win98. I installed Devede to burn my movie backup but it will not start it tells me it needs mplayer. So when I go to the software center and try to install mplayer it gives me an error (see attached screenshot please) I do not know how to compile from svn which is what I would like to do since I need to learn the commands for compiling anyway. So if anyone could help me to get this installed either by compiling or through software center I would be very greatful. Also if anyone could point me to some easy to follow guides for compiling that would be great also.

---

### Post by Linuxforall on 2009-12-11
Use synaptic and install devedee and it will automatically install mplayer from the repos. Make sure you have medibuntu repos enabled. Go to [www.medibuntu.org](www.medibuntu.org) and follow instructions on how to.

---

### Post by thumpszilla on 2009-12-11
Wow thanks for your quick reply I will try this now.

---

### Post by mc4man on 2009-12-11
> some easy to follow guides for compiling that

[http://ubuntuforums.org/showthread.php?t=1305181](http://ubuntuforums.org/showthread.php?t=1305181)

Edit :as far as your installing mplayer/devede issues - 
did you upgrade from jaunty to karmic?

do you have any ppa's enabled?
If so, which one, and what version of mplayer or mplayer-nogui is presently installed - ck. in synaptic package manager
(as far as I know the 'software center' will not install packages from ppa's,

---

### Post by thumpszilla on 2009-12-11
linuxforall I went by your instructions and opened software sources- other software and both medibuntu entries are checked. I unistalled devede and reinstalled using synaptic manager. However it did not install mplayer with it. Any clue why not?

mc4man thank you for the link will give it a read and see if it sinks in.

---

### Post by Linuxforall on 2009-12-11
> **thumpszilla said:**
> linuxforall I went by your instructions and opened software sources- other software and both medibuntu entries are checked. I unistalled devede and reinstalled using synaptic manager. However it did not install mplayer with it. Any clue why not?

mc4man thank you for the link will give it a read and see if it sinks in.

Can you check mplayer in your synaptic to see if it installs?

---

### Post by thumpszilla on 2009-12-11
mc4man- This was a fresh 9.10 install. I have no mplayer that shows up in my apps menu. If by ppa's you mean repos under software sources then please see attached image. 


Linuxforall- I will check that now and sorry for the noob ness

---

### Post by thumpszilla on 2009-12-11
ok mplayer installed using synaptic manager but devede still does not recognize it as being there. What now?

---

### Post by thumpszilla on 2009-12-11
while going by the posted compile tutorial in the first section I got these errors

Errors were encountered while processing:
 /var/cache/apt/archives/libopencore-amrnb0_0.1.2-1_i386.deb
 /var/cache/apt/archives/libopencore-amrnb-dev_0.1.2-1_i386.deb
 /var/cache/apt/archives/libopencore-amrwb0_0.1.2-1_i386.deb
 /var/cache/apt/archives/libopencore-amrwb-dev_0.1.2-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Linuxforall on 2009-12-11
> **thumpszilla said:**
> ok mplayer installed using synaptic manager but devede still does not recognize it as being there. What now?

Is mencoder installed?

---

### Post by mc4man on 2009-12-11
There's some posts with a similar problem as yours. I'll search out some links for you.

Meanwhile maybe try this

Open synaptic and search mplayer
Mark for complete removal - mplayer, mplayer-nogui, mencoder

Devede should also be set for removal from above actions, but go ahead and search it and also mark for complete removal
then click apply, after done close synaptic out

Then open a terminal, copy and paste this in, press enter
```
sudo apt-get update && sudo apt-get install devede
```

Try devede again, but leave the terminal open so you can copy and paste the output if devede doesn't start.

( you could after doing the above restart if devede doesn't open, karmic 'benefits' from restarts more than it should

Note: I would first square away devede before building your own mplayer-nogui, you need mencoder for devede and by default the guide won't install mencoder

---

### Post by thumpszilla on 2009-12-11
still not recognizing mplayer terminal output attached mplayer does not open either

```
sam@sam-desktop:~$ sudo apt-get update
[sudo] password for sam: 
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release.gpg
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign [http://ubuntu.global-web.us]("http://ubuntu.global-web.us/") binary/ Release.gpg                            
Ign [http://ubuntu.global-web.us]("http://ubuntu.global-web.us/") binary/ Translation-en_US                      
Ign [http://ubuntu.global-web.us]("http://ubuntu.global-web.us/") binary/ Release                                
Ign [http://ubuntu.global-web.us]("http://ubuntu.global-web.us/") binary/ Packages                               
Hit [http://archive.canonical.com]("http://archive.canonical.com/") karmic Release.gpg                            
Ign [http://archive.canonical.com]("http://archive.canonical.com/") karmic/partner Translation-en_US              
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic Release.gpg                                
Ign [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic/main Translation-en_US                     
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic Release.gpg                               
Ign [http://ubuntu.global-web.us]("http://ubuntu.global-web.us/") binary/ Packages                               
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/main Translation-en_US                 
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic Release.gpg                           
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic/free Translation-en_US                
Ign [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic/non-free Translation-en_US            
Hit [http://ubuntu.global-web.us]("http://ubuntu.global-web.us/") binary/ Packages                               
Hit [http://archive.canonical.com]("http://archive.canonical.com/") karmic Release                                
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic Release                                    
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic Release                                   
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic Release                                
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic Release                               
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates Release                        
Hit [http://archive.canonical.com]("http://archive.canonical.com/") karmic/partner Packages                       
Hit [http://ppa.launchpad.net]("http://ppa.launchpad.net/") karmic/main Packages                              
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/main Sources                              
Hit [http://archive.canonical.com]("http://archive.canonical.com/") karmic/partner Sources                        
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/main Packages                          
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic/free Packages                         
Hit [http://archive.ubuntu.com]("http://archive.ubuntu.com/") karmic/restricted Sources              
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/restricted Packages          
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/restricted Sources           
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/main Sources                 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/multiverse Sources           
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/universe Sources             
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic/non-free Packages           
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic/free Sources                
Hit [http://packages.medibuntu.org]("http://packages.medibuntu.org/") karmic/non-free Sources            
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/universe Packages            
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/multiverse Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security Release.gpg
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/main Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security Release
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/main Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/restricted Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/multiverse Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/multiverse Packages
W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
sam@sam-desktop:~$ sudo apt-get install devede
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdiscid0 jhead transcode-doc transcode libsox-fmt-base sox dvd-slideshow
  libsox-fmt-alsa xine-ui libsox1a libjpeg-progs libmusicbrainz3-6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  mencoder mplayer mplayer-nogui mplayer-skins
Suggested packages:
  mplayer-doc netselect fping
The following NEW packages will be installed:
  devede mencoder mplayer mplayer-nogui mplayer-skins
0 upgraded, 5 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B/11.7MB of archives.
After this operation, 17.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  mplayer-nogui mplayer mencoder
Install these packages without verification [y/N]? y
Selecting previously deselected package mplayer-skins.
(Reading database ... 197610 files and directories currently installed.)
Unpacking mplayer-skins (from .../mplayer-skins_3_all.deb) ...
Selecting previously deselected package mplayer-nogui.
Unpacking mplayer-nogui (from .../mplayer-nogui_3%3a1.0~svn-r29779-1_i386.deb) ...
Selecting previously deselected package mplayer.
Unpacking mplayer (from .../mplayer_3%3a1.0~svn-r29779-1_i386.deb) ...
Selecting previously deselected package mencoder.
Unpacking mencoder (from .../mencoder_3%3a1.0~svn-r29779-1_i386.deb) ...
Selecting previously deselected package devede.
Unpacking devede (from .../devede_3.14.0-0ubuntu5_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up mplayer-skins (3) ...
Setting up mplayer-nogui (3:1.0~svn-r29779-1) ...
Setting up mplayer (3:1.0~svn-r29779-1) ...
Setting up mencoder (3:1.0~svn-r29779-1) ...
Setting up devede (3.14.0-0ubuntu5) ...

sam@sam-desktop:~$
```

---

### Post by thumpszilla on 2009-12-11
tried running mplayer from terminal and got this

```
sam@sam-desktop:~$ mplayer
mplayer: error while loading shared libraries: libggi.so.2: cannot open shared object file: No such file or directory
sam@sam-desktop:~$ mplayer
Illegal instruction
sam@sam-desktop:~$ 

```

installed  libggi2 and dependencies and devede works but as you can see mplayer does not. I have smplayer frontend installed and this is the crash log it produce when trying to play video files. 

```
  p, li { white-space: pre-wrap; }  /usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv, -ao alsa, -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 60817423 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/sam/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -af equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/sam/Videos/The best christmas pageant ever[1986]{scooty1us}/The best christmas pageant ever[1986]{scooty1us}.avi

```

---

### Post by mc4man on 2009-12-11
Well obviously you're getting an mplayer from somewhere other than the karmic repo, most likely a ppa or some other repo
> Unpacking mplayer-nogui (from .../mplayer-nogui_3%3a1.0~svn-r29779-1_i386.deb) ..
ect.
Considering ppa's/repo's don't generally install themselves, then whose did you add?

Post these if inclined
```
ls /etc/apt/sources.list.d/*.list
```
```
cat /etc/apt/sources.list
```

Also - have you built and installed an mplayer at some point?

what's this show, if anything
```
ls /usr/local/bin
```

---

### Post by thumpszilla on 2009-12-14
Not sure how but I got it fixed. Sorry for late reply but haven't been home in a few days. Again thanks for all your help I learned alot.

---

