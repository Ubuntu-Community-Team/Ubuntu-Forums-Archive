---
title: "Help, can't watch live tv or scan channels"
date: 2010-07-24
forum: Mythbuntu
---

### Post by tghlk on 2010-07-24
I've got a pretty simple setup so I hope someone can help me. I've searched and read help files, but still cannot figure this out. I'm running the current version .23

AMD 3000 system with a single PVR-150 card connected to Time Warner cable service. I got everything setup as I think it should be and setup my schedulesdirect account too. What confounds me is that I had this halfway working in an older version. 

If I want to watch live TV, it says 'please wait' and then eventually times out. If I try to scan for channels, it seems to find some, but there's no data and I get a message that says 'no new channels found'

mythfilldatabase runs fine and completes without errors. 

what am I missing here? I've checked and rechecked backend settings. How can I test the capture card now without tv input?

---

### Post by klc5555 on 2010-07-26
> **tghlk said:**
> I've got a pretty simple setup so I hope someone can help me. I've searched and read help files, but still cannot figure this out. I'm running the current version .23

AMD 3000 system with a single PVR-150 card connected to Time Warner cable service. I got everything setup as I think it should be and setup my schedulesdirect account too. What confounds me is that I had this halfway working in an older version. 

If I want to watch live TV, it says 'please wait' and then eventually times out. If I try to scan for channels, it seems to find some, but there's no data and I get a message that says 'no new channels found'

mythfilldatabase runs fine and completes without errors. 

what am I missing here? I've checked and rechecked backend settings. How can I test the capture card now without tv input?

There are a couple of things that immediately come to mind.

1) In the backend setup, you should have the PVR 150 set up as a "MPEG-2 Encoder". If you have it set up as a V4l analog encoder, it won't work.

2) Does Time Warner cable transmit any analog signals any more in your area? By now they may have converted everything over to standard digital (plus low-level encryption on everything except the locals), requiring the intermediation of some sort of digital transport adapter (or set top box) provided by the company for their analog-only customers to receive anything, certainly above channel 13 and possibly below it as well.

Otherwise you'll have to check the backend log to see what's going wrong when the backend tries to initialize the pvr-150.

---

