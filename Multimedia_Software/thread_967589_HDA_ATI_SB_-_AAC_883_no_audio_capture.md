---
title: "HDA ATI SB - AAC 883 no audio capture"
date: 2008-11-02
forum: Multimedia Software
---

### Post by Spabuntu on 2008-11-02
Hello community!

i try to use skype to call friends back at home but it somehow does not work, nobody can hear me. i think this is somehow related to the audio capture but im not sure! the audiorecorder and audacity dont work either.

- i have tried all options in the audio preference settings for sound capture, depending on that the audiorecorder does not even start, doesnt record anything or seems to be recording but the length-of-file indicator is far to quick (about 40s per real time sec) the files are empty. audacity breaks down as soon as i push record

- in the audio preference menu for sound capture the option hda ati sb alc 883 (alsa) is listed twice. is that normal?

- in the volume control im using the HDA ATI SB device. the options in recording - capture and capture 1 recording always switch back to mute when i close the audiocontrol


I really hope someone can help me cuz i really need to use skype!:(

many thanks in advance, marc


p.s.: "sudo killall pulseaudio" sort of helped me. its still not perfect but at least i can use skype. quality is not really good tho!

---

### Post by Spabuntu on 2008-11-02
Hmm with "killall pulseaudio" i can use skype and audiorecorder etc. but it breaks down after something like 20 minutes or as soon as i open another programme like firefox. audiorecorder does not work anymore and noone can hear what i say on skype or ekiga.

than i have to restart my computer and have to disable pulseaudio again

- does anyone now how i can permanently disable pulseaudio as it obviously only cause problems?
- any ideas why the audiocapture breaks down after some time / opening a programme?

many thanks in advance!

marc

---

### Post by fabiobaq on 2009-05-10
I'm experiencing the same problem. I have removed pulseaudio and installed esound instead ([http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)). Though it works, captured sound quality is really very poor - it is almost impossible to maintain a conversation thru skype, for example.

---

