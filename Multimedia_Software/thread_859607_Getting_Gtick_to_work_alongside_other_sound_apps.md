---
title: "Getting Gtick to work alongside other sound apps"
date: 2008-07-14
forum: Multimedia Software
---

### Post by th3james on 2008-07-14
Basically, i want to be able to use Gtick (metronome) at the same time as watching videos, so i can practice my guitar. However, Gtick uses OSS (which, as far as i can tell, is a hatefully poor sound engine), and won't play nicely with other apps. I've tried to get it to work with Alsa using using alsa-oss and the command
```
aoss gtick
```
but gtick behaves the same, either not allowing sound apps to play if its run first, or giving this error if not:
```
Couldn't start metronome.
Please check if specified sound device
and sample file are accessible.
```

Anyone got any ideas to get it working? or any other metronome programs ( i couldn't find any in the repos)

Thanks in advance

James

---

### Post by fastfret79 on 2008-07-27
I was having the same issue but using 'aoss gtick' worked for me.

Browse to you /dev/ directory and look for anything that starts with dsp and then goto 'Edit > Preferences' in GTick and enter that path in the 'Sound Device Filename' - mine is just '/dev/dsp'

Hope that helps!?

---

### Post by offbyte on 2009-02-18
I have the same problem and that doesn't work on me

---

### Post by sbela on 2009-05-31
it works for me 'aoss gtick' where gtick is 0.4.2 on ubuntu 9.04, and sound device is /dev/dsp.

---

### Post by TheTeamFromMars on 2010-07-06
I have the same problem...
Installed Gtick last night using the Ubuntu Software Center and it worked fine. Tonight after restarting my PC I get the following error message after clicking the Start button: 
"Couldn't start metronome.
Please check if specified sound device
and sample file are accessible."

/dev/dsp was already listed as my default sound device in Gtick so the above fix didn't work for me either. 

Does anyone have another fix? 
Thanks...

************
Update... I got gtick working for me again by going to Sound Preferences | Hardware tab and setting the Profile to "Off". I have no idea what that does but gtick is working again anyway.

---

### Post by gacd on 2010-07-22
> **TheTeamFromMars said:**
> I have the same problem...
Installed Gtick last night using the Ubuntu Software Center and it worked fine. Tonight after restarting my PC I get the following error message after clicking the Start button: 
"Couldn't start metronome.
Please check if specified sound device
and sample file are accessible."

/dev/dsp was already listed as my default sound device in Gtick so the above fix didn't work for me either. 

Does anyone have another fix? 
Thanks...

************
Update... I got gtick working for me again by going to Sound Preferences | Hardware tab and setting the Profile to "Off". I have no idea what that does but gtick is working again anyway.

I can use any hardware profile. So, this is "my" way to fix the problem:

1. Install the alsa-oss package:
```
sudo apt-get install alsa-oss
```2. Then, run gtick with the alsa-oss compatibility:
```
aoss gtick
```3. If not yet has sound, so you can change the path of device to /dev/dsp0 in preferences menu.

Good luck...:D

---

### Post by Yellow Pasque on 2010-07-22
padsp...
[http://linux.die.net/man/1/padsp](http://linux.die.net/man/1/padsp)

---

### Post by taygan on 2010-11-28
Thanks for the padsp tip:
```
padsp gtick
```
works great!

I edited the Applications>Sound & Video>GTick menu (Preferences>Main Menu) and under the GTick preferences added "padsp" (no quotes) before /usr/bin/gtick in the command box.  All is well!

---

### Post by miousername on 2011-03-14
> **gacd said:**
> I can use any hardware profile. So, this is "my" way to fix the problem:

1. Install the alsa-oss package:
```
sudo apt-get install alsa-oss
```2. Then, run gtick with the alsa-oss compatibility:
```
aoss gtick
```3. If not yet has sound, so you can change the path of device to /dev/dsp0 in preferences menu.

Good luck...:D

Thanks it worked for me!

---

