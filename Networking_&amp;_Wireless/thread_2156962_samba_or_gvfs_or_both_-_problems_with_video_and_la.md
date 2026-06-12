---
title: "samba or gvfs or both - problems with video and large file transfers"
date: 2013-06-23
forum: Networking &amp; Wireless
---

### Post by JHAx86 on 2013-06-23
I'm in Ubuntu 12.10 64 bits, I don't sure when this started, maybe It is an known issue of 12.10 but I did get into it about a week ago.

I noticed it first when I was playing a video file directly from a windows shared directory in VLC player, the sharing machine had Windows 7 32 bits. VLC stopped responding and could not be killed, I attempted any method I know: from process monitor, from terminal with pkill and kill commands. After a Google search I found an Ubuntu bug report about this, a workaround to avoid logging off or reset the system is to kill gvfs process, this allows to kill VLC too.

I convived with the problem until I needed to copy files from a friend laptop. His hardrive has GPT partitions, so any attempt to mount them failed. GParted see the whole disk as unassigned or unknown. Others Windows machines see them as GPT Protective partitions and does not allow me to read from them. The only way I found is to temporally disable UEFI in the laptop and boot Ubuntu 13.04 from USB. This way partitions are readable.

Then the next problem.

My large HDD is in my Ubuntu 12.10 machine. I started to transfer the files to the directory I'm sharing using samba from Ubuntu 13.04 Live running in the laptop, after less than 1000 files completed the copy stalls, even if let alone hours, and no progress any more from that point. Trying to cancel the operation does nothing, forcing to reset the machine. Then I tried, only to test, to copy the same files running 13.04 live to shared folder of a PC with Windows 8. The process completed successfully.

Something should be wrong with samba in 12.10, any info appreciated. Also if somebody found a workaround please share it.

Sharing folders using samba is practical more than using pendrives or open cases to connect hard drives. I had done it for years. This is the first serious issue I had, that really impacts my use of this machine.

I'm not prepared to update to 13.04 yet.

---

