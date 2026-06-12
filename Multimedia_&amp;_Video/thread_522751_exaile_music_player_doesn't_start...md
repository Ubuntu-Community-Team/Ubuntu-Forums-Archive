---
title: "exaile music player doesn't start.."
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by sunshine12 on 2007-08-11
Installed exaile right now. But when I start exaile, it doesn't start..
typed in terminal, showed the following error..

Traceback (most recent call last):
  File "/usr/share/exaile/xl/xlmisc.py", line 36, in <module>
    from xl import mozembed
  File "/usr/share/exaile/xl/mozembed.py", line 29, in <module>
    import gtkmozembed
ImportError: No module named gtkmozembed
Traceback (most recent call last):
  File "exaile.py", line 2635, in <module>
    main()
  File "exaile.py", line 2627, in main
    exaile = ExaileWindow(options, fr)
  File "exaile.py", line 148, in __init__
    self.player = player.ExailePlayer(self)
  File "/usr/share/exaile/xl/player.py", line 460, in __init__
    GSTPlayer.__init__(self)
  File "/usr/share/exaile/xl/player.py", line 254, in __init__
    self.setup_playbin()
  File "/usr/share/exaile/xl/player.py", line 573, in setup_playbin
    GSTPlayer.setup_playbin(self)
  File "/usr/share/exaile/xl/player.py", line 257, in setup_playbin
    self.playbin = gst.element_factory_make('playbin')
PluginNotFoundError: playbin


What is the problem? and how to start it?
please help
thanks

---

### Post by sunshine12 on 2007-08-11
all dependancies installed, still not able to start it..
can anyone facing the same problem?

---

### Post by sunshine12 on 2007-08-11
can anybody help please.. 
waiting for the reply
thanks

---

### Post by sunshine12 on 2007-08-11
Solved Problem..

installing two packages solved the problem in xubuntu,

> sudo apt-get install python-gnome2-extras
sudo apt-get install gstreamer0.10-plugins-base

thanks

---

### Post by phenest on 2007-11-12
Same error here in Ubuntu 7.10. It worked ok when I first installed it, but then I installed the latest from Exaile's website. That worked until I restarted. Hasn't worked since and this fix doesn't work.

---

### Post by zanglang on 2007-11-12
> **phenest said:**
> Same error here in Ubuntu 7.10. It worked ok when I first installed it, but then I installed the latest from Exaile's website. That worked until I restarted. Hasn't worked since and this fix doesn't work.

Are you getting the same error message as above when you run 'exaile' from a terminal?

---

### Post by phenest on 2007-11-12
The exact same error.

---

### Post by zanglang on 2007-11-12
Odd, gstreamer0.10-plugin-base should have the playbin plugin.
Try this:
```
sudo apt-get install gstreamer0.10-*
```
You may need to reboot.

---

### Post by phenest on 2007-11-12
No change. I had also downloaded, compiled, and installed the latest gstreamer base from their site. This was in a vain effort to fix the equalizer problem. I guess that is what's causing it?

---

