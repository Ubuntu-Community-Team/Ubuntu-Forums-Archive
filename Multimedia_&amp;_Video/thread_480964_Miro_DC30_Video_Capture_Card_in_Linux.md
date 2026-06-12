---
title: "Miro DC30 Video Capture Card in Linux"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by AmpDivorax on 2007-06-22
I just put in a Pinnacle Miro DC30 card in my ubuntu machine.  However, when I try to use modprobe zr36057, I get a module not found error and a no such device error when I try to use zr36067.  Does anybody know what I have to do to get this working?

---

### Post by AmpDivorax on 2007-06-25
Alright, I have an update on issues I have had.  First, the system did detect and load the drivers properly, however it couldn't automatically select the hard so I had to reload the module with the card I have selected manually. (Card number listings are shown at [http://mjpeg.sourceforge.net/driver-zoran/documentation.php]("http://mjpeg.sourceforge.net/driver-zoran/documentation.php"))

modprobe -r zr36067
modprobe zr36067 card=3

The card can be seen now on applications, but it's not showing anything no matter what TV application I use. (Xawtv is the recommended application for video capture, but it doesn't work so I have to figure out why.)  I've also read some reports that the zoran drivers are pretty broken in Linux 2.6, so if anybody has gotten any of the zoran based hardware working can they drop a line to me about what they did?

---

### Post by steyze on 2007-11-19
Hi,

I've put the DC30 in my system three days ago.
I'm running Ubuntu 7.04 with the latest kernel.

The moudle was loaded automatically and the v4l-software is able to get the video input.
But I see only black/white and jerking video.
I don't know if it's a problem with my hardware, my drivers or the dc30 itself.
On Win2000 I've the same problems.

Does somebody has experiences with dc30 and/or zoran devices?


greets

---

