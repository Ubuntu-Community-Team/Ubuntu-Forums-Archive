---
title: "DVICO Fusion HDTV5 - no DVB"
date: 2008-05-15
forum: Mythbuntu
---

### Post by rreis on 2008-05-15
I am getting the following error in dmesg after I attempt to scan QAM 256 channels.  I was working fine in 7.10, but after I upgraded to 8.04 I have not been able to tune any QAM channels

[  477.509789] lgdt330x: lgdt3303_read_status: Modulation set to unsupported value
[  477.510517] lgdt330x: lgdt3303_read_snr: Modulation set to unsupported value
[  477.511350] lgdt330x: lgdt3303_read_snr: Modulation set to unsupported value

Any ideas?

Rich

---

### Post by rreis on 2008-06-24
Does anyone have any idea about this error with this card?  Was it a poor choice to expect to work on linux?

---

### Post by toddk111 on 2008-07-04
> **rreis said:**
> Does anyone have any idea about this error with this card?  Was it a poor choice to expect to work on linux?

You were able to get it to work in 7.10?  I've been trying to get it work in 7.10 and 8.04 but my QAM recordings end up having a lot of errors.  I know my signal is good because in Windows, the Fusion application records QAM without errors/glitches in the files. Did you do anything special to get it to tune error free QAM in v. 7.10?

I'll have to look at my notes and let you know how I got it to work in 8.04...with glitches/errors in the recorded files.  Maybe we can figure this out.

---

