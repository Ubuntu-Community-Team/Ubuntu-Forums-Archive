---
title: "Need some help with ffmpeg audio"
date: 2008-11-25
forum: Multimedia Software
---

### Post by xeddog on 2008-11-25
I have been using my computer to download video (mostly tv shows) using TED and Azureus.  I have mediatomb installed to stream (serve?) the  downloaded video to my D-Link DSM-520.  It works fairly well except when the file format isn't supported.  It seems like most high definition video is in .mkv file formats (containers?) which are not supported.  

I have downloaded a script from the internet that extracts the audio, video, and subtitle pieces from the mkv container using mkvextract.  Mkvextract produces a temp .avi video file, a temp .ogg audio file, and .srt subtitles files.  That seems to go well.

It then uses ffmpeg to do the actual transcoding.  I used the tutorial on this site to upgrade to the latest x264 and ffmpeg (FFmpeg version SVN-r15898 which is now a couple of days old) and that also seemed to work well.  (Good tutorial by the way)

I have come across several sets of arguments that allow me to play the transcoded videos on my computer with good video and audio.  I finally suck with a single set of video arguments and only changed audio arguments to try to get this worked out, but when I try to view the files using the D-Link, one of three things happens.

1.  I get an error message telling me that the codec is not supported.  I can deal with that one.

2.  The video will begin to play nicely but the audio is missing.  Then, about 6-8 seconds into the video, it will start displaying only about 1 or two frames per second.  When that happens, there will be a "chirp" for the audio that roughly corresponds to the frame-by-frame display of the video.

3.  The video will play nicely but there is absolutely no audio.

(remember, this is without changing any of the video arguments.  Just the audio arguments)

The D-link manual says that the supported audio formats are MP3, WMA, Wav & Aiff (PCM only), and Vorbis.  The supported video formats are WMV9, MPEG-1, MPEG-2, DVR-MS, XviD, AVI (MPEG-4 layer only), and MPEG-4 ASP only.  I can get the video working for me, but I need some help now with the audio.  

When running ffmpeg I have tried using "-acodec vorbis", "-acodec copy", "-acodec libmp3lame", and "-acodec libfaac" all with an assortment of other parameters, and I just cannot get the audio working.  I ran a "ffmpeg --formats" command and tried some other of the codecs, but many of them are not found.  Such as MP2, MP3, and I think aac (or was it AC3?).

The only thing I have found that does work is avidemux.  I like it a lot, but it is a little S  L   O   O  O  O  O  W.  To transcode a 7 minute 1080p video takes over an hour.  Imagine what a full 1080P movie would take.  (I have a P-III 2.4GHZ machine with 1GB ram).  When using ffmpeg, the same 7 minute input file transcodes quite a bit faster.  Don't know exactly how much faster because when running the transcode I also specify "-vframes 1000" to save some time. 

So now the questions.  Is there a way to see what the equivalent commandline arguments for avidemux might be?  If I could see them maybe I could match them to ffmpeg parameters.

Or, has anyone managed to get this working with a D-Link DSM-520?  I have sent several emails to the D-Link support email address but they have been totally unresponsive.  I think I just need to figure out the specific audio parameters that the D-Link is expecting.

Any help would be appreciated.

TIA,

xeddog

---

