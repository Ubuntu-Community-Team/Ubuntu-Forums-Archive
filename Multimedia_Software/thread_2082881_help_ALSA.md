---
title: "help ALSA"
date: 2012-11-10
forum: Multimedia Software
---

### Post by b49P23TIvg on 2012-11-10
OS ubuntu 12.10
Works: arecord, aplay, audacity, solfege---these work!
Developer installed: Furthermore, I found source for and can build aplay.

I'm struggling with the ALSA docs as I write an application to visualize sound.  Currently I get the PCM data reading a pipe to  arecord .  On a loaded computer at high data rate my program lags miserably.  I would like to use a memory map directly to libasound.  Failing that I'd like an example command line for arecord --mmap , including commands to set up the mapped file.

I assume that alsa would cyclically write to the map without checking to see if the data were read.  Then I could use the data on my schedule.  The application needs to run with small lag, and also capture high frequencies.  Losing contiguous chunks of data is OK as long as I can also capture most of the data in contiguous chunks.

My code is in post 3 of thread
[http://forums.devshed.com/python-programming-11/pyaudio-buffer-overflow-errors-926301.html](http://forums.devshed.com/python-programming-11/pyaudio-buffer-overflow-errors-926301.html)
After the program is designed I plan to write it in a compiled language.

Also, what, please, are the devices in /dev/snd ?  The sound devices seem different from the ubuntu release of 2010.
controlC0
controlC29
hwC0D0   
pcmC0D0c 
pcmC0D0p 
pcmC0D1p 
seq      
timer    

I appreciate your time and good guidance,
Dave.

PS. I see that pulse audio and jack may be options.  I haven't understood these, either.


update, maybe --mmap doesn't work yet?

$ alsa-utils-1.0.26.6.gf2826/aplay/arecord --mmap /tmp/buffer'
Recording WAVE '/tmp/buffer' : Unsigned 8 bit, Rate 8000 Hz, Mono
arecord: set_params:1192: Access type not available

---

