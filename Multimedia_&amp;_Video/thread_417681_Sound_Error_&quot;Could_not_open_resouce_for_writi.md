---
title: "Sound Error: &quot;Could not open resouce for writing.&quot;"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by anonymoususername on 2007-04-21
OK, so basically, I upgraded from Edgy to Fiesty, and now my laptop no longer plays sound. Several applications now give the error "Could not open resource for writing." when attempting to play sound. I've checked through the sound problems guide, and my drivers are all installed and loaded, it just doesn't work. I couldn't see anything else there, maybe I missed it, but I doubt it.

---

### Post by anonymoususername on 2007-04-22
If it helps, I'm using an ATI SB450 HDA Audio sound card, apparently.

---

### Post by taural.cw on 2007-04-22
I know how you feel.

I have exactly the same problem/error message with exactly the same sound card. Although Windows detects my card as a RealTech HDA card. Worked perfectly with Edgy but now its dead.

Have tried the fixes I have found on the forums but nothing seems to work, so I would be very interested in a solution to this problem too.

If I make any progress I'll let you know.

---

### Post by anonymoususername on 2007-04-24
Still no solution to this? Having no sound is a right pain in the backside.

---

### Post by Snowmayne on 2007-04-24
Amazing how many different threads there are on this issue (feisty with no sound) and yet, for all the different suggestions, it doesn't seem to be limited to 1 type of sound card, motherboard or model.

---

### Post by Snowmayne on 2007-04-25
So, yesterday I downloaded another copy of Feisty and ran a new install of the live cd. Long story short: sound's back up and running, but now I've got 2 days of fine-tuning to look forward to (apps to re-install, settings to fine tune, files to xfer over from window's partition).

Was just strange that the alsa folder was empty on the previous install and nothing (including re-installs of gstreamer and alsa) resolved that

---

### Post by anonymoususername on 2007-04-26
> **Snowmayne said:**
> So, yesterday I downloaded another copy of Feisty and ran a new install of the live cd. Long story short: sound's back up and running, but now I've got 2 days of fine-tuning to look forward to (apps to re-install, settings to fine tune, files to xfer over from window's partition).

Was just strange that the alsa folder was empty on the previous install and nothing (including re-installs of gstreamer and alsa) resolved that

****. With the number of files and applications I have on here, it would probably be a Hell of a lot easier to just wait it out until someone can find a solution. Even if it means silence for however long.

---

### Post by cgdef on 2007-07-11
i have a similar problem. TV time was not getting any sound but gnome applications like rhythbox and totem worked fine. So I recompiled and reinstalled alsa ( all of it's components ). Well now I have no sound and a stupid error that says could not open device for writing. Only mplayer works fine if you chose openal as the sound output device. And it also seems to detect the default alsa sound card. Oh and all the alsa configuration utilities work fine too and I get no other errors. I don't know what the problem is but this seems very much like an ubuntyuspecific one and it's about time that the sound issues get resolved. Oh and I would have never had to recompile alsa if the version in the repositories was up to date and supported ALL of the alsa supported cards.  

I like Ubuntu in general but this kind of crap ha to go. Oh and you can't tell people to just reinstall when they run into a problem. This is simply unacceptable if the software is supposed to be reliable. But apparently this is just my opinion ...

Edit: after some changes in .asoundrc now I can got the sound working when it's set to autodetect. However if I select any one of the 2 soundcards that I have it does not work. I get an error that device <some_number> is not found. This is deffinitely a configuration problem only the ubuntu configuration files documentation is simply marvelous and I can't seem to find what configuration file was moved to where and such. Well I guess this is another example of why you need documentation when you write software. ( or change things for that matter )

Anyway if anyone know how I can fix this error it would be much appreciated. 

sound-properties-Message: Error running pipeline 'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink': Could not open resource for writing. [gstalsasink.c(626): gst_alsasink_open (): /pipeline0/gconfaudiosink0/bin0/halaudiosink0/bin1/alsasink0:
Playback open error on device 'default:0': No such file or directory]

sound-properties-Message: Error running pipeline 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat': Could not open resource for writing. [gstalsasrc.c(600): gst_alsasrc_open (): /pipeline8/gconfaudiosrc3/bin16/halaudiosrc2/bin17/alsasrc3:
Recording open error on device 'plughw:1,1': No such file or directory]


and so on. The problem seems to be that gnome cannot find which device is which but then why does automatic discovery work? And I need to manually select the 2nd card as the input device because Indigo DJ does not have an input.

---

### Post by devapea on 2007-07-11
Ok I may have a tiny kernal of help for you guys.  Ive had the same problem with the same error messege when I tried playing dvds in totem.  A setting that you should look at is in system>preferences> sound.  I changed my music and movies sound  playback from Alsa to the older OSS.  try it and press the test button and see if ya hear a test  sound. I get one with OSS but not with Alsa.  good luck

---

### Post by speirint on 2007-07-18
I had the same problem but with an integrated intel sound card.  I tried reverting to the OSS and it worked for me.  I had to select the OSS mixer as my default mixer track device and set everything (music and movies, sound conferencing, and sound events) to the OSS.  Thanks devapea.  A brief search through some other forums also have some similar suggestions about the oss as well.

---

### Post by speirint on 2007-07-22
Alright, last night I was running the rythmbox media player and sound worked fine (albeit quieter than before when I used the ALSA) as well as in streaming internet (youtube, etc.) audio.  Suddenly, the songs (all of my audio files, I tried several other songs saved in different places, tried playing them individually through the places menu, even in different media players and I'd still get no sound) would no longer be playable, I'd get this pop up message:

Couldn't Stop Sound Playback
unknown playback error

Checking the sound settings in the system, everything was still set to the OSS players, which as I posted before did give me sound during the tests and made everything work out honky dory.  Now when I test them I get this:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.  

Was Bob Dylan's nasal voice too much for my computer?  What's going on now?

So in recap, I've got issues with media and sound (no sound) on the computer unless I play something from streaming media off of the internet.  Is this still the same problem as well?


Edit:7/24/07
The test sounds work again, as well as the normal rythmbox stuff now.  Strange indeed.

Edit:7/26/07
Test sounds do not work now.  Back to saying 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.

---

### Post by speirint on 2007-08-01
Try these out as well, several other people have been having problems with sound, one guide is very extensive and may answer many other sound problems, though I'm not sure if it solves mine.


[http://ubuntuforums.org/showthread.php?t=502880&highlight=audigy+sound+card+feisty&page=2](http://ubuntuforums.org/showthread.php?t=502880&highlight=audigy+sound+card+feisty&page=2)


[http://ubuntuforums.org/showthread.php?t=512039](http://ubuntuforums.org/showthread.php?t=512039)

---

### Post by gabrielcz on 2007-11-07
Same problem here guys.

I dont get the micro, Until now, my sounds works fine.
I touch ALL on settings without lucky.

Regards.

---

