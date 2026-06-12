---
title: "[SOLVED] Logitech AK5370 USB microphone"
date: 2007-10-13
forum: Multimedia &amp; Video
---

### Post by onlineapps on 2007-10-13
Hey all,
I'm having trouble with my new Logitech AK5370 USB microphone.  It shows up in lsusb, and Skype can even see it, but I can't make a call with it.  Same with mhwaveedit.  And yes, I set the volume to max in KMix.

Kubuntu Feisty

---

### Post by nossr50 on 2007-10-16
I have the same issue

---

### Post by JaYp146 on 2008-02-11
Bumping this thread, I'm having the same problem on kubuntu.  Any help is greatly appreciated...

---

### Post by onlineapps on 2008-02-11
Some how, when I cleanly reinstalled Gutsy, it worked out of the box. Try that.

---

### Post by KDE-fan on 2008-02-11
I just bought one myself!

This is what I did:

**1. Fixed** all mixer input settings. This includes un-muting the microphone and increasing the capture volume. Here are my settings from just before I plugged in the microphone: [http://img142.imageshack.us/img142/2936/kmixskypesettingsud3.jpg](http://img142.imageshack.us/img142/2936/kmixskypesettingsud3.jpg)

**2. Created** a file called "asound.conf" in /etc/ folder that includes the following text:
> 
 pcm.lydkort&mic {
         type asym
         playback.pcm {
                 type plug
                 slave.pcm "hw:0,0"
         }
         capture.pcm {
                 type plug
                 slave.pcm "hw:1,0"
         } 
 } I have no idea why this helped, or if it actually is necessary at all...

**3. Selected** correct input and output device in skype. 
> Sound In: AK5370 (hw;default,0)
Sound Out: VIA 8237 (hw, V8237,0)
Ringing: VIA 8237 (hw, V8237,0)

EDIT: I would like to add that KMix apparently has trouble saving the necessary settings: [http://ubuntuforums.org/showthread.php?t=692954](http://ubuntuforums.org/showthread.php?t=692954)

---

### Post by i8bugs on 2008-02-21
Mine is not even being detected.  What can I do so it will be detected?
dm

---

### Post by i8bugs on 2008-02-21
I'm getting error messages in Audacity trying to play back voice from my usb mic.
It says:
Error while opening sound device. Please check the output device settings and the project sample rate.

I lowered the sample rate...nothing.  Ran Audacity through terminal and recorded the results.  Does this mean anything that I can fix?

> i8bugs@i8bugs-desktop:~$ aoss audacity
JACK tmpdir identified as [/dev/shm]
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
Expression 'tempDevHandle = open( deviceInfo->name, flags )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 690

Expression 'parameters->channelCount <= maxChans' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924
Expression 'ValidateParameters( outputParameters, hostApi, StreamDirection_Out )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1142

Expression '*odev = open( odevName, flags )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 821
Expression 'OpenDevices( idevName, odevName, &idev, &odev )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 864
Expression 'PaOssStream_Initialize( stream, inputParameters, outputParameters, streamCallback, userData, streamFlags, ossHostApi )' failed in 'src/hostapi/oss/pa_unix_oss.c', line: 1230

Some insight to this would be great...
i8bugs

---

### Post by jcsteele on 2008-03-16
The device is working properly for me in the current development version of Hardy (post-Alpha 6) ... This is an improvement over Gutsy where I could not get anything to function with it.

$ lsusb
Bus 002 Device 002: ID 0556:0001 Asahi Kasei Microsystems Co., Ltd AK5370 I/F A/D Converter

Using audacity, make sure you have selected the correct recording device(AK5370) and its very important to make sure the recording channels is set to 1 (mono) ... as seen from the /var/log/message output when plugging the mic in, it does not support stereo (2 channel) recording.

Mar 16 22:28:05 neuron pulseaudio[5932]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.

After all that, simply make sure your mic is not muted, and audio recording from it is toggled to 'on' - then audacity will record from the microphone with very good quality...I am impressed, though limited to 1 channel might affect you tremendously ... I use the microphone for podcasting and basic voice operations so 2 channel recording is not a necessity for me.

---

### Post by z0mbie on 2008-03-30
> **jcsteele said:**
> Using audacity, make sure you have selected the correct recording device(AK5370) and its very important to make sure the recording channels is set to 1 (mono) ... as seen from the /var/log/message output when plugging the mic in, it does not support stereo (2 channel) recording.


I can't believe all this time I was tinkering with it, it was easy as that. Thank you very much jcsteele.

---

