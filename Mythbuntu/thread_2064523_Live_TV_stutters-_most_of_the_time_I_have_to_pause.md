---
title: "Live TV stutters- most of the time I have to pause for a second"
date: 2012-09-29
forum: Mythbuntu
---

### Post by Steve666 on 2012-09-29
I have a fresh up to date 12.04 mythbuntu installation. I use DVB-T via a hauppage card. For some reasons the LiveTV stutters a bit most of the time. If I pause for a second the stream runs smooth again. In previous mythbuntu installations this was much better. The TV buffering seams not to run anymore in an optimized way. Any thoughts?
(my installation: Intel i3-2000T processor as CPU and GPU)

---

### Post by nickrout on 2012-09-29
> **Steve666 said:**
> I have a fresh up to date 12.04 mythbuntu installation. I use DVB-T via a hauppage card. For some reasons the LiveTV stutters a bit most of the time. If I pause for a second the stream runs smooth again. In previous mythbuntu installations this was much better. The TV buffering seams not to run anymore in an optimized way. Any thoughts?
(my installation: Intel i3-2000T processor as CPU and GPU)

I believe this has been fixed in 0.25-fixes. Update via mythbuntu-repos.

---

### Post by Rotak on 2012-09-29
Also check your playback profiles. Some of them were removed, So you need to choose another one.

---

### Post by Steve666 on 2012-09-30
Thanks for your replies.

The latest 0.25 repos-fixes were already installed. 
I will try to change the playback settings. Has anybody a satisfying setting for a Intel i3-2100 CPU/GPU processor? ):P

---

### Post by Steve666 on 2012-10-01
I played around with some different playback profiles. The problem stays. But maybe I have not chosen the right combination. :confused:

---

### Post by nickrout on 2012-10-01
> **Steve666 said:**
> I played around with some different playback profiles. The problem stays. But maybe I have not chosen the right combination. :confused:What have you tried?

---

### Post by utar on 2012-10-01
I had this problem too when I first installed 0.25:

[http://ubuntuforums.org/showthread.php?t=1956746](http://ubuntuforums.org/showthread.php?t=1956746)

I "fixed" it by using the vdpau decoder for all TV playback.  Unfortunately with your Intel GPU you don't have that option.

---

### Post by Steve666 on 2012-10-22
Unfortunatly, I am using the GPU of the Intel i3-2100T CPU thus cannot use VDPAU.
I tried almost every combination of the playback options. Still the problem persists: Usually the Live-TV stutters when I switch the channel. Then I have to pause for a second and afterwards it works almost fine (still not always a smooth picture).

---

### Post by maxxx1234 on 2012-11-06
I have the same problem, using mythbuntu 12.04/mythtv 0.25 with intel G630T integrated graphics.

On liveTV, I have to pause for a second, otherwise it laggs every 3-4 secs. Tried playing around with playback profiles, deinterlacers, buffers etc. to no avail.

This is annoying as hell and basically breaks liveTV on Intel chipsets :(

---

### Post by nickrout on 2012-11-06
> **maxxx1234 said:**
> I have the same problem, using mythbuntu 12.04/mythtv 0.25 with intel G630T integrated graphics.

On liveTV, I have to pause for a second, otherwise it laggs every 3-4 secs. Tried playing around with playback profiles, deinterlacers, buffers etc. to no avail.

This is annoying as hell and basically breaks liveTV on Intel chipsets :(What playback profile are you using and which have you tried?

---

### Post by maxxx1234 on 2012-11-06
> **nickrout said:**
> What playback profile are you using and which have you tried?

Hi, I'm using OpenGL normal, and have tried all OpenGL and all "Normal" profiles. The rest does not seem to be an option (VAAPI crashes the frontend, and I don't have AMD/NVIDIA cards for VDPAU etc.).

I have now found reference to this bug and it seems to be fixed in 0.26:
[https://github.com/MythTV/mythtv/commit/483e06f6b8a9066f66cef3fcf0a5f844519f51f9](https://github.com/MythTV/mythtv/commit/483e06f6b8a9066f66cef3fcf0a5f844519f51f9)

Does anybody know how to request this fix to be backported to 0.25 as part of 0.25-fixes?

---

### Post by nickrout on 2012-11-07
> **maxxx1234 said:**
> Hi, I'm using OpenGL normal, and have tried all OpenGL and all "Normal" profiles. The rest does not seem to be an option (VAAPI crashes the frontend, and I don't have AMD/NVIDIA cards for VDPAU etc.).

I have now found reference to this bug and it seems to be fixed in 0.26:
[https://github.com/MythTV/mythtv/commit/483e06f6b8a9066f66cef3fcf0a5f844519f51f9](https://github.com/MythTV/mythtv/commit/483e06f6b8a9066f66cef3fcf0a5f844519f51f9)

Does anybody know how to request this fix to be backported to 0.25 as part of 0.25-fixes?mythtv-dev mailing list would be the place.

---

### Post by Steve666 on 2012-11-07
I have already upgraded to 0.26 and the problem still exists.
Interesting is that in the versions below 0.25 the problem was not there with exactly the same hardware.
:(

---

### Post by Steve666 on 2012-11-08
I opened now a bug for the developer. Hopefully someone will look into it.

---

### Post by Steve666 on 2013-02-09
I even changed now my GPU and installed a separate NVIDIA card. I changed the playback profile to VDPAU (all three different qualities) and the problem still persists. The only thing that improved is the smoothness of the picture moves.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by maxxx1234 on 2013-02-11
Opening tickets with the mythtv devs will not help, usually they just close them without a resolution.

Honestly, I would advise you to install XBMC as the frontend and use mythtv as the backend only. XMBC v12 has been out for some days now, and contains native support for mythtv. No stutters, and video accell works.

The mythtv frontend is such a crappy piece of software with so many bugs and horrible support that it is not worth to bother with. And thanks to XBMC, we don't have to anymore :)

---

### Post by PhilWig on 2013-02-12
Steve,
 A silly question probably but when you fitted your Nvidia card, did you invoke the drivers?
On my 12.04 system I needed  
Mythtv control centre 
> launch restricted drivers manager 
> nvidia accelerated graphics driver (version current) [recommended]

Best wishes
Phil

---

### Post by nickrout on 2013-02-12
> **maxxx1234 said:**
> Opening tickets with the mythtv devs will not help, usually they just close them without a resolution.

Honestly, I would advise you to install XBMC as the frontend and use mythtv as the backend only. XMBC v12 has been out for some days now, and contains native support for mythtv. No stutters, and video accell works.

The mythtv frontend is such a crappy piece of software with so many bugs and horrible support that it is not worth to bother with. And thanks to XBMC, we don't have to anymore :)let's see

* xbmc frontend looks dire
* xbmc deinterlacing far inferior
* xbmc frontend much slower

being an avid user of both XBMC and mythtv I still prefer mythtv frontend for watching live TV or recordings.

Personal preference of course.

---

### Post by alien878 on 2013-02-13
Same problem here.  Atom 330, Nvidia, VDPAU, latest nvidia drivers.  For the last few months, SD channels need a pause/unpause in livetv or they stutter.  HD channels are not a problem.  SD/HD playback settings are the same.

Looking at the playback info OSD (really cool display), it seems there is a definite buffering issue until I do a pause/unpause.  Percent buffer used is low and buffered frames keeps dropping.  Buffered frames stays at the max value for HD or after the pause/unpause on SD.

---

### Post by Steve666 on 2013-02-17
> **PhilWig said:**
> Steve,
 A silly question probably but when you fitted your Nvidia card, did you invoke the drivers?
On my 12.04 system I needed  
Mythtv control centre 
> launch restricted drivers manager 
> nvidia accelerated graphics driver (version current) [recommended]

Best wishes
Phil


Hi Phil, sometimes silly questions are the right thing to raise. But I have installed the latest driver, have them recognized in the mythtv control-center and I already also played around with the nvidia setting dialog interface. Unfortunatly, the stuttering when I start to shift to a new channel in live-TV mode stays the same.

Just a side notice:
I even have now new problems besides this stuttering.
With the GPU on the iCore processor, the smootheness of motions was (besides this clear stuttering) not perfect. Now with the NVidia Card and VDPAU settings this looks much smoother but now I get artifacts once a while for a fraction of a second. I still have DVB-T with low resolution which is calculated to 1080p. Maybe this would not happen if I would have HDTV already as a source signal (at least demo HDTV videos look very nice and the artifacts did not show up) . But somehow the VDPAU settings seem not to be perfect for scaling the picture from old TV resolution to 1080p even though hardware exceleration is working on the nvidia GPU.

---

### Post by topcat5 on 2013-02-18
I recommend that you read the Myth wiki for proper Nvidia settings.  There is a section on stutter free viewing.   It's also very important that you have sync to vblank enabled.  I noticed that on my last install, it wasn't enabled by default.

---

### Post by Steve666 on 2013-03-14
> **topcat5 said:**
> I recommend that you read the Myth wiki for proper Nvidia settings.  There is a section on stutter free viewing.   It's also very important that you have sync to vblank enabled.  I noticed that on my last install, it wasn't enabled by default.

I tried all this out. Still no change. It looks that the bug does not disappear. I am thinking of reinstalling everything again from scratch since it sounds that the problem is not an issue for most of you.

---

### Post by koma77 on 2013-04-12
This is most likely due to the playback being too close to the "edge" of the record buffer. That is why it helps when you pause for a while.

I have to do the same on some of my channels. Maybe those channels have extra high bandwidth or GOP-length.

---

