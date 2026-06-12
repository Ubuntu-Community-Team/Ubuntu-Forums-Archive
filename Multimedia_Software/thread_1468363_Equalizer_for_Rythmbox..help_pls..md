---
title: "Equalizer for Rythmbox..help pls."
date: 2010-05-01
forum: Multimedia Software
---

### Post by sixthwheel on 2010-05-01
Is there a plugin in the repos for this?
I found a website that has it, but I would rather install from the repos if I can.

---

### Post by bark50 on 2010-05-01
I think the only Rhythmbox equalizer you'll find -- and the one I use in my Rhythmbox -- is at [http://www.lirmm.fr/~morandat/index.php/Main/Tools]("http://www.lirmm.fr/~morandat/index.php/Main/Tools")

---

### Post by sixthwheel on 2010-05-01
```
www.lirmm.fr/~morandat/pub/upload/Main/rb-equalizer.tar.bz2 -O- | tar xvjf - -C ~/.local/share/rhythmbox/plugins
--2010-05-01 12:29:26--  http://www.lirmm.fr/~morandat/pub/upload/Main/rb-equalizer.tar.bz2
Resolving www.lirmm.fr... 193.49.104.249
Connecting to www.lirmm.fr|193.49.104.249|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7223 (7.1K) [application/x-tar]
Saving to: `STDOUT'

100%[======================================>] 7,223       --.-K/s   in 0.1s    

2010-05-01 12:29:26 (49.2 KB/s) - written to stdout [7223/7223]

tar: Record size = 8 blocks
equalizer/.hg_archival.txt
equalizer/Conf.py
equalizer/ConfDialog.py
equalizer/__init__.py
equalizer/equalizer-prefs.glade
equalizer/equalizer-ui.xml
equalizer/equalizer.rb-plugin
equalizer/equalizer.svg
peter@peter-desktop:~$ 

```

This is my output, but it's not showing up in Rhythmbox.

---

### Post by 2hot6ft2 on 2010-05-01
This is where to get the 10 band EQ for Rythmbox and other plugins for it.
I don't believe it's in the repos.
[http://live.gnome.org/RhythmboxPlugins/ThirdParty](http://live.gnome.org/RhythmboxPlugins/ThirdParty)

---

### Post by sixthwheel on 2010-05-01
I got it. had to enable it in plugins. Thank You.

---

### Post by olive.ewe on 2010-05-03
> **2hot6ft2 said:**
> This is where to get the 10 band EQ for Rythmbox and other plugins for it.
I don't believe it's in the repos.
[http://live.gnome.org/RhythmboxPlugins/ThirdParty](http://live.gnome.org/RhythmboxPlugins/ThirdParty)

Ah, just what I was looking for, couldn't find one in repos. I've been using VLC for my music atm purely because of the very good equalizer it has but really dislike the basic access to my library which I find annoying for quickly getting to the tracks I wish (ofc vlc meant more for video) compared to the ease of access in Rythmbox

Is this a trustworthy enough source?, I hate to install anything from outside the repos unless perhaps linked in the official ubuntu documentation site

---

### Post by bark50 on 2010-05-03
> **olive.ewe said:**
> Ah, just what I was looking for, couldn't find one in repos. I've been using VLC for my music atm purely because of the very good equalizer it has but really dislike the basic access to my library which I find annoying for quickly getting to the tracks I wish (ofc vlc meant more for video) compared to the ease of access in Rythmbox

Is this a trustworthy enough source?, I hate to install anything from outside the repos unless perhaps linked in the official ubuntu documentation site

I've used the Rhythmbox equalizer with 9.10 and now with 10.04 without any problems.  And I've never read any complaints about it here on the forums.  But if you're looking for a music player/organizer with an equalizer that doesn't take you outside of the repositories, you might want to try Banshee, Listen, and gmusicbrowser.  Audacious has an equalizer also, but it doesn't organize your music.

---

### Post by Foxcow on 2010-05-11
This equilizer does not work very well on either of my systems.  On my desktop, RB would crash randomlly.  On both laptop and desktop, when I hit the equilizer button, a blank window would appear without and presets or the ability to change the sliders.  I might just stick with Songbird.

---

### Post by sjhaffner on 2010-11-20
> **bark50 said:**
> I think the only Rhythmbox equalizer you'll find -- and the one I use in my Rhythmbox -- is at [http://www.lirmm.fr/~morandat/index.php/Main/Tools]("http://www.lirmm.fr/%7Emorandat/index.php/Main/Tools")

This Equalizer is much better than the other one. I've tried both and like this one much better! =)

[http://code.google.com/p/rbeq/](http://code.google.com/p/rbeq/)

Hope this helps!

---

