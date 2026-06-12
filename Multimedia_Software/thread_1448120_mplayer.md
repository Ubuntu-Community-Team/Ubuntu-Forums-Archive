---
title: "mplayer"
date: 2010-04-06
forum: Multimedia Software
---

### Post by ewe on 2010-04-06
Hi! I watch MLB.TV and had been advised to use a compiled version of mplayer. I removed the distro version (9.10) and tried the compiled player.

The problem is that the picture only comes in 'small' and when I press 'f' for full-screen the picture remains small and the outer portion fill up with black just like maximizing the window. I was told I must have compiled the player with out the -xo function, and was further advised trying the player from the repos should work okay.

I went ahead and reinstalled mplayer from the repos and left the compiled player on the system, but I don't know how to tell mlbviewer to use the distro player. I'm assuming its in my config file for mlbviewer which I'll post.

Help would be greatly appreciated. thanks in advance!

> show_player_command=0

live_from_start=0

favorite_color=cyan

speed=800

video_follow=

video_player=mplayer -fs -cache 2048 -really-quiet

show_inning_frames=1

x_display=

audio_player=mplayer -cache 64 -really-quiet

flash_browser=firefox %s

max_bps=800000

bg_color=xterm

coverage=home

strict_stream=1

audio_follow=

top_plays_player=

favorite=

use_color=0

use_nexdef=1

debug=0

time_offset=

blackout=
 

---

### Post by no2498 on 2010-04-06
smplayer is what i see we need now
type, smplayer in a terminal it tells  how to install it

hope this helps

---

### Post by andrew.46 on 2010-04-07
Hi ewe,

> **ewe said:**
> The problem is that the picture only comes in 'small' and when I press 'f' for full-screen the picture remains small and the outer portion fill up with black just like maximizing the window. I was told I must have compiled the player with out the -xo function, and was further advised trying the player from the repos should work okay.

Sounds like you were using x11 as a video out when the default is usually xv. x11 will still go to full screen as you would normally expect by using the -zoom option...

Andrew

---

