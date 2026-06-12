---
title: "Capture Card Recommendation: what is compatible with the current kernel?"
date: 2012-09-09
forum: Mythbuntu
---

### Post by dpapathanasiou on 2012-09-09
[As I posted before]("http://ubuntuforums.org/showthread.php?t=2044125"), I'm getting kernel panics when playing video.

At first I thought it was the video card and driver (an old ATI on-board), but even after replacing the video card with an nvidia one, I was still getting the same problem.

As [Rotak noticed]("http://ubuntuforums.org/showpost.php?p=12183110&postcount=10"), the problem was not the video card, but the capture card.

Since then, I tried both downgrading the version & kernel, as well as running the bleeding kernel from the ppa, but the panic still occurs.

So I'm resigned to the fact that I need to replace my capture card.

Despite going though [this thread]("http://ubuntuforums.org/showthread.php?t=566529"), I'm not sure which card would work with the current kernel.

I'd been using Hauppauge's 1187 WinTV-HVR-1250 Hybird PCI-E card for over a year, and never had any problems with it until recently.

I'm considering the [pcHDTV-5500]("http://www.pchdtv.com/hd_5500.html") since it was specifically designed for linux, unlike Hauppauge and these other cards, but it's almost five years old now, and I wonder if I'll have the same problems with the current kernel.

---

### Post by nickrout on 2012-09-09
> **dpapathanasiou said:**
> [As I posted before]("http://ubuntuforums.org/showthread.php?t=2044125"), I'm getting kernel panics when playing video.

At first I thought it was the video card and driver (an old ATI on-board), but even after replacing the video card with an nvidia one, I was still getting the same problem.

As [Rotak noticed]("http://ubuntuforums.org/showpost.php?p=12183110&postcount=10"), the problem was not the video card, but the capture card.

Since then, I tried both downgrading the version & kernel, as well as running the bleeding kernel from the ppa, but the panic still occurs.

So I'm resigned to the fact that I need to replace my capture card.

Despite going though [this thread]("http://ubuntuforums.org/showthread.php?t=566529"), I'm not sure which card would work with the current kernel.

I'd been using Hauppauge's 1187 WinTV-HVR-1250 Hybird PCI-E card for over a year, and never had any problems with it until recently.

I'm considering the [pcHDTV-5500]("http://www.pchdtv.com/hd_5500.html") since it was specifically designed for linux, unlike Hauppauge and these other cards, but it's almost five years old now, and I wonder if I'll have the same problems with the current kernel.
It would be more helpful if you told us where you are located and how you get your tv - cable, satellite, ota, analog/digital etc.

---

### Post by dpapathanasiou on 2012-09-09
I'm in the US and use Optimum Cable. There's no analog service anymore, so I need to be able to capture the digital signal.

While I found a relatively recent [review of the pcHDTV-5500]("http://ubuntuforums.org/showthread.php?t=1840947") and it was generally positive, it seems they wear down and become less reliable over time.

I'm also considering the [Hauppauge WinTV-HVR-2250]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2250"), since it seems fully supported now, but it is about three years old now, and I don't know if I would encounter the same kinds of problems with the current kernel that I have with the WinTV-HVR-1250.

Then again, I'm still baffled why the current kernel is giving me these panics; if it's related to the chipset Hauppauge uses, then perhaps I should avoid the WinTV-HVR-2250 as well.

---

### Post by nickrout on 2012-09-09
> **dpapathanasiou said:**
> I'm in the US and use Optimum Cable. There's no analog service anymore, so I need to be able to capture the digital signal.


Is your cable encrypted? have you thought about the (perhaps) need for a cablecard capable tuner?

---

### Post by dpapathanasiou on 2012-09-09
It's definitely not encrypted; I've had the same cable service since the switch to HD a few years ago, and I've always been able to record any channel w/o a problem.

It's just that when I set something to record now (since switching to 12.04), I can never be sure if the recording will complete properly, or result in a kernel panic.

Last night, for example, I recorded three hours in a row successfully, but then today, it gave me a panic 20 minutes into recording another program.

Above and beyond any hardware considerations, I'd really like to know what it is about the current kernal and my card's chipset or driver which is causing these panics.

---

### Post by nickrout on 2012-09-09
> **dpapathanasiou said:**
> It's definitely not encrypted; I've had the same cable service since the switch to HD a few years ago, and I've always been able to record any channel w/o a problem.

It's just that when I set something to record now (since switching to 12.04), I can never be sure if the recording will complete properly, or result in a kernel panic.

Last night, for example, I recorded three hours in a row successfully, but then today, it gave me a panic 20 minutes into recording another program.

Above and beyond any hardware considerations, I'd really like to know what it is about the current kernal and my card's chipset or driver which is causing these panics.

Well you don't need to worry about cablecard then.

I favour the hdhomerun tuners for my own use, they are great and very independent of kernel version as they are simply network connected devices.

This thread is not about your panics, but perhaps you could google the error messages you are getting, and/or go to the kernel mailing list?

Also as it seems to be interrupt related take a look to see it's not sharing an interrupt with another card.

---

### Post by dpapathanasiou on 2012-09-10
Nick, thanks for all the replies, especially regarding the HD Homerun tuner.

It's an interesting concept, and if I do have to replace my existing capture card, I think I'm going to try that.

As for the current problems, the panics leave no log information, and all I have to work with are the screen photos I take with my camera.

The capture card uses the only PCI-E slot on my motherboard, and while the bios seemed to assume that slot would be used for an alternative video card, I have replaced the default setting in that regard, but without success.

---

