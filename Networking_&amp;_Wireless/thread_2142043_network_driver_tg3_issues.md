---
title: "network driver tg3 issues"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by dmdelorme on 2013-05-04
Hi
I have been having issues with the tg3 driver on a 02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
 i am now running the following 
Linux solaris 3.9.0-030900-generic #201304291257 SMP Mon Apr 29 16:58:15 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
with driver
filename:       /lib/modules/3.9.0-030900-generic/kernel/drivers/net/ethernet/broadcom/tg3.ko
firmware:       tigon/tg3_tso5.bin
firmware:       tigon/tg3_tso.bin
firmware:       tigon/tg3.bin
version:        3.130
 this is the error that i am receiving
May  4 10:12:53 solaris kernel: [55170.600595] tg3 0000:02:00.0 eth0: Link is down
May  4 10:12:53 solaris NetworkManager[1145]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
May  4 10:12:56 solaris kernel: [55173.492995] tg3 0000:02:00.0 eth0: Link is up at 1000 Mbps, full duplex
May  4 10:12:56 solaris kernel: [55173.493003] tg3 0000:02:00.0 eth0: Flow control is on for TX and on for RX
May  4 10:12:56 solaris kernel: [55173.493005] tg3 0000:02:00.0 eth0: EEE is enabled
May  4 10:12:56 solaris NetworkManager[1145]: <info> (eth0): carrier now ON (device state 100)

now this does not happen all the time it appears to be random but related to large file transfers.. 
here are some results of a dd with net issues and no issues
 root@solaris:/home/david/Desktop/tg3-3.124c# time dd if=/dev/zero of=/nfs/raid/Downloads/testfile3 bs=16k count=514000
514000+0 records in
514000+0 records out
8421376000 bytes (8.4 GB) copied, 158.858 s, 53.0 MB/s

root@solaris:/home/david/Desktop/tg3-3.124c# time dd if=/dev/zero of=/nfs/raid/Downloads/testfile3 bs=16k count=514000
514000+0 records in
514000+0 records out
8421376000 bytes (8.4 GB) copied, 79.734 s, 106 MB/s

I am at wits end on this issue i think it is related to firmware on the chip ie rev 10 and down..
it also happened with several kernels
the server is not showing any errors nor is my openwrt router.

thanks David

---

### Post by dmdelorme on 2013-05-07
well I compiled a custom 3.9 kernel with some of the amd stuff removed.. it helped a bit.
To day i went back and  set cpu affinity. it corrected the issue but i am confused as  echo 3 > /proc/irq/16/smp_affinity resets back to the original setting.
 cat /proc/irq/16/smp_affinity
c0c
which i am assuming is 3 in hex. so why would this clear up the issue with dropping my nic... it also seem that every 4th or 5th packet runs into a issue of some sort.

---

### Post by dmdelorme on 2013-05-12
Well I learned a lesson today. after all the solutions i tried to fix the problem i put my cable in another port on my switch and it was fixed LOL. no errors no 
hiccups just clean and fast transfers.  I also learned a new command mii-tool -w eth0.

---

