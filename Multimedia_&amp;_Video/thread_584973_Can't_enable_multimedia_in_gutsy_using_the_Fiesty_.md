---
title: "Can't enable multimedia in gutsy using the Fiesty How TO"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by angus_young on 2007-10-21
Help

I've been trying to install the multimedia how to in gutsy using the fiesty multimedia how to

but i've had no joy, 

this is the problem i come up against
desktop:~$ sudo mousepad /etc/apt/sources.list[sudo] password for delboy:
desktop:~$ wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
gpg: no valid OpenPGP data found.
delboy@delboy-desktop:~$ 

then the folowing

desktop:~$ sudo apt-get update
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Get: 2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg [191B]                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Translation-en_GB                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/web Translation-en_GB            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
Get: 4 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]       
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_GB      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Translation-en_GB            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/web Translation-en_GB                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB            
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg [191B]           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/web Translation-en_GB           
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg                            
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_GB                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB    
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_GB             
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release                         
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages                          
  302 Found
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Packages             
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages                      
  302 Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources                           
  302 Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources                       
  302 Found
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release.gpg
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Translation-en_GB
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Packages
Hit [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Packages
Fetched 5B in 1s (3B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz)  302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz)  302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
desktop:~$ 

can anyone help please

---

### Post by super.roz on 2007-10-21
Similar problem here.  I tried to upgrade from feisty to gutsy using the update manager and received the following error:
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

---

### Post by Zwack on 2007-10-21
Go see this...

[Medibuntu help page]("https://help.ubuntu.com/community/Medibuntu")

Z.

---

### Post by super.roz on 2007-10-21
[https://answers.launchpad.net/ubuntu/+question/15530](https://answers.launchpad.net/ubuntu/+question/15530)

Address of the packages has changed.
The fix didn't actually work for me, but I went in and manually made the change in the sources.list file.
I changed [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) to [http://packages.medibuntu.org/](http://packages.medibuntu.org/)

---

### Post by JacobRogers on 2007-10-22
> **Zwack said:**
> Go see this...

[Medibuntu help page]("https://help.ubuntu.com/community/Medibuntu")

Z.

I'm trying this

---

### Post by JacobRogers on 2007-10-22
> **Zwack said:**
> Go see this...

[Medibuntu help page]("https://help.ubuntu.com/community/Medibuntu")

Z.

Worked perfect combined with adding all the codecs that are in plug ins in the repos.

---

