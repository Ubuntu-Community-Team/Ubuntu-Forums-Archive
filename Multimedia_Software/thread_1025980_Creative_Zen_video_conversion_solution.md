---
title: "Creative Zen video conversion solution"
date: 2008-12-30
forum: Multimedia Software
---

### Post by talon314 on 2008-12-30
In case anyone with a Creative Zen has been beating their head against the wall trying to convert video to a format the Zen is happy with (like I have been for a few weeks now), WinFF has a preset for the Zen. Install instructions here:

[http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)

or (more importantly), the ffmpeg command WinFF uses:

```
ffmpeg -i <input_filename> -r 29.97 -vcodec libxvid -vtag XVID -s 320x240 -aspect 4:3 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2 <output_filename>
```

I could not find a command for this (except a mencoder script that resulted in audio sync issues) anywhere, so I thought I'd post.

---

### Post by jacob01 on 2009-01-01
thank you

---

### Post by daverave999 on 2009-05-16
An tip for Jaunty users. Don't use the version in the Ubuntu repos (0.45), use the latest version (1.0.0) from the winff.org repos. I tried installing Zen presets into 0.45 and it didn't work.

---

### Post by paul.gevers on 2009-05-18
> **daverave999 said:**
> An tip for Jaunty users. Don't use the version in the Ubuntu repos (0.45), use the latest version (1.0.0) from the winff.org repos. I tried installing Zen presets into 0.45 and it didn't work.

Can you tell me what exactly you tried, because it is ffmpeg that does the job, so it really should not matter.

Version 1.0.0 and 0.45 are quite similar, but might have slightly different presets.

---

