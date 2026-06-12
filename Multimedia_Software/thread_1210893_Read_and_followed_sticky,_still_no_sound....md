---
title: "Read and followed sticky, still no sound..."
date: 2009-07-12
forum: Multimedia Software
---

### Post by Tyrfing on 2009-07-12
Hey guys, I just upgraded to Jaunty Jackelope, and I cannot get sound to play on my T43 IBM Thinkpad.

I followed the sticky guide about no sound.

When I used the aplay -l command, I got the following output:

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

________________________________________________________________________

I proceeded to play around with alsamixer, with no results.

If it helps in the debugging, my Thinkpad has volume buttons built in that have automatically worked with every previous distro I have used (Gutsy Gibbon and Hardy Heron). 

If anyone can help me, I would greatly appreciate it!

Thanks!

  -Tyrfingg

---

### Post by Tyrfing on 2009-07-12
bump

---

### Post by Tyrfing on 2009-07-12
bump

When mixing with the alsa mixer, I was able to get the playback from the built in microphone to play, but of course that is useless for my purposes.

---

### Post by igorzwx on 2009-07-12
Do not bump. 
Think!

I have IBM ThinkPad R40

I have my problems solved by installing OSS4.
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Pulse is now removed.
ALSA modules are blacklisted.
And I even utilized ALSA drivers for fixing playback of
ALSA applications.

Read this first:
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

But try this first on an old box, if you have one for experiments.

Best,
Igor

**Audio Noise in Ubuntu**
[http://ubuntuforums.org/showthread.php?t=1035892](http://ubuntuforums.org/showthread.php?t=1035892)

---

### Post by Tyrfing on 2009-07-12
I've heard the R40 thinkpads sound works quite differently from the T series.


Also, I am not wanting to switch audio programs.


I have been searching the internet for solutions, but haven't found any similar situations... any help guys?

---

### Post by 1roxtar on 2009-07-12
Try this and see if it works...


1. Open up the volume control.

2. Go to Edit.

3. Go to Preferences.

4. Scroll down list to External Amplifier. (check it)

5. Once it is check - close that out.

6. Go back to the volume control panel.

7. You should now see a Switches TAB at top. (select it)

8. Search for the External Amplifier on the list you see.

9. Uncheck the External Amplifier.

10. Now close out and go test your sound.

---

### Post by Tyrfing on 2009-07-12
Tried that out. All of those checked/unchecked settings were already set up that way, but no sound.

---

### Post by Tyrfing on 2009-07-13
bump

---

### Post by igorzwx on 2009-07-13
Think

---

### Post by igorzwx on 2009-07-13
Think why they need External Amplifier.
To fix another problem?
It was another bug

GOOLE -> "Ubuntu PulseAudio bug"

---

### Post by Tyrfing on 2009-07-13
I've googled that, and didn't see a link to any problem I am having... I do not understand what you are referring to.

---

### Post by igorzwx on 2009-07-13
You can try to fix ALSA
[http://ubuntuforums.org/showthread.php?t=1211713](http://ubuntuforums.org/showthread.php?t=1211713)

---

### Post by Tyrfing on 2009-07-13
bump


I don't know what would be wrong with ALSA, as every check I have done indicated that there is no problem with ALSA at all...

---

### Post by igorzwx on 2009-07-14
"I don't know what would be wrong with ALSA..."

If you know everything, life does not make sense at all.
Life is not a matter of knowings, it is a matter of trial and error.

---

### Post by Tyrfing on 2009-07-14
If you haven't deducted already I am fairly incompetent at Ubuntu, or Linux in general.

I am posting here for help because I do not know what to do, and everything you have submitted for me, has already been read, and does not seem like a correct fix.


Your attitude and remarks have become increasingly negative. I do not want to be insulted, I am merely asking if anyone knows anything that I can try, as losing sound on my laptop is extremely frustrating. If you do not have something constructive to say, please do not reply with insults.

---

### Post by igorzwx on 2009-07-14
Sorry!!!
I just wanted to say that you may better try this or that solution.
I do not understand anything in Linux, but I made it working by
trial and error

Sorry once more.

---

### Post by igorzwx on 2009-07-14
and your notebook is not so different from my.
Create a free space. 
Install there another Ubuntu in dual boot.
And make experiments ALSA, Pulse, or OSS4
Why not?
You see many people have problems now,
but they are trying to solve them in all possible ways,
logical or illogical.

---

