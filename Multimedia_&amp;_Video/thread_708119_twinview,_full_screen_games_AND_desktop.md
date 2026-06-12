---
title: "twinview, full screen games AND desktop?"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by Wyld on 2008-02-26
Howdy all,

I have a question, arising from the topic.  I have a nice nvidia card, two 19" 1400x900 monitors, and am happy using both in (k)ubuntu.  However, I wish to nail the final issue I have with it.  In essence, I have a single 2880x900 screen, and I want to alter this in a couple of ways.

Firstly, I want the desktop to maximise a window to ONE monitor, not both.  Same as various popup windows, I would like them to appear on one (either) of the windows, not sharing space between the two within the virtual resolution.

Secondly, and the lead out, is ... is there a way to run a game in fullscreen in one monitor, and use the other one as a desktop?  Interactivity not withstanding, just being able to watch a video file, IRC, a web page, whatever.  Some method of NOT shutting down the secondary monitor, and allowing fullscreen gaming goodness to the other.

I've searched around for a good while now, seen a few dozen threads asking for help, a few that say things like "the solution is on the forums", but I have yet to actually find one of these elusive hidden beasts.  If some kind sole knows the answer, and can provide some pointers to a solution, that would be fantastic.

Regards,

W.

---

### Post by chewearn on 2008-02-26
I know of two ways to do this:
1. if you want to keep twinview, and have compiz fusion, the desktop cube plug-in allow you to "make" like it's two separate desktops, instead of one desktop spanning two monitor.

2. if you don't mind ditching twinview, use "separate X screen" option instead.  Then, there is truly two separate screens (one for each monitor); the downside of this option is you can't drag window/apps from one screen to the other.

Both options have good and bad points; you have to try it yourself to see which one you can live with.

---

### Post by Wyld on 2008-02-26
I have had some success with twinview and maximising a standard window (firefox, terminal, whatever) to one monitor, leaving the other monitor alone.  I suspect this was achievied via metamodes.  It was, however, on a opensuse box that no longer exists so I can't refer to it's settings.

I do suspect that a fullscreen game in one monitor may also follow this path.

---

### Post by cheema on 2008-03-24
I had to add the metamodes line to my xorg.conf to do this:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    # Option         "metamodes" "DFP-0: nvidia-auto-select +2560+0, DFP-1: nvidia-auto-select +0+0"
    Option         "metamodes" "DFP-0: 1920x1200 +2560+0, DFP-1: 2560x1600 +0+0"
EndSection

```

---

