---
title: "Help Choosing What Version of Ubuntu to use"
date: 2009-07-01
forum: Multimedia Software
---

### Post by The Avatar of Time on 2009-07-01
Hello all,

I've been running Arch Linux for quite some time but I'm planning to try K/Ubuntu (not sure which) again. 

What I am trying to decide is what K/Ubuntu version to install. At the moment I'm trying to decide between 7.10 and 8.04 but I'm open to others as well. Here are the things I have to consider:

1.) I have a laptop with a X1200 series ATI graphics card. Catalyst dropped support for it and the xf86-video-ati (open source driver) won't detect my S-video out so I can't connect the laptop to the TV (which is a must). The xf86-video-radeonhd offers way to small of resolution and also doesn't detect S-video. Instead they both show a DVI port, which I do not have on the laptop.

Catalyst used my S-video and hooked up to the TV fine (back before support was dropped obviously). However it made the TV a virtual desktop that was way bigger than the visible portion. So if I tried watching a movie in fullscreen I could only see a little bit of it. I would have to manually resize the videos to be viewable and I had to do so everytime I started a show. I couldn't find any way to make the TV a normal resolution. It tries to use the same as the monitor. If I turn the monitor way down to make the TV normal I end up with problems on the monitor.

2.) I also have a desktop with an Nvidia card which I want to install K/Ubuntu on. This card is still supported by the official Nvidia drivers so I'm not worried there. However last time I tried KDE4 I couldn't setup a seperate X screen with my TV. At the time it said that wasn't offered and they had no intention to add it. Having this computer hook up to the TV is an absolute must. And I don't want somthing that will stretch one wallpaper across both. Has to have seperate wallpapers. Past that though I don't care if it's a seperate X screen. In fact it would be nice to be able to drag windows to the TV from the monitor.

3.) I'd also like to try LinuxMCE. However I hear you need two network cards and also that it won't work with the ATI card I have in the laptop. My main computer has two ethernet ports, so I'm not sure if then the laptop would work with MCE or no?

4.) I've tried both Ubuntu and Kubuntu 7.10 live cd's in the computer and both list the video driver (for the laptop) in the restricted driver manager as well as one for my wireless card. However on the Kubuntu 8.04 live DVD I have it does not show any driver for the video card, but it does show the driver for the wireless card.

So to recap I'm trying to decide what Ubuntu to install. I'm currently considering either 7.10 or 8.04, though I'm open to using another. 

I need a version of K/Ubuntu that has the older catalyst driver that still supports my X1200 series card (and does anyone know how to fix the resolution issue?). I think 8.10 is the newest I could use and after it support is dropped.

I want to use KDE4 on both computers but ONLY if I can get my TV and S-video and all that to work with it. Otherwise I'll use 3.5 or Gnome. 

To use MCE I take it I must have KDE. However for long term support I need Ubuntu 8.04 (Gnome) is that right?

Also how does KDE4 work on 8.04? Is it pretty bug free? Has anyone tried installing KDE4 on 7.10? If so how does it work?

Is there anyone using 8.04 with KDE4 and an Nvidia card? If so can you get seperate X screens on yours?

Is MCE good enough to bother with? I currently use MythTV. Can I have MCE only on the TV and have the computer monitor screen 'normal'? Or does MCE take over both screens regardless?

Thanks for any advice.

So what do you think I should do?

---

### Post by chadwick359 on 2009-07-01
Frankly, I don't see any good reason for you not to go with Jaunty. I don't see anything that jumps out and screams 'NOOOOOO' in your list of what you would like to do, and it's better put together. I haven't done much work with Myth/MCE, so I'm not much use there, but I use both the monitor out and s-vid on my nVidia 6800go on my laptop with no issues. As for the long term support issue? I wouldn't bother worrying about it, for the average user, regular releases are going to be a better idea anyway, so any deps for your media centers are more likely to up to date out of the box. As far as Kubuntu vs. Ubuntu, I would prolly have to say Ubuntu right at the moment. I go back and forth between KDE and gnome every once in a while, but KDE4 is a trainwreck atm/

---

### Post by The Avatar of Time on 2009-07-01
Jaunty is 9.04 right? The reason I might not be able to use it (esp. on the laptop) is if catalyst is new enough that it doesn't support the X1200 ATI card. Also according to their wiki 8.10 is the newest I can use with MCE. MCE can't be installed on any other distro can it?

But if 9.04 had old catalyst drivers that I can use and would work with MCE then I'd deffinately go for it since it's newer.

I put in a live cd of Kubuntu 7.10 a little while ago and got the S-video working with the TV via restricted drivers. The problem is though that the TV is still a virtual desktop, making maximized movies impossible to watch. I can set it to be seperate X screens, but the TV has the same resolution as the monitor, so I have to lower resolution to both, then I could watch maximized/fullscreen shows. I wish I just knew how to have the monitor and TV have seperate resolutions so it would work properly.

However when I put in an 8.04 disc it does NOT detect my video card. So I'm hesitant to try and install it.

I would be fine with running open source drivers on the laptop, but in Arch at least they wouldn't detect my S-video port. I have a Dell Inspiron 1721 laptop. Does anyone else have S-video trouble with the open source X1200 series ATI drivers?

---

### Post by ssri on 2009-07-01
Well, I'm running my laptop with Kubuntu 08.10 intrepid x86_64 due to the same reason you stated earlier, my ATI chip (mobility radeon x2300) is no longer supported in Catalyst 9.4 and above.  With Catalyst 9.3, I can watch videos from my laptop onto my TV just fine through svideo and in proper resolution provided that I disable xrandr ([http://ubuntuforums.org/showpost.php?p=7170485&postcount=2](http://ubuntuforums.org/showpost.php?p=7170485&postcount=2)).  It seems like xrandr and fglrx do play nice with each other.  Before disabling xrandr, I had similar resolution issues with my tv and laptop, meaning the screen res was too large for my tv to handle, etc.

From the thread I posted just above:
> **Keithus said:**
> Yay!  At Last!  Finally, finally, finally!  After all the cuss words, and hair-pulling, and general frustration in trying to get the amdcccle to work for me, this thread has given me the information I needed!  Little did I know that RandR was working away in the background to sabotage my attempts to make dual screens work properly, but now that it is disabled everything works just how I want it to!  Very many thanks for this extremely useful information!  Linux users are the best!

Plus, kde 4.2.2 is intrepid's backports.  Installing Catalyst 9.3 on intrepid was pretty easy, so long as I followed ubuntu's guide to the letter in creating ubuntu/intrepid packages from ati's atidriver.sh file.  For some reason, it seems that doing sudo sh ./ati-blah-blah.run never really worked flawlessly for me.  

Plus, for disk shock protection, I installed jaunty's 2.6.28-11 kernel on my laptop without any problems, so long as I installed kernel source along with it in order to allow fglrx to setup dkms automatically.  So far no problems.  Can't say much about Jaunty, as I have been less than satisfied with the radeon drivers (including the rewrites released a few weeks after jaunty).  Best of luck!

---

### Post by ssri on 2009-07-01
> **chadwick359 said:**
> Frankly, I don't see any good reason for you not to go with Jaunty. I don't see anything that jumps out and screams 'NOOOOOO' in your list of what you would like to do, and it's better put together. I haven't done much work with Myth/MCE, so I'm not much use there, but I use both the monitor out and s-vid on my nVidia 6800go on my laptop with no issues. As for the long term support issue? I wouldn't bother worrying about it, for the average user, regular releases are going to be a better idea anyway, so any deps for your media centers are more likely to up to date out of the box. As far as Kubuntu vs. Ubuntu, I would prolly have to say Ubuntu right at the moment. I go back and forth between KDE and gnome every once in a while, but KDE4 is a trainwreck atm/

Hmm, I've been pretty happy with kde 4.2.x in intrepid since its late Jan release.  It is like night and day compared to buggy mess that was 4.1.x.  Well, the OP referred to his legacy ATI and that is white elephant in the room here.  Currently, the drivers for ATI cards are in a state of flux.  Via phoronix, do not expect major gains with GLSL and OpenGL 2.0 support until gallium3d stack has been stabilized, which will not happen until 2010 (10.04), and that is being optimistic.  Furthermore, quite a few peeps have been having problems getting multiple monitors to work in jaunty using proprietary and opensource drivers.  Remember, the OP complained how the opensource drivers could not detect his svideo port.  There's your showstopper right there.  If the OP likes kde and wants to setup his laptop to his tv/projector/etc with the least amount of pain, I would recommend kubuntu intrepid with backports enabled.

---

### Post by The Avatar of Time on 2009-07-01
So 8.10 still has the drivers that I can use, and 9.04 is where support was dropped for my X1200 then?

It looks like MCE will build on 8.10 too.

Does anyone know what 7.10 will see and enable my video card driver but 8.04 won't?

How much difference in reliability, stability, etc.. is there between the releases? Is 8.10 loads better than 7.10? Is there really anything I'll be missing out on if I install 7.10 (it's what I'm leaning toward right now, since it's the only one that found my drivers). 

Now on the other hand sound seems to work with a Hardy live disc but not with Gutsy. 

I have a terrible time making up my mind on things like this. Perhaps I can get some pros and cons of using 7.10 vs 8.04 vs 8.10? 

I see that KDE4 can be installed on 7.10, has anyone tried this to see how it works? I used KDE4 on Hardy when it first came out but it was unusable for me. 

Is the version of KDE4 in Hardy better than it used to be? 

And if I go with gnome, which I will unless I decide to use MCE, what release is it most stable in?

ssri: thanks for the reply. How big of pain was it to get the correct catalyst version? You couldn't juse enable it from the restricted drivers manager?

chadwick359: Yeah the Nvidia cards like you have are a lot nicer for Linux. When you say KDE4.2.2 is in the back ports what does that mean? What version is installed by default?

Also is it generally accepted that KDE3.5 is better than KDE4?

---

### Post by The Avatar of Time on 2009-07-01
Okay according to this:[http://ubuntuforums.org/showpost.php?p=7170485&postcount=2](http://ubuntuforums.org/showpost.php?p=7170485&postcount=2) disabling xrandr will fix the virtual desktop issues. 

However this place doesn't exist: /etc/ati/amdpcsdb not even just the /etc/ati

That being the case how would I disable xrandr?

Something else odd is that the 7.10 shows my restricted drivers, 8.04 does not. However I have sound on 8.04 but no sound on 7.10. And idea what's up with that and if it will be fixable once I install?


***I find it very strange that 8.04 won't show available restricted drivers and yet 7.10 does. Makes me worry whether or not 8.04 would work with that card.

---

### Post by The Avatar of Time on 2009-07-01
> **ssri said:**
> Well, I'm running my laptop with Kubuntu 08.10 intrepid x86_64 due to the same reason you stated earlier, my ATI chip (mobility radeon x2300) is no longer supported in Catalyst 9.4 and above.  With Catalyst 9.3, I can watch videos from my laptop onto my TV just fine through svideo and in proper resolution provided that I disable xrandr ([http://ubuntuforums.org/showpost.php?p=7170485&postcount=2](http://ubuntuforums.org/showpost.php?p=7170485&postcount=2)).  It seems like xrandr and fglrx do play nice with each other.  Before disabling xrandr, I had similar resolution issues with my tv and laptop, meaning the screen res was too large for my tv to handle, etc.

From the thread I posted just above:


Plus, kde 4.2.2 is intrepid's backports.  Installing Catalyst 9.3 on intrepid was pretty easy, so long as I followed ubuntu's guide to the letter in creating ubuntu/intrepid packages from ati's atidriver.sh file.  For some reason, it seems that doing sudo sh ./ati-blah-blah.run never really worked flawlessly for me.  

Plus, for disk shock protection, I installed jaunty's 2.6.28-11 kernel on my laptop without any problems, so long as I installed kernel source along with it in order to allow fglrx to setup dkms automatically.  So far no problems.  Can't say much about Jaunty, as I have been less than satisfied with the radeon drivers (including the rewrites released a few weeks after jaunty).  Best of luck!

So you would deffinately recommend 8.10 as my best option? It should work with MCE it looks like. And apparently the catalyst drivers still work (I assume they'll work with the X1200 also). And how is KDE4 on it in terms of stability and reliability? Good I assume if you're using it ;)

And what kind of screen do you have the TV set to? Clone or seperate X? I take it you did have trouble with the TV being a virtual desktop before you turned off xrandr?


***Also where is it recommended to get Kubuntu 8.10 from? Their site only has 8.04 and 9.40.

***Nevermind. Here looks like a good enough place: [http://releases.ubuntu.com/releases/kubuntu/8.10/](http://releases.ubuntu.com/releases/kubuntu/8.10/)

---

### Post by The Avatar of Time on 2009-07-01
ssri: I just noticed that you mentioned having to install catalyst manually. I assume then that it's not in the repos/can't be enabled through restricted driver manager?

---

### Post by ssri on 2009-07-01
> **The Avatar of Time said:**
> ssri: I just noticed that you mentioned having to install catalyst manually. I assume then that it's not in the repos/can't be enabled through restricted driver manager?

The Catalyst driver included in the Intrepid repos is 8.11, which is utter crap.  Install that first though.  Afterwards, go to ATI's site, to their driver section and select linux->your card.  You should be directed to a page to download Catalyst 9.3

Following instructions here ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers)))

open your konsole and go to the directory where you downloaded the drivers and then enter the following: 

```
sudo apt-get remove --purge fglrx*

sudo apt-get install dpkg-dev debhelper libstdc++5 dkms build-essential cdbs fakeroot

sh ./ati-driver-installer-9.3-x86.x86_64.run --buildpkg Ubuntu/intrepid

sudo dpkg -i --force-overwrite xorg-driver-fglrx_8.593-0ubuntu1_amd64.deb fglrx-kernel-source_8.593-0ubuntu1_amd64.deb fglrx-amdcccle_8.593-0ubuntu1_amd64.deb

sudo dpkg-reconfigure -phigh xserver-xorg

sudo aticonfig --initial -f
```

To remove everything if it does not work and to reinstall the one that came with Intrepid:

```

sudo dpkg --purge fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx

sudo apt-get remove --purge fglrx*s

sudo apt-get autoremove

sudo apt-get install fglrx-amdcccle
```

Yeah, that's alot of CLI for anyone to take

---

### Post by ssri on 2009-07-01
> **The Avatar of Time said:**
> Okay according to this:[http://ubuntuforums.org/showpost.php?p=7170485&postcount=2](http://ubuntuforums.org/showpost.php?p=7170485&postcount=2) disabling xrandr will fix the virtual desktop issues. 

However this place doesn't exist: /etc/ati/amdpcsdb not even just the /etc/ati

That being the case how would I disable xrandr?

Something else odd is that the 7.10 shows my restricted drivers, 8.04 does not. However I have sound on 8.04 but no sound on 7.10. And idea what's up with that and if it will be fixable once I install?


***I find it very strange that 8.04 won't show available restricted drivers and yet 7.10 does. Makes me worry whether or not 8.04 would work with that card.

That directory should show up when you install ATI's restricted/proprietary Catalyst drivers...

---

### Post by snowpine on 2009-07-01
I can't believe anyone would consider switching from Arch to Ubuntu 7.10. Support for 7.10 ended back in April, meaning there will be no more bug fixes, no security updates, and the repositories are shut down. Arch, on the other hand, rocks. :guitar:

If Ubuntu has dropped support for your hardware (sounds like this may be true in your case) then I definitely recommend finding another distro instead of struggling with an obsolete Ubuntu release.

---

### Post by The Avatar of Time on 2009-07-01
> **snowpine said:**
> I can't believe anyone would consider switching from Arch to Ubuntu 7.10. Support for 7.10 ended back in April, meaning there will be no more bug fixes, no security updates, and the repositories are shut down. Arch, on the other hand, rocks. :guitar:

If Ubuntu has dropped support for your hardware (sounds like this may be true in your case) then I definitely recommend finding another distro instead of struggling with an obsolete Ubuntu release.

The trouble I have is that anything newer, including Arch, has a newer version of catalyst that won't work with my graphics card. It's not an issue of a particular distro dropping support, it's catalyst, the ATI driver, that has dropped support. So the only way to use it (and I have to use catalyst because the open source drivers won't detect my S-video) is find an older version. 

Therefore I can either fight with downgrading my Arch system, because with the older catalyst I have to have an older X server, and thus an older kernel (maybe not on the kernel, I'm not sure there) and so on, or find a distro that already uses the older catalyst version. The second option seems considerably easier because even if I get Arch downgraded and working (which I haven't had any luck doing) I'll never really be able to update it again which sort of defeats the purpose of a rolling release distro like that.

Ideally yes, I would much rather stick to running Arch, but this laptop is my mother's and she has to have it were it will hook up to the TV. I can't seem to get any help over at Arch forums in making the open source drivers detect S-video. If I could get them to do that then I'd continue running Arch with the open source drivers.

Also however I want to try LinuxMCE, at least on my main computer, and it requires Kubuntu 8.10 or older. 

However I didn't realize that the repositories closed when support was dropped, so I guess I won't be using 7.10. Thanks for bringing that to my attention though, it would of been annoying to find out later. 

Right now I'm planning to install Kubuntu 8.10 on the laptop. Hopefully by the time support on it is dropped there will be a working open source driver I can use,that will work with my S-video port. Otherwise I'll be permanently stuck on an old distro.

---

### Post by The Avatar of Time on 2009-07-01
Okay, I'm trying to install Kubuntu 8.10. However I'm having an issue, and it was the same with 7.10 or 8.04 (maybe both, don't remember for sure). When I get to the partitioner and choose manual it only shows /dev/sda. 

I have three partitions on that disc: swap, /, and /home but it isn't seeing them. This makes it impossible to install without losing /home.

Does anyone know what to do about this? Thanks.

---

### Post by The Avatar of Time on 2009-07-01
Ok while booted into the Kubuntu 8.10 Live CD I installed gparted. It only shows one 'unallocated' partition of 149gbs (the hard drive is larger than that I believe).

With sudo fdisk -l it shows three partitions, which is what there should be. Though I think the swap is showing as fat32. 

I don't know what the deal is here with this but I can't install unless I can save the /home folder.

---

### Post by The Avatar of Time on 2009-07-01
Correction, the drive is only 150gbs, so gparted and such are showing the whole drive, just not the partitions. 

I put in the Arch installation disc and it can see and mount the partitions fine. However if I try to enter the Arch partitioner I get an error about a partition ending in/on a cylninder. So something is messed up with my partitions, I just don't know what. 

So likely there won't be anyway to save the /home folder you think?

---

### Post by The Avatar of Time on 2009-07-02
Well I've decided to tar the home folder and save it on my other computer/server so that's no longer an issue. 

If it evers finishes transferring I'll be ready to put a clean install of Kubuntu 8.10 on. Then I'll be ready to try the posted instructions here for getting the right driver and disabling xrandr. 

Hopefully that all goes smoothly. I'm really hoping KDE4 has improved. I really liked it before but it wasn't usable for me at the time. 

Thanks for all the help so far and good luck to me I guess.

---

### Post by The Avatar of Time on 2009-07-02
Okay I got Kubuntu 8.10 installed on the laptop. However I can't get the restricted video driver to install now. 

I bring up the driver manager, it searches for available drivers, lists the one I need, and when I click activate a 'downloading driver' screen pops up for a second and then goes away and nothing more happens.

When using the 7.10 and 8.04 live discs I could enable the driver and restart x and the TV worked. Now it doesn't. 

Does anyone know why it won't install on 8.10?

ssri: Can I just ignore this and go straight to the steps you recommended?

Also my wireless broadcom driver showed up in either 7.10 or 8.04, maybe both, but it doesn't show up on 8.10. My video driver shows up but won't activate, and then 'wl' shows up already activated.

Well it occured to me that I should update the system before proceeding, so I'm doing that now. It shouldn't take too long. However, what happened to the safe-updrage command? I remember using that before but now it's dist-upgrade.

---

### Post by The Avatar of Time on 2009-07-02
Okay once I updated I was able to install the drivers. However I updated, restarted, tried to install the video card driver and it just sat there on 'downloading driver' for some time. I canceled it, restarted, and it said it was activated. It wasn't though, there was nothing going to the TV. So I disabled it, restarted, re-enabled it (worked fine this time), restarted again and I had a clone monitor on the TV (still a high resolution virtual desktop, but I expected that for now). Good.

However the TV magically stopped working. Both screens went to sleep and when I shook the mouse only the laptop came back on. Nothing on the TV. I restarted, still nothing. The driver still says it's activated though..... I assume this might have something to do with the driver being utter crap as before mentioned? 

Now the wireless on the other hand has been pleasent. I enabled 'Broadcom SAT' and it found my router and all is well. I was very impressed with this part. In Arch Linux it never would connect automatically (it does now on Kubuntu), I used to have to run a script at login. 

Anyway so far the wireless setup was pleasant. The video driver not so much.... 

I'm gonna try to get it working on the TV again and then I'll be ready to try ssri's instructions for updating it and turning off xrandr.

Does anyone know why the TV would of magically quit working? Or is it just the bad driver? Thanks so far for all the help.

---

### Post by The Avatar of Time on 2009-07-03
ssri: I went to [http://www.amd.com/us/Pages/AMDHomePage.aspx](http://www.amd.com/us/Pages/AMDHomePage.aspx)

Unfortunately they don't have the drivers that I need. X850 and X1300, but I have an X1200 series card.

What would be the proper course of action now?

Also on the link the instructions that you provided that are two methods, the first being to use the repos and the second being from ATI, which I assume is the directions I'm to follow. However I can't of course unless I can find the drivers. I am running x86_64 by the way, though that shouldn't make a difference really.

---

### Post by The Avatar of Time on 2009-07-03
I've updated to KDE4.2, wireless is still working fine, and I have the TV working with the computer but it's still a virtual desktop. I tried doing this: [http://ubuntuforums.org/showpost.php?p=7170485&postcount=2](http://ubuntuforums.org/showpost.php?p=7170485&postcount=2) but it doesn't help. I'm don't think it actually did anything for me. 

Also I cannot find the drivers for download. I tried the top instructions here (for 8.10) [ https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers ]( https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers )

However, this: ```
 sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko 
``` gives a no such location error. What would this do anyway? Update the restricted drivers that I enabled?

So at the moment I'm trying to disable xrandr to have a normal display on the TV and also to update the ATI catalyst driver, per ssri's advice. Does anyone have any advice on this for me? Thanks.

---

### Post by ssri on 2009-07-03
For your card, all you need to do is find the link that has Catalyst 9.3 (ati-driver-installer-9.3-x86.x86_64.run)(or i386), and then follow my instructions.  For svideo out though, I think I had to sudo amdcccle when messing with the settings, so ati could edit my xorg.conf for me.  Good luck!

---

### Post by The Avatar of Time on 2009-08-07
I should of replied earlier but I've been very busy. 

I had Kubuntu 8.10 x86_64, with KDE4.2 from backports, working rather nicely.

However, I could not for the life of me get flash to install and work with either Firefox or Konqueror. I ended up with an error about the md5sum of the flash installer if I remember right. 

I ended up reinstalling Arch64, but still can't seem to get it downgraded right to use catalyst. However installing flash was simple: 'pacman -S flashplugin' and it worked. 

I'm likely going to switch back to Kubuntu again, but I need to be able to get flash to work. Any ideas on what I can do? I'm quite out of place on Kubuntu, having used Arch for so long. Thanks for the advice.

---

