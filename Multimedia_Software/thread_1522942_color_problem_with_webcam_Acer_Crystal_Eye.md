---
title: "color problem with webcam Acer Crystal Eye"
date: 2010-07-02
forum: Multimedia Software
---

### Post by tjwilli on 2010-07-02
I recently upgraded from Jaunty to Karmic. Now I'm having issues with my webcam. I have an Acer Crystal Eye and when I try to use Cheese, to test it, the colors are not normal. Rebooting clears things up until I try again.

Also, when I try gstreamer-properties, If I use Autodetect for the plugin for default output, the test video has incorrect color bars. If I select "X Window System (No Xv)" (pipeline ximagesink) the color bars are correct, and the test for default input shows good video. The plugin for default input is "Video for Linux 2 (v4l2)".

If I leave the plugin set to X Window System, then when I bring up Cheese, I don't get live video, just a frozen frame.

How do get these colors right?

Thanks.

---

### Post by tjwilli on 2010-07-02
I found a thread that fixes this.

[http://ubuntuforums.org/showthread.php?p=5152874#poststop]("http://ubuntuforums.org/showthread.php?p=5152874#poststop")

The gstreamer-properties fix sets the color right for Cheese webcam,but Skype still has the wrong colors.

> Just letting you know I have discovered another work-around that doesn't require you to manually set the hue every time you open a video

To implement the workaround, do the following:

   1. Open gstreamer-properties (alt+f2, enter gstreamer-properties)
   2. Change to the video tab
   3. Change the default output plugin to "custom"
   4. Place the following command in the bottom box: videobalance hue=-1 ! autovideosink
   5. Close the box and enjoy your now correct colour

To fix Skype, I needed to use the first fix given in post #2 for the above mentioned thread

> The crux of it is you can test for this bug using the following:
Code:

xvinfo | grep -A2 XV_HUE

The XV_HUE should be 0... but for some reason it gets set to 178 when opening a movie in Totem using the GStreamer backend.

You can fix it using the following (temporary!) fix. This will need to be run after every boot, so you might want to set it to run automatically when you login possibly...
Code:

xvattr -a XV_HUE -v 0



I haven't rebooted to see if this all sticks yet, but so far, so good.

---

### Post by tjwilli on 2010-07-02
Not quite SOLVED yet. If I go back and forth between Cheese and Skype, 
> videobalance hue=-1 ! autovideosink
doesn't seem to do it. I can still reset with > xvattr -a XV_HUE -v 0

Setting hue=0 instead of -1 also seems to reset it. Not sure, but maybe any different value may reset it.

---

### Post by tjwilli on 2010-07-03
It looks like the playing back of the captured video is what corrupts the hue values. When I play it back with Totem Movie Player 2.28.2, the hue value changes, but VLC and mplayer work. I do get a popup with mplayer about not being able to open a codec, but the video plays fine.

The file type of .ogv (Ogg video)

---

### Post by tjwilli on 2010-07-03
Just opening up movie player w/o even playing a movie changes the hue! ](*,)

---

### Post by tjwilli on 2010-07-03
Found this thread about totem messing with colors:

[http://ubuntuforums.org/showthread.php?t=1312298&highlight=totem+colors]("http://ubuntuforums.org/showthread.php?t=1312298&highlight=totem+colors")

I went in gconf-editor, and I saw that the hue value was correct at zero, but still playback changes hue.

---

### Post by tjwilli on 2010-07-03
I may have fixed it. I brought totem up, then went to Edit->Prefences, Display tab, noticed that the Hue slider was set all the way to the left. I clicked the Reset to Defaults button, and that seems to have done it. I played the ogv file a few times, and the hue hasn't changed.:D

---

