---
title: "H264 ripping is WAY too slow - faster alternatives?"
date: 2008-06-02
forum: Multimedia Software
---

### Post by bluepowder7 on 2008-06-02
so i'm going through my (legal) DVD collection, and want to make some smaller 700meg or so files on the computer so that i don't have to lug around my originals and mess around with eject / insert / wait.  i'm ripping using VLC and using an MP4 container with H264 video / MP4 audio.  except that it's PAINFULLY slow, like real time or slower.

isn't there a faster way of ripping while keeping good quality?  i tried some of the other encoding options in VLC, but either they're pretty lame and mosaic-y or they don't do a proper time thing (can't skip around using the Alt-arrow hotkeys).

btw - i'm running 7.10 64-bit on an athlon 64 x2 4000 w/ 2g ram machine, and VLC 0.8.6c

---

### Post by disturbedite on 2008-06-02
you can set the settings that x264/h264 rips with to make it rip/encode faster.

but give theora video/ogg audio a try.  there are apps in the repo specifically for ripping/encoding to theora/ogg.  (with the ogm or ogg file extension).  i'd recommend 10 for audio & video quality.

---

### Post by bluepowder7 on 2008-06-02
where are the x264 settings?  in the vlc options windows, i can only set the video scaling and video bitrate, nothing more.  is there some specific config file for x264 that i need to find and edit?  and what should i edit?

i also tried the theora / vorbis options in vlc, and they went nowhere.  created a 0 byte file and then seized.

---

### Post by 4Orbs on 2008-06-02
The fastest codec I've used is divx and its faster because it encodes from both ends of the movie at the same time. Don't know if the free version uses bi-directional encoding, but the pro version did the last time I used it. I think DVDrip includes a divx codec in the install, but don't know which version or if its bi-directional. Last time I used divx I could achieve a single pass of a 2 hour movie in about 1 1/2 hour, this was back in my pre-Linux days.

Also, its much quicker if you first rip the vob files to a temp folder rather than do the encoding direct from disc. But the temp folder should be located where there is enough room to hold the enormous vob GB's

---

### Post by bluepowder7 on 2008-06-02
ok, i've ripped the dvd into a vob file on the hard drive, plenty of space, but the h264 encoding (via the VLC interface) is still as slow as before - well, maybe 10% faster at best.  still pretty well real time, instead of 4x or (pipedream) 10x.  if i just encode mp4 with around 2kbps video, it goes at a good rate (close to 4x), but the quality is noticeably worse.  i'm just doing short 2-minute test clips for now to see how things go.

strangely enough, if i shove it (h264 video + whatever audio) into an mp4 container, it plays normally, but if i shove it into a mpeg-ts container, video takes a while to kick in and then is flakey (pauses, glitches, doesn't Alt-arrow skip all that well)

should i be using a whole different front-end, or setting the encoding options externally somehow?  i'd prefer a gui, but i can deal with cli if i have to.

---

### Post by cariboo on 2008-06-03
Give acidrip a try. Its available in the repositories

Jim

---

### Post by cor2y on 2008-06-03
I have only tried encoding with vlc for video internet streams like asf files to avi container with divx or mpeg1 or mpeg2.
But if you are ripping my advice rip the vob then encode and encode with another encoding tool like ffmpeg or mencoder or avidemux.
In general x264 encoding is always slow because unlike xvid, or theora its very very cpu intensive the output looks great but it takes a long time to encode, i don't know how much is a long time for you but in general a regular sized (640x480 or 720x480) x264 encode of a 80 min dvd movie takes me about 7 to 9 hrs depending on what settings i use so i set everything up and simply let the pc run while i am asleep,  people who upconvert (1280x720 and higher resolutions) their video have longer waiting times.
However  this was with me using an Athlon XP 2800 cpu maybe with your dual core X2 4000+ it should be quicker , i have the exact same cpu with 2gb of ram but i haven't encoded a dvd rip to X264 in a while i now stick with xvid or the divx mpeg4 encoder, the lavc mpeg4/divx  encoder has come a long way from its early days.
If you are interested in not using vlc for the encode like i said avidemux for a gui frontend ,ffmpeg or mencoder for cmdline/terminal , also there are three scripts that can help with encoding/ripping from a dvd.
[divxenc]("http://divxenc.sourceforge.net/") (mpeg divx encoding script via mencoder), [H264enc]("http://h264enc.sourceforge.net/") (X264 encoding script via mencoder) and [xvidenc]("http://xvidenc.sourceforge.net/") (Xivd encoding script via mencoder) these scripts allow outputing to mp4 format with aac audio once the correct encoders are installed on ubuntu.

---

### Post by eye208 on 2008-06-03
> **bluepowder7 said:**
> so i'm going through my (legal) DVD collection, and want to make some smaller 700meg or so files on the computer so that i don't have to lug around my originals and mess around with eject / insert / wait.  i'm ripping using VLC and using an MP4 container with H264 video / MP4 audio.  except that it's PAINFULLY slow, like real time or slower.
Your approach to video encoding is totally wrong. You are doing constant bitrate encoding with VLC to meet a certain target file size. And since constant bitrate encoding yields the worst results possible, you are trying to make up for it by using the best codec available which is x264. You are fixing the problem at the wrong end.

You would be much better off using Xvid instead off x264, and two passes instead of one. I know what you're thinking now: x264 is better than Xvid. Yes, but **constant bitrate** x264 is much worse than **variable bitrate** Xvid. And since Xvid encodes much faster than x264, both passes will not take longer than one x264 pass.

x264 is no magic bullet. Using x264 makes sense only if you are willing to spend the increased encoding time. That's when x264 really shines over Xvid.

---

### Post by bluepowder7 on 2008-06-03
> **cor2y said:**
> But if you are ripping my advice rip the vob then encode with another encoding tool like ffmpeg or mencoder or avidemux.
In general x264 encoding is always slow because unlike xvid, or theora its very very cpu intensive the output looks great but it takes a long time to encode

i installed vobcopy and got the vobs onto the hard drive.  doing the vlc h264 encoding doesn't appear to be any faster, but it is more convenient!  if i could have enough hard drive space, i'd just keep the vobs since the quality is wicked and the vobcopy speed is quick!  alas, at around 4gigs a pop, it'll eat up space quickly.


> **cor2y said:**
> in general a regular sized (640x480 or 720x480) x264 encode of a 80 min dvd movie takes me about 7 to 9 hrs using an Athlon XP 2800 cpu maybe with your dual core X2 4000+ it should be quicker

wow, 7-9 hours would be molasses speed!  i'm currently getting it to encode at a bit less than real-time, so for a 100 minute movie, it might take 120 minutes.  if i fire up the system monitor, the encoding is only pinning one of the two cores at 100%, leaving the other mostly unused.  it'll swing from one core to the other (i guess to let the first one cool down?), but it doesn't seem like it's using all of the available resources.  is it possible to somehow make it use both cores (100% on one and maybe 70% on the other) since the only thing i'm doing while it's encoding is working on some documents (open office stuff)?


> **cor2y said:**
> If you are interested in not using vlc for the encode like i said avidemux for a gui frontend ,ffmpeg or mencoder for cmdline/terminal , also there are three scripts that can help with encoding/ripping from a dvd.

thanks, i'll look into those.  the OS install here is fairly recent (only a few months), so presumably i have adequate codecs floating around.  is there a quick way to check which specific ones i have and how old they are?



> **eye208 said:**
> Your approach to video encoding is totally wrong. You are doing constant bitrate encoding with VLC to meet a certain target file size. And since constant bitrate encoding yields the worst results possible, you are trying to make up for it by using the best codec available which is x264. You are fixing the problem at the wrong end.

am i?  in the vlc options for transcoding, i'm setting the codec and bitrate, but not the file size.  i ran some tests on short 2-min clips and i'm picking a bitrate that'll result in an acceptable file size in the end - and i'm not all that demanding about it, so whether it's 760meg or 823meg or 902meg, they're all ok, but 1.7gig would be excessive for a 90-min flick.  when i right-click for the audio / video properties of the finished file, the bitrates both show "NA".  does that mean that it actually encoded vbr?  and, is the bitrate i'm selecting just the average, and it's automagically going variable during encoding?  or does vlc always do a cbr (or nearly cbr) but doesn't store the bit rate info?


> **eye208 said:**
> You would be much better off using Xvid instead off x264, and two passes instead of one. I know what you're thinking now: x264 is better than Xvid. Yes, but **constant bitrate** x264 is much worse than **variable bitrate** Xvid. And since Xvid encodes much faster than x264, both passes will not take longer than one x264 pass.

is variable bit rate x264 possible?  if i open up acidrip and select the x264 codec, the file size & passes & bitrate fields are all grayed out, preventing me from setting anything (as if x264 has no options at all).  if i select xvid, then yeah i can select an approx file size, check the bitrate / bit-per-pix, and do 2-pass encoding.  is the bitrate in acid going to be vbr (so that what i enter is just an average)?  back in the early-90's when i was first using lame for my music, i seem to recall being able to select vbr'ing as well as roughly how variable it'll be - something like "0 = keep it fairly steady" to "10 = go nuts"


> **eye208 said:**
> x264 is no magic bullet. Using x264 makes sense only if you are willing to spend the increased encoding time. That's when x264 really shines over Xvid.

i'm currently encoding at approx real time, which i guess seems slow in comparison to going all-mp4, but the quality is nice.  is it even remotely possible to make it go twice as fast without having to buy a new $300 processor?  i'd rather spend the $300 on a few 1TB hard drives and do away with encoding altogether (keeping just the vobs around).  or keep the $300 in my bank!!!

having read and said all that, i'll do some time & quality trials with what i know how to use for now:

vlc - h264, 1024 kb/s video bit rate (variable?)
acid - x264, no options to set :(
acid - xvid, 2-pass, roughly 1000 kb/s bit rate (variable?)
ffmpeg / mencoder / etc - hmm, i'll have to read up on how to use those

btw - when using acid, which container format works better for those encoders?  avi or mpg?


.

---

### Post by aeiah on 2008-06-03
> **bluepowder7 said:**
> 
btw - when using acid, which container format works better for those encoders?  avi or mpg?


.

you should use avi. if you stick with x264 then consider .mkv, especially if subtitles are involved.

you'll get the best results from command line stuff as you can be more specific, but if you find that there's not much difference then go back to acidrip or something then. i use acidrip and i find a multipass xvid usually works out better than an x264, just because there doesnt seem to be much control over the x264 codec from inside acidrip. if you want to really get into it, you're best heading over to doom9.org and / or checking out what bitrates scene release groups encode in x264 at

---

### Post by bluepowder7 on 2008-06-03
ok, i dunno what i did wrong, but acidrip + xvid 2-pass is SLOW.  1st pass took over an hour for a 1h-20min film, and now it's doing the 2nd pass which will take nearly THREE HOURS.  it's clicking along at a marvelous 14-15 fps.  ouch.

one thing i noticed in the debug window is:

```

Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(

```

i had scaling and cropping turned off.  was that bad?  i was presuming that it'll just maintain the same 720x480 resolution as is on the dvd.

i'm wondering if i should kill the encoding now since it's WAY slower than i had thought it would be.  i'm not sure that i can live with 4+ hours to do a full encode of a 1h-20min movie.  i was planning on having my videos converted before the end of the month.  :P

---

### Post by FakeOutdoorsman on 2008-06-03
I use ffmpeg to encode to x264 after I rip with vobcopy, but I generally encode short films and not feature-length videos.  Also, I haven't encountered any subtitled films, so I can't comment on that.  I did a quick test on a 30 second film: the first pass took 13.3 seconds and the second took 43 seconds on my P4 3GHz.  So using those numbers, and all things being equal, I guess it would take around 220 minutes to encode a 120 minute video on my machine.

ffmpeg from the repository has not been compiled to support restricted codecs and formats, so you will either need to get it from the Medibuntu repository, or you can get the bleeding-edge: [HOWTO Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095").  I like compiling since ffmpeg and x264 development is quite active.

Here is the test script I used:
```
#!/bin/sh
time ffmpeg -y -i $1 -pass 1 -threads auto -vcodec libx264 -b 800k -bt 192k -flags +loop -cmp +chroma -partitions 0 -me_method epzs -subq 1 -trellis 0 -refs 1 -coder 1 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -an $2

time ffmpeg -y -i $1 -pass 2 -threads auto -vcodec libx264 -b 800k -bt 192k -flags +loop -cmp +chroma -partitions +parti4x4+partp4x4+partp8x8+partb8x8 -me_method umh -subq 5 -trellis 1 -refs 3 -coder 1 -me_range 16 -g 300 -keyint_min 30 -sc_threshold 40 -i_qfactor 0.71 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -acodec libfaac -ab 196k -ac 2 $2
```
Make the script executable (chmod +x convert.sh) and then run it (./convert.sh input.vob output.mp4).

---

### Post by disturbedite on 2008-06-04
> **bluepowder7 said:**
> where are the x264 settings?  in the vlc options windows, i can only set the video scaling and video bitrate, nothing more.  is there some specific config file for x264 that i need to find and edit?  and what should i edit?

i also tried the theora / vorbis options in vlc, and they went nowhere.  created a 0 byte file and then seized.
don't use vlc.  use avidemux.

---

### Post by eye208 on 2008-06-04
If you can live with somewhat unpredictable file sizes, there is a third option besides constant bitrate and average bitrate, and that is constant quality aka. constant quantizer.

Constant quality encoding requires only one pass. The idea is to choose a quality setting (i.e. a quantizer value), and the codec will allocate just as many bits as needed to keep quality on that level. The result will be a variable bitrate file.

The reason why VLC doesn't offer anything except constant bitrate is because it was designed to stream content over a network. This is when you need predictable bitrates. VLC was never meant to be a transcoding tool. Avidemux, MEncoder and FFMPEG are much better suited for that.

Regarding the container format, MP4 is perfect if both video and audio are MPEG encoded (ASP, H.264/AVC, AAC, MP3). If there is non-MPEG content involved (Theora, Vorbis, SRT/SSA subtitles etc.) use MKV instead.

Do not use AVI. It is considered obsolete because it lacks support for many essential MPEG-4 features (VFR video, VBR audio, B-frames) and subtitle streams.

---

### Post by bluepowder7 on 2008-06-05
(ah crap!  wrote, tried to post, got error, now have to retype it all...)

thanks for the various tips!  i'm using the h264enc script to encode through mplayer / mencoder.  it's still a slow process (guess h264 codecs have limits!), but it does give me more options for encoding!  i'm seeing that it can do 2-pass as well as 1-pass-constant-quality, so maybe THAT'S the option for me to use!  since i'm not TOO particular about file size, i can live with a bit of unpredictability.  it's not like they're going onto CD-R's or anything.  hopefully, one or two tries will give me a rough feel for how big things get.

one thing i did notice, though, is that on some films, i get skipped frame notices.  i wonder if that means that the frame rates aren't matching up, and i need to do some conversions...  time to dig!

btw - not to sidetrack my own thread, but:  i loaded up what appears to be the ubuntu-studio set of A/V tools (which then reset my nvidia driver and added a GRUB menu, but that's another issue).  from the massive list of tools, is there a package i should get familiar with that will let me look at what frame rate / interlacing / audio tracks / etc are actually happening on a DVD / VOB file?  and perhaps even edit out some of the first few seconds of films, the parts that contain splash screens of studio logos and whatnot (some are just a bit too long).

---

### Post by JEDIDIAH on 2008-06-05
> **eye208 said:**
> Your approach to video encoding is totally wrong. You are doing constant bitrate encoding with VLC to meet a certain target file size. And since constant bitrate encoding yields the worst results possible, you are trying to make up for it by using the best codec available which is x264. You are fixing the problem at the wrong end.

You would be much better off using Xvid instead off x264, and two passes instead of one. I know what you're thinking now: x264 is better than Xvid. Yes, but **constant bitrate** x264 is much worse than **variable bitrate** Xvid. And since Xvid encodes much faster than x264, both passes will not take longer than one x264 pass.

x264 is no magic bullet. Using x264 makes sense only if you are willing to spend the increased encoding time. That's when x264 really shines over Xvid.

Variable xvid is NOT better than x264. It's certainly not "much" better. xvid is a lot faster but it comes with a quality tradeoff. For most content it may not matter. For higher bitrate DVD stuff and some TV stuff it will matter and even niave viewers will be able to notice the difference.

Ultimately you need to try different options and see what you think works best. Your own eyeballs are the final arbiter.

---

### Post by JEDIDIAH on 2008-06-05
> **bluepowder7 said:**
> so i'm going through my (legal) DVD collection, and want to make some smaller 700meg or so files on the computer so that i don't have to lug around my originals and mess around with eject / insert / wait.  i'm ripping using VLC and using an MP4 container with H264 video / MP4 audio.  except that it's PAINFULLY slow, like real time or slower.

isn't there a faster way of ripping while keeping good quality?  i tried some of the other encoding options in VLC, but either they're pretty lame and mosaic-y or they don't do a proper time thing (can't skip around using the Alt-arrow hotkeys).

btw - i'm running 7.10 64-bit on an athlon 64 x2 4000 w/ 2g ram machine, and VLC 0.8.6c

This is computationally intensive stuff. Expect it to take awhile, especially for a large DVD collection. It's bound to take awhile
even with the "quickest available" options.

Compromising on the file size might help though. 700m seems a bit small
for a feature film (and I am sure others will disagree).

---

### Post by bluepowder7 on 2008-06-05
ok, so after using the **h264enc** script to encode a few flicks, i'm loving it.  turns out that what i was after all along was easily done using the constant-quality function, which just lets me set the quantizer to my preferred quality level, and let the file size be what it needs to be.  after running two or three trials, i can narrow it down to a quality level that spits out nice quality videos with a (roughly) 500megs-an-hour file size.  kick in some deinterlacing and frame-rate fixing down to 24p, and it's "perfect"!  fixed up the nasty interlacing on "March Of The Penguins" and kept great detail in the opening scene of "Lord Of War" (pinstriping on suit, chickenwire fence in background, spreading of smoke, etc) - at least those were the two i used as "benchmarks" since the funky content is within the first few minutes of the film.

as far as speeds, i'm getting somewhat slower than real-time (not as good as 4X, but sure beats 6 hours of waiting), and it's using up both processor cores to at least 95%, so i'm happy there!

thank you for all the help (and also to the author of the h264enc script!).  i'm getting great results, and learning a bunch of things along the way.

(i might try xvid to see if i can get similar results in half the time - though if the xvid results i got through acidrip are anything to go by, they'll be awful)

.

---

### Post by klavsk on 2009-09-04
@bluepowder7: Care to share what options you use for h264enc ? it sounds like you've found the magical option combination  :)

---

