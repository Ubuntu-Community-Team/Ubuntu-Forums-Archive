---
title: "Squished resolution and black bars on both sides of display"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by Nick816 on 2007-11-04
I used to have an older monitor that displayed at 1024x768, but now I've changed to a monitor that uses native resolution of 1440x900.
The problem is that I can use lower resolutions, but they are for square monitors. Mine is widescreen, and though the option for my native resolution is there, when i select it it comes up squished with black bars on the left and right. I can't make the image wider with the settings on teh actual monitor, either.
My computer uses intel onboard graphics, but I don't know how to get all the specifics that I've seen people post on the site. I'm more of just an everyday Ubuntu user, so I will need to be walked through any steps for editing files. Thanks :)

---

### Post by trappist on 2007-11-14
Read some of the other forum posts that talk about 915resolution and so on, that mostly applied to Feisty.  Then change drivers from "intel" to "i810" in your xorg.conf.  It's a downgrade, but it's what fixed me here.

---

