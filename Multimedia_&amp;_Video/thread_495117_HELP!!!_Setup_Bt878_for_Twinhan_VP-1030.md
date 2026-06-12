---
title: "HELP!!! Setup Bt878 for Twinhan VP-1030"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by jeanluc on 2007-07-07
Hi all!
I have a DVB-S Twinhan VP-1030... It works fine under Windows, and now I'm trying to have it working under Ubuntu 7.04... unfortunately without success.

The card is recognized:
$ lspci | grep Bt878
07:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
07:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

Modules are loaded:
$ lsmod | grep bttv
bttv                  173684  1 bt878
video_buf              26116  1 bttv
ir_common              31236  1 bttv
compat_ioctl32          2304  1 bttv
i2c_algo_bit            8712  1 bttv
btcx_risc               5896  1 bttv
tveeprom               15888  1 bttv
videodev               28160  1 bttv
v4l2_common            25216  3 tuner,bttv,videodev
i2c_core               22656  7 i2c_ec,nvidia,tuner,bttv,i2c_algo_bit,tveeprom,i2c_viapro 


**but I don't have any node in /dev!**:(

I have tried to follow the instructions I found on other threads, but seems that nothing can halp me to solve my problem.

Any suggestion will be very appreciated.
Thank you to everyone.

---

