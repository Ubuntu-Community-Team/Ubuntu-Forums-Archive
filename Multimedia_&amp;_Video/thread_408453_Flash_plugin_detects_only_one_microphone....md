---
title: "Flash plugin detects only one microphone..."
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by KnuX on 2007-04-13
Hi all,

I'm on Ubuntu Feisty 7.04 and I want to use my Webcam microphone for Flash applications.

I'm using a HP 510 notebook, with Intel chipsets.

Here is my configuration :
> $ cat /proc/asound/cards
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with unknown codec at 0xd0781000, irq 17
 1 [U0x46d0x8d9    ]: USB-Audio - USB Device 0x46d:0x8d9
                      USB Device 0x46d:0x8d9 at usb-0000:00:1d.0-1, full speed
> 
$ cat /proc/asound/
card0/       card1/       cards        devices      hwdep        ICH6/        modules      oss/         pcm          seq/         timers       U0x46d0x8d9/ version      
knux@knux-laptop:~$ cat /proc/asound/
card0/       card1/       cards        devices      hwdep        ICH6/        modules      oss/         pcm          seq/         timers       U0x46d0x8d9/ version      
> 
$ cat /proc/asound/devices 
  2:        : timer
  3:        : sequencer
  4: [ 0- 4]: digital audio playback
  5: [ 0- 3]: digital audio capture
  6: [ 0- 2]: digital audio capture
  7: [ 0- 1]: digital audio capture
  8: [ 0- 0]: digital audio playback
  9: [ 0- 0]: digital audio capture
 10: [ 0]   : control
 11: [ 1- 0]: digital audio capture
 12: [ 1]   : control

> $ aplay -l
**** Liste des PLAYBACK périphériques ****
carte  0: ICH6 [Intel ICH6], périphérique 0 : Intel ICH [Intel ICH6]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: ICH6 [Intel ICH6], périphérique 4 : Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
> 
$ arecord -l
**** Liste des CAPTURE périphériques ****
carte  0: ICH6 [Intel ICH6], périphérique 0 : Intel ICH [Intel ICH6]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: ICH6 [Intel ICH6], périphérique 1 : Intel ICH - MIC ADC [Intel ICH6 - MIC ADC]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: ICH6 [Intel ICH6], périphérique 2 : Intel ICH - MIC2 ADC [Intel ICH6 - MIC2 ADC]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: ICH6 [Intel ICH6], périphérique 3 : Intel ICH - ADC2 [Intel ICH6 - ADC2]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  1: U0x46d0x8d9 [USB Device 0x46d:0x8d9], périphérique 0 : USB Audio [USB Audio]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0

Flash only detects a  "Linux microphone" attached to the Microphone on my notebook (where I have to plug a jack).

I'm looking for make Flash using my USB Audio capture device... I think I should make it as the default device for capture but the configuration with Gnome assistant doesn't help.

Of course, the gnome sound recorder uses the microphone of my USB Webcam... So it works.

Can you help me please ? How can I configure my USB Audio device to be uses by default for captures ?

Thanks you in advance ;)

---

### Post by argotnaut on 2007-06-20
[bump]

I'd like to know too! I have a Logitech QuickCam Communicate STX. Built-in USB microphone works with Ekiga, but nowhere else. I've checked all mixer settings, changed defaults in the Multimedia control panel; nothing works, BUT it must be detecting the mic since it works in Ekiga.

Anyone know how to fix this? Or does anyone have a webcam with a built-in mic that just worked automatically everywhere?

---

### Post by BrewBelly on 2007-07-29
I have a Logitech Quickcam for notebooks pro and feisty.

So far, only ekiga can make and image from it and use the mic.  I need to use the webcam on FLASH websites and they don't work at all.

---

### Post by theycallmeguy on 2007-09-06
I myself am looking for a answer to this question. I am wanting to post on Youtube using the quick capture on the flash player. I have a Logitech usb Mic and i can record via Audacity. Yet when i go to Youtube and go to the audio setting in the quick capture. "Linux Microphone" is all it says. and nothing records. I am really interested in making this my broadcast box yet I cant change the audio setting in flash quick capture.

Can someone please help a noobie  :)
Thanks to all

---

### Post by argotnaut on 2007-09-09
I'm beginning to think there's nothing we can do at our end -- I think this is a problem that Adobe is going to have to fix.

---

### Post by sypher7 on 2008-01-08
Hey guys,

I had the same problem here, and after thinking about it I'm pretty sure I know what the problem is. The flash plugin isn't generating a full list of microphones from all mixers, just the default one. That means a workaround is possible if you want to go through the trouble of reordering your sound devices.

For me, something like this worked:

/etc/modprobe.d/alsa-base:
```
# Manual ordering allows USB mic for flash plugin
options snd-usb-audio index=0
options snd_intel8x0 index=1
options saa7134-alsa index=2
# Prevent abnormal drivers from grabbing index 0
...
```

Basically I took snd-usb-audio out of the list of devices that can't grab /dev/dsp (i.e. the options by default only allow it to grab /dev/dsp1 or 2 or 3, etc.). I then forced the ordering of my sound cards:

/dev/dsp = USB (webcam)
/dev/dsp1 = internal sound card
/dev/dsp2 = video capture card

Now Flash correctly detects my microphone but doesn't play back audio for the same reason that the microphone didn't work in the first place... So in short, it looks like the flash plugin isn't smart enough to look beyond the first audio device yet (for either sound playback *OR* microphone). I do believe they know about this and are hoping to get it fixed. Guess we'll have to wait it out and see when that happens...

---

