---
title: "[SOLVED] Can't enable w32codecs"
date: 2007-10-23
forum: Mythbuntu
---

### Post by Meph1st0 on 2007-10-23
I can't seem to enable w32codecs under the proprietary codecs tab of MCC.  I was able to enable libdvdcss2 and ffmpeg but when I select w32codecs and click apply it starts trying (it looks like it's trying to download 3 files) and then MCC just closes and I'm back to mythtv frontend.  Am I doing something wrong?

---

### Post by mskradri on 2007-10-23
I was having similar problems with installing the proprietary codecs. After quitting out of the mythtv frontend, I tried installing via the Synaptic Package Manager. It gave me a message asking me to place the Mythbuntu 7.10 LiveCD back into the cd drive. After doing this, the install completed successfully. Looks like somthing about the Mythbuntu install keeps pointing to library files stored on the disk instead of getting the file online.

---

### Post by tgm4883 on 2007-10-23
> **mskradri said:**
> I was having similar problems with installing the proprietary codecs. After quitting out of the mythtv frontend, I tried installing via the Synaptic Package Manager. It gave me a message asking me to place the Mythbuntu 7.10 LiveCD back into the cd drive. After doing this, the install completed successfully. Looks like somthing about the Mythbuntu install keeps pointing to library files stored on the disk instead of getting the file online.

Thats a feature (although I don't like it) of Ubuntu.  

My second question would be is this a 64-bit system?  If it is, you need w64codecs

---

### Post by Meph1st0 on 2007-10-23
No, it's a 32 bit system.  In fact w64codecs is greyed out for me so I can't even select it.  Not that I'd want to, since it's a 32 bit system. :)

---

### Post by Meph1st0 on 2007-10-23
mskradri,

looks like that worked.  I just reinserted my 7.10 disk and went back into MCC and selected w32codecs and it install straight away.  Thanks for your help.

---

### Post by superm1 on 2007-10-23
Can one of you guys file a bug regarding this, about how it needs the CD, but doesn't ask for it?

Thanks :)

---

### Post by Meph1st0 on 2007-10-24
Uh...I'd love to submit a bug.  I'd then feel like I'm contributing to the project instead of mooching off it.  But I don't know where to go to submit it.  :)

---

### Post by superm1 on 2007-10-24
[https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/156471](https://bugs.launchpad.net/ubuntu/+source/mythbuntu-control-centre/+bug/156471)

If anyone can post a more complete backtrace, that would be most useful.

---

### Post by Meph1st0 on 2007-10-24
Nevermind.  I just registered on Launchpad.net/~mythbuntu  but it looks like I need to be approved by someone before I can submit a bug.

---

### Post by Meph1st0 on 2007-10-24
Nevermind again.  Looks like it's already there.

---

### Post by superm1 on 2007-10-24
Yeah you can file a bug against 

```
http://bugs.launchpad.net/mythbuntu
```

in the future.  You don't need to be part of ~mythbuntu to do so.

---

