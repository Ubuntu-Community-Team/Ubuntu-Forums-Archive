---
title: "video stutters - high %wa and load ?"
date: 2010-06-10
forum: Mythbuntu
---

### Post by dualboot on 2010-06-10
I have a combined frontend/backend. Video stuttering after a few seconds or minutes of playback. I upgraded to 10.04 a few weeks back, but this only started a few days ago.  I was hitting a problem with frontend locking up, followed advice to move to daily builds that fixed it.  I think these problems started then, but can't be sure.

I noticed in 'top' that though there is no high cpu, the 'wa' figure is up at around 50pc whenever the video stutters. Also the load average is between 5 and 6 all the time (when its doing nothing)


I have two sata disks and so I don't believe it is a faulty disk. Same effect on either. When the 'wa' goes down the video if normal too.

I don't believe its actually either frontend or back end program but something at a lower level.

I get the same symptoms if I 'play' a file from the command line with vlc. Even copying a file from one disk to the other with mv hits the wa

Interestingly I attached a USB hard drive, and playing an archived .mpg file from that is fine. 

watching live TV is also fine !  Even if I pause it. What an earth is going on ? 

Any suggestions on way to troubleshoot it ?

I think the load average is way to high - what do other people have ?

---

### Post by nickrout on 2010-06-10
> **dualboot said:**
> I have a combined frontend/backend. Video stuttering after a few seconds or minutes of playback. I upgraded to 10.04 a few weeks back, but this only started a few days ago.  I was hitting a problem with frontend locking up, followed advice to move to daily builds that fixed it.  I think these problems started then, but can't be sure.

I noticed in 'top' that though there is no high cpu, the 'wa' figure is up at around 50pc whenever the video stutters. Also the load average is between 5 and 6 all the time (when its doing nothing)


I have two sata disks and so I don't believe it is a faulty disk. Same effect on either. When the 'wa' goes down the video if normal too.

I don't believe its actually either frontend or back end program but something at a lower level.

I get the same symptoms if I 'play' a file from the command line with vlc. Even copying a file from one disk to the other with mv hits the wa

Interestingly I attached a USB hard drive, and playing an archived .mpg file from that is fine. 

watching live TV is also fine !  Even if I pause it. What an earth is going on ? 

Any suggestions on way to troubleshoot it ?

I think the load average is way to high - what do other people have ?

what does dmesg tell you?

---

### Post by dualboot on 2010-06-11
Dmesg (or /var/log/kern.log for the readable time stamps) doesn't show anything when it happens.  There are the occasional disk type error messages against one of the disks like below, but they don't coincide with the problems.  This was what started me looking at if it could be the disk, but I don't see similar messages for other disks (I presume ata4 is my second disk, ata1 is my first ? )

> 
Jun 10 19:32:28 amilo kernel: [38854.884343] ata4.00: exception Emask 0x0 SAct 0
x7a SErr 0x0 action 0x0
Jun 10 19:32:28 amilo kernel: [38854.884349] ata4.00: irq_stat 0x40000008
Jun 10 19:32:28 amilo kernel: [38854.884356] ata4.00: failed command: READ FPDMA
 QUEUED
Jun 10 19:32:28 amilo kernel: [38854.884366] ata4.00: cmd 60/60:18:07:33:76/00:0
0:41:00:00/40 tag 3 ncq 49152 in
Jun 10 19:32:28 amilo kernel: [38854.884368]          res 51/40:0e:59:33:76/b9:0
0:41:00:00/40 Emask 0x409 (media error) <F>
Jun 10 19:32:28 amilo kernel: [38854.884373] ata4.00: status: { DRDY ERR }
Jun 10 19:32:28 amilo kernel: [38854.884376] ata4.00: error: { UNC }
Jun 10 19:32:28 amilo kernel: [38854.886575] ata4.00: configured for UDMA/133
Jun 10 19:32:28 amilo kernel: [38854.886593] ata4: EH complete
--

I've now noticed that after re-booting last thing at night and leaving it idle (i.e. booted to the main menu page in MB, but it has not recorded anything or played anything) the load is back down to "load average: 1.12, 1.20, 1.27"

I play a file, wa is high, load starts climbing above 3
when I exit out of it, load starts to drop.

So perhaps load is just a side effect, not a cause - don't know why it stayed high last night - perhaps system just gets progressively stressed ?

Dmesg showed nothing more since the reboot last night.

---

### Post by nickrout on 2010-06-11
what is your sata/motherboard chipsets? Looks to me like a kernel issue with your drive, or the chipsets accessing it. Some googling on those error messages may reveal?

---

### Post by dualboot on 2010-06-13
I've tried rebooting, and choosing the previous kernel from the grub list, and also booting from a live CD and it seems to be the same problem.

I've been racking my brains trying to find some consistency in it (other than the high wa figure in top), but can't find any.  The video can sometimes play fine in a section which if I re-play with stutter.  

I'm currently trying to copy the bulk of my recordings to a USD HD, so I can add that the the recordings storage group, and remove that disk, but is nearly 800G, and with the slow performance it had had 24 hours so far, and done only around 150G !

iotop is reporting the rsync process using around 250K/s pretty consistently.  This is a copy from a 1TB SATA disk to a 1TB USB disk.

I got comparable numbers copying from one SATA hard disk to the other in the same box.

Can anyone say if this is unusually poor ?

---

### Post by nickrout on 2010-06-14
Googling the type of errors you are getting leads me to believe your hard drive is dying. Get what you can off it and get a new one (under warranty with any luck!)

Then again other googling indicates it may be a kernel bug, and that a newer kernel may fix it.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/588439](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/588439)

---

### Post by dualboot on 2010-06-14
Thanks for your help Nick.

The kernel bug sounds highly plausible, but what do you make of still getting the symptom with the previous kernel from the grub list, and from a live CD ?  Maybe I should try a completely different distro's live CD ?

I'm getting stuttering video from recordings that are on two different drives, but looking a the results of the cp operation below suggest it is only the second big 1TB disk thats slow

I've just mounted an NFS volume, and copying a recording from the 1TB SATA drive to it gets similar ~500K/s in IOTOP, but copying a file from the first SATA or USB disk to it gets 10-20M/s !  

The ultimate test once I've finished this rsync (which will be a few days at this rate) will be to move the big SATA disk to the USB enclosure - if its fine then it will eliminate the disk.

The good news is at least recordings are being laid down OK.

---

