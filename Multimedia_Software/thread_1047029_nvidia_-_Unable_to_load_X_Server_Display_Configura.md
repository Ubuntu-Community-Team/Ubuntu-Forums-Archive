---
title: "nvidia - Unable to load X Server Display Configuration page"
date: 2009-01-22
forum: Multimedia Software
---

### Post by steenbras on 2009-01-22
I use TwinView on my laptop (Dell XPS M1530) at work and at home, and normally suspend between the 2. At work I connect to a dell LCD monitor, and at home often connect to my Samsung PDP to watch movies etc.

My normal course of events is to suspend, unplug everything, and then to reconnect to the other panel and open the lid, which performs a resume. I then launch the NVIDIA X Server Settings application, choose X Server Display Configuration, then detect displays to get it to notice that screen 1 is no longer the Dell LCD and is now the Samsung PDP (or vice versa). Then choose the new screen and setup TwinView and I'm all set to go.

[INDENT]Unfortunately, though, often, when I choose X Server Display Configuration, I get the following message:

Unable to load X Server Display Configuration page:

Failed to find display device 0x00000001 on screen 0 (on GPU-0)
while parsing metamode:

'CRT-0: nvidia-auto-select @1280x1024 +1440+0'
[/INDENT]

And the only way I can get both screens up again is to Ctrl-Alt-Tab and restart X Server.

2 questions:

[LIST=1]
[*]Is this a bug in the X Server Settings application?
[*]Is there a way I can recover without restarting the X Server - a command line way of removing display 1 or something?
[/LIST]

---

### Post by fafhrd on 2009-06-16
I struggled with this, and figured I should post a solution for posterity.

First, you get an error like the above.  In my case, it was complaing about "DFP-1" (the second monitor) that I had unplugged (using the nvidia-settings tool!!!), and now it was complaining when I wanted to get another monitor attached.

You need to use nvidia-settings on the command line to tell the server that the second monitor is removed.  So, if you query now, using the -d option to see human readable output, you see something like:
```
$ nvidia-settings -d -q AssociatedDisplays

  Attribute 'AssociatedDisplays' (lornvelpa:0.0): DFP-0, DFP-1.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.
```
... using non-human readable output, we see:
```
$ nvidia-settings -q AssociatedDisplays

  Attribute 'AssociatedDisplays' (lornvelpa:0.0): 0x00030000.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.

```
Note that the hexadecimal setting for the connected displays (plural) is 0x00030000.

So, we simply need to tell it that, yes, DFP-1 was actually removed.
```
$ nvidia-settings -a AssociatedDisplays=0x00010000
$ nvidia-settings -d -q AssociatedDisplays

  Attribute 'AssociatedDisplays' (lornvelpa:0.0): DFP-0.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.

```

Voila!  This has bugged me greatly over the years (all my laptops have had NVIDIA cards...), and I finally got into a situation where leaving X was simply not acceptable.

After the above, you can use nvidia-settings in GUI mode to reconfigure the monitor layout.

Also, your mileage may vary on the correct hexadecimal number to use.  If it's CRT-0 or 1, for e.g, that was connected, the erroneous hexadecimal number that represents both monitors might look different.  However, there's a really good chance that DFP-0 (the laptop LCD) is always 0x00010000 when alone -- but be careful.

---

### Post by rockorequin on 2009-09-09
Thanks for the info, but it's not working for me. I have DFP-0 and DFP-1 plugged in at the moment. CRT-0 was plugged in yesterday and I was able to use nvidia-settings this morning to enable DFP-1, but now I just get the error about the missing CRT-0 ("Failed to find display device 0x00000001 on screen 0 (on GPU-0) while parsing metamode: 'CRT-0: nvidia-auto-select...'").

Unfortunately, resetting the associated displays to only DFP-0 using the nvidia-settings -a command doesn't help.

Is there a way of clearing the metamodes? (Wouldn't it be great if nvidia-settings did this automatically?!)

FWIW, I'm using Jaunty with 2.6.31 and nvidia version 190.32.

---

### Post by wojox on 2009-09-09
Try resetting by:

```
gksudo nvidia-settings
```

---

### Post by rockorequin on 2009-09-14
> **wojox said:**
> Try resetting by:

```
gksudo nvidia-settings
```

I tried that, and no luck:

root@pegasus-jaunty:~# nvidia-settings -a AssociatedDisplays=0x00010000

  Attribute 'AssociatedDisplays' (pegasus-jaunty:0.0) assigned value 65536.

root@pegasus-jaunty:~# nvidia-settings -d -q AssociatedDisplays

  Attribute 'AssociatedDisplays' (pegasus-jaunty:0.0): DFP-0.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.

root@pegasus-jaunty:~# nvidia-settings

ERROR: Failed to find display device 0x00020000 on screen 0 (on GPU-0)
       while parsing metamode:
       'DFP-1: nvidia-auto-select @1680x1050 +1680+0'

ie the command nvidia-settings -a *seems* to be working, but nvidia-settings still thinks there is a display on the screen.

---

### Post by rockorequin on 2009-09-21
I think it's a bug in nvidia-settings. If I disable the VGA display before suspending, I can run nvidia-settings once I've switched over to the flat panel and enable it (and vice versa). But if I just suspend with the monitor enabled and resume without it plugged in, I need to restart X to run nvidia-settings.

---

### Post by eternacho on 2010-01-28
I solved it unpluging the TV, running nvidia-settings, pluging it and "Detecting Displays".

---

### Post by rockorequin on 2010-01-31
The problem I have is that once nvidia-settings runs into this problem, it doesn't display the X Server Display Configuration, so there is no 'Detect Displays' button. This is whether I unplug the devices from the HDMI/VGA port or not. So I have to restart X.

---

### Post by gradinaruvasile on 2010-01-31
Try installing the latest (195.30) drivers from Nvidia's site.

---

### Post by rockorequin on 2010-01-31
I've been using the 195.30 driver for some time now, and I've seen the problem occur with it.

Generally speaking, if I remember to unplug the monitor, use the "Detect Monitors" button, and approve removing the display that is no longer found, when I resume with a new monitor plugged in I'm *usually* able to use the "Detect Monitors" button to discover the new monitor. But it doesn't always work.

---

### Post by freeware.preacher on 2010-08-20
Worked for me! Thanks!

---

### Post by arsenix on 2011-01-06
I had been wrangling with this issue for a long time and this thread inspired me to poke into it some more, although the original solution didn't work for me.

This remains a bug in nvidia-settings... since it aborts operation when it finds a metamode with a non-enabled screen.

Anyways... the way I got around it was by compiling and using some of the command line sample programs that come with the nvidia-settings source.

I installed the nvidia-settings source using directions from this thread:
[http://ubuntuforums.org/showthread.php?t=922956](http://ubuntuforums.org/showthread.php?t=922956)

Once you have these compiled, the nv-control-dpy program can be used to manipulate the attached/enabled screens.

For instance, if I just reconnected my second display I run:
nv-control-dpy --probe-dpys
nv-control-dpy --set-associated-dpys 0x30000

This will re-enable DFP-1, and allow nvidia-settings to run properly again.


I reported this as a bug to nvidia many years ago but apparently they have never thought it important enough to fix...


James

---

