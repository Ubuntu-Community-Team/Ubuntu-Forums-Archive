---
title: "Scanning for analogue cable channels"
date: 2010-02-10
forum: Multimedia Software
---

### Post by rimshot4 on 2010-02-10
Hi All,

I'm trying to scan for analogue cable channels. How do I go about this?

I'm using the Hauppage HVR-1950 in Karmic. 

After initial setup I'd like to use a program other than MythTV.

Thanks.

---

### Post by rimshot4 on 2010-02-11
More info. 

It seems neither scan nor w_scan support NTSC/analogue, so I'm not able to produce a valid channels.conf using these programs. TVtime does not support the HVR-1950 because it does not produce a raw video stream (it's a MPEG2 encoder). 

According to this page ([http://klk64.com/wintv-hvr-1950/](http://klk64.com/wintv-hvr-1950/)) you can use tvscan to produce a .xaw file which lists channels, but you cannot use xawtv with the HVR-1950. I tried using this scan and it did seem to find channels during the scan (when scanning where our cable channels should be it produced "???" rather than "no channel found") but the output file has no frequencies in it. I can't get this file to work with any program.

Is it possible to simply build a channels.conf file from scratch, manually, using tables of frequencies for ntsc cable, or is there a program to use for this? And where could I find a channels.conf to use as a template?

---

### Post by rimshot4 on 2010-02-11
Here's the .xawtv file produced by tvscan. Is this output valid? There are no frequencies listed.

[global]
freqtab = us-cable

[defaults]
input = Television
norm = NTSC-M

[unknown (2)]
channel = 2

[unknown (4)]
channel = 4

[unknown (5)]
channel = 5

[unknown (6)]
channel = 6

etc.

In any case, simply renaming the file channels.conf does not work.

---

### Post by rimshot4 on 2010-02-14
Problem solved, mainly by an excellent little program called TV-viewer. [http://ubuntuforums.org/showthread.php?p=8823263#post8823263](http://ubuntuforums.org/showthread.php?p=8823263#post8823263)

---

