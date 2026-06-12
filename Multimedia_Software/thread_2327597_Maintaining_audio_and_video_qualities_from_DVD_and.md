---
title: "Maintaining audio and video qualities from DVD and Blu-ray to MP4"
date: 2016-06-12
forum: Multimedia Software
---

### Post by kc_2 on 2016-06-12
I own a sci-fi collection that I want to put onto 1 external drive. It consists of 95 discs total (1 blu-ray, 94 DVDs).

I want to rip each disc twice: 1) exact clone, and 2) MP4 with original audio & video qualities.

MP4, as far as I know, is required for compatibility via USB playback on TVs, blu-ray players, etc. I'll also use Videostream/Chromecast, but need the USB option.

Considering DVD quality is already lacking compared to present day productions, I'd like to maintain that quality with the MP4s.

After testing some MP4 rips, the quality is horrible, far below even DVD audio and video.

How do I rip the discs as exact clones?

How can I rip the discs to MP4 and maintain the exact same audio/video qualities as the originals?

Thank you!

---

### Post by X-RED_Tech on 2016-06-13
Install and use Handbrake. Easy GUI and effective.

---

### Post by kc_2 on 2016-06-13
I'll check it out, thank you.

What settings would I use?

Would this keep the original quality:
Standard MPEG-4 part 14 digital multimedia format
Codec: h264 + aac
(I already have software that has this option (above.))

Or this:
container: mp4
codec: h.264
quality level: 21
speed: medium
sound bitrate: 224
sound type: AAC
(I don't have software yet that gets specific like with "quality level".)

---

### Post by shantiq on 2016-06-13
```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk
```

to install handbrake then run in terminal:

```
time HandBrakeCLI -i /dev/cdrom -o outfile.mp4 -e x264  -E copy:aac  --all-subtitles -q 1
```


this will copy audio and video and retain quality also add subs; **time** beforehand tells you how long it took

for extra options see ```
HandBrakeCLI -h
```

---

### Post by Andreas_Zeitler on 2016-06-13
I'd like to chime in on the same problem. As the OP mentions "exact copy" especially, this is also what I'm looking for. An exact copy would imply to me to rip a DVD to disk, with the same content as the original has. Using something like HandBrake does a "rip and then encode". Since I haven't found anything that works well in 16.04 Xenial, I would like to ask the same question. We tried to use Brasero. With some pre-complications we were able to install libdvdcss but now I'm stuck with a stupid "can't read" error in Brasero. 

To the OP, here is a [list of things that are supposed to work with Ubuntu]("https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs") but apparently hasn't been updated for 16.04.  I couldn't find good info on AcidRip, Thoggen, or k9copy. Any help I'd greatly appreciate.

---

### Post by shantiq on 2016-06-13
&#10122; exact copy of dvd = put into drive >>  drag folder into hard or external drive=perfect copy    

&#10123; use vobcopy

```
 vobcopy -m
```


&#10124; for an mp4 or mkv keeping specs **[>>do ]("http://ubuntuforums.org/showthread.php?t=2327597&p=13503430#post13503430")**

---

### Post by kc_2 on 2016-06-13
> **shantiq said:**
> ```

sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk
```

to install handbrake then run in terminal:

```
time HandBrakeCLI -i /dev/cdrom -o outfile.mp4 -e x264  -E copy:aac  --all-subtitles -q 1
```


this will copy audio and video and retain quality also add subs; **time** beforehand tells you how long it took

for extra options see ```
HandBrakeCLI -h
```

It sounds like that's an excellent way to get MP4s at original quality. Just to make sure, the x264 and aac will use the original qualities, right? Does that apply to both Blu-ray and DVD? I only have 1 blu-ray for this collection, the original movie, all the DVDs are of the TV shows, but I'd like to keep the original qualities with both types of discs.

> **Andreas_Zeitler said:**
> I'd like to chime in on the same problem. As the OP mentions "exact copy" especially, this is also what I'm looking for. An exact copy would imply to me to rip a DVD to disk, with the same content as the original has. Using something like HandBrake does a "rip and then encode". Since I haven't found anything that works well in 16.04 Xenial, I would like to ask the same question. We tried to use Brasero. With some pre-complications we were able to install libdvdcss but now I'm stuck with a stupid "can't read" error in Brasero. 

To the OP, here is a [list of things that are supposed to work with Ubuntu]("https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs") but apparently hasn't been updated for 16.04. I couldn't find good info on AcidRip, Thoggen, or k9copy. Any help I'd greatly appreciate.

You are right, in addition to MP4s, I also want exact copies of the discs. I found one way to do it, although don't like that the way I found is with a Windows program. I'd rather use Linux. Regarding Windows, the WinX Ripper Platinum app has an option, "Clone DVD to ISO image" with description "1:1 copy DVD to ISO image - the full DVVD clone backup solution. The target ISO file playable with VLC player and easy to burn to DVD disc." That is exactly what I want to do, only on Linux.

> **shantiq said:**
> &#10122; exact copy of dvd = put into drive >> drag folder into hard or external drive=perfect copy 

&#10123; use vobcopy

```
 vobcopy -m
```


&#10124; for an mp4 or mkv keeping specs **[>>do ]("http://ubuntuforums.org/showthread.php?t=2327597&p=13503430#post13503430")**

I never thought a simple drag-and-drop would be a way to get an exact copy, that's pretty cool.

I'll check out vobcopy. Thanks! What do you mean by ">>do" for keeping specs with MP4?

On a side note, I want these to be MP4s so they're more likely to work on more models of TVs with USB ports, and also because they should definitely work with Videostream/Chromecast.

I want the exact copies (as VOBs or ISOs or whatever it takes) so I can both play back as mock blu-ray/DVDs directly from computers, and also for the purpose of having as backups. I know that one of these days those discs are going to get scratched up or they'll break... or maybe the external drive will die, then I'll have the discs still, to make more backups from. I just hope I don't lose both originals and backups. I invested a good bit of $$$ into that movie/TV show collection.

---

### Post by kc_2 on 2016-06-16
...I need an external blu-ray burner... initially so I can put my blu-ray movie on the external hard drive, as mentioned above, but also to back up files, save some space on the main drives. Is there a good one that is compatible for the purposes of my goal here with my movie/tv collection?

---

### Post by TheFu on 2016-06-18
I know lots of people who want all the menus from the dics - for them, **vobcopy -m** is the way.  Not all players will playback DVDs with menus.  For myself, I prefer extremely high quality transcodes with all the audio tracks, subtitles and captions included inside an MKV container.  MKV files are well supported these days.  The only trick is that chromecasts demand h.264 video and AAC audio.  That means DTS and DD and DD+ audio cannot be used.  Further, normal chromecast players automatically select the first audio track from any file, so that needs to be AAC with the number of channels the audio system connected to the chromecast can support.  

Of course, much of this can be mitigated by using a transcoding media server like Plex on a computer powerful enough to transcode on-the-fly to whatever format is needed by the player.  This way, you can retain the highest quality on disk and let plex transcode to the relatively bad quality a chromecast needs.  If you deploy a Raspberry Pi v2 or later, you can passthru the 7.1 audio to a receiver and maintain excellent audio reproduction.

Oh ... and I find that using a "quality setting" of 21 to cause artifacts.  I'd rather trade off a little more disk and use 19 for the QF setting.  I usually shove all the audio tracks into the MKV file and transcode the 5.1 into AAC.  Someday I might want to learn French, after all. ;)

I also use handbrake and handbrakeCLI to transcode.  For years, I used mencoder and ffmpeg and played with avconv, but found cropping to the smallest useful video resolution (remove black bars at the sides, top and bottom) easiest in handbrake. Automatic settings in all the tools sometimes get the wrong crop.

Cannot suggest anything about bluray.  Won't have it in my house due to personal reasons.

While you can use mp4 as the container, mkv is much more flexible. If your playback devices support mkv as a container, I'd highly recommend it.  All my players the last 5 yrs have.

---

### Post by kc_2 on 2016-06-21
Thank you for the response, TheFu, very insightful. What you talk about in it makes me curious to know more.

> **TheFu said:**
> I know lots of people who want all the menus from the dics - for them, **vobcopy -m** is the way. Not all players will playback DVDs with menus. For myself, I prefer extremely high quality transcodes with all the audio tracks, subtitles and captions included inside an MKV container. MKV files are well supported these days. The only trick is that chromecasts demand h.264 video and AAC audio. That means DTS and DD and DD+ audio cannot be used. Further, normal chromecast players automatically select the first audio track from any file, so that needs to be AAC with the number of channels the audio system connected to the chromecast can support.

Is quality lost if using vobcopy -m?

Does Chromecast forcibly reduce the qualities in MKVs?

I thought h.264 and AAC are good. What's the difference among all of those things?

Basically, I just want to keep the quality of my DVDs (and the 1 BD) when I put them onto the external drive, and for them to be able to play via USB-to-TV and via casting-to-TV (using my chromecast).

> Of course, much of this can be mitigated by using a transcoding media server like Plex on a computer powerful enough to transcode on-the-fly to whatever format is needed by the player. This way, you can retain the highest quality on disk and let plex transcode to the relatively bad quality a chromecast needs. If you deploy a Raspberry Pi v2 or later, you can passthru the 7.1 audio to a receiver and maintain excellent audio reproduction.

I've heard of Plex, haven't looked into it other than a quick google. Is it free? The only drawback to using a powerful computer is that presently I don't have that option.

I do have a couple Pi devices, an old Pi 1st gen, currently using OSMC on it, and a new Pi 3, using multiple cameras with it for surveillance, although will be setting the new Pi up for dual purpose, keeping the cameras running when not using it directly and otherwise using it as a generic *nix system. I'm using motionEyeOS right now on the Pi 3, but need to figure out if I'm going to put a more complete linux/bash/etc. build on top of that or if I should redo it with *nix and put motionEye on top. Anyway, I have a couple external hard drives that I use for watching videos on the old Pi with OSMC, but I haven't done a lot with either Pi, really, and I tend to just watch the external drives either via USB to blu-ray player or directly to TV, or via Chromecast with the drives hooked up to a laptop.

As for audio, I don't have much for speaker options right now, some old equipment including old 5.1 that require traditional speaker wire and an old poweramp/receiver for them, but haven't bothered with hooking that stuff back up to the TV (after a recent move). I'm just using cheap 2.1 computer speakers hooked up to the TV right now, but eventually I want to go back to 5.1 and perhaps more speakers later on down the road.

> Oh ... and I find that using a "quality setting" of 21 to cause artifacts. I'd rather trade off a little more disk and use 19 for the QF setting. I usually shove all the audio tracks into the MKV file and transcode the 5.1 into AAC. Someday I might want to learn French, after all. ;)

I have noooo idea what quality 21, 19, etc. mean... or QF... it's all French to me. I'd love to have a resource that talks about all the details of audio/video stuff within the context of these discussions, but a resource that's easy to understand without getting too "scientific".

> I also use handbrake and handbrakeCLI to transcode. For years, I used mencoder and ffmpeg and played with avconv, but found cropping to the smallest useful video resolution (remove black bars at the sides, top and bottom) easiest in handbrake. Automatic settings in all the tools sometimes get the wrong crop.

Okay, so another +1 for handbrake/handbrakCLI, cool. I've heard of mencoder/ffmpeg, I think once upon a time I even experimented with them somewhat, but never really did much. I've never messed with cropping videos. Of my 250-hour collection of DVDs(+1bd), I'm glad that the older discs - from when the 1st TV show was commonly aired in that boxy ratio - anyway I'm glad that they're at least widescreen and not stretched out. I don't mind the black bars on top/bottom, just glad the video isn't stretched.

> Cannot suggest anything about bluray. Won't have it in my house due to personal reasons.

Only 1 disc is blu-ray, the very 1st one in the collection. The movie was released in '94 but I own the blu-ray version of it. All 3 TV shows (and their TV movies) are all on DVDs. I could've purchased the final seasons of the 2nd show and only 1 of the 2 seasons of the 3rd show on blu-ray but didn't want to mess with that. I don't know, it just felt more consistent for all of them to be DVDs, so I bought all DVDs.

If all of those shows/movies were produced with technologies that would make full use of the qualities available through BD, and of course if they were actually all available on BDs, then I would've bought them on BDs instead. Since they're DVDs (480p? I don't know (I need to learn more about all of this)), one advantage to if they were on BDs would be more would fit on 1 disc, but that's all moot considering I'm going away from discs entirely by putting all the shows/movies on an external drive.

> While you can use mp4 as the container, mkv is much more flexible. If your playback devices support mkv as a container, I'd highly recommend it. All my players the last 5 yrs have.

I don't know if my TV's USB or blu-ray player's USB support MKV playback. I want to say they don't, they're old/cheap TV/BD player, but I'd have to check and see.

Quick edit - when I use chromecast, I almost always use videostream with it... actually, I think I use it 100% of the time with it.

---

### Post by TheFu on 2016-06-22
Don't know what "videostream" is.  I only use the chromecast to watch local media, usually recorded TV, from plex. Since it doesn't support mpeg2, that media must be transcoded to be viewed.

vobcopy does just that - make a copy.   Chromecast cannot play those files, however, since these are mpeg2 for DVDs.
The manpage for vobcopy has more details.

---

