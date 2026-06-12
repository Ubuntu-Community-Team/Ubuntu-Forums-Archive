---
title: "Graphics Tablet - Disable one display for pen but leave another active in Precise"
date: 2013-12-30
forum: Multimedia Software
---

### Post by ArtMonkey on 2013-12-30
Hi there. I'm toying with the idea of making a transition to Linux exclusively for my graphics work. So any help here would be fab!

I want to disable my Aiptek 14000U (Waltop) tablet on my right monitor so that only my left monitor is used for this device; like I can in Windows 7. 
I'm using an Nvidia GTX 460 Graphics card with dual display 2x DVI out.

Monitors - Left: Dell U2412M 1920x1200 (DFP-2)  Right: Dell ST2410 1920x1080 (DFP-0)

:~$ xinput --list

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Media Tablet stylus    id=8    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:101d    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; WALTOP International Corp. Media Tablet     id=9    [slave  keyboard (3)]
    &#8627; WALTOP International Corp. Media Tablet     id=10    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=11    [slave  keyboard (3)]
    &#8627;   USB Keyboard                              id=12    [slave  keyboard (3)]

---

