---
title: "Pentium 3 500 gigabit speeds?"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by rectifiercc on 2011-05-14
I have an old Pentium 3 500 that I've proudly resurrected into an Ubuntu file server. I installed a gigabit network card but on file transfers I only get an average of 250kb/s transfer rate wired or wireless. Can I get faster rates than that by installing cat6 cables etc or is the computer just too old to transfer any faster? When I copy files locally between drives on the server that's the fastest speed too. The drives are external USB 2 drives.

Any suggestions on speeding things up?

What speeds are some of you experiencing with your setup?

Here is my setup

Pentium 3 500 running Ubuntu 9.10 with a Gigabit ethernet card
Gigabit Netgear router
ethernet cables are all cat5e
Computers being serverd are all macintosh

thx

---

### Post by elliotbeken on 2011-05-15
What is the CPU load while you are doing a transfer. ?

---

### Post by slooksterpsv on 2011-05-15
If you're using an external on the Ubuntu Server (USB), then unless you've added a USB 2.0 card, I believe you're using USB 1.1.

Maximum throughput for USB 1.1 is: 12 Mb/s which is about 1.5MB/s
Mb = Megabit
MB = Megabyte

---

### Post by rectifiercc on 2011-05-15
Thx for the replies:

I forgot to mention that I did install a USB 2 card that the drives are connected to.

I did some interesting tests and here are the results.

In my initial post I was using ftp clients (Filezilla and Fetch) to transfer the file from my external USB drive on my server to my macbook pro. Those speeds were as posted, around 250KB/s

When I transferred the same file using afpd I got a transfer rate of 5.1MB/s (whoa big difference!)

When I transferred the same file using apache2 the transfer rate was also 5.1MB/s

When I transferred the same file using smb the transfer rate was a little slower at 4.75MB/s

When I transferred the same file using scp from command line the transfer rate was 3.3MB/s (surprising!)

Now when I transferred the same file from an internal drive on my server the speed almost doubled at 8.14MB/s

So it seems that using afpd or http, copying a file from an internal drive on the server, are the winners in my setup.

Now i wonder if installing a SATA card in the server and installing my drives all internally will yield better results yet?

By the way in response to elliotbeken the cpu usage on these tests all averaged around 12% with the exception of scp which had a CPU load of 45%

---

### Post by MartyBuntu on 2011-05-15
USB 2.0 is your bottleneck.

The gigabit card is wasted in a setup like this.

---

### Post by slooksterpsv on 2011-05-15
USB, which I don't know why we didn't use Firewire as it's better, is a CPU hog, no offense, but USB just sucks the speed of your computer down. Firewire, not so much. Firewire doesn't use too much of the CPU vs USB:

[quote=Wikipedia]
While USB 2.0 (introduced in 2001) is quoted as running at a higher signaling rate (480 Mbit/s) than legacy FireWire 400 (400 Mbit/s, available since 1995), data transfers over S400 FireWire interfaces generally outperform similar transfers over USB 2.0 interfaces in real world environments. Few if any USB 2.0 device implementations are capable of saturating the entire 480 Mbit/s, but this can be achieved with multiple devices on the same bus. In real world tests USB PC hosts rarely can sustain transfers exceeding 280 Mbit/s, with 240 Mbit/s being the norm. This is likely due to USB's reliance on the host processor to manage low-level USB protocol, whereas FireWire delegates the same tasks to the interface hardware (requiring less or no CPU usage). For example, the FireWire host interface supports memory-mapped devices, allowing high-level protocols to run without loading the host CPU with interrupts and buffer-copy operations.[6]
[/quote]

Sata card + internal may be faster to a degree... not sure on that hardware how it'd react to SATA or SATA's CPU requirements (if any) I'd have to research that.

---

### Post by rectifiercc on 2011-05-17
ok thx! Yeah it does seem like USB 2 is the culprit. Do you guys think it's better for me to install a firewire card or sata card in the old pc?

---

