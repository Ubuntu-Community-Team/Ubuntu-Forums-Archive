---
title: "Do I need a new video card and HDTV sound? ATI X1650 Pro driver woes"
date: 2009-10-04
forum: Mythbuntu
---

### Post by JMcFly on 2009-10-04
[SIZE=3][COLOR=Red]The video problem's fixed, sound still an issue
[/COLOR][/SIZE]I upgraded my gaming rig, leaving a bunch of parts available to build a Mythbuntu 9.04 box, but I'm having some issues.

Current system, running both the frontend and backend:
P4 2.4ghz
2gb ram D333
ATI X1650 Pro 512meg (having to run vesa drivers as AMD doesnt support this card in 9.04)
20gig operating system drive PATA
320gig recording drive PATA
HVR-1600 1199 tuner card with NTSC cable feed and ATSC antenna

I managed to get the NTSC feed working using ALSA:default (onboard AC'97 sound, only one stereo jack out) for every audio setting and picked out a ton of movies using ScheduleDirect.  Any recording is jittery/choppy on the PVR during high-motion scenes (even worse if I'm watching it "live")but if I move it over to the new gaming rig (quad 2.66, ATI 4870 1gb, 4gb ram, Vista business) the video looks awesome and doesnt jitter or lose a frame. I'm guessing this is due to the generic vesa drivers not using the full potential of the X1650? Would I be better off getting a 512meg GeForce 6200 rather than screwing around with getting it to work?  I've already had to reinstall Xserver once tonight due to a "guaranteed to work" work-around (reverting Xserver from Jaunty back to Intrepid) in an attempt to get the ATI drivers to work, not fun for someone that had to google "how do I make a directory in Linux" yesterday...

Another odd one is that I do not get any sound on my ATSC recordings, and those seem to have really limited options as to what could be wrong or what I could fix. If I try to switch from watching NTSC to watching ATSC it usually results in the frontend crashing, might this be related to the lack of audio in the recorded shows? :confused:

---

### Post by rob3435 on 2009-10-04
Before you go out an buy new hardware, have you given the open-source ati driver a try?

I currently ran 9.04 (and now 9.10 beta) on my mythbox with an ati X1550 (rv505) dual core x2  and all videos are perfect/smooth from my pvr-500 (analog) and hdhomerun (1080 hd) sources...

Note, sometimes fglrx can leave somethings behind clean them up with:

```

sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```

Regards,

---

### Post by JMcFly on 2009-10-04
The open source ATI driver (xserver-xorg-video-radeon) seems to have solve the analog problems, it does live TV and recordings very nicely once I followed [this work-around](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/341898/comments/87), I guess it doesnt like the MythTV fonts.

Any idea what might cause my lack of ATSC audio, or the front end crashes when I go from NTSC to ATSC?

---

### Post by JMcFly on 2009-10-05
Some more info about my ATSC problem:
The built-in sound card is an SiS SI7012 with a CMI9739 chipset, which I am listening to via stereo headphones plugged into the port on the back of the mobo (not the AC'97, sorry for the confusion). 

Recordings from HD channels have no sound when played in the Mythbuntu front end, but have sound when played in Xine and when transferred to my Vista box. I have all of the IEC958 settings in alsamixer muted ([suggested in this thread](http://ubuntuforums.org/showthread.php?t=884283)).

Any ideas on what I should try?

Thanks

---

### Post by larsolav on 2009-10-06
I may be way off base here, so please forgive if this is nonsense...
What happens when you play a DVD with the internal Mythtv player? It should also be digital audio. What are your Mythtv audio settings? Maybe it is set to pass through the digital audio and not to send the headphone jack? Again, I may be completely wrong...

---

### Post by JMcFly on 2009-10-06
Turns out the digital SPDIF output button was checked, removed it and I have audio in all of my playbacks. But now my HD playbacks are stuttering about once a second? :(

Would changing my playback profile help? Its on CPU++ at the moment but I'm not sure that is the right one.

---

