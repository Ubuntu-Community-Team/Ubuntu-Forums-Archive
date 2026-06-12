---
title: "Nvidia wont detect LCD TV resolutions 10.04"
date: 2010-05-11
forum: Multimedia Software
---

### Post by azizzle on 2010-05-11
I cannot seem to get the correct resolution for my TV. I have an Nvidia geforce 9500gt with a 19in monitor and a 42in lcd tv hooked up to it. In nvidia settings I can get a super wide range of resolutions for my monitor, but the highest I can choose for my TV is 680x400. I tried to manually edit the xorg.conf but if I choose 1280x720 the screen on my TV just goes black. 

Are there any alternatives to using nvidia or any ways I can get the settings to detect to correct resolutions?

---

### Post by shazbut on 2010-05-11
Maybe check your TV manual to see what modes are supported.  My 46" samsung series 6 needed something called reduced blanking to work properly at 1080p through the analogue vga port.  I had to set it manually using cvt/xrandr commands.
I decided it was easier just to use a DVI-HDMI cable and let the TV and the video card sort it out automagically between themselves.

---

### Post by Stephen90 on 2010-05-11
What type of cables are you using to connect your computer to your television?  Also, what is the native resolution on your television? 

I currently use my 17" laptop with my 32 inch TV as a monitor.  Did you already go to Nvidia X Server Settings -> X Server Display Configuration -> click on your TV and press configure?

---

### Post by azizzle on 2010-05-11
> **shazbut said:**
> Maybe check your TV manual to see what modes are supported.  My 46" samsung series 6 needed something called reduced blanking to work properly at 1080p through the analogue vga port.  I had to set it manually using cvt/xrandr commands.
I decided it was easier just to use a DVI-HDMI cable and let the TV and the video card sort it out automagically between themselves.
I don't think it has anything to do with any "modes". It works perfectly fine in windows :(

> **Stephen90 said:**
> What type of cables are you using to connect your computer to your television?  Also, what is the native resolution on your television? 

I currently use my 17" laptop with my 32 inch TV as a monitor.  Did you already go to Nvidia X Server Settings -> X Server Display Configuration -> click on your TV and press configure?

at first it was setup with just an hdmi cable. when i couldn't get the native resolution (1024x768) i tried to use a dvi-hdmi cable. still no luck. It doesn't even recognize my tv as a tv. 
it just says DFP in the settings.

---

### Post by azizzle on 2010-05-11
bump?

---

### Post by ratcheer on 2010-05-11
Are you trying to use it as a TV or as a monitor? I am using a Magnavox LCD as a monitor with nVidia 195.36.15 and it automatically chose the correct resolution (1440x900) and refresh rate. Is your monitor specifically recognized by the driver?

Tim

---

### Post by azizzle on 2010-05-11
im trying to use it as a tv. it is not being recognized by the driver.

here is the screen section from my xorg:



Section "Screen"

# Removed Option "metamodes" "CRT: 1440x900 +0+0, DFP: 640x480 +1440+0"
# Removed Option "metamodes" "CRT: 1440x900 +0+0, DFP: 1280x720_60 +1440+0"
# Removed Option "metamodes" "CRT: 1440x900 +0+0, DFP: 1280x720 +1440+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1440x900 +0+0, DFP: 640x480 +1440+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP: 640x400 +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by ratcheer on 2010-05-11
Sorry, I don't know anything about using it as a TV.

Tim

---

### Post by StephanG on 2010-05-19
Try using the DVI-D port.  Most monitors now come with a VGA -> DVI-D converter.  The DVI port, it seems, is just much better at detecting a monitor's capabilities.

---

