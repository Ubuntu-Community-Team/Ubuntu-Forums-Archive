---
title: "Use Ubuntu 10.04 to sync music to ipod touch 4g ios4.1"
date: 2010-12-31
forum: Multimedia Software
---

### Post by jameskevindoyle on 2010-12-31
Hi,

I have an ipod touch 4g running iOS 4.1 (not jailbroken).  Can I set up a new Ubuntu install that can sync music to it?  

I am thinking of just backing up my data from my current Ubuntu 9.04 install and installing a newer Ubuntu fresh, so I have freedom to install whatever works best.  

From different forum threads, it seems like ipod support is kind of a moving target, for instance, the usbmuxd < 1.0.6 in Ubuntus 10.04 and 10.10 would not recognize an ipod 4g at all due to the device ID (from what I read), and it looks like deb packages for usbmuxd 1.0.6 only became available the past week or so.  It does look like people have gotten it to work, for instance, slcpunk's posts in the thread [http://ubuntuforums.org/showthread.php?t=1576249&highlight=ios+4.1&page=10](http://ubuntuforums.org/showthread.php?t=1576249&highlight=ios+4.1&page=10)  But I'm not entirely clear on what people have done to get it to work - the libimobiledevice site seems to say its intention is to support non-jailbroken devices, but some of the thread posts with detailed instructions include jailbreaking.

My preference would be Ubuntu 10.04, since that's also on my wife's netbook, and the Ubuntu 10.04 live CD is acting less flaky on my desktop than the Ubuntu 10.10 live CD.  I'd also prefer Rhythmbox to other players, since I'm familiar with it already, but am willing to try whatever works.  And I really don't want to jailbreak our ipod touches (mine would be OK, but I don't want to mess with my other family members').

Here's where I've gotten so far:

Take 1: Ubuntu 10.04 + ppa: pmcenery/ppa

- Ubuntu 10.04 desktop live CD

- apt-get install the lucid packages from ppa: pmcenery/ppa:
gvfs ifuse libgpod4 libimobiledevice1 libimobiledevice-utils libplist1 usbmuxd

- this brings gvfs from 1.6.1 to 1.6.2, plist from 1.1 to 1.3, libgpod4 from 0.7.93 to +git20100608, usbmuxd from 1.0.2 to 1.0.6, and libimobiledevice1 new (1.0.4)

- log out and back in

- I make sure my ipod touch is unlocked (enter passcode) and plug in USB

- usbmuxd process properly starts running

- ideviceinfo command works

- gvfs for "jim's ipod" properly created, ipod-looking desktop icon for "jim's ipod" appears

- open "jim's ipod" folder, I can see the contents of the ipod (photos, itunes folders, etc.)

- open rhythmbox, I can see "jim's ipod" listed under Devices, and I can right-click to see its Properties

- I can drag music (MP3 files) from my library into "jim's ipod" and rhythmbox shows a status "transferring 1 of 10" with a progress bar that completes.  During this, ipod itself sometimes shows "Sync in progress".

- eject "jim's ipod" from within rhythmbox and disconnect USB, then on ipod itself, open Music, but this shows only "No content.  Content can be downloaded from itunes"

- connect ipod USB again and open "jim's ipod" folder, I can go into folders beneath "itunes_control" and find files named after the songs I transferred.  So something is being written to the ipod.  But apparently the ipod itself doesn't recognize it.

Take 2: Ubuntu 10.04 + ppa: pmcenery/ppa + webupd8 rhythmbox

Reading slcpunk's posts more carefully regarding the "sync" rhythmbox feature, I tried updating rhythmbox from the webupd8 PPA (to 0.13.1 I think), to get the latest support.  I was able to start rhythmbox again, open "jim's ipod" properties, go to the sync tab, select a playlist with 6 MP3 files, and then click the "sync with library" toolbar button.  rhythmbox shows a "transferring" status with a progress bar, and the ipod itself shows "Sync in progress".  But after it finishes and I eject the ipod from rhythmbox, I get the same result on the ipod itself.  Opening Music shows "No content.  Content can be downloaded from itunes".

Does anyone know what I'm missing?

This is what rhythmbox / libimobiledevice are supposed to be able to do, right?  The synced music should appear on the ipod touch under "Music"?

Did anyone else get Ubuntu 10.04, Rhythmbox, and iOS 4.1 without jailbreak to sync music successfully?  What would be really useful is a list of versions of the different packages involved (rhythmbox, libgpod, libimobiledevice, usbmuxd, etc.) from someone's working system.

Is it libgpod that's responsible for whether the ipod files/database are updated correctly in the right format?  Do I maybe have the wrong libgpod?

Thanks in advance,
Jim

---

### Post by jameskevindoyle on 2010-12-31
I did more research on libgpod and found a better explanation of libgpod's status on the Gtkpod-devel mailing list, from October:
[http://old.nabble.com/libgpod-0.8.0-td29942716.html](http://old.nabble.com/libgpod-0.8.0-td29942716.html)

This makes it sound like my problem is not that I'm running iOS 4.1, which is supported, but that the ipod touch model itself is 4g, which is not.  I guess I thought the compatibility with the iOS version is what was important, not the 2g/3g/4g hardware itself.  The 4g uses a database checksum hash which as of October hadn't been implemented in code that can be added to libgpod. 

You'd have to think, then, that no Ubuntu system would currently be able to sync music to an ipod touch 4g.

But slcpunk's posts in [http://ubuntuforums.org/showthread.php?t=1576249&highlight=ios+4.1&page=10](http://ubuntuforums.org/showthread.php?t=1576249&highlight=ios+4.1&page=10) mention an iphone4, and that uses the "new hash", doesn't it?  Was that iphone4 was jailbroken?

Does anyone know if someone is working on implementing the ipod touch 4g hash for libgpod?  I'll keep checking the November and December threads in Gtkpod-devel.

---

### Post by jameskevindoyle on 2010-12-31
Found an answer to one of my questions in the forum thread I mentioned before, [slcpunk]("http://ubuntuforums.org/member.php?u=956482")'s iphone4 is jailbroken:
[http://ubuntuforums.org/showpost.php?p=10128133&postcount=81](http://ubuntuforums.org/showpost.php?p=10128133&postcount=81)

> 

[LIST]
[*]jailbreak?  check.
[*]change DBVersion to 2?  check.
[*]delete itunes_control?  check.
[/LIST]


Is this how to get around libgpod not being able to work with the 4g hash?

Is jailbreaking the only way to do this?  Meaning for a 4g you have to decide between iTunes and jailbreaking in order to sync music to it?

---

### Post by conorsulli on 2011-01-05
some interesting reading for you

[http://ubuntuforums.org/showthread.php?t=1628529&page=8](http://ubuntuforums.org/showthread.php?t=1628529&page=8)

i did this, I can now see the contained files and sync music to it but not update the itunes db, no new files are shown.. however i can delete them out again :-/

---

### Post by conorsulli on 2011-01-05
and here 
[http://guide.ubuntuforums.org/showthread.php?t=1654861](http://guide.ubuntuforums.org/showthread.php?t=1654861)

---

### Post by DShad on 2011-01-05
> **jameskevindoyle said:**
> Found an answer to one of my questions in the forum thread I mentioned before, [slcpunk]("http://ubuntuforums.org/member.php?u=956482")'s iphone4 is jailbroken:
[http://ubuntuforums.org/showpost.php?p=10128133&postcount=81](http://ubuntuforums.org/showpost.php?p=10128133&postcount=81)



Is this how to get around libgpod not being able to work with the 4g hash?

Is jailbreaking the only way to do this?  Meaning for a 4g you have to decide between iTunes and jailbreaking in order to sync music to it?

Hi James,

I experienced the same with my iPod 4g...  Dd you try to jailbreak your iPod and if you did, does it make a difference?  Can you finally see the files after ejecting your pod?

Thanks for your help.

---

### Post by DShad on 2011-01-05
Have a look at this:

[http://cogizio.org/operating-systems/ubuntu/3089](http://cogizio.org/operating-systems/ubuntu/3089)

I'm gonna try this and let you know if it works...  With Banshee.

---

### Post by conorsulli on 2011-01-21
Had both banshee and rhythmbox working perfectly, I did a few things, restored my ipod too, updated and had a few issues to get it working again :-/ 

will post if i succeed again - it seems that a few things were going on in the ppa , my suspisions is that it now works with dbversion5 and i was stuck on 2? 

a guess only

---

### Post by conorsulli on 2011-01-21
sudo add-apt-repository ppa:pmcenery/ppa && sudo apt-get update

sudo apt-get dist-upgrade

[COLOR="SlateGray"]The following packages will be upgraded:[/COLOR]
*libgpod-common libgpod4 libimobiledevice1 libusbmuxd1 usbmuxd*


sudo apt-get install ifuse libimobiledevice-utils python-imobiledevice

[COLOR="Gray"]plug in ipod touch 4g - don't initialize anything if rhythmbox dialog pops up, especially if you have done so already with iTunes - i don't think this should happen anyway unless it is just out of the box[/COLOR]


That will get your ipod seen, however working is a different storey if its not jailbroken down to DBversion "2" from 5 - and even that method seems broken with the latest updates I performed on thurs 20 jan 11, the ppa did undergo updates the last week so its normal for that to happen

Ive accepted defeat for now running a dual boot once again - but I will totally look out for a fix as iTunes is completely anal with flac libraries and I dont have the time to be trans-coding them myself with even more bloatware :-(

keeping an eye on that PPA!

---

### Post by Smiff2 on 2011-09-19
no progress on this?

iPhone4 running IOS 4.2.1 from last November (nearly a year old!)
Ubuntu 10.10 with all latest updates from PPAs.

can mount iphone, can transfer tracks, but "No Content Found" error after unplugging.

very disappointing.. i realise this is Apple's fault but has the hash system in nearly one year old iOS 4.2.1 still not been reverse engineered?

---

