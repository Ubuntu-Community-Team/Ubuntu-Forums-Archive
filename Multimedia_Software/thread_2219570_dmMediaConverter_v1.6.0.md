---
title: "dmMediaConverter v1.6.0"
date: 2014-04-24
forum: Multimedia Software
---

### Post by mdalacu on 2014-04-24
[IMG]http://3.bp.blogspot.com/-MzzUeP2vkCE/VFN-LI5HXoI/AAAAAAAAn9c/XtfwJjHJn2Y/s1600/Screenshot%2Bfrom%2B2014-10-31%2B12%3A30%3A13.png[/IMG]
[IMG]http://2.bp.blogspot.com/-0TRvyLRXEwg/U3xeMmBUMLI/AAAAAAAAi8w/4C44hwteYoA/s1600/Screenshot+from+2014-05-21+11:04:34.png[/IMG]
dmMediaConverter is a FFmpeg frontend (GUI) exposing some of its features. It is intended to be simple and easy to use but also to be able to achieve complex tasks. I have inspired myself from a lot of media converters like Handbrake, WinFF and MkvMergeGui. One feature was lacking from most of them, video stream copy (pass through), that made me build this.

For download and more details, here: [http://dmsimpleapps.blogspot.com/2014/04/dmmediaconverter.html]("http://dmsimpleapps.blogspot.com/2014/04/dmmediaconverter.html")
**UPDATE**: **[COLOR="#FF0000"]DEB files[/COLOR]** are available for x86 and x64!

Now you can download it from **Ubuntu Software Center**! *Here it cost **[COLOR="#FF0000"]3$[/COLOR]** and it will be considered a donation*. It takes time to get the app updated into Ubuntu repository.
[https://apps.ubuntu.com/cat/applications/dmmediaconverter/]("https://apps.ubuntu.com/cat/applications/dmmediaconverter/")

---

### Post by mdalacu on 2014-04-25
Version 0.7 is up! :)

---

### Post by FakeOutdoorsman on 2014-04-25
Is the source code available? I wanted to see what ffmpeg commands you are using.

---

### Post by mdalacu on 2014-04-25
> **FakeOutdoorsman said:**
> Is the source code available? I wanted to see what ffmpeg commands you are using.

No, or at least, not yet. As I have stated in the blog post I have not decided if I will ever make the source code svailable.

---

### Post by andrew.46 on 2014-04-25
Perhaps have a quick look here:

FFmpeg License and Legal Considerations
[https://www.ffmpeg.org/legal.html](https://www.ffmpeg.org/legal.html)

Best get this sorted at the beginning :)

---

### Post by mdalacu on 2014-04-26
I really need to read this legal xxxx. I only bundle my app with an ffmpeg(.exe) statically build, from another site. I am not using libav and not compiling my self or modify the sorce code for ffmpeg / libav. Do i need to take any action or not? I will have to find out.

---

### Post by mdalacu on 2014-05-03
Within a week I will publish a first stable version with all the features prezented.

---

### Post by mdalacu on 2014-05-15
As promised, version 0.8 is up. It is a stable build with all intended features working.
Enjoy.

---

### Post by mdalacu on 2014-05-21
Version 0.9 is up. Some UI cleanups.

---

### Post by mdalacu on 2014-05-28
Version v0.9.7 is up. Added support for VP8, VP9,Vorbis, Opus so you can save in webp format.

---

### Post by mdalacu on 2014-05-30
Version 0.9.8 is up.
Added x86 and x64 **[COLOR=#ff0000]DEB files[/COLOR]**! :p

---

### Post by mdalacu on 2014-06-20
The app is now available in Ubuntu Software Center! :popcorn:
[https://apps.ubuntu.com/cat/applications/dmmediaconverter/](https://apps.ubuntu.com/cat/applications/dmmediaconverter/)

---

### Post by andrew.46 on 2014-06-20
Congrats :).

---

### Post by mdalacu on 2014-06-20
Thanks. :-)

---

### Post by mdalacu on 2014-07-03
Version 0.9.9 is up. :guitar:

---

### Post by Nistegmos on 2014-07-03
Thanks so much for your good program.  I was able to use it on first try for converting some videos I'd downloaded that didn't play correctly.  After I used your easy program to convert to MKV with a different audio codec, the videos played.  This makes it very handy for me because my home computer doesn't have internet access, so I can't update the codecs.  But since you made the program available as a Debian archive, I was able to download it from a different computer and put it on a flash drive.  Thanks so much!

---

### Post by mdalacu on 2014-07-06
@Nistegmos. Thank you for your kind words and i am glad that you liked it.

---

### Post by mdalacu on 2014-08-21
[dmMediaConverter]("http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html")  v1.0.0
MAJOR RELEASE! New Features!

- Stream Profiles! 
- Bulk Convert mode! Convert multiple files at once.
- 2 pass encoding for video codecs 
- DeShake filter (not so good ...)
- Creation_time tag
- HiDPI support
- Added all ISO 639-2 language codes :-) - Added color coded stream types for easy identification.&#65279;

I hope you like it and please, provide feedback.
thanks.

---

### Post by mdalacu on 2014-09-12
**ANOTHER BIG RELEASE!**
 - Added Preferences in main menu. [COLOR="#FF0000"]Please learn how to use Latest option because in the feature i will not ship FFmpeg anymore.[/COLOR]
 - Added Test Run.
 - Now you can rearrange and remove source files.
 - Metadata edit for stream and container.
 - Show complete stream and container info.
 - x264 and x265 extra settings field (ex. put there bluraycompat, etc)
 - More output container options.
 - On failure does not clear settings.

Have fun and, please, provide feedback!
Thx.

[http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html](http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html)

---

### Post by mc4man on 2014-09-13
when using the 'system'  ffmpeg option in prefs then something in your start up 'thinks' there are missing binaries though the conversion does work as ffmpeg is a valid command.
(doesn't really matter where the binaries are, by default here they're in /opt/ffmpeg symlinked to /usr/bin. Also tried ~/bin 

Also would be good to have a libfdk_aac option for aac encoding

---

### Post by mdalacu on 2014-09-14
> **mc4man said:**
> when using the 'system'  ffmpeg option in prefs then something in your start up 'thinks' there are missing binaries though the conversion does work as ffmpeg is a valid command.
(doesn't really matter where the binaries are, by default here they're in /opt/ffmpeg symlinked to /usr/bin. Also tried ~/bin 

Also would be good to have a libfdk_aac option for aac encoding

Yes you are right, this is a bug... i will try not to check for existing file with system installed option sellected. Regarding libfdk_aac i will re investigate if it is possible to support it.
Thank you for reporting this.

---

### Post by mdalacu on 2014-09-16
> **mc4man said:**
> when using the 'system'  ffmpeg option in prefs then something in your start up 'thinks' there are missing binaries though the conversion does work as ffmpeg is a valid command.
(doesn't really matter where the binaries are, by default here they're in /opt/ffmpeg symlinked to /usr/bin. Also tried ~/bin 

Also would be good to have a libfdk_aac option for aac encoding

Version v1.2.0 is up, mainly bug fixing.

---

### Post by mdalacu on 2014-10-31
New release: v1.5.0!
Changelog:
- Parallel jobs - you can run multiple jobs in the same time
- Initial job progress implementation
- Split UI improvements
- Running under WINE is more robust now (Mac Os)
- Internal code rework - multithreading
- Some bugs fixed
- Updated FFMpeg binary with latest version

I hope you like it and please provide feedback!&#65279;
 
[http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html](http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html)

---

### Post by mdalacu on 2015-01-23
I have made 2 videos demoing the app.
Basic demo 1: [https://www.youtube.com/watch?v=BMyJLoZ1SCk](https://www.youtube.com/watch?v=BMyJLoZ1SCk)
mp4 to mp3: [https://www.youtube.com/watch?v=rZR40mdFRoQ](https://www.youtube.com/watch?v=rZR40mdFRoQ)

Feedback please.

---

### Post by mdalacu on 2015-02-06
Version 1.6.0 is up! :-)

Minor release:
- Added checkup for not overwriting the source file.
- You can assign dmMediaConverter to open media files. (ex. Right clik on file and "Open with..." dmMediaConverter's executable). You can use it like media info.
- Now bitrate will be shown in kbit/s for better readability. 
- Small UI fixes 
- Updated FFMpeg binary with latest version&#65279;

[http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html](http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html)

---

### Post by mdalacu on 2015-05-22
[http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html](http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html)
Version 1.7.0 is up ;)

- Burn text based subtitles (not yet picture based).
- Now you can manually specify additional FFMpeg filters (More) for audio and video streams.
- On linux it removes automatically "'" from metadata. Workaround for MKVToolNix generated files.
- Added option for auto add subtitle file (only *.srt for now).
- Small UI fixes and bugfixing
- Updated FFMpeg binary with latest version&#65279;

---

### Post by mdalacu on 2015-09-21
[http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html](http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html)
Version 1.8.0 is up ;)

- Watermark. Doubble click on image to quickly position the logo.
- First Mac OSX native build. Available on Amazon for 5$.
- Estimate encoded stream size if the encoding type is CBR.
- Small UI fixes and refinements.
- Small bugs fixes.
- Updated FFMpeg binary with latest version.

---

