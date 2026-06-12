---
title: "Loss of TV signal: &quot;partial lock&quot;"
date: 2014-11-26
forum: Mythbuntu
---

### Post by Adam_Jacobs on 2014-11-26
I recently installed a new TV tuner card, a TBS6285, which I use with Freeview in the UK.

Mostly, it works fine, but every few days it seems to lose the signal. The symptoms of this are that if a recording is scheduled I end up with a zero bytes recording, and if I try to watch live TV, the frontend reports "partial lock" and puts a message on the screen saying that I should have received a lock by now.

So far, the signal has invariably returned after a reboot, but obviously it's a pain to have to reboot, especially if I don't notice the signal has gone until after it's missed a few recordings.

I can't find anything in the syslog that looks like it might be related, but here is something from the mythbackend log that seems to crop up (or similar variants of it) when the signal is lost:

```
Nov 26 09:23:49 htpc mythbackend: mythbackend[2007]: E DVBRead recorders/dtvsignalmonitor.cpp:322 (HandlePAT) DTVSigMon[1](/dev/dvb/adapter0/frontend0): Program #22080 not found in PAT!#012Program Association Section#012 PSIP tableID(0x0) length(25) extension(0x800a)#012      version(25) current(1) section(0) last_section(0)#012      tsid(32778) programCount(4)#012  program number     0 has PID 0x0010#012  program number 33088 has PID 0x03eb#012  program number 32842 has PID 0x03f3#012  program number 32896 has PID 0x03e8
```

Any idea what is going on here and how I might go about fixing it?

I'm using MythTV 0.27 on Ubuntu 14.04.

Many thanks

Adam

---

### Post by Mythological on 2014-11-26
I don't know if this will help or not, but you might want to try it:

[Do you run one or more TBS PCIe cards under Linux? Check your IRQs...]("http://freetoairamerica.wordpress.com/2014/11/08/do-you-run-one-or-more-tbs-pcie-cards-under-linux-check-your-irqs/")

---

### Post by khPWXxF on 2014-11-27
you do have a good signal? I had problems like this a few years ago after a period of prolonged heavy rain (sound familiar?).   Tv was fine - it only affected my Hauppage tuners.  Swapping to a new download fixed it and I presumed it was water in the lead.  See also the wiki - Google 'mythtv wiki reception'.
Phil

---

### Post by Adam_Jacobs on 2014-11-29
Many thanks for that link, Mythological, I also had some error messages in my syslog about IRQ 16, so it sounds like that could very well have been the problem. I also emailed TBS tech support, and they gave a very similar answer.

Anyway, I have followed the advice given, and I'm hoping that fixes it. Since it was only an intermittent problem anyway, I won't know for a little while if it really is fixed.

---

