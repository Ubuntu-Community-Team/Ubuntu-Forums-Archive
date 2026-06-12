---
title: "ATSC-Recorded MPEG Playback Stutter -- But only 'internal' player!"
date: 2010-11-14
forum: Mythbuntu
---

### Post by davelindquist on 2010-11-14
I'm having a problem with playing back ATSC-recorded MPEGs (1080p) from Digital Broadcast...

Basically, if I:

a) Use mythfrontend, browse to Recordings, and try to playback the recording, I get stuttering -- about every 2-3 seconds, a brief 'hiccup'.

--BUT-- if I:

b) nfs-mount the recordings directory, and use mplayer to play back the mpeg, it plays flawlessly.

The recordings are on a separate backend server, with 100MB ethernet in between.

The frontend machine *is* kind of old (AMD 2600+).

I'd understand this if I had the same problem when trying 'manual' playback -- but why is it only with the myth-internal player?

I tried to find some documentation on the 'playback profiles', but no luck...

Can anyone give me something to look at?

TIA!

---

### Post by ian dobson on 2010-11-14
Hi,

What graphic card have you got? If it's an NVidia and is new enough have a look at enabling VDPAU.

Also, when watching a recording run TOP and see how the CPU load is, and have a look in the frontend log file /var/log/mythtv/mythfrontend.log.

Regards
Ian Dobson

---

### Post by nickrout on 2010-11-15
> **davelindquist said:**
> I'm having a problem with playing back ATSC-recorded MPEGs (1080p) from Digital Broadcast...

Basically, if I:

a) Use mythfrontend, browse to Recordings, and try to playback the recording, I get stuttering -- about every 2-3 seconds, a brief 'hiccup'.

--BUT-- if I:

b) nfs-mount the recordings directory, and use mplayer to play back the mpeg, it plays flawlessly.

The recordings are on a separate backend server, with 100MB ethernet in between.

The frontend machine *is* kind of old (AMD 2600+).

I'd understand this if I had the same problem when trying 'manual' playback -- but why is it only with the myth-internal player?

I tried to find some documentation on the 'playback profiles', but no luck...

Can anyone give me something to look at?

TIA!

I doubt that you are getting 1080p broadcasts anywhere in the world.

In any event, what does your log file say?

---

