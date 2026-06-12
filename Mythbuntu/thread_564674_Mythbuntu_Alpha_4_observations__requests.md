---
title: "Mythbuntu Alpha 4 observations / requests"
date: 2007-10-01
forum: Mythbuntu
---

### Post by Panhead Bill on 2007-10-01
Items 1-3 copied from my post in multimedia forum.

1. Guided partitioning: The default seems to be 50% of the drive is used for the OS. Could the default be set to the required space that a Standard Mythbuntu install uses, plus a reasonable safety margin? What is the default Swap size in guided partitioning? is it 2X memory size? If memory is large enough, wouldn't 2X be a waste of drive space?

2. Kernel memory use: Does the standard kernel utilize all available memory or is it limited to 1gig? I read that the standard linux kernel would not utilize all available memory, and one would have to be compiled to use more than that. A followup would be is myth able to use memory above the 1gig limit?

3. LVM support: I'm running a 5 drive system on my master backend. An option to set up a LVM with the EXT3 space on the primary drive and all of the space on the additional drives would be sweet.

4. Possible bug: when erasing all recordings, or the last recording; the system seems to hang on the now empty menu.  ESC doesn't return me to the prior level.  It takes a forced reboot to get back to operational condition.  This has happened several times.

5. Possible bug: after a scheduled recording aborted, the recordings menu reported no recordings at all.  System status indicated drive space useage.  Reboot recovered recordings.  One occurance each of the aborted recording and the temporary loss of all other recordings.

Any estimate of release date?

Thanks for the efforts on Mythbuntu!

---

### Post by superm1 on 2007-10-01
I plan to do a custom partitioning recipe, but it might not make it into the 7.10 release with all of the other items that need to be sorted out still.  If someone wants to dive into helping figure that out, that'd be great.

As far as I know, you will be able to use up to 4G RAM with the standard kernels.

LVM: Not going to happen for 7.10, but I want to discuss it at UDS.  If you will be there, come join.

What filesystem are you using that you were removing recordings from? If its ext3, then you need to turn on slow writes in mythtv-setup.

Estimates of release date?  Right after gutsy release is the plan (barring any extenuating circumstances).  We are very near to a beta however.

---

### Post by Yoooder on 2007-10-01
My one issue, which has occured twice:

[http://ubuntuforums.org/showthread.php?t=564670]("http://ubuntuforums.org/showthread.php?t=564670")

---

### Post by jadfw007 on 2007-10-01
I have a request. Please make EIT an easy option to configure for American cable users. I have found no way to successfully do this in MythDora and have a feeling I'd have to recompile MythTV from source to get it working.

---

### Post by superm1 on 2007-10-01
> **jadfw007 said:**
> I have a request. Please make EIT an easy option to configure for American cable users. I have found no way to successfully do this in MythDora and have a feeling I'd have to recompile MythTV from source to get it working.

What's wrong with the current EIT setup?  Do you have a patch your referring to that needs to be applied to mythtv sources for EIT/cable to work?

---

### Post by jadfw007 on 2007-10-01
> **superm1 said:**
> 
LVM: Not going to happen for 7.10, but I want to discuss it at UDS.  If you will be there, come join.


I take it RAID also will not be supported then?

---

### Post by jadfw007 on 2007-10-01
> **superm1 said:**
> What's wrong with the current EIT setup?  Do you have a patch your referring to that needs to be applied to mythtv sources for EIT/cable to work?

I wish I could say for sure. From what I've found searching the forums, etc., it sounds like MythTV in MythDora was not compiled with the "-dvb" options which are necessary (I think?) for EIT to work. All I know for sure is I've configured it and re-configured it and cannot get it working.

---

### Post by JBAlaska on 2007-10-01
[quote="superm1 said"]What filesystem are you using that you were removing recordings from? If its ext3, then you need to turn on slow writes in mythtv-setup.[/quote]
I have been using JSF on my /video partition and this seems to cure the problem.

---

### Post by superm1 on 2007-10-01
> **jadfw007 said:**
> I take it RAID also will not be supported then?

Well not to say it "won't work", but it won't be configurable in the installer.  By doing a derivative frontend of ubiquity we have all the benefits it does of a fast install, but also defficiencies with regard to LVM and RAID.

If you want to do either of these setups (in 7.10) you will need to configure them post install unfortunately.

> 
I wish I could say for sure. From what I've found searching the forums, etc., it sounds like MythTV in MythDora was not compiled with the "-dvb" options which are necessary (I think?) for EIT to work. All I know for sure is I've configured it and re-configured it and cannot get it working.

We are build with dvb, and i've captured EIT data OTA myself previously.  Unless something special needs to be done for EIT/cable, you should be fine.

> 
I have been using JSF on my /video partition and this seems to cure the problem.

Or Xfs would likely be just as good for such a situation.

Do note, that if you follow the standard storage locations (/var/lib/), samba and nfs get preconfigured for you.

---

### Post by nowhere@cox.net on 2007-10-01
Hi all,

I just attempted a fresh install of Mythbuntu due to a horrible upgrade experience from FC5 to FC7. It did not go well and ultimately I went back to a FC7 fresh install.  Here are my comments

Mythbuntu Alpha 4. 
1. No LVM - I have an 80GB and 200GB hard drives. I would have lost almost 1/3 my storage space.
2. I have an integrated nvidia MX440 video card. "nv" drivers hung the system. I was looking for point and click install from Mythbuntu so I did not spend a lot of time troubleshooting at the time.
I recently tried a Ubuntu only install on another system with a 7800GT card with the same results. I had to manually change to the vesa drivers then use restricted package manager to install the nvidia drivers. Worked after that.
3. I have a realtek integrated sound card. I never was able to get any sound using any of the sound systems (ALSA OSS etc).
2 and 3 are obviously Ubuntu problems since I then tried to do a fresh install of Feisty and install mythtv from apt but had the same "nv" problems.  I also tried a fresh install of Gutsy which handles LIRC so much easier but had the same "nv" problems so I abandoned both options. It was a little disheartening to see the same serious install bug migrating through distributions like that. On my other system, I saw a grub problem handling boot order for SATA and PATA drives in the same system also cross the distro boundary. 

However, much to my delight and amazement, ivtv worked out of the box as did my bane of all existance, LIRC. Excellent work here!  (My install of FC7 and LIRC was once again a nightmare!).  Also, one attempt at the Mythbunutu fresh install made it all the way through the mythtv setup before the nv drivers hung the system. Very slick job on the integrating the installation. I am really excited about seeing the next revision!

So my one request besides just getting the "nv" thing sorted out and the sound which are both Ubuntu problems is I specifically HAVE to have LVM and a custom partition ability would be nice as well. Even if I upgrade with a newer bigger hard drive I will just add it to my exisiting system.

Excellent work all and THANKS!
Eric

---

### Post by superm1 on 2007-10-01
First off thanks for all the feedback:

> **nowhere@cox.net said:**
> Hi all,

I just attempted a fresh install of Mythbuntu due to a horrible upgrade experience from FC5 to FC7. It did not go well and ultimately I went back to a FC7 fresh install.  Here are my comments

Mythbuntu Alpha 4. 
1. No LVM - I have an 80GB and 200GB hard drives. I would have lost almost 1/3 my storage space.

Yeah i hear you here.  It's unfortunate, but our choices were either go alternate install disk and get LVM or go for very easy to follow graphical install for people.  For hardy we'll plan to see improvements here.
> 
2. I have an integrated nvidia MX440 video card. "nv" drivers hung the system. I was looking for point and click install from Mythbuntu so I did not spend a lot of time troubleshooting at the time.
I recently tried a Ubuntu only install on another system with a 7800GT card with the same results. I had to manually change to the vesa drivers then use restricted package manager to install the nvidia drivers. Worked after that.

Safe graphics mode on the live cd will boot you up into the vesa driver

> 
3. I have a realtek integrated sound card. I never was able to get any sound using any of the sound systems (ALSA OSS etc).

There are tons of realtek integrated cards, i'm surprised to see issues with regard to a single one.  Did you file a bug ever?  I know there has been some chatter on the kernel mailing list about broken alsa stuff, so if you did, hopefully fixes will be in soon.

> 
I also tried a fresh install of Gutsy which handles LIRC so much easier but had the same "nv" problems so I abandoned both options. It was a little disheartening to see the same serious install bug migrating through distributions like that. On my other system, I saw a grub problem handling boot order for SATA and PATA drives in the same system also cross the distro boundary. 

However, much to my delight and amazement, ivtv worked out of the box as did my bane of all existance, LIRC. Excellent work here!  (My install of FC7 and LIRC was once again a nightmare!).  Also, one attempt at the Mythbunutu fresh install made it all the way through the mythtv setup before the nv drivers hung the system. Very slick job on the integrating the installation. I am really excited about seeing the next revision!

So my one request besides just getting the "nv" thing sorted out and the sound which are both Ubuntu problems is I specifically HAVE to have LVM and a custom partition ability would be nice as well. Even if I upgrade with a newer bigger hard drive I will just add it to my exisiting system.

Excellent work all and THANKS!
Eric

Gparted on the disk can be done.  I'll see how much more space that adds and see what we can do.  As for LVM, if you don't touch your existing LVM groups, they will carry over to a new install.  Ubiquity won't wipe things unless you tell it to.
After install it'd be a matter of apt-get install lvm2.

---

### Post by Panhead Bill on 2007-10-02
SuperM1;

  The file system is the default EXT3, so I will alter the setup.  

  It looks like I jest need to "apt-get install LVM2" to resurrect my LVM, but how do I get to the terminal?  If I exit mythtv, I get the brown screen for a short while, but never can get to the terminal.  Mythtv reboots and I'm back where I started.  I'll have to set up a second PC and try ssh for now.

Anyway, Thanks to the Mythbuntu development group!  I like what I've seen so far.

---

### Post by superm1 on 2007-10-02
> **Panhead Bill said:**
> SuperM1;

  The file system is the default EXT3, so I will alter the setup.  

  It looks like I jest need to "apt-get install LVM2" to resurrect my LVM, but how do I get to the terminal?  If I exit mythtv, I get the brown screen for a short while, but never can get to the terminal.  Mythtv reboots and I'm back where I started.  I'll have to set up a second PC and try ssh for now.

Anyway, Thanks to the Mythbuntu development group!  I like what I've seen so far.
We're planning beta disk for tomorrow.  It includes a drastically different administration setup, so you should be able to do things a lot easier with it.  You can attempt to apt-get update/dist-upgrade to beta, but there are a few additional changes that would need to be made to take advantage of the new session.

---

### Post by Panhead Bill on 2007-10-02
I'll most likely do a fresh install of the beta.  All the broadcasts that I recorded on the mythbox can be deleted or are also on the VCR while I am testing the new releases.

  I'll also have to reteach myself LVM2, since my 4 disk storage array was set up with reiserfs instead of ext3.  Good thing I have my notes (somewhere).

On another front, where would be the best place to request minor changes/fixes to mythtv itself?  Mythsetup is visually confusing; the "select boxes" are not obvious and counter intuitive (to my eyes at least).  Let me explain, the check boxes have two states: (1) Slightly lighter and to my eyes seem like a button in the "out" position, and (2) Slightly darker and "in".  By experimentation with the programming auto update function I determined that the "out" position was select, and the in position was not-select.  A checkmark or some other identifier would help in setting up myth.

  In a similar vein, mythweather setup is another visually "less than optimal" interface.  It is not clear which measurement system is selected until Mythweather is on, and selection of connection speed and location are less than clear.  To put it another way, I know what I am trying to select (connection speed, and city), I know that I selected something, but it is not obvious which speed or city is selected until the program is run.  Of corse having mythweather running again is a welcome fix.

---

### Post by rusty0101 on 2007-10-03
The easy way to get to a terminal is to hold down the [Ctrl], [Alt] keys and press any of [F1] through [F6] That is how you get from X into console mode. You will have a text mode screen and you will be prmpted to log in, etc.

To add LVM, you will need to prepend the apt-get install lvm, or lvm2 command with 'sudo'.  You will then be prompted for your password again.

A more complicated way of getting to tha point where you can use a terminal is to go into the mythbuntu setup menu, and turn off booting directly into mythtv. aply the changes to the settings, and then exit from mythtv. This time when gdm prompts you to log in, you will have to do soyourself, (select the appropriate user, and enter the appropriate password, etc.) Once you log in you will get a mostly blank screen, right click on the background and fnavigate the menus to the point where you can open a terminal.

To return to Mythtv from the text mode console suggested in the begining, use [Ctrl]-[F7]. To do the same from X, either type mythfrontend in a console, or right click in the background and navigate to the appropriate menu entry to start the fron end again. You may also wish to go into mythbuntu config and turn on launching directly into mythtv again, that would be your decision to make however.

---

### Post by Panhead Bill on 2007-10-09
SuperM1:
> **superm1 said:**
> 
As far as I know, you will be able to use up to 4G RAM with the standard kernels.


In "Hacking Ubuntu" by Neal Krawetz, in reference to the 4 gig memory limits of the 32 bit i686 family:

"The second limitation comes from the linux 2.6 kernel used by Ubuntu's dapper drake.  The kernel can only access 1gb of ram. Any remaining ram is unused."  

and 

"If you compile a kernel from scratch, there is a HIGHMEM flag that can be set to access up to 4GB of ram on a 32 bit architecture. Unfortunately there is a reported performance hit since most hardware drivers cannot access the high memory."


So has the HIGHMEM flag been set on kernels after Dapper, and can Mythbuntu access it?

---

### Post by superm1 on 2007-10-09
> **Panhead Bill said:**
> SuperM1:


In "Hacking Ubuntu" by Neal Krawetz, in reference to the 4 gig memory limits of the 32 bit i686 family:

"The second limitation comes from the linux 2.6 kernel used by Ubuntu's dapper drake.  The kernel can only access 1gb of ram. Any remaining ram is unused."  

and 

"If you compile a kernel from scratch, there is a HIGHMEM flag that can be set to access up to 4GB of ram on a 32 bit architecture. Unfortunately there is a reported performance hit since most hardware drivers cannot access the high memory."


So has the HIGHMEM flag been set on kernels after Dapper, and can Mythbuntu access it?

supermario@portablemario:~$ cat /boot/config-2.6.22-13-generic | grep HIGHMEM
# CONFIG_DEBUG_HIGHMEM is not set
CONFIG_HIGHMEM=y
# CONFIG_NOHIGHMEM is not set
CONFIG_HIGHMEM4G=y

---

