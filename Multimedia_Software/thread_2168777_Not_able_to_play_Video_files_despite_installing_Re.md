---
title: "Not able to play Video files despite installing Restricted Extras"
date: 2013-08-19
forum: Multimedia Software
---

### Post by 7Starphy on 2013-08-19
I am using an Acer V5 Netbook with a AMD Dual Core processor . I am running Xubuntu 12.04. I am not able to play any video files despite installing Ubuntu Restricted Extras. Audio Files work perfectly. Parole says it is not able to initialize the Xv output. Can anyone help me out ?

---

### Post by TheFu on 2013-08-19
I find the pre-installed media players to be crap.  Install VLC from the repo, be happy.  If VLC can't play it, then I don't need to view it. ;)
BTW, I've never heard of "parole" and switched away from XFCE about 3 yrs ago.  Ah - a lite-weight video player ... interesting.
A comparison is here: [http://www.omgubuntu.co.uk/2010/09/linux-movie-players-vlc-vs-totem-vs-parole](http://www.omgubuntu.co.uk/2010/09/linux-movie-players-vlc-vs-totem-vs-parole)
Thanks for the education.

I'd also point out that a netbook will probably have trouble playing any hidef videos.  Mine can't do more than 600p without stuttering. The higher resolutions need GPU help during playback so hidef mpeg2 and h.264 content can work, but only with GPU support and the correct drivers.

---

### Post by BlinkinCat on 2013-08-19
Hi,

I installed Xubuntu Restricted Extras, which I found to work fine.

Can't say if that is the reason for your problems - others may have a point of view.

Cheers - :)

---

### Post by 7Starphy on 2013-08-20
> **TheFu said:**
> I find the pre-installed media players to be crap.  Install VLC from the repo, be happy.  If VLC can't play it, then I don't need to view it. ;)
BTW, I've never heard of "parole" and switched away from XFCE about 3 yrs ago.  Ah - a lite-weight video player ... interesting.
A comparison is here: [http://www.omgubuntu.co.uk/2010/09/linux-movie-players-vlc-vs-totem-vs-parole](http://www.omgubuntu.co.uk/2010/09/linux-movie-players-vlc-vs-totem-vs-parole)
Thanks for the education.

I'd also point out that a netbook will probably have trouble playing any hidef videos.  Mine can't do more than 600p without stuttering. The higher resolutions need GPU help during playback so hidef mpeg2 and h.264 content can work, but only with GPU support and the correct drivers.


It is not playing in VLC also. Any suggestions on any specific drivers I need to install ?

---

### Post by howefield on 2013-08-20
Is it all video formats or a specific one that you are having trouble with ?

---

### Post by TheFu on 2013-08-20
> **7Starphy said:**
> It is not playing in VLC also. Any suggestions on any specific drivers I need to install ?

If this happens for any video files, then I suspect a video driver issue.
If the problem is with a specific file, then I suspect a corrupt download or DRM.

---

### Post by Mark Phelps on 2013-08-21
The problem is that your video player does not have the correct video codec installed to play the video file.

VLC can play nearly everything because it comes with its own codec files.

You should Google for "fourcc" -- as this is a 4 character code embedded in the video file indicating how it was encoded, and what codec you would need in order to play it back.  Once you know the codec, you can then do a search to see if it available for Linux.

---

### Post by 7Starphy on 2013-08-21
> **howefield said:**
> Is it all video formats or a specific one that you are having trouble with ?

No video format works perfectly. Flv doesnt work at all. In mp4 only Audio works . So I don't think the main problem is "format" specific . Looks as if some major driver is not installed at all :( Any help ? VLC itself is not able to play :(

---

### Post by 7Starphy on 2013-08-21
> **TheFu said:**
> If this happens for any video files, then I suspect a video driver issue.
If the problem is with a specific file, then I suspect a corrupt download or DRM.
I get an error like XV output not initialized in Parole. Does this help in diagnosing the problem ?

---

### Post by TheFu on 2013-08-21
> **7Starphy said:**
> No video format works perfectly. Flv doesnt work at all. In mp4 only Audio works . So I don't think the main problem is "format" specific . Looks as if some major driver is not installed at all :( Any help ? VLC itself is not able to play :(

FLV, MP4, AVI, WMV - these are all containers, not audio/video formats.  We need to know the codecs used.  There are many different ways to ask a file which codecs it needs - **VLC** will show it in the file info and/or codecs menu. **mplayer -identify** is another.

BTW, I have a TV recording that I transcoded recently using popular tools that plays video (h.264) perfectly, but no audio (mp4a) will playback.  I'm in the process of dumping the AC3 audio from the source file and merging it into the MKV container now. Even the stock version of VLC 2.0.8 wouldn't play the audio. Glad that I had the 5.1 AC3 source file still.  It would suck to have to build a custom version of any player to support a specific codec.  I'd rather not go through it at all. I'm a little pissed that the transcoder created a file that "sucks for me."  OTOH, it was a PBS show and the PBS guys are famous for following standards, but not doing it the way everyone else does.

So, if you can figure out which specific codecs your problem files need, that really is the first step. Until that happens, we are stuck. Will you please report back on the codecs? Please?  It may turn out to have NOTHING at all to do with your issue, but we aren't making any progress any other way either.

The Xv error is just a rendering method.  With other player programs, you can force different rendering engines to be used. Xv is sorta .... old. It has a place, but probably should be avoided since the mid-1990s, IMHO.

---

### Post by MrSteve on 2013-08-21
this maybe of no help at all as this is video not dvd

install libdvdcss2 and see if it plays as it maybe encrypted ...
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by 7Starphy on 2013-08-22
> **TheFu said:**
> FLV, MP4, AVI, WMV - these are all containers, not audio/video formats.  We need to know the codecs used.  There are many different ways to ask a file which codecs it needs - **VLC** will show it in the file info and/or codecs menu. **mplayer -identify** is another.

BTW, I have a TV recording that I transcoded recently using popular tools that plays video (h.264) perfectly, but no audio (mp4a) will playback.  I'm in the process of dumping the AC3 audio from the source file and merging it into the MKV container now. Even the stock version of VLC 2.0.8 wouldn't play the audio. Glad that I had the 5.1 AC3 source file still.  It would suck to have to build a custom version of any player to support a specific codec.  I'd rather not go through it at all. I'm a little pissed that the transcoder created a file that "sucks for me."  OTOH, it was a PBS show and the PBS guys are famous for following standards, but not doing it the way everyone else does.

So, if you can figure out which specific codecs your problem files need, that really is the first step. Until that happens, we are stuck. Will you please report back on the codecs? Please?  It may turn out to have NOTHING at all to do with your issue, but we aren't making any progress any other way either.

The Xv error is just a rendering method.  With other player programs, you can force different rendering engines to be used. Xv is sorta .... old. It has a place, but probably should be avoided since the mid-1990s, IMHO.

Ok, I tried playing a .flv video file with VLC. It did not play both the audio and the video. The Codec for Stream 0 (Video) was H264 - MPEG-4 AVC (part 10) (avc1)
The Codec for the audio was MPEG AAC Audio (mp4aa). This doesn't work . So am I to infer that my pc is not at all able to play codecs of this particular format? The .mp4 video file I tried to play was also had the same Audio and Video codecs. It didn't play the .mp4 also.

But surprisingly VLC played the audio of a .mkv video file and it tried playing the video ,but you know ,it was not at all smooth and it stuttered a lot. But it's video and audio codecs were the same! (H264-MPEG-4 AVC) and (MPEG AAC Audio ). Am I missing anything here?

My VLC is also able to play a .avi video file whose video and audio codecs were (MPEG-4 Video (DX50)) and (A52 Audio (aka AC3)(a52)). Ironically, it played the .avi file pretty well compared to the .mkv file. This looks like a good sign.

---

### Post by TheFu on 2013-08-22
Thanks.  No real answer. I did get my PBS show to playback with the copied audio from the source. VLC and XBMC couldn't deal with the transcoded audio.

I think mp4aa is an issue - that is an Apple format. Many things with AVC1 are 1080p content. I doubt that any netbook has that screen resolution or the CPU power to decode it without huge amounts of stuttering.  I don't have any video with mp4aa - we always avoid anything from Apple here.

Beyond the same codec names, there are different encoders each with slightly different outputs to the "standard." The codec name gets into the ballpark.

DX50 stuff was created before we had HiDef anything, so almost any netbook will play that just fine.

Are you certain the files are not corrupt?

---

### Post by 7Starphy on 2013-08-22
Yeah pretty sure! They work fine on my laptop. So "no-video" watching on my netbook? :(

---

### Post by TheFu on 2013-08-22
What is different between the laptop and the netbook?

---

### Post by 7Starphy on 2013-08-22
Laptop runs on Ubuntu 12.10 . 4-GB Ram . Quad-Core Processor with dedicated graphic card. It is way more advanced and powerful than my netbook which has a 2-GB ram, AMD Dual Core processor (it is easy to carry ,portable than a laptop ,which is why i have one). That is why I am running XUbuntu on my netbook as it is Lightweight and doesn't consume too much of my computer's limited resources. It has a decent hardware configuration , I don't think it is not capable of playing a Video properly :(

---

### Post by TheFu on 2013-08-22
Have you lined up the HW and SW for each machine in 2 columns and compared them?
* CPU
* RAM
* OS / Kernel
* GPU drivers
* codecs
* player software

I completely understand using a netbook.  When I get on an airplane or just need simple remote access, I take the netbook. When I drive and need more power, I take a Core i5 laptop.  I run Ubuntu Server on both with LXDE as a GUI on top.

I haven't seen any video refuse to play on my netbook that plays on any other device when DRM was not involved.  If your laptop can play the same videos, your netbook should play them ... just with stuttering if the resolution it high or the bitrates for video are too high.

If your laptop can play it, perhaps if you transcode the video down to 480p resolution, so it will playback on the netbook?  **Handbrake** can probably do this ... just avoid the i-Device presets and go for a DVD-resolution.  I'd share my own script for doing this stuff, but I deal with lots of other aspects and removing those dependencies would be too difficult.  If handbrake seems too daunting, there are other tools with much greater capabilities.

You did say that the DIVX5 encoding played fine on the netbook, right?

---

### Post by SeijiSensei on 2013-08-22
Most netbooks do not have enough CPU power to play highly-compressed video files like those encoded with H.264.  Some machines with Intel or ATI graphics chips support the vaapi standard, but not all players support that in Ubuntu.  You can give the method described [in this post](http://www.webupd8.org/2012/11/install-mplayer-with-va-api-hardware.html) a try and see if it helps.  Otherwise you'll want to stick to videos encoded in older formats like XviD which are not so processor-intensive as H.264.

Like the author of the linked article, I use **smplayer** to watch videos.  It's a well-designed and well-maintained GUI interface for mplayer/mplayer2.

---

### Post by 7Starphy on 2013-08-22
> **TheFu said:**
> Have you lined up the HW and SW for each machine in 2 columns and compared them?
* CPU
* RAM
* OS / Kernel
* GPU drivers
* codecs
* player software

I completely understand using a netbook.  When I get on an airplane or just need simple remote access, I take the netbook. When I drive and need more power, I take a Core i5 laptop.  I run Ubuntu Server on both with LXDE as a GUI on top.

I haven't seen any video refuse to play on my netbook that plays on any other device when DRM was not involved.  If your laptop can play the same videos, your netbook should play them ... just with stuttering if the resolution it high or the bitrates for video are too high.

If your laptop can play it, perhaps if you transcode the video down to 480p resolution, so it will playback on the netbook?  **Handbrake** can probably do this ... just avoid the i-Device presets and go for a DVD-resolution.  I'd share my own script for doing this stuff, but I deal with lots of other aspects and removing those dependencies would be too difficult.  If handbrake seems too daunting, there are other tools with much greater capabilities.



Oh! Ok , I understand the problem now to an extent. So you are suggesting converting my videos to the appropriate Netbook-friendly format using Handbrake? I guess I got fooled when the Acer guy said my netbook can play 720p videos fine. But there is my friend using a similar netbook running on Windows 7 ,I don't think he has any video problems. 
> ** TheFu said:**
> 
You did say that the DIVX5 encoding played fine on the netbook, right?


And yes DX50 seemed to work smoothly.

Is it for sure that this is more of a "hardware" problem than a Xubuntu problem ?

---

### Post by 7Starphy on 2013-08-22
> **SeijiSensei said:**
> Most netbooks do not have enough CPU power to play highly-compressed video files like those encoded with H.264.  Some machines with Intel or ATI graphics chips support the vaapi standard, but not all players support that in Ubuntu.  You can give the method described [in this post]("http://www.webupd8.org/2012/11/install-mplayer-with-va-api-hardware.html") a try and see if it helps.  Otherwise you'll want to stick to videos encoded in older formats like XviD which are not so processor-intensive as H.264.

Like the author of the linked article, I use **smplayer** to watch videos.  It's a well-designed and well-maintained GUI interface for mplayer/mplayer2.

Ok , I will try that out and check whether it works! Thanks!

---

### Post by juanfcuesta on 2013-11-19
[SIZE=2][FONT=arial]Hello Guys

I finally managed to watch H264 MPEG-4 on my netbook (Asus EEEPC 1015pn with 2GB RAM)

The trick was using the "vdpau" as video output driver. This was posted by: [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195")

*"You can give the method described [in this post]("http://www.webupd8.org/2012/11/install-mplayer-with-va-api-hardware.html") a try and see if it helps"*

As I'm using Nvidia, this one worked for me [http://www.webupd8.org/2010/10/use-mplayer-with-vaapi-support-hardware.html](http://www.webupd8.org/2010/10/use-mplayer-with-vaapi-support-hardware.html)

Thank you all!!!![/FONT][/SIZE]

---

