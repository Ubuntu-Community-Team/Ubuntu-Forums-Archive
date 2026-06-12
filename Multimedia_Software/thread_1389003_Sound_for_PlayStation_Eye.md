---
title: "Sound for PlayStation Eye"
date: 2010-01-23
forum: Multimedia Software
---

### Post by sethhikari on 2010-01-23
I am using 9.10 and I am plugged in with my PS3's eye. I get perfect video but I can't manage to get sound. under volume control it shows up but when I speak the volume indicator is blank. Anything I need to do?:confused:

---

### Post by moddie666 on 2010-01-28
Hello.

I am having the same problem, running Karmic.

anyone got any ideas?

thanks

-EDIT-
It does seem to help if the Camera is connected before booting, the ps3 eye mic now works.

hope that helps.

greetings
/moddie

---

### Post by brand0ng on 2010-02-26
i am having the same problem, and my camera is connected at boot but i still cant seem to get it to use input for any app that ive tried (skype, sound recorder)

---

### Post by Dayofswords on 2010-02-26
i'm sorry...

its eye?

its this like the eyetoy?

---

### Post by kostkon on 2010-02-26
First of all, can you see it listed in the *Input* tab of your sound preferences (*System &#8594; Preferences &#8594; Sound*)?

---

### Post by tyfo on 2010-06-30
Hi all, this thread seems to be dead and unanswered question is what's last. I google more or less a week now trying to find solution for video AND sound working fine with ps3 eye in, say, Skype. It's actually in any other app. Since my Dell e6400 did not come with a built-in microphone module (don't ask, got it for free) and I happen to have the ps3 eye, I thought it would be a good use of both.

The video works fine anytime. Just plug in the ps3 eye, launch Skype and you can use the webcam for just anything you want.

The audio part is the tricky one. It seems to work just fine when ps3 eye is connected at boot time. It is visible in System > Preferences > Sound > Input as a separate device, can be chosen and use - in Skype as well. You can disconnect, Ubuntu will select the non-existing microphone (physically no mic module, the chip is there, you could probably use the mic jack). After connecting again, the ps3 eye is again visible as another audio input device.
What does NOT work is plugging the ps3 eye after boot up. You can't use the microphone at all, system does not see it as another audio input (in System > Preferences > Sound > Input), contrary to the above. But you still can use it as a webcam.

Any hints?

---

### Post by AKADAP on 2010-06-30
I was never able to get sound to work with the Playstation Eye in Skype. It would not turn the camera on, and the camera needed to be on to turn on the mic.

I was able to get the sound to work with the Microsoft LifeCam Cinema. That camera seems to work fine with Skype. Skype will turn this camera on to activate the mic.

---

### Post by tyfo on 2010-06-30
> **AKADAP said:**
> I was never able to get sound to work with the Playstation Eye in Skype. It would not turn the camera on, and the camera needed to be on to turn on the mic.
That is not the case for me. Mic and cam seem to work independent, but only when plugged in at boot time. Otherwise the it's not visible as a sound input device, webcam only.

> **AKADAP said:**
> I was able to get the sound to work with the Microsoft LifeCam Cinema. That camera seems to work fine with Skype. Skype will turn this camera on to activate the mic.
Thanks for the hint, but no I won't by that camera ;)

---

### Post by dbowlin17 on 2010-08-09
I was able to get sound to work. but when I went into cheese to test it out, the video turned the camera on... but the video was really messed up...

---

### Post by Rootbrian on 2010-11-22
I recently acquired a PlayStation Eye, it works quite well, only there's a glitch with the driver on ubuntu, I tested the windows driver just to be sure it wasn't a heat issue (the camera gets quite warm) and it worked fine without any glitches whatsoever.

I'm not concerned about the nonfunctional mic on the camera, as it's not such a big deal to me. I only need to find out why the video is going haywire when used in flash player and sometimes, Cheese.

Video: [http://www.youtube.com/watch?v=JcKHk7Ot5vY](http://www.youtube.com/watch?v=JcKHk7Ot5vY) (recorded on Ubuntu)
Video: [http://www.youtube.com/watch?v=YtWgZXFAkEE](http://www.youtube.com/watch?v=YtWgZXFAkEE) (recorded on Windows XP Home, using driver provided by Code Laboratories, inc.)

---

### Post by moddie666 on 2010-11-22
@Rootbrian
you should test it out on a ps3 to see if it is damaged.
mine seems to work fine if it is connected before booting,
even with sound.
what you have is not an issue I have ever seen with this
camera.
Perhaps if you used some kind of flash app for recording
that could be the source of the problem. Adobe Flash has
always been a bit buggy on Linux as far as I know.

Video always works, sound only works when connected before
booting.

Tested with VLC ( /dev/video0 )
and Skype
-EDIT-
Just tested now and there seems to be an issue like yours
since 10.04. I have no idea whats going on. Just wait some
time and see what happens with further updates.

greetings
/moddie

---

### Post by Rootbrian on 2010-11-24
> **moddie666 said:**
> @Rootbrian
you should test it out on a ps3 to see if it is damaged.
mine seems to work fine if it is connected before booting,
even with sound.
what you have is not an issue I have ever seen with this
camera.
Perhaps if you used some kind of flash app for recording
that could be the source of the problem. Adobe Flash has
always been a bit buggy on Linux as far as I know.

Video always works, sound only works when connected before
booting.

Tested with VLC ( /dev/video0 )
and Skype
-EDIT-
Just tested now and there seems to be an issue like yours
since 10.04. I have no idea whats going on. Just wait some
time and see what happens with further updates.

greetings
/moddie

Tried everything, don't have a PS/2 or PS/3 console, webcam works as normal on windows, it's just funky with flash player on linux as you mentioned. Not a big deal, sounds like it's a cool way to fool the viewers.

It works fine on cheese, though when capturing, cheese has that bug that puts video capture at 640x480 as 1 fpm (Frame per minute).

---

### Post by muzah on 2011-01-27
Hi!

I recently purchased a Playstation Eye.
Convinced I had to install drivers (make etc.) I lost a morning before noticing that it's just plug n'play with Maverick Merkat.

If video is great as mentioned before, the sound is quite unstable, or something like that. Like others, I have googled a lot before and no answer.

So, like you guys, the 4 mics are well recognize by pulseaudio but nothing on entry level. After noticed that the mics worked sometime, after random plug/unplug, PC on or off, etc. I just try to daemonize pulseaudio (sorry, I only have a [french source]("http://doc.ubuntu-fr.org/pulseaudio#pulseaudio_en_tant_que_demon_systeme") so I let you find the english one) and now, if after a normal boot of ubuntu the mics don't work, I just :

sudo service pulseaudio restart

Voilà! Check the sound properties and see the entry sound level working !

It's not the cutest way to make these mics work but...

I hope it helps you - and you understand my rusty English.

---

