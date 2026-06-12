---
title: "Low Resolution Only Matrox G100---NEED HELP PLEESE!!!"
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by adMOMistrator on 2006-08-16
I really hope that someone can help me here.  I am a homeschool mom who has been thrown into the job of network administrator.  So I upgraded the kids pc to Edubuntu coz Win 2K Pro stinks and Edubuntu looked so perfect for us.  The trouble that I have is I am stuck at 640 x 480.  I do not have an option for any other res on the menu.  I tried to do the xorg thing yesterday, but messed it up so bad that I got some message that it couldn't load something and ended up re-installing---same thing.

When I looked at the device manager it had listed together
Matrox Graphics MGA G100 (Productiva) AGP.    It is listed as a PCI device.  AND  Intel 440 BX/ZX/DX-82443BX/ZX/DX AGP.  It is also listed as PCI.

I think this might be the monitor--
Platform Device (VGA 16fb) vga16fb

This setup worked fine on Win 2KPro, res high enough that you couldn't read on the 14" monitor (old-at least 10 yrs or more).

So--probably what I will be told is to do the xorg thing and thats cool, but could I please get the info in BABY STEPS.  I am totally new to linux and am in a terrible hurry--we have internet classes that are starting on Monday and I would really like it if the kids could use that pc.

Thanks So Very Much
Danielle

PS--I have been using open source software on windows for a few years and can get around windows pretty well--this is just so new, and I don't have time for the learning curve right now.

---

### Post by tseliot on 2006-08-16
Try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by IYY on 2006-08-16
Don't forget to make a backup of your Xorg file this time:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Basically, you want to add your desired resolution to the list in the following section:
```

Section "Screen" 
  Identifier "Default Screen" 
  Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
  Monitor "CM752ET" 
  DefaultDepth 16 

  SubSection "Display": 
    Depth 16 
**    Modes "1280x1024" "1024x768" "800x600"**
  EndSubSection 
EndSection

```

It will look somewhat like this (but of course, the values for the Device and Monitor will be different, so you can't just copy/paste this code). The bold line is the one you need to change, and add the resolution you want.

To edit the xorg file you can use the following command:
```

sudo nano /etc/X11/xorg.conf
```

After making your changes, type Ctrl+X, and then Y to confirm saving.

---

### Post by wagerrard on 2006-08-16
A Matrox G100 is pretty old. In addition to setting the mode lines, search the web for the specs for your monitor.  If you can determine the precise vertical and horizontal refresh rates for your monitor, you can replace the numbers that are in the xorg.conf that Ubuntu generated.  In theory, that should provide a better image.  Good luck.

Also, [www.dotfiles.org](www.dotfiles.org) -- a collection of some congifuration files submitted by users, has a config file for the Matrox Millenium II card, which was also a 4-meg card. Go to [http://www.dotfiles.com/index.php?cat_id=10](http://www.dotfiles.com/index.php?cat_id=10) and page down until you see "XF86Config for Matrox Millennium II 4MB PCI".  The file is for XFree86, which is more or less the predeccesor to Xorg, but the differences in the config files are nonexistent. Check the "SubSection" tagged "Display" and copy the modelines. 

The resolution a card can deliver depends on the amount of memory.  With a 4-meg card, I'd settle for 1024xx768.

---

### Post by adMOMistrator on 2006-08-17
Another question--When I did xorg config the other day, I ended up with a bunch of questions about everything (keyboard, mouse, monitor) that I had no idea what to answer.  I couldn't even figure out how to disable that res on the little list of resolutions to try.  Was I at the wrong place?  If not, what do I do about that, especially since I only need to change the res? 

 Also, if I manually set the res #'s do I use the max or do I use a list if I want more than one? Just curious.

I know these are probably stupid questions, and I'm sure that I'll have a couple more--but thanks so much for all the help allready.  The ChangeResolution Ubuntu looks very helpful as does everything.  I am surprised that I hadn't found it with all the searching I've been doing.

Have A Good Day!

---

### Post by adMOMistrator on 2006-08-17
Ok I started with the backup and got this message:

cp: missing destination file operand after '/etc/X11/xorg.conf_backup'

Where do I want it to go, and how do I tell it?

Thanks a Bunch

---

### Post by blackened on 2006-08-17
Just copy and paste this code.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

And if that doesn't work (I can't imagine why it wouldn't), then try this:

```
sudo touch /etc/X11/xorg.conf_backup
```

and then again

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by adMOMistrator on 2006-08-17
:-)  :-)  THANK YOU ALL SOO MUCH!!!

Its working now-yea!!!

But i gotta tell you I thought that I went somewhere really bad while I was doing it.  Ended up in the questions and just escaped out of all the ones I didn't know.  Finally figured out the checkboxes on the lists too.  

Have A Beautiful Day!!

---

### Post by blackened on 2006-08-17
I don't even want to admit how long it took me to figure out that you have to use the spacebar to check things in interactive cli programs. It's just shameful. :)

---

### Post by adMOMistrator on 2006-08-17
LOL!  I hear you.  Does seem like maybe they should come up with some documentation for these silly little things, like a Quick start guide.  I'm sure that this kind of info is old hat to Linux users, but it would be much less frightening for Wdw's users to migrate if there was one place to go and have someone hold your hand through the basics.  Now I'm fighting with trying to get the plugins in Firefox and first one, Flash, tells me to open a command line in a certain directory.  Huh?  I keep trying to no avail.  But I just found some instructions maybe, so.....I have my fingers crossed.

Enjoy the Day!

---

### Post by blackened on 2006-08-18
For that I would suggest using Automatix. It makes the process absolutely simple.

---

### Post by adMOMistrator on 2006-08-18
Thanks!  I found it allready, and man am I glad.  It was awesome.  I had tried Easy Ubuntu the day before and it did ok on the pc with the res trouble, but it broke my laptop-started making these grinding noises and wouldn't load Anything-had to reinstall Edubuntu.  And Easy didn't do half of what Automatix did.  Those Firefox plugins are soo hard to get in sometimes-even in Wdws.

:-)

---

