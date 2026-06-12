---
title: "Avidemux2 no sound &quot;Trouble initializing audio device&quot;"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by arang on 2007-07-31
hi guys i installed avidemux 2.3 on ubuntu feisty 7.04 but im having this error that says
"trouble initializing audio device" , i know that under preferences i have OSS ALSA SDL and DUMMY OSS and ALSA give me a no go, OSS works if i start the app with aoss but, i get stuttering, the same with SDL, if i start it with SDL i have less stuttering but still some, i wish i could configure it to use ALSA but i dont know how ,if someone could tell me how, at the forums in the avidemux site they say that the standard version got X11 video support and also ESD support to work with gnome but i dont know how to do this, later versions 2.4 are known for having conflicts with the libraries that ffmpeg uses (i also use ffmpeg so uninstalling it is not an option) anyone could walk me thru configuring this thing to either work with alsa or add support for ESD without crashing the entire system???

any help is appreciated please im kind of noob at commands so its not that i know what pcm0d0 or whatever is what is using or allowing the output of sound or stuff so please help me.

---

### Post by datakid on 2007-08-01
I am having the same problems., haven't done as much trouble shooting, and can edit video ok - ie, thre sound is still there when I play the resulting file back in VLC.

Any help would be appreciated.

---

### Post by mattze on 2007-10-19
i had the same problem.
turns out the solution is very simple.
just change your audiodevice to 'default' (edit->preferences->audio->alsa device)
hope that helps!

---

### Post by c8h10n4o2 on 2007-11-07
> **mattze said:**
> i had the same problem.
turns out the solution is very simple.
just change your audiodevice to 'default' (edit->preferences->audio->alsa device)
hope that helps!

Fixed the problem!!! Thanks for the help

---

### Post by lukeduke on 2007-11-15
> **mattze said:**
> i had the same problem.
turns out the solution is very simple.
just change your audiodevice to 'default' (edit->preferences->audio->alsa device)
hope that helps!

And xubuntu? How does it do this? thank you

---

### Post by aparigraha on 2007-11-17
@lukeduke

Should be the same as above.
This is how i did it:

Edit>Preferences>Audio
Change Audio Output to ALSA
Under ALSA Device type: default

This also works on my Gutsy Xubuntu.
Changing Audio Output to OSS
and ALSA Device type: default

---

### Post by myonta on 2007-12-20
Hey, I know this is an old thread, but it's right in line with my current problem.

Changing the ALSA Device setting to 'default' definitely worked for enabling sound and getting rid of the "trouble initializing audio device" error. However, the sound playback in Avidemux is extremely choppy, even turning digitized at points.

Any ideas or suggestions where to start with this problem?

---

### Post by myonta on 2008-05-01
Hey all,

Since upgrading to Hardy this fix no longer works. My audio output is set to 'ALSA' and the device is still 'default' but the error "Trouble initializing audio device" has returned.

This is the only program on my system (that I've noticed, so far) that has an audio issue.

~Jon

---

### Post by myonta on 2008-05-05
Well, I don't know what happened but it started working fine. I wonder if my sound drivers/libraries got automatically updated while I wasn't looking.

Either way, I'm glad it works.

---

### Post by Ian Clark on 2008-05-06
> **mattze said:**
> i had the same problem.
turns out the solution is very simple.
just change your audiodevice to 'default' (edit->preferences->audio->alsa device)
hope that helps!
It does indeed!  Thanx!!:guitar:

---

### Post by Ian Clark on 2008-05-06
> **myonta said:**
> Hey all,

Since upgrading to Hardy this fix no longer works. My audio output is set to 'ALSA' and the device is still 'default' but the error "Trouble initializing audio device" has returned.

This is the only program on my system (that I've noticed, so far) that has an audio issue.

~Jon
Maybe you should update to Avidemux 2.4 (apt-get install avidemux, or through "add/remove programs").  I'm running 2.4 on Hardy, and you go to audio in the preferences, and type in "default" in the "alsa device" field.

---

### Post by jcarey on 2008-06-12
My experience is that the error only occurs when an a program is open that uses flash.  If I experience the error, I can keep avidemux and my file open, close down firefox (and I have to close down awn because I have the pandora radio player installed).  Then I can hit play and it will play the audio fine.

*same audio settings as mentioned in previous posts.

---

### Post by UAvron on 2008-07-20
Thanks guys, the setting of Alsa and Alsa Device worked perfectly well on Hardy.

---

