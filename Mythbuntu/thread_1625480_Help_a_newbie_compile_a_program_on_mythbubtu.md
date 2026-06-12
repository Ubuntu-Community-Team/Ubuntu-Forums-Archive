---
title: "Help a newbie compile a program on mythbubtu"
date: 2010-11-19
forum: Mythbuntu
---

### Post by fatbrunty on 2010-11-19
Hi, All usual apologies for being a newbie. I have a technotrend c2300 premium DVB-C card that I'm trying to get to work on mythbuntu. The problem is the vendor/subsys number it is reporting (in lspci) is corrupt. I did some research and found this thread: [http://www.freak-search.com/de/thread/330772/linux-dvb_diseqc_and_tt_3200-s2](http://www.freak-search.com/de/thread/330772/linux-dvb_diseqc_and_tt_3200-s2) and downloaded a program I'm hoping to use to correct eeprom but I can't understand the compile instructions:
 
Compilation:
------------
Mercurial(HG) driver:
- install driver for kernel 2.6.x
- cd .../v4l
- copy this file to the v4l directory
- edit Makefile:
add 'obj-m += fix_eeprom.o' at the end of the file
- make

 
 
Can someone point me to a FAQ or give me a clue where to start? 
 
Thanks,
 
IAn.

---

### Post by azmyth on 2010-11-19
You have to download the v4l drivers and then copy the fix eeprom file in the link on the page in your message to the v4l directory. Then edit the make file in the v4l directory with the changes in the instructions then enter make. Looks like the file reprograms you're eeprom so you may want to be careful.

---

### Post by fatbrunty on 2010-11-25
HAha this'll make you laugh. So, v4l is short for 'video for linux', realising this was the turning point because I had thought that it read v41 like 'version 41'. I squarely blame Micros**t as wordpad uses the same char for a one and for a lowercase L, although it serves me right for being lazy and using windoze.

Anyhow, the following got the program compiled and run, the vi .config is needed to turn off firedtv which doesn't make successfully.

[FONT=Courier New]34  apt-get install mercurial
   35  cd /usr/src
   36  ls
   37  hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
   39  cd v4*
   75  cd v4l
   76  vi .config
   77  cd ..

   79  make
   81  cd v4l
   88  cp /home/myth/Downloads/fix_eeprom.c .
   90  make
   93  insmod saa7146.ko
   94  lspci -v
      insmod fix_eeprom.ko old=0x32c2a9ff new=0x13c20002
      cd /lib/firmware
      cp /home/myth/Downloads/dvb-ttpci-01.fw-2622 dvb-ttpci-01.fw
      reboot


Cheers,

IAn.
[/FONT]

---

