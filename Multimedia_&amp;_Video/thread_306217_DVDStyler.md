---
title: "DVDStyler"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by Tim Prosser on 2006-11-24
I don't know about anyone else, but I like DVDStyler for creating DVDs as it is nice and simple.  QDVDAuthor has more options but I find it a bit flaky.

If you are using Edgy, and fancy using DVDStyler to create your iso files then....

Get the .deb file from [http://www.dvdstyler.de/](http://www.dvdstyler.de/) (I got the stable version, 1.4)

Save this somewhere and install it (I use kubuntu, so it was right click, install)

Start the application either from a terminal or the Run Command menu - command is just dvdstyler  (or create an icon)

Go to Configuration - Settings - Core

Change the first line to:

jpegtopnm "$FILE_IN" | ppmtoy4m -n 1 -I t -L $FRAME_RATE -S 420mpeg2  | mpeg2enc -f 8 -b $BITRATE -o "$FILE_OUT" $VIDEO_NORM


(ie insert -S 420mpeg2 at the end of the ppmtoy4m options)


Then you should be able to burn away....

If you don't change the configuration then you get an application crash as the mpeg2enc version in Edgy requires slightly different input from that expected.

Hope this helps someone...

---

### Post by redDEADresolve on 2006-12-12
me thanks!

---

### Post by fsman on 2006-12-12
lastest version works fine on edgy. (even though repos are from dapper).

see the wiki

[http://dvdstyler.sourceforge.net/wiki/Installation](http://dvdstyler.sourceforge.net/wiki/Installation)

---

### Post by tvphil on 2007-06-13
First of all, I have used DVDStyler for about 3 years, going back to my Suse days. Most recently, I've used it successfully in Ubuntu Edgy, using the first postings command corrections. Now that I upgraded to Feisty, I'm burning coasters after getting this warning once burning begins.................

Burning
Executing 'genisoimage -dvd-video /home/tvphil/dvd/ | builtin_dd of=/dev/dvd obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
/dev/dvd: "Current Write Speed" is 2.0x1352KBps.
:-[ WRITE@LBA=10h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( write failed: Invalid argument
/dev/dvd: flushing cache
/dev/dvd: updating RMA
/dev/dvd: closing disc

Anybody else have this problem or knows how to fix it? I also upgaded to the latest DVDStyler 1.5 and the same thing happened.

---

### Post by avik on 2007-06-14
In the spirit of this thread, I'd like to add that if you're looking for the amd64 version, it's at [http://www.getdeb.net/search.php?keywords=dvdstyler]("http://www.getdeb.net/search.php?keywords=dvdstyler").

And everything Tim Prosser said applies to this version as well, not to mention it works on Feisty too.  You may or may not have to change the configuration the way he said to; I had to on my amd64 Feisty computer.

And, tvphil, I looked in my configuration, and I didn't see any mention of genisoimage.  My version uses growisofs.  Maybe the edgy and feisty versions are different that way?

Here's what DVDStyler on my computer uses for burning:

> growisofs -dvd-compat -Z $DEV -dvd-video "$DIR" $SPEEDSTR

---

### Post by tvphil on 2007-06-14
That's another thing that's odd. My burning configuation is the same as your's, but instead, it comes up with genisoimage. I have no idea where that's coming from. On another matter, I need your help. I need the jpeg2mpeg command that come with the newest DVDStyler. I deleted that one and copied and pasted the one from Tim and now DVDStyler won't even get to the burning stage, it just crashes when I first execute the burn command. I tried uninstalling it and reinstalling it with synaptic and I just keep getting Tim's command, not the one that came with DVDStyler. If some has that one (all I can remember about it is it started out with "jpeg2yuv2" I think), please copy and post it, so I can paste it in, For now, I seem to be going from bad to worse. I'd like to get back to bad, it has more hope for a happy ending than I have now.

---

### Post by avik on 2007-06-14
> **tvphil said:**
> I need the jpeg2mpeg command that come with the newest DVDStyler. I deleted that one and copied and pasted the one from Tim and now DVDStyler won't even get to the burning stage, it just crashes when I first execute the burn command. I tried uninstalling it and reinstalling it with synaptic and I just keep getting Tim's command, not the one that came with DVDStyler. If some has that one (all I can remember about it is it started out with "jpeg2yuv2" I think), please copy and post it, so I can paste it in, For now, I seem to be going from bad to worse. I'd like to get back to bad, it has more hope for a happy ending than I have now.

```
jpegtopnm "$FILE_IN" | ppmtoy4m -n 1 -I t -L $FRAME_RATE | mpeg2enc -f 8 -b $BITRATE -o "$FILE_OUT" $VIDEO_NORM
```

This is the one I had, before I added the -S 420mpeg2 to fix an error that was coming up.  After adding that command, I ended up with:

```
jpegtopnm "$FILE_IN" | ppmtoy4m -S 420mpeg2 -n 1 -I t -L $FRAME_RATE | mpeg2enc -f 8 -b $BITRATE -o "$FILE_OUT" $VIDEO_NORM
```

You may or may not have to add that (I didn't on a previous install, but I did the latest time I installed it).  I hope that helps.

---

### Post by tvphil on 2007-06-14
Thanks for trying to help me, but no luck.DVDStyler still crashes with either one.

---

### Post by tvphil on 2007-06-18
I thought you'd enjoy reading this follow up. First of all, I went back to DVDStyler version 1.4 and it stopped crashing. The burning issue (get it) has evolved into what appears to be a problem with writing to either a DVD or a CD with the latest kernel of Ubuntu Feisty. This same writing error occurs with any type of burning to either DVD or CD, using DVDStyler, Gnome Baker or Nautilus CD/DVD Creator. You'll also be unhappy to know, the burner writes just fine in Windows. This is only a writing problem, I can still read (play) anything in the DVD drive in Ubuntu, I just can't write.I'd still love to hear any ideas on how to solve this from anyone.

---

### Post by tvphil on 2007-07-22
Well, I finally decided to bite the bullet and buy an new DVD burner.It's a Memorex Multi-format burner, for $50 I thought is was a good deal. Now DVDStyler works again. Obviously, it was a hardware issue all along. Why the old one would work in Windows (though not all the time) is still a mystery.

---

