---
title: "PC to LCD over HDMI taskbar out of sight"
date: 2010-02-05
forum: Multimedia Software
---

### Post by Papa.Coen on 2010-02-05
Hi

I'm running a clean install of 9.10 on a crispy new pc (Packard Bell I-extreme) I've connected my pc via HDMI to my Samsung 5 LCD tv (source is marked/named 'pc') by means of an NVIDIA

The problem is that the x screen is too large for my tv. I see the 'working area' but the top and bottom taskbar fall of the screen. 

The current settings (which I of course double checked) worked when the pc was connected to the lcd via VGA cable. X Server settings and TV resolution are set to the same values...(1920x1080)

What am I missing or doing wrong?

---

### Post by Grenage on 2010-02-05
This sounds like the usual Nvidia twinview EDID problem, you're likely getting overscan.  Are you able to download the Samsung EDID using nvidia-settings?

---

### Post by Papa.Coen on 2010-02-05
Thank you for your reply.

I think I've come across the option to retrieve it [EDID]. Does this automatically set the right settings or do I have to do s'thing with the info?

---

### Post by Grenage on 2010-02-05
Save the EDID file somewhere (I recommend /etc/X11) then take a look at xorg.conf.  It you're using Twinview then you can try something along the lines of:

```
Option	"TwinView"	"1"
Option	"TwinViewXineramaInfoOrder"	"CRT-0"
Option	"metamodes"	"CRT-0: 1440x900_75 +0+0, CRT-1: 1440x900_75 +1440+0"
Option	"CustomEDID"	"CRT-1:/etc/X11/edid.bin"
```

If not, and you're only using the TV:

```
Option "UseDisplayDevice" "CRT-0"
Option "CustomEDID" "CRT-0:/etc/X11/edid.bin"
```

As you can see, the part we're really interested in is the line that references a custom EDID.

---

### Post by Papa.Coen on 2010-02-05
Thanks again, I'll let you know how it works out...

---

### Post by Papa.Coen on 2010-02-09
Well, I didn't seem to work

Stuff I tried:
- I placed the lines in section 'Screen' or 'Device'
- I used the lines:
	Option "UseDisplayDevice" "DFP-0"
        Option "CustomEDID" "DFP-0:/etc/X11/edid.bin"
- I replaced CRT-0 with DFP-0 or DFP-1 (I do not use twinview though)
- I ran the nvidia-settings app as root and let it save a xorg,conf
- I did a chmod +r on edid.bin to have the same rights as xorg.conf, just in case.
- I removed a failsafe xorg config file, just in case.

Darnit. What am I doing wrong?

---

### Post by mcduck on 2010-02-09
One thing that comes to mind.. Have you checked your *display's* options? Most monitors and LCD TV's have their own tools for correcting image alignment (usually separate settings for each input). Often there's even an automatic option that will align the picture for you.

If the image is otherwise correct but aligned badly that would be the first thing to check. :)

---

### Post by Papa.Coen on 2010-02-16
Hehe,

It works now. I have (also!) changed a setting on my TV, it's a display size/format option. It was set fixed to 16:9, when I changed it to 'full screen' (with the description 'Shows the original, full HD screen only HD tv's can show'.

et voila! I've got my taskbars back...

I could try my original xorg.conf to see if it contributes to the solution too. But why bother :)

Thanks for the help!

---

