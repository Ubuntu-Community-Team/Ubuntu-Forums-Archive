---
title: "Advice Samba Share ubuntu 10.04"
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by wsastrawan23 on 2012-03-03
I am new for Ubuntu, this my first Linux OS installation.

I need to use Ubuntu 10.04 LTS with Samba to share file with other windows pc client over the LAN. (I use the server only for data share)

Is there will be problem to share the data to more than 15 PC client (ex: slow connection, etc)? I tested only for one PC client and it works great, how ever i am not sure if i use it for more than 15 client.

Any advices? 

THank you,
W Sastrawan

---

### Post by ahallubuntu on 2012-03-04
You have mentioned nothing about what kind of hardware you will run Ubuntu on.  Ubuntu 10.04 LTS itself works great for Samba sharing with multiple users.  The performance will vary depending on the speed of the hardware: CPU speed, hard drive specs (new driver or older hard drive?), specs of the network card (integrated on the motherboard?), how much RAM, etc.

I have Ubuntu 10.04 LTS installed on several old Pentium 4-based computers with 1GB of RAM each, and with a few users performance is adequate.  If I had 15 users heavily using the server, I might want to upgrade to newer hardware.

---

### Post by wsastrawan23 on 2012-03-04
Dear ahallubuntu,

Thank you for your reply, the Locayl area network will not heavily using the server, any advices for the minimum requirement is really appreciated.

What is the processor type should i use?
What is the hard disk drive type should i use?
Which NIC should i use?

I don't think i need to use high spec of hardware, this is only for data share...

Thank you and waiting your advices....

W Sastrawan

---

### Post by redmk2 on 2012-03-04
> **wsastrawan23 said:**
> Dear ahallubuntu,

Thank you for your reply, the Locayl area network will not heavily using the server, any advices for the minimum requirement is really appreciated.

What is the processor type should i use?
What is the hard disk drive type should i use?
Which NIC should i use?

I don't think i need to use high spec of hardware, this is only for data share...

Thank you and waiting your advices....

W Sastrawan

If this is only going to be a file server (NAS) then the CPU is not the thing to concentrate on.  The home user NAS units available prove that.  I believe most of them are ARM CPU's.  An Intel Atom CPU will work fine.  You really don't need more than 512 MB of RAM (Max 1GB).  The hard drive is where the money should be spent.  You should use a SATA drive.  If the motherboard doesn't support that then get a cheap PCI SATA adapter.  This will allow you to run SATA v1.  Bus speed and filesystem I/O is more important than CPU speed and RAM.  

I have a machine that is an old Dell P3 (Coppermine 1Ghz)  with 512 MB of RAM.  I added a SATA card and a Western Digital Caviar Black 1TB 64MB cache (WD1002FAEX).  This particular drive is fast for home use (7200 RPM) and has double ball bearings on the spindle (most have a single bearing).

This works perfect for me. I can backup 100GB chunks with no real load on the OS and it is pretty quiet.

---

### Post by wsastrawan23 on 2012-03-08
Thank you for sharing, I decide to use core2duo machine, also planned to install accounting software build with java + postgreSQL database.

Any comment?

Regards,
Wayan

---

