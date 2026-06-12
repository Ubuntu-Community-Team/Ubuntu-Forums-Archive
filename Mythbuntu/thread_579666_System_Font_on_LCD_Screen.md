---
title: "System Font on LCD Screen"
date: 2007-10-18
forum: Mythbuntu
---

### Post by edrock on 2007-10-18
Quick Summary: How do I get the fonts to display in a legible manner, on a 42" LCD Screen with a Nvidia GeForce MX400 graphics card, using the VGA monitor port out(to a VGA port in on the tv)?

Long Story:
My issue pertains to the system fonts, and their display on my 42" LCD TV. The are way to small, and I am unable to read them. I am new to Linux/Ubuntu/myth, so I am hoping there is a relatively easy solution for this issue.

When I first started the install process, I was unable to see the installation screens, so I figured it was my resolution(all the windows fit on the tv fine though), so I changed it to what I would guess was something around 800x600, just to see if I could see what the installation windows were saying. It changed the resolution, everything blew up huge on the screen, except for the fonts. They were still super small(like 2-3 pixels tall). I thought well maybe if I finish the installation, the nvidia drivers might fix this.(I have a nvidia GeForce MX 4000 which I'm using the vga port..to the vga in the back of my tv), so I took the pc into another room that has a standard crt monitor, plugged it in, and I could read everything. I finished the install, updated everything, etc.

Since I had all the updates and everything else I thought I would need, I took the pc back into the living room, plugged it in, and the mythtv screen preloaded the images...everything looked great! UNTIL i went to change a setting in myth, the drop down boxes, input boxes, text, everything is super small. I exit myth and ubunutu is the same way.

In short, how do I get the fonts to display in a legible manner, on a 42" LCD Screen with a Nvidia GeForce MX400 graphics card, using the VGA monitor port out(to a VGA port in on the tv)

Thank you so much in advance, and again I'm very new to linux, so please if there is a solution, understand that I might have more questions as to how to administer it.

---

### Post by superm1 on 2007-10-18
Check and make sure the DPI is 100x100.  It should be automatically when you installed (from the RC and onward).

```
xdpyinfo | grep dot
```

---

### Post by ickyb0d on 2007-10-18
I've had the same problem you described and took a look at it in [this thread]("http://ubuntuforums.org/showthread.php?t=575397").  

As of now the only way i can get good fonts is from using the VESA driver instead of my onboard intel.  In hopes of fixing this, i've purchased a nVidia GeForce 7600GS (hey... i needed a video card anyways).  So hopefully this will fix the problem.

Is this possibly just the display driver interpreting the EDID info from the TV wrong?  I've tried manually setting the DPI and DisplaySize (which calculates DPI) in the xorg.conf.  Still no luck.  Hopefully the new video card will solve all problems!

---

### Post by edrock on 2007-10-20
since i cannot read anything when its connected to my tv, i brought the computer back into the room that has the regular crt monitor. i typed what you said into the terminal.. and it shows as. resolutions:   96x98 dots per inch

now what?

---

### Post by edrock on 2007-10-20
since i enabled the nvidia drivers, the resolution has changed to 87x96 dots per inch.(on my crt monitor, after enabling drivers, and updating the system)

---

### Post by hugmenot on 2007-10-20
Just go into the Appearance dialog and increase the DPI in the fonts preferences until you&#8217;re happy. Simple.

---

### Post by superm1 on 2007-10-20
Nvidia cards support adding a 

```
 Option      "DPI"          "100 x 100"
```

Option in the xorg.conf

---

### Post by edrock on 2007-10-20
where is that located exactly? 
hugmenot

---

### Post by hugmenot on 2007-10-20
System &#8594; Preferences &#8594; Appearance &#8594; Fonts &#8594; Details &#8594; "Resolution" spinner field

God, this sounds like giving instructions for Windows dialogs.

---

### Post by thematadorme on 2007-12-14
I've just posted a detailed "how-to" on increasing the font size on TVs. I think it might help you.
[http://ubuntuforums.org/showthread.php?t=640389]("http://ubuntuforums.org/showthread.php?t=640389")

---

