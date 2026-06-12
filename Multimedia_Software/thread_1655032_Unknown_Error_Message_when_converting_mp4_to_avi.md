---
title: "Unknown Error Message when converting mp4 to avi"
date: 2010-12-29
forum: Multimedia Software
---

### Post by Viscount Bentos II on 2010-12-29
Hi all,

So I have been at this problem for most of the morning and I have run out of ideas:

I want to convert and mp4 to avi, and having uninstalled ffmpeg, winff and all other dependencies and followed the fabled guide 

[http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289](http://ubuntuforums.org/showpost.php?p=9868359&postcount=1289)

to install a complied version of ffmpeg, I keep on getting this error when trying to convert:

```

    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    creation_time   : 1970-01-01 00:00:00
    encoder         : Lavf52.84.0
  Duration: 01:16:18.13, start: 0.000000, bitrate: 1502 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 832x468 [PAR 117:117 DAR 16:9], 1401 kb/s, 25 fps, 25 tbr, 25 tbn, 50 tbc
    Metadata:
      creation_time   : 1970-01-01 00:00:00
    Stream #0.1(und): Audio: aac, 48000 Hz, stereo, s16, 94 kb/s
    Metadata:
      creation_time   : 1970-01-01 00:00:00
[COLOR="Red"][NULL @ 0x1994010] [Eval @ 0x7fff02619fe0] Invalid chars 'v' at the end of expression '4mv'
[NULL @ 0x1994010] Unable to parse option value "4mv"[/COLOR]
Invalid value '+4mv' for option 'flags'
Press Enter to Continue

```

I have opened up the config and removed all references to '4mv ' and replaced them all with '4m ' but to no avail. i have scoured the internet and these forums but still no joy. I know I have followed all the steps for the correct distro of Ubuntu, and I did have a working version of ffmpeg/winff before.

Any help/comments/suggestions/improvements greatly appreciated.

---

### Post by FakeOutdoorsman on 2010-12-29
What is your command?  *4mv* has been renamed to *mv4*:
```
$ ffmpeg -h
[...]
-flags             <flags> EDVA.
   mv4                     E.V.. use four motion vector by macroblock (mpeg4)
```

**Update:** Oh, are you using WinFF? I'm not sure if it's presets are up to date enough to use with current FFmpeg SVN.

---

### Post by Viscount Bentos II on 2010-12-29
I am using winff so no command line. I found this thread that was similar to the problem I found

[http://ubuntuforums.org/showthread.php?t=1520806](http://ubuntuforums.org/showthread.php?t=1520806)

essentially the suggestion in that thread is to open the presets.xml and update any references to the offending chars. So I removed the 'v' but if they have been renamed then I need to rename in the presets.xml file.

All very much trial and error really.

---

### Post by Viscount Bentos II on 2010-12-29
Ok so updated the presets file to 'mv4' where it said 'm4v' and that has fixed that problem, so thanks for your response.

Now onto the next problem... but it's probably one I can fix myself.

Thanks again.

---

