---
title: "Input/output error with growisofs"
date: 2010-03-09
forum: Multimedia Software
---

### Post by danger pigeon on 2010-03-09
I use the growisofs command from the terminal to do most of my burning. Mostly because i burn almost the exact same type of file every time so its pretty easy to set up. I've done this dozens of times and never once had a problem before. I loved it because it was so much simpler than doing this in windows where i would need to install a few extra programs and codecs. That was up until today where it started failing every single time i tried to burn something. For some reason every time i try to burn a disc it gives me this error message:
```
shawn@shawn-tower:/media/mybook/x360$ burn360 /dev/scd0=fifa10.iso
Executing 'builtin_dd if=fifa10.iso of=/dev/scd0 obs=32k seek=0'
:-? L0 Data Zone Capacity is set already
/dev/scd0: "Current Write Speed" is 2.0x1352KBps.
:-[ WRITE@LBA=0h failed with SK=3h/WRITE ERROR]: Input/output error
:-( write failed: Input/output error
shawn@shawn-tower:/media/mybook/x360$
```I'm really at a loss as to why this is happening. Every thread i found that discussed this problem was mostly focused on k3b or brasero and never really answered the question. As far as i know nothing has been updated since the last time i burned a disc a few days ago. Everything is exactly the same as it was when it worked. The only thing i could think of that might have caused this sudden failure is that i flashed the firmware of another cd drive using the same sata port that this drive is currently plugged into, but that was in windows so i dont see how it could have affected this drive. Any help would be appreciated.

---

### Post by no2498 on 2010-03-10
if i think right you need a iso file so more computers can read the disk now days
i may be wrong on all counts  times are changing fast now days

---

