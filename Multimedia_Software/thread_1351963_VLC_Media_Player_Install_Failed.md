---
title: "VLC Media Player Install Failed"
date: 2009-12-11
forum: Multimedia Software
---

### Post by ..::| Dave89 |::.. on 2009-12-11
I tried to install VLC Media Player by adding **ppa:c-korn/vlc** to Software Sources and installing from Ubuntu Software Center, but got this message:

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Am I doing something wrong? (Most likely).

---

### Post by alexfish on 2009-12-11
Hi

 do it direct from synaptic 

  look for VLC


  If You Have Pulse Audio then You will Need VLC-Plugin-Pulse Via Synaptic

Also install libsdl1.2debian-all 


This The Site For Video land  RE:Ubuntu Check out what you May need

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

You will also Need  libdvdcs2

---

### Post by ..::| Dave89 |::.. on 2009-12-11
I got the same message in Synaptic.

---

### Post by alexfish on 2009-12-11
> **..::| Dave89 |::.. said:**
> I got the same message in Synaptic.

Did you upgrade Or Clean Install

---

### Post by ..::| Dave89 |::.. on 2009-12-11
I did a clean install of 9.10.

---

### Post by mc4man on 2009-12-11
You should probably ck. and see that all the 'Ubuntu Software' sources are enabled in System -> Admin. -> Software Sources. The first 4 under Ubuntu Software, and the first 2 under 'Updates'. ( If you had to enable any of them then click close and reload.
Otherwise or then try just running (post complete output if vlc doesn't install
```
sudo apt-get update && sudo apt-get install vlc
```

---

### Post by ..::| Dave89 |::.. on 2009-12-11
I got:
dave89@dave89-laptop:~$ sudo apt-get update && sudo apt-get install vlc
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_AU
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_AU              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_AU          
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_AU                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_AU    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_AU      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_AU    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic Release.gpg                            
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/main Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/restricted Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/universe Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic/multiverse Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates Release.gpg
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/main Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/restricted Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/universe Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/multiverse Translation-en_AU
  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]
Fetched 308B in 2min 0s (3B/s)                        
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D
W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2)  Cannot initiate the connection to au.archive.ubuntu.com:80 (2001:388:30bc:cafe::beef). - connect (101: Network is unreachable) [IP: 2001:388:30bc:cafe::beef 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 1.0.3-1~ppa1) but it is not going to be installed
       Depends: libqtcore4 (>= 4.5.1) but it is not installable
       Depends: libqtgui4 (>= 4.5.1) but it is not installable
       Depends: libsdl-image1.2 (>= 1.2.5) but it is not installable
       Depends: libtar but it is not installable
       Depends: libx264-67 (>= 1:0.svn20090502) but it is not installable
       Recommends: vlc-plugin-pulse (= 1.0.3-1~ppa1) but it is not going to be installed
E: Broken packages
dave89@dave89-laptop:~$ 


I didn't have to enable anything in Software Sources

---

### Post by mc4man on 2009-12-11
Try opening software sources and pick another server, either use the main server (should be fine) or pick 'other' -> "select best server"
( also on the main software sources page make sure the cdrom source is **disabled**

---

### Post by ..::| Dave89 |::.. on 2009-12-11
Tried that, used the [http://mirror.upm.edu.my/ubuntu](http://mirror.upm.edu.my/ubuntu), which was selected as best server, still same message.

EDIT: I downloaded vlc_0.9.4-1ubuntu3_ i386.deb directly from [http://mirror.upm.edu.my/ubuntu](http://mirror.upm.edu.my/ubuntu) double clicked on the archive, and got this message:

Error: Dependency is not satisfiable: vlc-nox (= 0.9.4-1ubuntu3)

Also when trying to download PulseAudio plugin for VLC I get: 

"Could not mark all packages for installation or upgrade
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

vlc-plugin-pulse:
Depends: vlc-nox but it is not going to be installed"

I tried to install vlc-nox, but got this:

"Could not mark all packages for installation or upgrade
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

vlc-nox:
 Depends: liba52-0.7.4  but it is not installable
 Depends: libass3 (>=0.9.6-1) but it is not installable
 Depends: libavcodec52 (>=3:0.svn20090303-1) but it is not installable or
     libavcodec-extra-52 (>=3:0.svn20090303-1) but it is not installable
 Depends: libavformat52 (>=3:0.svn20090303-1) but it is not installable or
     libavformat-extra-52 (>=3:0.svn20090303-1) but it is not installable
 Depends: libavutil49 (>=3:0.svn20090303-1) but it is not installable or
     libavutil-extra-49 (>=3:0.svn20090303-1) but it is not installable
 Depends: libdca0  but it is not installable
 Depends: libdvbpsi5  but it is not installable
 Depends: libdvdnav4 (>=4.1.3) but it is not installable
 Depends: libdvdread4 (>=4.1.3) but it is not installable
 Depends: libebml0  but it is not installable
 Depends: libfaad0 (>=2.6.1) but it is not installable
 Depends: liblua5.1-0  but it is not installable
 Depends: libmad0 (>=0.15.1b-3) but it is not installable
 Depends: libmatroska0  but it is not installable
 Depends: libmodplug0c2 (>=1:0.7-4.1) but it is not installable
 Depends: libmpcdec3  but it is not installable
 Depends: libmpeg2-4  but it is not installable
 Depends: libpostproc51 (>=3:0.svn20090303-1) but it is not installable or
     libpostproc-extra-51 (>=3:0.svn20090303-1) but it is not installable
 Depends: libschroedinger-1.0-0 (>=1.0.7) but it is not installable
 Depends: libswscale0 (>=3:0.svn20090303-1) but it is not installable or
     libswscale-extra-0 (>=3:0.svn20090303-1) but it is not installable
 Depends: libtwolame0  but it is not installable
 Depends: libvcdinfo0 (>0.7.23) but it is not installable"

---

### Post by mc4man on 2009-12-11
Possibly similar situation..?
[http://ubuntuforums.org/showthread.php?t=1312561](http://ubuntuforums.org/showthread.php?t=1312561)

---

### Post by ..::| Dave89 |::.. on 2009-12-11
It does sound similar, I do have trouble updating and installing applications.

I typed in 
sudo apt-get update [FONT=monospace]
in the terminal: this is what I got:

dave89@dave89-laptop:~$ sudo apt-get update
[sudo] password for dave89: 
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_AU                     
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                  
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_AU    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_AU    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_AU
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_AU
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                           
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg [189B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release   
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release [44.1kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                 
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release [44.1kB]        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages [190kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages [5,133kB]             
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages [113kB]           
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages [14B]      
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages [3,041B]   
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages [64.4kB]     
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages [37.5kB]        
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages [14B]     
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages [1,666B]  
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages [14.1kB]    
Fetched 5,646kB in 2min 33s (36.7kB/s)                                         
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D
dave89@dave89-laptop:~$ 


[/FONT]

---

### Post by mc4man on 2009-12-11
Dave - wish I knew more about networking ect. , but don't.

A few observations - the errors in post7 match the link exactly, in that case 2 posters resolved with router firmware updates.
On the other hand I've noticed people having issues from au servers fairly frequently, switching to the 'main' server has helped.

The command you ran in posts 7 and 11 are  the same (sudo apt-get update), but on post 11 it succeeded., and if it had been followed by a sudo apt-get install vlc command it may have worked.

From reading some other pages on the basic error seen in post 7 (Network is unreachable), it also could be something in your network settings.(vs. the router or server used

Hopefully someone who knows more in this area will assist you.

---

### Post by ..::| Dave89 |::.. on 2009-12-11
I did the sudo apt-get install vlc command in terminal, got VLC installed, but while it plays audio CD's just fine, it won't play DVD's. I think it most likely needs a plugin, but I'm not sure which one, or where to look. Perhaps Synaptic?

---

### Post by mc4man on 2009-12-11
some progress..
> it won't play DVD's
Run this in a terminal, it will install libdvdcss2
```

sudo /usr/share/doc/libdvdread4/install-css.sh
```

Then try a dvd again. (sometimes in karmic a restart is needed when installing codecs, ect.

If no good then start vlc like this for starters and see whatshows up ( will keep output to a min

```
vlc dvd://
```

---

### Post by ..::| Dave89 |::.. on 2009-12-11
It works now, although it has lower volume than the audio CD I was playing.  I'm going to look through my previous thread about low volume in VLC and see if I can fix it.

I changed the download server in Software Sources from Server in Australia to Main Server, now I can download software.  I couldn't download anything before, now I can.

---

### Post by mc4man on 2009-12-11
> I'm going to look through my previous thread about low volume in VLC and see if I can fix it.

I generally find vlc has the best volume output of the media players, in karmic i  use the pulseaudio output in vlc's settings, typically the vlc level is 90 - 100%, master at 75%

Historically though  dvd movies have a lower volume output than other media, even on standalone hardware dvd players.



Edit; those values where for a laptop, on desktop with decent 5.1 they're lower, (70% or less), the external control takes care of volume

---

