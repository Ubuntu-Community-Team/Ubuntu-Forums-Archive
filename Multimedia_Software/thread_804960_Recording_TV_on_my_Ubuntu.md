---
title: "Recording TV on my Ubuntu"
date: 2008-05-23
forum: Multimedia Software
---

### Post by cazz on 2008-05-23
Hi I have a TV card on my Ubuntu so I can watch TV when I use "TVtime televisions viewer" and that works fine,

But I like to recording and save it as high quality as possible,

I have read that VLC can do it but I have no idea how I can pick right channel.

I have also read Mencoder can do it but only things I have found dont work so good.

I have even try with some program from my "Add/Remove Applications" but that is not so many that can recording and they I have found wont work at all for me :confused:

I don't want to use Myth TV because I just want to recording, nothing more.


/Update

I have found this code on Mencoder homepage

```
mencoder -tv driver=v4l:width=768:height=576 -oac mp3lame -lameopts cbr:br=64\
    -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=900 \
    -vf crop=720:544:24:16,pp=lb -o output.avi tv://
```

The only funny things is that I have to open "TVtime televisions viewer" to pick what channel I want to recording :)

So i have to first open the program, then pick a channel, then close the program and run the code.

---

### Post by cazz on 2008-05-24
have a little problem with the sound

I have to put a cable from my PC card to Line in in my sound card but I can't still change the volume, I think it go 100% and that dont sound good at all when I play what I have recording.

I have try to change the volume for Line-in but nothing happend, no change at all. :confused:


/Update

I use 

vol=0.2 in my code like this

```
mencoder -tv driver=v4l:width=720:height=576 -oac mp3lame -lameopts cbr:br=192:cbr:vol=0.2  -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=5000  -o output.avi tv://
```

/Update 2
Is no change at all :(

---

### Post by cazz on 2008-05-25
I have now try with mencoder and transcoder and I have change the volume in the code but same problem

Crackle sound when I try to recording the TV program.
When I watch a TV program it sound perfect but not when I trying to recording.

I have even try to turn off every level of the volume control but I have notice that the code dont care about the volume control at all.

I use Intel ICH5(alsa) and I run on a 2,4Ghz P4 with 1 GB memory so I can't possibly think my computer is to slow.

I maybe have to install windows to see if I can recording without get that crackle sound :(

---

### Post by xc3RnbFO8P on 2008-05-25
Can you try this:

In terminal:
> cat /dev/video0 > myvideo.mpg <return> 

Use CTRL + C to stop, and play
> mplayer myvideo.mpg

---

### Post by cazz on 2008-05-25
> **Ringi said:**
> Can you try this:

In terminal:


Use CTRL + C to stop, and play

that create a MPG file but I can't play it at all.

Not in Mplayer or VLC

---

### Post by xc3RnbFO8P on 2008-05-25
And you did **mplayer myvideo.mpg** in terminal?

---

### Post by cazz on 2008-05-25
> **Ringi said:**
> And you did **mplayer myvideo.mpg** in terminal?

```
mplayer myvideo.mpg
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing myvideo.mpg.
libavformat file format detected.
[mp3 @ 0x8804034]Could not find codec parameters (Audio: mp1, 128 kb/s)
LAVF_header: av_find_stream_info() failed


Exiting... (End of file)

```

That is what I get

---

### Post by xc3RnbFO8P on 2008-05-25
Then it doesn't work.

---

### Post by cazz on 2008-05-25
> **Ringi said:**
> Then it doesn't work.


What dont work?

---

### Post by xc3RnbFO8P on 2008-05-25
Post #4

---

### Post by cazz on 2008-05-25
> **Ringi said:**
> Post #4

ohh ok, no that dont work

Thanks anyway

---

### Post by MeKino on 2008-05-25
Install xawtv from Synaptic and use it to scan for channels.

This is how I used it for VLC:

[http://ubuntuforums.org/showthread.php?t=758845](http://ubuntuforums.org/showthread.php?t=758845)

---

