---
title: "Sound stuttering &amp; unable to change screen rez when HDMI connected"
date: 2012-08-14
forum: Multimedia Software
---

### Post by nkolvek on 2012-08-14
I have posted this on Chromium's bug report as well. Here is the problem.

1. Install Chrome for ubuntu, open Gmail (if you have an account)
2. start anything with constant audio
3. wait for horrible stuttering when gmail checks mail (approx. every 2-5 minutes).

I have an ASRock z67 Gen3 Pro3 mobo using the ALC892 chipset.

Ubuntu 12.04 & last 2 versions of Chrome for Ubuntu (don't know if this affected earlier versions, new ubuntu user.)

My other problem is when HDMI is connected I cannot change resolutions. ubuntu reports it's unsupported and errors (even though it is displaying at that resolution before hdmi is enabled)
My normal display rez is 1680 x 1050 with no issues until you try to change any monitors resolution when hdmi is enabled. (and yes, mirrored display was unchecked each time I tried)

My video card is a radeon hd6850.

---

### Post by riverfr0zen on 2012-08-15
Re: Your issue w/ Chromium+Flash, I am noticing the same problem (laggy, choppy or erratically paced video and audio) since the recent update to Chrome 21.0.1180.79

Everything works fine in Firefox, so I'm assuming there's a problem with the Flash that this new Chrome is using.

(On 12.04, 64-bit)

---

### Post by Dr Belka on 2012-08-20
I have this same issue.  I'm using Chrome vs Chromium.  Also I'm using an Nvidia card.

In addition to the audio stuttering, I get a graphics stuttering as well.  Like if I'm scrolling and the stutter hits, the scrolling will cease for the same duration as the audio stutter.

Every now and then my desktop will become completely unresponsive during a stutter and I'll have to reboot from another tty.  

I'm gonna take a shot in the dark here and say it has something to do with Chrome's GPU compositing.

---

### Post by riverfr0zen on 2012-08-21
I was able to fix the problem with Chrome (version 21.0.1180.79) by:

1) Go to chrome://plugins/
2) Expand the 'Details' link on the top right
3) Under Flash, disable version 11.3.31.227 (Hopefully you'll see a few other Flash version listed below, so your browser will start using those instead. For me, it is 11.2 r202).

It appears that Chrome has released with a version of Flash that works badly on 64bit machines.

---

