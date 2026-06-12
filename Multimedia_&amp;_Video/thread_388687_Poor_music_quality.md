---
title: "Poor music quality"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by akilarules on 2007-03-19
i just installed ubuntu and im not that familiar with some of it. im running music of my ipod through rhythmbox but the quality is pretty poor. what do i need to do to fix this?

---

### Post by jpeddicord on 2007-03-20
This might be related you your sound card's internal volume. Try turning it down:

Go to Applications > Sound & Video > Volume Control. Turn the slider marked 'PCM' down about halfway, and turn Master up a little bit. This might fix any scratchiness in the sound.

---

### Post by amanitaa on 2007-03-20
I am having the same problem. I am running Edgy, and installed gstreamer0.10-plugins-bad-multiverse and gstreamer0.10-plugins-bad. My AAC files sometimes work with rhythmbox but mostly the sound on my whole laptop, even start-up noises is a funny, fuzzy version almost distinguishable as the original sound, but not unless you already knew what that sound was supposed to be. I added the  faac package and saw no difference. Why would this installation (gstreamer) affect how all my files are played and not just the AAC files? Before Ogg files worked fine, now, nothing works. Yikes!

---

### Post by bourger on 2007-03-21
Confirm the problem. I run Ubuntu Dapper, my soundcard is built-in VIA 8235 (AC97). The sound quality when I play an audioCD is approximately equal to 32bit mp3. Under Windows the sound is OK.

---

### Post by ToeKing on 2007-03-22
Bump...

I've been running edgy for quite a while now and just recently the quality of my music playback has gone to crap...  You can hear everything, but it sounds like there's some distortion and crackling at certain frequencies.  I've messed with the volume settings and that doesn't help.  I'm trying to look through any new packages that might have caused this.  Haven't done a kernel update in a while, so that's not the issue either.  Any ideas?

I know this isn't a speaker problem because it sounds great if I boot into windows.

---

### Post by dmizer on 2007-03-23
> **bourger said:**
> Confirm the problem. I run Ubuntu Dapper, my soundcard is built-in VIA 8235 (AC97). The sound quality when I play an audioCD is approximately equal to 32bit mp3. Under Windows the sound is OK.

i have this card in one of my laptops.  sound is still bad, but i resolved most of it by doing this:

in your home directory (ie /home/bourger) create or modify the file .asoundrc so it looks like this:
```
        pcm.via82xx {
           type hw
           card 0
        }

        ctl.via82xx {
           type hw
           card 0
        }

```
this file tells alsa how to handle your card.  it will be different for different manufactures and chipsets.

++++ for the rest of you ++++

since bourger posted the manufacture/chipset, i was able to determine the exact .asoundrc file for bourger's card.  noone else has posted this information, so i can't do any more than give the rest of you directions on how to find the correct settings for your specific card.

to figure out what your .asoundrc file should look like, you'll need to know what chipset your running.  you can find it this way:
```
lspci -v
```
take a look at the results and you should be able to tell which device is your soundcard.

then, head over here: [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and find your manufacture and model in the dropdown menu at the bottom of the page.  it will return with a list of items matching the dropdown list, make sure you click on the link that matches your card.

once you have the right page for your card, scroll through and find the section titles "the .asoundrc file", and follow the directions for creating it as above, or as given at the alsa site.

*edit:
this information was pulled directly from the [comprehensive sound problem solutions guide](http://www.ubuntuforums.org/showthread.php?t=205449) located at the top of this forum.

---

### Post by mcduck on 2007-03-23
Just open the volume settings, enable all controls and make sure that no channel is set to 100%. That will in most cases cause distorted sound. I keep mine at 90% max and then the sound is fine.

edit: you might need to do this for both ALSA & OSS

---

### Post by bourger on 2007-03-23
**dmizer**
Thank you very much for such a comprehensive reply and for these links.
I've done exactly what you told but have got no result. I went to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) , recompiled the sound driver and reinstalled all the modules. But there is no evident result - music sounds unpleasantly. There is no any noises, playback is absolutely correct, but... poor.
**mcduck**
I moved these controls. Helpless...

---

### Post by dmizer on 2007-03-23
there are comments below the directons for recompiling.  one of the comments says:
> The above .asoundrc file didn't work for me. I changed it to use exactly the same name as in modules.conf and now it works great.

ie ... check your modules.conf file (the output of lsmod should also show this) for your soundcard module and see what it's called.  then edit your .asoundrc file and change these two lines:
pcm.via82xx
ctl.via82xx

so that it reads exactly how it does in modules.conf.  ie, most likely:
pcm.snd-via8235
ctl.snd-via8235

if that STILL doesn't resolve your problem, i suggest browsing through the rest of the comments attached to the alsa notes on your card [here](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=VIA&card=VIA+southbridge+AC97+audio.&chip=VIA82C686%2C+VIA8233%2C+VIA8233A%2C+VIA8235%2C+VIA8237&module=via82xx)

edit:
just noticed this, which might be your solution 
> I have a Debian GNU/Linux system with audio integrated into the VIA VT8235. 
I need to do the below to cure audio popping:

As root edit "/etc/modutils/alsa".  
	Above the line
		alias snd-card-0 snd-via82xx
	add the line
		options snd-via82xx dxs_support=4
Save /etc/modutils/alsa to disk.
As root run "update-modules".
Reboot.
The sound should be flawless.

---

### Post by jpeddicord on 2007-03-24
There is a package that might fix it on-the-spot with some applications also:

libsdl1.2debian-all

Install that package and you might get some improved sound quality. It works for some applications that don't use ALSA or ESD, and fixes some bugs with others.

---

### Post by bourger on 2007-03-24
Well, I've done just everything.
By the way, in my sistem there is no /etc/modules.conf (and conf.modules either) file. So most of comments on alsa project page turned to be useless for me.
At last I installed alsa driver 1.0.14rc3.
And after reboot all sound died.
No sound devices are recognised, no mixers can be opened.

Ufff... I have had some panic, really, when after I did >make uninstall for alsa-driver, alsa-lib and alsa-utils and after reboot my session haven't started at all. I remained with terminal only. Luckily, I could run Opera though... I recompiled 1.0.13 driver (luckily again I kept the sources)...
Now both system and sound work.
But the sound... just the same, no change to better.

---

### Post by bourger on 2007-03-26
Yes! I've done it!
Following this simple [instruction](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_configure_sound_to_work_properly_in_GNOME) solved the problem.
Music now sounds great, really better than in Windows.
Ubuntu rulez :)

---

### Post by Hatchet Soldier on 2007-06-04
I was having the same problem, poor quality sounded scratchy then i switched to this package _libsdl1.2debian-all _instead of the libsdl1.2debian-alsa package. Then tweaked the PCM controls and also went into _prefences --> sound _and switched from auto-detect to my sound card. Music sounds wonderful now. I hope this might be able to help some of you having the same problem. If anyone has gotten and ATI Radeon 340M to work with 3d graphics any help would be appreciated. Got music now just need video

---

