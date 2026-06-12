---
title: "Air2PC tuning problems"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by gizzard on 2007-05-18
I'm having trouble getting my Air2PC ATSC / DVB-T card to work under Ubuntu 6.06 LTS. I have been primarily following the DVB wiki at [www.linuxtv.org](www.linuxtv.org). This machine dual boots to XP, and using DVBviewer ([www.technisat.com](www.technisat.com)) I am able to successfully tune several HDTV channels. The frontend on the card is apparently a Broadcom BCM3510KPF. My kernel is 2.6.15-28-386. Synaptic shows that dvb-utils (version 1.1.0-9), dvbstream (0.5-1), and libdvb-dev (0.5.5.1-1) are installed. I have /dev/dvb/adapter0/ with demux0, dvr0, frontend0, and net0 contained within.

I have tried a number of things but I can't get the scan program to work. In the linuxtv wiki, once dvb-utils is installed, there should be an 'atsc' folder under /usr/share/doc/dvb-utils/examples/scan, but I only have dvb-t, dvb-s, and dvb-c. When I run 'scan -v dvb-t/uk-WinterHill' from the scan folder, I get the following:

> scanning dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 754166670 0 3 0 1 0 0 0
ERROR: initial tuning failed
dumping lists (0 services)
Done.

I don't have a dvb-t from my location (US), so I've created my own initial channel file using the channel data from the XP software and simply replacing the tuning frequencies, but that produces the same error (I may not have done that correctly).

I am assuming dvb-utils and dvb-apps refers to the same package. I have also tried installing a newer version of dvb-apps (1.1.1) by compiling the source myself from linuxtv. However, when I make install I get these errors:

> cat: CVS/Root: No such file or directory

make[1]: *** [Makefile] Error 2


For reference, here is my edited dmesg output (if there are additional lines that are needed, I can post them):

> [17179609.356000] b2c2-flexcop: B2C2 FlexcopII/II(b)/III digital TV receiver chip loaded successfully
[17179609.408000] flexcop-pci: will use the HW PID filter.
[17179609.408000] flexcop-pci: card revision 2
[17179609.408000] PCI: Enabling device 0000:02:0e.0 (0004 -> 0007)
[17179609.408000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 18 (level, low) -> IRQ 217
[17179609.424000] DVB: registering new adapter (FlexCop Digital TV device)
[17179609.424000] b2c2-flexcop: MAC address = 00:d0:d7:30:15:0f
[17179609.424000] b2c2-flexcop: i2c master_xfer failed
[17179609.576000] PCI: Enabling device 0000:02:0d.0 (0004 -> 0005)
[17179609.576000] ACPI: PCI Interrupt 0000:02:0d.0[A] -> GSI 21 (level, low) -> IRQ 193
[17179609.576000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[17179609.576000] 0000:02:0d.0: 3Com PCI 3c905 Boomerang 100baseTx at 0001d000. Vers LK1.1.19
[17179609.628000] b2c2-flexcop: i2c master_xfer failed
[17179609.628000] b2c2-flexcop: i2c master_xfer failed
[17179609.628000] nxt200x: nxt200x_readbytes: i2c read error (addr 0x0a, err == -121)
[17179609.628000] Unknown/Unsupported NXT chip: 00 00 00 00 00
[17179609.628000] b2c2-flexcop: i2c master_xfer failed
[17179609.628000] lgdt330x: i2c_read_demod_bytes: addr 0x59 select 0x02 error (ret == -121)
[17179609.628000] bcm3510: Revision: 0x1, Layer: 0xb.
[17179609.644000] b2c2-flexcop: found the bcm3510 at i2c address: 0x0f
[17179609.644000] DVB: registering frontend 0 (Broadcom BCM3510 VSB/QAM frontend)...
[17179609.644000] b2c2-flexcop: initialization of 'Air2PC/AirStar 2 ATSC 1st generation' at the 'PCI' bus controlled by a 'FlexCopIIb' complete

lspci -v produces this: 

> 0000:02:0e.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
        Subsystem: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card
        Flags: bus master, slow devsel, latency 32, IRQ 217
        Memory at db000000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at b800 [size=32]

I don't know what else to check. Please help! I am relatively new to linux so I don't know what next diagnostic steps to take.

---

### Post by unarmedninja on 2007-05-20
i have this card working on feisty fawn right now. I also had it working on 6.10.  your dmesg output looks okay its the same as mine.  Theres not much documentation for installing this card so you might have missed the part where you need the firmware file. you need to download "dvb-fe-bcm3510-01.fw" and put it in the /lib/firmware/(your kernel version) folder. you should be able to find this file on google.

you will need to get azap to test the card. I think this is only available in the cvs version of dvb-apps.  Im not sure where the command is but you will need to install cvs from synaptic and 'build-essentials' to compile. Once its installed you can follow the instructions on the linuxtv.org website, its pretty well documented there. 

currently i use azap to tune channels, vlc player to view them and dvbstream to record to .ts file.

---

### Post by gizzard on 2007-05-21
Thanks for your reply! I already had the firmware file in the appropriate directory, but thanks for the suggestion. I installed CVS via Synaptic and was able to compile and install dvb-apps that way. I was also successfully able to use dvbscan to build a channels.conf file, which I copied to my .azap, .xine, and .tvtime directories, but I can't seem to view any video using any of these applications. For example, if I run xine dvb://"WBRC DT" I get -xine engine error- there is no input plugin available to handle 'dvb://WBRC DT'. I have a bunch of plugins in /usr/lib/xine/ but none in my ~/.xine/. Is the syntax I am using correct?

---

### Post by unarmedninja on 2007-05-21
the way i do it is with azap, dvbstream and vlc player or mplayer.  I would recommend these players over xine.
first you will need to lock channel with azap.
> 
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
tuning to 509000000 Hz
video pid 0x001f, audio pid 0x0023
status 00 | signal ffff | snr 0000 | ber 00000000 | unc 00000000 | 
status 1f | signal ffff | snr 6c56 | ber 00000000 | unc 00000032 | FE_HAS_LOCK
status 1f | signal ffff | snr 6e27 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal ffff | snr 6e27 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status 1f | signal ffff | snr 6d02 | ber 00000000 | unc 00000000 | FE_HAS_LOCK


then you can use vlc player easily with one command.
> 
vlc dvb://

this will display the current channel that is locked.

to use mplayer it is a little different, you will need to get the video and audio pids of the channel.
after you lock a channel with azap you will need to run scan.
> 
scan -c

using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
service is running. Channel number: 5:1. Name: 'CBC Toronto High Definition Television'
dumping lists (1 services)
CBC Toronto High Definit (0x0003) 00: PCR == V   V 0x0031 A 0x0034 (eng) 0x0035 (eng) 0x0034 (eng) 0x0035 (eng)
Done.


the pids are in hex, you will need to convert them to decimal. (the video pid above is 49 and the audio is 52). you only need one audio pid. to play it in mplayer use the following.

> 
dvbstream -ps 49 52 -o | mplayer -cache 1024 -


in the above the -ps converts the stream to PS format which mplayer requires.  The actual format of a ATSC stream is in TS format.  the first number is the video pid and the second one is the audio pid. -o tells it to output to stdout. mplayer can take more parameters, you can look those up on google.

to record to a file i use
> 
dvbstream 8192 -o > outputfile.ts


To simply things i wrote my own shell scripts to do all this for me, so you dont really need to remember all these commands.  Im sure theres other ways of doing this but I find this way to be pretty straight forward.

---

### Post by gizzard on 2007-05-22
Great! Thanks so much. I wanted to use xine for the XvMC support, but vlc works ok. I didn't realize you had to run azap to lock the channel, stop azap, and then start vlc (otherwise vlc complains the device is in use).

---

### Post by unarmedninja on 2007-05-22
sorry I forgot to mention about the killing azap before you launch any player but at least you figured it out. if you really want to use XvMC mplayer does support it. you just need to use these parameters (assuming you have xvmc installed properly)
> 
mplayer vo=xvmc,xv vc=ffmpeg12mc,


this actually gives me worse performance so I dont use it but you can try it out if you want. you probably need to mess around with the parameters in mplayer to get the best results. deinterlacing also causes a big performance loss so i just stick with the interlaced 1080i output since it still looks pretty good.

---

