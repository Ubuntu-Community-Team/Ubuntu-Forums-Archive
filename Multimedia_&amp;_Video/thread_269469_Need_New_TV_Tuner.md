---
title: "Need New TV Tuner ?"
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by confusimo on 2006-10-01
I also need a new tuner. I have DD 6.06 64bit Ubuntu.

So like the hauppauge 33801 was mentioned here a few times.  If got one like of ebay of course or what have you. Would that work without recompling the kernal or adding any files right out of the box.

Or I found a kworld pci based on 878 (KW-TV878RF) on ebay. But I've rad here more files need to be added. Seems like a lot of work just to watch tv.

[http://cgi.ebay.com/Philips-713X-Chipset-USB-2-0-TV-Tuner-Capture-Box-MPEG4_W0QQitemZ160036484576QQihZ006QQcategoryZ3761QQrdZ1QQcmdZViewItem](http://cgi.ebay.com/Philips-713X-Chipset-USB-2-0-TV-Tuner-Capture-Box-MPEG4_W0QQitemZ160036484576QQihZ006QQcategoryZ3761QQrdZ1QQcmdZViewItem)

Or that usb philips.  Philips is also supported I've read.  But usb doesn't auto load right?

So which of the three is the better buy?

Thanks,
Confusimo

---

### Post by Neobuntu on 2006-10-01
I can't tell you about some unknown tuner card but from my experience with three of them, it's all about finding the right code for the tuner and the chip. 

I recall knoppix being instrumental in finding the right pair. I actually wrote the code numbers on the tuner shield for when I install them again (which I'm about to do.) I think any tuner can work.

What you might consider, is whether the tuner picks up stereo because they might go two channels out to soundcard but still do not pick up stereo; for you to record and without that, you can't have "prologic", which is encoded on broadcast movies for surround sound effects. It's about as good as 5 channel digital (on most DVD's.) Of cours,e plain music on two channel stereo sounds better too. FYI.

Second, if it has a remote controler, then that's one less thing you have to worry with.

I may be looking for a HDTV PCI tuner soon and building my own DVR.

---

### Post by confusimo on 2006-10-01
I already have a tuner.  But it won't work in Ubuntu with gnome 64bit Daper Drake.  See my whole story below.  So I need to know for sure.  No guessing.  No HI-DEF.  Just regular analog will do.  Jst need to watch TV.  No recording.  Just watch regular tv.

[http://www.ubuntuforums.org/showthread.php?t=265528&highlight=vvmer](http://www.ubuntuforums.org/showthread.php?t=265528&highlight=vvmer)

So I need to know which is the easiest to setup.  No recompling anything.

Thanks,
Confusimo

---

### Post by tagra123 on 2006-10-01
> **confusimo said:**
> I already have a tuner.  But it won't work in Ubuntu with gnome 64bit Daper Drake.  See my whole story below.  So I need to know for sure.  No guessing.  No HI-DEF.  Just regular analog will do.  Jst need to watch TV.  No recording.  Just watch regular tv.

[http://www.ubuntuforums.org/showthread.php?t=265528&highlight=vvmer](http://www.ubuntuforums.org/showthread.php?t=265528&highlight=vvmer)

So I need to know which is the easiest to setup.  No recompling anything.

Thanks,
Confusimo

WinTVGo cards work straight out of the box. I've used two of them with mythtv and no troubles. They are based on the bt878 chip.

By the way tvtime works well for just watching tv.

---

### Post by confusimo on 2006-10-01
Cool but how complicated would it be to setup the USB philips thing.  Would I have to recompile the kernal or change anything.

Thanks,
Confusimo

---

### Post by tagra123 on 2006-10-01
It might.

You may get some good results googling for your model tv tuner and ubuntu. See what comes up.

[http://www.mythtvtalk.com/forum/viewtopic.php?p=3225](http://www.mythtvtalk.com/forum/viewtopic.php?p=3225)

---

### Post by confusimo on 2006-10-01
No, nothing comes up and it dtects as a web cam so it not configurable.  

But the Philips USB thing.  Is philips supported or not?  And is usb not auto detect therefore mpre complicated.

Thanks,
Confusimo

---

### Post by tagra123 on 2006-10-01
I just don't know. Maybe someone who has used this will reply. I am 100% sure the pci model I mentioned works well -- from my own experience.

---

### Post by confusimo on 2006-10-01
But in general is Philips Chipset supported or not?

---

### Post by confusimo on 2006-10-02
Also is BT848 supported?  Or only BT878?

Thanks,
Confusimo

---

### Post by Neobuntu on 2006-10-05
I recall seeing those as supported, yes. It's about those settings for the 1) Tuner and 2) chipset (bttv).

Tuner card can be a bear because of all the combinations out there. 

Google searches and maybe a Knoppix Live CD to test (with Auto tuner card setup) are your friend.

---

