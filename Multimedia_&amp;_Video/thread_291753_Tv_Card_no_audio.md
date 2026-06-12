---
title: "Tv Card no audio"
date: 2006-11-02
forum: Multimedia &amp; Video
---

### Post by IndigoMontoya on 2006-11-02
I did a fresh install of edgy and can not get audio from my Hauppage TV card anymore.   It was working in dapper.  I believe (but may be wrong) that I had to change some configuration option to get it working previously, but I don't remember what (or een if I actually did this).  The audio out on the card is still connected to the audio in on the sound card and all my other audio is working.  Any thoughts?

lspci |grep bttv
```

bttv                  176116  1 
video_buf              27652  1 bttv
ir_common              28548  1 bttv
compat_ioctl32          2432  1 bttv
i2c_algo_bit           10376  1 bttv
v4l2_common            17280  3 tuner,msp3400,bttv
btcx_risc               6280  1 bttv
tveeprom               16144  1 bttv
i2c_core               23424  9 i2c_ec,i2c_viapro,tuner,tvaudio,nvidia,msp3400,bttv,i2c_algo_bit,tveeprom
videodev               10752  3 spca5xx,bttv

```

---

### Post by IndigoMontoya on 2006-11-09
Can anyone help?

---

