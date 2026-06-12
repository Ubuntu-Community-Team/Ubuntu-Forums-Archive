---
title: "Zotac NVIDIA Ion graphics/audio problems"
date: 2010-04-09
forum: Mythbuntu
---

### Post by x2aws on 2010-04-09
I take it this board is not that popular..  Doesn't seem to be supported at all in 9.x or 10.x.  Both versions I have installed, Nvidia driver fails right from the get go.  Can't even get HDMI audio to work.  
 
Does anyone know if this unpopular MB will ever be supported in Mythbuntu??

---

### Post by slamhound on 2010-04-09
It's working for me on 10.04 without much tweaking.  To get audio working, I followed some of the recommendations in the link in this post (and some of the other advice on that thread):

[http://ubuntuforums.org/showpost.php?p=8645262&postcount=2](http://ubuntuforums.org/showpost.php?p=8645262&postcount=2)

I think the critical things seemed to be changing the frontend audio settings and unmuting the last three things in alsamixer.  But I'm not entirely sure whether other steps were important, too.

---

### Post by x2aws on 2010-04-09
> **slamhound said:**
> It's working for me on 10.04 without much tweaking. To get audio working, I followed some of the recommendations in the link in this post (and some of the other advice on that thread):
 
[http://ubuntuforums.org/showpost.php?p=8645262&postcount=2](http://ubuntuforums.org/showpost.php?p=8645262&postcount=2)
 
I think the critical things seemed to be changing the frontend audio settings and unmuting the last three things in alsamixer. But I'm not entirely sure whether other steps were important, too.
 
How did you get the graphics to work??  Right out of the box I get a failed to load NVIDIA driver...  Screen just flashes alot, then gives me the option to either load a term, or go in min. graphics.....
 
BTW, in the setup I chose to enable NVIDIA drivers, use component out with a rez of 1080i.

---

### Post by movieman on 2010-04-09
I did a fresh 9.10 install on my new Ionitx board a couple of days ago and the only real issue was having to unmute those audio outputs before HDMI audio would work. Video driver just installed and worked.

---

### Post by x2aws on 2010-04-09
> **movieman said:**
> I did a fresh 9.10 install on my new Ionitx board a couple of days ago and the only real issue was having to unmute those audio outputs before HDMI audio would work. Video driver just installed and worked.
 
what did you use for tv out options???  With the settings right out of the box, I get no where...  Its like that for 2 of my boxes..So I know its not a MB issue..

---

### Post by movieman on 2010-04-09
> **x2aws said:**
> what did you use for tv out options???

I'm using HDMI, but it was working with the VGA output too. I haven't investigated component out.

Edit: looks like I don't have component out, just DVI, HDMI and VGA.

---

### Post by x2aws on 2010-04-09
> **movieman said:**
> I'm using HDMI, but it was working with the VGA output too. I haven't investigated component out.
 
Edit: looks like I don't have component out, just DVI, HDMI and VGA.
 
 
OK, I don't have component either, but HDMI..   Did you not set a TV out option??

---

### Post by movieman on 2010-04-10
> **x2aws said:**
> OK, I don't have component either, but HDMI..   Did you not set a TV out option??

I just left the settings on auto and the driver configured the right video mode for my TV (it's 1360x768, AFAIR).

---

### Post by x2aws on 2010-04-10
> **movieman said:**
> I just left the settings on auto and the driver configured the right video mode for my TV (it's 1360x768, AFAIR).
 
 
ok.. So you're saying that when the step came for the display driver, you changed it from open source to Nvidia, and for the TV out options you didn't touch anything else???  Did you run the disc, and after the live version came up install it from there, or did you install during the opening installation menu???
 
I have tried it BOTH ways and am still not getting anywhere on both of my MB's.  I still get the failed to load Nvidia driver...  Is there any other options I should/should not be checking when I go to do the install???

---

### Post by nickrout on 2010-04-10
This board is very popular for mythtv systems and works very well. 

After this failure to load the nvidia drivers (which i assume you installed), what does the X log say? it's /var/log/Xorg.0.log

---

### Post by slamhound on 2010-04-10
If you are using hdmi, you don't need to set a tv-out option when installing the drivers.

---

### Post by x2aws on 2010-04-10
Well all just wanted to say that I finally got it working.  I had to install using opensource drivers, then go into package manager and grab the NVIDIA-current..  What was weird was that it took 2 reboots to finally "load" the drivers.  since then the NVIDIA splash screen has been popping up with no problem.  Enabled VDPAU and was able to get a picture from one of my 2 HD-PVRs (1 is connected, but with no input attached).  After that I went to work on my sound.
 
First I added the asound.conf, rebooted and no go.  Went into Myth added ALSA:hdmi, etc and still no sound.  I did some further reading and someone mentioned a setting in the Mixer that has to be ticked "IEC958 1".  Did that and I had sound!!! Finally!!!
 
:guitar:  Rock on!!

---

