---
title: "Big media problems with 10.10"
date: 2011-02-25
forum: Multimedia Software
---

### Post by studdard on 2011-02-25
Hi all

I've had Ubuntu on my laptop for a while and was really impressed with it. I decided to have a dual install with XP on my desktop today. I used a CD from a magazine and opted to have the install "within" the existing filesystem. I didn't use wubi - this was one of the options when I put the CD in the drive. 

I booted into Ubuntu and went into my external hard drive to play some music. Nothing could play. It kept trying to open files such as mp4 in a window called "video player" and then asking to connect to the internet to find codecs which it then couldn't find. One filetype, I forget which, tried to open in Rhythmbox to play but then wouldn't play. 

I tried to download trusty VLC from the software centre. VLC came up when I typed it into the search field but there was no "call to action", just a button that said "more info". I was told that it is available from the "universal source" though I don't know what this is. I tried to get the source but the OS seemed to glitch or crash during the authenticate process. I therefore couldn't get VLC. 

Can anybody help?

Thanks in advance.

---

### Post by Terry of Astoria on 2011-02-25
You will want to enable the "Universe" software repository. VLC is in it.Look in Synaptic Package Manager. Click "settings" - "repositories" - Look around there. You'll see what I mean. You have to enable the repositories or sources for the programs you want to install via the package-manager.
  Read the official directions in this 
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683).

Actually I prefer this guy's instructions for enabling media:
[http://ubuntuforums.org/showthread.php?t=1469825&highlight=Ubuntu+Desktop+Computing+Made+Easy](http://ubuntuforums.org/showthread.php?t=1469825&highlight=Ubuntu+Desktop+Computing+Made+Easy)

I suggest using one or the other of the sets of instructions described above to enable media playing . . . In either case, read carefully from the start and do the relevant procedures in order.

---

### Post by studdard on 2011-02-25
Thanks but I went into "settings" - "repositories" in the synaptic package manager and couldn't find the word universe anywhere. 

Also [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) says that "In Ubuntu 9.04 (Jaunty) and later, the main, universe, restricted and multiverse repositories are enabled by default." Since mine is 10.10 won't universal "packages" be enabled by default?

---

### Post by emptythevoid on 2011-03-01
Go to your System menu, go to Administration, Synaptic Package Manager.

Once that opens, go to Settings, Repositories and make sure the following are checked:
Canonical-supported
Community-maintained
Proprietary Drivers for devices
Software restricted by copyright

The only ones you really need to be concerned about are "community maintained" and "restricted by copyright", but this is how mine is set up.  Once you make the change, it'll ask you to press the reload button.  Make sure you're connected to the internet and then do this.  When you open up a media file, Ubuntu should at least attempt to detect and download the codec (if you're connected to the internet).  Adding the "community-maintained" software source should also let VLC be available for download.

I like to install the package ubuntu-restricted-extras to give me all the codecs I need, but this is a sledgehammer approach, and may not cover all media files.

---

