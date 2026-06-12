---
title: "Ubuntu 13.04 can't install Guitar Pro 6"
date: 2013-05-24
forum: Multimedia Software
---

### Post by bmass on 2013-05-24
So I've spent the last few hours trying to trouble-shoot this issue by doing online searches but the more I read the more confused I get and I must suck at Linux because I don't understand what half of these guys are saying in terms of steps to follow.



Basically I have gp6-full-linux-r11201.deb and I tried double-clicking on it. This launches Ubuntu Software Centre which returns the error: Cannot install 'gksu:i386'

I tried this method for trouble-shooting: [http://getsatisfaction.guitar-pro.com/arobas_music/topics/how_to_install_gp6_from_the_demo_deb_in_ubuntu_11_10_64_bits](http://getsatisfaction.guitar-pro.com/arobas_music/topics/how_to_install_gp6_from_the_demo_deb_in_ubuntu_11_10_64_bits)

And it seemed to install Guitar Pro 6 but when I try to launch the program nothing happens.


```
peace-hammer@Peace-Factory:~$ sudo apt-get install qt4-qtconfig
[sudo] password for peace-hammer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  qt4-qtconfig
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/93.0 kB of archives.
After this operation, 561 kB of additional disk space will be used.
Selecting previously unselected package qt4-qtconfig.
(Reading database ... 279498 files and directories currently installed.)
Unpacking qt4-qtconfig (from .../qt4-qtconfig_4%3a4.8.4+dfsg-0ubuntu9_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up qt4-qtconfig (4:4.8.4+dfsg-0ubuntu9) ...
peace-hammer@Peace-Factory:~$ sudo dpkg --force-depends -i gp6-full-linux-r11201.deb
Selecting previously unselected package guitarpro6.
(Reading database ... 279517 files and directories currently installed.)
Unpacking guitarpro6 (from gp6-full-linux-r11201.deb) ...
dpkg: guitarpro6: dependency problems, but configuring anyway as you requested:
 guitarpro6 depends on libportaudio0; however:
  Package libportaudio0 is not installed.
 guitarpro6 depends on gksu; however:

Setting up guitarpro6 (6.1.4) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
peace-hammer@Peace-Factory:~$ qtconfig-qt4
```



So I opened the terminal and typed ```
sudo apt-get autoremove guitarpro6
``` and ```
sudo apt-get autoremove qt4-qtconfig
```

I think this successfully undid what I did with that guide.


```
peace-hammer@Peace-Factory:~$ sudo apt-get autoremove guitarpro6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  guitarpro6:i386
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 104 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 280249 files and directories currently installed.)
Removing guitarpro6 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
peace-hammer@Peace-Factory:~$ sudo apt-get autoremove qt4-qtconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  qt4-qtconfig
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 561 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 279516 files and directories currently installed.)
Removing qt4-qtconfig ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
```


I then tried this guide: [http://andyjstormont.blogspot.ca/2010/12/installing-guitar-pro-6-on-ubuntu.html](http://andyjstormont.blogspot.ca/2010/12/installing-guitar-pro-6-on-ubuntu.html)


```
peace-hammer@Peace-Factory:~$ sudo dpkg -i --force-architecture gp6-full-linux-r11201.deb
[sudo] password for peace-hammer: 
Selecting previously unselected package guitarpro6.
(Reading database ... 279498 files and directories currently installed.)
Unpacking guitarpro6 (from gp6-full-linux-r11201.deb) ...
dpkg: dependency problems prevent configuration of guitarpro6:
 guitarpro6 depends on libportaudio0; however:
  Package libportaudio0 is not installed.
 guitarpro6 depends on gksu; however:

dpkg: error processing guitarpro6 (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 guitarpro6
peace-hammer@Peace-Factory:~$ sudo apt-get install -f libportaudio0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 guitarpro6:i386 : Depends: libportaudio0:i386 but it is not going to be installed
                   Depends: gksu:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
peace-hammer@Peace-Factory:~$ sudo apt-get -f install libportaudio0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 guitarpro6:i386 : Depends: libportaudio0:i386 but it is not going to be installed
                   Depends: gksu:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
peace-hammer@Peace-Factory:~$ sudo apt-get -f install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gksu : Depends: libgksu2-0 (>= 2.0.8) but it is not going to be installed
 guitarpro6:i386 : Depends: libportaudio0:i386 but it is not going to be installed
                   Depends: gksu:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Then I downloaded and copied the 4 files into /opt/Guitar Pro 6

I used the launcher to run Guitar Pro 6 and again nothing happened so I autoremoved guitar pro 6 again and deleted the Guitar Pro 6 folder in /opt to be sure.



So I tried to follow these guides as best I could but I have absolutely no idea what they are supposed to do or if I'm even back at square one (did the dependencies install correctly? Do I need to uninstall them?)



Now I tried this guide: [http://ubuntuforums.org/showthread.php?t=1458626&page=2](http://ubuntuforums.org/showthread.php?t=1458626&page=2)

which is the only one that even kind of made sense to me. gksu is causing the error so remove the dependency... I can grasp that. The guy's link to the script just confused me even more and so I googled how to edit the dependencies of a .deb file and followed this guide: [http://ubuntuforums.org/showthread.php?t=110458](http://ubuntuforums.org/showthread.php?t=110458)

which is still really confusing (as in I don't know what any of the commands did) but I got a hacked.deb file now which I was able to open and install using the Ubuntu Software centre (after running ```
sudo apt-get install ia32-libs
``` from the terminal. But I get an error during install which says:

The package is of bad quality

The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organization who provided this package file and include the details beneath.

Details: ```
Lintian check results for /home/peace-hammer/hacked.deb:
E: GuitarPro6: control-file-has-bad-owner md5sums peace-hammer/peace-hammer != root/root
E: GuitarPro6: bad-package-name
E: GuitarPro6: package-not-lowercase
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Help/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Help/GP6 User's Manual 2010.06 DE.pdf 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Help/GP6 User's Manual 2010.06 EN.pdf 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Help/GP6 User's Manual 2010.06 FR.pdf 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Help/GP6 User's Manual 2010.06 JA.pdf 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Help/GP6 User's Manual 2010.06 PT_BR.pdf 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Help/Help.checklist 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Bass/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Bass/Acoustic Bass.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Bass/Electric Bass (finger).preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Bass/Electric Bass (pick).preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Bass/Funk Bass.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Bass/Funky Bass.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Bass/Overdriven Bass.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Bass/Slap Bass.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Drums/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Drums/Jazz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Drums/Rock.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Andy's Breathe.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Blues Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Day Trip Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Funky Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Funky Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Jazz Comping.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Modern Jazz Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Nothing Else But Arpeggios.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Reggae Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Stray Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Wes.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Clean/Wide Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Crunch/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Crunch/Alan H.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Crunch/Blues Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Crunch/Country Blues Drive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Crunch/Highway To Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Crunch/Jimmy Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Crunch/Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Crunch/Pop Drive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric Crunch/Satch Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Aint talkin bout EVH.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Alan.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Blues Lead Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Dirty Rat.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/EVH.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Grunge.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Heavy Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Heavy Rock Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Heavy and Loud.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/High Gain British Stack.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Jimmy Lead.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Luke Lead.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Metal Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Modern Rock.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Nu Metal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Satch Lead.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Thrash Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Electric High-Gain/Vintage Vibes.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Acoustic - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Acoustic Simulation - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Acoustic Simulation - Finger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Acoustic Simulation - Jumbo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Acoustic Simulation - Regular.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Acoustic Simulation - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Acoustic Simulation - Tiny.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Aerian Acoustic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Aerian Chorused Acoustic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Heaven Acoustic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Jeff Acoustic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Ovation Acoustic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Acoustic Tones/Taj Acoustic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Auto Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Blues Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Blues.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Boutique Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Chorus.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Distortion +.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Finger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Grunge Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Metal Pedal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Phaser.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Pi Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Rat Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Rock.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Screamer Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Tone Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Clean/American Clean - Tremolo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Auto Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Blues Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Boutique Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Chorus.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Cranked-up.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Distortion +.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Grunge Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Metal Pedal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Phaser.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Pi Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Rat Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Screamer Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Tone Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Tremolo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/American Tweed/American Tweed - Vintage.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/Bass - Amp Simulation.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/Bass - Auto Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/Bass - Boosted.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/Bass - Compressed.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/Bass - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/Bass - Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/Bass - Panning.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/Bass - Rock.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/Bass - Slap.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/Bass - Tremolo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Bass Tones/Bass - on Top-30.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Auto Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Blues Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Boutique Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Chorus.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Crispy.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Crunch.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Dirt.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Distortion +.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Grunge Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Metal Pedal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Phaser.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Pi Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Rat Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Screamer Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Tone Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Clean/British Stack Clean - Tremolo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Auto Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Blues Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Boutique Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Chorus.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Classic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Crunch.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Distortion +.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Grunge Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Hard Rock.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Metal Pedal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Phaser.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Pi Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Rat Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Rock.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Screamer Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Solo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Tone Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Stack Dist/British Stack Dist - Tremolo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Auto Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Blues Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Blues.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Boutique Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Chorus.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Crunch.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Distortion +.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Grunge Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Hard Rock.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Metal Pedal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Phaser.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Pi Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Rat Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Screamer Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Solo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Tone Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/British Vintage/British Vintage - Tremolo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Drums Tones/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Drums Tones/Drums - Compressed.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Drums Tones/Drums - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Drums Tones/Drums - Flange.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Drums Tones/Drums - Reverb.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Auto Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Blues Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Boutique Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Chorus.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Crispy.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Crunch.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Distortion +.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Finger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Grunge Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Metal Pedal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Phaser.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Pi Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Rat Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Screamer Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Tone Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Tremolo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Clean/Eddie Clean - Vintage.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Auto Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Blues Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Boutique Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Chorus.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Crunch.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Distortion +.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Eddie.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Grunge Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Hard Rock.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Metal Pedal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Metal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Panama.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Phaser.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Pi Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Rat Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Screamer Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Tone Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Eddie Lead/Eddie Lead - Tremolo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Aero Dream - Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Aero Dream - Lead.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Aero Dream - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Andy On The Moon - Chorus.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Andy On The Moon - Delay.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Andy On The Moon - Take.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Eddie Got Me - Acoustic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Eddie Got Me - Brown Sound.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Eddie Got Me - Church.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Eddie Got Me - Lead.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Eddie Got Me - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Eddie Got Me - Volcanic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Hey Jimi - Angel.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Hey Jimi - Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Hey Jimi - Crunch.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Hey Jimi - Disto.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Hey Jimi - Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Hey Jimi - Octavia.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Hey Jimi - Univibe.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Hey Jimi - Voodoo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Hey Jimi - Wind.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Jimmy Heaven - Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Jimmy Heaven - Lead.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Metal - Puppets.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Metal James - Acoustic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Metal James - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Metal Kirk - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Metal Kirk - Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Nork - Gear.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Nork - Head Set.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Nork - Munky Set.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/SRV - Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/SRV - Crunch.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/SRV - Lead.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/SRV - Tone.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Satch - Always.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Satch - Boogie.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Satch - Flying.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Satch - Surfing.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Above.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Another.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Apache.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - B. Goode.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Behind.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Brothers.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Carlos.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Dark Star.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Dead Skin.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - For Love.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Fuzzy Train.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Grunge.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Lazy.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Old Jazz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - One Step.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Ritchie, Randy, Yngwie.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Sleepwalk.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Stones.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Sugar.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Sunday.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Sweet Home.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Talking.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Teen Spirit.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - The Line.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Top Gun.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Single - Wylde.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Zakk Time - Acoustic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Zakk Time - Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Zakk Time - Lead.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Legend Tones/Zakk Time - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Other Tones/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Other Tones/Synth Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Auto Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Blues Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Boutique Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Chorus.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Clean.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Crispy.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Crunch.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Distortion +.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Finger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Grunge Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Metal Pedal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Phaser.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Pi Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Rat Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Screamer Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Tone Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Tremolo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Clean/Recti Clean - Vintage.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Auto Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Blues Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Boutique Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Chorus.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Crunch.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Distortion +.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Grunge Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Metal Pedal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Metal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Phaser.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Pi Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Rat Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Rock.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Screamer Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Tone Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Trash.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Tremolo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Recti Lead/Recti Lead - Vintage.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Auto Wah.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Blues Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Boutique Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Chorus.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Cranked-up.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Default.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Distortion +.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Flanger.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Funky.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Grunge Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Metal Pedal.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Phaser.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Pi Distortion.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Rat Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Rock.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Screamer Overdrive.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Tone Fuzz.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/GP5/Top 30/Top 30 - Tremolo.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Nylon/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Nylon/Bossa.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Nylon/Classical.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Nylon/Finger Comping.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Presets.checklist 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Steel/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Steel/Cash Rhythm.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Steel/Django Lines.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Steel/Gipsy Comping.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Steel/Jazz Acoustic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Steel/Processed Acoustic.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Steel/Steel Delay Reverb Pick.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Steel/Steel Finger Arpeggios.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Steel/Steel Reverb Pick.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Presets/Steel/Steel Soloing.preset 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/BongoNCongas/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/BongoNCongas/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/BongoNCongas/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Drumkit-Master/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Drumkit-Master/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Drumkit-Master/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Africa/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Africa/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Africa/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Agogo/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Agogo/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Agogo/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Bongo/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Bongo/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Bongo/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Conga/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Conga/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Conga/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Cuica/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Cuica/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Cuica/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Latino/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Latino/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Latino/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Percu/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Percu/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Percu/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Samba/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Samba/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Samba/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Timbale/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Timbale/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Timbale/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Whistle/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Whistle/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Whistle/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Woodblock/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Woodblock/assembly.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kit-Woodblock/bank.xml 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Soundbanks/Kits/Kits.checklist 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Acoustic Bass.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Blues Power Trio.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Classical Guitar.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Drumkit.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Electric Bass.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Electric Guitar Clean.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Electric Guitar Distortion.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Electric Guitar Overdriven.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Empty.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Jazz Guitar.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Jazz Trio.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Metal Band.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Nylon Guitar.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Rock Band.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Rock Power Trio.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Singer.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Steel Guitar.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Strings Quartet.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Synthesizer Bass.gpt 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Templates/Templates.checklist 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_da_DK.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_de_DE.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_en_US.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_es_ES.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_fi_FI.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_fr_FR.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_hu_HU.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_it_IT.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_ja_JP.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_ko_KR.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_nb_NO.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_nl_NL.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_pl_PL.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_pt_BR.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_pt_PT.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_ro_RO.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_ru_RU.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_sv_SE.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/GuitarProTR_zh_CN.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/Translations.checklist 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_da.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_de.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_es.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_fi.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_fr.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_hr.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_hu.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_it.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_ja_JP.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_ko.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_nb.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_nl.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_pl.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_pt.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_ro.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_ru.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_sv.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Data/Translations/qt/qt_zh_CN.qm 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/GPBankInstaller 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/GPConverter 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/GPInstaller 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/GPUpdater 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/GuitarPro 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/ 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-000 Acoustic Grand Piano.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-001 Bright Acoustic Piano.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-002 Electric Grand Piano.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-003 Honky-tonk Piano.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-004 Rhodes Piano.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-005 Chorused Piano.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-006 Harpsichord.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-007 Clavinet.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-008 Celesta.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-009 Glockenspiel.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-010 Music Box.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-011 Vibraphone.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-012 Marimba.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-013 Xylophone.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-014 Tubular Bells.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-015 Dulcimer.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-016 Hammond Organ.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-017 Percussive Organ.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-018 Rock Organ.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-019 Church Organ.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-020 Reed Organ.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-021 Accordion.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-022 Harmonica.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-023 Accordion.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-024 Acoustic Guitar (nylon).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-025 Acoustic Guitar (steel).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-026 Electric Guitar (jazz).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-027 Electric Guitar (clean).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-028 Electric Guitar (muted).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-029 Overdriven Guitar.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-030 Distortion Guitar.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-031 Guitar Harmonics.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-032 Acoustic Bass.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-033 Electric Bass (finger).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-034 Electric Bass (pick).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-035 Fretless Bass.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-036 Slap Bass 1.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-037 Slap Bass 2.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-038 Synth Bass 1.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-039 Synth Bass 2.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-040 Violin.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-041 Viola.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-042 Cello.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-043 Contrabass.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-044 Tremolo Strings.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-045 Pizzicato Strings.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-046 Harp.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-047 Timpani.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-048 String Ensemble 1.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-049 String Ensemble 2.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-050 SynthStrings 1.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-051 SynthStrings 2.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-052 Choir Aahs.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-053 Voice Oohs.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-054 Synth Voice.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-055 Orchestra Hit.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-056 Trumpet.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-057 Trombone.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-058 Tuba.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-059 Muted Trumpet.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-060 French Horn.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-061 Brass Section.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-062 Synth Brass 1.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-063 Synth Brass 2.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-064 Soprano Sax.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-065 Alto Sax.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-066 Tenor Sax.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-067 Baritone Sax.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-068 Oboe.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-069 English Horn.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-070 Bassoon.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-071 Clarinet.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-072 Piccolo.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-073 Flute.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-074 Recorder.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-075 Pan Flute.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-076 Blown Bottle.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-077 Shakuhachi.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-078 Whistle.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-079 Ocarina.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-080 Lead 1 (square).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-081 Lead 2 (sawtooth).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-082 Lead 3 (calliope).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-083 Lead 4 (chiff).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-084 Lead 5 (charang).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-085 Lead 6 (voice).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-086 Lead 7 (fifths).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-087 Lead 8 (bass+lead).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-088 Pad 1 (new age).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-089 Pad 2 (warm).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-090 Pad 3 (polysynth).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-091 Pad 4 (choir).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-092 Pad 5 (bowed).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-093 Pad 6 (metallic).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-094 Pad 7 (halo).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-095 Pad 8 (sweep).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-096 FX1 (rain).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-097 FX2 (soundtrack).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-098 FX3 (crystal).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-099 FX4 (atmosphere).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-100 FX5 (brightness).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-101 FX6 (Gobblins).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-102 FX7 (Echoes).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-103 FX8 (Sci-Fi).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-104 Sitar.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-105 Banjo.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-106 Shamisen.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-107 Koto.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-108 Kalimba.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-109 Bagpipe.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-110 Fiddle.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-111 Shanai.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-112 Tinkle Bell.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-113 Agogo.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-114 Steel Drums.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-115 Woodblock.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-116 Taiko Drum.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-117 Melodic Tom.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-118 Synth Drum.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-119 Reverse Cymbal.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-120 Guitar Fret Noise.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-121 Breathe Noise.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-122 Seashore.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-123 Birdtweet.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-124 Telephone Ring.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-125 Helicopter.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-126 Applause.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/00-127 Gunshot.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-028 Slap.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-039 Hand Clap.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-054 Tambourine.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-056 Cowbell.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-058 Vibraslap.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-060 High Bongo.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-061 Low Bongo.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-062 Mute Hi Conga.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-063 Open Hi Conga.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-064 Low Conga.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-065 High Timbale.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-066 Low Timbale.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-067 High Agogo.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-068 Low Agogo.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-069 Cabasa.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-070 Maracas.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-071 Short Whistle.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-072 Long Whistle.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-073 Short Guiro.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-074 Long Guiro.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-075 Claves.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-076 Hi Wood Block.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-076 Woodblock.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-077 Low Wood Block.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-077 Woodblock.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-078 Mute Cuica.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-079 Open Cuica.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-080 Mute Triangle.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-081 Open Triangle.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-082 Shaker.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-083 Jingle Bell.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-084 Bell Tree.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-085 Castinets.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-086 Mute Surdo.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/10-087 Open Surdo.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/12 Strings Acoustic Guitar (steel).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/12 Strings Electric Guitar (clean).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/12 Strings Electric Guitar (distortion).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/12 Strings Electric Guitar (overdrive).gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/Bongos N Congas.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/Drumkit Split.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/Drumkit.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/Kit Africa.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/Kit Latino.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/Kit Samba.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/Presets/presets/Ukulele.gpp 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/SoundbanksVolumeChangesSettings.ini 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/launcher.sh 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libGPCore.so 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libOverLoud.so 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libPickupModeling.so 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libQtCore.so.4 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libQtDBus.so.4 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libQtGui.so.4 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libQtNetwork.so.4 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libQtOpenGL.so.4 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libQtSvg.so.4 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libQtWebKit.so.4 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libQtXml.so.4 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libQtXmlPatterns.so.4 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libRSEAudioCore.so 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libRSECore.so 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libWavFile.so 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libZip.so 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libboost_date_time-gcc43-mt-1_39.so.1.39.0 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libboost_filesystem-gcc43-mt-1_39.so.1.39.0 1000/1000
E: GuitarPro6: wrong-file-owner-uid-or-gid opt/GuitarPro6/libboost_regex-gcc43-mt-1_39.so.1.39.0 1000/1000
```

As far as editing the .deb went I typed the following in a terminal (not sure what it does but...)


```
dpkg-deb -x gp6-full-linux-r11201.deb tmpdir
dpkg-deb --control gp6-full-linux-r11201.deb tmpdir/DEBIAN
sudo gedit tmpdir/DEBIAN/control
```

Then I removed gksu from the depends line and saved the file and ran:

```
dpkg -b tmpdir hacked.deb
```

from the terminal which gave me the hacked.deb file I ran which gave me the above error.



As far as the rest of the trouble-shooting outlined in this guide goes: [http://ubuntuforums.org/showthread.php?t=1458626](http://ubuntuforums.org/showthread.php?t=1458626)

I didn't really understand how to follow the steps. I couldn't find getlibs-all.deb on the internet anywhere.

Any help is appreciated. I'm not sure what to do next... I feel like I messed up somewhere with removing the dependencies from the original file... or some sort of error in repacking the new file. Thank you very much in advance.


EDIT: Sorry, forgot to mention that after getting the error installing hacked.deb in Ubuntu Software Centre I click ignore and install anyway and it installs Guitar Pro 6 but running the application through unity does nothing. I autoremoved again, so I have a clean slate presently.

---

### Post by bmass on 2013-05-26
bump

---

### Post by Finn bjerke on 2013-10-28
I have solved this problem look here: [http://ubuntuforums.org/showthread.php?t=2082197](http://ubuntuforums.org/showthread.php?t=2082197)

---

### Post by Finn bjerke on 2014-09-21
IT seems Ubuntu 14.04 works with Guitar pro 6 with out any modifications or trix

---

### Post by coffeecat on 2014-09-21
This thread concerns Ubuntu 13.04 which is long past end-of-life.

Old thread closed.

---

