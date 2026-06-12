---
title: "Burning CD and mp3 Tracks"
date: 2023-12-16
forum: Multimedia Software
---

### Post by Quarkrad on 2023-12-16
I have a number of small audio tracks I have been asked to burn to a CD.  At the far end we are not sure whether the CD will be listened on a standard CD player or something more modern (mp3).  So, I though I would burn both formats to a CD.  I can play the first two tracks on a standard CD player but not the rest - at this point I'm not sure if it was the burning process or my methodology.  Here is what I did:

[LIST]
[*]Obtained source files as wav (8 of them)
[*]Checked wav file were 16 bit and 44100Hz 
[*]Converted wav files to mp3
[*]Burnt all 16 files to a CD using K3B and choosing New Data Project as the method to create CD
[/LIST]


Is there a better method of burning such a mixed CD (CD containing mp3 files that could be played in car/modern mp3 player and standard audio tracks that can be played on a standard CD player)?

---

### Post by TheFu on 2023-12-16
CDs are either audio or data. Not mixed.  Create 2 discs.  One in CD audio format and the other in data format with an ISO9660 format.

[https://en.wikipedia.org/wiki/Mixed_Mode_CD](https://en.wikipedia.org/wiki/Mixed_Mode_CD) says that I'm wrong. It is possible to have mixed mode CDs. It is part of the specification.  So, the question becomes, does your burning software support mixed mode?  [https://www.unixguide.net/linux/lnag/lnag7.7.shtml](https://www.unixguide.net/linux/lnag/lnag7.7.shtml) Section 7.7.5 has instructions for mounting. reading, writing and authoring mixed mode CDs.  Looks like you have to author the Data and Audio sides separately, then burn them to the disk in a single session.

---

