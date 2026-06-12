---
title: "Does Rhythmbox support scrobbling iPods?"
date: 2008-05-09
forum: Multimedia Software
---

### Post by Pichu0102 on 2008-05-09
As in, can I scrobble last.fm plays to last.fm with it?

---

### Post by Glucklich on 2008-05-09
I don't know about that scrobbling thing, but iPod is fully supported by Rhythmbox. At least I have no complain about it.

---

### Post by eaidoido on 2009-02-07
it appears that rhythmbox has scrobbled my ipod's most recent plays in that the sequence of my last tracks scrobbled matches that of the last tracks i played. good job.

8.04

---

### Post by harrykar on 2009-03-16
> **Pichu0102 said:**
> As in, can I scrobble last.fm plays to last.fm with it?

Not scrobble for me :( in Interid & rythmbox v.0.11.6

---

### Post by tom957 on 2010-02-23
Does anyone have issues with the timestamp being off by many hours? I was looking for the location of the plugin, but no luck. Any ideas?

---

### Post by ranea on 2011-01-27
I used to have no problem and now it doesn't scrobble anymore.
I tried running debug mode
```
rhythmbox -D audioscrobbler &> rhythmbox-audioscrobbler.txt
```
and I get the following (last few lines, not full file):
```
(17:59:37) [0xd29040] [rb_audioscrobbler_perform] rb-audioscrobbler.c:696: Submitting to Audioscrobbler: (...)
(17:59:38) [0xd29040] [rb_audioscrobbler_nowplaying_cb] rb-audioscrobbler.c:1366: Now playing response
(17:59:38) [0xd29040] [rb_audioscrobbler_parse_response] rb-audioscrobbler.c:613: Parsing response, status=200 Reason: OK
(17:59:38) [0xd29040] [rb_audioscrobbler_parse_response] rb-audioscrobbler.c:629: OK
(17:59:38) [0xd29040] [rb_audioscrobbler_nowplaying_cb] rb-audioscrobbler.c:1370: Submission success!
(17:59:38) [0xd29040] [rb_audioscrobbler_submit_queue_cb] rb-audioscrobbler.c:904: Submission response
(17:59:38) [0xd29040] [rb_audioscrobbler_parse_response] rb-audioscrobbler.c:613: Parsing response, status=200 Reason: OK
(17:59:38) [0xd29040] [rb_audioscrobbler_parse_response] rb-audioscrobbler.c:629: OK
(17:59:38) [0xd29040] [rb_audioscrobbler_submit_queue_cb] rb-audioscrobbler.c:908: Queue submitted successfully
```
also, searched the full launchpad site and found no reported bugs about this.
does anyone have the same problem?

---

