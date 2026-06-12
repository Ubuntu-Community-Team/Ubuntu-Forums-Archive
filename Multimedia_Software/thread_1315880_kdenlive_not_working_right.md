---
title: "kdenlive not working right"
date: 2009-11-05
forum: Multimedia Software
---

### Post by mstjohn1974 on 2009-11-05
Hi,

I am trying to use kdenlive to do some video editing but I can't get it to work right...it doesn't mater what kind of video i add a clip kdenlive either wont play it at all or the sound is totally crappy a lot of static and th other symptom is that the sound is good but the video is not showing or greenish sometimes even scrambled.... all my video players play the files correctly if it's xine, mplayer, totem etc.

are there any special steps to do to make it work better....

I really like to get it working....


thanks for every hint

---

### Post by jaygo on 2009-11-06
same issue here. I tried manually setting the audio settings to pulseaudio and got *no* sound. Video is completely broken, like yours, but I noticed if you pause playback it immediately displays the frame you're at.

I also noticed it maxes out my dual core CPU during playback, even when I'm only playing an mp3 or ogg file. I think something's definitely broken here, though I'd guess it's only an issue on ubuntu.

---

### Post by jaygo on 2009-11-06
fixed it!
As suspected, the video problem went away after I disabled compiz. From what I recall, it's actually an nvidia problem but it's why I still can't use compiz (won't play videos over about 640x480).

For the video, just disable "visual effects" (compiz). System > Prefs > Appearance > Visual Effects = none

The audio issue is explained at [http://ubuntuforums.org/showthread.php?p=8260424](http://ubuntuforums.org/showthread.php?p=8260424). To sum up:

[LIST=1]
[*]change kdenlive settings > playback > audio > pulseaudio
[*]close kdenlive
[*]install libsdl1.2debian-all (this will replace libsdl1.2debian-alsa)
[*]try it out
[*]if it still doesn't work, run this terminal command:> $ export SDL_AUDIODRIVER=esd 			 		
[/LIST]

---

### Post by mstjohn1974 on 2009-11-10
I solved it a little bit different. I made a Youtube Clip that demonstrate the way I fixed it just go to [http://mstjohn1974.blogspot.com](http://mstjohn1974.blogspot.com)

---

### Post by GenePayne on 2009-11-15
I had problems with audio similar to what is described here, but not the video problems.

I solved it by following step A from this:
[HTML]http://ubuntuforums.org/showthread.php?t=789578[/HTML]

This was actually linked from a thread on the kdenlive forum:
[HTML]http://www.kdenlive.org/forum/help-ubuntu-910-fresh-install-ffplay-and-melt-crash[/HTML]

It looks like mstjohn1974 covers this in the latter-half of his video above (thanks for doing this great video).

I am posting this in case someone has only the audio problems and might think this thread doesn't apply to them.

---

