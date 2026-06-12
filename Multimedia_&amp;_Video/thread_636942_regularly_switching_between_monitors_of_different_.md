---
title: "regularly switching between monitors of different resolutions"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by aefaradien on 2007-12-10
I have a pc I use for multimedia playback in my living room.  Sometimes it is connected (via the VGA port) to a display that runs at 1920x1200.  Other times it is connected to a display that runs at 1024x768 (also via the VGA port - I am swapping the cable).

If I shut it down with the resolution set to 1024x768, then I can boot on either display with out issues.  If I shut down with it on 1920x1200, then I can't use the 1024x768 display (screen goes blank after boot progress bar screen) until I have booted under the larger display and changed the resolution.

Does anyone know of a way to make ubuntu ask what resolution you want each time it starts?  (with the question screen at 1024x768 ).  Alternatively, can someone please suggest a script or setting that will just make it boot at 1024x768 each time it boots, irreverent of what it was shut down at? (so I can at least see something).

Many many thanks in advance!

---

### Post by kubug on 2007-12-11
If you/anybody is wondering, the same would happen in Windows. 

Changing monitors before setting the resolution will always give you trouble.

But, if you have an nvidia video card you may be able to set the resolution to 1024x768 in your xorg.conf and once you are at your other (1920x1200) monitor you can use the nvidia-settings tool to change your resolution. 

Once you reboot you will be back to 1024x768 .... boy, I can see you getting tired of that quickly....

You may be able to do a similar thing with an ATI card (ATI people chime in!) or with an Intel integrated. But I am not sure with those.

---

### Post by sloggerkhan on 2007-12-11
well, I have an ati card, and currently, the way my computer is set up, I am pretty sure my laptop screen will always be working. If I have it at 3360x1050 and no external is hooked up, then I need to remember to lower the res or stuff might open on an invisible desktop. Likewise, if it's set to 1680x1050 and I boot, it defaults to mirror mode. Of course the displays in question on my machine are the same size.

---

### Post by aefaradien on 2007-12-12
thanks for the replies!

since this is linux, i am assuming the everything has a command line equivalent.  does anyone know the command to switch to a given res?  (like the option in the gnome preferences menu)

(in windows i know i can just write a quick vb script and call the appropriate api)

---

### Post by sloggerkhan on 2007-12-12
I think with an ati card, this might be done through the aticonfig command. There is also xrandr, but that doesn't work with all hardware.

---

### Post by aefaradien on 2007-12-12
interesting, i did not know about xrandr.  i shall have to give it a try.

---

