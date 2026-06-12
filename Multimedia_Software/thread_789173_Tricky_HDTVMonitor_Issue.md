---
title: "Tricky HDTV/Monitor Issue"
date: 2008-05-10
forum: Multimedia Software
---

### Post by gizzardgulpe on 2008-05-10
So far, everything except my TV has worked, or been easily fixed. However, getting my display to work properly has been nothing short of a nightmare.

So, I'm on an AMD 64 5000+ with 2 Gigs of RAM and the motherboard has a built in NVIDIA GeForce 6150se graphics card. I'm using a 32" Vizio HDTV with a native resolution of 1366x768.

After doing everything about 10 times on _[this page]("https://help.ubuntu.com/community/FixVideoResolutionHowto")_ I spoke to a friend who had me download the NVIDIA settings package via Synaptic. Then I ran;

```
sudo nvidia-settings
```

which almost fixed everything. Almost. The problem is, I am unable to select the native resolution, so I'm forced to stretch 1280 pixels of data across 1366 actual LCD pixels which is distorting everything on the screen. It's not a huge deal, but no matter what I do or how I fiddle with the xorg.conf file, I can't seem to get it to allow me to select the resolution of choice.

Any help would be wildly appreciated.

Edit: Windows Vista allowed me to use the 1366x768 resolution, so I imagine it's not impossible. :p

---

### Post by feenicks on 2008-06-17
I'm having the same issue with the Vizio VX20L 20" lcd.  Native rez is the same as yours.  I emailed Vizio tech support to see if they can give me a modeline.  Anyone been successful here?

---

### Post by gizzardgulpe on 2008-06-17
I would be very interested to find out if there is a way to get to the native resolution. At the moment, I have Ubuntu set to 1280x768, and Vista set to 1360x768 (there seems to be a glitch which is shifting half of the image off the screen if I use the native resolution with Vista). I used the television settings to shrink the size, so I'm not using the whole screen right now, but at least it isn't distorted and stretched.

---

### Post by anindya_m on 2008-06-17
Do you have the hardware accelerated nvidia driver installed? I have a 32" Sony Bravia with the same resolution as yours, and sometimes use nvidia-setings to configure the TV display on the fly (no entry in xorg.conf). The reported resolution is 1360x768 (I think the TV doesn't allow use of the 6 pixels, although you cannot tell this from the display). The picture is perfect and not stretched. I use a VGA cable.

---

### Post by gizzardgulpe on 2008-06-18
I have the nvidia-settings package installed. I know there are others, but understanding them and getting them to work is something I've left only for step by step instructions. :p

With the nvidia-settings menu I can choose from a wide array of display resolutions, but it skips the 1300 series completely, going from 1280x768, to 1400x900, to... I think 1600x1200.

---

### Post by anindya_m on 2008-06-18
Can you post the following files:

/etc/X11/xorg.conf
/var/log/Xorg.0.log

---

### Post by gizzardgulpe on 2008-06-18
I had no xorg.0.log file, so I attached the closest one, and another that might be of interest.

---

### Post by anindya_m on 2008-06-20
I can't see anything wrong. What happens if you comment out the tv resolution line (with 1280x768 ) from xorg.conf?

---

### Post by aeiah on 2008-06-20
the 1360 thing is because some cards have to display in multiples of 16, so they cant do 1366. this is normal and since its only 3 pixels each side you shouldnt be too worried about it. are you using hdmi, dvi or vga? have you tried adding an ignore EDID tag to your xorg.conf? 

perhaps you can try going into windows, downloading powerstrip, and getting it to copy the settings you are using to the clipboard. paste it into notepad and save it. you'll notice that amongst other information it'll give you a linux modeline for the resolution it is using. you can then apply that to your xorg.conf. its worth a try. worked for me (although i cant get [1:1 pixel mapping](pixelmapping.wikispaces.com) on my hdtv like you apparently can unfortunatley)

---

### Post by anindya_m on 2008-06-22
Actually it's multiples of 8 (as in 8 pixels = 1 character clock). Nvidia can do 1366 over DVI, but not VGA (this is true for my 6800). The Powerstrip suggestion is a good one. As suggested above, you can try disabling EDID (which seems to be lying in your case) and try manually putting a modeline.

---

