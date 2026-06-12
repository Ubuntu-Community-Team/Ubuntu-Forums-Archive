---
title: "Firefox doesn't use USB audio"
date: 2009-01-31
forum: Multimedia Software
---

### Post by atatistcheff on 2009-01-31
I just got a set of Logitech V10 USB speakers, hooked them up and went to System --> Preferences --> Sound.  There I selected USB Audio for every sound listed this includes Sound Events, Music and Movies and Audio Conferencing.  Sound from apps like Totem now comes through the USB speakers just fine.  However, audio from Firefix - particularly from Pandora - still comes through the default laptop speakers.  I can't find any other location to tell Firefox to play sound through the USB speakers.  

Laptop is a Dell Inspiron 1420
Ubuntu 8.04

How can I get Pandora to play through these new speakers?

---

### Post by atatistcheff on 2009-02-03
--- Bump ---

Apparently there is no way to do this in Ubuntu?  Maybe a bug report or feature request is in order.  Seems like sort of a basic function, works fine in Windoze...

---

### Post by markbuntu on 2009-02-03
Try this, it will get you some things and set you up for better control over your audio

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by atatistcheff on 2009-02-03
Thanks for the info.  I installed all the packages in the thread and using the PulseAudio server does give some more control.  However, I'm still having no luck getting the Pandora shockwave flash plugin to play through anything except my built-in speakers.  It doesn't show up as a playback stream in the PulseAudio volume control so I can't direct it to the USB.  My Totem player does show up but once again shockwave is bypassing the sound applets and just going to whatever sound card it wants to.  

I tried editing the /etc/firefox/firefoxrc file which contained a line:

## FIREFOX_DSP="none"

per another thread I replaced it with:

FIREFOX_DSP="aoss"

This didn't have any effect good or bad.  

This appears to be a shockwave issue, I think what I need to find out is how to get shockwave to send it's audio to the PulseAudio server.

---

### Post by markbuntu on 2009-02-03
If you installed all the packages and followed the setup flash should be using pulseaudio. That is weird. Where did you get this flash from?

---

### Post by kostkon on 2009-02-03
I would like to ask the same thing. What version of Flash do you have? Flash 9 or Flash 10?

---

### Post by atatistcheff on 2009-02-03
Shockwave Flash 9.0 r124, don't remember where I got it, I would think Adobe.  It's definitely bypassing the normal sound channels though.  

Also, once I have Pandora playing if I run Totem, VLC or another media player it won't play any sound.  I have to close Firefox to make the other media players work.  Running 8.04 and seeing the same behavior on two Dell laptops, one is an Inspiron 1420, the other is a Latitude D630.

---

### Post by kostkon on 2009-02-03
OK. As it is Flash 9 will not work with *PulseAudio*. It indeed tries to have exclusive use of the card (instead of using dmix) and that's why you get these problems with it.

You have two options.

Install the *libflashsupport* package to make *Flash 9* work with *PulseAudio* but there are many chances that will make *Firefox* to crash a lot (I mean a lot).

Or the best option is to remove *Flash 9* and install Flash 10 (which works OK with *PulseAudio*). First of all make sure that you have the Partner repository enabled. Go to *System &#8594; Administration &#8594; Software Sources* and select the *Third-Party Software* tab to check.

Then you have to completely remove *Flash 9*. If you installed it from the repos, go to *Synaptic*, search for the *flashplugin-nonfree* package and remove it completely. I hope you did not install it from *Adobe*, because I don't really know how you can remove it. Definitely, check in *Synaptic* if the *flashplugin-nonfree* is already installed. This will mean that you have the *Flash 9* from the repositories.

Then search for the *adobe-flashplugin* package (this is *Flash 10*) and install it.

Hope that helps.

---

### Post by atatistcheff on 2009-02-03
Hehe, I knew you'd say that.  So.... I removed the flashplugin-nonfree package but Flash 9 was still there.  I then located all the libflashplayer.so files on the system and tracked down the version 9 file.  It was in my home .mozilla folder.  I tried installing the version 10 .deb package from Adobe but it put the library in the wrong spot.  So, I then got the tar.gz version and put it in the .mozilla folder.  Now my add-ons shows version 10 and in Pandora right-clicking shows it's using version 10 also. 

That's the good news.

The bad news is that even with version 10 running I still don't see the stream in the PulseAudio volume control.  I'm going to try and reboot to see if that does anything.

Thanks for your efforts so far, I hate these troublesome glitches.

---

### Post by kostkon on 2009-02-03
> **atatistcheff said:**
> Hehe, I knew you'd say that.  So.... I removed the flashplugin-nonfree package but Flash 9 was still there.  I then located all the libflashplayer.so files on the system and tracked down the version 9 file.  It was in my home .mozilla folder.  I tried installing the version 10 .deb package from Adobe but it put the library in the wrong spot.  So, I then got the tar.gz version and put it in the .mozilla folder.  Now my add-ons shows version 10 and in Pandora right-clicking shows it's using version 10 also. 

That's the good news.

The bad news is that even with version 10 running I still don't see the stream in the PulseAudio volume control.  I'm going to try and reboot to see if that does anything.

Thanks for your efforts so far, I hate these troublesome glitches.
Oh, sorry I thought you had followed [this how-to]("http://ubuntuforums.org/showthread.php?t=789578"). In 8.04 *PulseAudio* is not setup the right way, so you need to do it yourself.

Specifically, in 8.04 *ALSA* audio does not pass through *PulseAudio* and that's why you don't see the *Flash* audio streams appearing in the *PulseAudio* volume control.

Thus, do what the how-to says and then your sound will work much better in general and you'll see *Flash* appearing in the volume control ;)


Hope that helps.

---

### Post by kostkon on 2009-02-03
Also, it would be better to revert this:
> **atatistcheff said:**
> 
## FIREFOX_DSP="none"

per another thread I replaced it with:

FIREFOX_DSP="aoss"

---

### Post by atatistcheff on 2009-02-04
Ahhh, sweet sound!  Pulseaudio now works for Flash audio.  Thanks for the help, once I got to the right set of instructions it's working now.  :p

---

