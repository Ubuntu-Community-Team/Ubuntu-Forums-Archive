---
title: "Video Conversion Settings"
date: 2014-09-10
forum: Multimedia Software
---

### Post by raccoonstrait on 2014-09-10
Good day to all,

I have gotten hold of some .avi files that fail to play the video portion on my OpenElec/XMBC Raspberry Pi. I tried to buy some codecs from the Pi people hoping that might resolve the issue, but their insistence on using PayPal has prevented that. So I turned to ffmpeg on my Xubuntu box to try a conversion. I got hold of winff and tried to do a conversion, but have no clue as to what video settings to use. They are looking for:

Video Bitrate
Frame Rate
Video Size   __x__
Aspect Ratio

The original .avi is an old movie (think 1940's) though the creation of the digital file is obviously more recent. The test I ran complained about not having those values. I was attempting to convert to MP-4 1080P. Is this reasonable?

The output is to run through the system mentioned above and then to an HD TV via HDMI.

I have a couple of old TV shows (Jack Benny, The Three Stooges, Abbott and Costello, etc.) that appear to have similar issues.

Is there a way to look at the original file and determine what it's parameters are, and then a way to determine what settings might give a decent quality output from that input?

If not, are there some guidelines someplace that might help. Two hours of searching have lead me to a lot of things, not relevant.

Thanks,

Raccoonstrait

---

### Post by papibe on 2014-09-10
EDIT: in Trusty, handbrake is available on the regular repositories. So you can install it using the Software Center. No need for ppa.

Hi raccoonstrait.

Been there ;) If I remember correctly I had problems with an avi file with a divx level3 codec... anyway.

I solved my problem using directly ffmpeg, (and avconv on a later instance).

I've tried WinFF, it's OK, but I recommend taking a look at HandBrake. Handbrake includes presets that set all technical parameters so you don't have to worry about them. For instance, some of the presets are 'iPhone', 'android', and probably more close to want you want, 'normal' or even 'high profile'.

Depending on your version you can use this ppa:
```
ppa:stebbins/handbrake-releases
```
If you are on Trusty, you may want to use this other one:
```
ppa:stebbins/handbrake-snapshots
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by lukeiamyourfather on 2014-09-10
I'd leave the frame rate, video size, and aspect ratio alone. By default most transcoding utilities will use the values from the source video which is the ideal. The bit rate will depend on the resolution of the source video. Here are some suggested bit rates for various resolutions (assuming H.264 codec).

SD: 2-5 Mbps
720p: 5-10 Mbps
1080p: 10-20 Mbps

If possible don't convert the videos at all. Since you're going from one lossy format to another lossy format the video quality can only go downhill from here. Do you know what codec the videos are that won't play?

---

### Post by raccoonstrait on 2014-09-10
Got Handbrake, and letting it run with defaults. Got an error when first started, it told me that my 2TB drive (less than half full) was out of space. It is reporting that there are 2.5 hours or so left on the decode, then I will test the file on the PI (it always worked in Windows and Linux). Let you know later.

BTW, thank you for the quick response.

Looking through the Docs  for Handbrake they don't tell much about the options, like Normal vs High Profile, nor does the list include Arm processors. I am sure there are differences, but what are they?

Raccoonstrait

---

### Post by raccoonstrait on 2014-09-10
The video is in a .avi container. Handbrake calls it MKV, but that again is beyond my ken.

I have plenty of other .avi files that do play, so it is what is in the container that is at issue. How does one tell?

Raccoonstrait

---

### Post by papibe on 2014-09-10
I believe HB uses /tmp as a temporary directory, so you may want to make sure there's enough space on your root partition (spaces and inodes). I haven't found a way to set another temp directory.

Here are details for each preset: [HandBrake's Built-In Presets]("https://trac.handbrake.fr/wiki/BuiltInPresets").

Even if you select a preset, you can fine tune the parameters by going to the 'Video' and 'Audio' tab and changing the parameters there. If you select 'Use Advance Options' the 'Advance' tab becomes available for more options.

Please note a correction made in my previous post. HB is available on the regular repos now. 
Regards.

---

### Post by raccoonstrait on 2014-09-10
Well, that appears to have worked, I only watch a few seconds of the film (it did use all of the HD screen), but that was better than what I was getting before. The size of the file went from 793.1 MB to 1.4 GB, but I could care less about that. I may try another test tonight, and set some different parameters, just to see what happens.

Thanks again,

Raccoonstrait

Oh, and you can mark this closed if you wish.

---

### Post by papibe on 2014-09-10
> **raccoonstrait said:**
> you can mark this closed if you wish.
You can do it yourself ;) [Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how.

Regards.

---

