---
title: "amakode transcode to ogg - is it possible?"
date: 2009-09-04
forum: Multimedia Software
---

### Post by vegmunky on 2009-09-04
I installed the amaKode script into Amarok per many people's suggestions. I have a mixed collection of flac, mp3, and ogg. My goal is to transcode everything to ogg when I load my MTP media player.  However, when I go to the config panel (gears) for my media player, amaKode says "Transcode to preferred format (mp3) for device".  I cannot figure out how to change the default format to ogg.

I believe amaKode is capable of doing this, because I opened up the .py script and it has oggenc listed as one of its encoders. There is also a note in my amakode.log file that says "No config file found, using defaults." Maybe I need a config file to specify that ogg is my default encoding format, but I can't find any documentation about how to set up the config file.

Any advice?  I did look into the Transcogg script, but it wanted me to install the "id3info" package which doesn't exist in Synaptic.

---

### Post by vegmunky on 2009-09-04
Nevermind. Problem solved, I think. Switched from MTP mode to MSC(UMS).

---

