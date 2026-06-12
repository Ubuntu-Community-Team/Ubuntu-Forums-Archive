---
title: "NVIDIA ION + Ubuntu 11.10 = Youtube stutter"
date: 2012-02-15
forum: Multimedia Software
---

### Post by jzn123 on 2012-02-15
Hi all,

I own a Shuttle Barebone XS35GT which runs with an Atom D510, 2 GB RAM, Intel 40 GB SSD and a  NVIDIA ION video chipset. This system worked perfectly with ubuntu 10.10 but since the upgrade to 11.10 the movies in firefox & chrome are stuttering, especially with HD. We tried multiple drivers, right now the latest Nvidia Linux Display Driver 290.10 + VDPAU is installed from multiple sources but it doesn't solve the problem.

Any suggestions to make the stuttering disappear?

---

### Post by jzn123 on 2012-02-17
Yes it would be very nice to know why the graphics were performing perfectly at 10.10 and now since 11.10 are stuttering.

---

### Post by jzn123 on 2012-02-25
We're thinking about going back to 10.04 because this way it's impossible to watch movies on youtube.

---

### Post by gaward on 2012-03-04
Hi,

to clarify I am also using a mini ITX motherboard (Intel Atom with Nvidia Ion chipset, 4GB RAM) and I am incurring exactly the same problem. I have installed the latest Nvidia drivers and have made a few smal attempts at playing with compiz, all without success.

As per your findings, I could watch HD movies and H.264 video without a problem on Ubuntu 10.xx but no longer, since upgrading to 11.xx . Firefox and videos all suffer from permanent stutters. I have confirmed the files I am using are in good order; they play perfectly on my Western Digitial set top box on my TV.

The choppy video is also consistent regardless of which media player I use too, EG VLC or Totem etc. With regard to Firefox, it may be a seperate issue, but I have noticed it stalls while loading pages, or when you are scrolling down a page. IE it has lost its responsive feel I'm accustomed to from earlier Ubuntu versions.

---

### Post by snowpine on 2012-03-04
I recommend using Minitube or downloading the movie to your hard drive and watching with your favorite media player (I use VLC personally) for best performance.

---

### Post by gaward on 2012-03-08
I cannot speak for all Nvidia cards, however I can say that I have had very few problems with my Nvidia Ion graphic chip-set working with Ubuntu in the past. The earlier versions of Ubuntu failed to install or utilise the correct driver (or propriety Nvidia close source driver) however this seems to no longer be the case. I have only succeeded in crashing my machine once (early days when I knew less than nothing about Linux) by forcing it to use the Nvidia driver when there were compatibility issues.

I think you will find that support for Linux by Nvidia has improved greatly, and you should have few (if any) problems getting your graphics card to work. Check on Nvidia's website for Linux driver compatibility for your specific card.

Historically (IE the last year or so) I have had no problems even with the most demanding video playback resolutions and formats etc. The problem I have posted here I am confident will be overcome in due course and are recent issues since upgrading to the latest version of Ubuntu.

---

### Post by gaward on 2012-03-08
downloading and then watching using VLC does not work I'm afraid. The video insists on being choppy or stuttering regardless of which player I use. I am therefore convinced it is either a codec or Nvidia driver (latest version installed) issue. Why it has only shown itself now after I upgraded to the latest version of Ubuntu, I don't know. I have read that this could be a Compiz issue too (integral part of Ubuntu GUI) but I don't know where to even start with this, or how to access it!

---

### Post by winh8r on 2012-03-08
First thing to try is check your Flash configuration.

Click on the link in my sig below "Help With Flash" and follow the instruction there.

See if that helps.

---

### Post by Eromatic on 2012-03-08
Didn't Adobe disable VDPAU hardware acceleration for on Adobe Flash 11 awhile back? Check your CPU usage when playing a video. If it's too high, it would be likely that VDPAU hardware acceleration is not being used. Or on the Youtube flash video window, you can right-click on the video and then select *Show Video info*. The info window needs to indicate *Hardware video rendering* and *Hardware video decoding* for it to be properly using GPU video acceleration.

---

### Post by Jose Catre-Vandis on 2012-03-08
Try turning off hardware acceleration in flash player? Right click on the video, > settings and untick the box.

---

### Post by pivert on 2012-03-18
Same problem here : 
- FP11.1.102.63
- Nvidia ION in Twinview.

Impossible to get HW acceleration to work, while it was working with older releases of flash.

I tried the HTML 5 version, however I'm missing h264 codec in Firefox, and I'm not sure Firefox is using hw acceleration for now. If someone has a link on how to setup hw acceleration for html5 video in Firefox...

Thanks,

---

### Post by TenPlus1 on 2012-03-18
Installed Flash 11.2 RC and hardware accel works on Ion and Ion2 gfx, only thing I've come accross is browsers that use hardware accel also which steals some of the GPU time as well but easily fixed by turning it off...

---

### Post by pivert on 2012-03-18
Thanks TenPlus1,

Same config, same solution, same results : It Works !!!

- I just downloaded flash 11.2 RC from :
[http://labs.adobe.com/downloads/flashplayer11-2.html](http://labs.adobe.com/downloads/flashplayer11-2.html)

- Removed current flash installation : aptitude remove flashplugin-installer
- And installed from the tar.gz as described in the readme.txt file inside.

I immediately got the HW acceleration working. (Of course, I had already libvdpau1 installed, and the /etc/adobe/mms.cfg file as described in many forums).

Thanks a lot,

---

