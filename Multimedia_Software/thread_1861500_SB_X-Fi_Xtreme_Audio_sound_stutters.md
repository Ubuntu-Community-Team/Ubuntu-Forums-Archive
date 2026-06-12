---
title: "SB X-Fi Xtreme Audio sound stutters"
date: 2011-10-15
forum: Multimedia Software
---

### Post by leonardteo on 2011-10-15
Hi all,

I just installed Ubuntu 11.10 and everything seems to check out. The only problem I'm having is that whenever I play any sound back, the sound stutters. I have a XB X-Fi Xtreme Audio PCI-E card and Ubuntu detects it just fine. I'm running Ubuntu 11.0 64-bit. Can anyone assist?

Thanks,

Leonard

---

### Post by larrypg on 2011-10-15
same problem here - have not found a workaround yet

---

### Post by EllieDragonfly on 2011-10-16
The same for me, the sound stutters, and my mic doesn't work either. Do you think that installing ubuntu again would help?

---

### Post by terryfield on 2011-10-16
I'm having the same problem. My sound card worked before upgrading to 11.10. I'm also running the x64 version.

---

### Post by super1285 on 2011-10-16
Same here, 64 bit 11.10, used to have sound before upgrade, now nothing.

---

### Post by way3000 on 2011-10-18
Same problem here, anyone knows what driver it uses in 10.04 natty?

If we can force it to use that driver it would be ace.

---

### Post by leonardteo on 2011-10-18
Is this a known issue that is being worked on? Where/how do we submit a bug or search for issues?

Leo

---

### Post by larrypg on 2011-10-22
Hello all,

I was wondering if anyone came up with a solution or have updates helped?  I am back to 11.04 until I know if things have been fixed.

---

### Post by petr.vi on 2011-10-25
I have the same problem, 64 bit 11.10

---

### Post by brian-w on 2011-10-26
If it helps, there is a bug report listed  ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/877509](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/877509)) with a temporary workaround using ubuntu-bugs (run from the terminal), which seems to do the trick until the next boot

Hopefully the boffins will issue a fix in due course, but in the meantime, for me at least, the workaround provides a working soundcard.

(64 bit 11:10 - SB X-Fi Xtreme Audio [CA0110-IBG])

Brian

---

### Post by terryfield on 2011-11-01
I ran "alsamixer", changed the volume of the PCM output, and now the stutter is gone. Probably alsamixer rewrote some settings. I also don't see my card in the hardware tab of the Sound application.

---

