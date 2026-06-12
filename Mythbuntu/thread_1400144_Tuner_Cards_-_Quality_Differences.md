---
title: "Tuner Cards - Quality Differences?"
date: 2010-02-06
forum: Mythbuntu
---

### Post by B34N on 2010-02-06
Can a capture card make a difference?

I have an old p4 running Mythbuntu as my MythTV backend.  It works well but I have noticed that I get choppy video and audio if I try to record two HD programs simultaneously.  I assume that this is due to the computer being overloaded but I wanted to make sure that it's not due to quality differences in the tuner cards.

I capture content over Clear QAM.  My primary tuner card is a Kworld ATSC-115 which uses the nxt2004 chipset.  My secondary tuner is a Hauppauge HVR-950Q which uses the xc5000 chipset.  Is one chipset better than the other?  Does the chipset make a difference in how much CPU power is required?

Thank you!

---

### Post by jdk82 on 2010-02-06
First off, I'm not an expert, so someone feel free to correct me if I am wrong. AFAIK, since those are both digital tuners, they do not assist with decoding at all, since it is unnecessary. The digital stream is transferred directly to the hard-drive, unlike with analogue. So no, I don't think the tuners make a difference for a digital signal. Try running top from a terminal while you are recording two shows

```
top
```

to see if you are really using all of your cpu power. I have a 950Q and a PVR-150 (analogue) and I can record with both while watching another program, also on an old P4, 2.8 GHz. I have several sata hard drives however, and I suspect that your bottle neck may be the speed of your hard drives. Hope this helps.

Josh

---

### Post by B34N on 2010-02-06
Thank you for the suggestion.  I did a quick check and it seems that the CPU is fine.  However, I wonder if I shouldn't run the frontend on the backend server when I'm not using it.  It seems that it took a good deal of CPU power even though it was idle.

I am definitely having trouble with the 950q regardless if another channel is recording.  I need to verify that I have it connected to a USB 2.0 port.  I'm 90% sure.  Any suggestions on how to verify?

---

### Post by ian dobson on 2010-02-07
Hi,

Are you sure the choppyness is comming from the recording and not the playback? Recording a HD stream doesn't put the tuner card under any real load, it just needs to pass the data through to the cpu which writes it to the disk.

If your using USB tuner cards make sure they're on different hubs so that your not sharing the root hub for 2 tuners. Maybe attach a lsusb

Maybe try disabling commflagging while recording, that puts the CPU/disk system under alot of strain (Writing to the disk, reading it back and updating the SQL database).

What harddisks re you using? Is everything on the same drive?

My big backend (Quad Core,8Gb ram,6Tb Raid 5 Array) can record 4 HD programs at the same time while playing back a SD recording on a remote Frontend, but the I/O load starts becomming a problem.

Regards
Ian Dobson

---

### Post by Kevbert on 2010-02-07
It may be a memory problem. How much RAM do you have ?

---

### Post by B34N on 2010-02-08
> **Kevbert said:**
> It may be a memory problem. How much RAM do you have ?

2.5GB.  It only happens with the USB tuner.

---

### Post by Caps18 on 2010-02-10
Is the cable wire good?  Any splitters?  Power wire interference?

I have two identical cards and one is having problems I think because of a bad connection.  (Or at least I hope it is that).  I will find out tomorrow night when I fix it.

---

### Post by B34N on 2010-02-10
> **Caps18 said:**
> Is the cable wire good?  Any splitters?  Power wire interference?


Yes they are on a splitter.  The strange thing is that it only happens occasionally and not on every channel.

---

### Post by aovermy on 2010-02-11
do you see anything in kern.log or dmesg when you start seeing sputtering? Can you transfer a recording where you see sputter to another box and see if you can watch it there? That can separate playback issues from recording issues. 

I've got a AMD XP 2400 (1 core running at 2000Mhz) that has 3 HD tuners (1 USb 2 PCI) and one USB analog tuner (Plextor go7007 device) and even recording 4 shows simulateously is fine. And my Satas are only running at 1.5Gbps (because of the old hardware).  Granted, I don't usually watch at the same time (it's why I have a PVR, I'm seldom around when anything I might want to watch is on).

---

