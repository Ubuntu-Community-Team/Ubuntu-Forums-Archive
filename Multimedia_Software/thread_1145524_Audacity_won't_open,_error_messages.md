---
title: "Audacity won't open, error messages"
date: 2009-05-01
forum: Multimedia Software
---

### Post by Mariane on 2009-05-01
Hi, 

I've been reading about audacity on this forum and gathered I should install alsa-oss and audiooss to 
solve audacity playback problems. I did it. I tried 
different settings in edit/prefs/audio. 

But now when I try to launch audacity (by typing 
"audacity") nothing opens but I get a lot of error 
messages scrolling by: 

Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1034
Expression 'AlsaOpen( hostApi, parameters, streamDir, &pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1066

**** alsa_pcm: xrun of at least 0.011 msecs

This last one reappears a few times, then I get 
the first one again. And it does not end until 
I do control C. 

I tried: 
sudo apt-get remove --purge audacity
sudo apt-get install audacity

I also tried rebooting. 

Nothing changes, audacity won't launch again. 

The sound output still works with for example 
"say hello". 

Please help

Mariane

---

### Post by BslBryan on 2009-05-01
I think I have an understanding of your problem, but I'm a little unclear because you say that the "sound output still works."  

Am I to assume that you mean that you can still hear out of your speakers, but Audacity is just screwing up?

---

### Post by Mariane on 2009-05-01
Yes. I test with typing "say hello" and this works. 

When I open the the same audio file with noatun 
I can hear it (but not edit it, of course, this is 
why I need audacity). 

Since I posted this I fiddled a bit, and audacity 
now launches itself but says "Error while opening 
sound device. Please check the output device 
settings and the project sample rate." 

I still get the error messages scrolling up the 
terminal window. 

What is the "project sample rate"? And how do I 
check it?  

The programs alsa-oss and audiooss seem to have 
added possibilities to the list that appears when 
I do edit - preferences - audio, but none of them 
work. 

Mariane

---

### Post by Mariane on 2009-05-04
SOLVED. 

Ref: [http://ubuntuforums.org/showthread.php?p=7212906&posted=1#post7212906](http://ubuntuforums.org/showthread.php?p=7212906&posted=1#post7212906)

Solved by going to Gnome desktop, System, language 
and setting the default to English. It had mysteriously 
turned to French during a dist-upgrade. 

Don't ask me how this is related to audacity... 

Mariane

---

