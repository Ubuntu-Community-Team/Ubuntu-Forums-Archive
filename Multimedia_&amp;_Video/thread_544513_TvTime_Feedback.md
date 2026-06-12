---
title: "TvTime Feedback"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by the.unclean.cpp on 2007-09-06
I was, at the beginning of my Linux experience, looking like nuts for drivers for my TV Tuner, I was pretty sure that installing TvTime first is not logic and it won't work. Today I just installed Kubuntu on my system and after that I installed TV Time. When I ran "tvtime-scanner" it worked like a charm. So setting up a TV Box on Linux isn't so hard after all. I mention that I am using Winfast PVR TV2000XP Deluxe Edition.

```
sudo apt-get install tvtime
sudo tvtime-scanner
```

I'm waiting for feedback with experiences of other users with other TV Cards, because I want to set up a list with "out of the box" supported TV Cards on Ubuntu.

Later edit: It seems that if you run the "tvtime" command as a normal user it doesn't have the permission to access the list of custom channels. You can resolve this problem by changing the permissions of the file or by typing "sudo tvtime".

---

### Post by wolfen69 on 2007-09-06
good to hear. vlc also works good for tv. here's how:

I have a Hauppauge 150 card running on my Feisty box, and I get live tv by: 

sudo apt-get install ivtv-utils (drivers)

open VLC 

File -> open Capture Device -> PVR -> OK

then you can do

ivtv-tune -h

to see the options which control the card. The interesting ones are

ivtv-tune -d(input number)

which changes the card's input from composite to s-video, and

ivtv-tune -c(channel number)

which changes the channel.

for a cool desktop tv remote, go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click:open with java.

---

### Post by acoustibop on 2007-09-06
I'm running a Hauppuage ImpactVCB, their video-only card; no tuner.  It suits me fine as I'm on cable, and don't have more than one channel to tune in anyway.

Worked out of the box.  I installed the card (physically), installed TVTime, mucked about with one or two settings and I was set.

On the other hand, I've tried a few ATI AIW and VIVO cards, and have never been able to get the video/TV components to work in Linux.

---

### Post by rsambuca on 2007-09-06
> **wolfen69 said:**
> open VLC 

File -> open Capture Device -> PVR -> OK

You can also create a program launcher on your panel or desktop that will open straight into the tuner if you wish.  Mine looks like this:

vlc pvr:// :pvr-device="/dev/video1"

Now to watch through the tuner I just press the button on my top panel and VLC opens it directly.  You may have to change the "video1" part to "video0" or whatever your card is set up as.

---

