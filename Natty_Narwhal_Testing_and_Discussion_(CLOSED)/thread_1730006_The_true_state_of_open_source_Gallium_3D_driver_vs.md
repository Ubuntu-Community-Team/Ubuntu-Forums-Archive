---
title: "The true state of open source Gallium 3D driver vs fglrx"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-04-15
It is interesting to check every now and then the true state of the Linux open source Gallium drivers (Mesa Gallium 3D) compared to the proprieatry ones (fglrx).

These tests are commonly run at Phoronics ([www.phoronics.com](www.phoronics.com)).
The latest test being from today, 15th April '11.
Here is the link to the article:
[http://www.phoronix.com/scan.php?page=article&item=amd_r600g_14apr&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r600g_14apr&num=1)

The main message was that even with ATI Radeon HD 4830, the fglrx was about 10 times faster than Gallium 3D.
For example in Nexuiz 2.5.2, Gallium would get 16 frames per second while fglrx could do 160 fps.
With ATI Radeon HD 5830 the difference was even greater.

---

### Post by thezood on 2011-04-15
This is probably true for 3D and other graphics-intense applications but when watching movies and only using web browsers and the UI, I much more prefer the open source driver. It feels faster and leaner and it's much simpler to configure (xorg.conf, begone). Catalyst may have more optimized code when using the GPU but I think it's inferior in every other way.

---

### Post by rapiertg on 2011-04-15
In my case it looks like this:

I got some cool game (like latelly on humble frozezbyte bundle) and have a bit time to play it - i install fglrx

when the game start to bore me or have litlle time to play - install open one.

I would stick to open driver if it only get opengl full 3.2 compablility and they were a bit faster, but it will need a bit more time I think...

---

### Post by Visceral Monkey on 2011-04-15
I loathe the open source drivers. I'm stuck with it right now because Gnome 3 doesn't work with the ATI ones. It's annoyed me enough that I've considered shelving linux until ATI and Gnome 3 work together without issue. There's nothing worse than having a high performance piece of hardware like a decent video card and having it lobotomized by navel gazing open source drivers. Ugh. 

The open source drivers are deficient in almost every way, I can't imagine a legitimate reason to use them unless ATI just stopped supporting their drivers completely. I'm not interested in open source politics personally, I just want the best performance.

---

### Post by thezood on 2011-04-15
> **Visceral Monkey said:**
> I loathe the open source drivers. I'm stuck with it right now because Gnome 3 doesn't work with the ATI ones. It's annoyed me enough that I've considered shelving linux until ATI and Gnome 3 work together without issue. There's nothing worse than having a high performance piece of hardware like a decent video card and having it lobotomized by navel gazing open source drivers. Ugh.

There is nothing like having a high performance piece of hardware and using it to write text documents. :D

---

### Post by Visceral Monkey on 2011-04-15
> **thezood said:**
> There is nothing like having a high performance piece of hardware and using it to write text documents. :D

I use my system for lots of things and I'd like my hardware support to be maximized. But to each their own.

---

### Post by beew on 2011-04-15
> **thezood said:**
> There is nothing like having a high performance piece of hardware and using it to write text documents. :D

Then don't buy high performance hardware.

I don't use ATI but I am with VM on this.

 I have a Nvidia card on my main machine and I wouldn't waste it on nouveau. I think nouveau is good in that if you boot Ubuntu off a live usb and it works out of the box. I use nouveau in my external drive installation of Ubuntu (i.e. just not installing any proprietary graphic driver) so I can use my external drive as a portable and boot it off any computer. But I wouldn't use nouveau for performance, and if I don't care about performance I would just get a machine with an Intel card. 

I think it is the same for ATI, if you plan on using the open source driver for ATI card you may as well not getting the ATI card in the first place, it will cost less.

---

### Post by yaji on 2011-04-15
> **Harry33 said:**
> 

The main message was that even with ATI Radeon HD 4830, the fglrx was about 10 times faster than Gallium 3D.
For example in Nexuiz 2.5.2, Gallium would get 16 frames per second while fglrx could do 160 fps.
With ATI Radeon HD 5830 the difference was even greater.

The picture quality is better on fglrx too. Look at this glorious 8x Edge Detect Antialiasing and 16x anisotropic filtering:

[[IMG]http://img858.imageshack.us/img858/493/zrzutekranuh.th.png[/IMG]](http://img858.imageshack.us/i/zrzutekranuh.png/)

Forget about seeing stuff like that with Gallium 3D.

---

### Post by seeker5528 on 2011-04-15
> **Visceral Monkey said:**
> I loathe the open source drivers. I'm stuck with it right now because Gnome 3 doesn't work with the ATI ones. It's annoyed me enough that I've considered shelving linux until ATI and Gnome 3 work together without issue.

If you have a game, CAD program, etc... where the difference in performance is actually noticeable to the average human, I could see ditching Gnome 3 so you can use the driver you need to get that performance.

Don't know why that would want to make you ditch Linux. 

It's not like the choice is any different than it has been in the past, just that you have Gnome Shell added into the mix instead of *just* having to worry about newer kernel/mesa/xorg.

On a side note, in Debian experimental the default r600 driver was switched back to the legacy driver, with a note in the changelogs indicating the gallium driver wasn't quite as ready as as the maintainers thought.

Later, Seeker

---

### Post by screaminj3sus on 2011-04-15
The OSS drivers are essentially useless on a laptop. The power management is still terrible to say the least. Even on low profile my laptop gets absurdly hot and battery life is terrible. And dynpm still flickers everytime the clocks change. 

fglrx ain't great either but it's gotten a lot better as of late. If we just had video acceleration they would actually be pretty decent. va-api doesn't work on my card as xvba is totally broken on uvd1 cards :(

---

### Post by rbrick49 on 2011-04-15
Using GLX_SGIX_pbuffer
3839 frames in 5.0 seconds = 767.800 FPS
3987 frames in 5.0 seconds = 797.400 FPS
4032 frames in 5.0 seconds = 806.400 FPS
4050 frames in 5.0 seconds = 810.000 FPS
4062 frames in 5.0 seconds = 812.400 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0"
      after 91639 requests (91639 known processed) with 0 events remaining.
with a 6950 card

---

### Post by pony-tail on 2011-04-15
Non issue for me ( Radeon 5770 ) open driver makes my screen flicker every 5 seconds or so - fglrx works without issue 
result = I am using fglrx 
I would prefer to use an open driver if it worked properly but on my hardware it does not .

---

