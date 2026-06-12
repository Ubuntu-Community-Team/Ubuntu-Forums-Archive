---
title: "ubuntu 14.04 toshiba satellite internal speakers work not headphones"
date: 2014-06-22
forum: Multimedia Software
---

### Post by dave125 on 2014-06-22
Hi folks, 

Could use some help here. I've installed 14.04 on my aging satellite laptop and sadly the headphone jack won't work Any help would be greatly appreciated.
I ran alsa and below is the link to my report. 
[http://www.alsa-project.org/db/?f=8b152469bf770ff45cb7dcd7404be31166b75be5](http://www.alsa-project.org/db/?f=8b152469bf770ff45cb7dcd7404be31166b75be5)


Thanks in advance.

---

### Post by Vladlenin5000 on 2014-06-22
Hi, welcome.

I many system you have to explicitly select that output. Just connecting won't change it.

---

### Post by dave125 on 2014-06-22
Thank you for the reply. Could you maybe give me the steps to do that? I'm pretty new to ubuntu and Linux in General.

---

### Post by Vladlenin5000 on 2014-06-22
It's as simple as clicking the sound icon > sound settings... You should be able to see what output is select and change it if needed.

---

### Post by dave125 on 2014-06-22
There is only one device listed

---

### Post by Vladlenin5000 on 2014-06-22
> **dave125 said:**
> There is only one device listed

... as it should be. Try the same with the headphones plugged in. If a second devices isn't shown then I'm out of ideas.

---

### Post by dave125 on 2014-06-22
Unfortunately that didn't work. Thank you for trying. :)

---

### Post by Bucky Ball on 2014-06-23
Welcoime. Install Pulseaudio Volume Control. Use Software Centre (look for 'pavucontrol') or use this in a terminal:
```

sudo apt-get install pavucontrol
```

Launch it from Apps>Multimedia (may be different on your release/flavour). Get some music going and have a look in 'Playback'. You should see the stream happening from your music playing app. Check where it is being sent. Check 'Output' tab and make sure nothing is muted there. Check the drop down menus to see the stream is being sent to the correct device (your headphones).

Bottom line: get a sound stream happening, check you have it up in 'Playback', check it is streaming to the correct device, check nothing's muted, and experiment til you hear some noise.

Other thing to do is to check alsamixer and make sure nothing muted there. I use gnome-alsamixer personally (also in the repositories). Like the clearer GUI. Good luck.

---

### Post by soodvarun78 on 2014-06-23
Hi,

your alsa dump is not showing anything related to Headphone. 
Just see in alsamixer you are getting headphone or not. 

your codec is Realtek ALC861, Verify whether this codec support headphone(which I think it should)
you may have to install a new driver for codec.

---

### Post by Bucky Ball on 2014-06-23
You should have absolutely no reason to install a driver/codec for your headphones or anything else at this point. Check Pulseaudio Volume Control. ;)

---

### Post by lidex on 2014-07-01
Has this been solved? You should update your system as there is a later alsa driver.
```
sudo aptitude update && sudo aptitude upgrade
```
Reboot and open alsamixer. You have a mixer control labelled "line" that is muted and at zero volume.
Play around with that.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

