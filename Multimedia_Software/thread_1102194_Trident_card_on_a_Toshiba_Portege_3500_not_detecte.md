---
title: "Trident card on a Toshiba Portege 3500 not detected"
date: 2009-03-21
forum: Multimedia Software
---

### Post by Albator on 2009-03-21
Hi, 

I recently installed Ubuntu 8.10 on a Tablet PC Toshiba Portege 3500.

Almost all of its hardware is detected nicely but the Trident video card is not.

This results in a max resolution of 800x600 and a black band around the screen of about 1" thick. 

The GUI is Gnome 2.24.1. 

I seem to have installed XDM also and configured it (probably not adequatly mind you...) and the only difference is the logon screen so far. 

I found some posts about later on how to configure my screen rotation with WACOM and to enable my Stylus pen but this will be another post once I get the screen going right.

The xorg.conf has almost nothing in it:

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"  "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Configured Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
End Section

Thats about all the info I got. Oh yeah, I downloaded the :
xf86-video-trident-1.3.1.tar.bz2  driver package. Where should I extract it? and how do I activate it since I do not find a ./install file?

Thx in advance

---

### Post by Favux on 2009-03-21
Hi Albator,

I should be able to help.  Go to this thread:

[http://ubuntuforums.org/showthread.php?t=1029397&highlight=tablet]("http://ubuntuforums.org/showthread.php?t=1029397&highlight=tablet")

and look at the xorg.conf on posts #4 and #11.  Be sure to back your xorg.conf up first and compare to the new ones to see what changes are made.

Then feel free to join us on this thread:

[http://ubuntuforums.org/showthread.php?t=1053210]("http://ubuntuforums.org/showthread.php?t=1053210")

where we are working on rotation.  Another 3500 user justind, just joined us on the first link today and may be posting on the second link today.  It would also be a good thing if you posted on the bug link.

I hope this helps.

---

### Post by matthewVS on 2009-03-25
I am a newbie. I installed Ubuntu 8.04 LTS on a toshiba portege 3500 and also do not have proper resolution. I am not interested in rotation or wacom at this point. I just want xorg to recognize my video card so I can boost the screen size to full screen instead of the black band all around. I have no idea how to edit/change xorg.conf. I did find a package that said it has trident drivers but installing it made no difference. (I assume I did not install it right) Can some one point me in the right direction?

---

### Post by Favux on 2009-03-25
Hi matthewVS,

Welcome to Ubuntu!

To edit xorg.conf you have to be root.  In a terminal (CLI-command line interface) you'd type "sudo" then it would ask for your password.  Since you probably want to use a gui program to edit you would use "gksudo".  gedit is included in ubuntu.  The xorg.conf lives in /etc/X11 so you'd type:
```
gksudo gedit /etc/X11/xorg.conf
```
As you know if you mess up xorg.conf you may not be able to boot into your gui so you want to be careful and back it up.  To back it up:
```
cp /etc/X11/xorg.conf /etc/X11/my_xorg.bak
```
or whatever name you want.  To restore the back up you just reverse it.
```
cp /etc/X11/my_xorg.bak /etc/X11/xorg.conf
```
It sounds like you need to tell xorg.conf to use the trident driver.  Ubuntu already has Xorg's trident driver.  You know about the other 3500 xorg.conf's referenced.  If you have questions ask.

Good luck!

---

### Post by matthewVS on 2009-03-26
I made a back up copy of the file the other day. When I try to edit the file in the manner you say to the screen opens up as blank. I would expect at least some text because everything else (sound,touchpad mouse,ect) work fine. Then the moment I make changes to the file an asterisk show up next to the name of the file in the tab and when I try to save the file I get the following message: **Unexpected error: File not found** I cannot save the file. I know I am in root when I am doing this

---

### Post by Favux on 2009-03-26
Hi matthewVS,

Weird, maybe that's the problem?

You should be able to use Nautilus to look at the file.  Use Places (Nautilus) on the top menu bar.  Click on home folder then click on file system.  Then on etc then X11.  See if there is an xorg.conf.  It will let you look in the xorg.conf but not edit it because you're not root.  Is it there?  Is there anything in it?

---

### Post by matthewVS on 2009-03-26
Yes, the file is there. It is not blank. It has the standard statements at the beginning followed by data such as generic keyboard,configured mouse, synaptics touchpad then it goes to the video device, monitor, and screen sections which are all blank.:confused:

---

### Post by Favux on 2009-03-26
Hi matthewVS,

OK, my guess is you typed x instead of X for X11.  I'm going to try and pull out a xorg.conf for you.  This is kind of tough because I can't just compare gorcq's to littlematt's.  His is very complicated and I thought he was running two monitors, but he said it was the only way he could get it to work on his laptop??  So this will take a little while.  In the meantime you could post your current xorg.conf and learn about xfix, in case it alls goes wrong.  It's here:

[http://kshoster.net/index.php?c=tuts/xfix]("http://kshoster.net/index.php?c=tuts/xfix")

---

### Post by matthewVS on 2009-03-26
Xfix did not fix. I retried making sure to use the proper capitalization but got the same results. I have attached the xorg.conf file that was created by xfix (at least the date code embedded in the file name indicated that and the file was not there before) Any suggestions that I can try tomorrow will be appreciated. I'm getting to the point where I should stop for the day before I make big mistakes.

---

### Post by Favux on 2009-03-26
Hi matthewVS,

I did not want you to run xfix, I wanted you to know about it in case the new xorg.conf broke things.  But you said you earlier saw a file with Nautilus with stuff in it.  What file was that?  Didn't it have keyboard, etc.  That's what I wanted.  Is it still there?  What is the path?

But what you now posted is interesting as it looks like littlematt's.  But it worked for littlematt.  A very messy video section.  I think littlematt had a different Trident driver than the others, that may be the difference.  I'll try to figure that out.  Meanwhile go to Synaptic Package Manager in System>Administration and see if you can figure out what version of the Xorg Trident driver you have.  Search Trident.  Do you know the version of the Trident chipset you have?

Hang in there.  This just looks tougher than it is because you're new.

---

### Post by Favux on 2009-03-27
Hi matthewVS,

Amazingly your xorg.conf and littlematt's on post #15 on this link [http://ubuntuforums.org/showthread.php?t=1053210]("http://ubuntuforums.org/showthread.php?t=1053210") are almost identical.  The trident driver he has is xserver-xorg-video-trident 1:1.2.4-1, or v. 1.2.4-1 in other words.

The difference is yours:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection
```
and his:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"
	EndSubSection
EndSection
```
So you could delete the lower resolution modes (to look like littlematt's), which are probably giving you the black bar.  Or use the "PreferredMode" option in the "Monitor", which should also work.
```
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
        Option	"PreferredMode"	"1024x768@60"
	Gamma	1.0
EndSection
```

I'm tempted to try the much simpler video section of gorcq but since your xorg.conf looks so similar to littlematt's...  If you have the same vide driver go for it.  If it is a different version from littlematt's, let's rethink.  OK?

---

### Post by matthewVS on 2009-03-27
I'll try and attach actual file in use and a copy I made on the 23rd before I started trying to change any thing. Using a command I found the other day 'lspci | grep VGA' my card is reported as a Trident Microsystems Cyberblade XPAi1 rev 82 which mostly matches what windows XP reports. 
Synaptic package manager shows the following search results:
       xserver-xorg-video-trident installed version 1:1.3.0-1 and said it is the latest version and that this driver is for Trident blade/image/providia/TGUI/9xxx

---

### Post by Favux on 2009-03-27
Hi matthewVS,

OK, then you may want to use gorcq's video section.  His driver is newer than littlematt's.  Not quite as new as yours.  I just found the deb for your driver the other day and suggested the other 3500 users might want to try it.  The only thing that concerns me about it is it said it was built against Xserver 1.4 (as a reversion) while 1.5 is in Intrepid.  They didn't say why they felt the need for the reversion.  The newest one 1.3.0-2 is built against 1.5 but is in experimental and I couldn't find a deb for it.

Now the gorcq xorg.conf is a Hardy style one.  Stuff that can be commented out in Intrepid is left active.  But that shouldn't make a difference.  Take a look at it and let me know what you think.

---

### Post by matthewVS on 2009-03-27
OK it looks much better than what I have (or haven't) got. I still was having trouble editing xorg.conf. Any ideas on what I was doing wrong?

---

### Post by Favux on 2009-03-27
Hi again matthewVS,

I edit it by:
```
gksudo gedit /etc/X11/xorg.conf
```
Is that what you're asking?  Or are you asking about specific format issues?

---

### Post by matthewVS on 2009-03-27
I open the file with the command you gave me but it opens a blank file. When I paste into the editor the file name in the tab gets an asterisks before the name and when I try to save I get the error message "unexpected error: file not found" and in the terminal window is the message 
"**(gedit:7982):WARNING**:Hit unhandled case 1`(file `not found) in gedit_unrecoverable_saving_error_message_area_new."

xorg.conf is in the right directory but I don't seem to be able to edit it with gedit.

---

### Post by Favux on 2009-03-27
Hi matthewVS,

It's not clear to me what's happening.  You now know the file paths are case specific and you have to use X not x.  If it was a permission problem it should say that I would think.  But that's about all I can come up with.  Check really carefully the name of the file that's there.  The one you think is xorg.conf.  You could try:
```
sudo nano /etc/X11/xorg.conf
```
Nano is a CLI editor.  Make sure I'm not spelling things wrong.
The other thing would be to try using:
```
gksudo nautilus
```
after shutting everything else down except your browser (good idea in general).  Then navigate to /etc/X11/.  Then tell nautilus to make an empty text file and call it xorg.conf.  Then cut and past the xorg.conf you want into the empty text file named xorg.conf and save it.

Back in a few.

---

### Post by matthewVS on 2009-03-27
Using your second method with nautilus WORKED! The system now displays in fullscreen. I want to thank you very much for getting me to this point. It will make learning about linux much easier.:P:popcorn:

---

### Post by Favux on 2009-03-28
Hi matthewVS,

Outstanding!  Nice job!

Now you're just a hop, skip, and jump away from getting Wacom working.

I'd would also love to know (and so would several 3500 users) whether the driver version you have supports rotation!

By the way where did you get it?  You said some packages.  Also did you use the gorcq test 2 xorg.conf or did you cut and paste?

Anyway good news.

---

### Post by matthewVS on 2009-03-28
No, rotation does not work. Not a big deal to me. I had to cut and paste but I don't remember if I used the one you had or gorcq. I have both files and later I'll look and compare the files to see which one I used. Oh, and the Wacom 'pen' does work, but the laptop needs a new screen, it has areas where the pen doesn't work right so I use it as a standard laptop.

---

### Post by Favux on 2009-03-28
Hi matthewVS,

Sorry to hear that, both about rotation and your screen.  Have you tried contacting Wacom and see if there is anything simple you can do to fix the screen?  If most of the grid is active and only a part is not conducting-does that imply a fairly "easy" fix?  Fix insulation on the LCD edge or something.  It may be as simple as one of the connectors from the digitizer being loose or corroded.  It can't hurt to ask them.  If you find anything out let me know.  I may be needing that info in few years too!

---

### Post by matthewVS on 2009-03-28
I'll ask them at some point, but it is not a high priority at this point. If I do learn anything I'll let you know.
 As far as which file, I copied gorcq. It was the number of resolutions that gave it away...jumps from 800 x 600 to 1024 x 768 with nothing in between.  Next thing I'll look`into is anti virus...AVG doesn't quite run right on this yet. Maybe I am missing some of the dependencies they talk about in their manual.

---

### Post by Favux on 2009-03-28
Hi matthewVS,

No urgency on an anti-virus in linux.  It's not like Windows.  As far as I know there still isn't an example of a virus in the "wild" with linux.

---

### Post by ShadowTachi on 2009-05-31
> **Favux said:**
> Hi matthewVS,

OK, then you may want to use gorcq's video section.  His driver is newer than littlematt's.  Not quite as new as yours.  I just found the deb for your driver the other day and suggested the other 3500 users might want to try it.  The only thing that concerns me about it is it said it was built against Xserver 1.4 (as a reversion) while 1.5 is in Intrepid.  They didn't say why they felt the need for the reversion.  The newest one 1.3.0-2 is built against 1.5 but is in experimental and I couldn't find a deb for it.

Now the gorcq xorg.conf is a Hardy style one.  Stuff that can be commented out in Intrepid is left active.  But that shouldn't make a difference.  Take a look at it and let me know what you think.


This is my first working Linux. I've been having the black bar blues as well. After reading through the forum for a day or so, I found this and it's been a lot of help. I tried cut and paste with the whole thing and it didn't work with my set up but with a few mods, I'm bar free. Thanks for putting that out there.

---

### Post by Favux on 2009-05-31
Hi ShadowTachi,

Welcome to Ubuntu!

Thank you very much for the thank you.  I'm glad the xorg.conf helped.

If you are using Jaunty that may have been part of the problem.  They've made changes and are deprecating xorg.conf.

---

### Post by ShadowTachi on 2009-06-01
Using Ubuntu, newest version. If the rest of the glitches smooth out this easy, I'm dropping windows off here all together, until then I still have a dual boot set up.

---

### Post by ShadowTachi on 2010-02-01
UGH! Down loaded Ubuntu and made a disk. Went with a full install and booted windows all together... now I'm back to the black bars again and can't find anything on my computer for xorg.conf except a file explaining what xorg is. There doesn't seem to be an actual xorg.conf. I've tried running searches for it and still find nothing. I'm stuck.

---

### Post by Favux on 2010-02-01
Hi ShadowTachi,

Karmic (which is what it sounds like you just installed) doesn't have a xorg.conf if the video driver is a Xorg driver.  So nVidia will have an xorg.conf but not Trident, which is Xorg.  So you need to create one:
```
gksudo gedit /etc/X11/xorg.conf
```
Then put all your video sections in there along with the "ServerLayout" with the video lines.

Something like:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0	"Default Screen" 0 0
EndSection
```
Or whatever your lines look like.  Then again it may want:
```
Section "ServerLayout"
	Identifier	"X.org Configured"
EndSection
```
Or maybe not since you are configuring it manually?

---

### Post by ShadowTachi on 2010-02-01
I was just learning and something happened with Ubuntu and it wouldn't boot so I stopped messing with it. Now I'm back to square one.
Funny thing is, I jacked the config and it only wants to run in low graphics mode now. Low graphics mode gets rid of the bars and lets me step up the resolution.


I love this. Since I created the xorg.conf, even though it was jacked up, it made it possible to edit it using littlematt's example. No more black bars and I'm now at 1024x768 resolution, perfect on a 12.1 inch screen.

Thanks Favux for the help, it got me the start I needed.

---

### Post by Ghirkin on 2010-04-14
I'm also new to linux and also having the problem with the p3500 (the 1 inch black border) I've tried using various xorg.conf files posted as attachments, but none of them seem to work, they cause it to display a black screen with flickering green lines after the Ubuntu splash screen. The only way I've found to fix it is to remove xorg.conf in recovery mode. 
By default xorg.conf was not present :confused:
I checked to make sure I had the driver, searching for 'Trident' in Synaptic shows that 'xserver-xorg-video-trident' version 1:1.3.3=1 is installed...

Would love to get it working at full resoloution, dont care too much about rotation and pen support [lost the pen :(]

---

### Post by matthewVS on 2010-04-17
hi Ghirkin,
it was a while since a got my screen to work right so my memory may be off a little but this is what I remember:
first: make a back-up copy of x-org.conf first!!
I used one of the links in this forum to find a copy of an x-org.conf file that worked (maybe it was from 'littlematt'?) then I opened gedit through the terminal screen. I had to open gedit with no file specified then open x-org.conf otherwise I couldn't save the file for some reason. I then replaced the sections from the one I got through the forums. I have made a minor modification to it since but nothing major.

I'll see if I can attach the sections of the file that made it work for me.

---

### Post by Toxicstupidity on 2011-01-31
Im having the same problems but my gedit is blank??? What do i do?

---

