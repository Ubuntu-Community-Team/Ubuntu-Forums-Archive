---
title: "Downloading realaudio/wma files from radio"
date: 2008-01-24
forum: Multimedia &amp; Video
---

### Post by pinkunicorn on 2008-01-24
Swedish radio [http://sr.se/](http://sr.se/) broadcasts book readings in instalments regularly. I'd like to download these files to be able to listen to them on my mp3 player, but I haven't been able to actually get at the files. The media formats they offer are RealAudio and Windows Media (not mp3), but since my SqueezeBox can play at least Windows Media I assume that it should be straightforward to convert that to mp3 if I can only get at the files.

The page [http://www.sr.se/cgi-bin/P1/program/sandningsarkiv.asp?ProgramID=1111](http://www.sr.se/cgi-bin/P1/program/sandningsarkiv.asp?ProgramID=1111) has a list of recent episodes. Is there a way for me to download the audio files for a "Radioföljetongen" link? A solution that can be scripted would be optimal, but something that involves manual intervention is also interesting.

---

### Post by mssever on 2008-01-24
For both Real and Windows Media, the first file you get after clicking on a link is actually a text file that contains information about the actual media. You cn use wget to examine those files and find the actual media file, which you can then download with wget or similar. One gotcha: Real files often use the propriatary rtsp: protocol, which means that you might not be able to download those files directly.

Another option might be to find some software that captures audio sent to the sound card and saves it in some format. I don't know of anything like that for Linux, but I haven't looked, either.

---

### Post by logos34 on 2008-01-24
You can't download it, all you can do is try to capture the stream.  (EDIT: or can wget do that, as mssever posted?)

I tried mplayer.  I clicked on one of the links on the page you provided, then I right-clicked on the pop-up player to copy the URL.  

Then I pasted it in this command:

$ mplayer -playlist "<URL>" -dumpstream -dumpfile <file>

$ mplayer -playlist "rtsp://lyssna-rm.sr.se/autorec/p1/radiofoljetongen/SRP1_2008-01-24_113459_1502_r3.rm" -dumpstream -dumpfile radiofoljetongen_test.rm

It starts up but can't grab onto the stream.

(It works fine for me with BBC streams)

If you could get it to work, then you could convert it to mp3 with SoX.


The easiet way is probably just to do

$ gnome-sound-recorder

set it for 

record from input: 'mix'
record as: mp3 

this will record off your soundcard and convert to mp3 on the fly. 

When complete, stop, name the file and save it.

---

### Post by mssever on 2008-01-24
> **logos34 said:**
> The easiet way is probably just to do

$ gnome-sound-recorder

set it for 

record from input: 'mix'
record as: mp3 

this will record off your soundcard and convert to mp3 on the fly. 

When complete, stop, name the file and save it.

Thanks for that. I didn't know that that was included by default.

---

### Post by logos34 on 2008-01-24
> **mssever said:**
> I didn't know that that was included by default.

I can't remember, TBH.  I may have gotten mine by installing the **gnome-media** pkg.

---

