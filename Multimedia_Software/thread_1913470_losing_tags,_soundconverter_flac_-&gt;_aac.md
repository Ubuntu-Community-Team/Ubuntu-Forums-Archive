---
title: "losing tags, soundconverter flac -&gt; aac"
date: 2012-01-22
forum: Multimedia Software
---

### Post by cometdog on 2012-01-22
Ubuntu 11.10, 64-bit.

I ripped some audio to .flac using Sound Juicer 2.32.1 and then converted them to AAC (.m4a) using SoundConverter 1.4.4.  The tags (Title, Artist, Album, etc.) seem to be missing in the .m4a files.  If I convert to .mp3 instead, the tags are preserved.  Anyone else observing this?

---

### Post by kassoulet on 2012-01-23
This is a known problem with SoundConverter/GStreamer, see [https://bugs.launchpad.net/soundconverter/+bug/805602](https://bugs.launchpad.net/soundconverter/+bug/805602)

As a workaround, you can use EasyTag: rename the files to match the tags, convert to AAC, and fill the tags from the filenames.

---

