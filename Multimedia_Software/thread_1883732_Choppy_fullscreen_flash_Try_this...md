---
title: "Choppy fullscreen flash? Try this.."
date: 2011-11-19
forum: Multimedia Software
---

### Post by light0 on 2011-11-19
Having trawled through numerous posts and articles which provided suggestions on improving flash performance, nothing worked on my particular hardware configuration. As there is nothing special about my hardware configuration (NVIDIA 6800 gfx card), I figure many people will be in the same boat I was. That is, trying various suggested fixes for flash but to no avail. 

After much searching, I came across this site:

[http://askubuntu.com/questions/16172/getting-flash-10-2-gpu-acceleration-working](http://askubuntu.com/questions/16172/getting-flash-10-2-gpu-acceleration-working)

This was after coming to the view that hardware acceleration was not functioning on my setup, given the extremely high CPU load under flash videos and despite having added the usual "OverrideGPUValidation=true" into /etc/adobe/mms.cfg. 

In the article above, it explains that a package called libvdpau1 must be installed, e.g. via:

sudo apt-get install libvdpau1

I tried this with the Adobe flash plugin installed by the flashplugin-installer package, yet I still received choppy video playback. 

Accordingly, I tried the latest 10.X series plugins (10.3.r183), downloadable from the adobe website. I believe that GPU support under linux for the 11.X flash plugins does not work.  

Then, much to my delight, flash videos began to work flawlessly under Ubuntu 10.4.3, as they do under Windows XP. 

So a three step process is as follows:

1) sudo apt-get remove flashplugin-installer
2) Download and Install Flash Plugin 10.3.XX from Adobe website
3) sudo apt-get install libvdpau1
4) sudo gedit /etc/adobe/mms.cfg, then put:

OverrideGPUValidation=true
EnableLinuxHWVideoDecode=1

Try flash. Hopefully it works now. If not, try removing pulseaudio and using alsa. I found pulseaudio to wreak havoc with my videos (either in mplayer or flash). Secondly, I ought to point out that I'm using compiz, composite and also DRI in my xorg.conf. If people would like more information on my particular settings then please ask and I'll supply.

---

