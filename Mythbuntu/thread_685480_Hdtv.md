---
title: "Hdtv"
date: 2008-02-02
forum: Mythbuntu
---

### Post by jolx on 2008-02-02
im thinking i might build me a htpc. What sort of processing power will i need to be watching something in 1920x1080p and at the same time record something the same resolution if my tv tuner didnt have hardware encoding or decoding?

---

### Post by newlinux on 2008-02-02
Well, for digital signals, hardware encoding doesn't exist, and all the HD out there is digital so you need not concern yourself with that. Recording digital signals takes very little CPU because all they do is capture the signal which is already in mpeg2 transport stream format, so no encoding involved. Decoding of HDTV will be handled by your CPU and video card.

To be safe and without XvMC, any dual core CPU will do (stick with a nvidia GPU). I can do 720p with a Pentium 4 2.6Ghz. But my systems connected to my HDTVs are x2 3800 and x2 4200. You can get away with less processing power, but with the prices of entry level dual cores, I'd go with that.

---

### Post by williammanda on 2008-02-02
One other thing to think about is the HTPC going to be used for media only. I use my systems as desktops as well as media. So you might need more horse power so that the recordings are not distorted while using the backend for other uses.
Thanks

---

### Post by newlinux on 2008-02-02
> **williammanda said:**
> One other thing to think about is the HTPC going to be used for media only. I use my systems as desktops as well as media. So you might need more horse power so that the recordings are not distorted while using the backend for other uses.
Thanksc

Recording and streaming from backends don't take many CPU cycles. I do this while using my backend as desktops and other as other servers.. However, this brings up a good point about other backend processes. If you are going to do a lot of transcoding and commercial flagging on your backend while using it for other things or using it as a frontend watching HDTV at the same time you may want a little more horsepower. If you are going to do a lot of transcoding in general you might want more than an entry level dual core, especially if you are transcoding HD to h.264.

---

### Post by jolx on 2008-02-02
im thinking of a pentium dual core e2160 but im not sure if i should use the gigabyte GA-73PVM-S2H with its onboard GF7100 or buy the GA-945GCM-S2L and get a good graphics card

---

