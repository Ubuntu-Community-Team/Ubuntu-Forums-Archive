---
title: "I can't compile the alsa driver"
date: 2009-01-01
forum: Multimedia Software
---

### Post by 602254985 on 2009-01-01
make -C /lib/modules/2.6.28-byjohnny/source SUBDIRS=/home/johnnys/1  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/home/johnnys/linux-2.6.28'
  CC [M]  /home/johnnys/1/drivers/pcsp/pcsp.o
In file included from /home/johnnys/1/drivers/pcsp/pcsp.c:2:
/home/johnnys/1/drivers/pcsp/../../alsa-kernel/drivers/pcsp/pcsp.c: In function 'snd_card_pcsp_probe':
/home/johnnys/1/drivers/pcsp/../../alsa-kernel/drivers/pcsp/pcsp.c:99: error: 'HRTIMER_CB_IRQSAFE' undeclared (first use in this function)
/home/johnnys/1/drivers/pcsp/../../alsa-kernel/drivers/pcsp/pcsp.c:99: error: (Each undeclared identifier is reported only once
/home/johnnys/1/drivers/pcsp/../../alsa-kernel/drivers/pcsp/pcsp.c:99: error: for each function it appears in.)
make[4]: *** [/home/johnnys/1/drivers/pcsp/pcsp.o] Error 1
make[3]: *** [/home/johnnys/1/drivers/pcsp] Error 2
make[2]: *** [/home/johnnys/1/drivers] Error 2
make[1]: *** [_module_/home/johnnys/1] Error 2
make[1]: Leaving directory `/home/johnnys/linux-2.6.28'
make: *** [compile] Error 2


someone tell me why???:(
I have tried to fix this problem for 2 weeks:(

---

### Post by 602254985 on 2009-01-01
I have fix up the problem just now
but,the audio didn't working:(

lsmod | grep snd
snd_page_alloc         11024  0

---

### Post by R@iner on 2009-01-04
> **602254985 said:**
> I have fix up the problem just now
but,the audio didn't working:(

lsmod | grep snd
snd_page_alloc         11024  0
Hi, 

i use the same kernel 2.6.28 and i have the same problem to compile the
new alsa 1.0.18a driver. What was your solution to fix this problem?

Bye
Rainer

---

