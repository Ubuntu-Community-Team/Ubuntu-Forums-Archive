---
title: "Image in guide - on screen display"
date: 2009-02-17
forum: Mythbuntu
---

### Post by iitywygms on 2009-02-17
Okay, I am getting picky I know but I want to remove the image behind my guide.  It is the dark square box I have outlined with blue lines and pointed to with red arrows.  I have no idea why it is there.  I am sure I have to edit the theme but do not know where to start.  Any ideas?

[IMG]http://i193.photobucket.com/albums/z161/dabears_rule/Screenshotofmythtv.png[/IMG]

---

### Post by scary_jeff on 2009-02-17
I can't tell what theme you are using so I can't tell you the exact file, but for me, the image being used is /usr/share/mythtv/themes/ProjectGrayhem-wide/programguide/pgv-background.png

I found this by looking in /usr/share/mythtv/themes/ProjectGrayhem-wide/ui.xml - it's the image for the background container for the programguide-video window in the program guide. I guess your theme might have different filenames or be split into more different files.

---

### Post by iitywygms on 2009-02-17
Im using mythbuntu-wide.  I will search for this and just delete it?

---

### Post by scary_jeff on 2009-02-17
I'm not sure. You could edit it to be totally transparent, or try altering the xml file to either remove the background completely, or if this doesn't work for some reason, you could try moving it off the screen! I don't really know much about working with themes, I just go into the xml files and alter things at random until I get the result I want. There is some explanation in the mythtv wiki, under theme development.

Your post inspired me to make the tv window in the corner bigger (something that's been bugging me for a while); in doing this, I found that you can reload the guide xml file just by leaving and reentering the guide. This made editing it a lot faster (using ssh from a laptop to edit the xml).

I just had a look in the mythbuntu-wide theme, and it looks like it uses the same relative file.

Good luck :)

---

### Post by iitywygms on 2009-02-17
Worked!  Thanks so much.
I forsee myself screwing up my theme.  I just love tweaking stuff.  I must backup!

---

