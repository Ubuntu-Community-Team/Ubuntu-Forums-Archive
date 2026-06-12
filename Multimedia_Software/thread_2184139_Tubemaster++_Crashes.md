---
title: "Tubemaster++ Crashes"
date: 2013-10-27
forum: Multimedia Software
---

### Post by registration-y on 2013-10-27
I'm having quite a time trying to get this to work. the program comes up but immediately crashes. Any ideas?

david@david-laptop:~/Downloads/TubeMaster++$ ulimit -c unlimited
david@david-laptop:~/Downloads/TubeMaster++$ sudo java -jar tm++.jar
TubeMaster++ detected operating system : Linux
*TubeMaster++ Core Started*
-= TubeMaster++ Started on null =-
-= TubeMaster++ Started on null =-
-= TubeMaster++ Started on Linux netfilter log (NFLOG) interface =-
-= TubeMaster++ Started on Pseudo-device that captures on all interfaces =-
-= TubeMaster++ Started on null =-
-= TubeMaster++ Stopped on Linux netfilter log (NFLOG) interface (Rcv=0|Drp=0)=-
* Conversion Thread Running*
#
#[B] A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x8b110132, pid=16920, tid=2336303936
#
# JRE version: Java(TM) SE Runtime Environment (7.0_45-b18) (build 1.7.0_45-b18)
# Java VM: Java HotSpot(TM) Server VM (24.45-b08 mixed mode linux-x86 )
# Problematic frame:
# C  [libpcap.so.0.8+0xc132]  pcap_stats+0x12
#
# Core dump written. Default location: /home/david/Downloads/TubeMaster++/core or core.16920
[/B]
Full error report log [B][http://pastebin.com/gNYkYhDB](http://pastebin.com/gNYkYhDB)

[/B]

---

### Post by xX0v0Xx on 2013-11-24
I am sufffering the same problem... and I am trying to solve it. 
Did you solve it already ?

---

