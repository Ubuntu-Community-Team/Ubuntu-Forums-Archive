---
title: "Audacity &amp; FFMPEG"
date: 2014-09-05
forum: Multimedia Software
---

### Post by ricardisimo on 2014-09-05
According to [this thread]("http://ubuntuforums.org/showthread.php?t=2219907"), which has been closed, the issue has been fixed on audacity 2.0.5-1ubuntu3.2. That is the version I have installed currently, and there has been zero difference. I still cannot open any more than a few audio file types (WAV, OGG, MP3, etc.) I would like to know if I am missing something. Should I uninstall audacity and ffmpeg and reinstall, for example? I'd just like to be able to import audio from any file that contains audio, just as I did with every Ubuntu before Trusty. Thanks in advance.

---

### Post by fidelis2 on 2014-09-05
Are you using Ubuntu 12 ?
I experienced your problem with (X-) Ubuntu 12 and 13.
Now with (X-) Ubuntu 14, everything is working fine with Audacity and the FFmpeg importers. The menu "Import / Audio" does import the audio of MP4 files, etc.

My Audacity has got the same version number you quoted.
How do I find out the FFmpeg version? I only know Audacity's main menu "Help / Show protocoll" which says:

11:25:19: Audacity 2.0.5
11:25:23: Retrieving FFmpeg library version numbers:
11:25:23:    AVCodec version 0x362300 - 54.35.0 (built against 0x362300 - 54.35.0)
11:25:23:    AVFormat version 0x361404 - 54.20.4 (built against 0x361404 - 54.20.4)
11:25:23:    AVUtil version 0x340300 - 52.3.0 (built against 0x340300 - 52.3.0)

Please tell me if I can quote more information.

---

### Post by ricardisimo on 2014-09-13
I'm on 14.04, fully updated everywhere. Audacity used to be able to extract audio from pretty much any file with an audio track. Now I'm limited to wavs, mp3s and other straight audio files.

---

### Post by mc4man on 2014-09-13
What does your audacity log show? (Help > show log

---

### Post by ricardisimo on 2014-09-13
> **mc4man said:**
> What does your audacity log show? (Help > show log

02:33:59 PM: Audacity 2.0.6-alpha-Apr 28 2014
02:33:59 PM: Trying to load FFmpeg libraries...
02:33:59 PM: mLibAVFormatPath ('/usr/lib/x86_64-linux-gnu/libavformat.so.54') is not empty. Loading from it.
02:33:59 PM: Checking for monolithic avformat from '/usr/lib/x86_64-linux-gnu/libavformat.so.54'.
02:33:59 PM: avformat not monolithic
02:33:59 PM: Loading avutil from '/usr/lib/x86_64-linux-gnu/libavutil.so.50'.
02:33:59 PM: Error: /usr/lib/x86_64-linux-gnu/libavutil.so.50: cannot open shared object file: No such file or directory
02:33:59 PM: Loading avcodec from '/usr/lib/x86_64-linux-gnu/libavcodec.so.52'.
02:33:59 PM: Error: /usr/lib/x86_64-linux-gnu/libavcodec.so.52: cannot open shared object file: No such file or directory
02:33:59 PM: Loading avformat from '/usr/lib/x86_64-linux-gnu/libavformat.so.54'.
02:33:59 PM: Error: Unknown dynamic library error
02:33:59 PM: Actual avutil path 
02:33:59 PM: Error: Unknown dynamic library error
02:33:59 PM: Actual avcodec path 
02:33:59 PM: Actual avformat path /usr/lib/x86_64-linux-gnu/libavformat.so.54.63.104
02:33:59 PM: Importing symbols...
02:33:59 PM: Error: Failed to load symbol av_write_header
02:33:59 PM: Trying to load FFmpeg libraries from system paths. File name is 'libavformat.so.52'.
02:33:59 PM: Checking for monolithic avformat from 'libavformat.so.52'.
02:33:59 PM: Error: libavformat.so.52: cannot open shared object file: No such file or directory
02:33:59 PM: Loading avutil from 'libavutil.so.50'.
02:33:59 PM: Error: libavutil.so.50: cannot open shared object file: No such file or directory
02:33:59 PM: Loading avcodec from 'libavcodec.so.52'.
02:33:59 PM: Error: libavcodec.so.52: cannot open shared object file: No such file or directory
02:33:59 PM: Loading avformat from 'libavformat.so.52'.
02:33:59 PM: Error: libavformat.so.52: cannot open shared object file: No such file or directory
02:33:59 PM: Error: Failed to load FFmpeg libraries.
02:33:59 PM: Error: Failed to find compatible FFmpeg libraries.

---

### Post by mc4man on 2014-09-13
Well that's not an Ubuntu package, where did you get it from?

---

### Post by ricardisimo on 2014-10-28
> **mc4man said:**
> Well that's not an Ubuntu package, where did you get it from?

What's not an Ubuntu package? Ubuntu doesn't distribute ffmpeg packages any longer, so of course I got those from PPAs.

---

### Post by mc4man on 2014-10-28
> **ricardisimo said:**
> According to [this thread]("http://ubuntuforums.org/showthread.php?t=2219907"), which has been closed, **the issue has been fixed on audacity 2.0.5-1ubuntu3.2. That is the version I have installed currently**, and there has been zero difference. I still cannot open any more than a few audio file types (WAV, OGG, MP3, etc.) I would like to know **if I am missing something**. Should I uninstall audacity and ffmpeg and reinstall, for example? I'd just like to be able to import audio from any file that contains audio, just as I did with every Ubuntu before Trusty. Thanks in advance.
I guess you were..
> **ricardisimo said:**
> 02:33:59 PM:** Audacity 2.0.6-alpha-**Apr 28 2014

> **ricardisimo said:**
> What's not an Ubuntu package? Ubuntu doesn't distribute ffmpeg packages any longer, so of course I got those from PPAs.
It supplies libav which for audacity's purposes works just fine. Currently libav9/10/11 are supported. So you could just use the repo builds or a ppa with the patched source

Otherwise your question should be directed to where you got your current package

---

