---
title: "please help with flash player!!! I am a first time user."
date: 2009-10-17
forum: Multimedia Software
---

### Post by tayday on 2009-10-17
Hi, I am sooo stressed over this computer.. I have tried numerous times to download flash player.. when I download it in the terminal it says the plug in has been downloaded. i have tried to uninstall it and reinstall it but whenever I go to youtube and any other site that requires flash it still says I need it. I have shockwave, but when I went to about plugins it says i dont have flash player...pleaseee helpppp!

:(

---

### Post by norm7446 on 2009-10-17
Try this to download and install Flash.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

8-)

---

### Post by tayday on 2009-10-17
> **norm7446 said:**
> Try this to download and install Flash.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

8-)
  thanks, but I already have it installed..its like firefox is not recognizing it completely

---

### Post by kvarley on 2009-10-17
If you install it via the command below it will work with firefox. It's what I use everytime I do an install for somebody.

> sudo apt-get install flashplugin-nonfree

---

### Post by tayday on 2009-10-17
It says I already have the newest version.. I just don't understand why it firefox won't recognize it... could it maybe be firefox that's messed up? because when I play mpgs I only see a black screen and hear the audio.

---

### Post by kvarley on 2009-10-17
Right remove the flash stuff you installed.

Then once its clean, run the command below.
> 
sudo apt-get install flashplugin-nonfree

---

### Post by tayday on 2009-10-17
how do I remove it?

---

### Post by kvarley on 2009-10-17
How did you install flash?

---

### Post by tayday on 2009-10-17
in the terminal

---

### Post by lovinglinux on 2009-10-17
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by RedRat on 2009-10-17
Use nautilus or Thunar file manager. Make sure that you have "show hidden files" checked. Go to home/usrname/.mozilla and see if you have a folder called "plugins". There should be a file called "libflashplayer.so" in that folder.

If you do not have it, create the folder under .mozilla and then download the  flashplayer from Adobe and save it in some convienent folder. Open the downloaded deb or gz file and look for "libflashplayer.so". Drag and drop it to some convienent location. Then drag and drop it into the newly created "plugins" folder under .mozilla. 

needless to say, if you downloaded from Adobe the suitable plugin for your verison of Ubuntu, you ought to use that file for getting libflashplayer. 

I too was frustrated by this installation too. I tried both Synaptic and Adobe and none installed it correctly.

---

### Post by Xalor on 2009-10-17
```
sudo apt-get remove flashplugin-nonfree
```If that doesn't work properly you can switch remove with autoremove. 

I wouldn't install it from the terminal if it doesn't work the second time around. 

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Just download the Ubuntu .deb package there. Save it to the desktop and then double click the package, and follow the prompts.

---

### Post by tayday on 2009-10-17
thank you everyone who has tried to help!!

nothing works.. at all I have tried various ways to download it and it is in fact installed but its not being recognized I have noticed one thing though, and that's when I installed it in terminal it was saying that I was installing flash player 9 and whenever I removed it to install it again deb says that i still have a later version installed... I'm so confused and don't know what to do =/

---

### Post by lovinglinux on 2009-10-17
> **tayday said:**
> thank you everyone who has tried to help!!

nothing works.. at all I have tried various ways to download it and it is in fact installed but its not being recognized I have noticed one thing though, and that's when I installed it in terminal it was saying that I was installing flash player 9 and whenever I removed it to install it again deb says that i still have a later version installed... I'm so confused and don't know what to do =/

See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by lasleym on 2009-10-17
I had this problem too.  I went to Synaptic Package Manager (>system >synaptic package manager), search for flash.  Remove (uncheck) **EVERY** one that isn't Adobe.  

Once Adobe Flash (non-free) was the only one running, my flash (google maps street view) worked great everywhere.

---

### Post by Ronny50 on 2009-10-24
Hi,

I wanted to add something here...

truly a weird thing...

Last night, I booted off the 9.04 live disk, went to HULU and clicked on the download flash link.

Then install it while using the LIVE edition, all without a hitch!


Now today, I decided to install 9.04 and I can't get flash installed for anything!! It says, ERROR wrong architecture i386 ??
What happened?? 

I went through the same steps as when I was running the LIVE edition and NADA!
Then I found this thread and tried several things here and NADA!

Wow...

what can I do?

---

### Post by RedRat on 2009-10-25
> **Ronny50 said:**
> Hi,

I wanted to add something here...

truly a weird thing...

Last night, I booted off the 9.04 live disk, went to HULU and clicked on the download flash link.

Then install it while using the LIVE edition, all without a hitch!


Now today, I decided to install 9.04 and I can't get flash installed for anything!! It says, ERROR wrong architecture i386 ??
What happened?? 

I went through the same steps as when I was running the LIVE edition and NADA!
Then I found this thread and tried several things here and NADA!

Wow...

what can I do?

Check out this thread:
[HTML]http://ubuntuforums.org/showthread.php?p=8161871#post8161871[/HTML]

It has some suggestions that involve removing a package called "swfdec-Mozilla". I would read it carefully and see if it applies, but the person had some success.

---

### Post by mvalenti on 2009-10-25
mark@mark-laptop:~$ sudo apt-get install flashplugin-nonfree 
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@mark-laptop:~$ sudo apt-get remove flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 41.0kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 170116 files and directories currently installed.)
Removing flashplugin-nonfree ...
mark@mark-laptop:~$

---

### Post by help_needed on 2009-10-25
> **vitium said:**
> If you install it via the command below it will work with firefox. It's what I use everytime I do an install for somebody.
I tried this, and it can't find anything needed to install flash. How do i fix this?

---

### Post by help_needed on 2009-10-25
this is what happens if i try installing.

Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse flashplugin-nonfree 9.0.159.0ubuntu1~gutsy1
  404 Not Found [IP: 91.189.88.45 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse flashplugin-nonfree 9.0.159.0ubuntu1~gutsy1
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.159.0ubuntu1~gutsy1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.159.0ubuntu1~gutsy1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu-laptop:/home/dottenator# apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.45 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
  404 Not Found
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by RedRat on 2009-10-25
[help_needed]("http://ubuntuforums.org/member.php?u=937429"):
You appear to be running Gutsy, 7.10. It may well be that support for that older distro may be spotty at best. this appears to be the case since so many files are not found. Since you are new to this, I would suggest that install a much more up to date version of Ubuntu, the latest 9.10 will be released next week I believe. You can install the latest beta of that version or version 9.04. 

At the very least, I would suggest installing version 8.04 LTS (LTS = Long term support, which I think is about 4 years). the next long term support version is due out in April of  next year, i.e., 10.04. 

You will note that most giving advice here are all running 9.04 or 9.10 betas. I tend to be conservative and am running 8.04, it does have some limitations but it is supposed to be quite stable. If I were just starting out like you seem to be, I would perhaps wait until next week and try 9.10.

---

