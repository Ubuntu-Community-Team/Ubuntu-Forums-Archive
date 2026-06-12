---
title: "Sound in Totem but not in Flash"
date: 2009-12-06
forum: Multimedia Software
---

### Post by Migi32 on 2009-12-06
I used to have an Intel headset. It worked great, but I also bought a **Creative Fatal1ty USB Headset**, because it has a mic. The Fatal1ty works for some applications but not for others, but I was fine with that as I only needed it for Skype.

The problem is, I dropped my Intel headset. Now it's broken, and for some applications I now don't have sound.

[B]Sound works for:
[/B]System > Preferences > Sound
Totem movie player
Rhythmbox
Miro
Songbird
Skype

[B]Sound doesn't work for:
[/B]Firefox/Flash!!!
Wine[COLOR=Silver] [EDIT][COLOR=DimGray]unless set to OSS[/COLOR][/EDIT][/COLOR]
LMMS
VLC

There are two drivers for my Fatal1ty headset, one for ALSA and one for OSS. The ALSA one gives me the following error even after a clean reboot:[INDENT]audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
[/INDENT]The OSS driver works (that is, it gives me a test sound).

I think the problem is that the programs that don't work still have my Intel headset in their settings. There are plenty of tutorials on how to reconfigure your default output for ALSA (I tried them), but none I've seen for OSS.

The lack of Flash sound is becoming annoying though, but I've read the entire internet and then some without finding a solution, and I can only see one way out: Reinstalling. I could combine it with the upgrade from 9.04 to 9.10, but still...

Please use your amazing House-M.D.-like diagnostic skills to almost destroy my computer about three times but eventually cure it from this wicked disease. ;)

---

### Post by Yellow Pasque on 2009-12-06
With the exception of Skype (which uses ALSA directly unless you're using the skype-oss package), all of your working programs use Gstreamer (which you have set to OSS).

Try selecting OSS output in VLC's options or try the OSS driver in WINE:
```
winecfg
```

If the OSS stuff always works for you, try OSS4 before you reinstall: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Migi32 on 2009-12-07
Thank you Temüjin for you quick response.
 
So I guess it's pretty clear that OSS works and programs that don't give me sound don't do so becuase they aren't listening to my settings.
 
I can't try winecfg because I'm at school right now, but I'll do it when I'll get home. If changing to OSS helps there too, then we can beyond reasonable doubt assume that I should be upgrading ALSA, not OSS, right? Why would upgrading OSS help anything if it's already working correctly? :???:
 
However, in that linked article, I saw something else that I might try: "Configure ALSA Apps to Use OSS". Now that might work ;)
 
Let's invent a god and pray.

---

### Post by Yellow Pasque on 2009-12-07
> Why would upgrading OSS help anything if it's already working correctly?

You would be switching your sound driver to OSS(4), getting rid of ALSA and PulseAudio completely.

---

### Post by Migi32 on 2009-12-07
I launched winecfg and set wine to use OSS, and guess what: it worked! ;) I also double-checked to see that Skype really worked and strangely, it did, even though you say it's hard-coded to ALSA. Curious, I went back to System > Preferences > Sound, and suddenly the drivers for my Intel headset were gone. With hopes raised a little, I selected ALSA, clicked test, and lo and behold: it worked! :D All applications, including Flash, all work! :D

The weird thing is that I had already tried rebooting with my Intel headset unplugged yesterday, but this didn't solve anything, so I plugged it back in afterwards. I guess Linux only removes the drivers if the hardware has been unplugged for a longer period of time.

Software is so weird. If a chair - or any other piece of furniture - is broken, you can see that, and you definitely won't go and sit on that chair. Software can work one day and fail the next, with hardly any apparent reason. It's almost like it has a will of its own. :D

I think this even deserves some kind of entry in the troubleshooting FAQ:[INDENT]If it stopped working, don't do anything dramatic yet. Wait a day or two.
[/INDENT]

---

