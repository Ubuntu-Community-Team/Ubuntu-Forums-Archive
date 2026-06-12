---
title: "[SOLVED] Video playback and thumbnails broken"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by puffyzacd on 2007-11-24
Hey all,

I'm experiencing a strange problem with my Gutsy install. Sometime last week video playback stopped working in all players I've tried (but VLC player works fine). Also, I've noticed no new video thumbnails are being generated.

When I open files I get errors like "Video codec 'XviD' is not handled". I have removed and reinstalled the required codecs several times to no avail.  :(

Does anyone have any ideas?

Cheers,

-Zac

---

### Post by puffyzacd on 2007-11-25
bump

Because as much as I like VLC player, I miss having a choice of media players and I miss my thumbnails!!

I don't want to have to reinstall!

---

### Post by deruberhanyok on 2007-11-25
Did you make any changes to the system? Manually trying to compile/install gstreamer plugins or anything like that?

---

### Post by puffyzacd on 2007-11-26
I was able to narrow the window of time when the problem started occurring down the day by looking at which thumbnails were properly created and which weren't.

As far as I know, the only change that I made during that time was that I uninstalled totem-mozilla. I've reinstalled it now, but I haven't recovered my ability to play video files.

Is there anywhere else I can look for logs that will show what changes were made to the system (other than the "History" menu in Synaptic)?

Thank you very much for your help with this!

---

### Post by deruberhanyok on 2007-11-27
Hmm, the mozilla totem plugin shouldn't have an effect on nautilus (the gnome file browser)... that's odd. Maybe it made changes to totem when it was removed.

I saw you mentioned you tried reinstalling codecs and the plugin... have you tried reinstalling the main totem player?

I think history in synaptic is the only place to check for changes, but it will only list changes that have been done using that app; if you manually compiled/installed something it won't show there (I think).

---

### Post by puffyzacd on 2007-11-30
Thanks for your help, but I still haven't gotten to the bottom of this problem yet.

I tried reinstalling totem, totem-xine, and mplayer...I'm still not able to watch video files in any of them.

It seems like this is a codec problem and not a graphics problem (going by the error messages I'm receiving and the fact that VLC works just fine)--is there a way to rebuild all the parts of my system that deal with codecs?

Sorry, I'm not exactly an expert with this sort of thing...thanks for your help and patience. :)

---

### Post by puffyzacd on 2007-11-30
It looks like I've managed to resolve my problem.

I uninstalled everything that seemed to be video related (all players and codecs) and then **manually deleted** the relevant hidden folders in my home directory (.mplayer, .xine, .gstreamer, etc.).

After this I just did
```
rm ~/.thumbnails/fail/gnome-thumbnail-factory/*
killall -9 nautilus
```
to refresh the thumbnails and voila! Video playback works as well.

Not sure what was the culprit in the end, but I'm just glad to have video back! Thanks for your help with this issue!

Cheers,

-Zac

---

