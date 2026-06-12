---
title: "subtitles"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by Gouz on 2007-09-26
Hey there.

I have a small problem with subtitles when I am using Mplayer to watch an anime and there is a Translators note or comments I can see only this and not the translation itself.
And when I use Totem I can see only the translation and not the TN :/

I tried to change the subs position side ect nothing helped.

Any ideas?
Thanks

---

### Post by shirilover on 2007-09-26
I'm going to need a little more information about the actual file in order to determine the best course of action.
So, is the file an .avi or .mkv or .mp4?
If the file is an .mkv, does it have soft-subs?
If so, did you use the 'j' key to show the subtitles?
Also, are you using ssa/*** subtitle rendering?

---

### Post by Gouz on 2007-09-27
It is in .mkv and there are soft subs yes. I check it with hard subs and there no problem with them.

I don't know what the j key meansor if I use ssa/*** sorry I don't know what that means.

I used the option from the control panel  view---->subtitles--->eng subs or track 1 or what ever the name is.

Gouz

---

### Post by shirilover on 2007-09-27
In mplayer, via gmplaer the GUI, you can right-click on the player skin and choose preferences(see screenshot). At the bottom is a checkbox to use libass for rendering subtitles.

Since the file has soft-subs, which are not normally enabled by default, you need to specifically set the player to show them. 
'j' is the keyboard shotcut for cycling through available subtitle streams. It also works in SMplayer.
As far as the translator notes, they may or may not be encoded into the video stream.

However, it appears that you may be using SMplayer which is a Qt frontend to mplayer.
In that case, go to Options->Preferences and select Subtitles from the list on the left. Then go to the SSA/*** Library tab(last tab on the right) and see if the checkmark is there.

---

### Post by Gouz on 2007-09-28
I don't have the SSA/** checkbox at all.
there is nothing down on the options box.

I have all ready click on the Unicode subtitle box. take a look at the screen shot a to see me Mplayers edition and properties.

---

### Post by shirilover on 2007-09-28
That must be an older version of mplayer, the latest stable (1.0rc1) would have another section at the bottom.

---

