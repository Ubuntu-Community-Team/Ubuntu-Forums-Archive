---
title: "Bootcamped Linux partition boots to grub after crash, how to retrieve old files?"
date: 2016-08-10
forum: Mac OSX
---

### Post by tdreid on 2016-08-10
Hi, roughly a year ago, my ubuntu partition on my mac notebook crashed and from then on, it has booted to grub. I did not need to access the data on it until now. I have tried the basic guides on how to boot from grub and I've mostly given up (unless you can provide a solution!). I don't necessarily need this partition and I can just make a new one. However, it does have valuable coding programs I would like to use as reference or for studying for the future (much of it provided by my professors in school and it's incredible code). I am mostly out of answers here so I come to you guys. I'm not exactly adept in this area either, so if you can please be a bit more explanatory when helping I'd appreciate it immensely. For the record, when I ls in grub it reads:```
(hd0) (hd1) (hd1, gpt3) (hd1, gpt2) (hd1, gpt1) error: failure reading sector 0x0 from 'hd0'. 
```

---

### Post by oldfred on 2016-08-10
Moved to Apple sub-forum where those who know Mac may be able to help.

From Ubuntu live installer you may be able to mount Linux partition or do repairs.
And the Summary Report from Boot-Repair often can help.
Or rEFInd can often boot, if you cannot boot at all.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

 [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) 
      [http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

