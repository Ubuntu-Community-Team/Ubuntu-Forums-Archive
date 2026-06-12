---
title: "This was a job for DeVeDe!  Or so I thought ..."
date: 2023-10-09
forum: Multimedia Software
---

### Post by Langstracht on 2023-10-09
I have a bunch of .mkv files that I want to put on to playable DVD's.

The files are all about 670Mb.

I added the first 6 to DeVeDe making no modifications to the defaults and, admittedly after a bit of a wait, ended up with a "good" DVD.(menu works, no video stuttering, fine audio ....)

Buoyed by this success I added the next 6 files to DeVeDe and let her rip - so to speak.

The result was NOT good.

The 4 Gb of mkv's was transformed by DeVeDe into 6.6 Gb of mpg's AND a 6.6 Gb .iso file which, of course resulted in no DVD burn.

I guess I'd like to know what is going on/wrong.  But far more importantly does anyone know how to fix this behaviour..

II it matters I'm using DeVeDe 4.8.0

TIA for any and all help.

---

### Post by TheFu on 2023-10-09
DVDs that can play on any DVD player have a mandated format, files, audio and video codecs.  MKV is a container than can hold nearly anything, including video and audio that aren't supported by the DVD mandates. This means that whatever tool is being used will almost always need to transcode the input files to a format that can be supported for DVD playback.

DVDs support mpeg2 video at either 480p (NTSC) or 576p (PAL).  I don't recall the exact audio codecs supported, but I think it is 5.1 channel AC3 PCM or 2 channel PCM audio. I could be wrong on that.

So, if the transcoding of the mkv files creates video that is larger than the size for the specific DVD disc used, then the burning will fail.  I think DVDs come in 4GB and 8GB sizes.  Which size do you have?  It should be clear if you try to put 6GB into a 4GB DVD, it won't work.

Many DVD players can deal with common mp4 containers and h.264/aac video/audio files stored as normal files these days.  Check what your specific DVD players support, since it would be better to just ensure the resolution 720x480p or 720x576p are provided.  Let me check some things ... 

For letterbox DVDs, the resolution can be 720:358 @ 23.98fps.
720:576 @ 25.00fps is for PAL.

I've never used DeVeDe.  I'm always trying to get stuff off mpeg2/DVDs to a smaller, better, more universal, format.  Long ago, I did put media backups onto DVDs. Had a bunch of scripts that would find optimal groupings of different files to full a DVD based on size (standard file system, not ISO/VOB files). That's the opposite of what you want.

---

### Post by mocha on 2024-01-06
Still using DVD Video format?  May I suggest simply burning all the MKVs to a blank BluRay or DVD as files.  I think that's a much better way to do it if you really insist on optical media as the storage medium.  Also, pretty much all standalone BluRay and DVD players are able to read ISO discs for at least the past 5 years.

---

### Post by SeijiSensei on 2024-01-06
Unless you're sharing these files with someone that has only a standard DVD player, then DeVeDe is the only solution I know of. 

Otherwise put the MKV files onto the DVD as data files as mocha suggests. Most modern players know how to handle those, although some, especially Sony products, will balk at some codecs and containers. The best universal solution I've found is mpeg4 video + AAC audio in the .mp4 container.

---

### Post by littlepeon on 2024-01-22
Ok, so it has been a while with no updates, but this is in response to your original post. I would suggest finding a Blu-Ray player or older DVD player that can read/play MKVs, because it is a much better and advanced codec than the DVD format. First of all it supports higher bit-rates and video quality. DVDs are basically 480p- anything over that is overkill. Secondly, MKVs support better file compression-- so you can get a better quality picture for a smaller file size. MKV shrinks filesize needed on a grand 1:8 ratio. So you are experiencing the fact that for your 4GB of MKV files, you are going to need 32GB of space(which is impossible with the DVD architecture--even DVD9 only have a 8.7GB capacity!) I would suggest breaking up the files and converting them one by one. First, install ffmpeg on your system. You can convert the MKV to either mpeg2 or vob(i suggest straight to vob). With ffmepg you can do this with ```
ffmpeg -i input.avi -target ntsc-dvd output.vob
```
This will transform a MKV file into a nice mpeg2 vob that DeVeDee can use. You can then use this file as an input file format for the program. You may like DeVeeDee, but I suggest using DvdStylerNG as it is still being updated.

---

