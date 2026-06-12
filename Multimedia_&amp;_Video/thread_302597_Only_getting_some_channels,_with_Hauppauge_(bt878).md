---
title: "Only getting some channels, with Hauppauge (bt878)"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by electronikjunkie on 2006-11-18
hello,

Ive been trying to capture TV with a Hauppauge WinTV bt878 card. I have Charter cable. I can get channels 60-74, but thats it. All the other channels are blue in tvtime and blue with static in mythtv. Im running ubuntu 6.10. Here is some info:

```
thomaskessler@dvr-server:~$ dmesg | grep bttv
[   54.399790] bttv: driver version 0.9.16 loaded
[   54.399794] bttv: using 10 buffers with 2080k (520 pages) each for capture
[   55.967786] bttv: Bt8xx card found (0).
[   55.967818] bttv0: Bt878 (rev 17) at 0000:00:0e.0, irq: 217, latency: 64, mmio: 0xebe00000
[   55.967831] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   55.967833] bttv0: using: Hauppauge (bt878) [card=10,insmod option]
[   55.967862] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   55.970364] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   56.059526] bttv0: Hauppauge eeprom indicates model#44811
[   56.059528] bttv0: using tuner=39
[   56.059662] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   56.061797] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   56.063952] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   56.134534] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   56.221932] bttv0: registered device video0
[   56.221946] bttv0: registered device vbi0
[   56.221962] bttv0: registered device radio0
[   56.221983] bttv0: PLL: 28636363 => 35468950 .. ok
[   80.481928] bttv0: PLL can sleep, using XTAL (28636363).
```

If anyone could help me out that would be great. The drivers seem to load I dont know what the problem is.

---

### Post by erik_boi on 2006-11-18
You might change to US-CABLE-HRC (I think it is) in the mythtv settings, this may solve the problem. Certain companies (I know comcast does) use different frequencies for their brodcasts.

---

### Post by electronikjunkie on 2006-11-19
holy cow theres a lot of post on this forum. i just posted last night and my post is on the 4th page with 1 reply. crazy amounts of people must be using this os. im a linux guy turn bsd and back to linux for better support on a dvr system, but i still like bsd better. just wish there was more support. anyway i tried the cable-hrc and irc, but it did not work. here is the process i go through.

-stop mythtv-backend
-run mythtv-setup
-start from scratch delete all video cards and inputs
-change general to cable or cable-hrc at the time
-setup my cards, inputs, and scan channels from zap2it.com
-quit
-run /etc/cron.daily/mythtv-backend
-run mythfilldatabase
-run mythtv-frontend
-drink beer

no luck... any suggestions...

---

