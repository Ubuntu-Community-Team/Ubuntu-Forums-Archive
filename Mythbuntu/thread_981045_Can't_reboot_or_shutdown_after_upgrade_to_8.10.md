---
title: "Can't reboot or shutdown after upgrade to 8.10"
date: 2008-11-13
forum: Mythbuntu
---

### Post by tbaca on 2008-11-13
I have been running Myth for several years.  I thought I would give Mythbuntu a try, so I loaded 8.04.  The machine is a dc7800 Q6600 HP machine.  I have it setup as a RAID 1 for the OS and a RAID 5 for storage.  The RAID 5 storage is 4 drives in and external box.  8.04 worked okay, except, when rebooting/restarting, it would not always configure the external storage correctly.  Many times I would have to re-add a drive and then it would take a day to re-sync.

I upgraded the NVIDIA driver to 177, no problems.  Then 8.10 came out.  The main reason for trying Mythbuntu was for the more frequent updates, so I installed it.  Every thing when smoothly, Video still works, RAID 5 box has always been set up correctly.  I had a real tough time getting my remote front-ends video drives installed (Diskless).  But I am having a new problem, that I have not been able to solve, 

**I can’t shutdown or reboot.**

I have tried shutting down via Myth (exit screen), Selecting Quit from the Desktop, CTRL-ALT-F1, login and do a reboot or shut down, even issuing a reboot (or shutdown) while remotely logged in.  If I use “Suspend” or “Hibernate” from the Desktop, the machine shuts down and powers off as it should.

I have tried several solutions:
[INDENT]Put:

ifconfig eth0 down 
ifconfig wlan0 down
at the beginning of “stop” in: /etc/init.d/alsa-utils

Put
1.add "apm=power_off" to kernel option.
2.add "apm power_off=1" to /etc/modules

Put:
#From [http://forum.eeeuser.com/viewtopic.php?id=1859](http://forum.eeeuser.com/viewtopic.php?id=1859)
rmmod snd-hda-intel

In /etc/init.d/halt

	Put:
append="'apm=on acpi=force"
in /etc/lilo.conf[/INDENT]
Nothing has fixed the problem.  Adding “rmmod snd-hda-intel” in /etc/init.d/halt helped in that I can now at least wait until the box finishes, then press and hold the power button and restart it that way.  Before adding that, when I would press and hold the power button, the machine would reboot, but LILO was corrupt causing the machine to only display 99 99 99 99 at boot time,  I had to use a rescue disk and run LILO to get the machine to reboot.

From memory, now when I issue a reboot from a terminal session, I see many processes shutdown, then a message that says “All processes shutdown within 2 seconds” (typed from memory).  There is some disk activity, then nothing; lastnight I waited 30 minutes, still nothing.

One other thing, I have not done as much work, but the diskless frontend won’t shutdown either.  Note, backend is running 64-bit, while frontend (P4) is running 32 bit.

Any ideas/suggestions are welcome.  I have found this problem very difficult to troubleshoot because I don’t know where to look.

---

