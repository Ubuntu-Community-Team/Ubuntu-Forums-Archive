---
title: "vdpau issues - Mythbuntu 10.10"
date: 2010-10-26
forum: Mythbuntu
---

### Post by lsheaves on 2010-10-26
Hi All...

First of all, I am a Newbie, so please be gentle.

I am running Mythbuntu 10.10, and have installed the NVIDIA drivers thru the restricted drivers control panel.

For the most part, the performance of the box is great, except that when watching a live 1080p HDTV stream on my 720p TV, I note that there is frame and audio loss.

Looking at the frontend logs, I see the following:

root@backend:/var/log/mythtv# more mythfrontend.log | grep VDPAU
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
2003-01-01 11:02:49.583 VDPAU Error: Error at mythrender_vdpau.cpp:1478 (#1, Unknown)
2003-01-01 11:02:49.583 VDPAU Error: Failed to create VDPAU device.
2003-01-01 11:02:49.583 VDPAU Error: No VDPAU device
2003-01-01 11:02:49.583 VDPAU: Failed to create dummy device.

in addition, I see the following:
root@backend:/var/log/mythtv# more mythfrontend.log | grep nvidia
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

The following packages are installed:
libvdpau1 0.4-5ubuntu1
   nvidia-173 173.14.28-0ubuntu1

I welcome any suggestions.

Thanks.

---

### Post by thatguruguy on 2010-10-26
> **lsheaves said:**
> Hi All...

First of all, I am a Newbie, so please be gentle.

I am running Mythbuntu 10.10, and have installed the NVIDIA drivers thru the restricted drivers control panel.

For the most part, the performance of the box is great, except that when watching a live 1080p HDTV stream on my 720p TV, I note that there is frame and audio loss.

Looking at the frontend logs, I see the following:

root@backend:/var/log/mythtv# more mythfrontend.log | grep VDPAU
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
2003-01-01 11:02:49.583 VDPAU Error: Error at mythrender_vdpau.cpp:1478 (#1, Unknown)
2003-01-01 11:02:49.583 VDPAU Error: Failed to create VDPAU device.
2003-01-01 11:02:49.583 VDPAU Error: No VDPAU device
2003-01-01 11:02:49.583 VDPAU: Failed to create dummy device.

in addition, I see the following:
root@backend:/var/log/mythtv# more mythfrontend.log | grep nvidia
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory

The following packages are installed:
libvdpau1 0.4-5ubuntu1
   nvidia-173 173.14.28-0ubuntu1

I welcome any suggestions.

Thanks.

It may be useful to know which nvidia card you have.

Also, why are you using nvidia-173, rather than nvidia-current?

---

### Post by lsheaves on 2010-10-26
My Xorg log file reports the following:

[411207.882] (II) NVIDIA(0): NVIDIA GPU Quadro FX 500/FX 600 (NV34GL) at PCI:1:0:0 (GPU-0)
[411207.882] (--) NVIDIA(0): Memory: 131072 kBytes
[411207.882] (--) NVIDIA(0): VideoBIOS: 04.34.20.18.13
[411207.882] (II) NVIDIA(0): Detected AGP rate: 8X
[411207.882] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[411207.882] (--) NVIDIA(0): Connected display device(s) on Quadro FX 500/FX 600 at
[411207.882] (--) NVIDIA(0):     PCI:1:0:0:
[411207.882] (--) NVIDIA(0):     SONY TV (DFP-0)
[411207.882] (--) NVIDIA(0): SONY TV (DFP-0): 135.0 MHz maximum pixel clock
[411207.882] (--) NVIDIA(0): SONY TV (DFP-0): Internal Dual Link TMDS
[411207.883] (II) NVIDIA(0): Assigned Display Device: DFP-0

As to why I am using the NVIDIA-173 drivers, this is the only option I was offered, possibly because of the age of the card?

Thanks

---

### Post by LowSky on 2010-10-26
your card doesnt seem to support vdpau
[http://us.download.nvidia.com/XFree86/Linux-x86/190.53/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/190.53/README/appendix-a.html)

---

### Post by nickrout on 2010-10-27
And the corollary is that you may need to set your video renderer to something that doesn't involve vdpau.

---

### Post by thatguruguy on 2010-10-27
> **nickrout said:**
> And the corollary is that you may need to set your video renderer to something that doesn't involve vdpau.


... or get a new video card.  You can find a card using the 8400GS chipset for between $20 and $50, and it will make a world of difference.

---

### Post by mymythtv on 2010-10-27
Not sure that's possible

>>>> [411207.882] (II) NVIDIA(0): Detected AGP rate: 8X

Seems to remember that VDPAU isn't supportet on AGP

---

### Post by thatguruguy on 2010-10-27
You're right about AGP.  However, [this card]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=4226576&CatId=1603") is available for $50, has the 8400 GS chipset, and will work in a regular PCI slot.

---

### Post by rhpot1991 on 2010-10-27
I wouldn't bother to sink any money into an AGP or PCI card anymore.  That $50 you are going to spend on a card is a good chunk of what an ION box costs, why not look at one of those and move your backend away from the tv?

---

