---
title: "slow playback of 1080p x264 .mkv files"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by theknowledgeist on 2008-01-17
Hi Folks,

_Problem:_
Playback of 1080p x246 .mkv files is very slow on my machine, regardless if I use totem or vlc media player. The video lags a lot but the audio is fine.

Also, when I try to fast-forward to a different scene in the movie, it takes the video a minute or so to catch up (ie the screen stays black), but the audio catches up almost instantly.

FWIW, playback in Windows Vista is better but it still lags.

_My Specs:_
I'm running Ubuntu 7.10, using nVidia restricted drivers, and I've done all the software updates. I've installed libmatroska0 from synaptic. Also I've disabled all visual effects. I've also installed ubuntu restricted extras and the w32codecs from medibuntu.

I have a Core 2 Duo 2.67ghz, eVGA 8800GTX, SB Audigy, Asus P5N-E sli motherboard.

If you need more info, please tell me and I'll get it for you. I'm new to Ubuntu and don't really know what other info to provide.

Thank you.

---

### Post by disturbed1 on 2008-01-17
I get the best x264 playback with Mplayer. Totem and VLC both have the occassional frame drop now and then, and forget about FF/RW takes forever for them to find a key frame to get the picture back.

---

### Post by killermist on 2008-01-17
It's unlikely that any amount of tweaking will help make that run smoothly for you without a highly specialized hardware decoder (xbox 360, playstation 3, or graphics card module).  Since it runs slow in windows too, I'd bet dollars to donuts that you don't have the right hardware decoder module, since you'd probably have the newest driver that would utilize it if present (because MS and it's hardware providers are SO on the ball with making sure you've got the right drivers.  Sorry, sometimes my sarcasm gets the better of me)
In the transition from standard mpeg4 to x264/h264, the quality level jumped significantly, and the total processing necessary to render files of even 720p resolution jumped exponentially.  1080i and 1080p make this even more noticable.
This is one of the things that's causing some slowing of the adoption of x264/h264 as a user-encoded format.
Even at VCDish resolutions, the processing power needed to render 2 files, from the same source, one into x264 and one into mpeg4, the x264 one will be noticably heavier on processor usage, but also cleaner to look at, or smaller on disk, whichever was prioritized.

I have 2 possible solutions (which you probably won't like).  
1.)  If you have a standalone player that can handle x264 encoded video, try that.  
2.)  If not, your only option may be to pass the file(s) through an encode process to another codec (likely decreasing the resolution considerably in the process).  

If you're interested in option 2, there are guides here and there for how to do so.

```
mencoder sourcefile.mkv -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vhq:v4mv:vqmin=2:vbitrate=1000 -vf pp=de,scale=525:-2 -o resultfile.avi
```
That's the command line I've been using dor my transcodes.  It keeps the old audio (because the audio isn't causing a problem, and better to not lose a generation of quality), and converts the video from whatever it was before (x264 in this case) to mpeg4 (somewhat generic) with good attempts to retain as much quality as possible, scaling it down to 525x[whatever] (retains aspect ratio as close as possible).  If you're overly paranoid about quality loss, then you can increase vbitrate=1000 to something more, and if it doesn't need it, then it likely won't use it.

---

### Post by theknowledgeist on 2008-01-17
Thanks disturbed and killermist.

Mplayer on ubuntu doesn't work for me: after a few minutes of video I keep getting an error message that says "too many video packets in the buffer." It will pop up, quickly go away, pop up again, quickly go away, and continue like that until I can quit mplayer. The video keeps playing in the background, but it is slower and unwatchable due to the flashing error message.

Mplayer for Vista however works pretty well. There are a few points during the movie when audio and video get choppy but its the closest to perfect I've seen so far. 

Killermist:

I don't have a standalone player; my computer is my only option. I have a few follow-up questions:

1. Is it simply not possible for a person with an nVidia card to playback x264 files? 

2. Are you saying that a video encoded in mpeg-4 will necessarily be of lower quality than an x264 encoded video?

3. Are x264 and h264 the same thing?

Thanks.

---

### Post by disturbed1 on 2008-01-17
I play 1080P content with system in my sig. An AMD Sempron 3000+ 1gig ram, nVidia fx5500 plays 720P content without issues.

Turnoff compiz if you have it enabled.

---

### Post by shirilover on 2008-01-17
> **theknowledgeist said:**
> 
1. Is it simply not possible for a person with an nVidia card to playback x264 files? 

2. Are you saying that a video encoded in mpeg-4 will necessarily be of lower quality than an x264 encoded video?

3. Are x264 and h264 the same thing?

Thanks.

Answers:

1. It is entirely possible to play back x264 encoded files with an nvidia card. I have done so with an older PC(Athlon 1.0 GHz, GeForce 4 Ti4200) at standard resolution(704x396, 853x480) without difficulty.

2. In most cases, yes, a video encoded in MPEG-4 ASP will be of lesser quality than the same encoded in MPEG-4 AVC.

3. H.264 is a codec primarily known as MPEG-4 part 10 AVC. x264 is the open source encoder for encoding H.264 video streams.

Final notes:

Playing high resolution H.264 video requires significantly more processing power that Xvid or othe MPEG-4 ASP codecs. Do not believe that your video card will necessarily have any effect on playing such video. H.264 video is _not_ hardware accelerated in linux. Most newer nvidia based cards do offer MPEG-4/H.264 hardware acceleration in Windows only.

This may not answer why you are unable to play back 1080P H.264 video; however, disabling compiz will greatly improve your chances as would compiling mplayer from svn sources so that the resulting binary in optimized for your hardware.

---

### Post by geoken on 2008-02-09
I'm pretty sure his issue has nothing to do with processing power. I get extremely choppy playback on any x264 encoded mkv file while using totem gstreamer. If this problem had something to do with cpu power I'm pretty sure that;

a) My CPU usuage would be a little higher than ~14% and
b) the problem wouldn't totally dissapear when I switch to totem xine (which handles the files beautifully)

---

### Post by Rusna on 2008-02-12
> **theknowledgeist said:**
> Mplayer on ubuntu doesn't work for me: after a few minutes of video I keep getting an error message that says "too many video packets in the buffer." It will pop up, quickly go away, pop up again, quickly go away, and continue like that until I can quit mplayer. The video keeps playing in the background, but it is slower and unwatchable due to the flashing error message.

Mplayer for Vista however works pretty well. There are a few points during the movie when audio and video get choppy but its the closest to perfect I've seen so far. 


I have the exact same problem, it would be nice to know if there's an answer or are the x264 files the only reason why I have to continue using Windows :I

---

### Post by miketedeschi on 2008-02-12
Here are some things i have found from experience with lots of user encoded .mkv files with x264 video.

1. if you have a dual core processor, make sure the decoder is set to 2 threads.  otherwise you are only using half of your cpu power. it makes a drastic difference.

2. most 720p .mkv 264 video files work fine on P4 3.0 ghz. if you have a single core cpu you can pretty much forget about 1080p mkv files. i think.

3. my dual core 2.8 ghz cpu, running the decoder with 2 threads utilizing both cores, will play all 720p mkv files flawlessly, and some 1080p mkv files.  lots of 1080p mkv files max out both my cores 100% and the video is unwatchable.

4. the video may appear smooth, but you may still be droping frames.  open task manger and check your cpu usage.  if you are averaging over 70% you are pushing it.

i use the k lite codec pack, i suggest upgrading to the newest verison if you use it and havent updated i a while. the encoder included allows you to set the number of threads it will use to decode the video stream.

To the best of my knowledge: I am assuming the only way to ensure that you can play all 1080p mkv in 264 format without some type of hardware decoder is to buy a quad core cpu, and run 4 threads on the video decoder.

quad core intel chips are down to $275 for te q6600. 

im going to buy one of these chips soon and will post my results.  if anyone has tried this let me know.

hope this helps

Mike

---

### Post by theacoustician on 2008-02-12
> **miketedeschi said:**
> Here are some things i have found from experience with lots of user encoded .mkv files with x264 video.

1. if you have a dual core processor, make sure the decoder is set to 2 threads.  otherwise you are only using half of your cpu power. it makes a drastic difference.

2. most 720p .mkv 264 video files work fine on P4 3.0 ghz. if you have a single core cpu you can pretty much forget about 1080p mkv files. i think.

3. my dual core 2.8 ghz cpu, running the decoder with 2 threads utilizing both cores, will play all 720p mkv files flawlessly, and some 1080p mkv files.  lots of 1080p mkv files max out both my cores 100% and the video is unwatchable.

4. the video may appear smooth, but you may still be droping frames.  open task manger and check your cpu usage.  if you are averaging over 70% you are pushing it.

i use the k lite codec pack, i suggest upgrading to the newest verison if you use it and havent updated i a while. the encoder included allows you to set the number of threads it will use to decode the video stream.

To the best of my knowledge: I am assuming the only way to ensure that you can play all 1080p mkv in 264 format without some type of hardware decoder is to buy a quad core cpu, and run 4 threads on the video decoder.

quad core intel chips are down to $275 for te q6600. 

im going to buy one of these chips soon and will post my results.  if anyone has tried this let me know.

hope this helps

Mike

:confused: k lite is a Windows package.

---

### Post by skibrianski on 2008-02-19
Simple solution is to use mplayer. With with a 1080p x264 mkv totem shows about 1 frame every 2-3 seconds at 100% cpu. With mplayer I get 85-90+% cpu usage, but framedrops are very rare, and the result is completely watchable. This is with compiz still enabled, on a 2.33GHz core2duo with a GeForce Go 7300.

---

### Post by bogolisk on 2008-03-03
> **geoken said:**
> I'm pretty sure his issue has nothing to do with processing power. I get extremely choppy playback on any x264 encoded mkv file while using totem gstreamer. If this problem had something to do with cpu power I'm pretty sure that;

a) My CPU usuage would be a little higher than ~14% and
b) the problem wouldn't totally dissapear when I switch to totem xine (which handles the files beautifully)

There's a bug in gstreamer-ffmpeg.

[http://bugzilla.gnome.org/show_bug.cgi?id=482660](http://bugzilla.gnome.org/show_bug.cgi?id=482660)

I dled hardy's gstreamer-ffmpeg source package, apply the patch, build the deb and install. Et voila! smooth x264 playback.

---

### Post by llove on 2008-03-08
hi, does anybody can tell me how can apply this patch?? a link to some guide, I have the same problem, it plays slow, but the CPU its not at 100%. thanks
best regards from buenos aires

ariel

ps:sorry for the spelling and grammar

---

### Post by nawitus on 2008-03-08
Also make sure that DMA is not disabled (you probably don't but it is worth a check in grub configuration, look for nodma).

---

### Post by mptpro on 2008-03-12
> **miketedeschi said:**
> Here are some things i have found from experience with lots of user encoded .mkv files with x264 video.

1. if you have a dual core processor, make sure the decoder is set to 2 threads.  otherwise you are only using half of your cpu power. it makes a drastic difference.


Thanks.

How do you enable 2 threads in a decoder?

---

### Post by miketedeschi on 2008-04-08
i would look around in settings in whatever player you are using.  depending on the way the file was encoded, x264 files may not take advantage of GPU and are completely relying on CPU power.  if you have a 1080p x264, get a core 2 duo or a core 2 quad to be safe.  pentim d will not cut it.

my core 2 quad uses 15-20% of all 4 cores when playing a 1080p x264 file.  and it is smooooth.

i also have a macbook with a core 2 duo and it plays them smooth aswell. maybe just get a mac mini for the plasma guys? you can always put windows xp on it if you insist......

---

### Post by miketedeschi on 2008-04-08
> **mptpro said:**
> Thanks.

How do you enable 2 threads in a decoder?

look in options/settings, not all can do it.  VLC can, and FFDshow can also.

the option will probably be called "number of decoding threads"

what CPU are you running mptpro?

---

### Post by kioftes on 2008-07-15
Hi guys! same problem here....anyone tried the patch mentioned above? I tried converting the mkv file to sth else but the quality seems always inferior...Can somebody give details to the ignorant ones (me) of how to install the patch?

---

### Post by Povilas on 2008-07-15
The way I fixed slow playback for HD videos:
Install SMplayer > Options > Preferences > Performance > H.264 > Loop filter > Skip only on HD videos

Worked for me and no patching required :P

---

### Post by outlaw45 on 2008-07-19
Hi guys,

I got the same problem with a Intel Core2 E6420 (dual 2.13Ghz), playing 720p is just fine but my CPU just can't handle 1080p on 1 thread. I've been trying to enable two threads on VLC but just can't find it.. The GUI doesn't have an option to enable multiple threads and I also can't find the commandline parameter.. Please tell me how to enable multiple threads for VLC so I can determine if I need a new CPU. I'll list my full specs below

Intel Core2 E6420
ATI Radeon X1950PRO 512MB
2GB RAM
Ubuntu 7.10 (fully updated)

---

### Post by andrew.46 on 2008-07-22
Hi:

> **Povilas said:**
> The way I fixed slow playback for HD videos:
Install SMplayer > Options > Preferences > Performance > H.264 > Loop filter > Skip only on HD videos

Worked for me and no patching required :P

You should not have to install smplayer just for this, although it is a fine front-end for mplayer. The mplayer manual mentions this filter:

> skiploopfilter=<skipvalue> (H.264 only)

Skips the loop filter (AKA deblocking) during H.264  de-
coding.  Since the filtered frame is supposed to be used
as reference for decoding dependent frames  this  has  a
worse  effect  on  quality  than not doing deblocking on
e.g. MPEG-2 video.  But at least for high  bitrate  HDTV
this  provides  a  big  speedup  with no visible quality
loss.

<skipvalue> can be either one of the following:

**none**:     Never skip.
**default**:  Skip useless processing steps (e.g.  0  size packets in AVI).
**nonref**:   Skip frames that are not referenced (i.e. not
          used for decoding  other  frames,  the  error  cannot "build up").
**bidir**:    Skip B-Frames.
**nonkey**:   Skip all frames except keyframes.
**all**:      Skip all frames.

  Andrew

---

