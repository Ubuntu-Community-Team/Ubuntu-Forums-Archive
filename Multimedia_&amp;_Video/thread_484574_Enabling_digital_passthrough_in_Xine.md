---
title: "Enabling digital passthrough in Xine"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by Bohlio on 2007-06-25
Ive been having a problem with my surround sound, No matter what option i choose in totem, It only outputs two channel PCM to my receiver. Well Im kinda a noob with ubuntu and dont know much about the command line, so i decided to run totem --debug and hope something interesting came up. Sure enough, It did. The message i got was ```
audio_alsa_out : supported modes are 8bit 16bit 24bit 32bit mono stereo 
(4-channel not enabled in xine config) (4.1-channel not enabled in xine config) 
(5-channel not enabled in xine config) 5.1-channel (a/52 and DTS pass-through not enabled in xine config)
```
So i guess the solution is to enable A/52 and DTS pass-through in Xine config, But i have absolutely no clue how to do that. Is anyone willing to help a noob out and point me in the right direction?? Thanks a bunch :-)

---

### Post by Bohlio on 2007-06-26
Well, I guess with a little bit of googling anyone can solve their own problem :-) Ill walk through what i did for anyone else who has this problem. Remember this is using Totem with Xine. 
To edit xine config, type in ```
 gedit .gxine/config
``` Search for "speaker_arrangement" using Ctrl F and you should have a block of text similar to this ```
# speaker arrangement
# { Mono 1.0  Stereo 2.0  Headphones 2.0  Stereo 2.1  Surround 3.0  Surround 4.0  Surround 4.1  Surround 5.0  Surround 5.1  Surround 6.0  Surround 6.1  Surround 7.1  Pass Through }, default: 1
#audio.output.speaker_arrangement:Stereo 2.0
``` Change the last line to ```
#audio.output.speaker_arrangement:Pass Through
```Save the file, and you should be all set for Dolby Digital or DTS passthrough :-) There is one thing that i dont get about this, I thought lines that had a "#" in front of them were ignored, yet editing it and leaving the "#" there fixed my problem. If any ubuntu genius could explain this, that would be great.
I hope this helps someone searching for their surround sound solution :-)

Edit: After going through my mini guide :-) to make sure it was right, I came across an oddity. When i look at my config file, the section that i edited seems to have reverted back to the original, like I never touched it, Yet my passthrough works perfectly now. If any ubuntu genius could explain this one too, that would be great :-P

---

