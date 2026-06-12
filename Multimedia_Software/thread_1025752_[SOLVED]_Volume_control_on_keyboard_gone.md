---
title: "[SOLVED] Volume control on keyboard gone"
date: 2008-12-30
forum: Multimedia Software
---

### Post by ussndmac on 2008-12-30
Hi All,

I fooled with the alsamixer and the gnome-volume-control because the volume was low.

Afterward the 3 touch pads on the laptop key (icons of a speaker at low volume, high volume and muted) no longer do anything.

When they are touched a popup shows up and the bar moves (louder/softer) and the mute indicator comes on , but they have no effect on the output level.

Can anyone guess what I changed and help me get them working again?

Thanks,
Mac

---

### Post by ussndmac on 2008-12-30
After reading the info in this thread:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I installed gnome-alsamixer.

It shows the keyboard buttons controlling the first capture device...

I can't see any way to define what device they control...

---

### Post by ussndmac on 2008-12-30
As I continue to work this problem I keep finding more.

I now notice that sound from Audacious and the system sounds seem to come from the PCM device. But, the system sounds are way loud when the Audacious levels are at normal listening levels...

Is there a way to change the system sounds independently?

Regards,
Mac

---

### Post by xc3RnbFO8P on 2008-12-30
Did you enable Master in Volume Control?

---

### Post by ussndmac on 2008-12-30
Yes the master is enabled...the various mixers control volume.

It's only the volume control pads on the laptop keyboard that have changed. They now control the level of capture0 and that appears to be an input. It should be the master no?

And the system sounds are much louder than other sources.

---

### Post by ussndmac on 2008-12-31
Ok, so does anyone know where the connection between the hardware control sound controls (the keyboard) and the device they control is made?

And, is there documentation on how it works?

I haven't found the appropriate search terms I guess.

---

### Post by xc3RnbFO8P on 2008-12-31
You have to give more information about your computer.

---

### Post by ussndmac on 2009-01-03
I agree for a specific fix that is true.

But there must be a general structure that is used to define what happens when the hardware is present and the button is pushed. I'm guessing the actual functionality is abstracted well above the physical switch.

Dell XPS 1530 laptop
Intel duo
Ubuntu Studio (64bit)

Please, let me know what other details are needed.

Thanks,
Mac

---

### Post by namdung on 2009-01-03
In *System==>Pref==>Sound*, ensure that **Master** is selected for *Default Mixer Tracks==>ALSA Mixer*

---

### Post by ussndmac on 2009-01-04
> **namdung said:**
> In *System==>Pref==>Sound*, ensure that **Master** is selected for *Default Mixer Tracks==>ALSA Mixer*

Thanks namdung.

That corrected the issue and I have marked this thread solved.

But, even after all the reading I've done on ALSA, Pulseaudio, and jack over the last few days the sound structure is way confusing, trying to keep inputs, outputs, sinks, sources, servers, deamons, helpers, and more straight.

I am going to attempt to make a diagram for my own purposes. Is there a way or place to keep graphics with posts?

Regards,
Mac

---

### Post by Keith_Beef on 2009-01-04
> **ussndmac said:**
> 
I am going to attempt to make a diagram for my own purposes. Is there a way or place to keep graphics with posts?

Take screenshots with either Applications -> Accessories -> Take Screenshot or with Gimp.

[LIST=1]
[*]Clean up the screenshots with Gimp.
[*]Upload your screenshots to Photobucket or similar image hosting site.
[*]Link to images using the Insert Image icon in the thread reply interface of Ubuntu Forums.
[/LIST]

So, here's an example of three screenshots done this way.

[LIST=1]
[*]Right click on the volume control icon in the panel. In the contextual menu that appears, select Open Volume Control.
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/screenshots/th_Screenshot-1.png[/IMG]](http://s71.photobucket.com/albums/i121/Keith_Beef/screenshots/?action=view&current=Screenshot-1.png)
[*]The Volume Control dialog appears.
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/screenshots/th_Screenshot-2.png[/IMG]](http://s71.photobucket.com/albums/i121/Keith_Beef/screenshots/?action=view&current=Screenshot-2.png)
[*]Make the screenshots and save them, following the three steps explained above.
[*]Use the Insert Image icon in the thread editor to add images to the thread.
[[IMG]http://i71.photobucket.com/albums/i121/Keith_Beef/screenshots/th_Screenshot-3.png[/IMG]](http://s71.photobucket.com/albums/i121/Keith_Beef/screenshots/?action=view&current=Screenshot-3.png)
[/LIST]

---

