---
title: "Strange GStreamer problems with Banshee"
date: 2010-09-04
forum: Multimedia Software
---

### Post by Natureshadow on 2010-09-04
Hi,

I recently switched from Rhythmbox to Banshee and am now experiencing problems with my FLAC collection.

Al the tracks in the database seem to be ok (well, Rhythmbox did not cough on them, using GStreamer as well) and Banshee plays all the files if I start playback manually. If it reaches a file automatically (one track has finished playback, and Banshee skips to the next track), chances are good it will catch a GStreamer error and stop playback, skipping the track in question.

The log looks like this:

```
nik@portux ~ % banshee
[Info  23:15:51.055] Running Banshee 1.6.1: [Ubuntu 10.04 LTS (linux-gnu, x86_64) @ 2010-06-18 18:47:49 UTC]
[Info  23:15:51.393] Starting collection of anonymous usage data
[Info  23:15:53.519] All services are started 2,227485
[Info  23:15:54.497] nereid Client Started
[Info  23:15:57.033] Uncached artwork size 175 requested
[Error 23:16:12.915] GStreamer stream error: Decode
[Info  23:16:13.715] Uncached artwork size 175 requested
[Error 23:16:17.316] GStreamer stream error: Decode
[Info  23:16:17.924] Uncached artwork size 175 requested
[Warn  23:16:31.468] Error posting metrics - System.Net.WebException: The request timed out (in `System')
  at System.Net.HttpWebRequest.EndGetResponse (IAsyncResult asyncResult) [0x00000] 
  at System.Net.HttpWebRequest.GetResponse () [0x00000] 
  at Hyena.Metrics.HttpPoster.Post () [0x00000] 
[Info  23:16:31.468] Posted usage data? False
[Info  23:21:12.900] Uncached artwork size 175 requested
[Warn  23:21:21.700] Audioscrobbler upload failed - The request timed out and was aborted
[Warn  23:21:21.700] Failed to get the request stream - System.Net.WebException: Aborted. (in `System')
  at System.Net.HttpWebRequest.EndGetRequestStream (IAsyncResult asyncResult) [0x00000] 
  at Lastfm.AudioscrobblerConnection.TransmitGetRequestStream (IAsyncResult ar) [0x00000] 
[Info  23:24:59.498] Uncached artwork size 175 requested
[Error 23:25:03.094] GStreamer stream error: Decode
[Info  23:25:03.853] Uncached artwork size 175 requested

```

This is annoying, and Banshee is the best GTK+ based meida player I've seen so far so I would really like to use it.

Does anyone have any idea o nthis?

Cheers,
Nik

---

### Post by lidex on 2010-09-05
Yeah, I wanted to like banshee but for some reason I dumped it for exaile. Had some issues with it I can't remember. Maybe you could try a ppa build and see if it works correctly.
[https://launchpad.net/~banshee-team/+archive/ppa](https://launchpad.net/~banshee-team/+archive/ppa)

---

### Post by Natureshadow on 2010-09-05
Switching to Exaile is not an option. I tried it yesterday, and its UI is awful.

But the PPA build is probably a good idea, I will try it in a few minutes ... however, I think this is more of a GStreamer issue - which does not make sense on the first sight, but after I saw a talk about GNOME 3 I am tempted to say nothing in GNOME makes sense anymore ;) ...

Cheers,
Nik

---

### Post by lidex on 2010-09-05
I'm pretty sure it's banshee. You said rhythmbox worked OK? There are a number of recent threads popping up with banshee issues. Or if you built your collection with r-box, maybe banshee implementation doesn't like it.

---

