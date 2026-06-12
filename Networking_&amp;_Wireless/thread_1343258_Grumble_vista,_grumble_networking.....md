---
title: "Grumble vista, grumble networking...."
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by Laphayette on 2009-12-01
So I would like to report that I am a happy new user of Ubuntu, but right now I keep hitting walls that are driving me nuts.
   I have an old comp with a 60 gig drive, with one partition that “runs” windows xp media centre (but that doesn’t work right now because I put in a new/old motherboard and xp won’t recognize it.  I have a legit key for the software but I can’t find it and I can’t recover the key right now.  But that’s another story).  So I decided to use GParted, cleaned up the hard drive a bit, and installed Ubuntu.  The reason for this is I want to use the desk top as the main place for a network.  I have an external 500 gig hard drive with music, movies and such and I want that hooked up to the desktop so I can access it with my laptop, which is running Windows Vista basic.  Saves me from lugging the drive around the house.
  The problem is I can’t get a network going.  I just did another re-install on the off chance that I did something wrong the last time but I still can’t get it working.  So here’s a detailed explanation of everything.
  Did the install from the live CD, after that was all done and Ubuntu was up and running, I did an update for a driver for my video card (nvidia), and than I did the update manager which had 143 things to update.
   After those two updates, when I start up the comp, it recognizes that windows xp and Ubuntu are there.  There are a bunch of booting options and they are as follows: Ubuntu, Linux 2.6.31.14 and 2.6.31.15 generic and recovery mode for each, windows xp and two different memory testers.  I start up with Ubuntu, Linux 2.6.31.15 generic.  
  So I try to set up a sharing drive and option.  ( I follow the tutorial found on the subject here [http://www.youtube.com/watch?v=89hjWOb8qmY&feature=related](http://www.youtube.com/watch?v=89hjWOb8qmY&feature=related) and followed it precisely and everything looked the same as it did on the video.)  So I made a folder on the desktop, put in a screenshot of the desktop.  Right click, and go to the share folder option, click the share this folder button, and I get the sharing service is not installed, so I install it and reboot the system when it’s done.  After that, I make sure that the network name is the same in both machines, which is the nice generic name of WORKGROUP.  No problems.  I right click on the folder, click the sharing options, and check all three spots available.  
  When that’s done, I go to my windows machine to see if things are all good, and they are not.  Nothing appears.  So I shut down the Ubuntu machine just in case that’s what needed, and when it starts up, the icon on the folder that says it’s a shared folder, is gone, ad it’s not a shared folder anymore.  So I think that it might have to do with the desk top, so I go into the external  drive (500 gigs, partitioned three ways) and share a couple of those folders, three from each partition.  Restart the comp, and some of the files stayed shared, some didn’t.  Some will be shared, but without the icon on the folder.  No patters with this what so ever.  
   I am a real beginner at networking, never set one up before.  Do I have to do anything in Vista to allow me to network with the Ubuntu system?  The name on my Vista network would appear to be “WORKGROUP”, so that’s the name that I setup on the Ubuntu system.   When I open the Network  tab in Vista, I see the laptop and the router, but not the Ubuntu computer.   When I open the Network tab in Ubuntu, I can see the Vista computer, but I can’t access it.
  Can someone please tell me what I’m doing wrong... any help would be greatly appreciated.  I know I wrote a lot, but better than questions going back and forth...

  Thanks all...

---

### Post by Iowan on 2009-12-01
A couple more How-To's for you:
[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")
[https://help.ubuntu.com/8.10/internet/C/networking-shares.html]("https://help.ubuntu.com/8.10/internet/C/networking-shares.html")

---

