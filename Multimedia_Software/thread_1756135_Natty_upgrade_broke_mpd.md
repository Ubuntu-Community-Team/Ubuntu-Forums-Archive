---
title: "Natty upgrade broke mpd"
date: 2011-05-11
forum: Multimedia Software
---

### Post by ashwinjm on 2011-05-11
So after my Natty upgrade, mpd stopped working. All I can see in the logs are the following lines:
----------------------------------------
No protocol specified
xcb_connection_has_error() returned true
----------------------------------------
The Pulse Audio wiki suggests that this might be an access rights problem:
[http://mpd.wikia.com/wiki/PulseAudio#For_Distros_where_PulseAudio_access_rights_are_broken](http://mpd.wikia.com/wiki/PulseAudio#For_Distros_where_PulseAudio_access_rights_are_broken)
I tried that, but with no success.

Anyone else had this problem? And any ideas about how I can diagnose and fix this?

---

### Post by vanadium on 2011-05-21
I confirm the problem. Sometimes its working, sometimes not. Today I started Sonata to see that it would not work (there was connection, but pressing "Play" did not play the song. At some point, Sonata would disconnect). My /var/log/mpd/mpd.log would contain the same two lines.

Now it is working after changing the port back to the default in the mpd config file, and restarting mpd (sudo /etc/init.d/mpd restart), but I do not know what it is going to be next time.

---

