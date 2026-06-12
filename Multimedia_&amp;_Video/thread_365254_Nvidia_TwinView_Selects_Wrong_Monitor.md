---
title: "Nvidia TwinView Selects Wrong Monitor"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by LaneLester on 2007-02-19
I prefer to run my two monitors and one card as separate X screens. But I'm now trying to get Beryl working in Feisty, and that won't work with separate X's (at least not for me and others). So I used nvidia-settings to switch to TwinView.

I haven't yet tried Beryl with TwinView, because I don't have TV working satisfactorily. The one thing that's wrong is that my CRT smaller-screen monitor is assigned as the "main" monitor instead of my larger LCD that sits right in front of me. So the top and bottom bars with all their goodies are over on the right and very inconvenient.

I've tried editing xorg.conf to get things the way I want them, but all I do is lose TwinView with my efforts. Do you know how I can fix this?

Lane

---

### Post by Skerit on 2007-07-21
I've been having the same problem, every application always open on my television instead of my monitor...

It's like a "baby hatchling" thing, when I added twinview on an old installation, everything went great, the screens just opened where they used to open, but on a new installation they choose the television first and like to stay there...

I read somewhere you need to use devilspie on Gnome, but there must be some other way, no?

---

### Post by DDRFreak21 on 2007-07-21
I just barely got my dual-monitor with beryl up and going not too long ago. My biggest issue was that my main monitor was on the right and secondary on the left and all the defaults were for the opposite.  What i finally ended up doing to get the situation right was going into nvidia-settings and setting both monitors as absolute and dragging them to the appropriate positions.
[IMG]http://i138.photobucket.com/albums/q273/DDRFreak21/Screenshot.png[/IMG]

*Note that you do not have to have space between the screens like mine is showing. The reason i did that is because I set beryl so that each monitor has it's own cube and when you combine that with the 3D windows that have space between each other on the cube i started to get a weird clipping from one monitor to the other when the windows got farther away. 

Basically all that means is, if you are going to have each screen be it's own cube AND do 3d windows then you may want to put the space in. However, if you aren't, say you use the cube but not 3d windows then you won't need to. 

If you do have space there is no way to span a program over both monitors. Which is ok for me since my screens aren't close enough to be seamless anyway. :)

Another thing I've noticed about doing dual screens with beryl is that when you double click an icon or start a program it will load the program on whatever monitor your mouse is at. 

Hope this helps!

---

### Post by Skerit on 2007-07-21
Hmm, the problem is the screens positions ARE absolute! So I guess your setup is working because you've added the dualscreen feature it a while after the installation?

---

### Post by DDRFreak21 on 2007-07-21
Possibly.. but i still had a lot of trouble getting things going initially and had to do some tweaking.

One thing that's important is what hardware are you using, video card, driver?
Also could both of you describe the exact layout of your screens relative to each other?

---

### Post by Skerit on 2007-07-21
I don't think it really matters what hardware it is, nvidie ofcourse, but this really seems like some stupid setting somewhere... 

Maybe in gconf or even xorg.conf ...

---

### Post by DDRFreak21 on 2007-07-21
So are you doing two monitors? Or a monitor and a TV?

---

### Post by MrHippocampus on 2007-07-21
If i've interpreted the problem correctly, the solution involves adding one line to the "device" section of the graphics card in /etc/X11/xorg.conf. The aptly named line is:

```
Option      "TwinViewXineramaInfoOrder" "DFP,CRT"
```

Normally twinview would treat my CRT as the primary and my flat panel (DFP) as the secondary, as im sure you can guess this line tells the driver to treat the DFP as primary and the CRT as the secondary. If you have e.g. 2 DFP's then numbers should be appened to the names, "DFP-1,DFP-2" (these show up in the nvidia-settings display configuration page, so just find out the right names and put them in xorg.conf)

For an example, heres the line in my "device" section of xorg.conf:
```

Section "Device"
[INDENT]        Identifier  "Card0"
        Driver      "nvidia"
        VendorName  "nVidia Corporation"
        BoardName   "NV40 [GeForce 6800]"

        Option      "RenderAccel" "true"
        Option      "backingstore" "true"
        Option      "AllowGLXWithComposite" "true"
        Option      "DamageEvents" "True"
        Option      "TripleBuffer"  "True"
        Option      "UseEvents" "1"

        Option      "TwinView" "1"
        Option      "Metamodes" "1280x1024,1280x1024; NULL,1280x1024;"
        Option      "TwinViewOrientation" "LeftOf"
        Option      "SecondMonitorHorizSync" "30 - 80"
        Option      "SecondMonitorVertRefresh" "50 - 75"

        Option      "TwinViewXineramaInfoOrder" "DFP,CRT"

        Option      "NoLogo" "1"
        Option      "Coolbits" "1"[/INDENT]
EndSection

```

Dont worry about all the other lines, there just there because I hand made my xorg.conf :)

More information about this command (and other useful ones) can be found in [appendix D (link)]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9626/README/appendix-d.html") of the nvidia driver documentation (its a fair way down the page so just search for "TwinViewXineramaInfoOrder").

---

