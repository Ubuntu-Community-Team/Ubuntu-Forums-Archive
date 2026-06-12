---
title: "Mythbrowser(SVN 0.21)+Flash"
date: 2008-03-05
forum: Mythbuntu
---

### Post by teetniin on 2008-03-05
Hi

 I'm using Mythbuntu 8.04 alpha, mostly it works great :)!
I was surfing around wiki.mythtv.org and found that mythbrowser(0.21) supports external plugins(like adobe flash).
Only problem is it requires konqueror flash plugin. It means i have to install konqueror under mythbuntu and if konq. works, mythbrowser will work too.
I tried with gnash(open source flash plugin) got youtube video window(both in konqueror and mythbrowser) but didn't get the video.
Tried to install adobe flash(installer succesfully) but configuration options under konq. have some error(missing components, its doesn't say which are missing).
If anyone has successfully got mythbrowser showing flash content, then i would really happy to read some pointers or mini How to :)

TIA
Teet

---

### Post by ahood on 2008-03-15
Me too. I would like to use Mythbrowser to watch hulu videos, but the videos don't play. I am running Mythbuntu gutsy and the latest official repository packages (0.21).

---

### Post by superm1 on 2008-03-15
If you guys sort out what's necessary, please file a bug against mythplugins to add the applications to recommends on mythbrowser.

---

### Post by ahood on 2008-03-15
Thanks for replying. What is the URL for submitting the request? I want to be sure I do it correctly.

Thanks in advance,

---

### Post by Kyle138 on 2008-05-10
Did anyone ever figure this out?

---

### Post by laga on 2008-05-10
You'll probably also need the 'konqueror-nsplugins' package.

---

### Post by fenian on 2008-06-18
First install Konqueror and flashplugin

> sudo apt-get install konqueror flashplugin-nonfree

Then open konqueror and go to the menu Settings>Configure Konqueror
Select plugins from the menu on the left
Click the new button and in the box to the left enter...

> /usr/lib/flashplugin-nonfree

Exit konqueror

Flash should now work in mythbrowser.

---

### Post by yojimba on 2008-08-19
> **fenian said:**
> First install Konqueror and flashplugin



Then open konqueror and go to the menu Settings>Configure Konqueror
Select plugins from the menu on the left
Click the new button and in the box to the left enter...



Exit konqueror

Flash should now work in mythbrowser.


Clean install of Mythbuntu 8.041. Konqueror and flashplugin-nonfree added through package manager. Also 'konqueror-nsplugins' package is installed. 

Unfortunately Flash pages not working and requesting flash download from applicable sites for me.

---

### Post by laga on 2008-08-19
Does it work in konqueror?

---

### Post by yojimba on 2008-08-19
No it does not . . .

Here are the errors from the terminal:

jim@jim-htpc:~$ konqueror
Zlib data error : (null)
Unable to read ZLIB data
Improper call to JPEG library in state 202
Unable to read JPEG data
Improper call to JPEG library in state 202
Unable to read JPEG data
Zlib data error : invalid distance too far back
Unable to read ZLIB data

---

### Post by elliott6 on 2008-08-19
> **fenian said:**
> First install Konqueror and flashplugin
Then open konqueror and go to the menu Settings>Configure Konqueror
Select plugins from the menu on the left
Click the new button and in the box to the left enter...

Exit konqueror

Flash should now work in mythbrowser.

Hey there, I just tried the above and it worked like a champ (sort of)!  Wish I would have had this for the PGA Championship a few weeks ago.

Anyway, a part that I think was missed is the after above, and prior to the exit of konqueror, there is a button to Scan for new plugins.  After clicking this button, and then closing out, I was able to view flash in konqueror.  And then after, I know can view flash in Firefox, or mythbrowser!

Thanks!  And good luck!!!

Sean

---

### Post by stillboy on 2008-11-22
I installed konqueror and got that to show flash plugins just fine (after hitting scan for plugins on the plugins setup page) although mythbrowser does not seem to want to use the flash plugins.

---

### Post by penbrock on 2008-11-22
> **stillboy said:**
> I installed konqueror and got that to show flash plugins just fine (after hitting scan for plugins on the plugins setup page) although mythbrowser does not seem to want to use the flash plugins.

Same here. I can get it to work fine now in Firefox and Konqueror but not in MythBrowser

---

### Post by EasyRiderOnTheStorm on 2008-11-23
I can't get it to work either. Oddly, it DOES work in Firefox (after installing Konqueror), but it does not in either Konqueror or Mythbrowser. Go figure... :(

---

### Post by penbrock on 2008-11-26
Anyone having any luck with this yet?

---

### Post by fatmonk on 2008-11-29
Is it right that Konqueror can't be installed without first installing KDE?

Is it safe to install KDE on a Mythbuntu system or will it affect XFCE etc?

Can anyone advise the minimum packages required to get this working?

Ta,

FM

---

### Post by 4ebees on 2009-01-25
> **fatmonk said:**
> Is it right that Konqueror can't be installed without first installing KDE?

You can install Konqueror without the whole of KDE.


> Is it safe to install KDE on a Mythbuntu system or will it affect XFCE etc?

Hasn't created any problems for me :)


> Can anyone advise the minimum packages required to get this working?

To quote Fenian further up:

> sudo apt-get install konqueror flashplugin-nonfree

---

### Post by jdeslip on 2009-02-19
I am using mythbuntu 8.10.  I got flash to work in konqueror by dropping back to the old version 9 of the flash plugin (version 10 does not work with konqueror apparently).  However, mythbroswer still says flash is not installed.  I suspect this is because 8.10 comes with version 4 of konqueror and mythbroswser wants 3.5?  Is there a way to overcome this?

---

### Post by jdeslip on 2009-02-19
Ok, I got it working!!

I installed konqueror-kde3 from these instructions: [http://ubuntuforums.org/showthread.php?t=963695](http://ubuntuforums.org/showthread.php?t=963695)

I created a new directory called /opt/flash9 where I put the libflashplayer.so from a flashplayer 9 archive:  [http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip) (I used the latest flash 9 relese).

I ran /usr/kde3/bin/konqueror and went to plugins - got rid of all the directories and added /opt/flash9 and then scaned for plugins.  It found the flash9 plugin.  

Close Konqueror.  Load of mythbrowser and flash and hulu is working!

---

