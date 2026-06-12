---
title: "Video Playback Problems in Miro"
date: 2011-01-29
forum: Multimedia Software
---

### Post by KFwLsKvVAs on 2011-01-29
Hello,

I am having trouble with video playback in Miro.  Videos downloaded and opened within Miro appear very dark and like...primary colors only, and very choppy to boot.  Opened with MPlayer from within Miro, same result.  

However, videos on my hard drive opened with MPlayer or VLC work perfectly fine.  

So I was wondering is there a way to change the video driver that Miro uses?  I know there isn't in any of the preferences menus, but what about editing a file or something?  

Here's the relevant portion of my lspci output:

```
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
```

So it's an integrated Intel card on a generic pentium 4.  

Anybody have any thoughts?

---

### Post by inof8or on 2011-05-24
If your running higher res videos miro will choke, especially on a p4, part of the reason i upgraded to a newer computer. Now since i have installed natty ive been getting choppy videos on my two year old computer. 

You could try switching to xine as the back end video player, its in the miro preferences last time I checked. (probably wont work) What I used to do when i was on a P4 i would just go directly to the .miro folder (press crl+h in your home) then play the files separately. Not glorious, but it works

---

### Post by beew on 2011-05-24
> **inof8or said:**
> If your running higher res videos miro will choke, especially on a p4, part of the reason i upgraded to a newer computer. Now since i have installed natty ive been getting choppy videos on my two year old computer. 

You could try switching to xine as the back end video player, its in the miro preferences last time I checked. (probably wont work) What I used to do when i was on a P4 i would just go directly to the .miro folder (press crl+h in your home) then play the files separately. Not glorious, but it works

I don't find any option to change backend player in Miro's preference. Can you be more specific? Thanks.

---

