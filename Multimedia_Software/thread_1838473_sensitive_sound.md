---
title: "sensitive sound"
date: 2011-09-03
forum: Multimedia Software
---

### Post by the_blue_box on 2011-09-03
Hi all

I've got an odd problem with my 11.04 Movie Player.
When I'm watching a DVD in Movie Player the sound is (for lack of a better word) "sensitive" the quiet bits in the sound are really quiet and the loud bits are really loud. I keep having to change the volume while I'm watching.
Is there anyway to even out the sound? 

Any help would be great.

[COLOR=Navy]The Blue Box[/COLOR]

---

### Post by papibe on 2011-09-04
I'm pretty sure you refer to the sound [dynamics]("http://en.wikipedia.org/wiki/Dynamics_%28music%29"). If the video or music that you are playing has a wide range of dynamics, it could be difficult to appreciate it and enjoy it.

In order to improve it you need to 'sort of flatten' the sound. That means to limit both how low the sound can go, and how high can get. The process is usually know as [audio normalizer]("http://en.wikipedia.org/wiki/Audio_normalization").

Movie Player is a very basic player, and can't do much about this. Luckily, the most common Linux players can normalize the sound on the fly: VLC and SMplayer.

In VLC go to Tools -> Preferences -> Show Settings -> All. Then Audio -> Filters. There Check 'Volume normalizer'. To adjust how the filter work click below in the actual parameters of Volume normalizer. [Here]("http://forum.videolan.org/viewtopic.php?f=14&t=91355")'s more information about that.

In SMplayer is more simple, just make sure Audio -> Filters -> Volume normalization is check. There are more low level options here, but you have investigate more (like editing the mplayer config file and using an specific ratio for the normalization [af=volnorm=something if I remember correctly]).

BTW, just guessing here, but most laptops have... not very good speakers (to say the least). You could improve the sound a lot if you pass the audio to a device with better audio reproduction capabilities (like a good powered speakers system).

I hope it helps,
Regards.

---

### Post by the_blue_box on 2011-09-04
I thought it would be along those lines.
I compleatly forgot about VLC, I've installed it now and it sounds better already (without me having to change anything)

Thanks for the help :)

[COLOR=Navy]The Blue Box[/COLOR]

---

