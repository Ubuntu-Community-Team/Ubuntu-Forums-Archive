---
title: "NVidia TV-Out problem"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by markkun on 2007-06-23
I have this strange problem with my Gutsy Gibbon ubuntu. I don't really know how to explain it, but hopefully that attached screen shot explains it all.

My xorg.conf is configured with two screens, normal monitor and TV out.

Does anyone know a fast work around for this problem. In KDE system with radeon I managed to repair this with  options "VideoOverlay" "off/on" and "GLOverlay" "on/off". But in Nvidia those doesn't work.

Basically my tv-out fullscreen movies plays, but it's in the bottom of the screen and misses most of the image.

Please help me! :)

---

### Post by jrib on 2007-06-23
This happened to me because the resolution was too large for tvout, try changing it to 640x480 .  I use twinview by the way.

[edit] I meant, I *don't* use twinview.  I have a seperate screen for the TV.  I set everything up with nvidia-settings

---

### Post by markkun on 2007-06-24
It's not about the resolution. The same problem is with 640x480 and 800x600.

I had no problem with the same video card in my Kubuntu computer. I changed to Gnome, But haven't tried this video card in it and I'd rather not try.

---

### Post by medhamsh on 2007-06-24
i face the same problem. I have connected the s-video out cable to my laptop and the audio video pins to the tv set but things getting wierd.
i did changes using nvidia-settings. it recognised the tv but in the tv just flickering is coming. what should i use ? twin view or seperate x-server? please help me...any changes to be apllied to the xorg.conf manually?
thanks in advance...

---

### Post by markkun on 2007-06-24
Problem solved: Downloaded Feisty and installed it. Everything works smoothly now.

Maybe it is a bug of some sort in Gutsy that need fixing.

---

### Post by amac777 on 2007-06-24
Hello all, I'm trying to do this too using an Nvidia FX 5200. I plug in my TV's yellow RCA cable between the video card and the TV's video input. Then I run vnidia-settings to configure the screens but I still only see my computer monitor. I know this used to work - at least once I could use nvidia-settings to setup the resolution on my tv and use twinview etc so I know the hardware does work. But for some reason, I just can't seem to get nvidia-settings to detect my TV and allow me to configure it. 

Anyone have any suggestions? 
Do I need to do some kind of a manual change to xorg.conf in order to allow nvidia-settings to detect the TV?

---

### Post by markkun on 2007-06-25
I'd use S-Video cable to connect to TV if your video card has one. If you don't have a S-Video plug in your tv, then I'd use a S-Video -> Scart adapter.

I have my doubts about using RCA cable..

---

### Post by amac777 on 2007-06-28
Well, my nvidia card (FX 5200) doesn't have an S-video card... Just on the offchance that the rca cable was broken, I tried a different cable and to my amazement it worked (was detected by nvidia-settings and could use etc). Put the old cable back and it no longer works. So looks likes my hours of time trying to change the xorg.conf file was just wasted effort cause the problem was hardware related not software. doh

---

### Post by Thalskarth on 2007-07-16
> **amac777 said:**
> Hello all, I'm trying to do this too using an Nvidia FX 5200. I plug in my TV's yellow RCA cable between the video card and the TV's video input. Then I run vnidia-settings to configure the screens but I still only see my computer monitor. I know this used to work - at least once I could use nvidia-settings to setup the resolution on my tv and use twinview etc so I know the hardware does work. But for some reason, I just can't seem to get nvidia-settings to detect my TV and allow me to configure it. 

Anyone have any suggestions? 
Do I need to do some kind of a manual change to xorg.conf in order to allow nvidia-settings to detect the TV?

Hello, i have a similar question... i also have a Nvidia FX 5200, but my card have a S-Video plug and I use a S-Video cable...

Yesterday i've intalled Ubuntu 7.04... and when i've activated que desktop effect i've installed que nvidia "protected" drivers... and i don't have signal in my TV... how can i enable que TV-Out???

Should I configure manually the xorg.conf?? what should i do??

Thank you

---

### Post by amac777 on 2007-07-20
Make sure your TV is plugged into the S-video cable and is connected to your computer and is turned on.

Then run this command at the terminal:

```
nvidia-settings
```

You can use that program to configure and activate your TV-out to split the screen (twinview) or run as a separate X window.

Hope that helps. It worked for me once I replaced the faulty cable between the computer and the TV.

---

