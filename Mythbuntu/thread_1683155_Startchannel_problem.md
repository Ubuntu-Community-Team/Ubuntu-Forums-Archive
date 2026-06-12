---
title: "Startchannel problem"
date: 2011-02-07
forum: Mythbuntu
---

### Post by Nikas on 2011-02-07
Hello.

I cant watch live tv right now. Start channel is set to 22.
Channel 22 does only transmit in the evening here in sweden. I can't change channel.. it tries to start channel 22 but i get a message about error in the ...program jump file? Direct translated from swedish. ;)

How can i set the start channel? I want the start channel permanent! I know i can select one in mythtv-setup but start channel changes automatically when watching live tv..too bad when the channel stops transmitting...

So, do i have to wait for the channel to start transmitting again before i can watch live tv? ;)

---

### Post by dibuntux on 2011-02-08
It is a problem. The start channel, as far as I get it, is the last succesfully tuned in channel.

It happens that if I tune in a encrypted channel that Myth cannot display and it crash (yes, it does so also on 0.24 latest PPA) that will be the latest channel in Myth on that tuner.

Sometimes you can get away with changing channel as soon as you get in Watch Tv, sometimes you have to manually change it from the mythtv setup.

Hope it helps.

Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by klc5555 on 2011-02-08
Rather than go into the backend setup, you can manually schedule a brief (1 min.) recording on a "good" channel. Scheduled backend recordings don't crash changing from a "bad" channel to a "good" one the way livetv does.

If channel 22 in Sweden goes off the air at a regular time every day, such a small recording could be set up to be done on a "good" channel daily, after 22 is off the air. Storage rules for the recording could be set to "keep 1; delete oldest". Then, "starting channel" for livetv will be ready to go on the "good" channel when necessary.

A silly workaround, to be sure. But livetv is something of an afterthought in the mythtv world. First and foremost it's a DVR.

---

### Post by nickrout on 2011-02-08
> **dibuntux said:**
> It is a problem. The start channel, as far as I get it, is the last succesfully tuned in channel.

It happens that if I tune in a encrypted channel that Myth cannot display and it crash (yes, it does so also on 0.24 latest PPA) that will be the latest channel in Myth on that tuner.


who on earth do you have encrypted channels in your setup?

---

