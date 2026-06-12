---
title: "Audio Editing programs for ubuntu"
date: 2007-01-10
forum: Multimedia &amp; Video
---

### Post by darkcyber on 2007-01-10
I'm working on switching a few of my pc's over to ubuntu.  One pc I use for audio recording and editing and I currently use Cool Edit 2000.  Since I'm sure Cool Edit probably will not work in linux, is there a good program for linux that does about the same thing as Cool Edit?

---

### Post by uuwatti on 2007-01-10
3 programs you might want to try are: Audacity, ReZound and Ardour.
ReZound and Audacity you can just apt-get. Ardour you have to compile.
[Read this.]("http://www.ubuntuforums.org/showthread.php?t=243426")
I used Audition (former Cool Edit Pro) on Windows and I find Audacity very similar and equally suitable for my needs. ReZound looks better and has fewer options I think and Ardour I never got to work properly. But, read on the subject more on these forums and find a program that suits you.

---

### Post by RaZoR-x11 on 2007-01-10
Hey there,

This might sound strange but i am using the wine win32/bin emulator 
and im running cubase VST 5.0 and cubase SX3 both run a treat + 
there very very good profession music editing tool's.

RaZoR

---

### Post by RaZoR-x11 on 2007-01-10
If you want to you cool edit. i suggest downloading Wine win32 emulator 
it should be able to run it

URL: [http://www.winehq.com/](http://www.winehq.com/)


RaZoR

---

### Post by darkcyber on 2007-01-10
uuwatti,

What do you mean by "you can just apt-get."  Total noobie here...just getting started with ubuntu.

As for as running wine and Cool Edit..I'm not stuck on Cool Edit and wouldn't mind trying something different, but all my other pc's we use Cool Edit on...so sticking with it would probably be better for the other people that have to use the pc.

On wine, do you install it and it just runs in the background or do you have to start it up say each time the pc is booted or something.  The reason I'm asking, is I have several other people that use this pc and just trying to figure out the easiest option for them...me it really doesn't matter.

---

### Post by RaZoR-x11 on 2007-01-10
Wine is a prog it's self it will run when you start a win32 app and when you quit it, it will stop wine.
it is easy to use for exp,

wine "c:\windows\notepad.exe" 

it have the file's in your home dir to unhide them use "Ctrl + H" then you will find .wine
in there is the C: drive and prog files and window's dir.


RaZoR

---

### Post by RaZoR-x11 on 2007-01-10
If you want wine go here and select your OS,

[http://www.winehq.com/site/download](http://www.winehq.com/site/download)

---

### Post by Shay Stephens on 2007-01-10
I must say, I have used cool edit 2000 for a while now and really love it.  I am currently watching the progress of jokosher, it looks similar in opperation to cool edit:
[http://www.jokosher.org/](http://www.jokosher.org/)

You can get it from the repositories if you are using edgy.

Funny, I use wine to run photoshop 7, but for some reason it never occurred to me to try running cool edit in wine...hehehe...I am going to try that this week.

---

### Post by jr.gotti on 2007-01-10
> **darkcyber said:**
> uuwatti,

What do you mean by "you can just apt-get."  Total noobie here...just getting started with ubuntu.

As for as running wine and Cool Edit..I'm not stuck on Cool Edit and wouldn't mind trying something different, but all my other pc's we use Cool Edit on...so sticking with it would probably be better for the other people that have to use the pc.

On wine, do you install it and it just runs in the background or do you have to start it up say each time the pc is booted or something.  The reason I'm asking, is I have several other people that use this pc and just trying to figure out the easiest option for them...me it really doesn't matter.

By apt-get he means you can (in a terminal) type:

sudo apt-get install rezound

or 

sudo apt-get install audacity

It will then ask for your password and then install the program for you.

For more details on apt-get....type "man apt-get" into a terminal.

-Jason

---

### Post by Shay Stephens on 2007-01-10
I just tried cool edit 2000 in wine .9.29 and it installs and when run, it shows the splash screen, but only gets to "Resetting Menus" and then just hangs.

---

### Post by darkcyber on 2007-01-10
Thanks everyone for the information...so refreshing to come to a forum and ask questions and no get flamed to death or told to just search for yourself.  This forum is far different from most.  Now if I can just get past these installation problems of ubuntu on my home pc with SATA.

Shay Stephens,

So, you are able to run Photoshop 7 with wine...great, because that's the version of Photoshop I use as well.  Thanks for the heads up that it works.

---

### Post by Shay Stephens on 2007-01-10
This is what I do to install and run Photoshop 7 with wine .9.29

Edit your xorg.conf file
```
gksudo gedit /etc/X11/xorg.conf
```

comment out the wacom tablet stuff at the top and three toward the bottom, assuming you **don't** use a wacom tablet of course.

Install Photoshop 7 from the CD
```
wine /media/cdrom0/Photoshop/Setup.exe
```

**Getting save for web to work:**
Save for Web works if you start photoshop this way: 
```
wine "c:\program files\adobe\Photoshop 7.0\Photoshop.exe"
```

Save for Web **WILL NOT** work with: 
```
wine "c:/program files/adobe/Photoshop 7.0/Photoshop.exe"
```

The pallet windows still behave a little wonky.  They don't take to manual resizing very well.  So I set them up the way I like them, then save the workspace.  So if the pallets become unusable, I reload the saved workspace to get them back to normal.  If you don't see the icons at the bottom of a pallet, switch tabs back an forth and they will show up.  And this may change as wine develops, but right clicking in the pallets can be problematic too, I use the right arrow button at the top of the pallet to do the stuff I normally would with right clicking.

So it works, it just takes a little bit of relearning and getting used to different behavior, but it works :-)

---

