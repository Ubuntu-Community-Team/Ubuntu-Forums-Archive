---
title: "Help needed with recurrent freezes if using NVidia video drivers"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by atonello on 2007-01-02
Well, after a long time of useless trying, browsing Ubuntu and NVidia Linux forums, I've finally decided to post my problem, hoping to find help...

My problem is that I can't use NVidia drivers in Ubuntu (*6.10 32 bit, but it was also the same in 6.06, even tried 32 and 64 bit, since it's a problem I'm regularly having since I built my current system on last september*) for more than a few hours (*sometimes it's more, sometimes just for a few minutes*) before it will inexorably freeze.

With *freeze* I mean that either usb mouse or ps/2 keyboard stop responding, system clock on the upper panel is equally freezed; if music was being played at freeze time, then it keeps looping last audio frame.

Ctrl+Alt+backspace, Ctrl+Alt+F1, Alt+SysReq+s/b - they're all useless since the keyboard stops responding, the only exit way is hitting the reset button...

If I use "nv" in xorg.conf the system is rock solid.

I've also tried various workarounds (such as noapic, nolapic, in kernel boot; disabling cpu frequency scaling, compiling my own kernels; etc.), with no luck.
Though I'm now using the latest NVIDIA...9746-pkg1.run driver, I've been struggling with the very same problem for months and, obviously, with different versions on NVidia drivers (either installed from synaptic or from NVidia and even using automated scripts such Envy and Automatix - in different times and passing through various formatting and reinstalling Ubuntu...).

Thank you

My system specs are here:
M/B Asus A8R32mvp (chipset Ati RD580) + Asus NVidia 7300LE Pci-e 256 mb + A64 X2 4200+ (no overclock)

P.S. Ram passed very long tests with memtest86+ and system is also stable under WinXp (other than using Ubuntu + "nv" in xorg.conf).

---

### Post by atonello on 2007-01-03
Anybody help?

Just in case, I'm attaching yesterday's nvidia-bug-report.log

---

### Post by closet geek on 2007-01-03
I'm afraid I can be of no real help. I can tell you however that you are not alone I have the exact same problem. It's very very frustrating.

cg

---

### Post by chronusdark on 2007-01-03
any chance you can pull up the nvidia settings so you can see the gpu core heat lvls or your CPU heat levels it sounds like a heat problem

im not an expert im just talking from experience

also try different resolutions/color depths/refresh rates

---

### Post by atonello on 2007-01-05
I don't think it's a matter of heat, yesterday I tried again with Nvidia drivers and collected two crashes in 10-15 min; while doing this, I was running glxgears and checking gpu temp. by Nvidia panel. At the moment of freezes it was 66-67°C. More relevant is the fact that I had established an ssh connection to my pc via lan: when it freezed, the connection was lost and even on my router the ip of the "freezed" computer had disappeared. I've exposed this on NV-Forums ([http://www.nvnews.net/vbulletin/showthread.php?t=83479](http://www.nvnews.net/vbulletin/showthread.php?t=83479)) and have been asked to setup a serial console to capture kernel messages from the system. Now I'm in the process of retrieving a null modem cable (10 years ago I made one but go figure where it is now! :mrgreen: ).

---

### Post by tseliot on 2007-01-05
Enter the BIOS and make sure that PCI-E is set as your graphical adapter instead of PCI.

---

### Post by atonello on 2007-01-05
Yes, unfortunately, it was already set on PCIE; as I was there, I've disabled 2nd pci-e (just in case). Later I'll check if that changes anything (now I can't risk crashing).

P.S. Thinking if it's the case of lowering pci-e speed, too... I'll try that.

edit:
Checked with only PCI-E n°1 enabled and set to 8x (instead of 16x per default) and it crashed! 
It was one of the shortest lived sessions I've ever seen, just the time to login and open a terminal and all freezed!

---

### Post by atonello on 2007-01-05
Arrghhhh... ](*,) 
There's no serial port on my motherboard (i gave it for granted... there's only a parallel one) > so I can't set a serial link to capture kernel messages as requested on Nvidia forum.

---

### Post by RandomJoe on 2007-01-05
I had a similar problem with a brand new C2D setup.  When I tried running multiple monitors (two dual-head cards) it would freeze hard at random intervals.  In my case, it never froze when only using a single card, but perhaps I just didn't wait long enough...!

After searching the nVnews forum I found a suggestion to try adding "pci=nommconf" to the kernel boot line and that fixed the problem!  I hadn't ever heard of that option - perhaps something to try?

---

### Post by atonello on 2007-01-06
unfortunately dmesg already shows "PCI: Not using MMCONFIG"; glad to know you solved your problems, anyway :)  
Now I'm searching about parallel ports and how to set a console through them (it seems to be possible, so I've not lost hope! -yet)

---

### Post by mysticmarks on 2007-01-15
its not just nvidia issues. This is coming up in multiple threads. I have had the same random lock up. it has been reported as a firefox/video hardware/plugin/totem/ etc. I think its something else all together. I run smooth for hours or sometimes minutes. tried including/excluding multiple everything. It seems that a majority of random freeze ups are from AMD systems. Im using ATI radeon 9200, same issues. Driver changes dont fix it because its very random.

---

### Post by allartk on 2007-01-16
Same problem here. Tried to disable composite, directrendering, upgraded my bios, set first graphics card to PCI-E but it didn't help. Same issue on suse 10.1 suse 10.2 and ubuntu edgy on different nvidia drivers including beta.

I have an onboard ATI-EXPRESS card that i don't use and a new NVIDIA CARD in my PCI-E. Since i put this new card in and use the nvidia drivers there are freezes on my system (AMD PROCESSOR, MSI motherboard).

If someone can help me i will be very very happy.

Edit:
Maybe this provides some answers:
[http://download.nvidia.com/XFree86/Linux-x86/1.0-9626/README/appendix-l.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-9626/README/appendix-l.html)

Edit2:
I hadn' t disabled "internal video mode" in my bios. I did only change "init display first". This seems to be the solution because playing nexuiz before was full of freezes and for now it runs smoothly.

Edit3:
This didn't solve everything. For example Beryl freezes pretty quick. I will post mij xconfig which lets me run stable for many hours.
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
#    Load 	   "dri"
#    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
#    Option  	   "XAANoOffscreenPixmaps"
#    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

---

