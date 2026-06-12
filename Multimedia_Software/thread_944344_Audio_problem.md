---
title: "Audio problem"
date: 2008-10-11
forum: Multimedia Software
---

### Post by claudiofax on 2008-10-11
Hello,

I am new ubuntu user from Italy. I ma facing problems with the audio configuration. 
The sound card is correctly seen by the system but i can ear only sound test (without possibility to stop it). 

I tried with the following

ubuntu@ubuntu:~$ asoundconf list
Names of available sound cards:
AudioPCI
UART
ubuntu@ubuntu:~$ asoundconf set-default-card AudioPCI

but no result...

the sound  card is:

lspci -v
...
00:0a.0 Multimedia audio controller: Ensoniq ES1370 [AudioPCI] (rev 01)
	Subsystem: Unknown device 4942:4c4c
	Flags: bus master, slow devsel, latency 32, IRQ 20
	I/O ports at d800 [size=64]


Please help me !!

thanks
claudio

---

