---
title: "[SOLVED] Squished together fonts - DPI setting seems not to help?"
date: 2008-02-14
forum: Mythbuntu
---

### Post by jpfreely on 2008-02-14
I've got a problem with the TV-out On Screen Display. Basically the fonts are squished together for the On Screen Display - i.e. the display that comes up while watching TV for Menus and program information. The size of the text is just fine but unreadable due to the squishing.

I read that the optimum setting was 100 dpi for the display, so I added the following to my monitor section:

Option    "UseEdidDpi"  "FALSE"
  Option    "DPI"  "100 x 100"

Checking /var/log/Xorg.0.log I find a line which says 
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
so I'm assuming that it is setting the correct DPI in theory (needless to say I've got an Nvidia card). This doesn't seem to change anything.

One interesting thing - if I VNC into the box then the fonts look absolutely fine.

---

### Post by jpfreely on 2008-02-17
Ok, so I discovered it's got nothing to do with the TV-out settings, rather it's the aspect ratio I had set.

I had it set to 16:9 zoom which cuts the sides of the picture to make it fit on my 4:3 TV. The picture looks great but this is what is causing the OSD fonts to be squashed together. Does anyone know if/where there's a setting to tell myth not to change the aspect ratio of the OSD?

Screenshot attached for those interested.

---

### Post by gsrcrxsi on 2008-02-17
do you have the menu set to the widescreen version?

---

### Post by jpfreely on 2008-02-17
I don't think so. I've got the monitor set to 4:3 in the appearance section and got the Retro-OSD theme in the TV settings - playback section. Unless there's another setting or a special version of the OSD theme I need? All OSD themes I currently have installed seem to do the same thing.

---

### Post by Caps18 on 2008-02-17
I've had the same thing happen to me today.  I made the font a little smaller and used a differnt font and it made things a little better when watching the non-HD channels.  It looks great on the HD 16:9 channels.

---

### Post by jpfreely on 2008-02-21
OK so I figured it out.

I forget where I saw it now (might have been on the Ubuntu forums even) but it somehow has to do with the font. The default font for most of the themes seems to be Vera - that's the sans serif font you see scattered throughout Ubuntu.

So I changed the font - I went to /usr/share/mythtv/themes/Retro-OSD and changed the theme's xml file by removing all references to any font. What this does is change it so the theme uses the font selected in MythTV's Settings (under I believe TV > Playback). The Freesans font that MythTV uses is much less resistant to squishing. You can tell it's still a little squished but it's definitely readable.

Apparently this is all caused by the fact that the OSD is generated as part of the video stream - i.e. it's not a seperate layer on top but actually but of the video. Thus it's resolution and aspect ratio will be the same as the video stream. Changing the aspect ratio therefore means Myth has to do some work to squish or stretch the OSD accordingly. This could obviously be done better to avoid some fonts being squished but as far as I've read anyone reporting bugs is pretty much told it's their own fault. (Incidentally it appears typical MythTV forums and bug reporting areas tend to trend towards this!)

---

### Post by notidefix on 2008-06-03
could you please elaborate on the details?

when I remove all references to all fonts, then ll I get is the background and no text whatsoever

---

### Post by jpfreely on 2008-06-03
Do you have a default font set under TV > Playback? This is what it should fall back to when you remove the font.

Otherwise try putting the font references back in but change from Vera to a different font name and try that.

---

### Post by notidefix on 2008-06-04
thanks, solved it. you're a legend!

---

### Post by notidefix on 2008-06-04
also, I noticed that the other OSD themes do not scale their info areas like the Retro theme.

Any idea what determines if a theme scales or not? I could not find any parameter in the xml file...

---

