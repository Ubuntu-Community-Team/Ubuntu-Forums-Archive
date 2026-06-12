---
title: "Updates disabling network"
date: 2006-01-10
forum: Networking &amp; Wireless
---

### Post by ml3p7 on 2006-01-10
I recently purchased the following combination of parts:

mobo:   ASUS A8N-SLI
processor:	AMD Athlon 64 x2 4200+


I installed the most recent version of Ubuntu.  It installs and works perfectly until I run the updates.  Whether I run them all in a batch or one at a time, upon rebooting I no longer have a network connection.  (I have DSL.)

I first installed it and allowed all (39) of the available updates to run.  I rebooted and no longer had a network connection.  I have some Windows technical ability, but I won't claim to have any Linux/Unix abilities.  That being said I did check the network connections and the relevant portions of the device manager, where everything seemed to look alright.  

I then re-installed the system.  I again had a network connection.  I picked only one update to run:  acpi-support  version 0.46 Ubuntu1.  I rebooted and when the machine was booting I watched one of the processes hang for a while at:

Waiting for network interface to come up - 	Fail  

I re-installed the system two more times, each time allowing only one update each time:  cpio v. 2.5-1.2,  and Perl 5.8.7 - 5.  Each time the same thing happened.

The system is fine until I let any update run, then my network connection is gone.  Also, when I re-install the system, I can't just let Ubuntu's install program re-partition and re-format the drive.  If I do, the network connection is unavailable even to the install program.  I have to expose the drive to a Windows drive, use the disk management applet that Windows provides to delete the partition, then start the install program on the drive I want to install Ubuntu on.  Then the install program has a live connection to work with.

What is the cause of this, aside from my inexperience and lack of know-how?  What can I do?

Thanks.

---

