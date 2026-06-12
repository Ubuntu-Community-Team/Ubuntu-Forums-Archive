---
title: "Need suggestions for tweaking playback performance during full screen panning"
date: 2008-01-06
forum: Mythbuntu
---

### Post by ubnewbie2 on 2008-01-06
I have a machine running mythbuntu that has reasonable specs

Athlon x64 4200+ cpu
1GB ram
nVidia Geforce 7 video card
500GB sata hard disk

and it runs very well, can record 2 HD TV programs from my 2 DVB-T tuners and playback at the same time.

One small glitch happens, however,  when watching a scene that pans very quickly through a scene.  I guess this is the hardest thing for the video to cope with.  What happens is that about half a dozen horizontal glitches appear across the picture. They aren't lines or noise, just more like discontinuities in the picture,  as if the half dozen bands across the picture don't quite all pan at the same time in sync.

They only exist while there is panning motion, and if part of the picture is stationary (like a shot of someone in a car with the scenery going past outside) then the lines are only visible in the moving bits.

It's only a little bit distracting, but if there was something I could try, - maybe a setting I can tweak, I'd like to see if I can get it perfect.

Of course, it MIGHT be being caused by something outside the myth box, like my flat panel TV which is being fed by a VGA input from the mythbox, and so is upconverting the video to it's native resolution on the fly.

Anyway - any comments/suggestions are welcome :-)

---

### Post by ubnewbie2 on 2008-01-07
An update:  I attached a cable between the DVI output on my nVidia card and the HDMI input on my flat panel (intending to see if the problem exists via HDMI).  However, before I enabled the DVI output under xorg, I happened to try playing a movie via the VGA cable which was also still connected.

It seems like the problem is fixed.  I will wait until I have watched some more stuff before I am confident.  My current theory is that, attaching the DVI/HDMI cable has allowed the driver to interrogate the flat panel and set itself to a better mode.  A quick look in the xorg log shows it is defaulting to "nvidia-auto-select", so maybe...

---

### Post by szwety on 2008-01-11
i don't have the same card as you i have an nvidia 4400 on my dell laptop i'm getting that same glitch with the panning, is there any way to fix it?

---

### Post by ubnewbie2 on 2008-01-11
Well, the problem can be fixed, but I don't know exactly what parameters have changed.  As I posted, my problem went away when I plugged in the HDMI cable.  If someone can suggest a way of discovering the details of what the nvidia-auto-select mode is selecting, we might have some clues as to what works I suppose.

---

### Post by laga on 2008-01-12
Have you tried to enable deinterlacing?

---

### Post by ubnewbie2 on 2008-01-12
> **laga said:**
> Have you tried to enable deinterlacing?

I've always had deinterlacing turned on.  This problem doesn't look anything like interlacing problems.  Interlacing problems manifest on any fast moving object and give you that comb like effect on the moving object.  This is half a dozen or so wide horizontal bands, with a discontinuity between them, on large areas of panning.

---

