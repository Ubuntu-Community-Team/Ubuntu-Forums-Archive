---
title: "Transcode a single title from a DVD?"
date: 2015-12-30
forum: Multimedia Software
---

### Post by SimonHGR on 2015-12-30
Hi all,

My precise problem is that I need to extract individual mpg files from each of the separate titles on a DVD. Also, I need to select a specific audio track while doing this. I would very much prefer to do this using command line tools so that I can write a single command to loop round all the titles, rather than have to manually intervene to create each one.

So far, I've tried handbrake and (c)vlc. Handbrake doesn't (seem to) allow me to choose the audio track, which is a fatal flaw for my needs. Also, it only seems willing to create mkv containers, which means I'd have to re-transcode everything afterwards. Further, it seems I have to manually tell it to extract every track individually. With cvlc, I came up with this:

[FONT=Courier New]  cvlc --audio-track 1 dvd:///dev/sr1#3:1[/FONT]

which sucessfully _plays_ the individual titles with the right audio, but as soon as I modify it to try to transcode:
[FONT=Courier New]
  cvlc --audio-track 1 dvd:///dev/sr1#3:1 --sout '#transcode{vcodec=mp4v, acodec=mpga} :standard{access=file, mux=mpg, dst=out1.mpg}'[/FONT]

it starts doing the entire disk again (plus, for some reason, both audio and video are horribly low quality, but I didn't bother investigating that, given the fatal flaw that it's not title-by-title any more).

Any suggestions? To recap, what's critical to me is a) the right audio track, and b) single-title output files. What's important but can survive without if I must is command line operation or batch processing.

TIA!
Simon

---

### Post by TheFu on 2015-12-31
**vobcopy** to get the correct track.
**handbrakeCLI** to transcode.  Trust me, you can select exactly which audio track to be transcoded/copied. It is in the extensive manpage, I believe.

---

### Post by SimonHGR on 2015-12-31
Oh, ok, thanks. I'll pursue handbrake further. Didn't even know it had a cli version, but that'll be great.

Much appreciated,
Cheers!

---

### Post by TheFu on 2015-12-31
There are many, many, many transcoders out there - most are based of ffmpeg code. mencoder, avconv, come to mind as alternatives too. With these, you can pick exactly which tracks (video/audio/text/subtitles) you want included in the new file and how to transcode any (or copy) you want.

I've never gotten acceptable results from VLC related to transcoding. Great viewer, but the transcoding parts never seem to work for me.

With HB-CLI, you can either specify everything with command line options or point to a "preset" created in the GUI handbrake tool. Sometimes this is easier.
Also, sometimes I find it useful to put existing videos into an MKV contain****er using mkvmerge to have easier control over all the different tracks/languages/audio that might be inside other video file formats. **mkvinfo** is very handy and **mkvextract** can pull the specific streams you want to retain out.

Anyway, there are many options.

---

### Post by SimonHGR on 2015-12-31
Indeed, the number of permutations just serves to make it harder, frankly. It becomes hard to find any particular piece of wood for the trees. Looking through the ffmpeg manuals is like trying to read the works of Shakespeare for a particular quotation. By the time you get half way through, you've usually forgotten what you came for! ;)

---

### Post by TheFu on 2015-12-31
> **SimonHGR said:**
> Indeed, the number of permutations just serves to make it harder, frankly. It becomes hard to find any particular piece of wood for the trees. Looking through the ffmpeg manuals is like trying to read the works of Shakespeare for a particular quotation. By the time you get half way through, you've usually forgotten what you came for! ;)

Yep. I learned what little I know a little at a time. When an old method didn't meet my needs, I found another solution (eventually). The change from mpeg2 to xvid to h.264 were times of large learning.  I still use mpeg2 stuff - broadcast TV here is mpeg2 even for 1080i stuff. Transcoding that to h.264 reduces the file sizes about 75% - more if commercials are removed. But for editing, mpeg2 is frame-accurate, unlike the F/LOSS tools for other video codecs.

I'm one of those people who wants all the audio tracks, captions, and subtitles in a single file, so the idea of removing all but 1 hurts me at a personal level.  After all, I might want to learn more Japanese or Thai or French or German or .... my hearing could go out and I'd need English captions - or I could lose my eyesight completely and need the English description audio in the future. Who knows? I don't.

So ... in summary, if I wanted 1 title/track of video, I'd use vobcopy to pull that off the media. Then I'd use handbrakeCLI (wrapped with a script) to transcode only the parts I wanted into a constant quality H.264 video + AC3 & AAC audio (I need both due to different players only supporting AAC, but I want 5.1 DD AC3 whenever possible in the home theatre room) + whatever captions + whatever subtitles into a single MKV file container.  If the caption files aren't in the language I want, I'd run them through a translation tool like apertium to create the language SRT file I want and add that to the MKV container (either before or after the transcoding).

Simple, if you do each step one-at-a-time over 10 yrs. ;)  Most of this is automated here, except the commercial removal part - that still requires manual validation, though a few tools do an excellent job of marking where commercials are in recordings, they aren't 100% and can miss entire blocks or get the start/end of a block wrong by 3 sec to 3 minutes, so that validation step of about 30 seconds is important to save 22 min of commercials from the files and remove the hassle of manually jumping each commercial block during viewing, IMHO.

Oh ... and I use ffmpeg for simple stuff mostly.  Removing video from files where only the audio is wanted or simple transcoding from dead vcodecs into something a player here can handle.

Why use vobcopy?  Because it is trivial to get the title you want. I'm sure that other tools do this, handbrake does, but sometimes there are "issues" which cannot be discussed. vobcopy handles about 95% of those issues for me, which is why it get's used.  For the last 5% with "issues", something like dd gets used then I can use *other tools* to address anything important.  There is a commercial tool for this - makemkv. Think it works, but it doesn't support captions, which is a non-starter for me.

IMHO. ....

Good luck. Start eating the elephant. ;)

---

### Post by andrew.46 on 2015-12-31
This page is a little out of date but does demonstrate a commandline method of extracting specific tracks:

FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

as well as working on the tracks and then remuxing. Needs a spring clean though...

---

### Post by SimonHGR on 2015-12-31
Well, this seems to be working as advertized. The only issue was this:

  [Handbrake-cli updated and now does not work]("http://askubuntu.com/questions/464865/handbrake-cli-updated-and-now-does-not-work")

which required me to manually fetch a working version of the handbrake tools.

Thanks!

---

### Post by TheFu on 2015-12-31
Best to always use a PPA for this stuff. I avoid directly downloading programs. Package management is in the top 3 reasons I prefer Debian/Linux over the other choices. [https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases) seems to be what I'd want - I'm an LTS-only guy.

---

### Post by SimonHGR on 2015-12-31
Oh, and FWIW, this was the command in the end that did exactly what I needed :)

[FONT=Courier New]for i in 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
do 
  HandBrakeCLI -t 3 -c $i -a 2 -i /dev/sr1 -o dvd-${i}.mpg
done[/FONT]

Thanks again!

---

### Post by TheFu on 2016-01-01
If all sequential, bash has a built-in for that ... 
```
for i in {1..24} ; do  echo $i; done
```

---

### Post by SimonHGR on 2016-10-30
Ah, didn't see this before. Nice, thank you !

---

