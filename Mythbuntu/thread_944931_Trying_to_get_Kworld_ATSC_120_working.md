---
title: "Trying to get Kworld ATSC 120 working"
date: 2008-10-11
forum: Mythbuntu
---

### Post by darren_j on 2008-10-11
The most recent useful information on this card I can find is here:
[http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120)

If I understand this right, and there's a good chance I don't, the Kworld 120 is not supported in the kernel found in Mythbuntu 8.04.  But I think it might be in the kernel in 8.10. That is 2.6.27-7.

Rather than update the kernel, I tried installing the 8.10 Beta released last week.  I actually had problems installing this, and ended up installing Xubuntu 8.10, then installing MythBuntu.

The card now gets recognized as analog /dev/video0 and as a DVB device.  I can run a channel scan on analog and ATSC, but no channels are found.

Does this mean I still need to update the firmware?

I tried following the firmware instructions found here,
[http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028#Firmware_Information](http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028#Firmware_Information)
but the script gives many errors, leaving me at a dead end.

Any suggestions?

Thanks.

---

### Post by darren_j on 2008-10-12
I made some progress, so I thought I'd update this thread.

I got the perl script to work thanks to this forum and instructions on the Kworld 115.  The part I didn't understand is that you need to cd to the documentation directory, where you'll find the perl script.

Take my instructions with a grain of salt since things aren't working perfectly yet:
$ cd /usr/src/linux-headers-2.6.27-7-generic/Documentation/video4linux
(using your own kernel version number)
Download the zip file as directed in the perl script, and unzip the file.
Then run the local perl script.  Don't download the perl script from the link given on the linuxtv.com site.  (that was my mistake).
Copy the generated .fw file to /lib/firmware
$ sudo cp xc3028-v27.fw /lib/firmware

I rebooted at this point.

After removing the DVB device, since nothing is getting locked from ATSC, I rescanned the analog channels.  It's picking up analog channels fine.  No audio, but I figure that's a different problem.

Now I have to figure out how to switch the board to ATSC mode.

---

### Post by darren_j on 2008-10-12
The ATSC setup was pretty easy.  I followed the final steps on the original page I linked to:
[http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120)
making edits to blacklist-misc and rc.local

Note that there's a typo on that page.  The modules are named cx88_dvb, with an underscore, not a dash.

Things aren't running perfectly for me yet, but I got audio running in ATSC mode.  Not sure if it'll work in analog mode.  More later.

I guess the good news is that using the beta version of xubuntu, I could get all this working without downloading kernels or source from mercurial, etc.

---

### Post by Jimbo13 on 2008-11-08
I'm having this problem and was researching a fix but im a linux noob. 

I found this, I believe its a patch but I don't know how to install (or what to download).  

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=99e09eac25f752b25f65392da7bd747b77040fea](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=99e09eac25f752b25f65392da7bd747b77040fea)

If it's useful I'd appreciate if you shoot me back the instructions on how to install it.

Good luck.

---

### Post by jeff45 on 2008-12-01
I also have a Kworld 120 that I'm attempting to get running.  I've used the same wiki in the post you mention.  I've updated the kernel, ran the script to generate the firmware, and added the blacklist/modprobe lines to the appropriate files.  At least now I can choose the card in myth, but like you I get no signal lock on channel scan.  There is a few setting/tweaks under the DVB card selection that I'm not sure about either.  Oh, since I only want the ATSC tuner part(from what I understand you can only use either digital or anolog, but not both), I have that set in my rc.local file.  I'm writing this post from a computer other than my backend, so I apologize for my "off the top of my head" post.

---

### Post by jeff45 on 2008-12-04
After replying to your post, I decided to try again.  You mentioned, in one of your post, about the hyphen-undercsore_ error.  I didn't think that made a difference, but evidently it does.  One of the tutorials points out that there is only support on one module, either analog or digital, at a time.  I did an # lsmod to show what modules where loaded and all of them had loaded - not good.  I change the blacklist and rc.local file to use underscores for the "cx_" modules and this fixed the problem for me.  Your post and discoveries actually help me solve my problem.  Thanks!

---

### Post by swalke66 on 2009-02-23
Jeff,

Same issue here.

Did you have to kill and restart mythtv in your rc.local file to get this to work?

I'm using mythbuntu 8.10, fully updated, but still can't scan any channels in ATSC mode.

---

### Post by jesuschris on 2009-07-22
Hi!

Just installed this card on a new machine today with the 9.04 release of mythbuntu. Supposedly, the custom kernal work as described on the mythtv and linuxtv wiki is not needed with the latest generic kernel (currently 2.6.28-13-generic)

In the mythtv config I am able to select and use the tuner card, am using ETI as the video source but scanning for OVTA HD channels finds nothing.

Anyone have any luck getting this card to pull in over the air HD?

I'm thinking I just need to muck about in the mythtv configuration...

Any help would be appreciated.

Will update as to my progress, if any, as well.

Thanks!

---

### Post by newlinux on 2009-07-22
You don't need the custom kernel, but you probably still need the firmware file be in the right place, and possible have to still load the drivers at the right time... have you done that?

---

### Post by jesuschris on 2009-07-22
Thanks for the reply newlinux,

I've hopefully loaded my drivers properly, based on instructions from the [linuxtv wiki]("http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120") (Step 3). I've got the blacklist-misc file and rc.local faile for ATSC on my system as described in the wiki.

I did run into some confusion on their wiki in regards to loading the mythtv backed _after_ the proper modules were loaded. I have no idea what to put in the rc.local to do that.

I have not yet attempted to use the drivers mentioned on their wiki as the instructions seemed to indicate they weren't necessary on post .26 kernels.

But I'll give that a shot.

Thanks again!

---

### Post by newlinux on 2009-07-22
> **jesuschris said:**
> Thanks for the reply newlinux,

I've hopefully loaded my drivers properly, based on instructions from the [linuxtv wiki]("http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120") (Step 3). I've got the blacklist-misc file and rc.local faile for ATSC on my system as described in the wiki.

I did run into some confusion on their wiki in regards to loading the mythtv backed _after_ the proper modules were loaded. I have no idea what to put in the rc.local to do that.

I have not yet attempted to use the drivers mentioned on their wiki as the instructions seemed to indicate they weren't necessary on post .26 kernels.


But I'll give that a shot.

Thanks again!

Yeah, I think that might be incorrect. I'm pretty sure you still need the firmware. Firmware and driver are not exactly the same thing.  I don't think the need for the firmware would go away, but I've been wrong before. I know I still need it with my kworld 115. I think what you don't need to do is update and configure the kernel or clone and build v4L-dvb tree.

---

### Post by jesuschris on 2009-07-22
OK. The firmware instructions on linuxtv/mythtv wikis seem to be in need of some editing. I will try and get to that later.

So. As of kernel 2.6.28-13-generic this is what you have to do to install the appropriate drivers.

Hit up [http://www.steventoth.net/linux/xc5000/](http://www.steventoth.net/linux/xc5000/)

Grab the zip.
Grab the extract.sh

Make the extract.sh executable.

Run that bad boy.

It's a much more refined process with the extract.sh as the authour has included the finishing steps upon completion.

```
 ./extract.sh
Extracting hcw85bda.sys from the windows zip file
Archive:  HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip
  inflating: Driver85/hcw85bda.sys   
Extracting firmware as dvb-fe-xc5000-1.1.fw from hcw85bda.sys
Firmware extracted successfully
Removing Driver85/hcw85bda.sys temporary file
Removing Driver85 temporary dir
Now manually copy dvb-fe-xc5000-1.1.fw into your firmware dir
  E.g. sudo cp dvb-fe-xc5000-1.1.fw /lib/firmware/2.6.28-13-generic
```

Time to TEST.

Thanks again all for the help. Will update my progress as warranted.

---

