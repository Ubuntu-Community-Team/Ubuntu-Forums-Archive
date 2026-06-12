---
title: "100Mbit connection - slow internal transfer rate"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by mykrob on 2009-02-06
Running Ubuntu 8.10 with all updates on my desktop, and Athlon 3200+ w 2GB of RAM, and it does fine. My laptop is also running 8.10, a 2.2GHz dual core Intel Centrino with 3GB of RAM. Seems that network transfer speed on my LAN is a bit slow. On a wired connection, I get a sustained transfer of about 4-5MB per second. on a 100Mbit connection, what kinds of speed should I be getting? While i don't know technically what I should be getting, sees to me that it should be much faster than this.

please advise.

thanks,
-myk

---

### Post by Roasted on 2009-02-06
That sounds... sorta normal...

100Mb connection means it's 100 megabits per second,  not 100 megaBYTES per second.

Things run in 8 bit... 100 megabits per second divided by 8 (bit) = 12.5

Meaning 12.5MB (megabytes) is the absolute max you will transfer data at on a 100Mb/s network... meaning, roughly 3 average length mp3 songs per second is what you will transfer when @ 12.5.

Mb = Megabits
MB = Megabytes

When I transfer stuff at home in between my Samba server and other computers, I get around 9MB/second. That's 12.5 + some overhead which can decrease performance (very long cables, low quality cables, kinked cables, poor hardware drivers, etc). It's very rare to max out at 12.5 MB/second. At work here, our internal network is mostly 10/100 switches and I normally transfer @ 7 MB/second.

When I transfer in the same scenario except wirelessly, I get 2-3 MB/second.

The only way to "beef" up the speeds is to run a gigabit network... meaning 1000 Mb/s... divided by 8 = 125 MB/second... BUT... you need a router with gigabit ports + gigabit network cards in all computers you're using to make that happen... which can add up to a lot of money.

---

### Post by mykrob on 2009-02-06
thank you, that all makes sense. Is there anything I can check or change to get better than 5? that is the best i get even when nothing else is going on on my network.

---

### Post by Roasted on 2009-02-07
If you run gigabit hardware, you'd see an increase in performance most definitely. But that'll require quite a bit of funds to buy the required parts and it'll also only apply to wired networks. Wireless will still be noticeably slower than wired, no matter how you look at it.

If you go gigabit, you need 10/100/1000 network cards in the computers you're using + a router with 4 outbound 10/100/1000 ports. I looked at doing this for the 4 desktops I have at my house + a router and it was easily over 100 bucks.

If you're going to stick with what you got, hmm, it's hard to say. Do you have a firewall in place? Things like that can hinder the performance of a straight-through cable. Also REALLY long cables can also lose their signal strength... but I run 200-300 foot patch cables at work and have decent performance, so I kind of doubt that you've maxed out beyond that point.

The network drivers associated with network cards could also play a factor in not completely maximizing speeds.

Have you tried a Windows vs Windows computer? At first I thought my Samba server was just slow when transferring Ubuntu-to-Windows or Windows-to-Ubuntu. I ended up booting into Windows on both my main desktop and my spare and transferred a 700mb image file. I ended up pulling 1MB/s less than I did with Ubuntu/Windows.... so I knew my set up was fine and it was simply hardware (router/wire/whatever) limitations that was bringing my POTENTIAL (but nearly impossible) 12.5MB/s to 9ish MB/s.

---

### Post by statmonkey on 2009-02-08
I am running Ibex, have 10/100 cards that run through a gigabyte switch (where I live finding 1000 cards is difficult).  What I am seeing is that on initial boot I get fairly robust speeds (around 8-10mb) but after transferring a few files this degrades.  In fact I can start a transfer and watch it drop from the initial 8 down to 17 or 18kbs during a transfer of 700mb or so.  This occurs during a transfer between local drives as well as between a local drive and a cifs mounted drive in my NAS and even from a local Sata to a USB thumb (although the relative speeds are different).  It renders the NAS and really Ubuntu pretty useless.  

Based on other threads I have tried remounting the drives nodiratime which had little or no affect. (edit) I have also changed out the cables, swapped network cards, attempted to adjust mtu's, looked into jumbo frames.  I did boot from the CD and this seemed to work faster but it is not realistic for me to boot a live CD whenever I want to transfer  Additionally I have attempted using ftp/ssh/rsync to transfer with the same results.  I never had this problem with 8.04 or earlier and am thinking of downgrading.  Any suggestions or ideas?  I believe I have read most of the threads on this but perhaps I missed something.

TIA

---

### Post by Roasted on 2009-02-10
How are the drives mounted? I have a samba storage setup with my Ubuntu computer and my samba drive is mounted automatically via fstab. I haven't had any issues with fstab auto-mounts.

---

