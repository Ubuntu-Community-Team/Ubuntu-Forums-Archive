---
title: "record sound card output to file (stereo mix)?"
date: 2013-06-19
forum: Multimedia Software
---

### Post by L a r r y on 2013-06-19
Running UIbuntu 12.04, and I have need to record what I hear over the speakers onto a sound file.

I can generate Morse code by using the command line program called **morse**.  It outputs in either ALSA or OSS, and I selected ALSA since the other does not work.  Using command line utilities that ship with ALSA, I can set the sound card  with **amixer** to stereo mix, and use **arecord** to record to a wave file.  Morse will play and arecord will record, and I can play it back in a music player.

My problem is, arecord's output is RIFFL format wave instead of RIFF format, as seen in a hex editor.  The DC bias is above the center line in my RIFF editor, and it is below the center line if I am recording off the microphone in my RIFF-compatible editor.  I can invert the RIFFL waveform to make the DC bias be the same on both, but that is about all I can do with it.  If I zero out the DC bias, if I try to reduce noise, then the file gets noisy.  if I use the Sound Converter, the resulting file will be noisy.  So I can DO Stereo Mix, but I can't convert the file for use on my web site.

I used Ardour, which recorded a nice RIFF file from my microphone, but if I use amixer to set to Stereo Mix, the Morse won't produce a sound until the Ardour is closed.  Sweep won't record it either, because if Morse is playing, Sweep finds the resource busy.  If I record then play Morse, Sweep records a blank file.

Of course Windows software in Wine won't touch it.  My Syntrillium Software Cool Edit just records a blank file if I have Stereo Mix turned on.  I run "Windowa XP."  Wine uses ALSA driver.

Maybe there's some hope with PulseAudio?  That leaves my Cool Edit out and I will have to use one of the Linux sound editors, but the morse program only supports ALSA or OSS.

There may be another way around this, by playing Morse on one computer and recording to another or to my voice recorder -- the latter would eat a lot of batteries!  But it would give me an MP3 file I can load back into the computer, rip and edit.

Anybody have ideas of how I might get this done?

Hmm.  Maybe I could burn an audio CD from the arecord file, then play the CD back.  Each track of an audio CD is seen as a wave file, maybe of the RIFF variety.....

---

### Post by ajgreeny on 2013-06-19
Try sound-recorder (part of gnome-media package) or audacity, both of which will record the soundcard output if you use the correct settings in pulseaudio or the sound configuration used by your machine.

---

### Post by CatKiller on 2013-06-19
ALSA output is fine for Pulse; it just treats it like any other application stream. Pulse uses ALSA as its backend, anyway. It should be able to do what you want. There's also a monitoring option that will double-up the output stream if you find that that's something you need.

If you want to get funky with your audio routing there's JACK, although that might be overkill for this particular task.

---

### Post by mc4man on 2013-06-19
Best current app to record sound (what you hear.
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

---

### Post by L a r r y on 2013-06-20
Thanks everyone, I will check out the suggestions made here, starting with the audio-recorder offered by mc4man, then the sound-recorder from ajgreeny. There are some good links there to follow up on.

I see I don't have either one of these in here, so I have some work to do!

---

### Post by L a r r y on 2013-06-20
> **mc4man said:**
> Best current app to record sound (what you hear.
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

This recorder has filled the need! 

I can record sound output from Wine software and Linux software.

Save it as 32 bit wave, or as CD quality ogg, and if I do the latter I can convert it to 16 bit wave, and it can be edited in good order in my Wine Cool Edit sound editor -- I just have to rename the file to remove Windows-illegal characters first.

I can record either off the output or the microphone, and I can meet my objective by recording off the output with the Morse program running.

I need to record a playback of those arecord files I have already created, that just get noisy if I convert them.  Maybe I can convert the resulting ogg to 16-bit wave and do some clean-up and convert them successfully to production files I can upload.

Used to be a "Mark thread as "SOLVED" in my thread tools above.  I would mark this one as SOLVED now.  Thanks guys!

---

### Post by ajgreeny on 2013-06-22
As you like it so much, I have just downloaded and tried the audio-recorder for myself.

Brilliant, I have to agree. it is a bit like sound-recorder from the gnome-media package but better, and the configuration is a lot easier to set up for whatever your particular need is at any time.
The one very minor disappointment as far as I'm concerned is that it is setup to autostart at login by default, something which annoys me, and I think should never be the default; I much prefer it when applications ask at first run, if you want that to happen.  I did set the configuration not to run at startup, but for some reason it still appeared in the system tray.

PS: To mark the thread as solved go to your original post and use "Edit Post" -> "Go Advanced" and change the Prefix box to **SOLVED** or add **SOLVED:** to the front of the title box.

---

### Post by osmoma on 2013-07-31
Hello [COLOR=#000000][[COLOR=#000000]ajgreeny[/COLOR]]("http://ubuntuforums.org/member.php?u=27747") [/COLOR]
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]
You can switch off the autostart in the [Additional settings]. Just tell me if it does not work. There were some problems with this in the earlier versions.
Ref: [http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/auto-start.c](http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/auto-start.c)

Kindly
 Moma Antero  (programmer of the audio-recorder).
Portugal

---

### Post by ajgreeny on 2013-08-08
> **osmoma said:**
> Hello [COLOR=#000000][[COLOR=#000000]ajgreeny[/COLOR]]("http://ubuntuforums.org/member.php?u=27747") [/COLOR]
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]
You can switch off the autostart in the [Additional settings]. Just tell me if it does not work. There were some problems with this in the earlier versions.
Ref: [http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/auto-start.c](http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/auto-start.c)

Kindly
 Moma Antero  (programmer of the audio-recorder).
Portugal

Hi there Moma.
Thanks for the info, which I have only just seen, though  I had already found the option to remove autostart and it is working exactly as I wanted, thank you.

Great program which makes recording some output so much more easy than the alternatives such as audacity, though I use that a lot for editing audio files.

That is the great advantage of linux; so much choice!

---

