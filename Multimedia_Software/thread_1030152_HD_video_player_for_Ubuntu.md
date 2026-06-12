---
title: "HD video player for Ubuntu"
date: 2009-01-04
forum: Multimedia Software
---

### Post by kitts on 2009-01-04
Hi,

I wiped out vista and installed Ubuntu 8.10 (GNOME) on my Lenovo 
y510 with supposedly dolby digital 5.1 audio support.

I wanted to play 1080 H.264 compressed and mp4 wrapped movie 'the matrix'. VLC, Totem, M player are just not able play it with out frame dropping. the same movie could be played on nero showtime under winxp.

Any suggestions for good video player for the HD video.??:popcorn:

---

### Post by aamod on 2009-01-04
Well VLC Media Player 0.9 series would work best. Also, you can try MPlayer.

Enjoy :popcorn:

---

### Post by tgpraveen on 2009-01-04
well for me also vlc doesnt seem to do a good job.

is there not a  good HD player for linux?

also maybe it could also do more software emulation so that old hardware systems could play hd??

---

### Post by tgpraveen on 2009-01-04
well for me also vlc doesnt seem to do a good job.

is there not a  good HD player for linux?

also maybe it could also do more software emulation so that old hardware systems could play hd??

---

### Post by Acradon on 2009-01-04
I use Kaffeine and have watched some HD trailers on it with no problems. I find that Totem really doesn't cut it, however, vlc is also a good choice as far as codecs are concerned. 

Acradon

---

### Post by Entity` on 2009-01-04
But what about HD-DVD/Bluray movies?  Is there any way to play them in all their glory in Linux?

---

### Post by kitts on 2009-01-05
is vlc 0.9 series the latest version or an earlier version?

---

### Post by kitts on 2009-01-05
> **aamod said:**
> Well VLC Media Player 0.9 series would work best. Also, you can try MPlayer.

Enjoy :popcorn:
is version 0.9 the latest version or an older version? M player plays with lot of skips.. so is my VLC. I know Vlc is extremely good otherwise. But to play this high definition stuff..can it handle it?

---

### Post by shirilover on 2009-01-05
Playing HD video, particularly HD h.264 video, requires significant processing power. 
The video player you use will have very little to do with decoding the video stream. All h.264 video decoding is done by your CPU, and if you want smooth playback of a 1080p h.264 video stream, you need a powerful CPU to do the decoding. Also, do not expect the video card to help with decoding as there is no MPEG-4 hardware acceleration in linux.

Some things you can try:
When using mplayer, add -lavdopts fast:threads=2:skiploopfilter=all

It will get better when multi-threaded h.264 decoding is coded into libavcodec.

---

### Post by Lee_Machine on 2009-01-05
Due to legal BS its harder but here is the offical ubuntu howto

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

enjoy.

---

### Post by bsmith1051 on 2009-01-05
I have found VLC to be best but it requires a couple tweaks:

[LIST][*]in Tools > Preferences, click on Show Settings:All (radio button in bottom-left)
[*]under Input/Codecs > Other > FFmpeg,
set "Skip loop filter for h.264" = ALL[/LIST]

This improves h.264 playback a lot!  Also, if you're watching something interlaced (e.g. AVCHD camcorder files) you want to enable Video > Deinterlace > Discard.  You have to do this while the file is already playing, though.  There's a menu option buried in Settings but it doesn't seem to work.

Finally, if you go to the VideoLAN.org website you can find instructions to install their latest beta version (aka "1.0~git") which I think has slightly better h.264 playback, but at the 'cost' of lots of interface bugs :-(
[http://nightlies.videolan.org/](http://nightlies.videolan.org/)

---

### Post by kitts on 2009-01-05
> **shirilover said:**
> Playing HD video, particularly HD h.264 video, requires significant processing power. 
The video player you use will have very little to do with decoding the video stream. All h.264 video decoding is done by your CPU, and if you want smooth playback of a 1080p h.264 video stream, you need a powerful CPU to do the decoding. Also, do not expect the video card to help with decoding as there is no MPEG-4 hardware acceleration in linux.

Some things you can try:
When using mplayer, add -lavdopts fast:threads=2:skiploopfilter=all

It will get better when multi-threaded h.264 decoding is coded into libavcodec.

I am aware that it eats up lot of cpu processing as is the case on xp. I have got 1 GB RAM, intel pentium dual core 1.6GHz chipset..which configuration is fairly sufficient to play the video. There aren't many players which it play smoothly not even on Xp.

---

### Post by kitts on 2009-01-05
> **Lee_Machine said:**
> Due to legal BS its harder but here is the offical ubuntu howto

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

enjoy.

The link provides solutions to HDdvd. i want to play h.264 video wrapped in mp4 format which is sort of rip  i guess. Does this file also got some encryption..i dont think so?

---

### Post by kitts on 2009-01-05
> **bsmith1051 said:**
> I have found VLC to be best but it requires a couple tweaks:

[LIST][*]in Tools > Preferences, click on Show Settings:All (radio button in bottom-left)
[*]under Input/Codecs > Other > FFmpeg,
set "Skip loop filter for h.264" = ALL[/LIST]

This improves h.264 playback a lot!  Also, if you're watching something interlaced (e.g. AVCHD camcorder files) you want to enable Video > Deinterlace > Discard.  You have to do this while the file is already playing, though.  There's a menu option buried in Settings but it doesn't seem to work.

Finally, if you go to the VideoLAN.org website you can find instructions to install their latest beta version (aka "1.0~git") which I think has slightly better h.264 playback, but at the 'cost' of lots of interface bugs :-(
[http://nightlies.videolan.org/](http://nightlies.videolan.org/)

i tried ur codec setting...not much change though.:(

---

### Post by Nepherte on 2009-01-05
No they don't use encryption, but BluRay uses H.264 so just skip the encryption part. Get a svn version of mplayer and ffmpeg.

---

### Post by kitts on 2009-01-05
I understand that any player built to play these HD VIDEO fall under FAIR USE>interoperability of independent program.
Surely any anti-circumvention deencryption of the above also falls under exception to violation of access controls.

But the dumping thing suggested above posts is a violation of access controls like the earlier 'css' technology atleast int the US under the DMCA,1998.

---

### Post by bsmith1051 on 2009-01-05
> **kitts said:**
> I am aware that it eats up lot of cpu processing as is the case on xp. I have got 1 GB RAM, intel pentium dual core 1.6GHz chipset..which configuration is fairly sufficient to play the video. There aren't many players which it play smoothly not even on Xp.
"fairly" or "barely" ?

Your 1.6 GHz processor is only going to be able to play 480p, or _maybe_ 720p, resolution h.264 files, even on Windows.  I've heard that the Core AVC codec (on Windows) is very efficient, though -- is that what you're using?  Also, the existing codecs on Linux only use 1 cpu/core.  So if/when they support dual-core you may have better results.

Long-term, you want a graphics card with h.264 support to handle all heavy decoding work, but none of that works under Linux yet.  What video card do you have?  And, is this a desktop (where you could upgrade the video) or a laptop (where you can't) ?
____________

Nevermind that last question, I just reviewed your original post and saw that you have a Lenovo Y510 laptop.  I'm assuming that you have the Intel X3100 video card and the 1280x800 LCD?  If so, why are you trying to playback 1080p video files?  Download the 720p versions and they'll match-up with your screen.  Anything higher-res is a waste of effort unless you're driving an external 1080p screen.

---

### Post by kitts on 2009-01-05
> **bsmith1051 said:**
> "fairly" or "barely" ?

Your 1.6 GHz processor is only going to be able to play 480p, or _maybe_ 720p, resolution h.264 files, even on Windows.  I've heard that the Core AVC codec (on Windows) is very efficient, though -- is that what you're using?  Also, the existing codecs on Linux only use 1 cpu/core.  So if/when they support dual-core you may have better results.

Long-term, you want a graphics card with h.264 support to handle all heavy decoding work, but none of that works under Linux yet.  What video card do you have?  And, is this a desktop (where you could upgrade the video) or a laptop (where you can't) ?
____________

Nevermind that last question, I just reviewed your original post and saw that you have a Lenovo Y510 laptop.  I'm assuming that you have the Intel X3100 video card and the 1280x800 LCD?  If so, why are you trying to playback 1080p video files?  Download the 720p versions and they'll match-up with your screen.  Anything higher-res is a waste of effort unless you're driving an external 1080p screen.

is laptop...

---

### Post by kitts on 2009-01-06
M player is doing the job 95% after setting the avoid skip thing. Audio..is pretty low..for whatever reasons.
Could anyone tell whats the reason for low audio in h.264 1080 HD video?
some issues with decoding or ?

---

### Post by mbobak on 2009-01-06
Wow!  Those mplayer options you suggested seem to be the magic solution!

I've not been able play a 720p h.264 file until I tried those options!


Thanks!

-Mark

---

### Post by Major_Kong on 2009-01-06
> **shirilover said:**
> Playing HD video, particularly HD h.264 video, requires significant processing power. 
The video player you use will have very little to do with decoding the video stream. All h.264 video decoding is done by your CPU, and if you want smooth playback of a 1080p h.264 video stream, you need a powerful CPU to do the decoding. Also, do not expect the video card to help with decoding as there is no MPEG-4 hardware acceleration in linux.

Some things you can try:
When using mplayer, add -lavdopts fast:threads=2:skiploopfilter=all

It will get better when multi-threaded h.264 decoding is coded into libavcodec.

+/-

Now there's VDPAU ([http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)). I think the latest (svn) version of ffmpeg has it now. And there's a patch for mplayer too.

---

### Post by Eddie Wilson on 2009-01-06
> **kitts said:**
> I understand that any player built to play these HD VIDEO fall under FAIR USE>interoperability of independent program.
Surely any anti-circumvention deencryption of the above also falls under exception to violation of access controls.

But the dumping thing suggested above posts is a violation of access controls like the earlier 'css' technology atleast int the US under the DMCA,1998.

What are you trying to say?:confused:

---

### Post by kitts on 2009-01-14
> **Eddie Wilson said:**
> What are you trying to say?:confused:
I am trying to understand the legality of decryption of HD video under the US anti circumvention laws (DMCA, 1998).

---

### Post by markbuntu on 2009-01-14
GPU driver support is why HD playback works in windows machines with slow cpus. The gpu driver takes the decoding and rendering load off the cpu.

ATI has recently hinted that h.264 and blue ray playback gpu hardware support will soon be added to their linux driver some time in the next few months. The newer hardware already has it, it is just a matter of encoding it into the driver.

All we can do is wait.

---

### Post by Adfc on 2009-02-13
> **bsmith1051 said:**
> I have found VLC to be best but it requires a couple tweaks:

[LIST][*]in Tools > Preferences, click on Show Settings:All (radio button in bottom-left)
[*]under Input/Codecs > Other > FFmpeg,
set "Skip loop filter for h.264" = ALL[/LIST]


Thank you very much, because your suggestion solved my problem!

---

### Post by Dr Zin on 2009-02-13
But My Mplayer player is freaking out and it will not load.

---

### Post by arkangelboss on 2012-03-04
Originally Posted by **bsmith1051** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6498643#post6498643") 				
 				[I]I have found VLC to be best but it requires a couple tweaks:

[LIST]
[*]in Tools > Preferences, click on Show Settings:All (radio button in bottom-left)
[*]under Input/Codecs > Other > FFmpeg,
set "Skip loop filter for h.264" = ALL
[/LIST]
[/I]


> **Adfc said:**
> Thank you very much, because your suggestion solved my problem!

Worked even for VLC 1.1.11!!!! Thanks a lot!

---

### Post by sffvba[e0rt on 2012-03-04
Back to sleep **old** thread...


404

---

