---
title: "Using 3 different sterio outputs to create 5.1 audio. is this possable?"
date: 2019-01-22
forum: Multimedia Software
---

### Post by Rushlight on 2019-01-22
so, I understand the basis of 5.1; you have 2 stereo speakers as front side and back side, then a center main and a sub. that totals 6 lines.
my question is is there an application I could use to make 3 stereo outputs appear as a single 5.1 digital output to the OS and other applications? 

additionally, if so, would it be possible to do on an ARM varient of Ubuntu (say for an Odroid or raspberry pi)?

---

### Post by TheFu on 2019-01-22
You'd get better/more useful help on the forums for the specific hardware you plan to use.

I've seen GPIO audio "hats" to provide HQ audio to r-pi devices.  I don't have one.

There are also USB audio devices. I haven't looked for ARM drivers, so be certain there are stable drivers for both the hardware and OS variant if you go this route.  For example, some Pine64Pro devices run media applications under android, not straight Linux, so you'd need android drivers.

There's also HDMI which support 5.1 audio.  Get a device that takes the hdmi audio and splits off to standard audio channels.  I have one of these boxes from J-tech.  It outputs digital over yellow cable, digital over Toslink/optical and stereo over a 3.5mm plug. Think it was $26 on amazon - yep. They sell a 4K video version. It requires power. The good news about this is that it doesn't care what feeds the HDMI input.

---

