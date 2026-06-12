---
title: "VDPAU Permissions"
date: 2015-11-30
forum: Multimedia Software
---

### Post by bmlong137 on 2015-11-30
I have an odd issue.  Right now, I have to run my video application (mythfrontend) as root and that is obviously not desirable. :-(

I am unable to get vdpau/vaapi working as a non-root user.  The non-root user is already in the "video" group.  /dev/dri/card0 is 770 root:video.  When I try to use VDPAU in VLC or mythfrontend, I get an indefinite black screen without sound.

vdpauinfo and vainfo both return a few lines, but stop and never finish the output.  Both work fine when run as root.

There are no errors or warnings in stdout, mythfrontend.log, VLC, or dmesg.  Any hints?  To my, it has something to do with permissions given it works as root...

I am using 15.10 with an AMD device (using amdgpu).  When I was using fglrx, VDPAU worked fine as a non-root user.

Thanks,
Brian

---

