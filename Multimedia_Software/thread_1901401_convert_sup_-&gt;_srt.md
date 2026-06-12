---
title: "convert sup -&gt; srt"
date: 2011-12-28
forum: Multimedia Software
---

### Post by ubuntukid on 2011-12-28
I have a jailbroken Apple TV which I use to watch my movie collection which I store on a NAS device. I'm currently using MakeMKV and Handbrake to rip and convert my DVD movies and this has worked quite well. The problem I'm having though is that I can't seem to find any software for Linux for converting sup files (dvd subtitles) to the srt format. I've gone through the software archive on doom9.org, but couldn't find anything there. Does anyone know of any software for this?

I haven't tried using Wine yet with any of the windows software. I prefer to use native software, but if none exists, I'll use Wine and the windows program Subtitle Edit.

---

### Post by rubylaser on 2011-12-28
Here's how I do it. This will require the Windows program Suprip, but it works very well in Wine.

```
mkvmerge -i Videos/FIREFLY_DISC_3/title00.mkv 
```
It will output something like this...

```
File 'Videos/FIREFLY_DISC_3/title00.mkv': container: Matroska 
Track ID 1: video (V_MPEG4/ISO/AVC) 
Track ID 2: audio (A_DTS) 
Track ID 3: subtitles (S_HDMV/PGS) 
Chapters: 13 entries
```
Here you can see the subtitles are track 3, so let's get them with mkvextract...

```
mkvextract tracks Videos/FIREFLY_DISC_3/title00.mkv 3:subtitles.sup
```
It will output something like this...

```
Extracting track 3 with the CodecID 'S_HDMV/PGS' to the file 'subtitles.sup'. Container format: SUP 
Progress: 100%
```
This will create a .sup file which unfortunately does not work in an mkv container, so we'll need to convert it to a .srt file with suprip, a winders program :(

```
mkdir suprip && cd suprip
wget  http://exar.ch/suprip/suprip-1.16.rar
unrar x suprip-1.16.rar && rm suprip-1.16.rar
```
Then run Suprip.exe with wine

```
wine Suprip.exe
```
Once in Suprip, set these options in the lower lefthand corner...

```
Space width: 10
Character Split Tolerance: 3
Character Similarity Tolerance: 20
```
Suprip is an OCR program, so you'll have to go through all the characters that aren't recognized, and input the right letters, after doing about the first 40 or so subtitles, it should know almost all the characters and be able to auto complete most of the rest for you.

Once your done, you can save out an .srt file to give to handbrake to include in your encode.

Here's a quick example of extracting your audio and video and mux it back together. One thing that's weird about mkvmerge, is that it defaults video tracks to 25fps as opposed to 23.976 like a film's proper framerate.

```
rubylaser$ mkvmerge -i Ip\ Man.mkv 
File 'Ip Man.mkv': container: Matroska
Track ID 1: video (V_MPEG4/ISO/AVC)
Track ID 2: audio (A_AC3)
Track ID 3: subtitles (S_TEXT/UTF8)
```
then rip the tracks out that you need...

```
mkvextract tracks Ip\ Man.mkv 1:video.h264 2:audio.ac3
```
mux it back together with the subtitle srt file with the video at the correct framerate...

```
mkvmerge -o ~/Movies/Ip\ Man_muxed.mkv --default-duration 0:23.976fps video.h264 audio.ac3 subs.srt
```
You can also pass chapters in too if you have them

```
mkvmerge -o ~/Movies/Ip\ Man_muxed.mkv --default-duration 0:23.976fps video.h264 audio.ac3 subs.srt --chapters chapters.xml
```

---

