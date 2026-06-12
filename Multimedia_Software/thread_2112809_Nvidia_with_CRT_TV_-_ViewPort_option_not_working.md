---
title: "Nvidia with CRT TV - ViewPort option not working?"
date: 2013-02-05
forum: Multimedia Software
---

### Post by violagirl23 on 2013-02-05
I have a Toshiba CRT TV that I hook up to my laptop via an S-video card to watch TV shows. I always needed to set the Overscan option in the TV section of Nvidia-settings to 82, since the TV itself doesn't have an option to disable overscan within its own hardware settings, and now that the option's gone in the newest driver, I found out I have to use the ViewPort option. I know I have an overscan of about 5% on all sides (which I determined by setting this as my background picture: [http://www.desktopwallpaperhd.net/wallpapers/6/e/computer-calibration-background-photo-kenmasters-realise-overscan-64398.jpg](http://www.desktopwallpaperhd.net/wallpapers/6/e/computer-calibration-background-photo-kenmasters-realise-overscan-64398.jpg)), and I'm trying to correct it with the ViewPortOut option, but the thing is, the command simply isn't working. Before I delve into the issue, here are some basic specs on my machine and setup:

I'm using Ubuntu 12.10 32bit with the nvidia-current driver, and my graphics card is a Quadro NVS 140M, which is inside my 2008 Thinkpad R61. My TV has a resolution of 1024x768, and my laptop has a resolution of 1680x1050. According to xrandr, my TV display is TV-0, and my laptop screen is DFP-0.

Here are the specifics for my video card, via lspci:
01:00.0 VGA compatible controller: NVIDIA Corporation G86 [Quadro NVS 140M] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Lenovo ThinkPad T61
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at d4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 2000 [size=128]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current, nouveau, nvidiafb


Here is the basic command I tried running from the terminal:
```
nvidia-settings -a CurrentMetaMode="DFP-0: 1680x1050, TV-0: 1024x768+1680+0 {ViewPortOut=964x708+30+30}"
```
The problem is that the command doesn't change the display on my TV screen one ioda. After issuing the command, both my screens black out for an instant and come back on, but the display on the TV doesn't change in the least, and the overscan stays the same. I also tried adding **ViewPortIn=1024x768** to the command to see if that would change anything, but it didn't. Tweaking the settings (increasing the pixel border) also does absolutely nothing. I'm completely torn on what to do. Is there a reason the command might not be not working? I think I have the formatting correct because I AM able to change the TV if I do this wacky command:
```
nvidia-settings -a CurrentMetaMode="DFP-0: 1680x1050, TV-0: 1024x768+1680+0 {ViewPortOut=512x384+10+10}"
```
The picture on the TV then changes so that only the upperleft corner has a picture (at a low resolution) with huge amounts of black on the bottom and right. Other than this extreme command, nothing else really seems to affect the TV screen at all.

Is there anything I can do to get this command to work for me, and if not, is there any way to keep 12.10 but downgrade to the old Nvidia driver that allowed Overscan within the menu? I tried downgrading my Nvidia driver manually by downloading it from the Nvidia website, but it effed up my whole display and I had to boot into recovery just to uninstall it and restore the nvidia-current driver.

---

### Post by BicyclerBoy on 2013-02-05
I pinned my HTPC nvidia driver to 295 to avoid this.
nVidia-settings is planned to have a new GUI overscan control at some point.

There is a suggestion that ViewPortIn is required in some cases. Maybe it is because you are using twinview.
Twinview is a probably sub-optimal for the combo of DFP & CRT TV via s-video.

This is a working overscan cmd for one monitor:
```

nvidia-settings --assign CurrentMetaMode="DFP-1: 1920x1080 { ViewPortOut=1880x1040+20+20, ViewPortIn=1920x1080 }"
```

I'll let you do the mental gymnastics required to work out nvidia's cmd line for twinview meta-mode..

---

