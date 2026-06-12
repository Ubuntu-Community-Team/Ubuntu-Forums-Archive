---
title: "Kino, after upgrade to Karmic, is missing H.264 export"
date: 2009-12-10
forum: Multimedia Software
---

### Post by MadKAT on 2009-12-10
Hi,

I just upgraded my ubuntu to 9.10 Karmic. But the Kino editor now is missing the entries for exporting to H.264. The scripts are there in the /usr/share/kino/scripts/export, but they don't appear in the drop-down list in Export->Other->Tools anymore.

Just a note, in Jaunty the entries were there, altho the scripts didn't work at first, but after editing, they did work.

Please let me know how to get them back in the dropdown list for Karmic.

Thank you in advance

---

### Post by MadKAT on 2009-12-11
Found out that this is because of the AAC issue in ffmpeg.
[https://bugs.launchpad.net/ubuntu/+source/faac/+bug/374900](https://bugs.launchpad.net/ubuntu/+source/faac/+bug/374900)

This sucks.

If there's anyone who knows how to modift the bash scripts in kino, could anyone please create a script that would do one for H.264 + MP3 (I guess this one would mean avi container instead of mp4).

I tried it myself but I think I screwed it up, because when I uploaded to youtube, the sound was in fast forward...

---

### Post by VertexPusher on 2009-12-11
The Quicktime DV export option will copy the raw DV video stream with uncompressed PCM audio to a MOV container. You can load that into Avidemux and do the H.264/AAC encoding there. This by the way will give you some additional format choices not available in Kino, e.g. export to MKV containers (aka. "DivX Plus").

---

### Post by MadKAT on 2009-12-11
Oh cool! That worked well, Thank you!!!
:D:D:D

---

### Post by MadKAT on 2009-12-11
Ooops, spoke too soon.  :(
With the loaded MOV file in Avidemux, the audio stops after about a minute of playback. Sometimes if I stop/pause and then play again, the audio returns, but after a minute it will die again.

Now, it would have been workable if this is only in the playback in avidemux, but the resulting exported file (saved to mp4), also has the audio broken, cut at the same position as where it stops during playback in avidemux.

Have you experience this before? Any workarounds/solutions?

Thanks

---

### Post by VertexPusher on 2009-12-12
Hmmm...

It seems that Avidemux has trouble demuxing the MOV file created by ffmpeg. You could try remuxing it to MKV before loading it into Avidemux. mkvtoolnix-gui can do that.

If that doesn't work either, you could try using x264 and faac on the command line to encode video and audio separately, then mux them together using MP4Box.

Or you could download the ffmpeg sources and compile a binary that includes libfaac support. This would make Kino's export script work again.

Try mkvtoolnix-gui first; it's very simple to use, and Avidemux has very stable support for MKV input files.

---

### Post by MadKAT on 2009-12-14
Didn't work for me. I got this warning from the MKV creator:
Warning: Quicktime/MP4 reader: Unknown/unsupported FourCC 'dvc ' for track 1.

And the resulting .mkv file only has audio and no video. :(

As for compiling the source... errr ahmm i think that's way over me hehe. im not a programmer so my brain might explode if i tried that haha.

---

