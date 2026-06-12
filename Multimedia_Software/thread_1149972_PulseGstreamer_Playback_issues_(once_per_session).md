---
title: "Pulse/Gstreamer Playback issues (once per session)"
date: 2009-05-05
forum: Multimedia Software
---

### Post by cak3 on 2009-05-05
Ok, so, yet another sound problem, big surprise (it's not). I haven't been able to find anything on this specific problem yet, so that interesting though.

Anyway, this issue is that, after logging on (i.e. it happens every log on, not just restart) the first music file I play goes too fast -- it skips. I pause it, resume it, and it's good. I have been able to reproduce this in both Banshee (my preferred media player) and in Rhythmbox. I think its a gstreamer issue, but I don't really have any reason for thinking so... I don't really know anything about gstreamer though.

Ok, so thats the problem, the rest is details about my audio setup. I have it using the s/pidf optical out on my motherboard (integrated sound card). Speakers are Logitech Z-5500 (probably not relevant). To get the optical working, I did have to compile the alsa-drivers myself. I used this guide: [[COLOR="Blue"]https://help.ubuntu.com/community/HdaIntelSoundHowton[/COLOR]]("https://help.ubuntu.com/community/HdaIntelSoundHowton"). The relevant bit is just this part (when compiling alsa-driver):
```
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)

```

As a side-note, that guide works fine on jaunty, despite what it says about not being valid after hardy or something like that (and the script it links to as an alternative does NOT work). 

As I mentioned before, I am using pulse, and have the pulse device manager installed. I had to do a bit of customization, so I have a custom default.pa (attached) and a few other things in ~/.pulse  The relevant bits there are loading the module and specifying the default sink. 

I also have a custom .asounrc but I don't know if it even affects anything. I am attaching it anyway, the commented out stuff if stuff I tried or was using (for various things). None of them seemed to make any changes (including what isn't commented). 

the device is listed as HDA Nvidia or ALC1200 Digital (or analog, but digital for the s/pdif out, which is what I want).

I can't think of anything else that might have a bearing on the situation atm, but if anybody wants more info, just ask.

Oh, I am running Ubuntu 9.04 (Jaunty) AMD64

Thanks
--Derek

---

### Post by Insanity01 on 2009-05-05
had playback problems with pulse aswell, so i install esound and works perfectly..
command i used are:
(reboot system afterwards tho, else it will go weird)
[INDENT] 
[LIST]
[*]killall pulseaudio
[*]sudo apt-get remove pulseaudio
[*]sudo apt-get install esound
[*]sudo rm /etc/X11/Xsession.d/70pulseaudio
[/LIST]
 [/INDENT]

---

### Post by cak3 on 2009-05-05
I don't really want to give up on pulse yet, I did get it mostly working, after all. Since this problem is temporary (the first song I play, or whatever) its annoying, but not fatal. Not that I am a huge fan of pulse, but I got it all set up and kinda understand how it works now.

Plus, I am not sure this is a pulse problem, other (not music, aka system) sounds seem fine, which suggests another issue (gstreamer?) to me.

---

### Post by cak3 on 2009-05-11
I did try ESD anyway, and, for me at least, pulse works better (or at least is easier to configure). 

Anyone got anything else?

---

### Post by psyke83 on 2009-05-12
The fix for your issue is included in the 2.6.28-12-generic kernel. You can get access to this now if you enable the "proposed" repository.

Bug reference: [https://bugs.launchpad.net/bugs/345627](https://bugs.launchpad.net/bugs/345627)

---

