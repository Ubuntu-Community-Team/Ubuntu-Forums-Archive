---
title: "Why I'm Glad I Back-up mythconverg"
date: 2016-05-11
forum: Mythbuntu
---

### Post by bilkay on 2016-05-11
The other night, my computer running the mythtv backend froze in the middle of recording a program. The syslog entries looked like this:

```
May  9 20:36:58 Jupiter kernel: [55592.840358] Event timed out
May  9 20:36:58 Jupiter kernel: [55592.840369] saa7164_api_i2c_read() error, ret(2) = 0x32
May  9 20:36:58 Jupiter kernel: [55592.840376] i2c_read_bytes: i2c_read_bytes(): i2c transfer failed
May  9 20:36:58 Jupiter kernel: [55592.840381] silabs_tercab_poll_response: silabs_tercab_poll_response() ERROR reading byte 0!
May  9 20:36:58 Jupiter kernel: [55592.840387] silabs_tercab_get_signal: [7-0060] Si2177_L1_TUNER_STATUS() failed (err=7)
May  9 20:36:58 Jupiter kernel: [55593.443718] Event timed out
May  9 20:36:58 Jupiter kernel: [55593.443727] saa7164_api_i2c_write() error, ret(1) = 0x32
May  9 20:36:58 Jupiter kernel: [55593.443733] i2c_write_bytes: i2c_write_bytes(): i2c transfer failed
May  9 20:36:58 Jupiter kernel: [55593.443738] silabs_tercab_get_signal: [8-0060] Si2177_L1_TUNER_STATUS() failed (err=3)
May  9 20:37:08 Jupiter kernel: [55602.866419] Event timed out
May  9 20:37:08 Jupiter kernel: [55602.866430] saa7164_api_i2c_read() error, ret(1) = 0x32
May  9 20:37:08 Jupiter kernel: [55602.866438] lgdt3306a_read_reg(): error (addr 59 reg 0080 error (ret == -5)
May  9 20:37:08 Jupiter kernel: [55603.469826] Event timed out
May  9 20:37:08 Jupiter kernel: [55603.469835] saa7164_api_i2c_read() error, ret(1) = 0x32
May  9 20:37:08 Jupiter kernel: [55603.469841] lgdt3306a_read_reg(): error (addr 0e reg 0080 error (ret == -5)
May  9 20:37:18 Jupiter kernel: [55612.892505] Event timed out
May  9 20:37:18 Jupiter kernel: [55612.892516] saa7164_api_i2c_read() error, ret(1) = 0x32
May  9 20:37:18 Jupiter kernel: [55612.892523] lgdt3306a_read_reg(): error (addr 59 reg 0080 error (ret == -5)
May  9 20:37:18 Jupiter kernel: [55613.495888] Event timed out
May  9 20:37:18 Jupiter kernel: [55613.495898] saa7164_api_i2c_read() error, ret(1) = 0x32
May  9 20:37:18 Jupiter kernel: [55613.495905] lgdt3306a_read_reg(): error (addr 0e reg 0080 error (ret == -5)
May  9 20:37:28 Jupiter kernel: [55622.918603] Event timed out
May  9 20:37:28 Jupiter kernel: [55622.918613] saa7164_api_i2c_read() error, ret(1) = 0x32
May  9 20:37:28 Jupiter kernel: [55622.918619] lgdt3306a_read_reg(): error (addr 59 reg 0080 error (ret == -5)
May  9 20:37:28 Jupiter kernel: [55623.522000] Event timed out
May  9 20:37:28 Jupiter kernel: [55623.522008] saa7164_api_i2c_read() error, ret(1) = 0x32
May  9 20:37:28 Jupiter kernel: [55623.522015] lgdt3306a_read_reg(): error (addr 0e reg 0080 error (ret == -5)
May  9 20:37:38 Jupiter kernel: [55632.944705] Event timed out
May  9 20:37:38 Jupiter kernel: [55632.944716] saa7164_api_i2c_read() error, ret(1) = 0x32
May  9 20:37:38 Jupiter kernel: [55632.944723] lgdt3306a_read_reg(): error (addr 59 reg 0080 error (ret == -5)
May  9 20:37:39 Jupiter kernel: [55633.548086] Event timed out
May  9 20:37:39 Jupiter kernel: [55633.548095] saa7164_api_i2c_read() error, ret(1) = 0x32
May  9 20:37:39 Jupiter kernel: [55633.548102] lgdt3306a_read_reg(): error (addr 0e reg 0080 error (ret == -5)
May  9 20:37:48 Jupiter kernel: [55642.970798] Event timed out
May  9 20:37:48 Jupiter kernel: [55642.970809] saa7164_api_i2c_read() error, ret(1) = 0x32
May  9 20:37:48 Jupiter kernel: [55642.970816] lgdt3306a_read_reg(): error (addr 59 reg 0080 error (ret == -5)
...

Repeated continuously until I did a power-down/up restart

```

My backup script, which I run daily, reported that the mythconverg database had "crashed". The data in mythtv was completely screwed up. Fortunately, I had a backup from the previous day and was able restore with only one lost day.

I certainly hope this isn't going to be a recurring event.

Mythbuntu 14.04.4
3.16.0 kernel

---

