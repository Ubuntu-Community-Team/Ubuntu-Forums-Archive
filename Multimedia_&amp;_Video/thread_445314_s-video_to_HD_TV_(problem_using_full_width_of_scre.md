---
title: "s-video to HD TV (problem using full width of screen)"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by aleska on 2007-05-15
My wife just got a new pc (running ubuntu of course), and given that her old pc (also running ubuntu) has a pretty recent (<2 year old) nvidia graphics card with s-video out, I thought it would be neat to use it with our big screen HD TV screen.  I have the nvidia-glx driver installed on it, so I thought this should work out ok.
Anyway, I attached it via s-video to the HDTV, I booted up and voila, it works, and its not bad I might add!  I get a decent picture.  

However, the max resolution 1024 x 768.  Neither nvidia settings nor display settings in the Preferences menu allow me to go beyond this.  So, basically the sides of the HD TV are cut off with nonusable blackspace.  I don't get any options to change the screen resolution other than your typical boxy shapes 1024 X 768, 800 x 600, etc.  

Now. actually, I find that text is easier to read when I change the resolution to 800 x 600 (so maybe lower resolution is the way to go); but still, I have the problem with the cutoff blackspace on sides of the screen.  

What should I do here to enable the use of the full HD screen?  Do I just edit something in xorg.conf?  If so, what dimensions should I hard code in there?  Any advice greatly appreciated.  TIA

---

### Post by NT4usB on 2007-05-15
You'll need to find out what your TV supports then add it to xorg.
Or, you could try:```
sudo dpkg-reconfigure xserver-xorg
```
might detect it... might also trash you xorg completely so back it up first.

---

### Post by aleska on 2007-05-15
I'm not sure what you mean by what the tv supports.  It's a Sony KDF-50E2000.  Here are the specs as shown on CNET.  [http://reviews.cnet.com/Sony_KDF_50E2000/4507-6482_7-31789644.html?tag=sub](http://reviews.cnet.com/Sony_KDF_50E2000/4507-6482_7-31789644.html?tag=sub)
What details do I need to know to edit xorg.conf properly?

Some of the details I see include:
Product type:  Rear projection TV
Technology:   Projection LCD
Diagonal size: 50 in
Image aspect ratio: 16:9
HDTV compatible: Yes
Series: GRAND WEGA
Digital TV Type:  HDTV 

Resolution:  1280 x 720
Comb filter:  3D-Y/C digital
Viewing angle:  130 degrees
Viewing angle (vertical): 60 degrees
Supported DTV Resolutions: 480i, 480p, 720p, 1080i 

Input/Output connections: 
2 x HDMI (19 pin HDMI Type A) - Rear, 4 x Audio line-in (RCA phono x 2) - Rear, 2 x Component video input (RCA phono x 3) - Rear, 1 x Component video input (RCA phono x 3) - Side, 1 x S-Video input (4 pin mini-DIN) - Rear, 2 x Composite video input (RCA phono) - Rear, 1 x Composite video input (RCA phono) - Side, 1 x Audio line-in (RCA phono x 2) - Side, 1 x Digital audio output (optical) (TOS Link) - Rear, 1 x Headphones (Mini-phone stereo 3.5 mm) - Front, 1 x Fixed/variable audio output - Rear, 2 x RF input (F connector) - Rear 

Operational power consumption: 200 Watt
Operational power consumption (standby): 0.8 Watt 

Are any of those details relevant for what I need to edit/include in xorg.conf?

Thanks in advance!

---

### Post by disturbed1 on 2007-05-15
You won't get much output from using S-Video. I've found that 720x480 was the best solution for me. If you start the nvidia control panel (nvidia-settings I believe) you can adjust overscan.

Use DVI or a DVI to HDMI connection for HDTV resolutions.

---

### Post by aleska on 2007-05-16
So, assuming I go out and buy a dvi to hdmi cable, would I still have to edit something in xorg.conf settings?  If so, what would I need to do?  :confused:

---

### Post by NT4usB on 2007-05-16
> **aleska said:**
> I'm not sure what you mean by what the tv supports....
What details do I need to know to edit xorg.conf properly?

Resolution:  1280 x 720

Supported DTV Resolutions: 480i, 480p, 720p, 1080i 


Thanks in advance!

Once you get your component cable, your 'Screen' section would look something like this:```

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option         "TVOutFormat" "Component" #or HDMI or, ...
    Option         "TVStandard" "HD480i" # or HD480p, HD720p, HD1080i, etc
    Option         "ConnectedMonitor" "Monitor[0]"
    SubSection     "Display"
        Depth       24
        Modes      "1280 x 720_60"#assuming you're 60Hz
    EndSubSection
EndSection
```

---

