---
title: "TV 50/50 chance of it working &quot;Error was encountered while displaying video&quot;, logs up"
date: 2009-06-22
forum: Mythbuntu
---

### Post by GCFreak on 2009-06-22
Hi,

I finally upgraded my Mythbuntu media centre to 9.04, and I'm loving it so far. Just got everything configured, and I installed the Avenard repository to provide the fixes for New Zealand's Freeview|HD service to work properly and provide VDPAU for my NVIDIA graphics chipset. I never tried TV extensively without the Avenard stuff installed so I don't know if that had the same problem.

Anyway, my problem. When I start TV, there's a 50% chance that it gives off a "Error was encountered while displaying video" error, and sometimes it just works properly. And whenever I change channel, it always comes up with that error. I'm really at a loss as to why this is happening. I've provided my logs for you guys to see, don't be fooled by the hardware, all the HD channels on my service (480i, 720p and 1080i all H.264, even with deinterlacing!) work absolutely no issues at all, full speed, no skipping, dropping, corruption or slowing down. Thanks for any help you guys can give me.

[http://mythbuntu.pastebin.com/ff20e881](http://mythbuntu.pastebin.com/ff20e881) - I just started up MythTV, put on some child education on channel 6, waiting for it to screws up because sometimes it does do it after a while of watching, I got fed up of waiting so I changed channel to 3 (which had Infomercials on) and it reproduced the error. I then got out of MythTV, collected the logs and uploaded it.

EDIT: Just to say this happens with other decoders as well, not just with VDPAU.

EDIT2: I've reinstalled Mythbuntu 9.04, redid everything, and it's doing exactly the same thing. It does it when I turn on TV, it does it when changing channels and after running TV for a while it does it as well.

---

### Post by Scunizi on 2009-06-22
I don't know mythTV but it sounds like a video card driver problem.  Nvidia's site shows that their latest driver ([http://www.nvidia.com/object/linux_display_ia32_185.18.14.html](http://www.nvidia.com/object/linux_display_ia32_185.18.14.html)) has fixed the following concerning VDPAU.. So bottom line you might need to deactivate the Ubuntu supplied driver and then uninstall it.  After that you'll need to install the one from nvidia.  See my attachment for the instructions.  I do this all the time.  Keep in mind that with a kernel upgrade you'll need to reinstall the driver.  Always check for the latest and download it prior to restarting after a kernel upgrade.  That will save you the headache of figuring out links or elinks (cli web browsers) and wget (a web based download utility) at a terminal prompt.

[quote]
# Fixed VDPAU to eliminate some cases of corruption when decoding H.264 video containing field-coded reference frames on G84, G86, G92, G94, G96, or GT200 GPUs. Such streams are commonly found in DVB broadcasts.
# Slightly improved the performance of the VDPAU noise reduction algorithm.
# Enhanced VDPAU to validate whether overlay usage is supported by the current hardware configuration, and to automatically fall back to the blit-based presentation queue if required.
# Fixed error checking in VdpVideoMixerRender, to reject calls that specify more layers than the VdpMixer was created with.
# Modified VDPAU's VDPAU_DEBUG code to emit a complete backtrace on all platforms, not just on 32-bit Linux.
# Improved interaction between VDPAU and PowerMizer; appropriate performance levels should now be chosen for video playback of all standard resolutions on all supported GPUs.
# Fixed a bug in VDPAU that sometimes caused "display preemption" when the VdpDecoderCreate function failed.
# Fixed a potential segfault in the VDPAU trace library, triggered by a multi-threaded application creating a new VdpDevice in one thread, at the same time that another thread detected "display preemption".
[quote]

---

### Post by GCFreak on 2009-06-24
I've reinstalled Mythbuntu 9.04, redid everything, and it's doing exactly the same thing. It does it when I turn on TV, it does it when changing channels and after running TV for a while it does it as well.

Scunizi: the Avenard repository's MythTV packages are built only for the 180 series NVIDIA drivers, so I can't try the newer drivers

---

