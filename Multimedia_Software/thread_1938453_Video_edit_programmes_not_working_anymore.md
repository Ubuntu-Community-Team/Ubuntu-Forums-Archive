---
title: "Video edit programmes not working anymore"
date: 2012-03-09
forum: Multimedia Software
---

### Post by Finn bjerke on 2012-03-09
I use video editing programmes such as openshot video editor, Kdenlive, Kino. None of em works ! They used to.

1. OPen shot does not start
2. Kdenlive startanother programme which is an ebook reader programme it seems
3. Kino starts allright but can not edit. 

There is a rather strange error message regarding 

> Fatal error MLTs SDL module not found

Screendump:
[img]http://gratisupload.dk/billede/thumb/675394/full/[/img]

---

### Post by Finn bjerke on 2012-03-11
From Terminal :

> finnbjerke@finnbjerke-desktop:~$ openshot

------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.2)
--------------------------------

Detecting formats, codecs, and filters...
Segmentfejl


---

### Post by sudodus on 2012-03-11
You need to tell us more, otherwise it is hard to help.

- What version and flavour of Ubuntu were you running when the video tools worked?

- And what are you running now (what has changed)?
. Have you updated, upgraded, installed or deleted something?

---

### Post by Finn bjerke on 2012-03-11
Thx 4 the kind reply. 

11.10 is the Ubuntu version I use, openshot worked very well in Ubuntu 11.10 until recently. I have installed calibre and little else since the video began to act strange. 

"Segmentation error" 

sound a tad serious ... what is it ?

---

### Post by cfhowlett on 2012-03-12
ALL your video editing programs went down?  VERY strange - but it does suggest a couple of possibilities;

A change to your video card settings resulting in a global change

A change in hardware resulting in a global change - card failure?

What gpu do you have?

---

### Post by sudodus on 2012-03-12
> **Finn bjerke said:**
> Thx 4 the kind reply. 

11.10 is the Ubuntu version I use, openshot worked very well in Ubuntu 11.10 until recently. I have installed calibre and little else since the video began to act strange. 

"Segmentation error" 

sound a tad serious ... what is it ?
I suggest that you test what happens, when you boot a live session from your Ubuntu install CD or USB drive. Do not install, only test, and when running, install openshot into your live session (this does not touch the internal HDD)
```
sudo apt-get install openshot
```Does it work?
If it works, then you have a software error, so I suggest that you try to repair the system by uninstalling and reinstalling software related to graphics and video. If it does not work, then there might be a hardware error (unless you have problems with the graphics in the live session).

---

### Post by Finn bjerke on 2012-03-16
YES indeed. Openshot works well when I boot from install disc, no problem. So where do I go from here?

---

### Post by Finn bjerke on 2012-03-16
Its a little strange that Kdenlive starts an Ebook reader programme when I harddisk boot that is..????

---

### Post by sudodus on 2012-03-16
> **Finn bjerke said:**
> Its a little strange that Kdenlive starts an Ebook reader programme when I harddisk boot that is..????
'Only a little strange' ;-)
Obviously, there is something wrong with your installation, some links point to the wrong targets. I have no idea how easy it would be get things repaired. If it is only the graphics programs, maybe you can purge and reinstall them, for example

```
sudo apt-get purge openshot
``````
sudo apt-get update
``````
sudo apt-get upgrade
``````
sudo apt-get install openshot
```From ```
man apt-get
``` you get this info about purge
>        purge
purge is identical to remove except that packages are removed and purged (any configuration files are deleted too).


---

### Post by Finn bjerke on 2012-03-16
Thansk a lot I tried the procedure you describe no luck - its not working I still get the "segmemnt error" 


------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.2)
--------------------------------
Process no longer exists: 3787.  Creating new pid lock file.

Detecting formats, codecs, and filters...
Segmentfejl

-------------------------------------------------------------------------------------------

---

### Post by sudodus on 2012-03-17
> **Finn bjerke said:**
> Thx 4 the kind reply. 

11.10 is the Ubuntu version I use, openshot worked very well in Ubuntu 11.10 until recently. I have installed calibre and little else since the video began to act strange. 

"Segmentation error" 

sound a tad serious ... what is it ?

1. Do you get normal output or some indication of errors when you run the following commands
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

2. Try to uninstall calibre and 'little else', and after that re-run the commands in post #9.

---

### Post by pixiq on 2012-03-17
> **Finn bjerke said:**
> Thansk a lot I tried the procedure you describe no luck - its not working I still get the "segmemnt error" 


------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.2)
--------------------------------
Process no longer exists: 3787.  Creating new pid lock file.

Detecting formats, codecs, and filters...
Segmentfejl

-------------------------------------------------------------------------------------------
There is something very wrong with your system. If it were mine, I would make a backup of my personal files (documents, pictures, video-clips ...) and then re-install Ubuntu. That is problably easier than to repair it, at least for beginners.

---

### Post by Finn bjerke on 2012-03-17
Update and upgrade seems OK: 

op:~$ sudo apt-get update
[sudo] password for finnbjerke: 
Ignorerer [http://deb.opera.com](http://deb.opera.com) stable InRelease
Havde [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                  
Havde [http://deb.opera.com](http://deb.opera.com) stable Release                                      
Ignorerer [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                       
Havde [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                       
Ignorerer [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                           
Ignorerer [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                
Havde [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                         
Henter:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                   
Havde [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                 
Havde [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                             
Havde [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                            
Havde [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                     
Havde [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                      
Ignorerer [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex               
Havde [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages               
Ignorerer [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex        
Ignorerer [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-da_DK               
Ignorerer [http://apt.spideroak.com](http://apt.spideroak.com) release InRelease                           
Ignorerer [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-da                  
Ignorerer [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                  
Havde [http://apt.spideroak.com](http://apt.spideroak.com) release Release.gpg                             
Havde [http://apt.spideroak.com](http://apt.spideroak.com) release Release                                 
Havde [http://apt.spideroak.com](http://apt.spideroak.com) release/restricted i386 Packages                
Ignorerer [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-da_DK       
Ignorerer [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-da_DK              
Ignorerer [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-da          
Ignorerer [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-da                 
Ignorerer [http://apt.spideroak.com](http://apt.spideroak.com) release/restricted TranslationIndex         
Ignorerer [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en          
Ignorerer [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                 
Ignorerer [http://apt.spideroak.com](http://apt.spideroak.com) release/restricted Translation-da_DK        
Ignorerer [http://apt.spideroak.com](http://apt.spideroak.com) release/restricted Translation-da           
Ignorerer [http://apt.spideroak.com](http://apt.spideroak.com) release/restricted Translation-en           
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                           
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                           
Ignorerer [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric InRelease                       
Ignorerer [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates InRelease               
Ignorerer [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports InRelease             
Ignorerer [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security InRelease              
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                             
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric Release.gpg                         
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates Release.gpg                 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports Release.gpg               
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                             
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security Release.gpg                
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric Release                             
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates Release                     
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                 
Ignorerer [http://linux.dropbox.com](http://linux.dropbox.com) oneiric InRelease                           
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports Release                   
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                            
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                      
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex               
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security Release                    
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/main Sources                        
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/restricted Sources                  
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/universe Sources                    
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/multiverse Sources                  
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/main i386 Packages                  
Havde [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease                          
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                            
Havde [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                      
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex               
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/restricted i386 Packages            
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/universe i386 Packages              
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/multiverse i386 Packages            
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/main TranslationIndex               
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/multiverse TranslationIndex         
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/restricted TranslationIndex         
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/universe TranslationIndex           
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/main Sources                
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/restricted Sources          
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/universe Sources            
Havde [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release.gpg                             
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/multiverse Sources          
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/main i386 Packages          
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/restricted i386 Packages    
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/universe i386 Packages      
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages    
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/main TranslationIndex       
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/universe TranslationIndex   
Havde [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages                 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/main Sources              
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/restricted Sources        
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/universe Sources          
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/multiverse Sources        
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/main i386 Packages        
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/restricted i386 Packages  
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/universe i386 Packages    
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages  
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/main TranslationIndex     
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/universe TranslationIndex 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/main Sources               
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/restricted Sources         
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/universe Sources           
Havde [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release                                 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/multiverse Sources         
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/main i386 Packages         
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/restricted i386 Packages   
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/universe i386 Packages     
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/multiverse i386 Packages   
Havde [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages             
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/main TranslationIndex      
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/multiverse TranslationIndex
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/restricted TranslationIndex
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/universe TranslationIndex  
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/main Translation-da                 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/main Translation-en                 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/multiverse Translation-da           
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/multiverse Translation-en           
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/restricted Translation-da           
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/restricted Translation-en           
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/universe Translation-da             
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric/universe Translation-en             
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/main Translation-en         
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/multiverse Translation-en   
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/restricted Translation-en   
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-updates/universe Translation-en     
Havde [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main i386 Packages                      
Ignorerer [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex          
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/main Translation-en
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/multiverse Translation-en 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/restricted Translation-en 
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-backports/universe Translation-en   
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/main Translation-en        
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/multiverse Translation-en  
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/restricted Translation-en  
Havde [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) oneiric-security/universe Translation-en    
Ignorerer [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex      
Ignorerer [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main TranslationIndex               
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-da_DK              
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-da                 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-da_DK              
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-da                 
Ignorerer [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                 
Ignorerer [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-da_DK              
Ignorerer [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-da                 
Ignorerer [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en                 
Ignorerer [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-da_DK         
Ignorerer [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-da            
Ignorerer [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en            
Ignorerer [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-da_DK     
Ignorerer [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-da
Ignorerer [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en
Hentede 72 B på 13s (5 B/s)                               
Indlæser pakkelisterne... Færdig


------------

 sudo apt-get upgrade
[sudo] password for finnbjerke: 
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
0 opgraderes, 0 nyinstalleres, 0 afinstalleres og 0 opgraderes ikke.

---

### Post by Finn bjerke on 2012-03-17
I need my Calibre info and books, can i back it up ?

---

### Post by sudodus on 2012-03-17
> **Finn bjerke said:**
> I need my Calibre info and books, can i back it up ?

It is a good idea to back everything up, before you are changing your system. At least you should backup your private files including documents, pictures and video clips, in your case obviously also your ebooks. I don't know how much work you have invested in the Calibre settings, anyway, that should reside in some dedicated directory (I don't know where, maybe ~/.calibre)

If you have or can get an external HDD, it will make the backup easier.

*Edit: But before doing anything else, it's a good idea to check your file system (the system partition / ) with e2fsck.* Check what partition it is running the command ```
df
``` You must boot from another drive (I suggest a live session from your Ubuntu install drive. Do not mount any partition on your internal drive! And then run
```
sudo e2fsck -f /dev/sdxy
```
where x is a for the first drive, and y is 1 for the first partition /dev/sda1 and for example /dev/sdb5 for the fifth partition on the second drive.

---

### Post by BCtom on 2012-03-17
Just adding to this thread. I just changed the PPA, and downloaded and installed the latest version of openshot too: Version: **1**.4.2, and I get the same result, in this thread.

> ------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.2)
--------------------------------
Process no longer exists: 2889.  Creating new pid lock file.

Detecting formats, codecs, and filters...
Segmentation fault

As far as I can tell it only effects openshot for me, and no other programs that I can tell are not working on my machine. I may just wait until 12.04 LTS is out and see if that fixes it since we are so close to the change anyway. I will keep an eye on this thread though. 

Running Gnome/ Ubuntu 11:10

---

### Post by Finn bjerke on 2012-03-17
Very important info. Thanks you so much ! is it at all possible to downgrade to the previous version of openshot  ?

---

### Post by Finn bjerke on 2012-03-18
Copying the home files to external harddisk gave a few errors. copying hidden files 10 files or so wouldnt copy.

---

### Post by sudodus on 2012-03-18
> **Finn bjerke said:**
> Copying the home files to external harddisk gave a few errors. copying hidden files 10 files or so wouldnt copy.
Maybe some file is opened, and not allowed to be copied. If you run a live session booted from a CD or USB drive, you should be able to copy everything (with sudo). Or there is an error with your file system, that might be repaired with e2fsck.

But *BCtom*'s information is important. Probably that is a key to your solution. Have you installed some special PPA (Personal Package Archive repository) to get the newest version? In that case, remove that, purge openshot, and reinstall (and now it should install the standard version. Or are you running a beta version of Ubuntu?

Which versions of Ubuntu and Openshot are you running?

---

### Post by 2bob on 2012-03-18
Hi!
It seems that you have to reinstall Openshot if you installed it from ppa but before read this please: [http://askubuntu.com/questions/307/how-can-ppas-be-removed](http://askubuntu.com/questions/307/how-can-ppas-be-removed).
2bob

---

### Post by Finn bjerke on 2012-03-18
Your kind help is much appreciated. 

Well I just reinstalled Ubuntu 11.10 Openshot is now working  !   But there is a challenge: Codecs are missing i need to 
** Install libx264 and libmp3lame**

link here: 
[https://answers.launchpad.net/openshot/+faq/1040](https://answers.launchpad.net/openshot/+faq/1040)

Alternatively I just use mpeg2 and not use the H264 option.

This worked for me (so far) 

I terminal in did this: 

> sudo apt-get install ffmpeg libavcodec-extra-53 

Inspired by this link
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

now it works. I have not yet tested is rigouresly but I will.

---

### Post by 2bob on 2012-03-18
```
sudo apt-get install non-free-codecs
```
might help a lot... :p

---

### Post by Finn bjerke on 2012-03-18
Im getting nervous, now it works so why experiment. If it aint broke dotn fix it... 

hmm also Im curious..

So I tried: The pacakage was not found. 

sudo apt-get install non-free-codecs
finn@finn-desktop:~$ sudo apt-get install non-free-codecs
[sudo] password for finn: 
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
E: Kunne ikke lokalisere pakken non-free-codecs



THANK YOU GUYS.  I love Ubuntu

---

### Post by 2bob on 2012-03-18
Hi!
You have to enable Medibuntu repository first. You'll find it here: 
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)
After that run
```
sudo apt-get install non-free-codecs
```
You'll get a much better life, believe me.
Cheerio!
2bob

---

### Post by Finn bjerke on 2012-03-18
Medibuntu will actually improve my lifequality ? interesting...

---

### Post by Finn bjerke on 2012-03-18
OK installed it. openshot still works also in High def H264 formats. thx a lot.

---

### Post by pixiq on 2012-03-18
> **Finn bjerke said:**
> OK installed it. openshot still works also in High def H264 formats. thx a lot.
You got some valuable help and made it without reinstalling. Congratulations :KS

I think we are several people around here, who are learning from this thread.

---

### Post by sudodus on 2012-03-18
> **Finn bjerke said:**
> OK installed it. openshot still works also in High def H264 formats. thx a lot.
I'm glad too, you made it without reinstalling the whole system :KS

Please mark this thread as SOLVED, click [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page!

---

### Post by 2bob on 2012-03-18
> **Finn bjerke said:**
> OK installed it. openshot still works also in High def H264 formats. thx a lot.
Seee... I told you...! 
I will rephrase: "You'll get a... high quality... life." :lolflag:
Viva Tux!
2bob

---

### Post by Finn bjerke on 2012-03-18
Oooooops I did reinstall Ubuntu 11.10 -

---

### Post by 2bob on 2012-03-18
Well... I am on 12.04 already and Openshot seems to run okay. Next time, if you decide to start from the beginning, try a repair only - it usually saves you the time with recovering the files and settings.
2bob

---

### Post by BCtom on 2012-03-18
Thanks guys, it worked for me too! I would say this is "solved" also. :p Downgrading fixed it.

---

