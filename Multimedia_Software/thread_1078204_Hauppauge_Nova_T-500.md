---
title: "Hauppauge Nova T-500"
date: 2009-02-23
forum: Multimedia Software
---

### Post by pjs_flyer on 2009-02-23
Hi

I've installed a new Hauppauge Nova T-500 and I'm having problems getting it to play back.

I can get w_scan to pick out all the channels (which I then send into the appropriate files in the .gstreamer and .xine directories).  I can also select dvb-0 or dvb-1 in totem.  Totem then shows a list of channels, but (1) in totem-gstreamer there is no sound or video playback and trying to change channels tends to make the window go grey and unresponsive, and (2) in totem-xine it gives a message saying that the signal is lost, and when the dialog box is closed, totem-xine also closes.  Both totems work fine with e.g. streaming internet audio.

I've installed the appropriate plugins I think (gstreamer-plugins-bad from the universe rather than the multiverse, ffmeg etc) 

I'm running ubuntu 8.10 64-bit (is this this issue?) with visual effects enabled (or this?).  The video card is an nvidia 9800gt (or is this it?)

Any ideas as to what's not working or what I should try next?

Thanks!

P.

---

### Post by pjs_flyer on 2009-02-24
ok...using w_scan with an -X option to generate a channels.conf file for Xine means that totem-xine now works with the card! Only problem is, the colours are inverted!  Any ideas?

[EDIT]

By the way, it's an nvidia geforce 9800GT, and I'm using visual effects.

[EDIT 2]

...and using the same channels.conf file for gstreamer means that I can get that program to work as well, but still with inverted colours!  Also, switching desktop effects off doesn't help...help!!!

---

### Post by smbm on 2009-02-24
I have this card which I use through Mythtv which is a massively over specced solution to this problem. Maybe something worth investigating though?

Have you tried any of the other media players? I understand VLC has DVB support built in. I've not tried it though.

---

### Post by pjs_flyer on 2009-02-24
It was (ahem) the hue in preferences - setting this to zero seems to work!

The main lesson, though, is to use the right options when using w_scan (in particular the -X option to give the right sort of configuration file).

---

