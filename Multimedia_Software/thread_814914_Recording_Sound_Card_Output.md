---
title: "Recording Sound Card Output"
date: 2008-06-01
forum: Multimedia Software
---

### Post by Eidolons on 2008-06-01
I want to record my sound card's output for obvious reasons.  I looked at 'alsamixer' in the terminal and it seemed that the audio output went through "Front."  So I went into Audacity and set the recording setting to "ALSA: Front."  It altered my audio settings that I have setup because one of my earbuds is a lot quieter than the other.  Other than that, hitting record did nothing.  I noticed the tab with the settings like "Capture:0", "Capture:1", "Digital:0."

Is there a better program that I could use or something else that I need to set?  Someone told me about Jack Audio, but I have had a hard time finding proper documentation and it might be more complicated than it needs to be.

I could give more details about my sound hardward but it is just integrated audio for an Inspiron 1520, as far as I know.  I had to use 'backports' to get my sound to work on Ubuntu 7.10 which is what I am using.

---

### Post by ron999 on 2008-06-01
> **Eidolons said:**
> 

Is there a better program that I could use or something else that I need to set?  
Hi
I use **arecord**.
It's tricky to set up.
But when it's right the command is just:-
```
arecord -f cd foo.wav
```
Also there are different commands to capture as mp3 or ogg or whatever.

No need to use Audacity unless you want to edit the recording later.
This is the howto that I followed:-
[http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/]("http://jordilin.wordpress.com/2006/07/28/howto-recording-audio-from-the-command-line/")

---

