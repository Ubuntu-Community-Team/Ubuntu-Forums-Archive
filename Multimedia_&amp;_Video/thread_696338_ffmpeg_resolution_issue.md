---
title: "ffmpeg resolution issue"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by mamboze on 2008-02-13
Hi everybody,

I have been using ffmpeg to convert a .vob file to .flv format. I've been able to do this OK when no resolution change is specified. So transcoding  from a 720x540 vob file to 720x540 flv file is no problem. Even with the very large reduction in file size >400Mb to around 60Mb the quality of the flv file is good. 

The flv file is needed for a website but at 720x540, is too large. What I want is a smaller window, around 540x360 or maybe less. But using  -s 540x360 in the command line produces a flv file with noticeable video artifacts, - the color seems pixelated and seems to flicker slightly. 

Any advice on what should (or can) be done would be much appreciated. Thanks in advance.

---

### Post by gsmanners on 2008-02-13
540x360 gives you 1.5:1 aspect. Maybe you should try 480x360 or 540x405.

---

### Post by mamboze on 2008-02-14
Hi gsmanners,

Sorry, the 540X360 was a typo, I did try 480x360, but it didn't help either. I've looked around online and I don't see anything about transcoding to a different (lower) resolution degrading video quality. I guess there is another parameter that needs to be set, but I don't have any idea which one. 

thanks for your help

---

### Post by philc on 2008-02-14
Can you post your full FFmpeg command here for review please?

---

### Post by mamboze on 2008-02-14
I'm a noob at video, period, so I made an obvious mistake using -f avi, in the command line

ffmpeg -i /home/roy/video/VTS_01_1.VOB -f avi -vcodec mpeg4 -b 800k -g 300 -bf 2  /home/roy/video/lpdaze.flv

OK very obvious 

Now with the following command I get a .flv file with good quality video. :

ffmpeg -i /home/roy/video/VTS_01_1.VOB -ab 56 -ar 22050 -b 500000 -r 15 -s 540x360 /home/roy/video/lpdaze.flv 

but I get a warning

: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s

Is this significant? Also, the command line output is: 

frame= 9736 fps= 49 q=6.6 Lsize=   54176kB time=649.0 bitrate= 683.9kbits/s    
video:39763kB audio:14042kB global headers:0kB muxing overhead 0.689026%

How much could the frame rate be reduced (if any) without affecting video quality? Or are there other settings which wpuld help with file size?

Thanks for your help, it is much appreciated.

---

### Post by philc on 2008-02-14
> **mamboze said:**
> 
Now with the following command I get a .flv file with good quality video. :

ffmpeg -i /home/roy/video/VTS_01_1.VOB -ab 56 -ar 22050 -b 500000 -r 15 -s 540x360 /home/roy/video/lpdaze.flv 

but I get a warning

: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s

Is this significant? Also, the command line output is: 


This is probably with relation to the audio bitrate. -ab 56 sets the audio bitrate to 56 bits per second. Try either -ab 56k or -ab 56000 for 56 kbps.

---

### Post by disturbedite on 2008-02-14
or better yet, doesn't flv support even higher quality audio parameters?  its just that sites live youtube use the really crappy audio settings...

---

### Post by gsmanners on 2008-02-14
I don't really see how dropping the frame rate would help. In fact, you would probably be better off setting it to 24 or 30 fps.

---

### Post by mamboze on 2008-02-14
With the following settings:

ffmpeg -i /home/roy/video/VTS_01_1.VOB -ab 56k -ar 11025 -b 500k -r 15 -s 480x320 /home/roy/video/lpdaze.flv

and output:

frame= 9736 fps= 54 q=2.8 Lsize=   47144kB time=649.0 bitrate= 595.1kbits/s    
video:39718kB audio:7055kB global headers:0kB muxing overhead 0.792615%

OK video/audio quality.

Just a little background, this is a  video about Lampang, a city in northern Thailand which will be used on a local website/portal. Due to local bandwidth considerations, I would like to reduce the file size as far as possible consistent with reasonable video/audio quality. Is there any fine tuning that can be done here?

thanks for the help

---

### Post by gsmanners on 2008-02-14
You could try 320x240 and maybe play with the bitrate.

---

### Post by philc on 2008-02-15
> **mamboze said:**
> 
Just a little background, this is a  video about Lampang, a city in northern Thailand which will be used on a local website/portal. Due to local bandwidth considerations, I would like to reduce the file size as far as possible consistent with reasonable video/audio quality. Is there any fine tuning that can be done here?


Did you know that the latest Flash player will support playback of H.264 MPEG4 content?

Here's an example site, using embedded flash player for playback and all the videos are H.264 MOV files:

[http://www.kapitalmototv.co.uk](http://www.kapitalmototv.co.uk)

With H.264 you should be able to obtain better quality files at a smaller filesize. 

FFmpeg supports H.264 through the x264 codec (-vcodec libx264). You might also need to install this library and re-compile FFmpeg against it ([http://stream0.org/2008/01/install-ffmpeg-on-ubuntu-gutsy.html](http://stream0.org/2008/01/install-ffmpeg-on-ubuntu-gutsy.html))

I agree with gsmanners that lowering the framerate is probably not the way to go. However, reducing the file dimensions is an option.

Also, try variable bitrate encoding rather than constant bitrate. So, try the following FFmpeg settings:

For 480x360 content: -b 350k -maxrate 500k

For 320x240 content: -b 250k -maxrate 350k

The best way really is to systematically try some different settings until you find an acceptable quality/filesize ratio for yourself.

---

### Post by mamboze on 2008-02-15
HI,

Some fiddling and this command

ffmpeg -i /home/roy/video/VTS_01_1.VOB -ab 56k -ar 22050 -b 300k -r 15 -s 480x360 /home/roy/video/lpdaze483622.flv
gave this
frame= 9736 fps= 53 q=14.6 Lsize=   38391kB time=649.0 bitrate= 484.6kbits/s    
video:23978kB audio:14042kB global headers:0kB muxing overhead 0.975085%

Great

thanks to all

BTW another noob question - how do people get (and give) the indicated thanks, I had a look around in forum help but couldn't see anything applying

---

### Post by gsmanners on 2008-02-15
I found the thread on that:

[http://ubuntuforums.org/showthread.php?t=685924](http://ubuntuforums.org/showthread.php?t=685924)

---

