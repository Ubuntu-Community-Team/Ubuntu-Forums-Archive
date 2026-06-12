---
title: "Music player with parametric equalizer"
date: 2011-11-02
forum: Multimedia Software
---

### Post by Lysander10 on 2011-11-02
I'm looking for a music player for Linux that has the following features (in this order of importance, and does not require WINE):
[LIST=1]
[*]Parametric equalizer
[*]Savable equalizer profiles 
[*]Cross-feed
[*]Music library management
[*]Dithering
[/LIST]

If you're familiar with Rockbox, I'm looking for something similar to that. I don't care if it supports these features natively or through plugins, or if I have to download and compile it from Source Forge, etc. Please let me know if any player exists that has these features. Thanks!

---

### Post by &#1048;&#1075;&#1086;&#1088; on 2011-11-02
I do not know what is RockBox, but... try VLC...

---

### Post by Lysander10 on 2011-11-02
[Rockbox]("http://www.rockbox.org/") is a replacement, open source PMP firmware that has the features I'm looking for. Unfortunately, I don't think it can be run (easily) under Linux.

VLC does have an equalizer, but it doesn't look like it's parametric. It also doesn't support music library management.

---

### Post by Lysander10 on 2011-11-02
Update: It looks like Aqualung supports parametric equalization through the LADSPA framework. However, it does not include a library manager. Is there a music player with a library manager that uses LADSPA?

---

### Post by ajgreeny on 2011-11-02
Audacious can use LADSPA plugins, but I don't think it has an parametric equalizer, unless there is another plugin that I don't have.  Its own equalizer is reasonable, but I can't compare it with others, as I have seldom used the equalizer in it.

---

### Post by Lysander10 on 2011-11-02
Thank you! I have spent all day looking for a music player that has a parametric equalizer. There is indeed a LADSPA plugin for this; it's called "Triple band parametric with shelves". It comes included in the standard Ubuntu package (at least it does in 10.10).

---

### Post by Lysander10 on 2011-11-02
It appears that I was mistaken: there is a LADSPA parametric equalizer plugin, but you have to install the "fil-plugins" package to use it.

---

### Post by hitchhiker4242 on 2011-11-11
Ok, I installed fil-plugins, but how do you make it show up in Audacious and use it? Thanks.

---

### Post by Lysander10 on 2011-11-11
Yeah, it's hidden pretty well, isn't it? Open Audacious, go to File >> Preferences, and select "Plugins" from the menu on the left. Then select the "Effects" tab, find "LADSPA host" from the menu, select it, make sure it's checked, and click on "Preferences". Search through the menu that pops up for "Triple band parametric with shelves", select it, and click "Add". You can then configure the parametric equalizer from this menu.

---

### Post by Lysander10 on 2011-11-11
I'd also like to say that I was wrong about Aqualung - it does have a music library manager; the interface is just unintuitive. But it has a lot of great features for audiophiles, and I've come to prefer it to Audacity. Here is how to use the parametric equalizer from fil-plugins in Aqualung:

Select FX (the LADSPA patch builder) from the main menu. In the menu that pops up, scroll down to "Triple band parametric with shelves", and add it to the list of running plugins. You can then select it from the running plugins list and click "Configure" to adjust the parametric equalizer.

---

### Post by maxoud on 2012-10-27
> **Lysander10 said:**
> VLC does have an equalizer, but it doesn't look like it's parametric.
VLC does have parametric equalizer since v1.1.0 RC.
Tools->Preferences->Show All Settings->Audio->Filters->Parametric Equalizer

---

