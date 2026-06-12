---
title: "unable to have two programs playing sound at the same time"
date: 2008-12-06
forum: Multimedia Software
---

### Post by hatten on 2008-12-06
Hello, I'm using Ubuntu hardy heron and i cannot have two programs playing sound at the same time, Firefox and Iwbtg (with wine) just doesn't make any noice, totem and rythmbox doesn't play at all, and OpenLieroX crashes if i have another application running with sounds at the same time. Is it some weird preference somewhere, wrong with my computer, a bug or anything similar? My brother suggested a "mixer" like program that collects all sounds and then sends them to the speakers but i haven't found any good yet.

---

### Post by hatten on 2008-12-07
wine (iwbtg) an openlierox succeeded in having both running with sounds at the same time...:S

---

### Post by hatten on 2008-12-09
Nobody knows anything? lol, i haven't even been asked for an output (that i in this case do not know how to get) while in the absolute beginner talk i got help in a few minutes, where are everybody? Or should i repost this in the absolute beginner talk lol?

---

### Post by andr100 on 2008-12-09
It's very original to listen 2 music simultaneous! I can't help you! Sorry

---

### Post by hatten on 2008-12-09
but i want the sound effects of one game and the music from rythmbox. It's not enough with pausing rythmbox either but i must quit it each time i want to check a youtube movie or similar and then boot it again :P

---

### Post by druellan on 2008-12-09
Just for the check, make sure you are NOT using OSS as audio output on system->preferences->sound. Also, you can take a look running on a terminal: gstreamer-preferences.

---

### Post by hatten on 2008-12-09
```
hatten@stetson:~$ gstreamer-preferences
bash: gstreamer-preferences: command not found
```like that?
And in system->preferences->sound there is no such thing as audio output?

---

### Post by druellan on 2008-12-09
On system->preferences->sound just switch all options to automatic or pulseaudio or ALSA sound system. You don't need to restart the system but close and reopen all audio apps like Rhythmbox. (BTW, the default value must be automatic).

About gstreamer-preferences: my fault, its gstreamer-properties :P But before running it, check the changes in system->preferences->sound.

---

### Post by pietjanjaap on 2008-12-09
Search for pulsaudio.

---

### Post by hatten on 2008-12-09
> **druellan said:**
> On system->preferences->sound just switch all options to automatic or pulseaudio or ALSA sound system. You don't need to restart the system but close and reopen all audio apps like Rhythmbox. (BTW, the default value must be automatic).
my sound preferences looks like this: [http://img411.imageshack.us/img411/804/screenshotsoundpreferenkt5.png](http://img411.imageshack.us/img411/804/screenshotsoundpreferenkt5.png)
the three first beeps when testing, but the last one does not, not at a single one of the options that i have, not even the test sound. When i tried changing the first one to OSS i got the error message ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.
``` and with ALSA ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.
```i had rythmbox running.
After closing rythmbox both of them worked.

---

### Post by hatten on 2008-12-09
In gstreamer-properties [http://img401.imageshack.us/img401/6098/screenshot3av4.png](http://img401.imageshack.us/img401/6098/screenshot3av4.png)

the first one beeps but the second does not

---

### Post by wolfen69 on 2008-12-09
which flash version are you using? flash 9 had a bug which would not allow 2 sound sources at the same time. uninstall the current flash and go [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu and click to install. then reboot.

---

### Post by hatten on 2008-12-09
> **wolfen69 said:**
> which flash version are you using? flash 9 had a bug which would not allow 2 sound sources at the same time. uninstall the current flash and go [here]("http://get.adobe.com/flashplayer/") and download the .deb for ubuntu and click to install. then reboot.

how can i check which version of flash i have?

---

### Post by juanoleso on 2008-12-09
you might try going back into system >  preferences > sound and changing music and movies to ALSA and if that doesn't work changing all of them to ALSA.  That worked for me when I couldn't do Rhytmbox and UrbanTerror at the same time.

---

### Post by hatten on 2008-12-09
> **juanoleso said:**
> you might try going back into system >  preferences > sound and changing music and movies to ALSA and if that doesn't work changing all of them to ALSA.  That worked for me when I couldn't do Rhytmbox and UrbanTerror at the same time.

it worked with changing everything to ALSA! thanks a lot! :D

---

### Post by druellan on 2008-12-09
Glad to hear that :)

---

