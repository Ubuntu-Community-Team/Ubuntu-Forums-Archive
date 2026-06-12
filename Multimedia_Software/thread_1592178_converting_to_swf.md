---
title: "converting to swf ?"
date: 2010-10-10
forum: Multimedia Software
---

### Post by inobe on 2010-10-10
convert to swf from any format, i can't seem to accomplish this.


thanks a million for any advice :)

---

### Post by inobe on 2010-10-10
i'm completely lost on this fellas, any ideas will be helpful.

---

### Post by andrew.46 on 2010-10-11
Hi inobe,

The problem lies in the nature of the swf file itself. It was designed really to be a small file that contained entertaining content, much of it interactive. For this purpose swf files can contain objects, images and scripts *as well as* video and audio. It is easy enough to use a program like FFmpeg to pack some audio and video into a swf file but it is a different thing completely to create a proper animated, interactive swf file. So it depends on what you are after?

I have produced a simple bundling of audio and video into a swf container using FFmpeg if you are interested in having a look:

```
wget http://www.andrews-corner.org/samples/legend_guardians.swf
```

and I attach a screenshot showing this little clip playing in the standalone flash player. The point is that it is really only a swf file in name alone, there is no animation, no scripting and no interactivity. Had to bump the bitrate up a little too, flv is not the best for video :).

Andrew

---

### Post by inobe on 2010-10-11
a friend of mines gave me an image hosting account from his site, i have some family video, small clips i would like to share with forums, friends and family without having to use the tube. it hosts swf, this is why i wanted to convert the videos to that format, it wont host flv or any other format for whatever reason.


thanks

---

### Post by inobe on 2010-10-11
> **andrew.46 said:**
> Hi inobe,


```
wget http://www.andrews-corner.org/samples/legend_guardians.swf
```


that plays in firefox 

[http://www.andrews-corner.org/samples/legend_guardians.swf](http://www.andrews-corner.org/samples/legend_guardians.swf)

---

### Post by LuridCinema on 2010-10-11
Try this w ffmpeg . Open a terminal in the folder of the input file and change the INPUT.MOV to the file name and extension of your input file AND CHANGE THE "-S 720x480" to the correct resolution

```
ffmpeg -i INPUT.MOV -s 720X480 -sameq -ar 44100 -ab 192 OUTPUT.swf
```

---

### Post by andrew.46 on 2010-10-11
Hi inobe,

> **inobe said:**
> a friend of mines gave me an image hosting account from his site, i have some family video, small clips i would like to share with forums, friends and family without having to use the tube. it hosts swf, this is why i wanted to convert the videos to that format, it wont host flv or any other format for whatever reason.

In that case I suspect that FFmpeg will do the job quite nicely and the answer will be to convert the video stream to flv and the audio to mp3 and place in swf. This is definitely not ideal encoding but it should fit your needs. FFmpeg has a learning curve and if you are interested this curve starts here:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

There is a gui called winFF which I have not personally used but this might make life a little easier. 

All the best,

Andrew

---

### Post by inobe on 2010-10-12
> **LuridCinema said:**
> Try this w ffmpeg . Open a terminal in the folder of the input file and change the INPUT.MOV to the file name and extension of your input file AND CHANGE THE "-S 720x480" to the correct resolution

```
ffmpeg -i INPUT.MOV -s 720X480 -sameq -ar 44100 -ab 192 OUTPUT.swf
```

that did the trick man 8)

thanks to both for helping out.

andrew i tried winff and it only produces flv outputs, i guess i have to compile ffmpeg from source with some swf syntax.

swf doesn't seem to be an option in any gui tools yet i can encode to just about any format other than swf, weird as if it's unsupported unless i do this in cli.

---

### Post by inobe on 2010-10-13
SOLVED ffmpeg command, not sure how to set the thread solved :P

---

### Post by andrew.46 on 2010-10-14
Hi inobe,

Perhaps a starter for a WinFF preset for your needs might be something like the following:

```

  <swfinobe>
    <label>SWF: Written for inobe</label>
    <params>-vcodec flv -f flv -b 300k -g 160 -cmp dct -subcmp dct -mbd 2 -flags +aic+cbp+mv0+mv4 -trellis 1 -acodec libmp3lame -ac 2 -ar 44100 -ab 128k</params>
    <extension>swf</extension>
    <category>Websites</category>
  </swfinobe>

```

Depends if your version of FFmpeg takes 'k' or 'kb' especially, what sort of baseline bitrate you are after and whether or not your copy of FFmpeg is set for mp3 encoding, but it works well enough on my system. I stole the nice flv parameters from one of the flv presets that shipped with winff :).

**Edit:** Found the nice import export feature so I have attached the preset ready to import :).

Andrew

---

