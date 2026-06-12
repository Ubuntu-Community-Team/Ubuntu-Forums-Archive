---
title: "CD Ripping"
date: 2010-07-06
forum: Multimedia Software
---

### Post by jeggerleg on 2010-07-06
Why are things so difficult using Linux/Ubuntu?
I'm trying to rip some tracks from a CD, I've looked at various threads telling me how this might be possible.  I've tried RipperX, installed it, used it, and the resultant track I was told couldn't be played because I didn't have the necessary files installed.  Funny because I have quite a number of MP3's which play quite happily
I tried RubyRipper, couldn't for the life in me work out how to install, never mind use it.

I then switched to Windows, Googled CDex, downloaded it, installed it and ripped the three tracks in less time than it's taken me to type this.
Don't get me on the subject of cropping photos in Gimp or F-Spot.

---

### Post by Darkness Des on 2010-07-06
Ever considered importing the tracks through Rhythm box? Or simply going into the directory where the CD was mounted and just copying and pasting? Sometimes the simple things escape us.

---

### Post by jeggerleg on 2010-07-07
> **Darkness Des said:**
> Ever considered importing the tracks through Rhythm box? Or simply going into the directory where the CD was mounted and just copying and pasting? Sometimes the simple things escape us.

I hadn't considered that, but it won't give me MP3's will it.

---

### Post by mc4man on 2010-07-07
> but it won't give me MP3's will it.

Sure it will, just install the gstreamer plugins

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly-multiverse
```

Then in rhythmbox -> edit -> Music you should see mp3 in the Preferred format dropdown.

The default mp3 parametrs are not so great - unfortunately to change you need to properly edit the gstreamer profile

If you're running karmic or earlier you'll find rubyripper very easy to use (lucid has some limitations) - I see you had issues with the ppa.
The ppa is using an outdated version and the instructions on how to install rr from source have been removed from the howto in lieu of the ppa.
(though you could use the ppa if you wish - 

If you wish can get rr up & running in a min or two without the ppa

---

### Post by Boondoklife on 2010-07-07
Why not use **[sound-juicer]("apt:sound-juicer")** it is in the repos.

---

### Post by Linuxforall on 2010-07-07
Ripper X works fine here ,no need to install anything, it pulls in all the necessary libraries unless you want lame conversion, in that case just do a sudo apt-get install lame and you are all set.

---

### Post by jeggerleg on 2010-07-07
> **Linuxforall said:**
> Ripper X works fine here ,no need to install anything, it pulls in all the necessary libraries unless you want lame conversion, in that case just do a sudo apt-get install lame and you are all set.

Thank you for your help, that seems to work.  However, I stick by my original assertion that Linux/Ubuntu is not the easiest to get to grips with. And it needs to be to outstrip Bill's offering.

---

### Post by Linuxforall on 2010-07-07
> **jeggerleg said:**
> Thank you for your help, that seems to work.  However, I stick by my original assertion that Linux/Ubuntu is not the easiest to get to grips with. And it needs to be to outstrip Bill's offering.

In Windows you need to install LAME and other codecs as well, Linux is not MS Windows, its different, its a learning curve and thankfully its not a clone of Windows, otherwise I wouldn't be using it and would be looking elsewhere, just have some patience and you will find that Linux offers way more than MS can ever dream of.

---

