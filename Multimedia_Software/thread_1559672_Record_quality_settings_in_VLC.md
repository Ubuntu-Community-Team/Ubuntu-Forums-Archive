---
title: "Record quality settings in VLC?"
date: 2010-08-23
forum: Multimedia Software
---

### Post by Moozillaaa on 2010-08-23
What settings can I tweak in VLC, or even what hardware settings, to make sure I'm getting the best record quality?

Hardware is 
Hauppauge PVR500 PCI card input through coax from satellite DVR (SD recordings)
Athlon x2 6400+ 3.2G
4 x 1G memsticks 667megHz

VLC is the app I'm using for recording... Hardy x64

Thanks.




edit:
I start up VLC in these parameters:
 vlc pvr:// :pvr-device="/dev/video0" :pvr-radio-device="/dev/radio0" :pvr-norm=0 :pvr-frequency=-1 :pvr-bitrate=-1 --sout '#duplicate{dst=display,dst=std{access=file,mux=ts ,dst="/home/chucknb/output.mpg"}}'

---

