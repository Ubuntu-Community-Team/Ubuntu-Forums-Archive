---
title: "Create DVD using MP4 with embedded subtitle"
date: 2012-11-23
forum: Multimedia Software
---

### Post by LoungeLizard on 2012-11-23
I have a MP4 file that has a subtitle track (playing it in VLC show the subtitle being there and can be activated).  Using "devede" and playing with a few settings (primarily changing the deinterlace setting), I can get the MP4 to create an ISO that I can burn - but mounting the ISO to test it shows that there is no subtitle track.  I've done a bunch of research and am running into circles and spending a lot of time getting nowhere.  Anyone know how do I get the subtitle track to get encoded into the ISO image?

-- da Lizard

---

### Post by evilsoup on 2012-11-24
What you're probably running into is DVDs supporting less types of subtitles than MP4 files. Most modern subtitles are stored in marked-up plaintext, SRT seems to be the most common; but DVD subtitles are stored as a sort of image file. I think DeVeDe can convert text-based subtitles to DVD-subtitles, but it has problems detecting them within a file (or it did when I tried using it a while ago), so you could try manually extracting them first.

To extract the subtitle track, use MP4Box, a command-line tool. There is probably a GUI frontend out there somewhere; WinFF can probably do this, if nothing else (though that's an ffmpeg frontened). Or Avidemux. Anyway, from [here](http://denihow.com/how-to-extract-subtitles-from-mp4-and-mkv-movies/):
```
MP4Box -info input.mp4
```
will give you the track ID. Then:
```
MP4Box input.mp4 -srt *n*
```
where *n* is the track ID (normally 3). This will create a file called input_3_text.srt, or something similar. You should be able to use this separate file in DeVeDe as a source for your subtitle.

---

