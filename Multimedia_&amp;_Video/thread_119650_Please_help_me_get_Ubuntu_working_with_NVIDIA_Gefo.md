---
title: "Please help me get Ubuntu working with NVIDIA Geforce 6100"
date: 2006-01-19
forum: Multimedia &amp; Video
---

### Post by adamthompson on 2006-01-19
I have a new computer with a Biostar Tforce6100-939 motherboard. So far I have been unable to get the Gnome Display Manager working--it crashes at start-up. I thought that installing the new NVIDIA driver would solve the problem, but it didn't. I used this guide [http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074") and was able to install the NVIDIA driver, as far as I can tell. The NVIDIA installer said that it installed it no problem. However, the new driver made absolutely no difference. GDM still crashes at start-up, just like before.

I believe that some people have managed to get NVIDIA Geforce 6100 graphics working with Ubuntu. If so, please share with me what you did to get it working.

---

### Post by HIGHLIFE on 2006-01-25
I just reconfigured the xserver and it worked fine for me.  Have you been able to get your ethernet working?  I'm having no luck with this board under linux:( .

---

### Post by Sefianix on 2006-03-07
Highlife, how did you reconfigure it?  which driver did you use?  

Nvidia's binary driver doesn't support the 6100 so no luck that route for me.  Did you use the vesa or nv driver?

:-k 

if you are having trouble with ethernet (and maybe sound too??), and you have a 6100 gpu, i could guess you have a mobo with nforce chipset?  Nvidia has drivers for the nforce boards like the 410 and 430.  However, I didn't need it for the ethernet; and they didn't work for me on the sound either.  

On a hunch, I ended up installing a really cheap sound card, and the ethernet card starting working during the install (before, it couldn't setup the ip thru DHCP.)  Hope this helps.

an nvidia thread:
[http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=75074&highlight=nvidia)

nvidia binaries:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by Sefianix on 2006-03-08
\\:D/ 

Great news.  Got the nvidia driver to work.  Hope the following info helps others.

The reason my efforts had always failed, it appears, was b/c the amd kernels and nvidia's binaries were not working well together.  my first efforts were with the amd 64 kernels.  Later, I switched to the k7 kernels under 32-bit but still no go.  Due to another post:
[http://ubuntuforums.org/showthread.php?t=134402&highlight=6100](http://ubuntuforums.org/showthread.php?t=134402&highlight=6100)
I figured there must be something i'm fouling up.  On a hunch, I went to the 686 kernel and voila it worked!  BTW, in case someone wonders, I did download the nvidia driver for each respective kernel.  At least for me, it turned out that it worked only under the 686 kernel.  Now I have everything working!

Edit:  I mentioned in the post before that the 6100 was not supported by the nvidia driver.  I said that b/c the 6100 wasn't listed as supported by the driver on nvidia's site.  But obviously i'm wrong.

---

### Post by Sefianix on 2006-03-08
I just wanted to add that at first it didn't seem to work but a restart got things going.

---

### Post by galligator on 2006-04-16
Hi,
           i have breezy badger installed on my Biostar TFORCE 6100 GEFORCE 6100 AND MY SOUND DOSENT WORK AT ALL!! WHEN I CLICK ON THE LITTLE SPEAKER ICON IT SAYS THAT IT CANT FIND ANY HARDWARE.............. HELP!!!!!!!!!!!!! THEN MY TOTEM MOVIE PLAYER DOSENT WORK EITHER. WHEN I PUT A DVD IN IT SAYS THAT TOTEM IS ALREADY IN USE BUT ITS NOT IF ANYBODY HAS ANY ANSWERS PLZ LET ME NO!

THANX.

---

