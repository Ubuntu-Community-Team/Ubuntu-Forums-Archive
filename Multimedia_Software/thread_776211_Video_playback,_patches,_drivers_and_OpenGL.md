---
title: "Video playback, patches, drivers and OpenGL"
date: 2008-04-30
forum: Multimedia Software
---

### Post by HTML-insane on 2008-04-30
This isn't a, "how do you fix it" question, more like a, "why is it broken" question:
Which driver is the, "auto" driver in e.g. Xine/kaffeine? Is it OpenGL?
If not, why do OpenGL based desktops interfere with it?
How does the Mplayer patch work, and can the same method be used with other programs (KDE4's Dragon player, for example)? If so, why hasn't this already been done, seeing as KDE4 comes with it's own composition effects?

I'm asking because I want to go into computing in the near future (filling my head with code), and I want to be able to contribute to the free world (as well as changing things here and there to look/behave how I want them to, because that would be fun).

---

### Post by Melcar on 2008-04-30
I think "auto" reverts to using X (or Xv if your graphics chip supports it), but I'm not sure.  The problem you describe is more of a limitation than anything else.  Once DRI2 comes out, then we will be able to use accelerated 3D desktops and still render videos in opengl/Xv.

---

### Post by Nergar on 2008-04-30
this seems like a nice place to ask, why does the video playback quality is worse than in windows?

I have plenty of h264 encoded videos and video playback is a little choppy, just enogh not to enjoy them at 100%

and I really dont like the idea of booting XP or whatever just to watch a movie.

and hardware isn't the problem unless a quad core, nvidia 8400 and 4 GiB of ram isn't enough

there must be a something i need to change, like video driver or something but being new in linux, I really dont know what.

---

### Post by Nergar on 2008-05-01
I did some reading and I cant believe how many things are taken into account for graphical output, like choosing between Xorg or Xfree86, xgl, opengl, AIGLX, and lots and lots of things. The solution may be to standardize all this in the linux world. This is one big disadvantage over commercial OSs. A lot of people is working on things but most go in different directions which IMHO makes all this projects not as solid as they could be.

meh. still, this is better than using a proprietary OS.

---

### Post by HTML-insane on 2008-05-01
> **Nergar said:**
> this seems like a nice place to ask, why does the video playback quality is worse than in windows?

I have plenty of h264 encoded videos and video playback is a little choppy, just enogh not to enjoy them at 100%

and I really dont like the idea of booting XP or whatever just to watch a movie.

and hardware isn't the problem unless a quad core, nvidia 8400 and 4 GiB of ram isn't enough

there must be a something i need to change, like video driver or something but being new in linux, I really dont know what.

Really? Because whenever I watch DVDs on my Linux machine, the only time it's not DVD quality is when I use the xshm (or something like that) driver. The bonus is it isn't interfered by 3D desktops.

---

### Post by HTML-insane on 2008-05-05
> **Melcar said:**
> I think "auto" reverts to using X (or Xv if your graphics chip supports it), but I'm not sure.  The problem you describe is more of a limitation than anything else.  Once DRI2 comes out, then we will be able to use accelerated 3D desktops and still render videos in opengl/Xv.

What's DRI2, and when does that come out?

---

### Post by sloggerkhan on 2008-05-05
> **Nergar said:**
> this seems like a nice place to ask, why does the video playback quality is worse than in windows?

I have plenty of h264 encoded videos and video playback is a little choppy, just enogh not to enjoy them at 100%

and I really dont like the idea of booting XP or whatever just to watch a movie.

and hardware isn't the problem unless a quad core, nvidia 8400 and 4 GiB of ram isn't enough

there must be a something i need to change, like video driver or something but being new in linux, I really dont know what.

The issue you have is that your nvidia card isn't actually accelerating the playback of h264, or at least the decode, which is the intensive part. And for a 1080p video, I would say it takes about 1 2.2 ghz core to do solid effective high quality decode. So what you might have to do is make sure that your ffmpeg decode of of h264 1080p vids is multi-threaded at launch.

However, you shouldn't have and trouble with 720p or smaller h264.

---

### Post by Nergar on 2008-05-07
> **sloggerkhan said:**
> The issue you have is that your nvidia card isn't actually accelerating the playback of h264, or at least the decode, which is the intensive part. And for a 1080p video, I would say it takes about 1 2.2 ghz core to do solid effective high quality decode. So what you might have to do is make sure that your ffmpeg decode of of h264 1080p vids is multi-threaded at launch.


How can i use my nvidia card for video acceleration and how do i make ffmpeg decode multi-threaded?

this can get really annoying.

---

### Post by Melcar on 2008-05-07
> **Nergar said:**
> How can i use my nvidia card for video acceleration and how do i make ffmpeg decode multi-threaded?

this can get really annoying.

I don't think any of the drivers (be they from ATI or nvidia) can properly decode h264 video yet.

---

### Post by HTML-insane on 2009-06-17
Update: so it looks like more recent hardware with more recent graphics cards and more recent graphics card drivers don't have this problem. I see how it's more of a limitation then a problem now...

---

### Post by Melcar on 2009-06-17
Nvidia circumvents (more like replaces) X, and the current ATI drivers have their own DRI2 implementation. Neither will suffer from blinking anymore.  In the open source front, only the latest Intel drivers have initial DRI2 support, with the rest being worked on; this means that for the most part you will still suffer from blinking.
As for accelerated HD content, nvidia has VDPAU which is being widely used now.  ATI has XvBA, which is a replacement for UVD, but for some reason nobody is even bothering to look at it.  I don't know what Intel has.

---

