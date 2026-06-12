---
title: "dmMediaConverter v2.1.0 - FFmpeg GUI [Linux/Windows/Mac (wine))]"
date: 2017-04-04
forum: Multimedia Software
---

### Post by mdalacu on 2017-04-04
[IMG]https://4.bp.blogspot.com/-5u3Xx7Y3vzY/WNzJnh3musI/AAAAAAABT8s/b6aPZvwgxpQdF89q7T3E-cDhs7MCP1IewCLcB/s1600/Screenshot_2017-03-30_12-00-59.png[/IMG]
#dmMediaConverter 
[http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html](http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html)
Version 2.1.0 is up
- Now you can have special characters in file names on windows and single quote on linux systems.
- FFMpeg progress output is done on single line.
- Clear settings when done option (default on).
- Split: new Trim mode
- More... now you could manually specify input file format (in case FFMpeg auto detection fails)
- NVENC on Linux x64 and Windows.
- Intel QuickSync on Windows (you must have Intel Media SDK installed). If you manage to get the SDK installed on Linux it should be working also.
- Lots of bug fixing
- Updated FFMpeg binary with latest version
- WinXP - no longer supported. You could use this version with a ffmpeg binary without mfx.
Enjoy and please provide feedback!&#65279;

---

### Post by mdalacu on 2017-04-04
**dmMediaConverte**r is a crossplatform FFmpeg frontend (GUI) exposing some of its features. It is intended to be simple and easy to use but also to be able to achieve complex tasks. I have inspired myself from a lot of media converters like Handbrake, WinFF and MkvMergeGui. One feature was lacking from most of them, video stream copy (pass-through), that made me build this.

Main features:

stream copy (video, audio, subtitle)
stream conversion - almost any codec into: 
video - h264, h265, vp8, vp9
audio - aac, mp3, flac, pcm, vorbis, opus
subtitles - srt, ass, ssa, mov_text, dvdsub
add multiple streams into one mkv, mp4  or any other container known by ffmpeg that accepts multiple streams (with or without reencoding). Supports multiple video streams in the same file. Also you can reorder stream position.
stream profiles - create and apply audio and video profiles
merge files with the same properties - no reencoding. Ex. Files made by a phone or camera.
merge different kind of files (different codecs, resolution, etc) into one file. It chooses an output with the biggest width of all source files. 
split or trim a file by given time points (no reencoding)
bulk convert files using stream profiles or manual settings (no filter options for manual)
job queue - you can add multiple tasks into a job queue
parallel jobs - you can run multiple jobs in the same time (multithreading)
audio auto gain detect - it will parse the whole file and find the proper gain value (reencode)
picture settings - with changes immediately displayed (reencode)
scaling - change video resolution (use -1 to keep the aspect ratio)
cropping and padding
auto crop - detect best crop values for encoder
rotate picture in 90 degrees increments
grayscale
deinterlace
deshake
burn subtitles (only text based for now)
watermark
manually add FFMpeg video stream filters
video aspect correction - no reencoding
write stream tags like language and title, also container title and creation time -  no reencoding
copy, add or modify any metadata to stream and container.
multiplatform

---

