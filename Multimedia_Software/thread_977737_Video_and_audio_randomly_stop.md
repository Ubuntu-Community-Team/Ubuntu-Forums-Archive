---
title: "Video and audio randomly stop"
date: 2008-11-10
forum: Multimedia Software
---

### Post by braneed on 2008-11-10
I am running Kubuntu 8.04 and when i use mplayer, xine, amarok (with xine engine), minirok or rhythmbox for audio-video playback the playback will stop and act paused. 
Most times, im mplayer, if i pause/unpause or take it from fullscreen back to fullscreen it will start again, but will then pause again at a random moment. 

I have tested this with at least 20 different forms of digital video (both divx/qt and DVD) and all types of digital music format. I am currently using PulseAudio.

Does anyone have any idea what would make this happen? i have checked to make sure i have nothing else running, ie artsd or gstreamer, and i have a fairly decent system. 

This never happened until i upgraded to 8.10, then had to do a full reinstall of 8.04. I did not install 8.04 back on top of 8.10, i backed up /home and a few custom edited files in /etc


Thank you

Just for giggles, the stats of my system are as follows:

cpu:
    Intel(R) Pentium(R) 4 CPU 2.80GHz, 2795 MHz
    Intel(R) Pentium(R) 4 CPU 2.80GHz, 2795 MHz
graphics card:
    nVidia GeForce FX 5700LE
sound:
    FIRST INTERNATIONAL 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller
network:
  eth1      FIRST INTERNATIONAL RTL-8139/8139C/8139C+
  eth0      Netgear FA310TX
01: None 00.0: 10103 CPU
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 15.2.9 "Intel(R) Pentium(R) 4 CPU 2.80GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,pebs,bts,cid,xtpr
  Clock: 2795 MHz
  BogoMips: 5595.15
  Cache: 512 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

02: None 01.0: 10103 CPU
  Hardware Class: cpu
  Arch: Intel
  Vendor: "GenuineIntel"
  Model: 15.2.9 "Intel(R) Pentium(R) 4 CPU 2.80GHz"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,dts,acpi,mmx,fxsr,sse,sse2,ss,ht,tm,pbe,pebs,bts,cid,xtpr
  Clock: 2795 MHz
  BogoMips: 5590.85
  Cache: 512 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

01: None 00.0: 10102 Main Memory
  Hardware Class: memory
  Model: "Main Memory"
  Memory Range: 0x00000000-0xbe303fff (rw)
  Memory Size: 3 GB
  Config Status: cfg=new, avail=yes, need=no, active=unknown

---

