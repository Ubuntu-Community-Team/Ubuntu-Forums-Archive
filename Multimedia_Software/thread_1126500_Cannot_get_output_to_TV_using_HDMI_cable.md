---
title: "Cannot get output to TV using HDMI cable"
date: 2009-04-15
forum: Multimedia Software
---

### Post by EvilBear on 2009-04-15
I need help getting my shows to output to a TV using a HDMI cable. I have never done this before, don't know where to start. I am using Ubuntu and the default totem player w/ working codecs. All movies play fine on my laptop. Help please :)

Looked for solutions in google and was confused. Will need a little handholding, but i can enter stuff in my CLI as pompted.
Adam

---

### Post by wolfen69 on 2009-04-15
what's your video card? you will probably need the drivers for it.

---

### Post by jowilkin on 2009-04-15
I had to install the latest drivers to get HDMI working on my computer.  I have Nvidia so the driver I used was from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).  

I can't speak for ATI or Intel cards.

Getting sound to work through HDMI is a whole nother issue... It took the latest ALSA and some tweaking to get it working for me.  I followed this thread to get the latest alsa: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

Does your computer have an HDMI port or are you using a DVI to HDMI converter?  If you are using the converter then you won't be able to get sound to work, but if you have an HDMI port on the computer there is a chance you can get sound working (with some effort).

---

### Post by EvilBear on 2009-04-15
My computer has an HDMI port. He showed me a command xrandr --auto which got it to appear on a monitor at school through a different port, the one with all the pin connections (no idea what it's called, not labeled :) )
so i will try that command when i get home. But my Totem freezes once in a while. Maybe new drivers will fix that. Also need to see if audio works when i get back home. I'll repost if i still have trouble. Thank

---

### Post by EvilBear on 2009-04-15
> **wolfen69 said:**
> what's your video card? you will probably need the drivers for it.

I have no idea. It's a dell. How do i find my video card?

---

### Post by gdbutcher on 2009-04-15
To Identify your graphics card, go to Applications menu > Accessories > terminal.

Copy and paste the following lines into the terminal:

```
 gedit /etc/X11/xorg.conf 
```

This will open a file with your display settings in, go about a 3rd of the way down the page to where it lists your "Devices" you should see something like this telling you your graphics card:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M G"
EndSection

So my graphics card is NVIDIA GeForce 8400M G. tell us what you says and we can help you from there.

---

