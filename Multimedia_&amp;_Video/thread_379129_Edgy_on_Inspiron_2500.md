---
title: "Edgy on Inspiron 2500"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by frisket on 2007-03-08
I managed to get Edgy to install on an Inspiron 2500 via the Alternative CD using the command-line installer because the video card settings aren't auto-recognised correctly.

It's an Intel 82815, which in the xorg.conf file seems to be recognised OK, but when X starts, I get a blank screen along with the Ubuntu opening sounds. I trimmed the default monitor settings to 8bit only, 800x600 and 640x480 (which I think is all it's capable of), but I don't know what else needs adding (my X config experience is limited to CRTs where you need vertical and horizontal scan frequencies, so I'm a little lost with fixed-pixel LCDs).

Does anyone have a working xorg.conf for an Inspiron 2500 they'd be willing to share?

---

### Post by renzokuken on 2007-03-08
what driver is your xorg.conf trying to use.

try the vesa driver, its very generic and stable

---

### Post by frisket on 2007-03-08
It turned out that it was just a matter of finding the right combination of depth and res. The only one which works with this machine is 16 bit and 800x600 -- you just need to edit out all other settings from xorg.conf so it doesn't even try them: the probkem seems to be that if it tests a res it can't handle, it's lacking the toggle to get back to the place where it can try another mode. Or something...

I might play with the vesa driver once this has stabilised, but as the LCD only possesses 800 dots by 600 dots there's not much point in trying 1024x768 :-) and I doubt there is memory for a 24bit depth.

---

