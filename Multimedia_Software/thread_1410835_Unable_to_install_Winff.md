---
title: "Unable to install Winff"
date: 2010-02-19
forum: Multimedia Software
---

### Post by Brother Ubun2 on 2010-02-19
Hi All,

So far I have had allot of fun with Intrepid Ibex...

However I have run into a brick wall with trying to install winff.

Below is the error message in Syn. Manager.

winff:
 Depends: ffmpeg  but it is not installable
 Recommends: winff-doc but it is not going to be installed
 Recommends: libavcodec-extra-52  but it is not installable

In addition to the above is there a comprehensive software source list that every Ibex user should have?

Thanks for your help in advance!

---

### Post by mc4man on 2010-02-19
Not sure where you are getting the winff package to install but it's not meant for intrepid, probably it's for karmic.

You need to add this ppa, using the intrepid address ( click on "not using Ubuntu 9.10 (karmic"
[https://launchpad.net/~paul-climbing/+archive/ppa](https://launchpad.net/~paul-climbing/+archive/ppa)

further info, ect., ect.
[http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)

---

### Post by Brother Ubun2 on 2010-02-19
Hi. Thanks for responding.

I have done as suggested (i hope) and get the following:

ubuntu@ubuntu-desktop:~$ wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add -
OK
ubuntu@ubuntu-desktop:~$ echo "deb [http://winff.org/ubuntu](http://winff.org/ubuntu) intrepid ibex" | sudo tee /etc/apt/sources.list.d/winff.list
deb [http://winff.org/ubuntu](http://winff.org/ubuntu) intrepid ibex
ubuntu@ubuntu-desktop:~$ sudo apt-get update && sudo apt-get install winff
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid Release                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates Release                      
Get:1 [http://winff.org](http://winff.org) intrepid Release.gpg [197B]                             
Ign [http://winff.org](http://winff.org) intrepid/ibex Translation-en_US                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/multiverse Packages                  
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/multiverse Sources                   
Get:2 [http://winff.org](http://winff.org) intrepid Release [2041B]                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Fetched 2238B in 1s (1177B/s)
W: Failed to fetch [http://winff.org/ubuntu/dists/intrepid/Release](http://winff.org/ubuntu/dists/intrepid/Release)  Unable to find expected entry  ibex/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
ubuntu@ubuntu-desktop:~$

---

### Post by Brother Ubun2 on 2010-02-19
Below is also a list of my software sources.

---

### Post by mc4man on 2010-02-19
Looking at your sources you already had the ppa - paul-climbing

Why he has a recommend of libavcodec-extra-52 for the intrepid .deb I don't know - libavcodec-unstripped-51 is the intrepid ver.
Any way it's just a recommend, what your issue is  - why is ffmpeg not installable.?

You could search ffmpeg in synaptic and see what the story is there.

What may be better is to forget the intrepid ffmpeg - it's pretty old, and go here and build and install a new static ffmpeg to use with winff.
If so, then follow the directions for intrepid - if you have any issues with the presets than post in that thread for help

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Brother Ubun2 on 2010-02-20
Hi Mc4man,

Have done as suggested but the problem just seems to get more complicated. Is there a debug report that I can generate or a hijackthis type report?

Thanks for your help.

---

### Post by SuperSonic4 on 2010-02-20
Those packages are in medibuntu, which you don't seem to have

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Brother Ubun2 on 2010-02-21
Hi SuperSonic,

Thanks for your help. 

Based on what MC4MAN posted on the last round I followed the link ([http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)), clicked on the link (Install FFmpeg and x264 on Ubuntu Intrepid Ibex 8.10) and got as far as step 3 before a quite because of catch 22 nonsense as you can see below.

Prior to doing this though I added the medibuntu sources as you suggested. Pls see attached. 

Thanks at anyrate for your input. Much appreciated.


ubuntu@ubuntu-desktop:~$ sudo apt-get remove ffmpeg x264 libx264-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ffmpeg is not installed, so not removed
Package x264 is not installed, so not removed
Package libx264-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  id3v2 libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
ubuntu@ubuntu-desktop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US                                                       
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid Release.gpg                                                                               
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/restricted Translation-en_US                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US                                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                                                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                                                                            
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/multiverse Translation-en_US                                                              
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates Release.gpg                                                    
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US                                   
Ign [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US                                   
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid Release                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                                                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                                                                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US                                                                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US                                            
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages                                             
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates Release                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                                                                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                                                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources                                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources                        
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/restricted Packages                              
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/restricted Sources                               
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/multiverse Packages                              
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid/multiverse Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources                                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                                                         
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [82.7kB]                                    
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/restricted Packages                                              
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/restricted Sources                                                  
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/multiverse Packages                                                 
Hit [http://ls.archive.ubuntu.com](http://ls.archive.ubuntu.com) intrepid-updates/multiverse Sources                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources
Fetched 82.7kB in 4s (17.7kB/s)                        
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_intrepid-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_intrepid-security_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
ubuntu@ubuntu-desktop:~$ sudo apt-get install build-essential subversion git-core checkinstall yasm texi2html libfaac-dev libfaad-dev libmp3lame-dev libsdl1.2-dev libx11-dev libxfixes-dev libxvidcore4-dev zlib1g-dev apt-get update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
Package subversion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package subversion has no installation candidate
ubuntu@ubuntu-desktop:~$ cd
ubuntu@ubuntu-desktop:~$ git clone git://git.videolan.org/x264.git
The program 'git' is currently not installed.  You can install it by typing:
sudo apt-get install git-core
bash: git: command not found
ubuntu@ubuntu-desktop:~$ cd x264
bash: cd: x264: No such file or directory
ubuntu@ubuntu-desktop:~$ ./configure
bash: ./configure: No such file or directory
ubuntu@ubuntu-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
ubuntu@ubuntu-desktop:~$ sudo checkinstall --fstrans=no --install=yes --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1" --backup=no --default
sudo: checkinstall: command not found
ubuntu@ubuntu-desktop:~$ sudo apt-get install git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package git-core is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  git-gui
E: Package git-core has no installation candidate
ubuntu@ubuntu-desktop:~$ sudo apt-get install git-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  git-gui: Depends: git-core (> 1:1.5.6.3) but it is not installable
           Depends: git-core (< 1:1.5.6.3-.) but it is not installable
           Depends: tk8.5 but it is not installable
           Recommends: gitk but it is not installable
E: Broken packages
ubuntu@ubuntu-desktop:~$

---

### Post by mc4man on 2010-02-21
> Package subversion is not available, but is referred to by another package.
Because of that nothing else was installed from the apt-get install command including git-core so ..
> ubuntu@ubuntu-desktop:~$ git clone git://git.videolan.org/x264.git
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git-core

Everything you ran after that was to no avail, no source was dl'ed, ect.

> ubuntu@ubuntu-desktop:~$ cd x264
bash: cd: x264: No such file or directory
ubuntu@ubuntu-desktop:~$ ./configure
bash: ./configure: No such file or directory
ect. ect.



You''ve got some issue with your sources, reflected by above troubles and also by 
> ubuntu@ubuntu-desktop:~$ sudo apt-get remove ffmpeg x264 libx264-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package ffmpeg is not installed, so not removed
Package x264 is not installed, so not removed
Package libx264-dev is not installed, so not removed
 maybe post 
> cat /etc/apt/sources.list


Also, out of curiousity, when you did your re-install you didn't pick a username?, or used ubuntu as one?
> ubuntu@ubuntu-desktop:~$

---

### Post by Brother Ubun2 on 2010-02-22
Hi Mc4man,

To be honest I wanted to keep it ubuntu. Generic as possible. Is this an issue? or just confusing? I have done as suggested. See below. Thanks for your help.

ubuntu@ubuntu-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) intrepid restricted
deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) intrepid restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) intrepid-updates restricted
deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) intrepid-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://ls.archive.ubuntu.com/ubuntu/](http://ls.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) intrepid main
# deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) intrepid main
deb [http://ppa.launchpad.net/paul-climbing/ppa/ubuntu](http://ppa.launchpad.net/paul-climbing/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/paul-climbing/ppa/ubuntu](http://ppa.launchpad.net/paul-climbing/ppa/ubuntu) intrepid main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted multiverse universe
ubuntu@ubuntu-desktop:~$

---

### Post by Brother Ubun2 on 2010-02-24
Hi All,

This thread is going stale. Anybody out there who ca help?
Thanks

---

