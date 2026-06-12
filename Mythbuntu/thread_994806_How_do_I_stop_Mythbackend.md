---
title: "How do I stop Mythbackend?"
date: 2008-11-27
forum: Mythbuntu
---

### Post by rdstokes on 2008-11-27
I just need to stop mythbackend to import a mythcoverg restore.  (I assume I have to stop mythbackend to restore a table...)  All the commands I try result in "command not found" messages.

On Fedora, I used this command but Ubuntu doesn't like it:
/sbin/service mythbackend stop
sudo: /bin/service: command not found

All the web sites for Ubuntu say to use this command but other sites say init.d has been removed from the latest version:
$ sudo /etc/init.d/mythbackend stop
sudo: etcinit.dmythbackend: command not found

This web page for 8.10 (although I'm at 8.04,) [http://www.dedoimedo.com/computers/ubuntu-8-10-review.html](http://www.dedoimedo.com/computers/ubuntu-8-10-review.html), says to use:
$ sudo service mythbackend stop
sudo: service: command not found

Can anyone tell me what the command is to stop mythbackend?

Thanks,
Rob
My configuration is: 
MythTV version: 0.21.20080304-1 16838
Ubuntu 8.04.1, kernel version: 2.6.24-21-generic
CPU: Intel Pentium 4 CPU 3.2GHz Socket 775 800 FSB w/Hyper Threading Technology 
Memory: 1Gig DDR 333 Memory 180 Pin 
Motherboard: ASRock 775i65G Mother Board 
Optical Drive: LG 18X DVD RW + Dual Layer 
Hard Drive: 1 Western Digital 1 TB 7200 RPM Cache Serial ATA
Video onboard: Integrated SiS Ultra256 2D/3D Graphics 
Video card: Micro-star International (MSI) AGP GeForce FX5200-TD128LF, 8X, 128M, DDR1, D-Sub, DVI-D, TV-out
Audio onboard: AUDIO ADI AD1888 6-channel audio CODEC 
Audio card: Riviera C-Media CMI 8738 (Connected to my entertainment center via the optical cable)
Network Card: Onboard 10/100 Network Card 
Tuner card: pcHDTV HD-5500

---

### Post by meanmrmustard on 2008-11-27
Try this:

sudo /etc/init.d/mythtv-backend stop (and conversely start, also: restart)
works on my 8.10 boxes.

---

### Post by rdstokes on 2008-11-27
meanmrmustard,

That did it!  Thank you!

Rob

---

### Post by R3M3 on 2010-06-24
Since I never can remember it, and this thread is the first Google Hit for "mythbuntu stop mythbackend", I'll resurrect this thread to add new info.

Running "sudo /etc/init.d/mythtv-backend stop" on recent Ubuntu version (e.g. Karmic or Lucid) produces the following:

> Since the script you are attempting to invoke has been converted into an
Upstart job, you may also use the stop( 8 ) utility, e.g. stop mythtv-backend

"sudo stop mythtv-backend" and "sudo start mythtv-backend" work, and seem to be the preferred way of doing it these days.

---

