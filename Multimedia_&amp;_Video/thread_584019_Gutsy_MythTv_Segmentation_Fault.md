---
title: "Gutsy: MythTv Segmentation Fault"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by mikaelFF on 2007-10-20
I upgraded to Gutsy today and everything went smoothly until I tried to start MythTV. It complained about not being able to access the backend. I tried to start the backend and got a segmentation fault. I got no logs, nothing.

I removed all the mythtv packages and installed them again. Now both backend and frontend give me a SegFault.

I removed all the packages again. Downloaded the mythtv sources, installed a lot och dev-packages, compiled everything. It still gives me a segmentation fault.

I am suspecting it isn't MythTv that is the root of the problem, rather some underlying component. But I don't have a clue. 

I am running on an " AMD Athlon(tm) 64 X2 Dual Core Processor".

Anyone else with similar experience?

---

### Post by mikaelFF on 2007-10-20
After looking at the problem a little bit more I found kernel logs when Mythbackend crashed:

@fusion:~# Oct 21 00:53:36 fusion kernel: [14639.646283] mythbackend[20907] general protection rip:2b169dd2c257 rsp:7fff144696c0 error:0

But, I still don't have a clue.

Anybody?

---

### Post by avsa242 on 2007-10-21
mikael,

Yes I am now running into the same problem with my backend. So far I have only been able to get it to happen twice, although the first time I can't recall what I was doing when it happened. This second time (which occurred about two minutes prior to this post - decided to google for 'mythtv general protection') I believe I attempted to tune into an analog channel (pcHDTV 5500 in dvb mode and an ADS Channel Surfer TV analog card; in my error I enabled the ADS in the 'Analog options' section of the HD5500 setup instead of adding it as a separate card)
I am running 64 bit Gutsy; which are you running (guessing amd64 as well by the size of your 'rip')?

Oct 21 13:38:59 fortanium kernel: [ 9796.582904] mythbackend[10694] general protection rip:2b25691fc1a4 rsp:49014f28 error:0

Cheers
Jesse Burt

---

### Post by mikaelFF on 2007-10-22
Jesse,

I am running 64 bit Gutsy on an AMD X2 processor. How often does you backend crash? Does it happen with the frontend as well?

Both my backend and frontend give me an instant segmentation fault.

Maybe I have some old mythtv libs hanging around. I don't think so, but I will check to make sure.

/Mikael

---

### Post by avsa242 on 2007-10-24
mikael,

Mine is a single core "old" socket 754 Athlon64. Before I posted that reply, that was the second time I had noticed a crash. However, it has now crashed at least once or twice more with a segmentation fault:

Oct 23 13:44:07 fortanium kernel: [36373.144960] mythbackend[9269]: segfault at 00002aaaab183001 rip 00002b53854b58fd rsp 0000000049014d30 error 4

[15445.786090] mythbackend[17535]: segfault at 00002aaaab052000 rip 00002b528ec8d901 rsp 000000004c01ad30 error 4

My frontend seems solid though; I don't believe I've witnessed it crash.
I wish I had made a note of what I was doing at the time of those two segfaults but unfortunately I didn't.

---

### Post by mikaelFF on 2007-10-26
Ok. I think I have solved my problem, but I don't why...

I found out that my sound card wasn't working and that the kernel module for the card (Nvidia HDA integrated on an Asus M2H board) didn't exist. So I downloaded the Ubuntu Gutsy kernel sources. I configured the kernel and added my sound card (all other sound cards where enabled as modules !!!). Compiled and installed the kernel. Rebooted. 

Installed the proprietary NVidia Gfx drivers from nvidia.com. Rebooted again.

apt-get install mythtv-database
apt-get install mythtv-backend

Now I can at least start the mythtv-backend and it starts to record.

Like I said before, I don't understand why this made any difference.

/Mikael

---

