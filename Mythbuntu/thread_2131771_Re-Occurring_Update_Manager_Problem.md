---
title: "Re-Occurring Update Manager Problem"
date: 2013-04-02
forum: Mythbuntu
---

### Post by gga96 on 2013-04-02
It was suspected that a similar event involving samba may have been responsible for corruption reported in my previous post "Get DVD operating in Myth frontend ?".

Whilst running Update Manager today the following (partial) output reported an error: 
> 
Unknown parameter encountered: "force user" 
Ignoring unknown parameter "force user" 
Unknown parameter encountered: "force group" 
Ignoring unknown parameter "force group" 
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied 
dpkg: error processing samba4 (--configure):  subprocess installed post-installation script returned error exit status 126 


On this occasion nothing seems to be corrupted, however I would still like to know why samba hiccuped and the fix?

Any ideas gratefully received.

---

### Post by schragge on 2013-04-03
Login on a text console (e.g. **Ctrl**+**Alt**+**F1**), and try to reconfigure Samba:
```
sudo dpkg-reconfigure samba4
```

---

### Post by gga96 on 2013-04-03
Thanks schragge.

I followed your instructions and the response was "dpkg: error: need an action option".  Samba was installed by Control Centre>Services and being  new to linux I do not know the answer to correct the error.

Glen

---

### Post by schragge on 2013-04-03
Looks like you've put a space between *dpkg* and *-reconfigure* thus the error message. *dpkg-reconfigure* is _one_ command word. Please try it again.
```
sudo dpkg-reconfigure samba4
```

---

### Post by gga96 on 2013-04-03
Thank you results:
> 
glen@glen-mythtv:~$ sudo dpkg-reconfigure samba4
[sudo] password for glen: 
/usr/sbin/dpkg-reconfigure: samba4 is broken or not fully installed

What do you think is the best way to proceed.

---

### Post by schragge on 2013-04-04
Well, try to remove *samba4*, then re-install it:
```
sudo dpkg --force-remove-reinstreq -r samba4
sudo apt-get clean
sudo apt-get update
sudo apt-get install samba4

```

---

### Post by gga96 on 2013-04-04
Because the backend desktop is now not operating as it should as a result of the samba4 error, I have now "Mythbuntu Software Centre">"Removed" samba4 . Then followed up with with a samba4 "Install". No errors reported, but the desktop is still a mess. 

I hope the desktop can be repaired before I have to re-install the lot.

---

### Post by gga96 on 2013-04-04
Hi schragge.
You must have posted when I was completing my previou post.

I have tried to use the terminal with the instructions from your last post but the terminal will not accept focus or keyboard input.
The desktop is a shambles:
-loss of window focus
-intermitand mouse with X as the mouse cursor at times...
-no window menu access by keyboard or mouse.
-no window x_[] icons.
-new window placed at 0,0 witch meens covered by horizontal "Applications" bar (move to vertical now)
- ...

Is it posible to repair the desktop?
Glen

---

### Post by schragge on 2013-04-04
Hmm, the desktop was okey before you removed Samba? Anyway, six virtual text consoles should be accessible by pressing **Ctrl**+**Alt**+**F1** through **Ctrl**+**Alt**+**F6**. Try
```
sudo dpkg-reconfigure x11-common
``` from there.

---

### Post by gga96 on 2013-04-04
Tried above:
Response is a note followed by 3 choices of who should do it:
 -Root Only
-Console Users Only
-Anybody
I have answered all 3 in turn which takes focus to screen bottom line with [EMAIL="glen@....~$"]glen@....~$[/EMAIL] where I re-entered the command and  that loops back to the 3 questions.
Glen

---

### Post by schragge on 2013-04-04
Press **Ctrl**+**Alt**+**F7** to return back to graphical screen. TBH, I have no idea what's going on with your desktop.

---

### Post by gga96 on 2013-04-04
I dont know either!

The first case of corruption occured some weeks ago, invoked when I ran Update Manager and the error involved samba4 being denied permission. I could get no were with it and eventually re-installed the system from scratch.

The exact same corruption happened again. re-installed again.

When it happened a 3rd time I re-installed I started post "Vanilla Mythbuntu expanded to multi Frontends" this led to a sucsessful conclution about 5 daya ago.

Started this post to warn others but the next day boot resulted in desktop corruption once again.

After a couple reboots tonight I have got a clean Terminal and repeated the remove and re-install of sambs4 the result follows
> 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_AU
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
Fetched 467 kB in 1min 27s (5,352 B/s)
Reading package lists... Done
W:  GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release: The following  signatures couldn't be verified because the public key is not  available: NO_PUBKEY 2EBC26B60C5A2783


There has to be some cause is this it ?
Glen

---

### Post by schragge on 2013-04-04
Check that package *medibuntu-keyring* is installed
```
dpkg -l medibuntu-keyring
```
If yes, run
```

sudo rm -frv /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-key update
sudo apt-get update

```
Otherwise, run
```

sudo apt-get --allow-unauthenticated install medibuntu-keyring
sudo apt-get update

```

---

### Post by gga96 on 2013-04-04
Good morning.

Result of your last post was negative followed by else commands as follows;
> 
len@glen-mythtv:~$ dpkg -l medibuntu-keyring
No packages found matching medibuntu-keyring.
glen@glen-mythtv:~$ sudo apt-get --allow-unauthenticated install medibuntu-keyring
[sudo] password for glen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,448 B of archives.
After this operation, 49.2 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Get:1 [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise/free medibuntu-keyring all 2008.04.20 [3,448 B]
Fetched 3,448 B in 2s (1,499 B/s)              
Selecting previously unselected package medibuntu-keyring.
(Reading database ... 137846 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK
glen@glen-mythtv:~$ sudo apt-get update
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg [198 B]                
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release                              
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [65.1 kB]       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B] 
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [24.0 kB]   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,380 B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [245 kB]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [73.0 kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [114 kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [44.9 kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release.gpg                           
Get:18 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates Release.gpg [198 B]        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release                               
Get:19 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates Release [49.6 kB]          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Sources                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe TranslationIndex             
Get:20 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Sources [374 kB]      
Get:21 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Sources [5,494 B]
Get:22 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe Sources [83.4 kB] 
Get:23 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Sources [4,746 B]
Get:24 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main i386 Packages [603 kB]
Get:25 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.1 kB]
Get:26 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe i386 Packages [194 kB]
Get:27 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse i386 Packages [10.4 kB]
Get:28 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:29 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:30 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:31 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Translation-en_AU                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Translation-en_AU          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Translation-en_AU          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Translation-en_AU        
Get:32 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Translation-en [266 kB]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Translation-en_AU  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Translation-en_AU  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Translation-en     
Get:33 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe Translation-en [113 kB]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports/universe Translation-en     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_AU               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_AU
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
Fetched 2,351 kB in 1min 2s (37.7 kB/s)
Reading package lists... Done
glen@glen-mythtv:~$ 


The system then opend an Update Manager with no mention of samba but the mention of Firefox, ffmpeg, libav-tools, libavcodec53, libavdevice53, libavfilter2, libavformat53, libavutil51, pibpostproc52, libswcale2.
I decided to "Install Updates". Clean execution.

I now question if I should do the yes case from your last post?
Glen

---

### Post by schragge on 2013-04-05
No, you shouldn't. It was for the case the GPG error had been caused by corruption of a file containing the GPG key for Medibuntu. In your case, the key simply hasn't been installed.

---

### Post by gga96 on 2013-04-05
Hi,
Any other ideas?

---

### Post by schragge on 2013-04-05
What ideas? If that was not clear, the problem with medibuntu is fixed by now. I hope your samba4 problem also got fixed in the process. As to your desktop corruption, I don't know how to fix it, sorry.

---

### Post by gga96 on 2013-04-05
Thank you for your help schragge.
The desktop is still corrupt.
 I will now re-install or try Control Centre>Sytem Roles>Desktop Role>Ubuntu Desctop.

---

### Post by gga96 on 2013-04-05
Tried Control Centre>Sytem Roles>Desktop Role>Ubuntu Desctop and some things improved.

Some desktop corruption items are:
-no z order with focus window coming to the top
-no caret in gedit
-no window sizing.

Myth backend and front seem to be working normally.
I am very reluctant to re-install again.

I hope some one may know how to repair the desktop interface.
Any ideas gratefully received.
Glen

---

