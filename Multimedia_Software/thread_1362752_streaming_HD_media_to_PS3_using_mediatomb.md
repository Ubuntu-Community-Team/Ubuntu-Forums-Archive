---
title: "streaming HD media to PS3 using mediatomb"
date: 2009-12-23
forum: Multimedia Software
---

### Post by fcuk112 on 2009-12-23
hi, i am currently streaming 720p mkv files to my PS3 using mediatomb.  the following is my 720p profile:

> 
 <profile name="mencoder-720" enabled="yes" type="external">
 87         <mimetype>video/mpeg</mimetype>
 88         <accept-url>yes</accept-url>
 89         <first-resource>yes</first-resource>
 90         <accept-ogg-theora>yes</accept-ogg-theora>
 91         <agent command="mencoder" arguments="%in -aid 0 -sid 0 -oac lavc -ovc lavc -of mpeg -lavcopts vcodec=mpeg    2video:keyint=1:vbitrate=200000:vrc_maxrate=12000:vrc_buf_size=1835 -mpegopts muxrate=12000 -vf harddup,scale -zo    om -xy 720 -font /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf -subfont-autoscale 0 -subfont-text-scale 20     -slang nl,en -noautosub -ofps 24000/1001 -o %out"/>
 92         <buffer size="1000000" chunk-size="512000" fill-size="20480"/>
 93       </profile>


however when i stream the cpu utilisation is quite high.  i was wondering if i could offload some of this processing to my nvidia 9600GT card (vdpau?).

can anyone please advise?

---

### Post by TheMoken on 2010-01-05
I'm not sure about video card offloading, but I solved my underpowered CPU vs. HD problem by pre-transcoding into .mpg. It has the added advantage of being seek-able from the PS3.

---

