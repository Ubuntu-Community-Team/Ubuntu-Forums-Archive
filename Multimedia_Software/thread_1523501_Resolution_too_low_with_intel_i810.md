---
title: "Resolution too low with intel i810"
date: 2010-07-03
forum: Multimedia Software
---

### Post by Vyco on 2010-07-03
So.  I'm using Karmic and just recently had to do a fresh install.  After installing I immediately ran the update manager and updated everything I was told to update. Upon rebooting, my resolution is stuck at either 800x600 or 640x480.  I've been searching around for a while now, and none of the fixes I've looked at have worked with my architecture.  Here's my lspci output.

```

lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (gmch) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
01:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

```Ideally I'd like to have 1280x1024, which is what I had originally.

EDIT: I'm new here, and just realized this probably should have went in the general help section.

---

### Post by SmokeyThePanda on 2010-07-03
I have had several problems with this. It happens every time I do a clean install. It's an easy fix though. :)

Open your terminal and type the command:

[I]sudo nano /etc/X11/xorg.conf

[/I]You may replace nano with your favorite text editor, I use nano because it's simple. :p

What you will need to do is look at the list I post below and edit them to fit your needs. You will need to find all available resolutions available for your monitor as well as the vertical refresh and horizontal syn. You can usually find these in your monitors manual or a site that gives specs on your monitor. 

```
Section "Device" 
        Identifier      "Configured Video Device" 
EndSection 

Section "Monitor" 
    Identifier    "Generic Monitor" 
    HorizSync     30 - 60 
    VertRefresh   60 - 75 
EndSection 

Section "Screen" 
    Identifier    "Default Screen" 
    Device        "Configured Video Device" 
    Monitor        "Generic Monitor" 
    DefaultDepth    16 
    SubSection "Display" 
        Depth        16 
        Modes      "1024x768" "800x600" "640x480" 
    EndSubSection 
EndSection  

```Note, this *may* not work for you. However, it works for most people. Just make sure to edit it to fit your monitor. If it doesn't work, repost in this thread and someone will attempt to help you further.

---

### Post by Vyco on 2010-07-03
Thanks for the quick response, but I'm still having problems. My monitor doesn't have any kind of identification, and I have no idea where I could find info on it.

---

### Post by SmokeyThePanda on 2010-07-03
Hmm..Not sure what you could do then, to be honest. Do you have an alternative monitor you can use?

---

### Post by Vyco on 2010-07-04
Well, not sure what I did, but I logged out of my xterm session and the resolution went back to normal.  That was odd.

---

