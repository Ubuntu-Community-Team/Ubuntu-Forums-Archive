---
title: "USB audio (Griffin iMic) install difficulties"
date: 2008-05-06
forum: Multimedia Software
---

### Post by fogelfink on 2008-05-06
Need help with USB soundcard (Griffin iMic)

I am completely new to Ubuntu/linux and am still in the process of setting up my new laptop (Acer 5720Z).  I had difficulties to get the sound working after installing Ubuntu 8.04 – issues I have fixed using various posts on this forum. (Though I am not really sure why and what I did, since  I am really new to the whole command line thing.)  Internal speakers and headphone socket seem to work fine now, but I still can't use my iMic USB soundcard.

I am using [B]Advanced Linux Sound Architecture Driver Version 1.0.16
[/B]
I checked if the computer recognises my sound cards using:
 ```
 cat /proc/asound/cards
```

The output I am getting is:   
 ```
0 [Intel          ]: HDA-Intel - HDA Intel

                      HDA Intel at 0x98400000 irq 23

 1 [system         ]: USB-Audio - iMic USB audio system

                      Griffin Technology, Inc iMic USB audio system at usb-0000:00:1d.2-1, full speed
```


So to me it seems that my computer recognises that I have those soundcards installed.  I simply don't know how to proceed from here in order to channel the sound of mediaplayers through iMic (or for that matter any sound). 
 
When I go to System>Preferences>Audio and try to switch any settings tab from ALSA to USB soundcard and then press try, I get the following error message:  > audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Since I am new to Ubuntu, I am simply a bit careful just trying to follow command line instructions I find for similar problems (I.e. with other soundcards).  I found the following article on the ALSA wiki about hot swapping USB audio devices, but am not sure if that would help me: [HTML]http://alsa.opensrc.org/index.php/Hotplugging_USB_audio_devices_(Howto)[/HTML]
 I looked into my settings in the alsamixer, but see no option that gives me output on the iMic. I installed the default soundcard package, so now I have a System>Preferences>DefaultSounsCard panel, which gives me the following options to choose from:  Intel, system and PulseAudio.  I have no clue which to choose and why the USB soundcard is not in the list.

Since the solution to my problem might be really simple, I don't want to rush into changing any more system configurations of which I have no idea what they do.

Thanks for your help

---

### Post by fogelfink on 2008-05-10
anyone???
 - I still haven't solved this.  I have been trying to use Ubuntu for a week now and am nowhere with anything.  Can't play audio the way I want.  DVDs won't play (tried following guides on this forum for two days now) and I had to give up on trying to mount an external usb drive after six hours.  This is the forth time over the last ten years that I am trying to use linux and it remains a nightmare for the non-expert to do so.
please help

---

### Post by fogelfink on 2008-05-11
What solved my problem partly is the following thread:
[http://seehuhn.de/pages/alsa](http://seehuhn.de/pages/alsa)

What I still have to figure out is hot to make the iMic hot swappable, so when I unplug it the sound switches back to the internal speakers.

If anyone knows of a way to do that your help is much appreciated!

---

### Post by leisuresuitgreg on 2009-06-04
Hey Fogelfink

I'm having similar issues trying to get my iMic running on my new copy of Jaunty (with Ubuntustudio add-ins, but not the real-time kernal, but that's another story). Did you manage to get any of this sorted?

HP 6735s
AMD Turion X2 RM-72
4.0 GB RAM

Cheers

Greg

---

