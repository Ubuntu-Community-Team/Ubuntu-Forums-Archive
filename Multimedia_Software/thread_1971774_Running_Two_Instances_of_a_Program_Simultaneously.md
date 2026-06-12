---
title: "Running Two Instances of a Program Simultaneously"
date: 2012-05-02
forum: Multimedia Software
---

### Post by dodle on 2012-05-02
I am using ffmpeg to capture my screen. Though i am having a problem with audio syncronisation:

```
ffmpeg -f x11grab -r 30 -s 1280x800 -i :0.0 -f alsa -i hw:0,0 -sameq -vcodec libxvid -acodec libmp3lame -ab 128k -ar 44100 -ac 1 test.avi
```

One site I read suggested recording audio and video separately, so I tried this:

```
ffmpeg -f x11grab -r 30 -s 1280x800 -i :0.0 -sameq -vcodec libxvid video.avi & \
ffmpeg -f alsa -i hw:0,0 -acodec libmp3lame -ab 128k -ar 44100 -ac 1 audio.mp3
```

But only the audio is recored while an empty "video.avi" is created. How can I create two instances of ffmpeg running at the same time?


**----- SEMI-SOLVED -----**

I figured out how to use [color=red]nohup[/color] in order to successfully run the first intance of ffmpeg in the background:

```
: nohup ffmpeg -f x11grab -r 30 -s 1280x800 -i :0.0 -vcodec libxvid video.avi & \
ffmpeg -f alsa -i hw:0,0 -acodec libmp3lame -ab 128k -ar 44100 -ac 1 audio.mp3
```

The problem now is how to kill the first process along with the second.


**----- SOLVED -----**

The PID of the first instance of ffmpeg can be placed in a variable using [color=red]$![/color], then just kill that process ID when the second instance is finished:

```
nohup ffmpeg -f x11grab -r 30 -s 1280x800 -i :0.0 -vcodec libxvid video.avi &
P1=$!
ffmpeg -f alsa -i hw:0,0 -acodec libmp3lame -ab 128k -ar 44100 -ac 1 audio.mp3

kill $P1
```

---

