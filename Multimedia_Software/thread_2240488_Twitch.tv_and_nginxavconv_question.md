---
title: "Twitch.tv and nginx/avconv question"
date: 2014-08-20
forum: Multimedia Software
---

### Post by tomatogoatee on 2014-08-20
Alright, here's what I'm trying to accomplish:
Stream to both twitch.tv AND hitbox.tv at the same time through my Ubuntu 12.04 server, but add an overlay to the twitch.tv stream telling viewers to follow me on hitbox.tv

Here's the pertinent part of my nginx.conf file:
```

application dual_stream {
     live on;
     record off;
# Added to stream to Twitch.tv and Hitbox

     push rtmp://live.vgn.hitbox.tv/push/<stream key>;

     exec avconv -i rtmp://localhost/dual_stream/$name -vf "movie=/shared/message.png[logo];[in][logo]overlay=0:70[out]" -c:a copy -c:v copy -b:v 800k -maxrate 800k -minrate 800k -bufsize 800k -g 60 -f flv rtmp://live-ams.twitch.tv/app/<stream key>;
}
```
Now, as it is, this code works. When I tell OBS to stream to my Ubuntu server, nginx and avconv play nice and relay the stream to the respective servers. HOWEVER, as you can see from the settings above, avconv is only using a direct copy of the stream (audio AND video) and my message.png isn't being added. So I changed "-c:v copy" to "-c:v libx264" (because twitch likes to complain if you don't use h.264) and my twitch dashboard claims the stream is "excellent", but nothing ever comes through. (The video just says "loading" but never starts.) If I change the target from twitch to my local machine and open the stream with, say, VLC then the stream plays fine, overlay included!

So, to those of you who are more savy than myself, what do you think the problem is? I've captured both the source from OBS and the output from acvonv and, at least at first glance, the two are alike as far as codec and compression level. (I didn't think to check the bitrate of the files. I should do that.)

---

### Post by mastalavista on 2014-08-21
Hello tomato,

this command works for me:

```
avconv -i rtmp://localhost/dual_stream/$name -vf "movie=/shared/message.png[logo];[in][logo]overlay=0:70[out]" -vcodec libx264 -vprofile baseline -preset veryfast -acodec copy -ar 44100 -ac 2 -b:v 800k -maxrate 800k -minrate 800k -bufsize 800k -g 60 -f flv rtmp://live-ams.twitch.tv/app/<stream_key>;

```

cheers!

---

### Post by tomatogoatee on 2014-08-21
Thank you, mastalavista! I'm at work right now, but I will try this once I get home tonight.

---

### Post by tomatogoatee on 2014-08-21
Works like a champ! Thank you for your help!

Only problem now is I didn't realize how much of a load avconv would put on my poor server. Guess it's time to upgrade. Ha!

---

