---
title: "Single frame grabber"
date: 2008-03-14
forum: Multimedia Production
---

### Post by Steven_B on 2008-03-14
I need a simple tool to grab a frame from my usb capture device and save it as an image.  A simple command-line program would be best.  
Nearly all of the tools I've found have issues or save a garbled image.  Perhaps I've got some settings wrong, but I don't know how to go about fixing them.  tvtime works fine, so it isn't a driver problem.
Thanks!

---

### Post by nalmeth on 2008-03-14
What kind of capture device? Is it a webcam?

---

### Post by Steven_B on 2008-03-14
It's a composite/s-video to USB widget.
[http://www.amazon.com/Eforcity-USB-Video-Capture-Software/dp/B000E8FPZS]("http://www.amazon.com/Eforcity-USB-Video-Capture-Software/dp/B000E8FPZS")
Attached is an example of the mess I'm getting.

---

### Post by nalmeth on 2008-03-14
I see. We'll considering there is an image being grabbed at all there must be some partial support for the device.

Can you point out what you have tried already so we can narrow the scope of the problem?

---

### Post by Steven_B on 2008-03-14
I think I've figured out what's wrong.
The device has three channels, and only composite is actually receiving any input.  Since this isn't the default, the programs read from the "tv input", which isn't really receiving a signal.
Now I need to figure out how to set the channel...
I've used:
ffmpeg
vgrabbj
gqcam
lavrec
camorama (said it was unable to connect to /dev/video0)
camstream (segfaults)


```
steven@steven-laptop:~$ dov4l -q
dov4l v0.9, (C) 2003-2006 by folkert@vanheusden.com

Canonical name for this interface: MSI VOX USB 2.0
Type of interface:
 Can capture to memory
 Has a tuner of some form

Number of radio/tv channels if appropriate: 3
Number of audio devices if appropriate: 0
Maximum capture width in pixels: 640
Maximum capture height in pixels: 480
Minimum capture width in pixels: 48
Minimum capture height in pixels: 32

Image size (x,y): 640, 480

The channel number: 0
 The input name: Television
 Number of tuners for this input: 1
 Channel has tuners
 The input is a TV input
 The norm for this channel: 0
  Number of the tuner: 0
  Canonical name for this tuner: Tuner
  Lowest tunable frequency: 0
  Highest tunable frequency: 0
  Current frequency: 567MHz
  Flags describing the tuner:
   PAL tuning is supported
   NTSC tuning is supported
   SECAM tuning is supported
   Frequency is in a higher range (tuning frequencies are in 1/16th MHz)
  The video signal mode if relevant:
  Signal strength if known: 0
The channel number: 1
 The input name: Composite1
 Number of tuners for this input: 0
 The input is a camera
 The norm for this channel: 0
The channel number: 2
 The input name: S-Video
 Number of tuners for this input: 0
 The input is a camera
 The norm for this channel: 0
Brightness: 32896
Hue: 32896
Colour: 33026
Contrast: 33026
Whiteness: 0
Depth: 16
Palette: Describe me

```

---

### Post by kc8hr on 2008-03-17
Try xawtv or motv. Both will grab jpegs or ppms.

---

### Post by Steven_B on 2008-03-18
Motv works, but I need to be able to run the capture command from a script.

---

