---
title: "Need help installing cineraella"
date: 2008-05-20
forum: Multimedia Software
---

### Post by nerd0795 on 2008-05-20
I want to install cinerella and since I'm a ubuntu nub I just wanted some help.  

I used this guide:
[http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)
 
I am using ubuntu 8.04 and I am confused with a few steps.

I don't know what to do after

```
- Installations from this repository need an authentication key. Add it by typing in your terminal the following command:
wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```

When I finished that step it just says this:
```
OK
Hit http://repository.akirad.net akirad-hardy Release.gpg
Hit http://ca.archive.ubuntu.com hardy Release.gpg                             
Ign http://ca.archive.ubuntu.com hardy/main Translation-en_CA                  
Ign http://repository.akirad.net akirad-hardy/main Translation-en_CA 
Hit http://security.ubuntu.com hardy-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/main Translation-en_CA           
Ign http://ca.archive.ubuntu.com hardy/restricted Translation-en_CA            
Ign http://ca.archive.ubuntu.com hardy/universe Translation-en_CA              
Ign http://ca.archive.ubuntu.com hardy/multiverse Translation-en_CA            
Hit http://ca.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://ca.archive.ubuntu.com hardy-updates/main Translation-en_CA          
Ign http://ca.archive.ubuntu.com hardy-updates/restricted Translation-en_CA    
Ign http://ca.archive.ubuntu.com hardy-updates/universe Translation-en_CA      
Ign http://ca.archive.ubuntu.com hardy-updates/multiverse Translation-en_CA    
Hit http://ca.archive.ubuntu.com hardy Release                                 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_CA     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_CA
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com hardy-security Release                
Hit http://repository.akirad.net akirad-hardy Release                
Hit http://ca.archive.ubuntu.com hardy-updates Release             
Hit http://ca.archive.ubuntu.com hardy/main Packages                           
Hit http://ca.archive.ubuntu.com hardy/restricted Packages           
Hit http://ca.archive.ubuntu.com hardy/main Sources                  
Hit http://ca.archive.ubuntu.com hardy/restricted Sources            
Hit http://ca.archive.ubuntu.com hardy/universe Packages             
Hit http://security.ubuntu.com hardy-security/main Packages          
Hit http://repository.akirad.net akirad-hardy/main Packages          
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://ca.archive.ubuntu.com hardy/universe Sources
Hit http://ca.archive.ubuntu.com hardy/multiverse Packages
Hit http://ca.archive.ubuntu.com hardy/multiverse Sources
Hit http://ca.archive.ubuntu.com hardy-updates/main Packages
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://ca.archive.ubuntu.com hardy-updates/main Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://ca.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://ca.archive.ubuntu.com hardy-updates/universe Packages
Hit http://ca.archive.ubuntu.com hardy-updates/universe Sources
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://ca.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done

```

I don't know much about terminal though.

---

### Post by rocknrolf77 on 2008-05-20
Now you can just go to synaptic and install cinelerra :)

---

### Post by nerd0795 on 2008-05-20
Yay I got it installed thank you!

---

### Post by jerboyd on 2009-04-19
i haven't been able to get akirad working on jaunty. i'm using ubuntu studio and after installing akirad with the addakirad.deb package and updating apt i get a 404 not found error and none of the akirad packages are available to me. i've also tried manually adding the repo in sources.list but i get the same issue. are the mirrors just not up yet because jaunty still hasn't officially been released?

jeremy boyd

---

