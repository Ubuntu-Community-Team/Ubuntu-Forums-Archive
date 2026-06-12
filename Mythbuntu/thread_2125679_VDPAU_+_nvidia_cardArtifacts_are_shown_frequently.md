---
title: "VDPAU + nvidia card:Artifacts are shown frequently"
date: 2013-03-14
forum: Mythbuntu
---

### Post by Steve666 on 2013-03-14
Dear all, I have mythbuntu 0.26 on an intel core i3 T2100 cpu and a nvidia graphics card (GT610) system installed. I hoped to get a better, smoother video performance than just running the integrated gpu of the cpu. The video performance improved by smoother moves but there are frequently the following problems (videos and live-tv):
a) artifacts are shown frequently
b) horizontal moves end up in a sligh jumping picture move

I tried almost everything already that is recommended at [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU) .

What else can it be? Has anybody a similar problem or are all other happy running mythtv with a nvidia gpu and VDPAU?

---

### Post by AlecJ on 2013-03-14
You don't say what driver your using?

This will get the latest installed.
```

[COLOR=red]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update 
sudo apt-get install nvidia-current[/COLOR]
```

---

### Post by PhilWig on 2013-03-15
Steve,
You seem to have a real hum-dinger here! 
No magic solution but three things things you might like to check after Nvidia driver as Alec suggests:
1.  Did you need to switch your bios to get it to accept the new card?   Is there an option to allocate memory to it?
2.  When you play a video which shows the problem, is it consistent?  Are the faults/artifacts the same every time?  If so, then video source is implicated not the display stuff.
3.  Other hardware - Cooling?  Memory soak test?
Phil

---

### Post by Steve666 on 2013-03-15
Thanks for the hint.
I actually have now nvidia driver v304.64 (status Nov 2012) running and I looked up that there are new one available. Since there was an upgrade done lately I thought that the Nvidia driver was also updated. But seems to be not the case. I try the manual update as you suggested and will see if something changes (hopefully). Cheers Steven

---

### Post by Steve666 on 2013-03-16
I updated to the latest driver now and the the issues are still there.
I wonder if it might be caused by the fact that I use a DVB-T signal at the moment which is scaled up by mythtv to 1080p. Could it be that in case of a poor DVB-T resolution, the algorythms have problems to scale it up?
I downloaded some short HDTV demos which look fine. Maybe I need to organize a complete HDTV movie to test it.

---

### Post by novellahub on 2013-03-19
Have you tried this?

[http://www.mythtv.org/wiki/VDPAU#Tearing.2FStuttering](http://www.mythtv.org/wiki/VDPAU#Tearing.2FStuttering)

following lines in /etc/X11/xorg.conf:

```

   Section "Extensions"
       Option "Composite" "Disable"
   EndSection

```

I had to do this with my GT 240 Nvidia card.  It cleared up the same symptoms on my setup.

---

### Post by Steve666 on 2013-03-19
yes, I followed the little change in the xorg.conf. Did not change the symptoms. :(

---

### Post by newlinux on 2013-03-19
Can you try playing back the problem recordings with VDPAU disabled? I have much older hardware, but it's documented for my nvidia cards that corruptions in the stream will cause poor image quality from time to time when using hardware acceleration. When using software decoding these problems don't manifest in the output as bad.

---

### Post by BicyclerBoy on 2013-03-27
The GT610 can decode 2 HD streams but is very light on shader performance. So it is possibly underclocked for de-interlacing/denoise/sharpen & HQ scaling (VDPAU feature set C & D).
The GT610/520 are not recommended for OTA broadcast streams, fine for HD BD24p.

You could try VDPAU slim or normal instead of HQ..

The composite setting in xorg.conf blocks the composite effects window managers (compiz, mutter, metacity, clutter etc)
Composite forces VDPAU to use blitter video presentation which is less efficient & does not prevent tearing.

I don't think mythbuntu Xfce using composite effects manager but if it does there could/should be a tool for disabling composite redirection for full-screen (un-redirect fullscreen video) 

In Unity & likely Gnome2 (both compiz):
You can disable compiz composite (effects manager) for "full screen apps" by using "ccsm" tool & selecting "un-redirect fullscreen".
KDE has a "kwin" setting to do the same..

My GT240 has no playback issues (VDPAU + denoise/sharpen/2xadv-deinterlace/HQscale) driving 2 screens with composite not blocked.
The scaling/sharpen is only required for DVD playback.

---

### Post by Steve666 on 2013-04-04
Thanks for the feedback.
I was so far not aware that GT610 is not recommended for OTA. Since I already had the suspicion that a frequently poor DVB-T quality due to high compression might be the cause - I tried out some demo HD videos and it looks that there is no problem. I plan now to switch to HDTV in the nearby future and decomission DVB-T.
If I use software decoding the artifacts are not shown but movements are poorly displayed (then the performance is nearly the same if I use the GPU of the I3-2100T CPU).
Since I am using mythbuntus xfce desktop, the compiz settings should be of nor relevance.

---

### Post by BicyclerBoy on 2013-04-06
All 1080 broadcast OTA is interlaced 1080i..
Some of the early dvb-t freeview here was 720p50 & 1080i, now all 576i & 1080i.

Most demo stuff I've seen is progressive..
In the UK the dvb-t stuff is ?? 576i, 576p, 720p

The decoder in the 610 is fine (very good), it is the shader that is weak.
No/little shader performance is required for BD24p & US 720p (no scaling).
But good VA (feature set C&D) de-interlacing & scaling needs GPU power..

Broadcast TV is highly compressed but there should not be any decoding artifacts.
VDPAU slim or normal (maybe) should be fine.

The s/w de-interlacers (like yadif etc) are very CPU intensive
The intel (VAAPI) de-interlacers are still not very good yet..

So maybe you're right that the scaling is the problem. Try driving the TV at 720p & not at native.

---

