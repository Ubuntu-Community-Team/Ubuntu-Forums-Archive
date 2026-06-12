---
title: "Can't play AVI files"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by toecutter on 2007-09-04
I've just tried installing the gxine Movie Player as a last resort, but it isn't playing some AVI files I have.

The program seems to start up, flash for a quarter second, then shut down with nothing happening. *I have no clue* what is happening.

I've also tried: 
KMplayer (same result as above)
Mplayer (same result as above - but nothing will play with it)
VLC (very jerky with any video, unwatchable with these latest files)

I use Envy to have the latest ATI drivers installed, I've updated it tonight and still the same result. Also, as far as I know there is no DRM (these were downloaded from a bittorrent site). What am I missing? 

I've tried adding win32 codecs per the Ubuntu help guide and got this:
```
frank@frank-linux:~$ sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

```

AFAIK I've tried every possible Ubuntu movie player and I don't have satisfactory video performance. Nothing I would want to show my Windoze-using friends, anyway.

---

### Post by taurus on 2007-09-04
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by toecutter on 2007-09-04
Thanks for the quick reply! :) 

OK I did everything in the link you posted, but the win32 codecs still are having troubles:
```
frank@frank-linux:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
frank@frank-linux:~$ 
```

Gxine and Mplayer won't open anything (same symptom as before) but VLC is a tiny bit smoother but still jerky. KMplayer actually plays the first 10 seconds smoothly, but after that goes black. Can't move to a different part of the movie or anything (actually this is the same problem with all the movie players I've tried).

Any ideas? Is the problem still the win32 codecs, considering that is apparently the only thing that hasn't worked?

---

### Post by taurus on 2007-09-04
Did you add the medibuntu's repo to /etc/apt/sources.list?

Did you remember to update the source list first?

```
sudo apt-get update
```

Otherwise, post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by toecutter on 2007-09-04
Thanks again :)

I did the apt-get update, then the install command for win32 codecs, still nothing. 

Here is my sources.list:

frank@frank-linux:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

### added by me
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
## Medibuntu - Ubuntu 7.04 "feisty fawn" ----- for DVD & Win32 Codecs 
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

---

### Post by taurus on 2007-09-04
Can you post the complete output of this command?

```
sudo apt-get update
```

---

### Post by toecutter on 2007-09-04
yarp:

frank@frank-linux:~$ sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB          
Get: 2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_GB              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB    
Get: 3 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]                  
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_GB                 
Get: 4 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release.gpg [189B]                    
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Translation-en_GB             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                             
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_GB             
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release                                  
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Get: 5 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release.gpg [191B]               
Ign [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Translation-en_GB              
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Hit [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets Packages                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages                       
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release                             
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty/main Packages                       
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
Get: 6 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]       
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_GB      
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Get: 9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Sources
Fetched 9B in 5s (2B/s)  
Reading package lists... Done

---

### Post by taurus on 2007-09-04
Try it again this time.

```
sudo apt-get install libdvdcss2 w32codecs
```
Otherwise, either reboot or fire up synaptic and see if you can find w32codecs on the list with the Search option.

---

### Post by rsambuca on 2007-09-04
Whoa, Whoa, Whoa!

I see from your signature that you are using Feisty 64bit.  You can't install the W32codecs.  Try the w64codecs instead!

---

### Post by toecutter on 2007-09-04
Ah.

Yes.

Stupid, stupid me. 

I successfully installed the win**64**codecs package, however the movies are still as jerky as ever in VLC, and Gxine, Mplayer, etc., still don't work at all.

---

### Post by toecutter on 2007-09-06
I can still just barely watch stuff in VLC - should I try uninstalling and re-installing the other movie players? That's the only thing left I can think of...

---

### Post by rsambuca on 2007-09-06
OK, let's figure this out.  Does this only happen with certain avi files, or all avi files.  What about dvd's, mpegs, etc?

---

### Post by Seamyst on 2007-09-15
I just did a nuke-and-pave of my Feisty partition and have done all the usual instructions to get media files to work... and most of my avi files will play just fine.  One, however, doesn't.  No matter what I open it with, the program will open for a second and then automatically quit.  I know the file itself isn't corrupted, because I can watch it with VLC on my OS X partition.

Any ideas?  I've tried all the suggestions in this thread and no luck.

---

### Post by toecutter on 2007-09-18
> **rsambuca said:**
> OK, let's figure this out.  Does this only happen with certain avi files, or all avi files.  What about dvd's, mpegs, etc?

Hi, sorry, my subscription email thing didn't work, I'll try out a series of movies with all the players and report back in the next day or so. Basically, the ONLY player that plays any video at all is VLC, all the others don't open at all (Mplayer) or seem to start up but take ages to load (Gxine).

---

### Post by toecutter on 2007-09-27
OK - sorry I couldn't post sooner, my work sent me away unexpectedly last week, etc., etc... :)

Anyway, all AVI files are affected. VLC plays most of the randomly collected files I have just fine, some are very jerky and stuttery but the rest are watchable or 100% fine. No other player I have works: Mplayer, Movie player, Gxine, whatever, none of the them work. These players don't even start up properly. I posted earlier in the thread about the dependencies and files and such I've installed to get all the codecs and stuff. 

With MPEG files, same exact thing happens except VLC is more likely to be very jerky with some (audio is okay).

For DVDs, only VLC seems to work! Video is jerky, audio is fine.

So at the moment I'm a bit stuck with being able to watch some of my files with just one program. It just seems really strange that these other programs don't work at all.

---

