---
title: "Need compander program"
date: 2013-10-26
forum: Multimedia Software
---

### Post by Autodave on 2013-10-26
I record the worship services at my church and I am looking for a compander (compressor / expander) program.  It can either be a stand-alone program or come with a program for recording audio.

Anyone know of such a program?

---

### Post by mastablasta on 2013-10-27
you can use for example audacity and then save as mp3 file format.

otherwise compressing as tar.gz or 7zip can be done with default compressor.

---

### Post by Autodave on 2013-10-27
> **mastablasta said:**
> you can use for example audacity and then save as mp3 file format.

otherwise compressing as tar.gz or 7zip can be done with default compressor.

No, I am not speaking about a file compression program.  A compander is a device (used to be a separate component) that is used when reording a live performance.  Radio and TV stations also use them.  It takes the incoming audio signal and either softens or raises the volume level to keep it at a specific level.  I see now that there is software to do this on a PC rather than have a seperate component.  I am looking for the software to do this through Linux: even if it is a pay program.

---

### Post by Yellow Pasque on 2013-10-28
[http://sox.sourceforge.net/sox.html#EFFECTS](http://sox.sourceforge.net/sox.html#EFFECTS)

EDIT: ffmpeg project also recently added compand as a filter (version 2.1), but it would take some work to get that in your current install. Try SoX first, as that's readily available. [http://ffmpeg.org/ffmpeg-filters.html#compand](http://ffmpeg.org/ffmpeg-filters.html#compand)

---

### Post by FakeOutdoorsman on 2013-10-28
> **Temüjin said:**
> ...but it would take some work to get that in your current install.

Can be done in three commands (including the actual ffmpeg command).
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.2013-10-25.tar.gz
tar xzvf ffmpeg.static.32bit.2013-10-25.tar.gz
./ffmpeg -i input -af compand output
```

The lazy can try*:
```
wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date +"%F").tar.gz
```
* Not working now since there are no builds for today, but it appears to be a temporary issue.

Or you can follow a [step-by-step guide to compile FFmpeg on Ubuntu](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) (probably what Temüjin was referring to).

---

