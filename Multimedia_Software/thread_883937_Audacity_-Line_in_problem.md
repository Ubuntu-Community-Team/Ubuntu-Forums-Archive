---
title: "Audacity -Line in problem"
date: 2008-08-08
forum: Multimedia Software
---

### Post by thered on 2008-08-08
just got a second hand turntable and decided to copy some old vinyl to mp3/wav.

i can hear the sound coming through my soundblaster live card, no bother on line in.

I can't however get it to record in Audacity, files are blank.  I've tried all the available audio devices - none seem to work.

Headscratching here, anyone help.

edit: Oh, it works in windoze -so not a hardware problem.

---

### Post by fishbulb1022 on 2008-08-08
I think i had a similar problem in windows once, i believe the simple solution i used was to just plug the source (your record player) into the mic instead of the line in. (Also, you might look at audacity's settings and configuration in audacity if you have't already, or just do a google search for recording with audacity)

---

### Post by thered on 2008-08-08
fishbulb: Seems to be a paucity of information apart from the standard 'help' files.

Plugging in to mic input didn't help either.

As I've said already tried ***all*** input devices in Audacity' preferences.

Have noticed that in 'Sound Preferences' I get no test sound in 'Audio conferencing - Sound Capture' no matter which device I use. Not sure if this is related to the initial problem.

Thank for trying to help.

---

### Post by fishbulb1022 on 2008-08-10
I looked around the forums and found some other people were having the same problem as you, this one [http://ubuntuforums.org/showthread.php?t=873951&page=4]("http://ubuntuforums.org/showthread.php?t=873951&page=4") got solved, so you might check it out, this is a link to the last page (i think), you'll probably want to look at it from the beginning. I hope it helps.

---

### Post by thered on 2008-08-13
Fishbulb: Sorry about delay in replying.  I have different settings to those but I've tried all the available options.  

<i'll keep trying though.>

---

### Post by JC Cheloven on 2008-08-13
> **thered said:**
> just got a second hand turntable and decided to copy some old vinyl to mp3/wav.

i can hear the sound coming through my soundblaster live card, no bother on line in.

I can't however get it to record in Audacity, files are blank.  I've tried all the available audio devices - none seem to work.

Headscratching here, anyone help.

edit: Oh, it works in windoze -so not a hardware problem.

I'm having the same problem this evening. I'm trying to record sound under linux for the first time. 

At first sight I figure out that is a matter of program versions: In windows the delivered version (at least mine) is 1.2.6 stable, which also works flawessly for me. In ubuntu the delivered version is 1.3.4 beta, which I think is not ready yet. I'll look for a proper way of installing Audacity 1.2.6 stable in ubuntu.

If you do so before me, please post your experience ;-)

Greetings

---

### Post by thered on 2008-08-19
JC: Just back to try again in linux - no joy yet.

I too have version 1.3.4

Please post here again if any more info.

cheers 

R.

edit: Can't record using linein on 'sound recorder' either!  Can hear the bl**dy thing through speakers though -very frustrating!

---

### Post by thered on 2008-08-19
OK...I think I've sorted it.

Need to add 'Capture' to 'volume control' GUI and also line in capture 'switch' 

Couple of images attached to help explain.

I left audacity set with defaults - i.e. OSS:/dev/dsp

Only problem now is output volume from Audacity too low.  Working on it.

---

### Post by varangian on 2008-08-24
Thanks thered, your research was most useful. Whilst I don't see quite the same dialogs as you - due to having a different sound card I'd guess - you pointed me in the right direction to solve exactly the same problem. Would have taken me much longer if a forum search hadn't brought me to this thread.

---

### Post by ave2 on 2009-09-01
I want to also add my thanks- Came across this from google-it helped a lot

---

### Post by TSMJ on 2009-12-20
What fixed it for me:

1. Open up the Volume Control
2. Ensure an 'Alsa mixer' device is selected
3. Click Preferences
4. Enable all 'Recording' and 'Options' entries
5. Click the new Options tab and select the input source
6. Set the volume of the input on the Recording tab.

---

