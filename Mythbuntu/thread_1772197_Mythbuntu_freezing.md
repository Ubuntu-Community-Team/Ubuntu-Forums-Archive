---
title: "Mythbuntu freezing"
date: 2011-05-31
forum: Mythbuntu
---

### Post by sqeelurgle on 2011-05-31
OK,longstory, so here goes.

I had a mythbuntu 9.10 box.  There were some issues with it, so I upgraded to 10.04, by doing a complete reinstall.  

I then needed to upgrade to kernel 2.6.33 in order to have the driver for my tuner cards.

I was getting major video problems, because there was an ATI video card in there.  It never gave me any trouble on the 9.10 box, but under 10.04 the driver didn't work properly, and the AGP slot was run in PCI mode and was veeeery slow.  

I replaced the video card with an Nvidia card.  Couldn't boot to X at all so used another computer to download drivers from the nvidia site and installed them manually (version 270).  That allowed me to boot up, but there were random freezes.  I therefore used Synaptic to install the current ubuntu supported ones.  (195)  Still freezes randomly.  I found kernel version 2.6.35 in synaptic, and installed that, in case a newer kernel solved the problem.  Nothing.

The only thing I have found in logs is this:

(polkit-gnome-authentication-agent-1:1417): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1417): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

Seems to appear in .xsession-error and stdout at about the time of the freeze, but I can't seem to find much about what (if anything) it means or how to solve the problem.

Help please!

---

### Post by klc5555 on 2011-05-31
Sounds mostly like thermal lockups of some sort.

When I still used AGP cards, my installation was tight enough space-wise that I would frequently have thermal lockups using a fanless NVidia 6200. (PC freezes with last image on screen; no keyboard or SSH; have to do hard reset.) As there was no space in the small gaming case for still another case fan, I had to switch to an NVidia 7400 AGP card that had a standard fan on the GPU, and that solved the problem for as long as that particular motherboard lasted. 

From time to time, particularly when hotter-running AMD CPUs would start to randomly lock up, I'd have to clean the dust and gook out of the CPU heat sink, which over time would act like a thermal blanket and prevent warm air from escaping to the CPU fan.  

So check your cpu/case temps periodically, and also immediately after a lockup by going into the hardware bios at reboot. If you notice excessive temps somewhere, you may have to adjust your PCI card layout a bit to maximize airfow, arrange for better cooling of the case, GPU, or mem simms; and/or do a cleaning of CPU heat sink. 

You can also try the experiment of popping the top on your case and letting the machine run uncovered for a while, to see whether the lockups become less frequent or even disappear. If they do, then you know you've got it.

It may end up being something non-thermal, but that's the place to start looking.

---

### Post by sqeelurgle on 2011-05-31
The symptoms you describe are exactly what I am getting, and I have just installed a fanless Nvidia 6200 (I wanted fanless because I had a fan cooled one in there ages ago, and it was way too noisy for home theatre).  I'll try it with the case open for a while and see what happens - thanks.

---

### Post by sqeelurgle on 2011-06-02
OK, I am now running my box with the side off.  It's a full size desktop tower case, and the video card has a spare slot next to it.  Anyway, it's still freezing.  Tonight it had been on for a while recording, and then it froze within 2 minutes of starting to watch an HD video.  I did a hard reset, and it booted fine.  I was able to watch 30 mins of the same video with no trouble.  Then watched 2 hours of an SD video.  It then froze while on the X desktop, running firefox.  The page stopped loading, and the page woudn't scroll (I was looking at a launchpad bug report page, so no fancy flash or anything).  Th escreen wasn't totally locked, as the mouse cursor could still be moved around the screen, but it didn't change the way it does to indicate clickable links etc, and the keyboard also didn't work.  The hard drive light was flashing occasionally, indicating that the backend server was still running and recording, so the whole thing wasn't locked up completely.

Any ideas?

Thanks

---

### Post by klc5555 on 2011-06-02
Well, it may not be thermal. Though you'd still want to reboot immediately after a lockup go into the hardware bios and check the temperature to be sure. AMD Athlons and similar CPUs begin locking at 95-100 degrees C or so, and most are generally supposed to be run at 90 degrees or below. Intels are supposed to be kept cooler -- except for things like hot running Pentium Ms, most are supposed to be kept below about 80 degrees C.

I don't think it's another hardware problem like failing memory or things like power supply issues that imitate failing memory: these issues would tend to cause spontaneous reboots, not lockups. Though the old specs for the 6200 recommend at least a 300W power supply, I don't know how the system reacts if the power needs of the 6200 are not met.

The problem should not be Nvidia drivers for the 6200 --I know the card works with drivers at least as late as the 255. series. But you could test this on your machine by restoring the open-source NVidia driver (nouveau or nv, as the case may be), and then running the machine normally but watching only SD content to see whether the machine locks.

If hardware seems to be ruled out, then it's a shot in the dark. But you asked for ideas, so here goes. 

In a similar circumstance on my own equipment, I'd be prone to take the highly unsupported step of reinstalling 9.10 and compiling a set of tuner drivers from V4L-DVB source at linuxtv.org to support your newer tuners. linuxtv's final Mercurial daily snapshot dates to last August, is therefore more recent than the kernel drivers in 2.6.33 (or 10.04), and is simpler to use than installing all the "Git" nonsense for the most recent V4L source. The problem would be that you would need to have saved a copy of your old mythconverg database, as the updated one from 10.04 will likely be useless. But if the older hardware in general runs better on 9.10, keep using it. If my family theater's motherboard hadn't fried, it would still be running 7.10.

On my own equipment I might also be inclined to take the less unsupported step of backing up the database, wiping and reinstalling 10.04, but keeping this install as close to plain-vanilla as possible rather than immediately doing kernel and Nvidia upgrades and downgrades and other 10.04 patching, to avoid any corruption of your installation of X that these sorts of activities may have introduced. At least until you have all the parts properly flying in formation together. You'd still need to compile a set of updated tuner drivers by hand. And, if the kernel is updated at some point, the home-compiled V4L drivers have to be recompiled and installed again.

Hopefully some other folk will have additional, better ideas.

---

### Post by sqeelurgle on 2011-06-11
I seem to have solved it.  I tried a lot of things.  I am convinced that somewhere in there is was a driver issue with the nvidia driver.  One thing is that I could reliably and deliberately freeze the system by loading a site form launchpad.net.  No idea what content loads last, but just when the progress bar was almost complete, it would freeze every time, no matter how long the computer had been on etc.  Anyway, I was considering backing and completely reinstalling but one step before I tried that was to reinstall my old ATI card, and use the xorg-edgers drivers instead of the standard open source ati drivers.  So far that seems to have fixed it.  Video performance is adequate (where it was VEEERRYYY slow with the standard open source drivers) and it hasn't frozen since.  I can even browse the lauchpad repository sites.  So, I haven't solved the problem of the system freezing with an nvidia card in it, but I have got a usable stable system, which is all I need.

---

