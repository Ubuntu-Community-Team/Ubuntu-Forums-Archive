---
title: "Brasero no longer writing to media"
date: 2009-07-03
forum: Multimedia Software
---

### Post by gunterb on 2009-07-03
Brasero worked fine for several weeks, copying CD's, DVD's, writing ISO's. The drive is still reading media just fine, but when Brasero goes into the Image Burning Setup, it opens this setup twice or more often. When selecting Burn, it says: "Error while burning. the drive is busy". (it makes no difference whether I close the excess Image Burning Setup windows).
Here are the last few lines of the session log:
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO
BraseroWodim stdout: Drive buf size : 1310720 = 1280 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stdout: Encoding speed : 309x (23173 sectors/s) for libedc from Heiko Ei
Session error : The drive is busy (brasero_burn_record burn.c:2599)

Are there any clever people around who can help me fix this one? I already removed and re-installed Brasero, no difference.

---

