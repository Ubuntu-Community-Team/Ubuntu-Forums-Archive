---
title: "Watch ITV streams in UK with mpv"
date: 2019-05-28
forum: Multimedia Software
---

### Post by shantiq on 2019-05-28
streamlink used to work very well to see ITV and ITV4 but they have changed the way the streams are delivered
Was trying to play Roland Garros through mpv instead of through a browser ...   the stream is available to anyone who registers on the site [https://www.itv.com/hub/itv4](https://www.itv.com/hub/itv4)  but it is more stable i find through a player than a browser ;   there is however a way to do this and modifying slightly one of the lines on this [github page]("https://github.com/streamlink/streamlink/issues/1788") it gives you just that; play not dumping

for Roland Garros currently on all 2 weeks use

```
rtmpdump -v -r "rtmpe://cp532702.live.edgefcs.net/live" -a "live" -f "WIN 30,0,0,113" -p "https://www.itv.com/hub/itv4" -W "http://www.itv.com/mediaplayer/ITVMediaPlayer.swf" -y "itv4static@45482"  | mpv -
```

If you wanted ITV instead:

```
rtmpdump -v -r "rtmpe://cp532701.live.edgefcs.net/live" -a "live" -f "WIN 30,0,0,113" -p "https://www.itv.com/hub/itv" -W "http://www.itv.com/mediaplayer/ITVMediaPlayer.swf" -y "itv1static@45475" | mpv -
```


This might be of use to others  ...   if you know of any other way let us know

---

