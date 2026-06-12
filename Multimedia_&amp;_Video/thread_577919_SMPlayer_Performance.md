---
title: "SMPlayer Performance"
date: 2007-10-16
forum: Multimedia &amp; Video
---

### Post by Benjamin_Vedder on 2007-10-16
When i play videos in smplayer they get out of sync and the framerate seems to be low. But, other mediaplayers like vlc, totem and even mplayer (as far as i know smplayer is based on mplayer) work great. The worst performance in smplayer is when i play h.264-videos.

I use xv for video and alsa for audio. My gxf-card is GF8600m GT, cpu core2dou 1,8 GHz, ram 2048 mb ddr2, and all drivers are installed..., so i dont think the hardware is the problem.

The strange thing is that i use the same settings as far as i know for mplay, and that works.

I have installed everything i found about codecs.. gstreamer, w32codecs, libdvdcss2...

I really like smplayer because its so much easier to use then mplayer, so i would appreciate your help.

thanks for replies.

---

### Post by rvm4000 on 2007-10-17
If your videos play well in mplayer but they don't in smplayer, then probably is because of some setting in preferences.

Try to change the video or audio driver. Play a little bit with the performance options.

I had a similar problem with mp4 videos. It seems it was due to the cache setting. I had set to 800 kb. Disabling the cache or setting it to a higher value (4000) seems to have solved the problem.

---

### Post by Benjamin_Vedder on 2007-10-18
Well, i have played around with the settings, and it made no differense. But since i upgraded to gutsy smplayer works exactly like mplayer, but the sound still is a little out of sync (less then 1 secont compared to vlc). The settings i use for the best possible performance in smplayer for me (in case someone else has trouble with performance) are the following:

Video: xv
Dobule buffering, nothing else

Audio: alsa

Performance tab:
uncheck everything works good, and enabling cache also works if it is 4000. Less then 2000 gives performance loss.

when h.264 playback is slow you can add

-lavdopts fast=1:skiploopfilter=all

to mplayer options under advanced

Thx for the reply

i still dont know how i can make the audio completely synced to the video...

---

### Post by Benjamin_Vedder on 2007-10-18
I still notice the video delay in mplayer and smplayer. its the same on all my computers, and with all codecs. the sound comes an half second before the video. That is very annoying when i play movies with a lot of effects, like tricking iT 2, an quake3-movie.

this dont happens in vlc, totem or gxine.

So, is there some way to solve this?

---

### Post by rvm4000 on 2007-10-18
Does that sync problem happen with all videos? In that case it could be a bug of mplayer, anyway look at its config file, maybe you have an option there which is causing the problem.

smplayer (and mplayer) has some options to adjust manually the audio delay: Audio->Delay- and Audio->Delay+

---

### Post by Benjamin_Vedder on 2007-10-19
Well, i seems like + and - are binds to increase and decrease the audiodelay, and i think i hit them by accident... that feels stupid.. hehe i have to unbind those keys..

btw, is there some way to reset the delay in the config, because i can only change the delay, but not reset it. 

thanks for your replies

---

### Post by Benjamin_Vedder on 2007-10-19
ok, i found smplayer.ini and figured out every movie has its own settings for audio delay and a lot of other stuff. I changed audio_delay to zero everywhere and that did the trick for ALMOST all movies. I think the problem is something with the decoding in the mplayer engine, because the movie itself also seems laggy sometimes and for the movies with audiodelay, the delay is different during the playback. And, the lag don't depends on the quality of the movies.

You can see what i mean by trying to play this for example and look at the part whith the effect r_showtris right after the names flashed up somewhere in the beginning. Compare smplayer, vlc and gxine. Btw, r_showtris shows lines on the textures, and they edited it to the music.

[http://files.filefront.com/sp+tricking+iT2zip/;4898242;/fileinfo.html](http://files.filefront.com/sp+tricking+iT2zip/;4898242;/fileinfo.html)

Its the same on my laptop and my desktop. Maybe mplayer cant handle 5 audiotracks in an avi-file in this case.

---

### Post by rvm4000 on 2007-10-19
What version of mplayer are you using?

If it's 1.0rc1 then maybe it's worthy to update it to 1.0rc2.

---

### Post by Benjamin_Vedder on 2007-10-20
i am using the one that comes with gutsy, version 2:1.0~rc1-0ubuntu13

---

### Post by rvm4000 on 2007-10-21
Version 1.0rc1 is more than a year old. A lot of bugfixes and improvements have been done since then.

You really should try to update to 1.0rc2, and see if the problems you're having have been fixed.

---

