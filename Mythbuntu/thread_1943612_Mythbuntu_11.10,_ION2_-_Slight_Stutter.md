---
title: "Mythbuntu 11.10, ION2 - Slight Stutter"
date: 2012-03-19
forum: Mythbuntu
---

### Post by tobiz on 2012-03-19
I've finally got my Atom 525, ION2 m/b running into my Marantz 5002 AV amp running mythbuntu 0.24 (11.10) for HDMI video and 7.1 sound.  But when using mythtv for HD live or recorded material I get a slight audio and video stutter, more an infrequent 'glitch' (it may be present even when myth is not running). Xorg.conf has composite disabled, compiz is not installed, mythtv has VPDAU high quality enabled. I've tried most things without success. Has anyone else had this and if so managed to solve it? My next step is to upgrade to the very latest nvidia driver, 295.20 but it doesn't mention any fixes for such symptoms.

---

### Post by nickrout on 2012-03-20
> **tobiz said:**
> I've finally got my Atom 525, ION2 m/b running into my Marantz 5002 AV amp running mythbuntu 0.24 (11.10) for HDMI video and 7.1 sound.  But when using mythtv for HD live or recorded material I get a slight audio and video stutter, more an infrequent 'glitch' (it may be present even when myth is not running). Xorg.conf has composite disabled, compiz is not installed, mythtv has VPDAU high quality enabled. I've tried most things without success. Has anyone else had this and if so managed to solve it? My next step is to upgrade to the very latest nvidia driver, 295.20 but it doesn't mention any fixes for such symptoms.

Are there any revealing entries in your frontend log when the glitch appears?

---

### Post by tobiz on 2012-03-20
Attached is the last mythfrontend.log when the audio/video 'glitches' were happening. I'll try and produce a new log and give (approx) times when the glitches happen.

Entries such as the following look strange but may be ok:
"2012-03-19 23:16:38.551 RingBuf(/var/lib/mythtv/livetv/1050_20120319231637.mpg) Warning: Not starting read ahead thread, already running
2012-03-19 23:16:38.739 Player(3): Forcing decode extra audio option on (Video method requires it).
2012-03-19 23:16:38.922 [h264 @ 0x7700b40]non-existing SPS 0 referenced in buffering period
2012-03-19 23:16:38.922 [h264 @ 0x7700b40]non-existing PPS referenced
2012-03-19 23:16:38.923 [h264 @ 0x7700b40]non-existing SPS 0 referenced in buffering period
2012-03-19 23:16:38.923 [h264 @ 0x7700b40]non-existing PPS 0 referenced
2012-03-19 23:16:38.923 [h264 @ 0x7700b40]decode_slice_header error
2012-03-19 23:16:38.923 [h264 @ 0x7700b40]non-existing PPS 0 referenced
2012-03-19 23:16:38.923 [h264 @ 0x7700b40]decode_slice_header error
2012-03-19 23:16:38.923 [h264 @ 0x7700b40]non-existing PPS 0 referenced
2012-03-19 23:16:38.924 [h264 @ 0x7700b40]decode_slice_header error
2012-03-19 23:16:38.924 [h264 @ 0x7700b40]non-existing PPS 0 referenced
2012-03-19 23:16:38.924 [h264 @ 0x7700b40]decode_slice_header error
2012-03-19 23:16:38.924 [h264 @ 0x7700b40]non-existing PPS 0 referenced
2012-03-19 23:16:38.924 [h264 @ 0x7700b40]decode_slice_header error
2012-03-19 23:16:38.924 [h264 @ 0x7700b40]non-existing PPS 0 referenced
2012-03-19 23:16:38.924 [h264 @ 0x7700b40]decode_slice_header error
2012-03-19 23:16:38.924 [h264 @ 0x7700b40]no frame!"

---

### Post by newlinux on 2012-03-20
have you tried playing recordings outside of myth using mplayer with VDPAU to isolate whether the problem is myth playback configuration or not?

---

### Post by tobiz on 2012-03-20
Newlinux, yes I've tried this a little. I've played a DVD via vlc and it was ok, no issues (not sure whether it was using VDPAU, I'll check that too). Not tried playing any of the TV recordings outside myth yet but will do so and report back.

---

