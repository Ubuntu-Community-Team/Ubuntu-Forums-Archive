---
title: "convert video for mp4 device"
date: 2009-12-02
forum: Multimedia Software
---

### Post by rpuchadm on 2009-12-02
information direct from [email]soporte@energysistem.com[/email]
for encoding video for the mp4 portable device
energy sistem inngenio 6000
i've tried

mencoder macaco-movin.flv -ofps 20 -vf-add scale=320:240 \
-vf-add expand=320:240:-1:-1:1 -srate 44100 -ovc xvid \
-xvidencopts bitrate=600:max_bframes=0:quant_type=h263:me_quality=4 \
-oac lavc -lavcopts acodec=mp2:abitrate=128 -o macaco-movin.avi

where macaco-movin.flv is input video taken from youtube
and macaco-movin.avi is the output file

works fine
I'm very thankfull energysistem

---

