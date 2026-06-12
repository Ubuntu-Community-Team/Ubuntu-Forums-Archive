---
title: "HD Video &quot;tearing&quot; in SMPlayer"
date: 2010-05-27
forum: Multimedia Software
---

### Post by hsoulen on 2010-05-27
Hi Folks,

Hope someone out there can assist.

I have an Asus 1201n Netbook, dual-core Atom 330 (with HT), NVidia ION chipset and 4GB RAM. I have the NVidia proprietary driver 195.36.24.

I am using mplayer/smplayer with vdpau which I am confident is working as1080p/720p video play with ~20-30% CPU and look fantastic except for one tiny problem... Video tearing!!!

It does not matter what content I play, divx/xvid/mp4 with any container, avi/mkv the same thing happens. If I play the same non-HD content in Totem the video is clean but as soon as I play it in mplayer/smplayer the video tears, even if smplayer is using ffmpeg it still tears and I am getting frustrated :confused:.

I found this post and although this seems to have temporarily solved the issue with HD video, now any OpenGL game just looks awful!

[http://www.function13.net/2010/02/22/ubuntu-9-10-karmic-koala-fix-video-tearing-with-compiz-nvidia-geforce-gts-250/](http://www.function13.net/2010/02/22/ubuntu-9-10-karmic-koala-fix-video-tearing-with-compiz-nvidia-geforce-gts-250/)

Is it possible to have the best of both Worlds or am I just doomed to the tearing?

Cheers,

Hank

---

### Post by Jose Catre-Vandis on 2010-05-27
I'm on Xubuntu and have compositing turned off. This gives tear-free playback of HD video in mplayer using vdpau. So maybe live without Compiz? I use gl2 for xvids/avis to get tear-free there.

---

### Post by hsoulen on 2010-05-27
> **Jose Catre-Vandis said:**
> I'm on Xubuntu and have compositing turned off. This gives tear-free playback of HD video in mplayer using vdpau. So maybe live without Compiz? I use gl2 for xvids/avis to get tear-free there.

Thanks, you are 100% correct that disabling Compiz is the ultimate solution but I am just a sucker for cubes, folding airplanes and fire on my screen :guitar:

Sad I know but I am trying to see if there is a happy medium with compositing + vdpau and unfortunately I think your answer is probably the only one, pick fancy effects or clean video.

Cheers,

Hank

---

### Post by hsoulen on 2010-06-03
Just called it a day with Compiz and turned off the desktop effects.

Will miss my "wobble" but at least HD vid is sweet and my battery lasts a bit longer.

Cheers,

Hank

---

### Post by whiskthecat on 2010-10-19
Hey guys, there is a setting under the CompizConfig Settings Manager. Grab it from the package manager if you dont have it. Now, General -> General Options -> Display Settings -> Enable Sync to VBlank. Problem solved, now vsync is on for Compiz. :popcorn:

---

