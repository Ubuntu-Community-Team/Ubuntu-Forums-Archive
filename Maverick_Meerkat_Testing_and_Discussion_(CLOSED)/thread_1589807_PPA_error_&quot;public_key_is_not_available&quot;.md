---
title: "PPA error &quot;public key is not available&quot;"
date: 2010-10-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sendblink23 on 2010-10-07
This is a clean fresh install of 10.10 RC from probably 3 days ago - already using all latest updates

My PPA's are working fine but... not sure.. but at the end I'm getting an error of public key... is that normal for any of you guys when running: sudo apt-get update  - I haven't changed anything to my PPA's... just only added Docky & Wine PPA's(on which they update perfectly fine - the error is not from them)

This is the error at the end:
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```


My current: sudo apt-get update
```
sendblink23@sendblink23-MS-7577:~$ sudo apt-get update
[sudo] password for sendblink23: 
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Get:1 http://extras.ubuntu.com maverick Release.gpg [65B]           
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/docky-core/stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/docky-core/stable/ubuntu/ maverick/main Translation-en_US
Get:2 http://pr.archive.ubuntu.com maverick Release.gpg [198B]       
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release             
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://pr.archive.ubuntu.com maverick-updates Release.gpg        
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release                        
Get:3 http://extras.ubuntu.com maverick Release [57.3kB]             
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Err http://extras.ubuntu.com maverick Release                                  
  
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://ppa.launchpad.net maverick Release  
Hit http://security.ubuntu.com maverick-security/main Sources        
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://pr.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Get:4 http://pr.archive.ubuntu.com maverick Release [57.3kB]         
Hit http://security.ubuntu.com maverick-security/restricted Sources         
Hit http://security.ubuntu.com maverick-security/universe Sources           
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main amd64 Packages         
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages   
Hit http://ppa.launchpad.net maverick/main Sources     
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages     
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages   
Hit http://ppa.launchpad.net maverick/main Sources                           
Hit http://ppa.launchpad.net maverick/main amd64 Packages
Hit http://pr.archive.ubuntu.com maverick-updates Release
Get:5 http://pr.archive.ubuntu.com maverick/main Sources [829kB]
Get:6 http://pr.archive.ubuntu.com maverick/restricted Sources [4,370B]
Get:7 http://pr.archive.ubuntu.com maverick/universe Sources [4,178kB]
Get:8 http://pr.archive.ubuntu.com maverick/multiverse Sources [151kB]         
Get:9 http://pr.archive.ubuntu.com maverick/main amd64 Packages [1,492kB]      
Get:10 http://pr.archive.ubuntu.com maverick/restricted amd64 Packages [6,002B]
Get:11 http://pr.archive.ubuntu.com maverick/universe amd64 Packages [5,771kB] 
Get:12 http://pr.archive.ubuntu.com maverick/multiverse amd64 Packages [180kB] 
Hit http://pr.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://pr.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://pr.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://pr.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://pr.archive.ubuntu.com maverick-updates/main amd64 Packages          
Hit http://pr.archive.ubuntu.com maverick-updates/restricted amd64 Packages    
Hit http://pr.archive.ubuntu.com maverick-updates/universe amd64 Packages      
Hit http://pr.archive.ubuntu.com maverick-updates/multiverse amd64 Packages    
Fetched 12.7MB in 26s (473kB/s)                                                
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by mc4man on 2010-10-07
see here to add the key or for the moment you can disable the 'extra' source in software sources. (i think it may be called 'Independent' in 'other software'  - don't have here - isn't added thru updates

(thought I saw an update that resolved this - may only apply to fresh installs after the update.

[http://ubuntuforums.org/showthread.php?p=9912525#post9912525](http://ubuntuforums.org/showthread.php?p=9912525#post9912525)

---

### Post by sendblink23 on 2010-10-07
> **mc4man said:**
> see here to add the key or for the moment you can disable the 'extra' source in software sources. (i think it may be called 'Independent' in 'other software'  - don't have here - isn't added thru updates

(thought I saw an update that resolved this - may only apply to fresh installs after the update.

[http://ubuntuforums.org/showthread.php?p=9912525#post9912525](http://ubuntuforums.org/showthread.php?p=9912525#post9912525)

Thank you, that post from that thread fixed it:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```

---

