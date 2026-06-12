---
title: "Gnome Panel broken with latest updates?"
date: 2010-06-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Arla on 2010-06-17
Has anyone else had issues with the gnome panel, I'm seeing double viewing of wireless, battery, and bluetooth indicators, one set works, the other just appears to be a graphic problem.

I had to add a shutdown button to the panel since it was so messed up last time I booted that the shutdown button wasn't accepting selections.

---

### Post by wilee-nilee on 2010-06-17
You probably added a extra notification area from add to panel, or you can at least remove one.

---

### Post by mick222 on 2010-06-17
Recently I lost my volume control from the panel think I messed it up myself though. I tried adding notification area to panel which messed it up more. How do I remove The notification area It so that I have only one and reset the volume control on panel.
Wont be able to reply as I'm going to work just now.

---

### Post by wilee-nilee on 2010-06-17
First to the op I don't think the applets are part of the notification actually. I remove those as I don't use evolution and I don't like the volume control.

To the volume question go to start up application put a new one in  and in the command ```
gnome-volume-control-applet
```

Then restart/logout the desktop or reboot it will be there every time.

---

### Post by Deadite81 on 2010-06-17
I have similar problems sometimes at boot time.  Running the command
```
killall gnome-panel
```
will restart your panel(s).  Usually I have to run this command around once every 10 boots because everything is duplicated in the Indicator Applet and the Indicator Session Applet.


If this happens every time you boot no matter what, perhaps you should try deleting the panel and reconfiguring a new one.

Also, you say
> Recently I lost my volume control from the panel think I messed it up  myself though.

How?  What in particular did you do?  Are you using Ubuntu 10.04?

---

### Post by Nr90 on 2010-06-17
I haven't seen volume control in my 10.10
Don't really mind but still...

---

### Post by Deadite81 on 2010-06-17
Really?  I wish I could get rid of mine!  I haven't looked too deeply into it, but I've gone as far as deleting the startup entry altogether in ~/.config/autostart.  I still appears merged to my indicator applet.  I am not a fan of having to have a systray AND a second systray like thing that makes me left click and then choose to show Transmission or Rhythmbox when I used to be able to left click to show and right click for the same menu.  Terrible.  Inefficient.  But I dig the messaging part, so...

I use the PulseAudio applet (which controls the volume of individual applications = awesome), and it's nonsense that I have to have 2 volume applets just to access my social media in a convenient way.

Sorry, that was a total rant.  Probably not the place.

Anyway, if you want a volume control applet, the PA applet is located [here]("http://code.google.com/p/gnome-pulse-applet/").
Download the .deb applicable to your system and double-click to install.  There is mention of a "next generation" applet on this page, but you have to compile it and I could not get it to work.  The applet is quite old, but has worked for me on 9.10 and is working now on 10.04.  Here's a picture.  Ok bye.

---

### Post by Deadite81 on 2010-06-17
After some investigation I have learned what controls the volume applet displayed as part of the indicator applet.

There are apparently no configuration options, in gconf editor or anywhere else.  You actually have to install/uninstall an entire package, which is crappy.  This is a design flaw in my opinion.

Anyway, the package is "indicator-sound" and can be installed by running this in a terminal:
```
sudo apt-get install indicator-sound
```
and likewise it can be removed with:
```
sudo apt-get remove indicator-sound
```
You can also add/remove many other aspects of the applet, just search for "indicator" in Synaptic.  So that may be your solution Nr90.

---

### Post by Nr90 on 2010-06-17
Thanks for the tip,
I don't actually use it, but it's good to know how to get it back in case I do want it there.

---

### Post by Arla on 2010-06-17
> **wilee-nilee said:**
> You probably added a extra notification area from add to panel, or you can at least remove one.

Would be nice if that was the case, but no, it's not.

I still only have one notification area, it just has double icons in it (and half of them can be used, and half can't).

I've had other issues playing around some (my name was duplicated over the shutdown button at one point and I couldn't use the shutdown button) will play some more today.

---

### Post by Arla on 2010-06-17
So booting into 10.10 as of this morning, this is what I get,

Note the duplicated bluetooth icon, but lack of wireless icon, and the date/time duplicated over both my name and the normal shutdown button.

running $ killall gnome-panel did seem to resolve it (at least for now) but it will be a pain to have to do that every single boot (but we are in testing).

---

### Post by mick222 on 2010-06-20
> **wilee-nilee said:**
> First to the op I don't think the applets are part of the notification actually. I remove those as I don't use evolution and I don't like the volume control.

To the volume question go to start up application put a new one in  and in the command ```
gnome-volume-control-applet
```

Then restart/logout the desktop or reboot it will be there every time.

Thx that got me the volume control but it's the old one from Karmic not the plain white one.Seems  it has been changed in Maverick also tried reinstalling the notification area which didn't work.

---

### Post by null_pointer_us on 2010-06-20
Someone posted this a while ago:

```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

The first command reverts your panel settings to their default values and the second command kills and restarts the gnome-panel process.

---

### Post by mick222 on 2010-06-20
> **null_pointer_us said:**
> Someone posted this a while ago:

```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

The first command reverts your panel settings to their default values and the second command kills and restarts the gnome-panel process.

thx that worked Probably the bug so I'll see if it returns

---

### Post by crjackson on 2010-06-21
> **Arla said:**
> So booting into 10.10 as of this morning, this is what I get,

Note the duplicated bluetooth icon, but lack of wireless icon, and the date/time duplicated over both my name and the normal shutdown button.

running $ killall gnome-panel did seem to resolve it (at least for now) but it will be a pain to have to do that every single boot (but we are in testing).

It's a real PIA for me too.  This happens on all of my Lucid machines as well.

---

### Post by tokyobadger on 2010-06-22
Latest updates cleared things for me. Previously the power management indicator would show up (on this desktop). Removing it would take out the volume indicator and remove weather from the date/time indicator.

Haven't been hit by that mute-at-boot issue reported elsewhere

---

