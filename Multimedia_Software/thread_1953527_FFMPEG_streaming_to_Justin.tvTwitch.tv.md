---
title: "FFMPEG streaming to Justin.tv/Twitch.tv"
date: 2012-04-06
forum: Multimedia Software
---

### Post by SAKeeler on 2012-04-06
Does anyone have any advice on how to make this work?  I am using a modified script found using google.
Running Ubuntu 11.10 with Unity

```
#Streaming screen to Justin.tv
streaming() {
INRES="1920x1080" # input resolution
OUTRES="1280x720"
FPS="30" # target FPS
QUAL="medium"  # one of the many FFMPEG preset
STREAM_KEY="$1"
URL="rtmp://live.justin.tv/app/$STREAM_KEY" #flashver=FMLE/3.0\20(compatible;\20FMSc/1.0)"  

#ffmpeg -f x11grab -s "$INRES" -r "$FPS" -i :0.0 -ab 22050\
# -f alsa -ac 2 -i pulse -vcodec libx264 -s "$OUTRES" -level 30 -f mpegts \
# -acodec libmp3lame -ac 1  \
# -f flv "$URL"




ffmpeg -f x11grab -s "$INRES" -r "$FPS" -i :0.0  -ab 96k \
    -f alsa -ac 2 -i pulse -vcodec libx264 -crf 30 -vpre "$QUAL" -s "1280x720" \
    -acodec libmp3lame -ar 44100 -threads 8 \
    -f flv "$URL"
}
```

After modifying slighly I have it working, somewhat, it doesn't throw errors in the command line, but I don't get any video coming through when I load my channel on Juistin.tv.

Any sugestions? Pointers? and please don't say Webcamstudio, ffmpeg is far lighter weight, and all things considered easier to deal with.  Aside from this little hiccup of course.;)

---

### Post by balloons on 2012-04-09
You want to use vlc with this:

[http://apiwiki.justin.tv/mediawiki/index.php/Linux_Broadcasting_API](http://apiwiki.justin.tv/mediawiki/index.php/Linux_Broadcasting_API)

---

### Post by SAKeeler on 2012-04-10
> **guitara said:**
> You want to use vlc with this:

[http://apiwiki.justin.tv/mediawiki/index.php/Linux_Broadcasting_API](http://apiwiki.justin.tv/mediawiki/index.php/Linux_Broadcasting_API)

I really was trying to avoid it, but I will be giving it a read through and testing it this weekend.  Still tinkering with the ffmpeg solution though,
it's infuriating, it should work but just isn't, and I can't figure out why.
Makes me crazy.

Thanks for the link btw.

---

### Post by balloons on 2012-04-25
LOL -- ok, here's an example of ffmpeg working

```
#!/bin/bash
API_KEY="live_*****************"
FPS="15"

INRES='1280x1024'
OUTRES='1280x1024'

ffmpeg -f x11grab -s "$INRES" -r "$FPS" -i :0.0+1280 \
       -f alsa -i pulse -vcodec libx264  -s "$OUTRES"  \
       -acodec libmp3lame -ab 64k -ar 22050 -threads 0 \
       -f flv "rtmp://live.justin.tv/app/$API_KEY"
```

---

### Post by vitrums on 2012-07-28
It's actually kinda weird that this issue hasn't been resolved yet. At least I just couldn't find any solution whether googling or posting the official FFmpeg IRC channels. Any idea why I get a blank video on such RTMP resources  as justin.tv, own3d and so on. Once again, there's no issue with local recordings, it works just fine.

---

### Post by vitrums on 2012-07-29
The solution came from a member of FFmpeg development group. Since the video itself is fine when it's examined locally, there must be some trouble with some of the formats. Actually it was all about pixel format.

If we capture the screen locally with the output option set as *-f flv out.flv*, the later examining of the video with *ffprobe out.flv* would show that the pixel format is 444, and it's not yet widely supported. Hence, it's necessary to add *-pix_fmt yuv420p* in the encoder properties to get your video playable by justin, twitch, own3d, ustream and other rtmp services :popcorn:

---

### Post by SAKeeler on 2012-08-05
Man, I'll have to make note and try it when i get a Ubuntu box up and running again.

thanks, wouldn't have thought of that.

> **vitrums said:**
> The solution came from a member of FFmpeg development group. Since the video itself is fine when it's examined locally, there must be some trouble with some of the formats. Actually it was all about pixel format.

If we capture the screen locally with the output option set as *-f flv out.flv*, the later examining of the video with *ffprobe out.flv* would show that the pixel format is 444, and it's not yet widely supported. Hence, it's necessary to add *-pix_fmt yuv420p* in the encoder properties to get your video playable by justin, twitch, own3d, ustream and other rtmp services :popcorn:

---

### Post by dannyboy79 on 2012-12-10
trying to accomplish this and I get the following error.
my script looks like this trying to implement your idea about the -pix_fmt as well as set the threads to 2 since I have a core 2 duo CPU.
```
#!/bin/bash
API_KEY="live_xxxxxxxxxxxxxxxxxxxx"
FPS="15"

INRES='1440x900'
OUTRES='1440x900'

ffmpeg -f x11grab -s "$INRES" -r "$FPS" -i :0.0+1440 \
       -f alsa -i pulse -vcodec libx264 -pix_fmt yuv420p  -s "$OUTRES"  \
       -acodec libmp3lame -ab 64k -ar 22050 -threads 2 \
       -f flv "rtmp://live.twitch.tv/app/$API_KEY"
```

```

./stream 
ffmpeg version 0.8.4-6:0.8.4-0ubuntu0.12.10.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:49:20 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[x11grab @ 0x9f4bce0] device: :0.0+1440 -> display: :0.0 x: 1440 y: 0 width: 1440 height: 900
[x11grab @ 0x9f4bce0] shared memory extension  found
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  130 (MIT-SHM)
  Minor opcode of failed request:  4 (X_ShmGetImage)
  Serial number of failed request:  11
  Current serial number in output stream:  11

```

ANy help would be appreciated


UPDATE: i posted how I got it all fixed over here: [http://ubuntuforums.org/showthread.php?t=2084420&highlight=twitch](http://ubuntuforums.org/showthread.php?t=2084420&highlight=twitch)  In short, the script is a tiny bit different and the inres and outres changed and there was no need for -pix_fmt

---

### Post by Kranium31 on 2013-12-03
You need to change the video output in the player to x11.  

i've got all that working but i'm having sync issues with the sound. The video is behind the audio and it gets progressively worse as the stream goes through the playlist.

---

### Post by Nickolai_Leschov on 2013-12-27
I've had some success with the code modified from [here]("http://www.thegameengine.org/miscellaneous/streaming-twitch-tv-ubuntu/").
My version: ([on pastebin]("http://paste.ubuntu.com/6646835/"))
> [COLOR=#008800]*#! /bin/bash*[/COLOR]

[COLOR=#008800]*# streaming on Ubuntu via ffmpeg.*[/COLOR]
[COLOR=#008800]*# see [http://ubuntuguide.org/wiki/Screencasts](http://ubuntuguide.org/wiki/Screencasts) for full documentation*[/COLOR]

[COLOR=#008800]*# input resolution, currently fullscreen.*[/COLOR]
[COLOR=#008800]*# you can set it manually in the format "WIDTHxHEIGHT" instead.*[/COLOR]
[COLOR=#B8860B]INRES[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]**$(**[/COLOR]xdpyinfo | grep [COLOR=#BB4444]'dimensions:'[/COLOR]|awk [COLOR=#BB4444]'{print $2}'[/COLOR][COLOR=#AA22FF]**)**[/COLOR]

[COLOR=#008800]*# output resolution.*[/COLOR]
[COLOR=#008800]*# keep the aspect ratio the same or your stream will not fill the display.*[/COLOR]
[COLOR=#B8860B]OUTRES[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"960x540"[/COLOR]

[COLOR=#008800]*# input audio. You can use "/dev/dsp" for your primary audio input.*[/COLOR]
[COLOR=#B8860B]INAUD[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"pulse"[/COLOR]

[COLOR=#008800]*# target fps*[/COLOR]
[COLOR=#B8860B]FPS[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"30"[/COLOR]

[COLOR=#008800]*# video preset quality level.*[/COLOR]
[COLOR=#008800]*# more FFMPEG presets avaiable in /usr/share/ffmpeg*[/COLOR]
[COLOR=#B8860B]QUAL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"fast"[/COLOR]

[COLOR=#008800]*# stream key. You can set this manually, or reference it from a hidden file like what is done here.*[/COLOR]
[COLOR=#B8860B]STREAM_KEY[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]**$(**[/COLOR]cat /some_dir/twitch.key[COLOR=#AA22FF]**)**[/COLOR]

[COLOR=#008800]*# stream url. Note the formats for twitch.tv and justin.tv*[/COLOR]
[COLOR=#008800]*# twitch:"rtmp://live.twitch.tv/app/$STREAM_KEY"*[/COLOR]
[COLOR=#008800]*# justin:"rtmp://live.justin.tv/app/$STREAM_KEY"*[/COLOR]
[COLOR=#B8860B]STREAM_URL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"rtmp://live.twitch.tv/app/$STREAM_KEY"[/COLOR]

ffmpeg [COLOR=#BB6622]**\**[/COLOR]
-f alsa -ac 2 -i [COLOR=#BB4444]"$INAUD"[/COLOR] [COLOR=#BB6622]**\**[/COLOR]
-f x11grab -s [COLOR=#BB4444]"$INRES"[/COLOR] -r [COLOR=#BB4444]"$FPS"[/COLOR] -i :0.0 [COLOR=#BB6622]**\**[/COLOR]
-vcodec libx264 -pix_fmt yuv420p -s [COLOR=#BB4444]"$OUTRES"[/COLOR] -preset [COLOR=#BB4444]"$QUAL"[/COLOR] [COLOR=#BB6622]**\**[/COLOR]
-acodec libmp3lame -threads 6 -qscale 5 -b 64KB [COLOR=#BB6622]**\**[/COLOR]
-f flv -ar 44100 [COLOR=#BB4444]"$STREAM_URL"[/COLOR]

Per [this discussion]("http://askubuntu.com/a/370725/181242") I've changed xwininfo to xdpyinfo, -vpre to -preset and audio sample rate from 22050 to 44100. It works, though it produces the following [warnings]("http://paste.ubuntu.com/6646602/") ([full log]("http://paste.ubuntu.com/6646587/")) and, more importantly, it is only recording sound from the microphone. Any suggestions regarding how to fix this?

Also, now that it's working, how do I optimize it. I want this to work on a Core 2 laptop, with display resolution of up to 1920x1080. Will I save much CPU power if I reduce the streaming resolution? I'm using preset "fast", there's [also]("http://ubuntuguide.org/wiki/Screencasts") "lossless_ultrafast". How do I see which presets are there? When the streaming is running, there's a line like
```
frame=  229 fps= 21 q=-1.0 Lsize=     532kB time=00:00:10.68 bitrate= 408.0kbits/s 
```
Can I use it to gauge the performance of streaming? I'm not sure I understand it: it says something like "fps=21" which is always less than the fps I asked for. Looks like it's dropping frames, even if CPU isn't at 100%.

---

### Post by FakeOutdoorsman on 2013-12-27
Why do you want to "save CPU power"? What's the actual question here? Why do you not want ffmpeg to take advantage of all available resources? It's a tradeoff: fewer resources = lower frame rate and/or frame size.

[list]
[*] Why do you use "-threads 6"? libx264 automatically determines the optimal number of threads by default so you generally do not need to declare threads unless you want to reduce them.
[*] "-qscale" and "-b" are mutually exclusive, but luckily libx264 ignores "-qscale".
[*] "-b" is ambiguous and you should use a stream specifier with this option: "-b:v" or "-b:a" (same with "-qscale").
[*] A better suggestion may be to base your encoding options on your upload rate if that is a limiting factor. I will expand on this later when I return from a trip. What is your max upload rate?
[*] There is no "lossless_ultrafast" preset unless you're using ancient or fake ffmpeg. Lossless = huge files which would probably not be good for uploading a live stream to this video service.
[/list]

---

### Post by Kranium31 on 2014-01-01
add -g 2 to your -vcodec line,  that will allow you to stream video as well as audio.

---

