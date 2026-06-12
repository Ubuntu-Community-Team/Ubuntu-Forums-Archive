---
title: "Just one app is keeping my friend from being able to migrate completely to Ubuntu..."
date: 2010-12-01
forum: Multimedia Software
---

### Post by CoolBreeze47 on 2010-12-01
Hi everyone.

I am writing this on behalf of a friend of mine. He really likes Linux and has been using Ubuntu for about 3-4 years. He is growing increasingly frustrated with windows and is always saying that if he could find an alternative to ConvertXtoDVD he would move over to Ubuntu and ditch Windows completely.

He has tried Devede, WinFF and ConvertXtoDVD on Wine and none of these have panned out for him. The first two are confusing and unfamiliar to him with too many possible options and steps to take and then it takes a long time to do the actual conversion and it never seems to come out right (or at all). I'm sure these are good programs and I am not knocking them. It's just that he has tried them over and over again with no luck. ConvertXtoDVD was tried over and over again on Wine and no luck with that either. He is used to the "one-click" simplicity of ConvertXtoDVD and so he has to have a second computer with Windows and ConvertXtoDVD installed on it. One computer just to run a single program. Blah.

My question is this: Is there anything else he can use that has the speed and simplicity of ConvertXtoDVD on Ubuntu?. If it has to be installed on Wine then so be it but the other converters have just lead to a great deal of frustration. What else can he do?. Is there anything else he can try?. This has been the ONLY thing keeping him from switching over completely and he really wants to.

Thank you for your help with this, CB

---

### Post by amsterdamharu on 2010-12-01
> Is there anything else he can use that has the speed and simplicity of ConvertXtoDVD on Ubuntu?
As you mentioned he only ran ConvertXtoDVD on the other computer (without any other programs). I always run ffmpeg in tty1 without even a gui on; do the following:

Log out of the gui -> press control + alt + f1 -> log in -> type the following commands:
```
sudo service gdm stop
bash yourwinff_script.sh
```

The file yourwinff_script.sh is created by winff, if he likes the output of ConvetXtoDVD I need to know what settings he uses. You can add some settings to winff (like resolution and scale).

When adding the files to devede he needs to go to "advanced options" -> misc tab -> check the "this file is already a DVD/xCD suitable MPEG-PS file". 

If you want to cut files into certain chapters at certain points (devede does it every 5 minutes) then open the converted file in avidemux and save the chapters as separate files. Choose video and audio codec copy and format "MPEG-PS (A+V)" in the settings on the left side of the program.

---

### Post by amsterdamharu on 2010-12-01
By the way; to check out what format that ConvertXtoDVD creates and your friend like so much can be checked out by using it as an input file for ffmpeg:
```
ffmpeg -i myconvertedfile.mpg
```

This could give an output like:
```
Input #0, mpeg, from 'myconvertedfile.mpg':
  Duration: 00:01:00.60, start: 0.500000, bitrate: 1400 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 352x288 [PAR 16:11 DAR 16:9], 9000 kb/s, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 128 kb/s
At least one output file must be specified
```

---

