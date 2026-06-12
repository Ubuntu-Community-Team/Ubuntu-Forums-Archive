---
title: "Rhythmbox Track Length Errors"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by newagelink on 2007-08-11
An entire album, Jaktens Tid by Finntroll, is in my music library ... each song after the first being between 0:01 and 0:04 seconds in length.

The songs play fine, but the length is corrupted ...? How do I fix this? I have tried removing it, then File > Import Folder ... it imports it back at 0:04 lengths, etc. :(

---

### Post by Alexander2007 on 2007-08-11
> **newagelink said:**
> An entire album, Jaktens Tid by Finntroll, is in my music library ... each song after the first being between 0:01 and 0:04 seconds in length.

The songs play fine, but the length is corrupted ...? How do I fix this? I have tried removing it, then File > Import Folder ... it imports it back at 0:04 lengths, etc. :(

What format are they encoded in?
Files encoded in MP3 VBR may display track times incorrectly in applications based on Gstreamer0.10
Maybe you should try another music player (like "Banshee") Banshee is also based on Gstreamer0.10 but it works better in my opinion.
You can find it in "Add/Remove" and "Synaptic".

---

### Post by newagelink on 2007-08-20
[COLOR="Indigo"]All it says for bitrate when I right click > properties > Details is "128 kbps". They're mp3. Do you think it might be displaying VBR as 128? Or would it say VBR?

Why does this error occur?

I don't really want to switch music players *again*; I already tried amarok but it won't install correctly from the program repository; very frustrating, and I don't know why it seems to work for others but not me. (I assume it does, otherwise surely this huge error would be fixed.) Banshee ... I dunno why I haven't tried it already, but there's a reason; ... Banshee isn't listed as a supported Ubuntu application. What does this mean? (I know how to switch it to show all programs; I wonder, though, what it means to be supported versus not supported.) I'll read [http://www.ubuntu.com/community/ubuntustory/components](http://www.ubuntu.com/community/ubuntustory/components) again (thanks to aysiu).

I don't want to switch because of my ~14000 songs I've rated 1221 of them, and I'd hate to have to start all over *again*.

Does that make any sense?[/COLOR]

---

