---
title: "HD DVD Cannot Be Mounted Except Readable By Root"
date: 2008-06-24
forum: Multimedia Software
---

### Post by H4rm0ny on 2008-06-24
I have just bought a LG HD-Blueray combi drive and it works. I have replaced Kubuntu's default UDF.ko module with a patched version. Success - I can now see the contents of a HD disc that I insert. It mounts by default to /media/cdrom1. Well that's all fine but I can't read from it except as root.

I may have made a stupid mistake so don't be shy of pointing out the obvious. I can: su root on the command line and enter the directory that way, run konqueror as root (!) and enter the mounted directory happily. I have tried to chmod the permissions as generously as they can be for the mounted directory. Nothing allows a non-root user to access that directory which I need to do.

Any help is much appreciated.

Many thanks,

Harmony.

**EDIT:** The device is /dev/scd0 and I am running Hardy Heron on an AMD64 box. Anything else that's relevant, let me know.

**EDIT EDIT:** Something else I tried is just ripping an entire DVD using dd into a file which I then [successfully] mounted as a file system. Again - root only.

---

