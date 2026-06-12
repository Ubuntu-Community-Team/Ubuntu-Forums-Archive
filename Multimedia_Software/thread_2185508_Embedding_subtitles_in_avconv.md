---
title: "Embedding subtitles in avconv"
date: 2013-11-02
forum: Multimedia Software
---

### Post by rubensaurus on 2013-11-02
Hi, I was wondering how to embed subtitles (srt) using avconv.

---

### Post by TheFu on 2013-11-03
I dont know, but you can take any file and add SRTs to an mkv container that will work.

**mkvmerge -o output-file.mkv avconve-output.mp4 all-the-captions.en.srt all-the-captions.es.srt all-the-captions.fr.srt all-the-captions.br.srt**

The video/audio part can be 1 file or 2 or 5 as well.  MKV containers are really awesome.

There is a way to force a specific subtitle to be displayed by default too - much better than forcing them to be burned into the video stream.
_Embed_ can have 2 meanings. Please clarify.

Of course, if your playback device doesnt like MKV, then we need to know the exact container AND the exact video + audio codecs used.
Also, there are many, many, many options for avconv, so the best way to know exactly which options are available with the version on your system is through the man page.  **man avconv** should explain. I would look for _srt_ there.

---

### Post by rubensaurus on 2013-11-03
The video is a matroska file. My device doesn't play mkv, so I usually change the containers to mp4. In this case, I'd like to keep the subtitles,  audio,  video while changing the container from mkv to mp4.

I also have some files that are mkv and have the subtitles in srt format that havent been placed in the video.

I'm pretty new to Linux and using avconv, so I'll try my best to supply you with the information needed

---

### Post by TheFu on 2013-11-03
avconv has _copy_ modes.  I would use mkvexport to dump all the different tracks, then find a way to shove those into the mp4 container without transcoding.  If done properly, it should be as fast as a file copy.

If you **are not** trying to script this, then using a GUI tool like **handbrake** or **avidemux** is probably easier.  Handbrake is probably the easiest, but it may transcode every time. I am unsure of how to include SRTs with avidemux - though the tool will help to convert SUB/idx files into SRTs with powerful glyph matching.

Sorry I cant help more.  avconv is not part of my normal toolkits.  I use lots of other things daily, but all my systems support MKV, so I am always converting MP4 into the, better, MKV containers.  Google found this:
[http://askubuntu.com/questions/50433/how-to-convert-mkv-file-into-mp4-file-losslessly](http://askubuntu.com/questions/50433/how-to-convert-mkv-file-into-mp4-file-losslessly) - but since that time, avconv options have probably changed.  Sadly, RTFM is probably the best answer I can provide.  Can you post a few of the commands that you have tried and how they failed?

With MKV it is possible to change aspect ratios, resync audio playback, add multiple video and audio tracks .... simply amazing what changing some settings in a track header can do without transcoding anything. Alas, that doesnt help you.

---

### Post by rubensaurus on 2013-11-03
i've tried -scodec copy, -c:s copy, -map 0:2 but i'm probably doing it wrong. to change containers i normalle use avconv -i input.mkv -vcodec copy -acodec copy output.mp4

i've tried doing avconv -i input.mkv -vcodec copy -acodec copy -scodec copy output.mp4 (or c:s copy; -map 0:2 in place of -scodec copy).

for errors ill get something like:

[mp4 @ 0x1695960] Application provided invalid, non monotonically increasing dts to muxer in stream 0: -83 >= -83
av_interleaved_write_frame(): Invalid argument

or 

Encoder (codec id 0) not found for output stream #0:0

Thanks for your help though! It just caught my attention since I found a video where the .srt file was seperate-- the mkv file wasn't in English, but the srt file shows the English subtitles. Can't watch the video since the .srt file is no longer "embedded' in the video anymore

---

### Post by SeijiSensei on 2013-11-03
I don't believe it is possible to use the copying modes while attaching and synchronizing subtitles.  You might have to write an entirely new encoded file.  That's obviously true if you convert the subs to hard subs, since they will need to burned into the picture.  With soft subs it should be possible to avoid encoding the streams again, but I don't know for sure.

I suggest taking a look at the **mkvtoolnix** package from the repositories as well.  That provides utilities like  mkvextract and mkvmerge which let you disassemble and reassemble Matroska files.

---

### Post by FakeOutdoorsman on 2013-11-04
MP4 is picky when it comes to subtitles support. You can try "-codec:s mov_text". Results may vary.

Alternatively, as SeijiSensei mentioned, you can use hard subs as a last resort. See [How to burn subtitles into the video](https://trac.ffmpeg.org/wiki/How%20to%20burn%20subtitles%20into%20the%20video) and the [FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide). Note that you'll have to use ffmpeg from FFmpeg; not avconv or the libav version of "ffmpeg" in the repo since libav lacks the required features. Just another little bonus from the switch to libav for the Ubuntu users.

You can simply download a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) or follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

---

