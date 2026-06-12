---
title: "Zoom H2 as USB Mic fails on Hardy"
date: 2008-07-29
forum: Multimedia Software
---

### Post by hipnerd on 2008-07-29
I recently acquired a Zoom H2 portable recorder. It can also double as a USB microphone. My research indicated that it would work with Ubuntu, but I've had zero luck getting it to go.

When I set the Sound Capture device to USB Audio and click "test," I get:

[INDENT]gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for recording.[/INDENT]

The unit works perfectly on my wife's Windows box. (dammit)

I also tried using Audacity. It locks up when I chose the mic. 

**ALSA:H2:USB Audio (hw 1,0)**

In the course of trying to get this to work, I followed a tutorial to get PulseAudio configured. It made no appreciable difference, but I figured I should mention it because I'm sure that it changed things somehow. I have since changed my settings back to "autodetect."

Does anyone have any help for me here?

---

### Post by foresto on 2008-08-15
I just tried my Zoom H2 as a USB mic, and it seemed to work fine.  I inserted batteries, powered it up, entered the menu, set it to USB microphone mode, plugged in the USB cable, and saw these lines in /var/log/messages:

Aug 15 20:36:31 ocelot kernel: [119408.189920] usb 7-2.1: new full speed USB device using ehci_hcd and address 9
Aug 15 20:36:31 ocelot kernel: [119408.286922] usb 7-2.1: configuration #1 chosen from 1 choice
Aug 15 20:36:31 ocelot kernel: [119408.449405] usbcore: registered new interface driver snd-usb-audio

/dev/dsp2 was created.  (I already had /dev/dsp and dev/dsp1.)

I then used sound-recorder to record a 10 second WAV file, using this command line:

sound-recorder -A /dev/dsp2 -c 2 -s 44100 -b 16 -f wav -S 00:10 foo.wav

The new file played back as expected.  Did you remember to put the H2 in USB microphone mode?  Could your problem be your choice of recording software and/or device name?

I'm using XUbuntu Hardy 32 bit.

---

