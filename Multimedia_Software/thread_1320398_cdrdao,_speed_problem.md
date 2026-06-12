---
title: "cdrdao, speed problem"
date: 2009-11-09
forum: Multimedia Software
---

### Post by WDYSUN on 2009-11-09
Hello Dears

I am an audiophile so when I have to backup a cd-audio for car listening I take a lot of care to make the best copy I can. EAC is the only thing I miss in Linux, but I usually use copied cd only to bring them in my car where the hifi system is not perfect.

My car CD doesn't like CD written at high speed. On my old PC I had Debian and I could use cdrdao writing at speed 2X with this command

```

cdrdao write --device 1,0,0 --driver generic-mmc --speed 2 --eject album.toc

```

On my current laptop (DELL Latitude D520) with Ubuntu 9.04 I have the following device:

```

pietro@dell-laptop:~$ cdrecord -scanbus
scsibus1:
	1,0,0	100) 'TSSTcorp' 'DVD+-RW TS-L632H' 'DW10' Removable CD-ROM
	1,1,0	101) *
	1,2,0	102) *
	1,3,0	103) *
	1,4,0	104) *
	1,5,0	105) *
	1,6,0	106) *
	1,7,0	107) *

```


but running the command above I am not able to write at speed lower than 10X. 

Could anybody help me with this? There is anything I should do to force cdrdao to write at lower speed?

Best Wishes
Pietro

---

