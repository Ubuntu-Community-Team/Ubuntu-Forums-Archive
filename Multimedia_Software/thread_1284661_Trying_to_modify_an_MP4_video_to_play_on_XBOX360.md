---
title: "Trying to modify an MP4 video to play on XBOX360"
date: 2009-10-06
forum: Multimedia Software
---

### Post by spiritofcat on 2009-10-06
I use my XBOX360 to play all sorts of videos from USB storage devices and up until now it has worked very well every time.

The problem now is that I've run into a file that it doesn't like.
It gives an error code 69-C00D36BE

I've done some googling and discovered that this can be solved in most cases without re-encoding by [simply re-packing the MPEG-4 file]("http://www.boards.ie/vbulletin/showthread.php?t=2055192916&page=14").

There's a program to do that called [MPEG-4 Modifier]("http://www.moitah.net/").

The GUI version is said to require Windows and .NET Framework, but further investigation reveals that there is a _[command line version](http://forum.doom9.org/showthread.php?t=117553)[U]._[/U] which is supposed to also work in Linux with the aid of something called Mono.

Later in the CL version thread there is a post from the author showing a screenshot of the GUI version running in Ubuntu, and a download link for that fixed version.

I've downloaded the fixed version and extracted it and tried to run it from the command line using:
```
mono MPEG4Modifier.exe
```but I get an error:
```
* (MPEG4Modifier.exe:8356): WARNING **: The following assembly referenced from /media/Byte of Terror/Archive/Apps/MPEG4Modifier.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=0)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/media/Byte of Terror/Archive/Apps/).


** (MPEG4Modifier.exe:8356): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (MPEG4Modifier.exe:8356): WARNING **: Missing method EnableVisualStyles in assembly /media/Byte of Terror/Archive/Apps/MPEG4Modifier.exe, type System.Windows.Forms.Application

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'

```I've checked my version of mono using:
```
mono --version
```Which returned:
```
Mono JIT compiler version 2.0.1 (tarball)
Copyright (C) 2002-2008 Novell, Inc and Contributors. www.mono-project.com
    TLS:           __thread
    GC:            Included Boehm (with typed GC)
    SIGSEGV:       altstack
    Notifications: epoll
    Architecture:  amd64
    Disabled:      none
```So I think I have version 2.0.1 and the author was talking about it working on 1.2.3 so I don't think the problem should be there.

Can anyone help me to get this program working? Or suggest another way of fixing my MPEG-4 file?

---

### Post by mastermindg on 2009-10-07
You may want to check AviDemux. It's a native app and it will repackage mpeg4 video. Check out this post:

[HTML]http://ubuntuforums.org/showthread.php?t=987762[/HTML]

---

### Post by spiritofcat on 2009-10-07
Thanks for the tip.
I have tried using avidemux to re-encode the video a couple of times, but I don't know what settings to use to get decent quality and have it play on the 360.
You said it could re-package it in your post, but the thread only talks about encoding.
As I understand it from the first link in my first post, re-packaging can change the properties of the file quickly without having to actually process the video to re-encode it.
Re-package should take maybe up to 10 minutes, while re-encode takes an hour or two.
Can avidemux re-package the file?

---

### Post by directhex on 2009-10-07
> **spiritofcat said:**
> ```
* (MPEG4Modifier.exe:8356): WARNING **: The following assembly referenced from /media/Byte of Terror/Archive/Apps/MPEG4Modifier.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=0)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/media/Byte of Terror/Archive/Apps/).


** (MPEG4Modifier.exe:8356): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (MPEG4Modifier.exe:8356): WARNING **: Missing method EnableVisualStyles in assembly /media/Byte of Terror/Archive/Apps/MPEG4Modifier.exe, type System.Windows.Forms.Application

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'

```

[libmono-winforms2.0-cil](apt:libmono-winforms2.0-cil)

---

### Post by spiritofcat on 2009-10-07
Thanks directhex. That's got the program working now.

When I try to open my .mp4 file in the program it gives an error about it not being an AVI.

I worked out how to change container in avidemux without re-encoding, but the 360 still doesn't like the file.
The original .mp4 is DIVX video with MP3 Audio.
According to the chart here: [http://www.afterdawn.com/guides/archive/what_will_xbox_360_play.cfm](http://www.afterdawn.com/guides/archive/what_will_xbox_360_play.cfm)
The 360 doesn't like MP3 Audio in an MP4 container.
Putting it in an AVI container instead should make it work according to the chart, but still no dice.
I've also tried re-encoding it to XviD video with MP3 Audio in an AVI and it doesn't like that either, even though that chart implies that it should.

At least MPEG4Modifier can open it now. I'm not sure what needs to be done with the program though to make the file compatible with the 360.
I have changed the aspect ratio output to 16:9 with it because that also needed fixing anyway.
I'll try that file now in the 360.

If that doesn't work maybe I should try leaving it as DIVX in an MP4 and just change the audio from MP3 to AAC.

Edit:
Okay! I converted the audio from MP3 to AAC and now it works!
Only thing is that the aspect ratio is still off. The 360 can stretch it so it looks okay, but I think I'll try putting the now working video into an avi container so that I can use MPEG4Modifier to fix the aspect ratio and then put it back into the MP4 container.

Edit Again:
Well the MP4 --> AVI --> MP4 conversion to try to fix the aspect ratio failed pretty badly. For some reason the program ended up speeding up the audio rather than changing the aspect ratio of the video.
I'll just be content with having the xbox stretch it out to the right size for me.

---

