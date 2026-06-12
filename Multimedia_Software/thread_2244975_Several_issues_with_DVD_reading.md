---
title: "Several issues with DVD reading"
date: 2014-09-20
forum: Multimedia Software
---

### Post by ciryon03 on 2014-09-20
Hello to all 

I have several issues with DVD reading on my ubuntu based desktop.

I precise that the DVD tested is correct quality and does read without problems on my standard dvd player on my TV.

the first issue is when I inser the DVD in my DVD drive on the PC, the 1st time, Ubuntu ask me what to do (the default configuration) but if I open and close again the DVD drive, Ubntu stop asking me what to do, I have looked at the setting and saw nothing wrong.

Default player : the default player does not let me the entire DVD, somehow, it skips some episodes. Some bonus are read pixelised (lot of little squares appears in the image). sometimes the default player freeze.*

VLC : I've downloaded VLC and tried it, VLC perform better but sometimes the reading is abruply stopped at a pârticulat point of the DVD and always the same. If I close and reopen VLC again, the problem disappears.

If I try to make VLC the default player for reading video DVD in the system setting, the system setting keeps staying on the ubuntu default player when I relaunch it, if instead I put the reading video DVD setting on "ask me what to do", this setting stay.

Finally I've tried using Smplayer but he does not read my DVD. 

Anyone could help me fixing these ? i'ts not a big issue, I still can read DVD on my TV but sometimes I'd like to make all the thing on my computer and this little dvd issues are anoying as 

Thanks a lot


config :
Ubuntu 14.04 64 bits
8 GB RAM
Nvidia GT740 with 340.32 nvidia driver

---

### Post by Vladlenin5000 on 2014-09-21
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ciryon03 on 2014-09-22
> **Vladlenin5000 said:**
> [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I installed the restricted format package but that has uninstalled something previously installed, it was too quick I did not saw what.

Concerning libdvdread4, I had already installed it but do it again.

I inserted a DVD and VLC launched automatically although is is totem configurated by default. I closed VLC.

I've installed regionset and launched it with sudo and got the following message
```
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
```

So the DVD is read but regionset does not find it.

I typed that : 
sudo regionset /dev/sr0

and thit time it worked and I could see the good region was already selected (2).
```

Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 3
drive plays discs from region(s): 2, mask=0xFD

```

About enabling DMA (to fix the choppiness), I've looked at that page : [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA), type the command mount | egrep 'udf|iso966 and obtained that
```

/dev/sr0 on /media/yann/HEROCORP_S2_DVD3 type udf (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,uhelper=udisks2)

```


Tis is nor scd0 nor hdc so I don't know how to check if dma is activated.

---

