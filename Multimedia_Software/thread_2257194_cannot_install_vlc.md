---
title: "cannot install vlc"
date: 2014-12-17
forum: Multimedia Software
---

### Post by jgw on 2014-12-17
I am running with ubuntu 14.10   I thought that I had vlc installed but when I checked it was not.  So I tried to install it and got:
The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.2.0~pre2-4build1) but 2.2.0~pre2-4build1 is to be installed
     Depends: libavcodec-extra-56 (>= 6:11~beta1) but 6:11-1 is to be installed
     Depends: libavutil54 (>= 6:11~beta1) but 6:11-1 is to be installed
     Depends: libc6 (>= 2.16) but 2.19-10ubuntu2.1 is to be installed
     Depends: libegl1-x11 but it is a virtual package
     Depends: libfreetype6 (>= 2.2.1) but 2.5.2-2ubuntu1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-16ubuntu6 is to be installed
     Depends: libgles1 but it is a virtual package
     Depends: libgles2 but it is a virtual package
     Depends: libpulse0 (>= 1:1.0) but 1:4.0-0ubuntu22 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1 is to be installed
     Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.6+git49-gbc62005+dfsg-1ubuntu1 is to be installed
     Depends: libstdc++6 (>= 4.9) but 4.9.1-16ubuntu6 is to be installed

I went to synaptic and tried to fix broken packages.  It said it did that but ended up with the same problems.  I also got an ubuntu error:"error submitting transactions" and the error was duly reported.  I would include the details but, after submitting the report an error froze.   I can keep on trying different things but, I fear, I can also REALLY screw things up if I keep dinking with this with some help.  When I tried to install vlc again, with synaptic it asked if I wanted to completely remove vlc or install it.  Since I had failed I told it to completely remove vlc,  It did that so I tried to reinstall and failed.

I have tried to install with synaptic and failed, I also tried to install from the Ubuntu software center with the same results.  I have also rebooted which didn't help with this one.

thank you.............

---

### Post by mc4man on 2014-12-17
There's nothing standing out in what you posted. Maybe try removing all of vlc & try again.
This will do - 
```
sudo apt-get purge vlc-data
```
Then ```
sudo apt-get update && sudo apt-get install vlc
```

---

### Post by ian-weisser on 2014-12-17
You are trying to install a version of VLC from a PPA or other non-Ubuntu source.
The non-ubuntu version has version conflicts with your Ubuntu software.
Example: libavutil54 version 6:11~beta1 is not in the Ubuntu repositories, but  version 6:11-1 is.
Those error messages are the version conflicts. It's apt telling you exactly what the problem is.


1) Remove all software from non-Ubuntu source.
```
sudo apt-get autoremove vlc
```

2) Disable the non-Ubuntu source.
Go to System Settings --> Software & Updates --> Other Software, and uncheck the offending source.
If you can't remember which non-Ubuntu source you added to get VLC, then disable them all.

3) Refresh your package database without the non-Ubuntu source.
```
sudo apt-get update
```

4) Test that your package manager is working properly now.
```
sudo apt-get upgrade
```

5) Install VLC fromthe Ubuntu repositories (the only remaining choice)
```
sudo apt-get install VLC
```

---

### Post by jgw on 2014-12-18
Thank you for the reply.

I have a problem, I think.  At the bottom is a recap of my commands as per the last reply.  Before that, however, I tried to run the update manager and was told that I could only do a partial system update.  I kept getting that and I did it three times.  Its dealing with the same thing, over and over.  In my update setup - other.  I have canonical (packages, no source), Independent (packages and source), no ppa or disabled on upgrade to utopic are checked.  (I fear I have a real mess)

Here are the results of my terminal commands:
greg@greg-N61PB-M2S:~$ sudo apt-get autoremove vlc
[sudo] password for greg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'vlc' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
greg@greg-N61PB-M2S:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic InRelease                   
Ign [http://archive.canonical.com](http://archive.canonical.com) utopic InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) utopic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release    
Hit [http://archive.canonical.com](http://archive.canonical.com) utopic Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security InRelease            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) utopic/partner amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates Release.gpg           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports Release.gpg         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main amd64 Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) utopic/partner i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main i386 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) utopic/partner Translation-en                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/main amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/multiverse amd64 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/main i386 Packages          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/multiverse i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/main amd64 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/restricted amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/multiverse amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-backports/universe Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/main amd64 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/restricted amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/universe amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/multiverse amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) utopic-security/universe Translation-en       
Reading package lists... Done                                                  
greg@greg-N61PB-M2S:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-cirrus xserver-xorg-video-fbdev
  xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-s3
  xserver-xorg-video-savage xserver-xorg-video-siliconmotion
  xserver-xorg-video-tdfx xserver-xorg-video-vesa
0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.
greg@greg-N61PB-M2S:~$ sudo apt-get install VLC
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: libgles1-mesa (>= 7.8.1) but it is not going to be installed or
                libgles1
E: Unable to correct problems, you have held broken packages.

---

### Post by ian-weisser on 2014-12-18
Find out why that specific dependency cannot be installed:
```
sudo apt-get install libgles1-mesa
```

Partial upgrades are often a bad sign - usually means you have installed non-Ubuntu packages from someplace out in the wild, and it's causing problems.
Good practice is to reject partial upgrades, uninstall ALL non-Ubuntu software, and try upgrading again. After the upgrade completes successfully, you can reinstall you non-Ubuntu software.

---

### Post by j0sk on 2014-12-18
Be sure that you haven't enabled **proposed** repository. It may be reason for dependency issues.

---

### Post by jgw on 2014-12-18
thank you for the replies.  I have no idea where to find "proposed repository" (its in the update manager?)  I also keep wondering, should I leave all those repositories, in setup - other, that were disabled on update to utopic.  I have 3 ubuntu machines.  I noticed that on one I left all those disabled unchecked but checked all the other ppa stuff. Anything I have installed, on any of my machines, either came from the ubuntu software center or synaptic.  As far as I know those are good sources.  I also don't know what "The following packages have been kept back:" means.  I do know, when I tried to remove vlc (told me there was no vlc installed) and then install, that it gave me the name of what is was missing (there was only 1 thing).  I neglected to save that (apologies)

Anyway, I will make a run at your suggestion in the next hour or so - thanks again!

---

### Post by mc4man on 2014-12-18
A couple of things - 
At the  risk of being redundant if one wants to completely remove vlc then  'apt-get remove vlc' or 'apt-get autoremove vlc' is** Not **going to get the job done. As I mentioned before purging vlc-data will remove **all** the vlc packages commonly installed.

Please run this & post results - 
```
apt-cache policy libgles1-mesa
```

---

### Post by jgw on 2014-12-18
greg@greg-N61PB-M2S:~$ apt-cache policy libgles1-mesa
libgles1-mesa:
  Installed: (none)
  Candidate: 10.3.0-0ubuntu3
  Version table:
     10.3.0-0ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
greg@greg-N61PB-M2S:~$

---

### Post by mc4man on 2014-12-18
> **jgw said:**
> greg@greg-N61PB-M2S:~$ apt-cache policy libgles1-mesa
libgles1-mesa:
  Installed: (none)
  Candidate: 10.3.0-0ubuntu3
  Version table:
     10.3.0-0ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/main amd64 Packages
greg@greg-N61PB-M2S:~$
Maybe we can see why it won't install (there is a newer mesa in utopic -proposed, you may have gotten some of already & if so may be a  block on the libgles1-mesa package avail.
This is just a simulation, post results
```
sudo apt-get -s install libgles1-mesa
```

---

### Post by ian-weisser on 2014-12-19
> **jgw said:**
> I have no idea where to find "proposed repository" (its in the update manager?)

Not Update Manager.
System Settings --> Software & Updates --> Updates (tab).

> **jgw said:**
> Anything I have installed, on any of my machines, either came from the ubuntu software center or synaptic.  As far as I know those are good sources. 

Not quite.
Software Center and Synaptic are not sources. They show you the packages available from good and bad sources.
You choose the those sources in System Settings --> Software & Update

The Debian package system isn't a walled garden. You can add ANY source you wish, even if it's foolish or dangerous to do so. The package system is not psychic, and cannot predict the results of poor source choices. The default install of Ubuntu has good, tested, supported sources. But, as you have  discovered, adding sources that break your system is easy to do.

When you add a lousy source for software that will break your system, Software Center and Synaptic will happily use it and help you install packages from it. The applications are designed to do your will, not to protect you. Your protection comes from choosing your sources wisely...and from the support community to help you undo a poor choice of source.

---

### Post by jgw on 2014-12-19
Here is the result of your suggestion.  I should add that I went to synaptic and clicked on "fix broken packages" - it said it fixed them (I am always told that, by that program - seems it too is confused <g>)

This is a a bit strange.  I also have another topic and it too seems to be having problems with installations although that one is on a different computer.   Here is a link: [http://ubuntuforums.org/showthread.php?t=2257311](http://ubuntuforums.org/showthread.php?t=2257311) in case you might want to take a look.

I have posted a picture of my other software so that you can see what I have checked and what is not checked.  You can see this at [https://drive.google.com/file/d/0B6pBQ549bl3WNlliMFpaUUdjc3c/view?usp=sharing](https://drive.google.com/file/d/0B6pBQ549bl3WNlliMFpaUUdjc3c/view?usp=sharing)     I would have attached it but, for some strange reason I cannot find the attachment thing that this site uses for such.

---

### Post by mc4man on 2014-12-19
Pretty simple - 
There are more than a few ppa's that need to be 'purged' back to ubuntu package versions** before **upgrading using ppa-purge. 
xorger's happens to be one of them.
So you can - 
1. do a fresh install
2. figure out all the ppa packages you have from xorger's, collect the repo packages for 14.10 & 'downgrade' them all at once with dpkg
3. Add the xorger's ppa for utopic, update your sources, & do a dist-upgrade. This is much easier than option 2 & preferred method to resolve.
After adding back xorgers, ect. if you don't want to keep their packages then do ppa-purge on the ppa.

guess I could of rememberer as this has come up recently, ex. - 
[http://ubuntuforums.org/showthread.php?t=2254168](http://ubuntuforums.org/showthread.php?t=2254168)
(- but then again you could of mentioned that you were it using prior to upgrade & that you had done an upgrade vs. fresh install in the first place...

---

### Post by jgw on 2014-12-19
thank you........

I am now, however, completely at sea.  

I think this is what I am supposed to do:
3. Add the xorger's ppa for utopic, update your sources, & do a dist-upgrade. This is much easier than option 2 & preferred method to resolve.
After adding back xorgers, ect. if you don't want to keep their packages then do ppa-purge on the ppa.

I am incredibly ignorant about this stuff.  first I am supposed to add the xorger's ppa for utopic - HOW?  Should this be done before stuff is deleted or purged?

I only can see two xorg entries - both of which are xorg-edgers.  I can do this? (found in the link you supplied)
To install the ppa-purge package:
Code: sudo apt-get update && sudo apt-get install ppa-purge
To use against xorg-edgers:
Code: sudo ppa-purge ppa:xorg-edgers/ppa

I have no idea howto do a dist update or what that does.  (did some reading - sudo apt-get dist-upgrade?)

I just pressed ^f, entered "xorg" (just seeing where they were, I pressed enter and it deleted one, I think (it was quick)
Anyway, from what you have said, I need to do more than just start deleting stuff from software and updates.  there are also all those that were disabled on update to utopic.  Should those too be purged?

Anyway, I, obviously, am clueless.  I had no idea that I was supposed to remove stuff before I updated and still am having problems understanding.  My thought is to purge, or delete, everything in other software that is unchecked.  My belief that if its unchecked its no being used, makes me think that.  If this is true then I would appreciate it if you could tell me how I should do that properly.  Once that is done then I should do a dist upgrade which should, in theory, get rid of anything it found that is not necessary and remove it and update all dependencies, and install any necessary that are not there?   Am I getting close?

I really do appreciate your help and time spent and apologize for my ignorance.  I am, however, trying.  I also wonder, was there documentation I missed, when I updated to 14.10?  I made an assumption that all that was needed was to push the upgrade button, obviously a bad assumption.  I have three of these machines, and upgraded them all.  Two are now showing problems and I suspect they are all related.  This machine is my tv & download machine, another I use for programming, the third is extra and also used for backup.

---

### Post by mc4man on 2014-12-19
Don't worry about it.. though you may have a little mess because you used 2 x-swat ppa's in trusty & only 1 has utopic packages
If you haven't added the 1 ppa back - (xorg-edgers), then run this
```
sudo add-apt-repository ppa:xorg-edgers/ppa
```
Then update your sources - 
```
sudo apt-get update
``` 
Then simulate a dist-upgrade, post the results
```
sudo apt-get -s dist-upgrade
```

(- as far as not purging the ppa(s) before upgrading - 
In this case at least one of the ppa's was missing the warning about purging the ppa before upgrading to a new release, it was inadvertantly removed from the ppa main page. That should be rectified shortly.

In general whenever you add a ppa read the description in the terminal or better yet go to the ppa's page.

---

### Post by jgw on 2014-12-20
Thanks again............

I did as you asked.  Instead of cluttering I put it all on pastebin - [https://pastebin.com/uruFyJcN](https://pastebin.com/uruFyJcN)

---

### Post by mc4man on 2014-12-20
That looks ok so go ahead & run the upgrade for real - 
```
sudo apt-get dist-upgrade
```

When the above is done then try to install vlc again, let's see what happens
```
sudo apt-get install vlc
```

If that all works out then you can decide if you want to stay with the  xorg-edgers ppa or downgrade with ppa-purge to 14.10 versions
(- I see nothing wrong with using the ppa, maybe give it a test out & see. If keeping just remember to downgrade with ppa-purge before you upgrade to 15.04 down the road. Or if you forget then you'll just add back, ect. afterwards.

---

### Post by jgw on 2014-12-20
I did that stuff - results are in [http://pastebin.com/7JFWVEmm](http://pastebin.com/7JFWVEmm).

Now, I have two other machines with, I suspect, the same problems.  Given what we have done I suspect I should:
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade

then, on all machines:   sudo apt-get install ppa-purge 
to be ready for the next update?  I guess this will be run against the xorg-edgers (if there are any)?

Actually my main problem with one other machine (the other, apparently, is fine) is that I have lost "startup applications".  Since I have NO xorg's at all in my other softwae how about just doing the last two (update and upgrade)?

---

### Post by mc4man on 2014-12-20
> **jgw said:**
> I did that stuff - results are in [http://pastebin.com/7JFWVEmm](http://pastebin.com/7JFWVEmm).

Now, I have two other machines with, I suspect, the same problems.  Given what we have done I suspect I should:
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get dist-upgrade

then, on all machines:   sudo apt-get install ppa-purge 
to be ready for the next update?  I guess this will be run against the xorg-edgers (if there are any)?

Well if you decide to keep & use xorg-edgers **now in 14.10** then it doesn't really matter when you install ppa-purge but you can install now if you wish.
When the day comes that you want to upgrade to 15.04, then run ppa-purge  as noted in the ppa page, ie. 

sudo ppa-purge xorg-edgers

 If you don't want the xorgers package versions right now then install & run the ppa-purge command
(I'd give it a test as you're getting fresher source packages.

---

### Post by mc4man on 2014-12-20
In regards to the other machine ( no startup app), I didn't realize it was a different machine. Seems an odd issue so go ahead & update it & post **in that thread** the results of this - 
```
echo $DESKTOP_SESSION
```

---

