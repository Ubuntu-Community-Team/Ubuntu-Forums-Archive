---
title: "Aircrack Issues"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by riQeh on 2010-01-31
Hello.

I have a new Ubuntu 9.10 install on my HP G60 laptop. Everything working perfectly (thanks for help on a previous thread).

I am new to linux, and am enjoying learning about my new OS.

I am now trying to follow a tutorial: [http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/)

But i am experiencing a few problems. Maybe this is an out of date tutorial, or maybe i'm doin something wrong.

But when i type:
sudo gedit /etc/apt/sources.list

and change it to:[INDENT]## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
 ## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
 ## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
 ## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
 ## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
[/INDENT]i then type: 
sudo apt-get update


i get: 

Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Translation-en_GB                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Translation-en_GB              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Translation-en_GB                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Translation-en_GB              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Translation-en_GB            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Translation-en_GB        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Translation-en_GB      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Translation-en_GB          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Translation-en_GB    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Translation-en_GB    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources              
93% [Connecting to packages.freecontrib.org (34.52.53.34)]                     
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg    
  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Translation-en_GB
  Unable to connect to packages.freecontrib.org http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Translation-en_GB
  Unable to connect to packages.freecontrib.org http:
Reading package lists... Done                             
W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_GB.bz2)  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

Now i know it seems very early in the tutorial to get stuck, so there may be many more threads, after i get this solution.. Any ideas people??

Thanks in advance..

---

### Post by abyrne on 2010-01-31
Ok. Well first of all, that is an outdated tutorial. second, you screwed up your apt sources badly. Why? because now your getting packages from an outdated ubuntu repository (ur getting dapper packages instead of karmic packages). Third, it looks like half of that site that you got the tutorial from is down. so the repos it gave you are probably down too. 

Solution
Try to restore your package sources. ( you'll have to find a clean one for karmic somewhere on the web)
Get a new tutorial.

Correct me if im wrong.

PS: ive tried doing that WEP hack thing before. maybe it was just me, but it just didnt want to work for me. Good luck

---

### Post by mongr31 on 2010-01-31
WEP hacking is really easy, why don't you just use the official documentation from aircrack-ng?

[http://www.aircrack-ng.org/doku.php?id=tutorial&DokuWiki=a24314ca49eacef9adb3ac58a308de1c](http://www.aircrack-ng.org/doku.php?id=tutorial&DokuWiki=a24314ca49eacef9adb3ac58a308de1c)

---

### Post by pdc on 2010-01-31
maybe post this anew on the Absolute Beginners Forum; maybe a kindly soul can just help you rebuild the sources you need

---

### Post by mongr31 on 2010-01-31
Here's a basic one for you:

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://us.archive.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu karmic partner
```

[http://go2.wordpress.com/?id=725X1342&site=ubuntulady.wordpress.com&url=http%3A%2F%2Frepogen.simplylinux.ch%2F](http://go2.wordpress.com/?id=725X1342&site=ubuntulady.wordpress.com&url=http%3A%2F%2Frepogen.simplylinux.ch%2F)

---

### Post by riQeh on 2010-01-31
i did actually backup my original sources.list

So thank you for that. I did encounter (obviously) lots of problems using the modified sources.list.

Anyway i'm off to read the Aircrack documentation.. 

Cheers..

---

