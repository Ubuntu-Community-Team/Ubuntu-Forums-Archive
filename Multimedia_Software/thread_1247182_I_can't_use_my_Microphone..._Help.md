---
title: "I can't use my Microphone... Help"
date: 2009-08-22
forum: Multimedia Software
---

### Post by Dotan on 2009-08-22
Hi,

I've been trying to use Skype since I bought this Laptop. No success so far.

It seems that my microphone is not working, or is it the driver? I have no clue.

if you know anything about sound configurations please help.

Thanks,
Dotan.

------------------------------

GigaByte Laptop,
Ubuntu 9.04
Kernel - 2.6.30.1-candela.

---

### Post by ajgreeny on 2009-08-22
Just with skype or system-wide with all applications?  Also what kind of mic is it, usb or plugged into the souncard?  Finally make sure you have checked all the channels available in the Volume Control > Preferences;  maybe something is muted, or set too low.

---

### Post by Stochastic on 2009-08-22
Moved to Multimedia & Video.

---

### Post by Elviswind on 2009-08-22
Make sure the microphone channel is turned on or set to record in the "capture" section of your mixer GUI.  I think you'll want to have the microphone boost set to the highest level in the "capture" section as well.  Also select microphone as in input source.

You can test your microphone by unmuting and turning up the volume of microphone in the "playback" section.  If you speak into your microphone, you should hear your voice come out of your speakers.

I actually find alsamixer run from the terminal to be more precise way to adjust sound levels since it provides better feedback than the mixer GUI that comes with Xubuntu.

---

### Post by Dotan on 2009-08-23
I looked at the ALSA HDA Alsa mixer and I tuned my internal mic to the max.
I muted the mic boost
The capture is now set to internal mic
and the recording volume is at it's max.

I have a built-in mic that I want to use. that is way I chose internal-mic over "mic".

I added a screenshot of my desktop.



I can't understand what are those options that skype gives me:

[B]Default device (default)
HDA intel (hw:intel,0)
HDA intel (plughw:intel,0)
HDA intel (hw:intel,6)
HDA intel (plughw:intel,6)
hdmi
headset
pulse[/B]

now, from what tested the only time I could make a test call (an option skype has) is if I choose in all the sound devices options (sound in, sound out, ringing) "pulse".

so my question is - what is pulse? what are the rest of the options mean? and most important - how can I use my mic???

when I do a test call when "pulse" is chosen the mic does not record...

---

