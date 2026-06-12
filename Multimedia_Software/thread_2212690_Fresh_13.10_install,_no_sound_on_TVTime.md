---
title: "Fresh 13.10 install, no sound on TVTime"
date: 2014-03-22
forum: Multimedia Software
---

### Post by Kevin_Melka on 2014-03-22
Brand new install of 13.10 on a Dell Optiplex 620, 4gb RAM, whole 500gb disk, default install.
Have run an older version (11.x) on this hardware with no issues, including cable feed to my ATI TV card that worked flawlessly without any special config. Swapped in a new HD to try 13.10, and now TVTime has no sound. Found a command line execute for TVTime to debug, this is what I get:

[B]username@OptiPlexGX620:~$ tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay - +
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/username/.tvtime/tvtime.xml
ALSA lib pcm_hw.c:1667: (_snd_pcm_hw_open) Invalid value for card
arecord: main:722: audio open error: No such file or directory
aplay: playback:2715: read error
mixer: find error: Success
mixer: Can't open mixer default, mixer volume and mute unavailable.
mixer: Can't open device default/Line, mixer volume and mute unavailable.
[/B]
Sound works fine for other things like YouTube, movie player, but nothing on TVTime (channels work fine).
Not a complete ubuntu beginner, but not advanced. Any advice would be helpful.

thx

---

