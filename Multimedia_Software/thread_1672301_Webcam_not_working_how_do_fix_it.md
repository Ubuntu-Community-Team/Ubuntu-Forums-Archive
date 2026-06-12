---
title: "Webcam not working how do fix it?"
date: 2011-01-20
forum: Multimedia Software
---

### Post by Bushcraft Bill on 2011-01-20
I am getting lots of database errors trying to search for a fix here? so I will post in the hopes someone has a fix or is willing to help me out getting my webcam working. I have cheese installed here is some info I know is needed to help me out...

Bus 004 Device 003: ID 041e:4055 Creative Technology, Ltd Live! Cam Video IM Pro

cheese gives me no device found

Bill

---

### Post by no2498 on 2011-01-21
see if you can find and install xawtv
it loads a grabber
retry cheese

---

### Post by Bushcraft Bill on 2011-01-21
will not even start for me and I installed the extras too?

> **no2498 said:**
> see if you can find and install xawtv
it loads a grabber
retry cheese

---

### Post by Bushcraft Bill on 2011-01-21
this is what I get with gstreamer does any of this info help?

gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not open device '/dev/video0' for reading and writing. [v4l2_calls.c(502): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: Permission denied]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not open device "/dev/video0" for reading and writing. [v4l_calls.c(179): gst_v4l_open (): /GstPipeline:pipeline2/GstV4lSrc:v4lsrc1:
system error: Permission denied]

---

### Post by no2498 on 2011-01-21
looks to me like you need Permission for the cam/video

and im not that good at remembering how to get/do it sorry

? you get the v4lconfig too

---

### Post by no2498 on 2011-01-21
i need to run for now but have a look

[http://www.google.com/search?q=GstV4lSrc:v4lsrc1:+system+error:+Permission+denied%5D&hl=en&client=opera&hs=wIk&rls=en&channel=suggest&prmd=ivnsfd&filter=0](http://www.google.com/search?q=GstV4lSrc:v4lsrc1:+system+error:+Permission+denied%5D&hl=en&client=opera&hs=wIk&rls=en&channel=suggest&prmd=ivnsfd&filter=0)

---

### Post by Bushcraft Bill on 2011-01-21
from what I am finding their is no driver support for ubuntu for my webcam...:frown:

---

### Post by gordintoronto on 2011-01-21
If you are running 10.10, this might help:
Download the gspca-2.11.3.tar.gz tarball from the following gspca web site:
[http://moinejf.free.fr/](http://moinejf.free.fr/)
You might need to install build-essential using Synaptic.
Untar the file, then follow the readme instructions from the tarball:
Open a terminal, and cd to the directory where the make file is. Then:
make
sudo make install
Reboot to load the new modules. Run Cheese to confirm that it works.
You have to do it again every time there is a new kernel.

---

### Post by Stemp on 2011-01-22
> **gordintoronto said:**
> You might need to install build-essential using Synaptic.

And linux-headers I think.

BTW the latest is now 2.12.2, it's moving fast ;)

---

### Post by gordintoronto on 2011-01-23
Thanks for the info about the version change.

In my experience, the headers always arrive when there is a new kernel.

---

