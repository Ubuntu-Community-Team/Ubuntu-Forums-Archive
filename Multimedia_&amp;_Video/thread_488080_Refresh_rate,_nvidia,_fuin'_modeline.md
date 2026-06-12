---
title: "Refresh rate, nvidia, fu*in' modeline"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by Tibology on 2007-06-29
Hi there!! :)

(My english is not so good, sorry about that...)

So i have a problem with my refresh rate. I want to use my monitor in 1280x1024 at 100Hz minimum,
but the largest refresh rate what i can use is just 85Hz with this resolution.
In windows that is works...
i tried to edit xorg.conf, added a modeline, but xorg absolutly doesn't care that, like xvidtune tells me when
i want to do something: 

Sorry: You have requested a mode-line
That is not possible, or not supported by your hardware configuration

I don't know what to do, and i don't find anything about this on google.
Any idea from anybody pls?



my xorg.conf:  (I have a TV, thats works perfectly)

```

Section "Device"
Identifier "nvidia1"
VendorName "nVidia"
Driver "nvidia"
Screen 1
BusID "PCI:1:0:0"
Option "NvAGP" "3"
Option "NoLogo" "true"
Option "CursorShadow" "true"
EndSection

Section "Monitor"
Identifier "MCM"
VendorName "Hyundai Electronics Industries Co., Ltd."
ModelName "Hyundai DeluxScan 15G+"
HorizSync 50.0-60.0
VertRefresh 100.0-240.0
DisplaySize 270 205
Option "DPMS"
#Option "UseEDIDFreqs" "FALSE"
Option "NoBandWidthTest" "TRUE"
Option "ExactModeTimingsDVI" "TRUE"
#Option "ModeValidation" "NoEdidModes, NoMaxPClkCheck, NoVertRefreshCheck, NoHorizSyncCheck, 
NoEdidMaxPClkCheck"
Modeline "1280x1024" 247.50  1280 1408 1712 2272  1024 1024 1028 1089
EndSection

Section "Monitor"
Identifier "TV"
HorizSync 30-100
VertRefresh 60
EndSection

Section "Screen"
Identifier "Screen0"
Device "nvidia0"
Monitor "MCM"
DefaultColorDepth 24

Subsection "Display"
Depth 24
Modes "1280x1024"
EndSubsection
EndSection

Section "Screen"
Identifier "Screen1"
Device "nvidia1"
Monitor "TV"
DefaultColorDepth 24
Option "ConnectedMonitor" "CRT, TV"
Option "TVStandard" "PAL-B"
Option "TVOutFormat" "COMPOSITE"
# Option "TVOverScan" "0.5" # Only from GeForce4
Subsection "Display"
Depth 24
Modes "800x600" "640x480"
EndSubsection
EndSection

```

---

### Post by imluxwhoru on 2007-06-29
I believe your problem lies with your VertRefrest and HorizSync lines in the Monitor section.  I can tell you what to change them to, but 1st I need to know a little more about your displays.

Your Monitor is a Hyundai DeluxScan 15G+, correct?

What type of TV is connected? (CRT, LCD, Plasma?) What is the Brand and Model number?

Are you running both displays at the same time, showing the same screen, or are they both showing different displays (Dual Display)?

If you tell me the answers to these questions I will be able to tell you what to change the HorizSync and VertRefresh lines to. Then your refresh rate and resolution should do what you want them to. :)

Good luck!

---

### Post by Tibology on 2007-07-02
My monitor is Infotronic gzm1724. Have you any idea where i can a manual for this. I tried a lot, but nothing. My tv is projektor, samsung, i don't know what type, but it's working fine.

---

### Post by imluxwhoru on 2007-07-02
Ok. I have no idea where to find a manual for your monitor. Actually, I could not find much information at all about it. So, I'll just have to use my genius to figure it out. :)

Lets try this. I believe it'll work.

Open up /etc/X11/xorg.conf in your favorite text editor.

Look for the section "Monitor" That has the identifier "TV" And change the VertRefresh & HorizSync values as so:
```
HorizSync 42.0 - 94.0 
     VertRefresh 56.0 - 76.0
```

Then, find the section "Monitor" that has the identifier "MCM" and change the VertRefresh & HorizSync values like this:
```
HorizSync 31.0 - 81.0 
     VertRefresh 56.0 - 76.0
```

Then, in that same section, delete or #Comment out this line:
```
Modeline "1280x1024" 247.50  1280 1408 1712 2272  1024 1024 1028 1089
```

Save and Exit.

Restart X (Ctrl+Alt+Backspace)

That should take care of it. If not, let me know, and I'll rethink this one.
Good luck!!

---

### Post by Tibology on 2007-07-04
Thank you for your quick answer.

Now im don't use the tv, it isn't in my xorg.conf now.
I rewrite it how you sad, monitor HorizSync and VertRefresh, and deleted the modline.
It's the same when i'm used the 'dpkg-reconfigure xserver-xorg', and in the monitor settings i set in simple mod to 21".
Its working fine, but in 'nvidia-settings', the max settingable Hz is just 85Hz.

I can't understand, when in windows i just have to set 1280*1024 and 100Hz, it works fine.
Why not working in here? Or can i read the settings in windows and just write it in my xorg.conf?
I don't have a win now in my comp, but if this can solve the problem it doesn't problem.

My another problem is i can't resize the picture in my monitor, cause i locked the monitor keyboard (osd), and i can't unlock it. And there is no manual. :S :) And xvidtune doesn't work for me. It say me when i click to apply or  test button, even if i don't change anything:

Sorry: You have requested a mode-line
That is not possible, or not supported by your
hardware configuration

So i think now i have to use the same refresh rate what i used in win, because that mode are in my monitor memo, and the screen position is saved and correct.

Any idea?

---

### Post by Tibology on 2007-07-27
I'm sad if there's no solution for this not so big problem :???:
Maybe Linux isn't so good, how i think that?? :-(

---

### Post by kostkon on 2007-07-27
First of all, I think it's Nvidia's Linux driver fault and not Linux or Ubuntu's fault.

Anyway, the thing I did to force a specific vertical refresh rate for my Nvidia card is to put this line in the *Screen* section of my xorg.conf

```
 Option         "metamodes" "1024x768_60 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
```

This line forces the Nvidia card to use 60 Hz vertical refresh rate at 1024x768 resolution. If you can somehow change it to fit your circumstances maybe it'll work. Nevertheless, I cannot guarantee that it will work or that it will not destroy your monitor! Thus, I cannot take any responsibility for this, it works for me but I cannot say that it will work for you. But, you can start from this and research it more on the net.

There is a bug with the Nvidia driver I use (the version of the driver that is offered from Synaptic) that does not show all the available resolution and refresh rates that your graphic card and monitor can handle or even it loses your selection every time you restart and you have to set it again every time.

Thus, I had to do this in order to fix this problem.

---

