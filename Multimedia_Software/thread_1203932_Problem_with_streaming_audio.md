---
title: "Problem with streaming audio"
date: 2009-07-04
forum: Multimedia Software
---

### Post by wwnliu on 2009-07-04
Dear all,

My ubuntu system used to play streaming audio fine. But starting from a week ago, I can't play streaming audio with any of the software on my computer (firefox plugin, gnome player, exaile).

I wonder is there any other people experienced that before? Any one knows the cause of the problem?

Please help.

This is the terminal output:

```
Last playlist loaded
Loading page 1
Traceback (most recent call last):
  File "/usr/share/exaile/xl/gui/main.py", line 1241, in as_play_track
    int(track.duration), track.track)
  File "/usr/share/exaile/lib/scrobbler.py", line 149, in now_playing
    raise AuthError("Please 'login()' first. (No session available)")
lib.scrobbler.AuthError: Please 'login()' first. (No session available)
<gst.Message GstMessageError, gerror=(GstGError)(NULL), debug=(string)"gstmms.c\(464\):\ gst_mms_start\ \(\):\ /GstPlayBin:playbin0/GstMMS:source"; from source at 0x98ed8c0> ['__class__', '__cmp__', '__delattr__', '__dict__', '__doc__', '__format__', '__getattribute__', '__grefcount__', '__gstminiobject_init__', '__gtype__', '__hash__', '__init__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'copy', 'flags', 'parse_async_start', 'parse_buffering', 'parse_clock_lost', 'parse_clock_provide', 'parse_duration', 'parse_error', 'parse_info', 'parse_new_clock', 'parse_segment_done', 'parse_segment_start', 'parse_state_changed', 'parse_tag', 'parse_warning', 'set_buffering_stats', 'set_seqnum', 'src', 'structure', 'timestamp', 'type']
ReplayGain support initialized.
Not using Equalizer disabled by the user

```

---

### Post by wwnliu on 2009-07-26
Anyone can help here?

---

