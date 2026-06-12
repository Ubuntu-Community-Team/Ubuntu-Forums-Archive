---
title: "Need to do basic editing on a sound file - all programs are failing"
date: 2008-09-07
forum: Multimedia Software
---

### Post by Vadi on 2008-09-07
Hi,

I need to accomplish a simple task - cut out a part of an .ogg file and then mute the ending. In Linux.

I've tried every program I found so far in repositories and every single one failed me. Can anyone share the secret on being able to accomplish this basic editing task on Linux?

I tried so far:
- Audacity. By default, it cannot play sound. I have to launch it with the "padsp" command. I cut the selected part fine, press play, it plays until the end ok. I move - or attempt to - the play cursor towards the beginning, and the program freezes. Every single time.
- GNUsound. I get this error when opening my ogg: "Error: Unknown file format for /home/vadi/Music/Viktoria/Unknown Title/09 - Track 9.ogg". OGG is an unknown file format? WTH?
- Jokosher 0.10. Double-click, right-click menus randomly doesn't work. Sound visualizations randomly corrupt. I was able to cut and move the parts together as necessary, but I see no way of muting the volume at the end.
- MusE. Upon launch it tells me "Failed to find Jack audio server", and tells me that I'll have no sound. Obviously this won't work.
- ReZound. When I click play, it tells me the name of some program function and says "sound player not initialized". I thought the program would've done that automatically for me, but I see no way to do this myself either.
- Rosegarden. What a pretty welcome screen. But it spoils that right after by failing to find the Jack audio server guy too.
- Sweep. Doesn't playback sound either.

Um, that's it. Can anyone help me out please? Any programs I missed?

---

### Post by Vadi on 2008-09-08
Can anyone help?

---

### Post by logos34 on 2008-09-08
to cut:

sudo apt-get install vorbis-tools

man vcut

other than audacity not sure what app to suggest for mute/fade out

---

### Post by Vadi on 2008-09-09
Well, just stuck with the muting problem. I managed to cut the track (blindly, visualizaion was totally off track) already.

---

### Post by Vadi on 2008-09-14
Converting the .ogg to .wav with [http://media-convert.com/](http://media-convert.com/) and then editing it in sweep worked.

---

