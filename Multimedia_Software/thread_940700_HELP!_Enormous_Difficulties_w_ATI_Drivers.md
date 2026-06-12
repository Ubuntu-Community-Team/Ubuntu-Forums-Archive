---
title: "HELP! Enormous Difficulties w/ ATI Drivers"
date: 2008-10-07
forum: Multimedia Software
---

### Post by Day Tripper on 2008-10-07
Hi all,

I'll start by saying: I'm relatively new to Ubuntu (installed about 4 days ago). So far, I'm very impressed.

However, I have been encountering enormous difficulty with my Hardware Drivers.

After checking "Enabled" next to "ATI accelerated graphics driver" as a restricted device (and subsequently rebooting my system), I encountered frequent lock-ups causing my computer to crash leaving only the option of a manual shutdown.

I have since uninstalled the drivers. Ubuntu runs just fine in 2D - However, I would quite like to enable Normal/Extra visual features (or even Compiz Fusion, which I've heard interesting things about).

Also, when attempting to watch a DVD, playback is incredibly choppy and slow (almost webcam like); I'm not sure whether or not that's related. - I'm using VLC.

Any information would be greatly appreciated.

In the simplest terms:
- I am using an ATI X1900 256mb Radeon Graphics Card.
- Upon installing restricted drivers, my system experienced frequent crashes.
- System runs fine without drivers; however, I would like to utilize the full 3D capacity of my graphics card (for obvious reasons).

Many thanks!!

---

### Post by stromdal on 2008-10-07
Did you try the instructions outlined on this ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) page?

Regards
/stromdal

---

### Post by Day Tripper on 2008-10-08
Did as the instructions suggested.

Unfortunately, it doesn't look as though I've made any progress.

Have I overlooked something?

Also, I've noticed that when I stick an external fan next to my computer - the freezing becomes much less frequent. I should note that this wasn't the case when I had Windows installed; so, I doubt it's the result of a hardware failure.

Perhaps my video card is overheating?

Is there a way to configure the 3D acceleration?

Thanks again!

---

### Post by markbuntu on 2008-10-09
Those instructions are incomplete. try these method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by Day Tripper on 2008-10-11
Nothing seems to work.

I'm currently not using any ATI drivers (my resolution is really stretched :() lest my computer freeze for the 1000000th time.

Is this issue likely to be resolved in 8.10?

..Any other suggestions?

---

### Post by donhilliard on 2008-10-14
I am having a similar issue with the VGA compatible controller, a ATI Mobility Radeon 9600 M10, on my laptop. system locks up right after I login. 

lspci -v gives me this info.

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] (prog-if 00 [VGA controller])
	Subsystem: Mitac Unknown device 8050
	Flags: bus master, 66MHz, medium devsel, latency 8, IRQ 10
	Memory at a8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at c100 [size=256]
	Memory at e0010000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at a0000000 [disabled] [size=128K]
	Capabilities: <access denied>

any suggestions please.

---

### Post by MaDxCrEaM on 2008-10-27
I'm also having the same issue. I have a X1950 256MB card. Locks up after installing ati drivers after a period of time. Seems to be just the graphics since my hard drive lights still blink every now and then. I've tried Intrepid 32bit, 64 bit, and now just tried 8.04 64 bit release and all do the same thing. I had ubuntu installed a while back with no problems, now I wanted to run it again and running into these problems.

Anyone have any clues what it is? The ati drivers themselves? Thanks for any help.

---

