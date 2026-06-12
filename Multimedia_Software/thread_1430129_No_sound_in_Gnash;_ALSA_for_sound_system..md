---
title: "No sound in Gnash; ALSA for sound system."
date: 2010-03-15
forum: Multimedia Software
---

### Post by RobbieThe1st on 2010-03-15
I'm running Kubuntu 9.10 X64, and am using ALSA for my sound.
I have no trouble with sound: VLC, Adobe's Flash plugin, Java, etc. all work properly.
When I run the Gnash standalone player, sound does not work at all.
When I run Gnash in a terminal, I get this:
> 
robbiethe1st@rb-dt:/Data/comics/Artists/tirrel$ gnash -v ./1220368654.cerberus_rockoonstv.swf
**11011:1] 21:42:55 ERROR: Could not create sound handler: Unable to open SDL audio: No available audio device. Will continue w/out sound.**
11011:1] 21:42:55 ERROR: Gui::getQuality called before a movie_root was available
11011:1] 21:42:55 ERROR: Gui::getQuality called before a movie_root was available
Fontconfig warning: "~/.fonts.conf", line 586: saw number, expected matrix
11011:1] 21:42:55 SECURITY: Checking security of URL 'file:///Data/comics/Artists/tirrel/1220368654.cerberus_rockoonstv.swf'
11011:1] 21:42:55 SECURITY: Load of file /Data/comics/Artists/tirrel/1220368654.cerberus_rockoonstv.swf granted (under local sandbox /Data/comics/Artists/tirrel/)
11011:1] 21:42:55 SECURITY: Extensions disabled
11011:2] 21:42:55 ERROR: There is no sound handler currently active, so DisplayObject with id 17 will NOT be added to the dictionary
11011:2] 21:42:56 UNIMPLEMENTED: DefineFontInfo2 partially implemented
I'm thinking it has something to do with the bold line; I tried googling, but I didn't turn up much.
I'm hoping that this problem is simple: It's probably just a missing package or something.


Any ideas guys?

-Robbie

---

### Post by Yellow Pasque on 2010-03-15
Ok, so gnash is trying to use SDL. I assume you have the libsdl1.2debian-alsa package installed. If not, install it. If that doesn't help, make sure the environment variables are set properly.
```
kate ~/.bashrc
```
Append these lines to the end of the file:
```

export SDL_AUDIODRIVER=alsa
export AUDIODEV=plug:dmix

```
Save. Quit. Log out and back in. Try it again.

---

### Post by RobbieThe1st on 2010-03-15
First off, thanks for taking the time to help me out here.
It appears that for some odd reason, I had the PulseAudio version of that package installed. Once I installed that ALSA version, I stopped getting the "unable to open audio" error.

However, sound still doesn't work. I've tried with several flash files, to the same effect:
```

robbiethe1st@rb-dt:/Data/comics/Artists/tirrel$ gnash -v 1220368654.cerberus_rockoonstv.swf
3410:1] 19:45:25 ERROR: Gui::getQuality called before a movie_root was available
3410:1] 19:45:25 ERROR: Gui::getQuality called before a movie_root was available
Fontconfig warning: "~/.fonts.conf", line 586: saw number, expected matrix
3410:1] 19:45:25 SECURITY: Checking security of URL 'file:///Data/comics/Artists/tirrel/1220368654.cerberus_rockoonstv.swf'
3410:1] 19:45:25 SECURITY: Load of file /Data/comics/Artists/tirrel/1220368654.cerberus_rockoonstv.swf granted (under local sandbox /Data/comics/Artists/tirrel/)
3410:1] 19:45:25 SECURITY: Extensions disabled
3410:2] 19:45:25 UNIMPLEMENTED: Different stream/playback sound rate (22050/44100). This seems common in SWF files, so we'll warn only once.
3410:2] 19:45:25 UNIMPLEMENTED: Different stream/playback sample size (32/16). This seems common in SWF files, so we'll warn only once.
3410:1] 19:45:25 UNIMPLEMENTED: MP3 delaySeek
3410:2] 19:45:25 UNIMPLEMENTED: DefineFontInfo2 partially implemented
3410:2] 19:45:25 UNIMPLEMENTED: MP3 soundblock seek samples

```

Thanks,
-Robbie

---

### Post by soltanis on 2010-03-16
Chances are that wasn't the only thing that was configured for PulseAudio. Do you have PulseAudio installed? If so, I would try disabling it or removing it, then installing ALSA support packages instead.

---

### Post by Yellow Pasque on 2010-03-16
I'm guessing that the UNIMPLEMENTED warnings indicate limitations of gnash, and not audio setup problems. What version of gnash are you using? If you're using the 0.8.6 version from the karmic repo, you might want to try the 0.8.7 version using this PPA: [https://launchpad.net/~gnash/+archive/ppa/+packages](https://launchpad.net/~gnash/+archive/ppa/+packages)

---

### Post by RobbieThe1st on 2010-03-16
I just setup the PPA and upgraded... works, but no luck. I've tried any number of flash files, some from before 2006(Though all seem to have MP3 content in them), and absolutely no sound.

With each of them, I get:
```

3904:2] 19:43:55 UNIMPLEMENTED: Different stream/playback sound rate (5512/22050). This seems common in SWF files, so we'll warn only once.
3904:2] 19:43:55 UNIMPLEMENTED: Different stream/playback sample size (32/16). This seems common in SWF files, so we'll warn only once.
3904:2] 19:43:55 UNIMPLEMENTED: MP3 soundblock seek samples
3904:1] 19:43:57 UNIMPLEMENTED: MP3 delaySeek

```
Either its not playing because of these, or something completely differen't isn't right; perhaps FFMPEG isn't installed right? Any thing I can check?
Heck, if one of you guys had a flash file that was known to work on Gnash, that would be helpful.
---
I just checked again: PulseAudio is -not- installed.

---

