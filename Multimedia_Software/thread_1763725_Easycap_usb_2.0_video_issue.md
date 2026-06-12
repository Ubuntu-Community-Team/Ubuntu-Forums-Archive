---
title: "Easycap usb 2.0 video issue"
date: 2011-05-20
forum: Multimedia Software
---

### Post by tommah04 on 2011-05-20
hi all,

I REALLY need to find a usb video capture device and after trying a few things I've gotten the most progress with the Easycap.  But I'm stuck at a really weird spot.

when bringing up the video under PAL, the video is fuzzy and extremely distorted but does technically capture.  However, when I bring up the video under NTSC it shows a perfect video for roughly 3-5 seconds then cuts to Vertical grey lines on the screen (I'm assuming its used to adjust contrast or just the default image) and I have to unplug the device in order to get the video back.

I generally use VLC to mess with Easycap, but have tested it with Cheese and mencoder and same results. 

any help would be great

Thanks,
Tommah

Ubuntu 10.04
32-bit

---

### Post by grandmasterhack on 2011-05-20
i have one of these laying around.(easy cap dc60)

drivers: [http://sourceforge.net/projects/easycapdc60/](http://sourceforge.net/projects/easycapdc60/)

they dont work for me though.
vlc couldn't detect it on my Ubuntu 10.10 64bit
:confused:

---

### Post by tommah04 on 2011-05-20
yea, that's the driver I'm using.

thanks for the reply. I really appreciate it

---

### Post by rmt1947 on 2011-05-21
Hi,

The grey-bar testcard just means a problem with the analogue input signal - see post #4 in the thread at:

[http://ubuntuforums.org/showthread.php?t=1753438](http://ubuntuforums.org/showthread.php?t=1753438)

What video source are you using?  If it's ordinary PAL, you could try something like:

```
mplayer tv:// -tv driver=v4l2:norm=PAL_BGHIN:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=0:fps=25:noaudio -hardframedrop -vo xv
```

(You may need to modify "easycap0" here if /dev/easycap0 is not present.)

If your source is NTSC, try instead:  

```
mplayer tv:// -tv driver=v4l2:norm=NTSC_M:width=640:height=480:outfmt=uyvy:device=/dev/easycap0:input=0:fps=30:noaudio -hardframedrop -vo xv
```

In my experience, the driver generally works well on Ubuntu 10.04, so I'm wondering if there is anything unusual about your analogue video source.

I find it's best to use mplayer/mencoder for initial testing of the driver rather than VLC and Cheese, which have their own complicating peculiarities.

Mike

---

### Post by tommah04 on 2011-05-22
hey rmt,
Thanks for the post.

as I said I tried both sources:  PAL giving me a fuzzy/distorted video,  and NTSC giving me perfect video but for only 5ish seconds.

I tried your codes and the code on suggested forum you gave me and all the same results.

with PAL I get an output like the on in the picture below.  Its distorted, but you can actually see images showing through while playing.  

any other suggestions?

---

### Post by tommah04 on 2011-05-22
bump

---

### Post by tommah04 on 2011-05-25
bump.... really need help.  is it possible its just a bad capture card?

*edit*
not the capture card, works perfect in Windows

---

### Post by tommah04 on 2011-05-25
I'm pretty sure the video source is NTSC... but is there anything I could try to continue the signal?  it just stops after 5 seconds.

---

### Post by rmt1947 on 2011-05-25
I've never personally experienced a situation where the driver works initially and then stops after a few seconds, so I can't confidently offer any suggestions.  I had thought the symptoms might indicate a mismatch between the actual signal standard (NTSC_M, NTSC_443, etc) and the standard specified in the mplayer command line, but this probably isn't the right explanation if you are getting good results from the MicroSoft Windows driver when it's set up for plain NTSC.

To find out definitively what's wrong it would be necessary to build the driver with DEBUG=9 (see the README file for details) and examine the diagnostic output which is written to file /var/log/kern.log.  But even if this time-consuming procedure is followed and the cause of the problem is eventually identified, there's no guarantee that the problem can be fixed.

Mike

---

### Post by jcoles on 2011-06-10
How do well do other USB devices perform for you? 

My experience with Linux is that it does not achieve full USB 2.0 performance. It's a pity. For example, long file transfers to an external HDD go slower and slower. It's easy to imagine that the USB interface doesn't deliver the data from your digital video device fast enough after the first few seconds.

---

### Post by grandmasterhack on 2011-06-21
i cant get them to compile i get the "iocelt" error. sorry im on a mobile device now so i cant copy & paste the error.

---

### Post by thunderbirdje on 2011-06-27
Just wondering if anyone got the Easycap to work? 

I am going to buy one. Would you advice the DC60 or another one? :-)

Thank you!

---

### Post by grandmasterhack on 2011-06-28
well i think this uses something in the old kernel. i heard people who use ubuntu 9.10 were successful. i'll try it in a vm to see if it works. i searched the same error with out including "easy cap" and people who use the kernel source code said it was because the coder was trying to use something that didn't work the same way it used to or the name has changed.

---

