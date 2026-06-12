---
title: "Smart Stretch (aspect ratio)"
date: 2010-06-05
forum: Multimedia Software
---

### Post by zippyblue on 2010-06-05
New to Ubuntu and all, but not doing badly.

On MS media edition, using Power DVD to watch movies, I can select Smart Stretch to fill my 32" screen with a program that was originally 4:3 without unpleasantly distorting the image.

My question: is there a way to customize aspect ratios in Totem movie player?  Or, is there open source software for Ubuntu that has that capability?

James

---

### Post by dv3500ea on 2010-06-05
in totem have a look at 
view -> aspect ratios

---

### Post by xzero1 on 2010-06-05
Mplayer should provide a bit more flexibility. You can do some similar to this:

mplayer -aspect AR -panscanrange N ...

This allows you to pick any aspect ratio (stretch) and also interactively zoom in a bit as needed using the "w" and "e" keys. 
It is not clear to me how N relates to the actual zoom factor despite the docs, but negative values means a larger zoom. I would start with values around -0.45. Note that this is experimental and only works when viewing fullscreen. I find this especially useful when playing widescreen videos.

---

### Post by zippyblue on 2010-06-06
The aspect ratio settings in Totem are "Auto" "Square" "4:3 (TV)" "16:9 (Widescreen)" and "2:11:1 (DVB)".  There is no obvious allowance for a custom setting.

---

### Post by zippyblue on 2010-06-06
In installed Mplayer yesterday and tried to play a DVD.  I received an error message.  No doubt, I overlooked some obvious step or bit of information.

---

### Post by xzero1 on 2010-06-06
Post your mplayer command line with the errors.

---

### Post by freetolio on 2010-06-13
I have a related problem with Gnome-mplayer.  I can select view->aspect->"follow window" every time I run it, but after reading the documentation and googling around, I couldn't figure out how to set it to that by default every time it runs.  

For some reason the regular 16:9 setting doesn't scale right and I get black bars above and below on my 16:9 display.

---

### Post by xzero1 on 2010-06-15
> **freetolio said:**
> I have a related problem with Gnome-mplayer.  I can select view->aspect->"follow window" every time I run it, but after reading the documentation and googling around, I couldn't figure out how to set it to that by default every time it runs.  

For some reason the regular 16:9 setting doesn't scale right and I get black bars above and below on my 16:9 display.

If the aspect ratio of the video you are trying to play is greater than 16:9, then this is normal. It should only fit 'perfectly' if the video's aspect ratio is the same as your display (16:9).

---

### Post by freetolio on 2010-06-15
The stuff I'm watching is just TV streams from the web, so I don't think they would be recorded in a wider than 16:9 format.

I couldn't find how to config the auto zoom properly.  I tried monitoraspect, monitorpixelaspect, aspect, and zoom keywords.  I now just tap 'A' four times and that seems to work.  What is really odd is that mplayer launched from the command-line WILL respect the zoom settings in the config file and scale properly by default, but the version launched in-browser or when clicking a file will not and has to be cycled by the 'A' key.

---

### Post by xzero1 on 2010-06-15
> **freetolio said:**
> The stuff I'm watching is just TV streams from the web, so I don't think they would be recorded in a wider than 16:9 format.

I couldn't find how to config the auto zoom properly.  I tried monitoraspect, monitorpixelaspect, aspect, and zoom keywords.  I now just tap 'A' four times and that seems to work.  What is really odd is that mplayer launched from the command-line WILL respect the zoom settings in the config file and scale properly by default, but the version launched in-browser or when clicking a file will not and has to be cycled by the 'A' key.

Once the file is playing, run system monitor, point to the process (mplayer) and you will see the invoked command line. That should help you see if it correctly applies the config file settings.

---

