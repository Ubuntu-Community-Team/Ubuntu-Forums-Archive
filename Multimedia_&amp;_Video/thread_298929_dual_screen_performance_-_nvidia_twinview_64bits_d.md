---
title: "dual screen performance - nvidia twinview 64bits dapper"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by woorzel on 2006-11-13
Hi all,

I'm curious how to benchmark my video performance..
I was previously running gentoo 32bit with the same (roughly) kind of desktop (twinview) and I find my performance to be a bit lacking in ubuntu now.
I did change a few things, as I installed ubuntu dapper 64 bit when I replaced my CPU, mobo and graphic card so obviously this is not the same hardware but it should only perform better I guess..

I have a fairly decent config, an athon 64 3500 with 1G of DDR400 memory (dual channel), and I use a PCIe nvidia 7300GS card. Now I know this is a budget card but I would expect it to cope great with desktop stuff (I don't do much games). back when I was running gentoo I had a much older but slightly higher range AGP nvidia card and it ran really smooth.
I guess I must also say that I run a 2560x1024x24b desktop = same as before.

Things run ok = I do get 3D acceleration from the binary nvidia driver but many things still peg my CPU. I recently tried Compiz 64bit (still using it now) and find it really cool, but moving around a window with the wobbly effect results in nearly 100% CPU usage. same for the GL xscreensavers (even without Xgl) - they run ok, slightly slow and use nearly 100% CPU.
As it is everything is very useable but I can notice the slowness at times, and it just doesn't feel right that moving a window uses up all my cpu.. (probably helps that the CPU is relatively fast).

So I guess what I'm asking here is wether there is a good way to really benchmark my system and figure out if I have a problem. Compiz runs fine but I've seen demos at conferences where a cheap laptop outperformed my box easily... is it because of the dual screen output? cheap graphic card? 64 bit drivers?

I'm not a complete newbie at this but any advice would be much appreciated :)

---

### Post by lonce on 2006-11-13
One quick way that I use is the glxgears command.  If you open a terminal and type glxgears -printfps it will open a window with some gears running.  Every 5 seconds it will display the frames per second.

There are other more detailed ways, but I use that for quick dirty numbers.

---

### Post by earobinson on 2006-11-13
glxgears is a good program to benchmark with

---

### Post by woorzel on 2006-11-13
I get about 1440 FPS from glxgears (with 100 CPU, as with every 3D thing I try..)
how does that sound? even tho 1440 FPS sounds ok it does not feel really smooth while it's running (I'm in Xgl/Compiz now)
thanks for the feedback.

---

### Post by earobinson on 2006-11-13
what dosent feel smooth? xglxgears or Xgl/Compiz (xglxgears never seems to be smooth but the higher the frame count the better)

Also you can maximise xglxgears and then look at its output for better stats

---

### Post by woorzel on 2006-11-13
well pretty much anything with 3D doesn't feel really smooth. it works, sure, but it pegs the CPU and feels a bit sluggish.
If I maximise the glxgears (well, on one of my two screens) then it REALLY slows down, to like 200=400 FPS or so (at least that's what it says, because it really feels more like 3FPS from what I can see).

this is not really a question about compiz which I'm using now, it's about 3D in general with twinview/64bit dapper as I had the same feeling before using compiz.
the xscreensavers for example, I'm using those nice caleidoscopes (two of them, since I have 2 screens) and they run ok but slow down frequently, and use 100% CPU. I don't think they're supposed to do that....

---

### Post by earobinson on 2006-11-13
hum ya something does feel wrong, it also seems to me that glxgears would only test 2d and not 3d preformance. Ill look into this a bit more and post if I find anything out

---

### Post by woorzel on 2006-11-13
thanks, your help is much appreciated :)

---

