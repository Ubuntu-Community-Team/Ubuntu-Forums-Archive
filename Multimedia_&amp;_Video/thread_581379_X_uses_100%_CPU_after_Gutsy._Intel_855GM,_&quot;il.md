---
title: "X uses 100% CPU after Gutsy. Intel 855GM, &quot;illegal extended x86 opcode&quot;"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by gspr on 2007-10-19
Hi.

After upgrading to Gutsy on my laptop, where an Intel 855GM (Xorg module i810, kernel module i915), handles the graphics, X tends to lock up every hour or so. By SSH'ing in from another machine, I find that X is using 99% of the CPU. The only suspicious event in the Xorg log is:
```
f000:5503: 01 ILLEGAL EXTENDED X86 OPCODE!
```

No special software tends to be running when this happen - the computer may well be idle.

Any ideas, anyone?

---

### Post by gspr on 2007-10-19
It seems to be related to a known bug [1] in X. I have applied the patch [2] referred to in the launchpad entry, and no crashes so far. I'll report back on this.

[1] [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/146643](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/146643)
[2] [http://launchpadlibrarian.net/9834085/int10_edi_fix.patch](http://launchpadlibrarian.net/9834085/int10_edi_fix.patch)

---

### Post by gspr on 2007-10-21
Never mind - crash continues. I'll report a bug on Launchpad.

---

### Post by gspr on 2007-10-25
Switching to the new "intel" drivers seems to work around the problem.

---

