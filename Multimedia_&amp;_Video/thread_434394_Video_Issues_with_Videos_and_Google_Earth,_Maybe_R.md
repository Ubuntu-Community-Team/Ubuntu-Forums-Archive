---
title: "Video Issues with Videos and Google Earth, Maybe Related?"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by tripinva on 2007-05-05
So everything had been working fine since my upgrade to Feisty.  But then out of the blue, I started having a whole slew of problems all at once, and so I've managed to fight my way through them.

1)  Sound failed (corrupt file)
2)  Full hard drive caused X Server to crash on log-in
3)  Swap file UUID is wrong in /etc/fstab on boot
4)  Suddenly needed lapic and irqpoll in the boot options for LAN/WLAN/USB/Sound to work

Now I'm running Kubuntu 7.04 on a Toshiba A15-S157, a fairly dated piece of hardware (Summer 2003), and I'm replacing it in the next three months, so I'm trying very hard not to have to wipe it and start over.

So all of a sudden last night, seemingly unrelated to the above problems (though I can't be sure), I've been having two video problems.

The first of which is that videos will not play at all in mplayer (can't initialize the video out?), and play audio but with garbled video in Kaffeine (runs on the Xine library).  They still play in VLC, but that doesn't help since Flash videos have no audio in VLC.

Also, Google Earth has suddenly gotten VERY sluggish.  It had been perfectly smooth in its performance and zooming, but all of a sudden is now very choppy and difficult to manipulate.

If I didn't know better, I'd say there's a screwed up video driver, but does the Intel integrated graphics chip even have a dedicated driver to mess with?

Thanks for any assistance.

- Trip

---

### Post by tripinva on 2007-05-05
And just like that it works again.  I ran xserver-xorg's configuration tool again and picked the Intel driver, and manually set the video memory to the correct size instead of leaving it blank.

This fixed both problems.  I'll go disappear now.

- Trip

---

