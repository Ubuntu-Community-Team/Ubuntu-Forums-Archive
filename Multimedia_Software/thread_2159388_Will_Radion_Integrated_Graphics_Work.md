---
title: "Will Radion Integrated Graphics Work?"
date: 2013-07-02
forum: Multimedia Software
---

### Post by GUZZLR on 2013-07-02
Hello All,
I see a lot of post with NVIDEA graphics questions, but not too many about Radeon.  The reason I ask, is I'm gearing up to build a computer and it will have integrated Radeon with FM2 socket.  I have had success (finally) getting Nvidea to work, but am wondering if ATI Graphics Cards will work better, or have all the difficulties which I encountered, while getting Nvidea to work.
Also, at some point, I will probably go with a discrete graphics card, but for now, just the integrated.

Thoughts?
Thanks for the help

Ubuntu 13.04 on an external drive
Windows 7 internal

---

### Post by cub on 2013-07-03
There are proprietary drivers available for ATI cards. I use it on my laptop. It's not excellent when connecting two monitors and I have to launch the Amd control center everytime I boot. But otherwise it works.

---

### Post by Mark Phelps on 2013-07-03
The problem is the FM2 is not an ATI video card; instead, it's an integrated solution.  I went to the AMD driver website and could find no mention of any Linux drivers for the FM series.  So, without that, you'll be limited to the default open-source Radeon drivers, which might not work with the integrated chipset.

---

### Post by GUZZLR on 2013-07-03
```
[COLOR=#000000]you'll be limited to the default open-source Radeon drivers, which might not work with the integrated chipset.[/COLOR]
```
So, If I go with a Nvidia discrete card, then theoretically, it should work as there are Linux drivers for that?  One thing nice about the aftermarket MoBo's is they allow for just the discrete card by itself. Although, it seems a waste to not utilize the onboard graphics... 
Thoughts?
Thanks for the help

---

### Post by Yellow Pasque on 2013-07-04
> **Mark Phelps said:**
> So, without that, you'll be limited to the default open-source Radeon drivers, which might not work with the integrated chipset.
Incorrect. fglrx/Catalyst supports the FM2 APU's.

> The problem is the FM2 is not an ATI video card; instead, it's an integrated solution.
It's a RadeonHD integrated into the CPU, so it is an AMD/ATI GPU.

> I went to the AMD driver website and could find no mention of any Linux drivers for the FM series 
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
Select APU, Desktop APU, A-Series, Linux, and it will bring you to Catalyst download page.

---

### Post by smuggly on 2013-07-04
Phoronix Has A Review of the new richland 6800K with the new Beta Driver.. Google Came up with it. I'm searching for it also & came to this post.

---

### Post by exploder on 2013-07-04
Just putting in my two cents here for what it's worth. I have an HP DV6 laptop that has an AMD A6 Vision Quad Core processor. I am running Ubuntu 12.04 x64 on it, not because of the graphics but because the Ralink WiFi works better with it than anything else I have tried. I was originally running 12.04 with the 3.4 kernel and the proprietary driver. A kernel update trashed the driver and I was stuck with Unity 2D. I reinstalled 12.04 and stayed with the latest 3.2 kernel and the open source driver and everything is working just fine now.

As I understand things, currently the open source driver has better 2D support and alright 3D support. The proprietary driver has slightly better 3D support and alright 2D support. By staying with the open source driver Plymouth displays well and the laptop throttles down to 800 MHz so it stays reasonably cool. This is just my experience with this and I am sure my description is not the best. I have tried quite a few different distros with this hardware but currently 12.04 with the 3.2 kernel and the open source drivers works better than anything else. Also, Unity uses Compiz for compositing and I do not get any artifacts or screen flicker, mutter and muffin gave me problems with occasional screen flickering and artifacts.

At any rate I hope this is of some help to you and I would be interested in how things work out for you.

---

### Post by GUZZLR on 2013-07-04
I'm still curious about cramming an Nvidia card in there and in BIOS disabling the integrated to see what happens...

---

### Post by Mark Phelps on 2013-07-04
> **Temüjin said:**
> Incorrect. fglrx/Catalyst supports the FM2 APU's.


It's a RadeonHD integrated into the CPU, so it is an AMD/ATI GPU.

 
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
Select APU, Desktop APU, A-Series, Linux, and it will bring you to Catalyst download page.

My bad ... I didn't know the FM2 was an "a-series" FPU.

---

### Post by GUZZLR on 2013-07-04
```
open source drivers works better than anything else
```
You lost me on this one...you mean the open source drivers recommended in software update when you reload Ubuntu?  it sounds as if the integrated Radeon graphics is working for you; if so, are the colors on your screen "bright" or dull as if the grphics are not working.  The reason I ask, is I am in the process of builiding a PC, with one drive to house Windows, and another drive to house Linux. I am currently on an HP laptop with a small Nvidea card, and it's actually working nicely. So, I'm concerned that with the new build, windows will certainly work fine with the integrated graphics, which are actually not too bad, but will Linux on the other drive work?  I don't seem to see any drivers for a Linux/ATI system, but there are plenty of drivers for Linux /Nvidia system.  Which is why I'm thinking I can forget about the integrated Radeon, and just go with an Nvidea discrete card...This is new for me as well.
I do see the latest Linux Beta drivers on the AMD website, and this driver seems to support the integrated graphics (HD 7000 series) which is on the Motherboard.
Thanks

---

