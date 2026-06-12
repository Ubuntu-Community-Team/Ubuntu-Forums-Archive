---
title: "ivtv install problems"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by whein on 2006-07-31
First off, I'm a relative newbie, so sorry if this should be an obvious fix.  I'm trying to install the ivtv drivers so I can use MythTV and my new Hauppauge PVR-350 card.  I've looked at a bunch of different how-to and walkthroughs and they all seem to hang at the same point.  I get to the following output:
```
root@HappyDrive1:/usr/src/ivtv-0.4.6/utils# depmod
root@HappyDrive1:/usr/src/ivtv-0.4.6/utils# modprobe ivtv
FATAL: Error inserting ivtv (/lib/modules/2.6.15-23-amd64-generic/ivtv/ivtv.ko): Unknown symbol in module, or unknown parameter (see dmesg)
root@HappyDrive1:/usr/src/ivtv-0.4.6/utils# dmesg
<snip>
[38925.760748] ivtv: no version for "struct_module" found: kernel tainted.
[38925.761096] ivtv: Unknown symbol dma_ops
<snip>
[118708.525216] ivtv: Unknown symbol dma_ops
root@HappyDrive1:/usr/src/ivtv-0.4.6/utils#

```
I *think* I have all the packages installed I'm supposed to, but I'm not sure what I really need or which versions.  The install I have is the 2.6.15-23-amd64-generic kernel and I've tried to get all the source and header files I've installed to match that.  However, I have a K8 board so I'd love to switch to that and maybe a more recent kernel at the same time.  I'm still in the learning phase so I figured I'd take baby steps first.

To complicate things that much more, I have no internet connection to the machine that I'm installing on, so I've been downloading files from work to a USB drive and setting them up in a local repository.  Anyone know what to do to fix the ivtv problems?  Is it safe to jump to a newer kernel and a K8 kernel and install all these drivers in one she-bang?  Thanks in advance for any help!
-Will

---

### Post by whein on 2006-08-07
Well, still haven't figured out what the problem was, but I installed a newer kernel (2.6.15-26-amd64-k8 ) and all the files that go with it and the drivers installed on that with only minor hiccups.  I'm now able to watch TV through mplayer and plan on taking the plunge to MythTv soon (though on a different box...  go fig).
-Will

---

