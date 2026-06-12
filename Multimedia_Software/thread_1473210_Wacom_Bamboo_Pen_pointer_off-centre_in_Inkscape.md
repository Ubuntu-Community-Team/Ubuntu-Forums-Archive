---
title: "Wacom Bamboo Pen pointer off-centre in Inkscape"
date: 2010-05-05
forum: Multimedia Software
---

### Post by jonjermey on 2010-05-05
Installed Ubuntu 10.4 -- wonderful.

Installed Inkscape -- no problem

Followed some instructions from the Web and got a Wacom Bamboo Pen tablet working perfectly in every single program (including GIMP) except Inkscape. In Inkscape for some reason, when I go to draw, the lines and shapes on the screen appear about 100 px below and about 5px to the right of the cursor showing the position of the pen. Meanwhile using the mouse moves the pointer but doesn't draw anything. None of this seems to change no matter what Input Device settings I select from the File menu.

Any ideas?

Thanks in advance,

Jon.

---

### Post by Favux on 2010-05-05
Hi Jon,

Given that everything else works try a simple approach.  I'd go to Synaptic Package Manager and get Inkscape.  Then right click on Inkscape and tell Synaptic to reinstall.  See if that clears it up.

---

### Post by jonjermey on 2010-05-06
Solved -- I think. I re-installed and then plugged in the tablet, and re-started Inkscape. At first I couldn't even set a stroke or fill -- the options just wouldn't respond -- but then I played around with the Input Device settings under File for a bit and it seemed to wake up. After that I was able to replicate the problem (mode set to 'Window) and get the tablet working properly by changing the device to 'Wacom Bamboo 4 * 5 Pen' and the mode to 'Screen'. So which of these actually fixed the problem I still don't know.

Thanks for your help.

Further to this: the way I 'woke it up' was to double-click one of the tools and choose 'This Tool's Own Style' from the dialog box. The logic seems to be that Inkscape can't use the previous (default) tool settings when you use a tool for the first time (?!). But if anyone reading this knows what the heck the 'Save' button in the Input Device settings window is supposed to do, please tell me.

---

### Post by Favux on 2010-05-06
Hi Jon,

Great!  Nice job.  I think the key things were:
> get the tablet working properly by changing the device to 'Wacom Bamboo 4 * 5 Pen' and the mode to 'Screen'.

---

