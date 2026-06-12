---
title: "error in Version string '3.0.10-54097_Ubuntu_karmic':"
date: 2010-09-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2010-09-21
after upgrading to MM, I get this error when I run installs
karmic?? going back aways
> scott@scott-desktop:~$ sudo apt-get install openoffice.org-pdfimport
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  openoffice.org-pdfimport
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 713kB of archives.
After this operation, 795kB of additional disk space will be used.
Get:1 [http://mirrors.rit.edu/ubuntu/](http://mirrors.rit.edu/ubuntu/) maverick/universe openoffice.org-pdfimport i386 1.0.2+OOo3.2.1-6ubuntu2 [713kB]
Fetched 713kB in 0s (772kB/s)                   
warning, in file '/var/lib/dpkg/status' near line 55330 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 57385 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
Selecting previously deselected package openoffice.org-pdfimport.
(Reading database ... 496863 files and directories currently installed.)
Unpacking openoffice.org-pdfimport (from .../openoffice.org-pdfimport_1.0.2+OOo3.2.1-6ubuntu2_i386.deb) ...
warning, in file '/var/lib/dpkg/status' near line 55351 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 57406 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
Setting up openoffice.org-pdfimport (1.0.2+OOo3.2.1-6ubuntu2) ...
Copying: pdfimport.oxt
Enabling: PDF Import
 Enabling: PDFImport
 Enabling: xpdfimport
 Enabling: pdfimport.uno.so
 Enabling: pdf_import_filter.xcu
 Enabling: pdf_types.xcu

unopkg done.
scott@scott-desktop:~$ 


---

### Post by yeus on 2010-09-22
yeah same problem here..  solution would be very much appreciated..

---

### Post by grinias on 2010-09-23
> **yeus said:**
> yeah same problem here..  solution would be very much appreciated..
Same problem here...

---

### Post by dino99 on 2010-09-23
clean your virtualbox setup (or remove/reinstall it), this might be oldish things left behind.

---

### Post by yeus on 2010-09-24
> **dino99 said:**
> clean your virtualbox setup (or remove/reinstall it), this might be oldish things left behind.
This doesn't even work when deinstalling it.. error still remains..

---

### Post by piscue on 2010-09-28
the same :/

---

### Post by dino99 on 2010-09-28
- check your sources.list: might be clean (no exotic ppa, same distro and release)

- sudo apt-get clean / autoclean / autoremove

into nautilus: search for karmic

you can use gtkorphan, gconf-cleaner and bleachbit to remove unneeded stuff

- sudo apt-get update
- sudo apt-get install -f

Also see:
[https://bugs.launchpad.net/ubuntu/+source/dirac/+bug/649280](https://bugs.launchpad.net/ubuntu/+source/dirac/+bug/649280)
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/482486](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/482486)

**** which virtalbox is it: ose or puel ?

---

### Post by sdowney717 on 2010-09-28
Think that fixed it thanks
```
scott@scott-desktop:~$ sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  advancecomp libfaad0 libmodplug0c2 optipng python-qt3
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 12.4MB disk space will be freed.
Do you want to continue [Y/n]? y
warning, in file '/var/lib/dpkg/status' near line 49505 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 57557 package 'virtualbox-3.0':
 error in Version string '3.0.10-54097_Ubuntu_karmic': invalid character in revision number
(Reading database ... 483221 files and directories currently installed.)
Removing advancecomp ...
Removing libfaad0 ...
Removing libmodplug0c2 ...
Removing optipng ...
Removing python-qt3 ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for python-support ...


scott@scott-desktop:~$ sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by sdowney717 on 2010-09-28
got another issue this one.
running update does not get rid of that error

W: Duplicate sources.list entry [http://archive.canonical.com/](http://archive.canonical.com/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_maverick_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


```
scott@scott-desktop:~$ sudo apt-get update
Get:1 http://mirrors.rit.edu maverick Release.gpg [198B]
Ign http://mirrors.rit.edu/ubuntu/ maverick/multiverse Translation-en          
Ign http://mirrors.rit.edu/ubuntu/ maverick/multiverse Translation-en_US       
Get:2 http://dl.google.com stable Release.gpg [189B]                           
Ign http://mirrors.rit.edu/ubuntu/ maverick/universe Translation-en            
Hit http://archive.canonical.com maverick Release.gpg                          
Get:3 http://archive.ubuntu.com maverick Release.gpg [198B]                    
Ign http://mirrors.rit.edu/ubuntu/ maverick/universe Translation-en_US         
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Hit http://mirrors.rit.edu maverick-updates Release.gpg                        
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en      
Ign http://mirrors.rit.edu/ubuntu/ maverick-updates/multiverse Translation-en  
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://mirrors.rit.edu/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://mirrors.rit.edu/ubuntu/ maverick-updates/universe Translation-en    
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Ign http://mirrors.rit.edu/ubuntu/ maverick-updates/universe Translation-en_US 
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://mirrors.rit.edu maverick-security Release.gpg                       
Ign http://mirrors.rit.edu/ubuntu/ maverick-security/multiverse Translation-en 
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Ign http://mirrors.rit.edu/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Get:4 http://dl.google.com stable Release [1,338B]                             
Ign http://mirrors.rit.edu/ubuntu/ maverick-security/universe Translation-en   
Ign http://mirrors.rit.edu/ubuntu/ maverick-security/universe Translation-en_US
Ign http://archive.canonical.com/ maverick/partner Translation-en              
Get:5 http://mirrors.rit.edu maverick Release [57.3kB]                         
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Get:6 http://dl.google.com stable/main i386 Packages [613B]                    
Ign http://archive.canonical.com/ maverick/partner Translation-en_US           
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Hit http://mirrors.rit.edu maverick-updates Release                            
Hit http://archive.canonical.com maverick Release                              
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Hit http://mirrors.rit.edu maverick-security Release                           
Hit http://archive.canonical.com maverick Release                              
Get:7 http://mirrors.rit.edu maverick/universe Sources [4,183kB]               
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Hit http://archive.canonical.com maverick/partner Sources                      
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://archive.ubuntu.com maverick-updates Release.gpg                     
Hit http://security.ubuntu.com maverick-security Release                   
Hit http://archive.canonical.com maverick/partner i386 Packages                
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en   
Hit http://security.ubuntu.com maverick-security/main Sources                
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://security.ubuntu.com maverick-security/universe Sources              
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en 
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Hit http://archive.ubuntu.com maverick-backports Release.gpg                   
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Get:8 http://mirrors.rit.edu maverick/multiverse Sources [150kB]
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Get:9 http://mirrors.rit.edu maverick/universe i386 Packages [5,784kB]
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Get:10 http://archive.ubuntu.com maverick Release [57.3kB]
Get:11 http://mirrors.rit.edu maverick/multiverse i386 Packages [182kB]       
Hit http://mirrors.rit.edu maverick-updates/universe Sources                   
Hit http://mirrors.rit.edu maverick-updates/multiverse Sources                 
Hit http://mirrors.rit.edu maverick-updates/universe i386 Packages             
Hit http://mirrors.rit.edu maverick-updates/multiverse i386 Packages           
Hit http://mirrors.rit.edu maverick-security/universe Sources                  
Hit http://mirrors.rit.edu maverick-security/multiverse Sources                
Hit http://mirrors.rit.edu maverick-security/universe i386 Packages            
Hit http://mirrors.rit.edu maverick-security/multiverse i386 Packages          
Hit http://archive.ubuntu.com maverick-updates Release                         
Hit http://archive.ubuntu.com maverick-backports Release             
Get:12 http://archive.ubuntu.com maverick/main Sources [830kB]       
Get:13 http://archive.ubuntu.com maverick/restricted Sources [4,361B]          
Get:14 http://archive.ubuntu.com maverick/universe Sources [4,183kB]           
Get:15 http://archive.ubuntu.com maverick/multiverse Sources [150kB]           
Get:16 http://archive.ubuntu.com maverick/main i386 Packages [1,495kB]         
Get:17 http://archive.ubuntu.com maverick/restricted i386 Packages [6,000B]    
Get:18 http://archive.ubuntu.com maverick/universe i386 Packages [5,784kB]     
Get:19 http://archive.ubuntu.com maverick/multiverse i386 Packages [182kB]     
Hit http://archive.ubuntu.com maverick-updates/main Sources                    
Hit http://archive.ubuntu.com maverick-updates/restricted Sources              
Hit http://archive.ubuntu.com maverick-updates/universe Sources                
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources              
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages              
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages        
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages          
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages        
Hit http://archive.ubuntu.com maverick-backports/main Sources                  
Hit http://archive.ubuntu.com maverick-backports/restricted Sources            
Hit http://archive.ubuntu.com maverick-backports/universe Sources              
Hit http://archive.ubuntu.com maverick-backports/multiverse Sources            
Hit http://archive.ubuntu.com maverick-backports/main i386 Packages            
Hit http://archive.ubuntu.com maverick-backports/restricted i386 Packages      
Hit http://archive.ubuntu.com maverick-backports/universe i386 Packages        
Hit http://archive.ubuntu.com maverick-backports/multiverse i386 Packages      
Fetched 23.0MB in 29s (775kB/s)                                                
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_maverick_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
scott@scott-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scott@scott-desktop:~$ 

```

---

