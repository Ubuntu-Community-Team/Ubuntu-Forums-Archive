---
title: "[SOLVED] How to convert to &amp;quot;.mov&amp;quot; format?"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by berliita on 2007-09-15
I'd like to convert a video, which is available to me in either ".avi" or ".mpg" format, to the ".mov" format. How to do that?

I tried ffmpeg, thus:
<code>
$ ffmpeg -i input.avi output.mov
</code>

But the following error message resulted:
<code>
Unsupported codec for output stream #0.1
</code>

I'm not married to ffmpeg, just want the job done.

---

### Post by asmoore82 on 2007-09-15
I think you may need to be more specific,
there has been more that one ".mov" format over the years,
and, moreover, I can't fathom a reason you would actually
want to convert *to* the format unless you are trying
to get a video to play on an iPod ...

---

### Post by berliita on 2007-09-15
Hi, asmoore82. Thanks for replying.

I'm trying to follow Cinerella's "Getting Started" tutorial (
[http://www.robfisher.net/video/cinelerra1.html](http://www.robfisher.net/video/cinelerra1.html)). Section "Setting Project Options" opens with the following words:
<quote>
By now you should have a selection of video captures in Quicktime (.mov) format.
</quote>

I've only got ".avi" and ".mpg" files at my disposal. I've tried the Mux website ([http://mux.am/](http://mux.am/)) to do the conversion, but the resulting video's quality was poor.

---

### Post by asmoore82 on 2007-09-15
that tutorial seems to be a little outdated ...

[QUOTE="Rob Fisher"]1 December 2002

Added the Cinelerra tutorial.[/QUOTE]

Kino has come a long way since then and can probably accomplish the task without cinelerra.

Either way, you would probably benefit greatly from some more up-to-date documentation ...

Kino Homepage: [http://kinodv.org/](http://kinodv.org/)
Cinelerra Doc: [http://heroinewarrior.com/documents.php3](http://heroinewarrior.com/documents.php3)

---

### Post by Crenfinkle on 2007-09-15
I'm not sure, but you may have to download extra codecs from the medibuntu repo. I stressed over this problem when converting .flv to .mp4 and ultimately this was the solution. (Is .mov considered a proprietary format?) Try this before you give up, because I have found ffmpeg to be super-versatile, fast, and effective.

---

### Post by berliita on 2007-09-16
Thanks, asmoore82 and Crenfinkle, for replying. I'll try to get by without an ".avi" -> ".mov" converter.

---

### Post by cotcot on 2007-09-16
Try kino.
Import the avi and export as quicktime.
Kino knows the format. I capture with kino (so .dv) and save it as quicklinux to edit in cinelerra.

---

### Post by vrix on 2007-09-17
you may want to try WinFF. you can get it from here: [WinFF.]("http://biggmatt.com/programs/video-converter/winff---free-video-converter.html")

Important note: in order for it to work, you must change the preset, in the command line parameters to: "-acodec pcm_s16le -ab 128"
from -acodec ac3...

---

### Post by berliita on 2007-09-21
Thanks, cotcot and vrix, for your replies.

cotcot: Could you please explain in more detail how you get Kino to export to Quicktime format?

vrix: I've browsed to the WinFF webpage. It looks like a nifty tool, but it's just a GUI for the ffmpeg command, which i can't get to work in the first place.

---

### Post by berliita on 2007-09-27
Problem solved. See [http://ubuntuforums.org/showthread.php?p=3434109#post3434109](http://ubuntuforums.org/showthread.php?p=3434109#post3434109) .

---

### Post by cotcot on 2007-09-27
> **berliita said:**
> Thanks, cotcot and vrix, for your replies.

cotcot: Could you please explain in more detail how you get Kino to export to Quicktime format?

.

Select in the menu at the right side "export". Selecte then the DV tab. There you will find quicktime dv

---

### Post by berliita on 2007-09-27
Thanks, cotcot. I see the the radio button you were referring to, but it's disabled. :(

---

### Post by cotcot on 2007-09-28
> **berliita said:**
> Thanks, cotcot and vrix, for your replies.

cotcot: Could you please explain in more detail how you get Kino to export to Quicktime format?

.

---->  Export  ----> DV file  ----> Quicktime DV

---

### Post by berliita on 2007-09-28
No, cotcot, i wasn't kidding: i see the "Quicktime DV" radio button you mentioned, but it's disabled. I can't choose it.

---

