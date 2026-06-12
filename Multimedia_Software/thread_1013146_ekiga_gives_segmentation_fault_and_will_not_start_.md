---
title: "ekiga gives segmentation fault and will not start up"
date: 2008-12-16
forum: Multimedia Software
---

### Post by BioGeek on 2008-12-16
Hey,

When I click on the ekiga logo, it gives a a spinning wheel and then stops. It never even opens. 

When I start ekiga via the command line with debugging on, I get the following error.

```
~$ ekiga -d 4
2008/12/16 21:37:44.747	  0:00.213	                  ekiga	ekiga	Version 2.0.12 by  on Unix Linux (2.6.27-9-generic-x86_64) at 2008/12/16 21:37:44.746
2008/12/16 21:37:45.049	  0:00.515	                  ekiga	Detected audio plugins: ALSA
2008/12/16 21:37:45.050	  0:00.516	                  ekiga	Detected video plugins: Picture,V4L2,V4L
2008/12/16 21:37:45.051	  0:00.517	                  ekiga	Detected audio plugins: ALSA
2008/12/16 21:37:45.052	  0:00.518	                  ekiga	Detected video plugins: Picture,V4L2,V4L
2008/12/16 21:37:45.053	  0:00.519	                  ekiga	Detecting V4L2 devices
2008/12/16 21:37:45.054	  0:00.520	                  ekiga	Unable to detect v4l2 directory
2008/12/16 21:37:45.188	  0:00.654	                  ekiga	Detected the following audio input devices: Default,HDA Intel with plugin ALSA
2008/12/16 21:37:45.189	  0:00.655	                  ekiga	Detected the following audio output devices: Default,HDA Intel with plugin ALSA
2008/12/16 21:37:45.190	  0:00.656	                  ekiga	Detected the following video input devices: No device found with plugin V4L2
2008/12/16 21:37:45.191	  0:00.657	                  ekiga	Detected the following audio input devices: Default,HDA Intel with plugin ALSA
2008/12/16 21:37:45.192	  0:00.658	                  ekiga	Detected the following audio output devices: Default,HDA Intel with plugin ALSA
2008/12/16 21:37:45.193	  0:00.660	                  ekiga	Detected the following video input devices: No device found with plugin V4L2
Entity: line 2: parser error : invalid character in attribute value
<group uid="" name="On This Computer" base_uri="file:///home/tr/.evolution/addr
            ^
Entity: line 2: parser error : attributes construct error
<group uid="" name="On This Computer" base_uri="file:///home/tr/.evolution/addr
            ^
Entity: line 2: parser error : Couldn't find end of Start Tag group line 2
<group uid="" name="On This Computer" base_uri="file:///home/tr/.evolution/addr
            ^
Entity: line 2: parser error : Extra content at the end of the document
<group uid="" name="On This Computer" base_uri="file:///home/tr/.evolution/addr
            ^
Entity: line 2: parser error : invalid character in attribute value
<group uid="" name="On This Computer" base_uri="file:///home/tr/.evolution/addr
            ^
Entity: line 2: parser error : attributes construct error
<group uid="" name="On This Computer" base_uri="file:///home/tr/.evolution/addr
            ^
Entity: line 2: parser error : Couldn't find end of Start Tag group line 2
<group uid="" name="On This Computer" base_uri="file:///home/tr/.evolution/addr
            ^
Entity: line 2: parser error : Extra content at the end of the document
<group uid="" name="On This Computer" base_uri="file:///home/tr/.evolution/addr
            ^
Segmentation fault

```

So it seems that there is a problem with a user id. It shows as a leftpointing triangle on my terminal, but when I try to copy paste it, my cursor jumps to the beginning of the line.

I have the following user IDs on this machine.

```

$ id
uid=1000(tr) gid=1000(tr) groups=4(adm),20(dialout),24(cdrom),46(plugdev),108(lpadmin),123(admin),124(sambashare),1000(tr)

```

---

