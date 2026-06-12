---
title: "Daewoo DMV-G264 - Portable Video"
date: 2010-05-18
forum: Multimedia Software
---

### Post by MepisReign on 2010-05-18
I bought a Daewoo DMV-G264 portable video player. It happens that the software to convert videos only works with Winblows. Well, looking here and there I just found that the said software use Mencoder, well after some testing I found that any owner of this kind of device can use the command line in order to convert any video format to the one compatible with this little bastard.

mencoder -ofps 20 -vf-add scale=320:180 -vf-add expand=320:240:-1:-1:1 -srate 44100 -ovc xvid -xvidencopts bitrate=450:max_bframes=0:quant_type=h263:me_quality=4 -oac lavc -lavcopts acodec=mp2:abitrate=64 input.file -o outputfile.avi

That should do it, of course remember that mencoder must be installed

Best Regards

MepisReign :guitar:

---

### Post by MepisReign on 2011-04-06
The best video quality can be achieved with this command

[INDENT]
mencoder -ofps 20 -vf-add scale=320:240 -vf-add expand=320:240:-1:-1:1 -srate 44100 -ovc xvid -xvidencopts bitrate=600:max_bframes=0:quant_type=h263:me_quality=4 -oac lavc -lavcopts acodec=mp2:abitrate=128 input.avi -o output.avi[/INDENT]

Adding subtitles to the video file   :popcorn:

[INDENT]*mencoder -ofps 20 -vf-add scale=320:240 -vf-add expand=320:240:-1:-1:1 -srate 44100 -ovc xvid -xvidencopts bitrate=600:max_bframes=0:quant_type=h263:me_quality=4 -oac lavc -lavcopts acodec=mp2:abitrate=128 inputfile.avi -sub subtitlefile.srt -o outputfile.avi*[/INDENT]

---

