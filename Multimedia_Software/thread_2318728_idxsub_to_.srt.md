---
title: "idx/sub to .srt"
date: 2016-03-28
forum: Multimedia Software
---

### Post by John Jason Jordan on 2016-03-28
My computer has Xubuntu 14.04.3, up to date. Everything works. :)

I have an MKV file of an old and unusual film (out of copyright in the country of origin) that someone else ripped and encoded to MKV. I do not have the original media. The MKV file is huge and I wish to re-encode it to a more manageable size, and I also wish to encode the subtitles into the new file. Unfortunately, the original encoder (now deceased) created the subtitles as .idx and .sub files. They work, but I cannot figure out how to encode them into my new MKV file. My usual tool for ripping and encoding is Handbrake, because I don't know what I'm doing and Handbrake is pretty foolproof. But Handbrake can only handle .srt files. I also have just about every multimedia tool that I could find in the repositories, but none of them seem to be able to handle the task.

Searching the Ubuntu forums I find suggestions to use Gaupol, Gnome Subtitles, or Subtitle Editor to convert the idz/sub files to srt. However, none of them will open the .sub file, mostly with an error message that the file is too big. (Yet it has subs only for one language.) I can open the .idx file in a text editor just fine, but Gedit and other plain text editors take forever to open the .sub file, and the results are gibberish. Yet these subtitles do work, so the subs must be inside the file somewhere.

I could use any and all suggestions!

---

### Post by papibe on 2016-03-28
Hi John Jason Jordan.

You should be able to merge the VoSub subs (idx/sub combo) to the mkv movie using mkmerge from the mkvtoolnix package (or mkvtoolnix-gui).

Unfortunately, VoSub are images with timecodes. That's the reason they don't scale very well and if they are from a old DVD my guess they are low res too.

They can't be converted to text using Gnome-Subtitles and alike. You need an [OCR]("https://en.wikipedia.org/wiki/Optical_character_recognition") program. Here's a couple of tips on how to do that: [How can I convert IDX/SUB DVD subtitles into a text SRT subtitle file?]("http://askubuntu.com/questions/149798/how-can-i-convert-idx-sub-dvd-subtitles-into-a-text-srt-subtitle-file")

In my experience, the Avidemux alternative is too difficult (almost a manual translation of each line).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by John Jason Jordan on 2016-03-29
> **papibe said:**
> You should be able to merge the VoSub subs (idx/sub combo) to the mkv movie using mkmerge from the mkvtoolnix package (or mkvtoolnix-gui)..

Thanks.

I had tried the mkvmerge gui previously but couldn't figure out which files to put in which windows. I fumbled around trying different things, but without success. But after reading your words of encouragement I tried again, and this time I succeeded. Now I only need to try to remember how I did it in case this comes up again.

---

