---
title: "VIA VN800 - Openchrome - 6.06 - kernel 2.6.15-25-386"
date: 2006-06-30
forum: Multimedia &amp; Video
---

### Post by acojlo on 2006-06-30
Does anyone have binaries for the situation described in the title?

---

### Post by ahaslam on 2006-06-30
[QUOTE=acojlo]Does anyone have binaries for the situation described in the title?[/QUOTE]
The only Dapper binaries that I've noticed can be found here:
[[installation] General 6.06 - VIA Unichrome S3 display driver]("http://ubuntuforums.org/showthread.php?t=184512")
It also goes through the installation steps.

Let us know how you get on,

Tony.

---

### Post by acojlo on 2006-06-30
Thank you, Tony.

Although I use x.x.x-25 I also have x.x.x-23 kernel. I used binaries from the refferenced thread. I checked xorg.conf, copied *.ko drivers in drm folder, done depmod -ea, installed some xorg-via-drivers package, but overall result is very nice wall of ubuntu logo on the screen - no go to login. Switching to text console and undoing changes was a solution.

It was same under both kernel versions.

---

### Post by acojlo on 2006-06-30
A breaktrough has occured :)

What I did? I installed just the package (no *.ko) from referenced thread and put the "via" instead "vesa" in the xorg.conf. I realy can't measure how it is faster now, but I have feeling of everything going smoothly.

I will try adding additional parameters in the xorg.conf, but I feel no success about DRI without compiling by myself.

---

### Post by ahaslam on 2006-06-30
[QUOTE=acojlo]A breaktrough has occured :)

What I did? I installed just the package (no *.ko) from referenced thread and put the "via" instead "vesa" in the xorg.conf. I realy can't measure how it is faster now, but I have feeling of everything going smoothly.

I will try adding additional parameters in the xorg.conf, but I feel no success about DRI without compiling by myself.[/QUOTE]
Just out of curiosity, did the 'via' x.org driver in Ubuntu not work for you?
I only ask as the x.org via driver worked out of the box for me. I've added two options to the device section of my xorg.conf: "DisableIRQ" & "EnableAGPDMA". I don't know if the options have much impact, but DRI is on and I'm getting 421 fps in glxgears (on a 2 year old laptop).

Tony.

---

### Post by acojlo on 2006-07-01
No Tony, standard x.org driver do not work for me. I also added those two option and now it is working. If someone else is doing this just be carefull if you change Identifier "Generic Video Card" to something like "VIA Unichrome Pro" in xorg.conf . You have this two times in xorg.conf. Change it two times.

DRI is not working for me. Right now I use standard *.ko (after changes I execute sudo depmod -ae). BTW, I noted the binary *.ko from pirast (user on this forum) are for 686 architecture, but my is 386, as uname -r states:'2.6.15-25-386'


This is interpretation of my X.org logs:

after going through 
	information	drmOpenDevice: node name is /dev/dri/card251
	information	drmOpenDevice: open result is -1, (No such device)
	information	drmOpenDevice: open result is -1, (No such device)

from card42 to card254 I get:

	information	VIA(0): [drm] drmOpen failed
	error	VIA(0): [dri] DRIScreenInit failed.  Disabling DRI.
	information	VIA(0): - Visuals set up
	information	VIA(0): VIAInternalScreenInit
	information	VIA(0): - B & W
	information	VIA(0): Using 2304 lines for offscreen memory.
	information	VIA(0): Using XFree86 Acceleration Architecture (XAA)

System Log states:
fsap-laptop	kernel	[17179615.008000] [drm] Initialized drm 1.0.1 20051102

I guess I must compile. Shall I do it?

---

### Post by acojlo on 2006-07-02
No need to compile. The *.ko files at [http://gamesplace.info/opensource/openchrome/dapper-binaries/](http://gamesplace.info/opensource/openchrome/dapper-binaries/) were for 686 kernel. But, kernel installed by default was for 386. So, I only needed to upgrade my kernel to 686. Now DRM is working, still complaining about small memory allocated to video, but working.

If anyone want to upgrade kernel I will not post direct instruction, because of different types of kernels for different type of cpu's (amd, intel, older, newer), but here you are the link: [http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917) . It is very simple.

---

### Post by acojlo on 2006-07-03
Another problem:

System log:

[17179611.780000] [drm:via_mem_alloc] *ERROR* Attempt to allocate from uninitialized memory manager.

Official openchrome mailing list states on this: This is known bug, upgrade to new version.

---

