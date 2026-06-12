---
title: "Trouble changing webcam settings"
date: 2009-01-23
forum: Multimedia Software
---

### Post by justin75 on 2009-01-23
I have an old (90s) intel create and share webcam- just plug it in and it works- thank you ubuntu hardy!

Using Kopete I can alter the brightness, contrast, etc settings perfectly, but it doesn't save the settings.

I'd like to use this as a weather-cam, ie grab a snapshot every minute or two and save to the /www folder. from the command line, camgrab gets the picture, but it's all blue and pink, ie wrong exposure settings.

Dov4l seems like the solution, but it doesn't acutally change the settings.

this is the original 'get settings' output:
[INDENT]
[SIZE="1"]me@home:~$ dov4l -q
dov4l v0.9, (C) 2003-2006 by [email]folkert@vanheusden.com[/email]

Canonical name for this interface: Intel Create and Share
Type of interface:
 Can capture to memory

Number of radio/tv channels if appropriate: 1
Number of audio devices if appropriate: 0
Maximum capture width in pixels: 640
Maximum capture height in pixels: 480
Minimum capture width in pixels: 160
Minimum capture height in pixels: 120

Image size (x,y): 352, 288

The channel number: 0
 The input name: SPCA501
 Number of tuners for this input: 0
 The input is a camera
 The norm for this channel: 2052
Brightness: 0
Hue: 0
Colour: 20480
Contrast: 43521
Whiteness: 0
Depth: 24
Palette: RGB888 packed into 24bit words.[/SIZE]
[/INDENT]

then I'll run (sudo) dov4l -b 50
and then run dov4l -q again and receive the same output as above, and of course the images are still unusable.

how do i alter and save the settings? preferrably from the command line :D

thanks

---

### Post by justin75 on 2009-01-23
it seems the answer was already here
[http://ubuntuforums.org/showpost.php?p=4183572&postcount=3](http://ubuntuforums.org/showpost.php?p=4183572&postcount=3)

thanks UBForums!

lesson of the moment, Google is not everything, use the site search!
doh! :o

---

