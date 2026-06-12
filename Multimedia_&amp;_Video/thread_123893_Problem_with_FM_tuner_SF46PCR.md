---
title: "Problem with FM tuner SF46PCR"
date: 2006-01-31
forum: Multimedia &amp; Video
---

### Post by yasman on 2006-01-31
I have a SF64PCR FM tuner PCi card, is there any possible way to make it work on video4linux ?
In case i`m running on Ubuntu 5.10 and in Devide Manager this card is recognised as 
Xwave QS3000A [FM801]
and
Xwave QS3000A [FM801 game port]

Reference to manufacturer:
[http://www.mediaforte.com.sg/products/tv_and_radio/sf64_pcr/index.htm](http://www.mediaforte.com.sg/products/tv_and_radio/sf64_pcr/index.htm)

yes, i tried fmio it works, but i want it under v4l...

Anyone?

THNX in advace!

---

### Post by mpvano on 2006-01-31
All my radio cards seem to be set up as /dev/radio0 by Ubuntu.
All my radio applications are looking for /dev/radio.

You can find out if this is your problem by simply typing the following into a terminal window:

ls -l /dev/radio*

and seeing if you have any radio devices at all.

You can either fix it properly (a lot of work figuring out how the device file system actually gets configured at boot) OR do what I do and just tell the applications to look for /dev/radio0.

If your applications are hard to reconfigure, and if this is your problem, try making a link like this:

sudo ln -s /dev/radio0 /dev/radio

If that works, it'll do the job but you may need to do it after every reboot or find some way to automate it in the startup scripts....

hope it's this easy....

Mario

---

