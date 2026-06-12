---
title: "Why is there no good webcam video capturing programs?"
date: 2011-01-05
forum: Multimedia Software
---

### Post by w1ll1am on 2011-01-05
I purchased a logitech cheap webcam that i was going to use to record some youtube videos and for skype and in Cheese the video was slow and glitchy. So I went out and bought a very nice 5mp HD widescreen HP webcam because I thought that maybe I just did not have a good enough webcam. The resolution for my new webcam goes up to  1280x720 but the highest I can get to work in Cheese without major slowness is 432x240. Does anyone have any suggestions for a better program or maybe a way to make cheese work better? Thanks

---

### Post by no2498 on 2011-01-05
try using vlc to record
open vlc click media open capture device click play then record


hope that helps some

---

### Post by w1ll1am on 2011-01-05
I tried that before I posted this but then my computer freaked out so I am reinstalling and I will get back to you.

---

### Post by BicyclerBoy on 2011-01-06
ffmpeg

[http://www.ffmpeg.org/ffmpeg-doc.html#SEC27](http://www.ffmpeg.org/ffmpeg-doc.html#SEC27)
# Grab and show the input of a video4linux device.
ffplay -s 320x240 -f video4linux /dev/video0

# Grab and show the input of a video4linux2 device, autoadjust size.
ffplay -f video4linux2 /dev/video0

# Grab and record the input of a video4linux2 device, autoadjust size.
ffmpeg -f video4linux2 -i /dev/video0 out.mpeg

or does it have to have a GUI interface ?

---

### Post by w1ll1am on 2011-01-07
> **BicyclerBoy said:**
> ffmpeg

[http://www.ffmpeg.org/ffmpeg-doc.html#SEC27](http://www.ffmpeg.org/ffmpeg-doc.html#SEC27)
# Grab and show the input of a video4linux device.
ffplay -s 320x240 -f video4linux /dev/video0

# Grab and show the input of a video4linux2 device, autoadjust size.
ffplay -f video4linux2 /dev/video0

# Grab and record the input of a video4linux2 device, autoadjust size.
ffmpeg -f video4linux2 -i /dev/video0 out.mpeg

or does it have to have a GUI interface ?

I tried this and it works okay but it is still kind of slow and I could not get sound on the video. Can you tell me how to get the sound working?

---

### Post by BicyclerBoy on 2011-01-07
Depends on your audio setup etc
ffmpeg -f alsa -i hw:0 alsaout.wav

First try this for audio recording..

Open the ffmpeg doc link in the previous post.
Scroll up a couple pages to the audio stuff

When you join the video & audio stuff together, you will
 need to select an audio codec to use with the output container type.

---

### Post by sdowney717 on 2011-01-07
I found sound on the webcam input was muted. Open sound applet icon and explore to see

you can also test the sound input using that sound preferences
 
guvcview also expose v4l2 settings

---

### Post by gordintoronto on 2011-01-07
The best solution would be a faster CPU! I have one of the world's crummiest webcams, but I can record 640x480 videos just fine in Cheese.

---

### Post by w1ll1am on 2011-01-08
> **gordintoronto said:**
> The best solution would be a faster CPU! I have one of the world's crummiest webcams, but I can record 640x480 videos just fine in Cheese.

I have a 2.4Ghz intel Core2Quad is this not fast enough?

---

### Post by w1ll1am on 2011-01-08
Okay I got the sound working but now how do I get both the sound and the video together I tried this 

```
 sudo ffmpeg -f alsa -i hw:1 -f video4linux2 -i /dev/video0 /home/w1ll1am/Desktop/out.ogg 
```but I get this error

```
 [video4linux2 @ 0x1f353a0]Cannot find a proper format for codec_id 0, pix_fmt -1.
/dev/video0: Input/output error 
```

So I am not too sure but I guess I am not setting the codec?

Also the /dev/video0: input/output error just started happening and i can no longer get the video to show up it was working and then I tried to run it again and it stoped working any thoughts?

---

### Post by BicyclerBoy on 2011-01-09
ogg files are audio only..

The filename extension is important if the container type is not stated/passed.

Try .ogv

---

### Post by w1ll1am on 2011-01-09
> **BicyclerBoy said:**
> ogg files are audio only..

The filename extension is important if the container type is not stated/passed.

Try .ogv

Sorry I meant .ogv I tried both because I could not remember which one was both. when I try .ogv everything runs and it comes up to the press q to quit encoding and it does not show anything happening. If you hit q nothing happens also so I have to close the terminal and if I try to play the file created in totem I get an error that says  could not demultiplex stream?

---

### Post by BicyclerBoy on 2011-01-09
I know the video worked before but..the file extension forced the video codec.
And it was not .ogv but mpg...

The std *buntu ffmpeg (& 7x libav*) has most functionality removed.
What you need built in ffmpeg is libtheora.

Ffmpeg reports it configured/compiled status every time it is invoked/run.

What does it report ?
Building a working ffmpeg may be too difficult.

Can you use mpeg-4 instead of ogv ?

Don't use totem to check media files. Better to use VLC or mplayer.
I think VLC & mplayer can both be made to record from alsa & video devices..

---

### Post by w1ll1am on 2011-01-09
I am about to give up sometimes it works and other times it doesn't and by that i mean 

```
sudo ffplay -f video4linux2 /dev/video0
```gives an input/output error sometimes and in VLC the same thing happens. When it does work in VLC my speakers make a strange sound and it gets louder and louder I am not sure what thats about.

---

### Post by BicyclerBoy on 2011-01-09
Don't use sudo..

Your ffmpeg packages could be too old/bugged.
Getting a good full featured build of ffmpeg is not easy.

VLC may make a strange noise if it is outputting sound & recording from some input.
It is possible to create digital & analogue feedback/loopbacks..

Time to give all that away & try something else..
Have you tried guvcview ?

---

### Post by gordintoronto on 2011-01-09
> **w1ll1am said:**
> I have a 2.4Ghz intel Core2Quad is this not fast enough?

Should be OK. I'm really baffled about why you are having trouble with this.

---

### Post by BicyclerBoy on 2011-01-09
Further to my earlier suggestion.
guvcview works okay recording internal webcam video & audio on my netbook.

I used a simple video codec in mkv container.

Files play okay in totem (std netbook app).

---

### Post by w1ll1am on 2011-01-10
> **BicyclerBoy said:**
> Further to my earlier suggestion.
guvcview works okay recording internal webcam video & audio on my netbook.

I used a simple video codec in mkv container.

Files play okay in totem (std netbook app).

Right now I am at school but I just tried guvcview on my netbook and it works great much better than cheese does on here so I am hoping it will do the same on my desktop I will try it tomorrow because I have to work tonight but I will let you know thanks.

Well maybe I spoke too soon I am having a problem on the netbook might not happen on my desktop but the video and audio are not syncing up the audio finishes way before the video does.

---

### Post by 0N3 on 2011-01-10
Webcamstudio 

[www.ws4gl.org](www.ws4gl.org)

---

### Post by w1ll1am on 2011-01-10
I am having the same problem on my desktop as i did on my netbook the video and audio are not syncing does anyone have any idea why?

I just downloaded webcamstudio I will try it out tomorrow.

---

### Post by s8472 on 2011-02-10
> **BicyclerBoy said:**
> ffmpeg

[http://www.ffmpeg.org/ffmpeg-doc.html#SEC27](http://www.ffmpeg.org/ffmpeg-doc.html#SEC27)
# Grab and show the input of a video4linux device.
ffplay -s 320x240 -f video4linux /dev/video0

# Grab and show the input of a video4linux2 device, autoadjust size.
ffplay -f video4linux2 /dev/video0

# Grab and record the input of a video4linux2 device, autoadjust size.
ffmpeg -f video4linux2 -i /dev/video0 out.mpeg

or does it have to have a GUI interface ?
Thank you very much for sharing.  Is it also possible to capture the video and audio from an incoming call?  If not, any pointers in the right direction would be much appreciated.  Thanks in advance.

---

### Post by hornetster on 2011-02-13
[http://www.ffmpeg.org/ffmpeg-doc.html#SEC27](http://www.ffmpeg.org/ffmpeg-doc.html#SEC27)
# Grab and show the input of a video4linux device.
ffplay -s 320x240 -f video4linux /dev/video0

# Grab and show the input of a video4linux2 device, autoadjust size.
ffplay -f video4linux2 /dev/video0

# Grab and record the input of a video4linux2 device, autoadjust size.
ffmpeg -f video4linux2 -i /dev/video0 out.mpeg


Whenever I use the above commands for video4linux2, I get: *[video4linux2 @ 0x9731300]Cannot find a proper format for codec_id 0, pix_fmt -1.*
Using video4linux gives me a green static screen...

Have searched but found no answers...
Thanks, John.

---

### Post by w1ll1am on 2012-03-14
> **w1ll1am said:**
> Right now I am at school but I just tried guvcview on my netbook and it works great much better than cheese does on here so I am hoping it will do the same on my desktop I will try it tomorrow because I have to work tonight but I will let you know thanks.

Well maybe I spoke too soon I am having a problem on the netbook might not happen on my desktop but the video and audio are not syncing up the audio finishes way before the video does.

I am still having this issue and it is really getting annoying does anyone else have this issue?

---

### Post by w1ll1am on 2012-03-14
I was able to get the video and audio to sync if I used a separate mic not the one that is built in to the web cam. But now when I am recording or even just watching what is being displayed with out recording if I move too quick it blurs. I have a $50 web cam that makes very nice videos in windows that are half as blurry as these why?

---

