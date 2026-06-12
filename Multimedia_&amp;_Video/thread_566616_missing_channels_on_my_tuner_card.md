---
title: "missing channels on my tuner card"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by xinman on 2007-10-03
I'm upgrading to feisty and I have a Hauppage pvr-250.  I'm running kernel 2.6.20-16-generic.  In mythtv I only get channels 2-13, so I loaded up tvtime and it tells me 
```

ivtv: invalid argument
cannot open capture device /dev/video0

```

I figured I would at least get channels 2-13 on tvtime.  The cable does work if I hook it directly to the tv up to channel 70 something.  

Everything I read says that the hauppax50 series works out of the box in feisty.  

The only other thing that struck me odd is that in the mythtv-setup before I upgraded it said I used Tuner0 now it says Tuner1 and there is no option for Tuner0.  I don't know if that has any relevance or not.  

Any help would be great its been down for two weeks and it sucks.

Thanks,
Dan

---

### Post by jimbodude21 on 2007-10-06
try using "ivtv-tune" to change the channel on the card to something you don't think you get.  Use "cat" to put the output of the card directly into an MPEG file, then play that.
```

j@jmedia:~$ ivtv-tune --device=/dev/video0 --channel=70
j@jmedia:~$ cat /dev/video0 > test.mpg
```
CTRL+C to terminate the cat command, play the MPEG with your favorite program.

If that works, make sure that MythTV knows about those channels - you will have to add them to your cable lineups.  Set up your lineup service with the correct channels, following this guide: [http://www.mythtv.org/wiki/index.php/Updating_Channel_Lineup](http://www.mythtv.org/wiki/index.php/Updating_Channel_Lineup)

---

### Post by rsambuca on 2007-10-06
Depending on your setup, your tuner may be set up on /dev/video1 instead.

Have a look at your dmesg output and you will see the ivtv section.  Look to see if it is video0 or video1.

---

### Post by jimbodude21 on 2007-10-06
Good point.  This will show you all of them:
```
ls /dev/video*
```

---

### Post by wolfen69 on 2007-10-07
do this if you have ivtv-utils installed.

open VLC-
file>open capture device>PVR>OK
open terminal-```
ivtv-tune -c25
```
would be channel 25

for a desktop "remote control", go to [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

i have a PVR150, so i know this will work for you.

---

### Post by rsambuca on 2007-10-07
> **wolfen69 said:**
> do this if you have ivtv-utils installed.

open VLC-
file>open capture device>PVR>OK
open terminal-```
ivtv-tune -c25
```
would be channel 25

for a desktop "remote control", go to [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

i have a PVR150, so i know this will work for you.

This won't work if his device isn't video0.  I think we need to find out what device number it is.

---

### Post by xinman on 2007-10-07
Ok, well this is weird.

It is in fact /dev/video0 so I know that's setup fine.  I also have another issue with the ATI fglrx drivers and in working through that all of my channels started showing up.  I'm not sure why because I only changed a few values in the xorg.conf and as far as I know that shouldn't affect any of the channels (maybe i'm wrong).  But it's been working for about 2 days and I'm checking to make sure it doesn't go away again.  I really appreciate all of your help, and I'm sorry I didn't post that it was fixed as I wasn't sure that it was and if so why it was!  Like I said I'm not sure what exactly I did to make it start working.  On the ATI front I'm looking at moving to nvidia on all of my boxes, but that's another story.  If anyone can explain what may have caused my channels to start working feel free, I would like to know.

Thanks again.

---

### Post by rsambuca on 2007-10-07
I have no idea!  I just know that for some reason, my tuner is video0, and sometimes it is video1, switching with my webcam.  I have no idea why the order is switched sometimes at bootup, but it is a little bit annoying.

---

### Post by xinman on 2007-10-07
> **rsambuca said:**
> I have no idea!  I just know that for some reason, my tuner is video0, and sometimes it is video1, switching with my webcam.  I have no idea why the order is switched sometimes at bootup, but it is a little bit annoying.

I don't have any other devices that would take video0 from it so I don't think that is the case and either way if that was the case I don't think channels 2-13 would still work perfectly...  I'm really happy that it seems to be working now I just wish ATI would create and support better drivers or at least open them up so that some of the talented community could work on them.

Thanks for your input.

---

