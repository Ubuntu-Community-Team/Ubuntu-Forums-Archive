---
title: "Restart song in Banshee using multimedia keys"
date: 2010-01-05
forum: Multimedia Software
---

### Post by bala on 2010-01-05
Is there way I can restart the current playing song (instead of playing previous one) using multimedia keys(in Banshee)? It works perfectly in Rhythmbox, but in Banshee it always previous song. 

When I check banshee command line help, it says "--previous Play the previous track, optionally restarting if the 'restart' value is set". Where can I find this "restart" setting?

---

### Post by boombox1387 on 2010-01-07
Generally, Banshee will jump to the previous song if the current song has been playing for less than 3 seconds or so; if it's been playing for longer than that, Banshee will restart the current song.  This works as expected when you click the "Previous" button in Banshee and when you use Banshee's shortcut ('B'), but you're right, for some reason it doesn't work when you use the multimedia keys on a keyboard.

I'd recommend filing a bug in [Banshee's bug tracking system]("https://bugzilla.gnome.org/browse.cgi?product=banshee").  You'll probably want to search first, but I don't remember seeing a report for this issue.

---

### Post by jamesisin on 2011-08-05
I am working on a script for controlling Banshee.  I can't get --previous to ever do anything but restart the current track.  Perhaps you have something useful to add to this problem?

---

