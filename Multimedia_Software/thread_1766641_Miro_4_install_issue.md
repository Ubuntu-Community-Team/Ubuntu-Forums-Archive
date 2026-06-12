---
title: "Miro 4 install issue"
date: 2011-05-24
forum: Multimedia Software
---

### Post by inof8or on 2011-05-24
I have been trying to install Miro 4 but when I add the ppa and do the update it gives me a 404 cant connect error. 

Anyone else having the same issues? Im using Natty, are they currently doing a Natty build, it does't look it?

Can't wait to see the new changes in 4!

---

### Post by beew on 2011-05-24
> **inof8or said:**
> I have been trying to install Miro 4 but when I add the ppa and do the update it gives me a 404 cant connect error. 

Anyone else having the same issues? Im using Natty, are they currently doing a Natty build, it does't look it?

Can't wait to see the new changes in 4!


??? Which ppa? PCF Miro's ppa only has version 3.5.1 and it works only up to Maverick (and has not been updated since Feb14)

---

### Post by tomfoley on 2011-05-25
I too have the same issue. On opening Miro 3.5.1 I'm asked to upgrade to Miro 4.0 and am taken to the page [http://www.getmiro.com/download/for-ubuntu/](http://www.getmiro.com/download/for-ubuntu/)

Following the instructions on that page I added the source ppa:pcf/miro-releases.

Then, running a sudo apt-get update I receive a 404 for these two packages...

[http://ppa.launchpad.net/pcf/miro-releases/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/pcf/miro-releases/ubuntu/dists/natty/main/source/Sources)

[http://ppa.launchpad.net/pcf/miro-releases/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/pcf/miro-releases/ubuntu/dists/natty/main/binary-i386/Packages)

It looks like the error is on Miro's side.

---

### Post by JebusWankel on 2011-05-26
I just checked and it looks like that PPA just added support for Natty literally 3 hours ago.

For the record that means you can install Miro 4 with the following
```
sudo apt-add-repository ppa:pcf/miro-release
sudo apt-get update
```
then either
```
sudo apt-get upgrade
```
if you already have Miro installed, else click here
[**Install Miro**]("apt:miro")

Update: Having done the above, it looks like all the bugs aren't quite worked out. Consider yourself warned.

---

### Post by tomfoley on 2011-05-26
Hi JebusWankel,

Your proposed solution is a disaster. More errors than originally produced.

I appreciate your willingness to assist, but for Pete's sake, stay away with your untested notions.

---

### Post by beew on 2011-05-26
> **tomfoley said:**
> Hi JebusWankel,

Your proposed solution is a disaster. More errors than originally produced.

I appreciate your willingness to assist, but for Pete's sake, stay away with your untested notions.

What errors? He just says to upgrade from Miro's ppa, nothing unusual. I have upgraded to Miro 4 on Ubuntu 10.10 and it seems to work fine.

---

### Post by beew on 2011-05-26
Just upgraded to Miro 4.01 in 11.04 using ppa, it is working great as far as I can tell.

---

### Post by michael.yahav on 2011-05-30
There is type error it should be written this way:

sudo add-apt-repository ppa:pcf/miro-releases
sudo apt-get update
sudo apt-get install miro

---

### Post by mtotowajirani on 2011-06-08
I get the same error 404 error after installing it using:

> sudo add-apt-repository ppa:pcf/miro-releases sudo apt-get update sudo apt-get install miroThis is the error I get. Please help:

> 
admin@mothership:~$ sudo apt-get update
[sudo] password for admin: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
W: Failed to fetch [http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/pcf/miro-release/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
admin@mothership:~$ 



---

