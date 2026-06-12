---
title: "HOWTO: Can't display any resolution above 640x480, or other crappy resolution"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by caspian on 2008-01-27
I've been working on this problem for half the day, and finally figured it out after many hours of frustration. During my search for a solution, I've seen other people who had the same problem but was never resolved on these forums. Rather than bumping an old post, I've decided to create this "howto" hoping that someone experiencing the same problem may find this post.

The problem is that Xorg refuses to display any resolution above the minimum, which is 640x480. This was the resolution in my case, and searching around, it's the resolution many other people experienced, as well, who experienced this same problem.

Check your Xorg log in /var/log/Xorg.0.log . Search for "No valid modes for". If you see something like this, then you are experiencing the same problem I had:
> (WW) NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(WW) NVIDIA(0): No valid modes for "640x480"; removing.
(WW) NVIDIA(0):
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0): "nvidia-auto-select".
(WW) NVIDIA(0):
In my case, this only occurred when I was using the nvidia driver (it went away when I just used nv).

Ok, so here's how to solve the problem...

[SIZE="3"]**Has your monitor worked with your machine before?**[/SIZE]
If your monitor, graphics card, etc. has worked with your machine and xorg file in the past, and it suddenly stopped working without anything changing, then try rebooting your monitor. (I'm serious!) Log out, turn off your monitor, and unplug it for several seconds. Plug it back in and log back in. This ended up solving my problem, after I edited my xorg file (see below)... but just editing the xorg file and rebooting X wasn't enough ;)


[SIZE="3"]**If monitor rebooting didn't help, or you've never got your monitor/graphics card/xorg.conf working together in the past**[/SIZE]
If this is the case, your xorg.conf probably isn't configured correctly. Assuming you already have a xorg.conf file (this post is NOT meant to replace the other howto's on how to configure your xorg file), here's the basic rundown of what your xorg file should have...

Make sure that you have the "Modes" set in your Display subsection of Screen. Here's what my Screen section looks like:
> Section "Screen"
    Identifier     "Screen0"
    Device         "Card0"
    Monitor        "Monitor0"

    DefaultDepth   24
    SubSection     "Display"
        Depth      16
**        Modes      "1680x1050" "1024x768" "800x600" "640x480"**
    EndSubSection
    SubSection     "Display"
        Depth      24
**        Modes      "1680x1050" "1024x768" "800x600" "640x480"**
    EndSubSection
EndSection
(the line(s) in bold are the ones you need to make sure you have)

If this still doesn't work, make sure that you have the appropriate Modeline set. I chose to make a Modes section like this:
> Section "Modes"
    Identifier  "16:10"
**    Modeline    "1680x1050 (GTF)" 154.20 1680 1712 2296 2328 1050 1071 1081 1103**
EndSection
Your Modeline probably won't look like mine. Hopefully, you know the specs of your monitor (or can look them up). You can use this tool to generate the Modeline for you:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Finally, make sure that the Monitor section includes your HorizSync and VertRefresh options. These are values specific to your monitor (again, you'll need to look up your monitor's specs)

Here's my Monitor section
> Section "Monitor"
    Identifier      "Generic Monitor"
[b]    HorizSync       30-83
    VertRefresh     60[/b]
    Option          "DPMS"
    UseModes        "16:10"
EndSection
Log out and log back in. If the problem persists, reboot your monitor as described above.

I hope this post will help someone, someday!

---

### Post by AncientPC on 2008-03-30
This helped me just now (monitor worked before, needed a monitor reboot only).  Thanks!

---

