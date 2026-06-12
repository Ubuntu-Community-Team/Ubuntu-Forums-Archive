---
title: "Handbrake/DeVeDe issue"
date: 2012-11-22
forum: Multimedia Software
---

### Post by cottfcfan on 2012-11-22
When ripping a DVD using Handbrake (Default settings), the resulting .m4v file plays fine.
 However if I turn the .m4v file back into an iso using DeVeDe, the video on the resultant iso plays back at about 10 times the speed it should, while the audio is fine.
 Any ideas what is going wrong here?

ps ripping the file using dvd:rip, with xvid as the video codec, and repeating the above works fine.

---

### Post by JohnAStebbins on 2012-11-23
> **cottfcfan said:**
> When ripping a DVD using Handbrake (Default settings), the resulting .m4v file plays fine.
 However if I turn the .m4v file back into an iso using DeVeDe, the video on the resultant iso plays back at about 10 times the speed it should, while the audio is fine.
 Any ideas what is going wrong here?

ps ripping the file using dvd:rip, with xvid as the video codec, and repeating the above works fine.

I don't really know anything about DeVeDe and you didn't provide a HandBrake activity log so I can't tell what settings you used, but I'll make a guess.  Your using HandBrake default framerate settings which generate variable framerate output and DeVeDe isn't properly understanding variable framerate.  Try changing the HandBrake framerate to constant.

---

### Post by cottfcfan on 2012-11-24
Thanks John,
Will try that and reply back.

edit...
Tried again using constant bitrate.
This time, when converting back to DVD, I got the error message "conversion failed, a bug in mencoder"

edit 2...
It seems this is a devede/mencoder issue.
Strange thing is that DeVeDe converts dvd:rip files fine, just not Handbrakes.
Will carry on digging.

---

### Post by jerome1232 on 2012-11-24
I've made my own "devede compatible" profile and set it to constant framerate 29.97 (NTSC Video)

Ensure in DeVeDe that you are encoding to NTSC and not Pal (it defaults to pal, and I think I've had that error when trying to convert one of my handbrake video's into a dvd)

---

### Post by cottfcfan on 2012-11-24
Thanks Jerome,
Just tried that but get the same error message whether using NTSC or PAL.

---

### Post by jerome1232 on 2012-11-24
Even in the individual files properties?

I know I've ran into this before and fixed it but can't for the life of me recall what the issue was exactly, all I can remember is the pal/ntsc and the variable framerates being issues.

---

### Post by cottfcfan on 2012-11-24
Don't think it can be the NTSC/PAL thing.
In USA you use NTSC, in GB & Europe we use PAL.
All our DVDs are in PAL so need ripping as such.
Will try your suggestion later though, just to see if it eliminates the problem, and post back.
Thanks for your suggestion.

---

### Post by cottfcfan on 2012-11-25
After a lot of experimenting I think i'll stick with DVD:RIP.
It seems to just work for me & i'm used to its settings.
Does anyone know if it's possible to encode using the H264 format on DVD:RIP?

---

### Post by vanadium on 2012-11-25
That is then where you need handbake. DVD:RIP for ripping a DVD to DVD, Handbrake for ripping to a video file.

---

### Post by jerome1232 on 2012-11-25
> **cottfcfan said:**
> After a lot of experimenting I think i'll stick with DVD:RIP.
It seems to just work for me & i'm used to its settings.
Does anyone know if it's possible to encode using the H264 format on DVD:RIP?

It should be under Global Options > Misc. options, you can change which container you want to use and which codec you want to use.

---

### Post by cottfcfan on 2012-11-26
Hi Jerome,
I've checked there. While there are many options, there is none for h264/x264, unless it goes by another name.

---

