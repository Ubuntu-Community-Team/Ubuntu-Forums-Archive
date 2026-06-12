---
title: "Request for help recording mic + game audio + Desktop with avconv"
date: 2013-07-13
forum: Multimedia Software
---

### Post by tazyload on 2013-07-13
I'm fairly new to Ubuntu but after some googling I have cobbled together (copy +pasted :D) two scripts, one for streaming to Twitch.tv;

```

#!/bin/bash
 
API_KEY="live_12345_ABCDEFG"
FPS="30"
INRES="1280x720"
OUTRES="1280x720"
 
ffmpeg -f x11grab -s "$INRES" -r "$FPS" -i :0.0 \
-f alsa -ac 2 -i default -vcodec libx264 -s "$OUTRES" \
-acodec libmp3lame -ab 128k -ar 44100 -threads 2 \
-f flv  "rtmp://live.twitch.tv/app/$API_KEY"

```

And one for just recording the desktop and outputting a .mkv file;

```

#!/bin/bash


echo "Enter the output file name: "; read name


avconv -f alsa -i pulse -f x11grab -r 30 -s 1280*720 -i :0.0 -vcodec libx264 -preset ultrafast -ab 320k -threads 2 $name.mkv



```

Now these both work fine but only give me the option of capturing microphone input **or **game audio and I would really like to have both. I have been looking at the ffmpeg wiki but the section on multiple inputs is sparse from the perspective of a n00b like myself. 

Any help you can give will be greatly appreciated and I thank you for taking the time to read this.

---

### Post by dannyboy79 on 2013-07-15
this is what i used to get the recording of the game audio and your mic, you load the pulseaudio loopback module
[http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html#](http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html#)!

---

### Post by tazyload on 2013-07-15
> **dannyboy79 said:**
> this is what i used to get the recording of the game audio and your mic, you load the pulseaudio loopback module
[http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html#](http://www.creativetux.com/2012/11/streaming-to-twitchtv-with-linux.html#)!

Thanks for the reply, I am following the instructions but when I get to the stage where I have to run the "audio.sh" file I get this back in the terminal;
```

audio.sh: 2: audio.sh: load-module: not found
Failure: Module initalisation failed
Failure: Module initalisation failed
```

Is there something else I have to install? Had to install[FONT=arial] wmctrl so not sure if I'm missing something else.[/FONT]

---

### Post by dannyboy79 on 2013-11-18
i've since found this to be very helpful, [http://askubuntu.com/questions/257992/how-can-i-use-pulseaudio-virtual-audio-streams-to-play-music-over-skype](http://askubuntu.com/questions/257992/how-can-i-use-pulseaudio-virtual-audio-streams-to-play-music-over-skype)
as far as setting up the loopbacks BUT i am getting horrid lag between the actions on the stream and when my actual voice is heard. they are about 25 seconds out of sync

---

