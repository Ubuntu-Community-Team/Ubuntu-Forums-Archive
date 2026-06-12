---
title: "mplayer command lines? Want AC3, DTS, Stereo, etc.."
date: 2009-02-21
forum: Multimedia Software
---

### Post by gungfujoe on 2009-02-21
I recently installed Myuthbuntu, and noticed that my MKV videos containing AC3 audio weren't sending the AC3 signal over the S/PDIF line, but were instead downmixing to stereo.  Then I found the following command line in another thread:

mplayer foo.avi -ao alsa:device=spdif -ac hwac3

This command line works great.... for files with AC3 audio.  However, if I try playing a file that doesn't have an AC3 track with this command line, I get no sound at all.

How do I tell mplayer to play the audio in the best format that it can?  I need a single command line because MythTV has a single command line for videos, or I think I can set one per file extension, but each container format can contain multiple types of video and audio formats.  So some AVI files might contain AC3 audio, others might contain stereo MP3 audio.  I see that I can set VLC to default to send via S/PDIF, and it'll send whatever format it can.  How do I make mplayer do the same?

---

### Post by gungfujoe on 2009-02-22
Apparently the "-ac hwac3" switch forces AC3 output whether the audio is there or not.  Using the Audio Family instead, with "-afm hwac3" does exactly what I want, plus it'll send any DTS tracks over S/PDIF, if I happen to stumble across any videos with DTS audio.

---

