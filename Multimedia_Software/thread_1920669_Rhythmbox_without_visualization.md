---
title: "Rhythmbox without visualization"
date: 2012-02-05
forum: Multimedia Software
---

### Post by Raf Berkvens on 2012-02-05
Hello all

I've been using Rhythmbox for a while now and I recently figured I liked a visualization with it. So I went searching for one on the internet and found that there should be one included, GOOM or such. There should be a button next to the music controls to enable it. This button is missing in my version, however. 

I've tried to install an additional visualizations plugin, but nothing happened. 

I'm using Rhythmbox 2.90.1 on a Ubuntu 11.10 64-bit system.

Running Rhythmbox from command line gives following error:
```
$ rhythmbox 

(rhythmbox:3285): Rhythmbox-WARNING **: Could not open device /dev/radio0
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/replaygain/player.py", line 156, in playing_entry_changed
    pad.set_blocked_async(True, self.rgvolume_blocked_cb, self.rgvolume)
AttributeError: 'Pad' object has no attribute 'set_blocked_async'

(rhythmbox:3285): Json-CRITICAL **: json_object_get_array_member: assertion `JSON_NODE_HOLDS_ARRAY (node) || JSON_NODE_HOLDS_NULL (node)' failed

(rhythmbox:3285): Json-CRITICAL **: json_array_get_length: assertion `array != NULL' failed

```But I don't think this'll be useful in solving the problem. Please feel free to ask for any other information. 

Thanks for considering the problem!

---

### Post by Damascushead on 2012-02-05
Hmmm....
Maybe just try a simple reboot so it recognizes the plugin(s)?

If that doesn't work I guess you could try reinstalling Rhythmbox, although you have the newest version so that shouldn't be a problem.

---

### Post by Raf Berkvens on 2012-02-06
Thank you for replying. Rebooting does not solve the issue. Reinstalling Rhythmbox might, I've been thinking of that. But what of my settings, I don't know whether a visualizer is worth losing those.

---

### Post by Damascushead on 2012-02-06
I understand. Reinstalling Rhythmbox or any music player can be a pain. Especially if you have worked so hard to get your music all nice and organized.:p
 
I have the same version that you have and I don't see any visualization option in the plugin menu. However I am not running 64 bit.

---

### Post by Raf Berkvens on 2012-02-07
Ah, maybe I wasn't clear in the plugin part: Visualization in Rhythmbox shouldn't be a plugin. GOOM seems to be, as far as I can tell from posts about it, a program working with Rhythmbox, not listed in the plugins list. Searching for goom in 'apt-cache' doesn't give me anything however. I could be completely wrong in this, of course.

---

### Post by Zoasterboy on 2012-02-23
I also am without visuals, since doing a fresh install with 12.04. Interface is a little different, there's no menu option under "view" for visualizations.

---

### Post by schum3,1415 on 2012-03-09
Hi,

since upgrading to Ubuntu 11.10 I'm also left without visualization (rhythmbox version: 2.90.1).
There's no icon nor a menu-point in the upper menu-context.
Also de-installing (apt-get remove) and re-installing (apt-get install) didn't bring any change.

---

### Post by rg4w on 2012-03-25
Has a bug report been filed for this?

---

### Post by Raf Berkvens on 2012-03-26
Not by me.

---

### Post by rg4w on 2012-03-29
Anyone here know if the removal of the visualization options is a bug or was intentional?

---

### Post by alienseer23 on 2012-06-01
It was intentional. The new Rhythmbox uses something called clutter for it's visualizer, and ubuntu devs are, apparently, trying to stay away from it. Trying to install clutter, and placing the plugin in $HOME/.local/share/rhythmbox/plugins/

If it works. I'll let you know.

---

### Post by solidsnake666 on 2012-06-05
> **alienseer23 said:**
> It was intentional. The new Rhythmbox uses something called clutter for it's visualizer, and ubuntu devs are, apparently, trying to stay away from it. Trying to install clutter, and placing the plugin in $HOME/.local/share/rhythmbox/plugins/

If it works. I'll let you know.

Did this work? I really want to get visualizations working in rhythmbox if possible.

---

