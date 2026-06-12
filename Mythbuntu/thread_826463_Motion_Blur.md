---
title: "Motion Blur"
date: 2008-06-11
forum: Mythbuntu
---

### Post by danbodoh on 2008-06-11
I'm getting motion blur (blur when there's a fast motion on the screen).  Any ideas how to eliminate it?

I'm using the Hauppauge prv usb2 tuner, a 1.6 GHz Core 2 Duo Dell laptop, intel GM965 graphics on the S-Video output, with standard definition.  XvMC is not yet supported for the GM965, so I'm using the standard playback (ffmpeg+XVideo).

I'm running cpufreq with ondemand. The CPU never gets above 14% during playback, and I always sit at the low cpufreq clock of 1 GHz.

I'm running 800x600 on the S-Video.  I've tried to set a Modeline to match the 720x480 of the tuner, but the intel driver seems to ignore the ModeLine.

I never experienced this on my old setup using the Hauppauge prv 350 tv-out.

Ideas?

Dan Bodoh

---

### Post by pssturges on 2008-06-12
1st thing to try would be different deinterlacing methods. Either by changing playback profiles, or changing the deinterlacing method within the profile you are using.

Choosing the right deinterlacing method for your setup can make a huge difference as far as motion blur goes.

Hope that helps,
Phil

---

### Post by danbodoh on 2008-06-12
Why is it necessary to deinterlace at all?

My system reads interlaced from the tuner and displays interlaced on an old-fashioned CRT TV via S-Video coming out of the Intel graphics.

Dan Bodoh

---

### Post by pssturges on 2008-06-12
You need to deinterlace always, unless your display is set at the exact same resolution as the content you are trying to play. This can only be done using either DVI,HDMI,VGA or component (scart maybe?). When using S-video or composite you can only use 640x480, 800x600 or 1024x768.

Phil

---

