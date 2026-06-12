---
title: "some dvds simply won't play!!!!"
date: 2017-01-06
forum: Multimedia Software
---

### Post by christon74 on 2017-01-06
Hello fellow-ubunters. 
"1746, the last highland charge" won't play:confused:. There once was a time, not long before we all had to upgrade to 16.04, when it would.  Usually, when you insert a dvd in the drive there is a pop up that asks you what you would like to do, and lets you choose the software you want to play your disc. Not this time. A window opens which only contains the audio file.  VLC won't play this DVD, neither will Parole nor KMPlayer.
Is there any universal DVD player which will play all DVDs, irrespective of the file format, whether it's pal, ntsc, vob....

Thank you in advance for any piece of advice.
I have just tried Kaffeine but it says "error NAV packet expected but not found". It also seems something went wrong during the installationof Kaffeine.

---

### Post by #&amp;thj^% on 2017-01-06
Maybe related to this: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by QIII on 2017-01-06
Hmmmm.  I must not have gotten the memo that we all had to upgrade to 16.04.

---

### Post by deadflowr on 2017-01-06
Try removing (or moving) your ~/.dvdcss folder.
See if you ran into a similar problem as this:
[https://bbs.archlinux.org/viewtopic.php?pid=1350974#p1350974]("https://bbs.archlinux.org/viewtopic.php?pid=1350974#p1350974")

---

### Post by christon74 on 2017-01-06
Thank you 1fallen and QIII
Here are all the packages already installed:
  	 	 	 	   libdvd-pkg
 libdvdnav-dev
 libdvdread-dbg
 libdvdread-dev

 libdvd-css2

 libdvdread4

 libdvdnav4

 
I have just installed "libdvd-pkg" _ and it seems that something went wrong this time yet again:

  	 	 	 	   
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:20
 W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:20
 W: Target Translations (universe/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:20
 W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:20
 W: Target DEP-11 (universe/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:20
 W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:20
 W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:30
 W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:30
 W: Target Translations (multiverse/i18n/Translation-en_GB) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:30
 W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:30
 W: Target DEP-11 (multiverse/dep11/Components-i386.yml) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:30
 W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:9 and /etc/apt/sources.list:30

---

### Post by deadflowr on 2017-01-06
The warnings are just that, warnings.
You seem to have duplicate entries in your sources.list file.
You'll want to open it and review which.

---

### Post by christon74 on 2017-01-06
Gripes! move or remove my ~/.dvdcss folder? I am 100% certain I do not know how to do that!

---

### Post by deadflowr on 2017-01-06
Open your file manager (on pure Ubuntu it is called Files)
You need to set it to view hidden files/folders (pressing ctrl +H will set it to view hidden)
Scroll down and you should see a folder for dvdcss.

right click on it and choose to 

1)move it somewhere else (perhaps put it in a another folder)

2)move it to trash

3)rename it some different name

Pick one.

(your call)

ftr: the ~ symbol is a nifty shorthand for your home folder.
just in case you where wondering about that...

---

### Post by christon74 on 2017-01-07
Thank you ever so much deadflower. I have just done that this morning (moved the dvdcss to the rubbish bin. I'm going to try playing this DVD again. Starring in it are Brian Blessed, Iain Cuthbertson, Jake D'Arcy, Carolyn Konrad and "Fish" from the band Marillion.

---

### Post by christon74 on 2017-01-07
Not to much avail have I thrown the dvdcss folder. The DVD still does not play.  When you start it, you get this screen with a photograph and captions displayed: "Play video/ Scene selection/ Battlelines/ Music video / cinema trailer. But clicking "play video" simply causes VLC to shut down.
What's more, when the DVD is inserted into the drive, what is displayed is just the audio files (which is empty) I had to boot vista to find the video files, copy them to an external hard drive. Now I can watch "1746" sliced in four sequences appromimately 30 minutes duration each.

---

