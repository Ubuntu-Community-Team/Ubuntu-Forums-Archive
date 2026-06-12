---
title: "vlc media player installation issue Package Dependencies cannot be resolved"
date: 2015-04-18
forum: Multimedia Software
---

### Post by ljm2 on 2015-04-18
[SIZE=2]I have tried installing vlc without success, always receiving this message:[/SIZE]

```

The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.1.6-0ubuntu14.04.1) but 2.1.6-0ubuntu14.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.19-0ubuntu6.6 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.5.2-1ubuntu2.4 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
     Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.8.2-19ubuntu1 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
```

[SIZE=2]I have run *sudo apt-get clean *and *sudo apt-get auto clean* with no success. I am new to ubuntu and wish to resolve this issue. Thanks.[/SIZE]

---

### Post by mc4man on 2015-04-18
Well let's take a quick look, run both, post results -  (put separately  in quote boxes, ie. highlight the text in your reply, click on the little quote icon in toolbar
```
sudo apt-get update
```
```
apt-cache policy vlc vlc-nox vlc-data libvlccore*
```

---

### Post by ljm2 on 2015-04-19
After running *sudo apt-get update* I got the following:

```
Ign [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty InRelease
Ign [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates InRelease                           
Ign [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security InRelease                          
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty Release.gpg 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease  
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Get:1 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates Release.gpg [933 B]
Get:2 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security Release.gpg [933 B]              
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release     
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                        
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty Release                             
Get:4 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates Release [63,5 kB]                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Get:5 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security Release [63,5 kB]                
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/main Sources                               
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/restricted Sources              
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/universe Sources                
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/multiverse Sources             
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/main amd64 Packages                         
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/restricted amd64 Packages                   
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/universe amd64 Packages                     
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/multiverse amd64 Packages                   
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/restricted i386 Packages                    
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/universe i386 Packages                      
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/multiverse i386 Packages                    
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/main Translation-en                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/multiverse Translation-en                   
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/restricted Translation-en                   
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/universe Translation-en                     
Get:6 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/main Sources [194 kB]             
Get:7 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/universe Sources [112 kB]         
Get:8 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/restricted Sources [2.564 B]      
Get:9 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/multiverse Sources [4.775 B]      
Get:10 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/main amd64 Packages [502 kB]     
Get:11 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/restricted amd64 Packages [9.238 B]
Get:12 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/universe amd64 Packages [269 kB] 
Get:13 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/multiverse amd64 Packages [11,7 kB]
Get:14 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/main i386 Packages [491 kB]      
Get:15 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/restricted i386 Packages [9.256 B]
Get:16 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/universe i386 Packages [270 kB]  
Get:17 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/multiverse i386 Packages [11,9 kB]
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/main Translation-en                 
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/multiverse Translation-en           
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/restricted Translation-en           
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-updates/universe Translation-en             
Get:18 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/main Sources [78,4 kB]          
Get:19 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/universe Sources [20,3 kB]      
Get:20 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/restricted Sources [2.061 B]    
Get:21 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/multiverse Sources [1.922 B]    
Get:22 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/main amd64 Packages [258 kB]    
Get:23 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/restricted amd64 Packages [8.875 B]
Get:24 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/universe amd64 Packages [95,9 kB]
Get:25 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/multiverse amd64 Packages [3.451 B]
Get:26 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/main i386 Packages [248 kB]     
Get:27 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/restricted i386 Packages [8.846 B]
Get:28 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/universe i386 Packages [95,9 kB]
Get:29 [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/multiverse i386 Packages [3.643 B]
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/main Translation-en                
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/multiverse Translation-en          
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/restricted Translation-en          
Hit [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty-security/universe Translation-en            
Ign [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/main Translation-en_US                      
Ign [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/multiverse Translation-en_US                
Ign [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/restricted Translation-en_US                
Ign [http://ftp.tecnoera.com](http://ftp.tecnoera.com) trusty/universe Translation-en_US                  
Fetched 2.841 kB in 55s (51,2 kB/s)                                            
Reading package lists... Done
```

And now after running *apt-cache policy vlc vlc-nox vlc-data libvlccore**
 ```

vlc:
  Installed: (none)
  Candidate: 2.1.6-0ubuntu14.04.1
  Version table:
     2.1.6-0ubuntu14.04.1 0
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty-updates/universe amd64 Packages
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty-security/universe amd64 Packages
     2.1.2-2build2 0
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty/universe amd64 Packages
vlc-nox:
  Installed: (none)
  Candidate: 2.1.6-0ubuntu14.04.1
  Version table:
     2.1.6-0ubuntu14.04.1 0
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty-updates/universe amd64 Packages
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty-security/universe amd64 Packages
     2.1.2-2build2 0
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty/universe amd64 Packages
vlc-data:
  Installed: (none)
  Candidate: 2.1.6-0ubuntu14.04.1
  Version table:
     2.1.6-0ubuntu14.04.1 0
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty-updates/universe amd64 Packages
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.1.2-2build2 0
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty/universe amd64 Packages
libvlccore7:
  Installed: (none)
  Candidate: 2.1.6-0ubuntu14.04.1
  Version table:
     2.1.6-0ubuntu14.04.1 0
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty-updates/universe amd64 Packages
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.1.2-2build2 0
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty/universe amd64 Packages
libvlccore-dev:
  Installed: (none)
  Candidate: 2.1.6-0ubuntu14.04.1
  Version table:
     2.1.6-0ubuntu14.04.1 0
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty-updates/universe amd64 Packages
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty-security/universe amd64 Packages
     2.1.2-2build2 0
        500 [http://ftp.tecnoera.com/ubuntu/](http://ftp.tecnoera.com/ubuntu/) trusty/universe amd64 Packages
```

---

### Post by mc4man on 2015-04-20
Try to install again, - 
```
sudo apt-get install vlc
```
If that doesn't work then open up -
```
software-properties-gtk
```
In the "Download from:" dropdown pick Main server, close, click Reload button  & then  try again

---

### Post by ljm2 on 2015-04-20
I ran recommended codes and got this:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.1.6-0ubuntu14.04.1) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.1.6-0ubuntu14.04.1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.1.6-0ubuntu14.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by dino99 on 2015-04-20
external sources:
[http://www.videolan.org/news.html](http://www.videolan.org/news.html)
[https://launchpad.net/~videolan/+archive/ubuntu/stable-daily](https://launchpad.net/~videolan/+archive/ubuntu/stable-daily) (select 'trusty' indeed)

---

### Post by mc4man on 2015-04-20
Weird, did you change to the main server from ftp.tecnoera.com?
Anyway it could be vlc-nox that's the problem (vlc comprises several packages, vlc-nox has most of the dependencies

Try this to see if informative - 
```
sudo apt-get install vlc-nox
```
If nothing shows up useful then install aptitude & use it, should be more verbose
```
sudo apt-get install aptitude
```
then 
```
sudo aptitude install vlc
```

---

### Post by ljm2 on 2015-04-20
Yes, I did change to the main server.  After running > sudo apt-get install aptitude and then > sudo aptitude install vlc  vlc installed successfully and runs fine. Thank you very much for you help. Have a great week

---

