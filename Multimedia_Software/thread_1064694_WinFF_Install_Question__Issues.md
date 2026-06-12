---
title: "WinFF Install Question / Issues"
date: 2009-02-09
forum: Multimedia Software
---

### Post by martied on 2009-02-09
Hi guys,

I am newish to Ubuntu. I have used it before and had it running side by side with windows. But now looking for Ubuntu only dekstops.

I have installed and checked FFMpeg and codecs. But now trying to install winff in synaptic and getting messages about 

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

I added the download location and also the key but still no go.

Any help would be great

Thanks 

Marty

---

### Post by martied on 2009-02-09
I have tried this and I get this error.

marty@MartyServer:~$ echo "deb [http://winff.org/ubuntu](http://winff.org/ubuntu) intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list
[sudo] password for marty: 
deb [http://winff.org/ubuntu](http://winff.org/ubuntu) intrepid universe
marty@MartyServer:~$ wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add - && sudo apt-get update
OK
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_AU 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_AU
Hit [http://winff.org](http://winff.org) intrepid Release.gpg                            
Ign [http://winff.org](http://winff.org) intrepid/unive Translation-en_AU                
Ign [http://winff.org](http://winff.org) intrepid/universe Translation-en_AU
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Translation-en_AU
Hit [http://winff.org](http://winff.org) intrepid Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-security/multiverse Sources
W: Failed to fetch [http://winff.org/ubuntu/dists/intrepid/Release](http://winff.org/ubuntu/dists/intrepid/Release)  Unable to find expected entry  unive/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
marty@MartyServer:~$ sudo apt-get install avidemux ffmpeg winff
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
E: Couldn't find package winff
marty@MartyServer:~$

---

### Post by paul.gevers on 2009-02-10
Can you please provide the content of /etc/apt/sources.list.d/winff.list (for instance by running "cat /etc/apt/sources.list.d/winff.list") It looks like there is an error in that file (unive instead of universe).

Paul

---

### Post by martied on 2009-02-11
Hi,

Thanks for getting back to me :)

That is what I get..


marty@MartyServer:~$ cat /etc/apt/sources.list.d/winff.list
deb [http://winff.org/ubuntu](http://winff.org/ubuntu) intrepid universe
marty@MartyServer:~$

---

### Post by martied on 2009-02-11
Yelp

that was it, there was 2 x entries in the file. Removed incorrect line and re run and all good 

Appreciate your help and pointing that out for me

:)

---

