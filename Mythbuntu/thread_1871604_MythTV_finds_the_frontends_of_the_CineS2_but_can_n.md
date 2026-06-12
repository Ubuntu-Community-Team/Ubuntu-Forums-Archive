---
title: "MythTV finds the frontends of the CineS2 but can not scan"
date: 2011-10-29
forum: Mythbuntu
---

### Post by TwPlo on 2011-10-29
An update of the older post concerning the cines2 and VideoforLinux.
Not placed there cause nothing was working at that stage, compiling errors.


Meaning : Videoforlinux is corretly installed.
System description : 

Asus E35M1-M mainboard , AMD Zacate dual core CPU.
AMD 6100 series video processor.
AMD Hudson on board.
2GB patriot DDR3 memory
DigitalDevices CineS2 also known as Mystique.
CAM module installed , connected to mini-PCIE card from DigitalDevices.


Ubuntu 11.10 32 bit
Build environment available : V4L-dvb seems correctly installed and various logs find the micronas based design of the CineS2.
Perhaps one thing that I did not had to do: I installed also the Linux-firmware-nonfree with the result that a huge number of different firmware packages are installed, so not onle ngene_18.fw is installed, also ngene_17.fw and ngene_15.fw. Perghaps is should this firmware pack again. Installed via Synaptic.

Note: befiore installing the linux-firmware-nonfree pack, same results so installing the pack did not change anything related to the cineS2.
The CAM card is also detected, well, the small mini-Pci-E adapter card of it.
I can only find out if the CAM (Seca2/3) will work as soon when channels are found.

Receive equipment:
Wavefrontier 90cm dish, pointed towards Astra 19.2E, 25E and 28.2E, Hotbird 13E
Since the CineS2 has two inputs, alls LNB's are connected to two disecq switches
placed outdoors on the dish pole.

What follows now is the history of the log files.
Logs txt files, zipped.


Logs as attachments:

Lspci started as root
dmegs.log
dmegs.0.log
kern.log
mythbackend.log


All files zipped, not that that was really needed since logs are not so big.
But saving every bit of bandwidth.


Kernlog says something that the firmware (ngene_18.fw) is not loaded but it is installed under /lib/frimware.

Also, MyhTV find the CineS2 as STV09X device (which is the demodulator of the CineS2)
But if I click in the backend on diseq, : not connected message.
Scan also.

But if the firmware is not loaded, then this sounds rather logical.

MythV: the backend config in several steps assumes that a analog tuner or dvbT/C tuner settings.
Is this normal that the backend menu structure is sort of generic and since most users use DVB-T or C or should the backend detect installed tuners first?

I have no clue why the firmware can not load.

---

### Post by nickrout on 2011-10-30
from your backend log:

> 2011-10-28 21:20:50.994 MythBackend, Warning: No valid capture cards are defined in the database.
2011-10-28 21:20:51.030 New DB scheduler connection
2011-10-28 21:20:51.061 Connected to database 'mythconverg' at host: localhost
2011-10-28 21:20:51.079 Scheduler, Error: No capture cards are defined in the database.
			**Perhaps you should re-read the installation instructions?**

Start at the beginning - do you have the expected /dev/dvb devices once the drivers are loaded?

Can you scan or pick up any channels using the usual command line test tools. - dvbscan, dvbtune, etc

Once you are sure the card is working, then we will go on to set up the device in mythtv.

---

### Post by walter- on 2011-12-11
Hi TwPlo, 

Still looking for a solution?
As far from the logs, the CineS2 card drivers are loaded ok (fw18)

see dmseg.log 

DVB: registering new adapter (nGene)
[   10.117304] DVB: registering adapter 0 frontend 0 (STV090x Multistandard)...
[   10.168962] LNBx2x attached on addr=8
[   10.168981] stv6110x_attach: Attaching STV6110x
[   10.168986] DVB: registering new adapter (nGene)
[   10.168992] DVB: registering adapter 1 frontend 0 (STV090x Multistandard)...

I couldn't directly find anything about the CI module being detected, but I don't think this is supported at the moment in Mythtv anyway.  

And as nick is pointing out; start by defining the cards in Mythth (the log form Nick is showing there are no cards defined yet in Mythtv).   

Walter

---

