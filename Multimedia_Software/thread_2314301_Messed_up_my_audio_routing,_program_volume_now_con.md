---
title: "Messed up my audio routing, program volume now controls master"
date: 2016-02-20
forum: Multimedia Software
---

### Post by morganpatrick on 2016-02-20
Hi, I was recently trying to disable pulseaudio for when I use Jack. Somehow in this process, I messed up my audio routing so that individual audio programs control the master volume.

First, Nightingale, my music player, is way too loud. It goes up to 100 and I generally need to keep it on 3 when plugged into computer speakers. I will then turn the master volume way down, and when the next song starts, the master volume will get automatically bumped back up. I will go into alsamixer, set master a 18, headphones and PCM at 80, and then when I go to the next song PCM goes to 100, headphones to 100 and master to 25.

I have similar problems with VLC. Turning the volume up above a certain threshold then starts bumping up the master volume.

I can't remember everything I did to change my configuation, but I do remember I went into .pulse/client.conf and added autospawn = no. I also did this in /etc/pulse/client.conf. I think I also disabled the daemon in another way, but I don't remember now. Then I ran pkill -f pulseaudio to kill everything. Even though I've turned off the autospawn = no commands, pulseaudio still won't start when the computer starts.

Finally, alert sounds go off even though I have them totally disabled in my settings. The login drum sound doesn't go off, but the thud when you backspace as far and you can goes off, the empty trash sound goes off etc.

So what happened? How do I get my audio functioning properly again? Thanks

---

