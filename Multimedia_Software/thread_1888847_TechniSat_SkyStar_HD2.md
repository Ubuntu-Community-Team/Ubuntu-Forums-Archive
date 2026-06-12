---
title: "TechniSat SkyStar HD2"
date: 2011-11-30
forum: Multimedia Software
---

### Post by aasgaa on 2011-11-30
I have the following running Tvheadend installation:
•    Ubuntu server 10.04 (Lucid Lynx)
•    Kernel version 2.6.32-33-generic-pae
•    KNC1 TV-Station DVB-C Plus card

I have now for several days tried to add a ”TechniSat SkyStar HD2” card (DVB-S/S2) and make it work - without any success so far.

*lspci –v* gives me the following output:
02:02.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)
        Subsystem: Device 1ae4:0003
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 32 (2000ns min, 63750ns max)
        Interrupt: pin A routed to IRQ 9
        Region 0: Memory at fc7ff000 (32-bit, prefetchable) [size=4K]

As you can see there is no driver loaded. Anyone out there who can help?
Thanks!

---

### Post by Lampi on 2011-11-30
There is a ppa for lucid that will support the skystar hd2 card - it's from the yaVDR team

```
sudo add-apt-repository ppa:yavdr/stable-vdr
sudo apt-get update
sudo apt-get install v4l-dvb-dkms
sudo reboot
```
the card itself is supported from kernel 2.6.33, but it misses an important patch for reliable tuning that will make it into kernel 3.2.

try the ppa and v4l-dvb-dkms, it offers all you need for that card

---

### Post by aasgaa on 2011-11-30
Lampi, thanks a lot for a very quick solution. Now the driver is loaded:

lspci –v gives the following output:
02:02.0 Multimedia controller: Twinhan Technology Co. Ltd Mantis DTV PCI Bridge Controller [Ver 1.0] (rev 01)
        Subsystem: Device 1ae4:0003
        Flags: bus master, medium devsel, latency 32, IRQ 24
        Memory at fc7ff000 (32-bit, prefetchable) [size=4K]
        Kernel driver in use: Mantis
        Kernel modules: mantis

Unfortunately a scan is failing.

sudo scan /usr/share/dvb/dvb-s/Astra-19.2E > channels.conf

scanning /usr/share/dvb/dvb-s/Astra-19.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 12551500 V 22000000 5
>>> tune to: 12551:v:0:22000
DVB-S IF freq is 1951500
WARNING: >>> tuning failed!!!
>>> tune to: 12551:v:0:22000 (tuning failed)
DVB-S IF freq is 1951500
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

Any thoughts what could be the cause for this?

---

### Post by Lampi on 2011-11-30
can you try w_scan?

---

### Post by aasgaa on 2011-11-30
w_scan -fs -cDE -sS19E2

w_scan version 20100316 (compiled for DVB API 5.1)
using settings for 19.2 east Astra 1F/1G/1H/1KR/1L
frontend_type DVB-S, channellist 6
output format vdr-1.6
Info: using DVB adapter auto detection.
main:2930: FATAL: ***** NO USEABLE DVB CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

---

### Post by Lampi on 2011-11-30
are you sure the module is loaded?

lsmod | grep mantis

will tell you if it is - if not oyu have to add mantis to /etc/modules

---

### Post by aasgaa on 2011-11-30
l[FONT=Courier New]smod | grep mantis
mantis                 19083  0
mantis_core            29327  1 mantis
dvb_core               73304  1 mantis_core
rc_core                17771  9 rc_terratec_cinergy_s2_hd,ir_lirc_codec,ir_sony_               decoder,ir_jvc_decoder,ir_rc6_decoder,mantis_core,ir_rc5_decoder,ir_nec_decoder[/FONT]

---

### Post by Lampi on 2011-11-30
weird... is your KNC1 card interfering? you know they get assigned to adapter0, adapter1, adapter2 and so on

maybe mantis is adapter1?

can you look in dmesg if you got assigned an adapter for mantis?

---

### Post by aasgaa on 2011-11-30
I have already removed the KNC1 card yesterday to eliminate possible interference.

dmesg | grep -i mantis
[    6.668159] Mantis 0000:02:02.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[    6.760394] DVB: registering new adapter (Mantis DVB adapter)
[    7.705172] input: Mantis VP-1041 IR Receiver as /devices/pci0000:00/0000:00:1c.0/0000:02:02.0/rc/rc0/input5
[    7.705268] rc0: Mantis VP-1041 IR Receiver as /devices/pci0000:00/0000:00:1c.0/0000:02:02.0/rc/rc0

---

### Post by Lampi on 2011-11-30
please try again with different w_scan parameters:

w_scan -fs -s S19E2 -X >> astra.conf

also make sure you disabled all vdr, kaffeine, mythtv whatever you use

---

### Post by aasgaa on 2011-11-30
Now something happened. I tried another scan:

$ sudo scan /usr/share/dvb/dvb-s/Astra-19.2E > channels.conf

scanning /usr/share/dvb/dvb-s/Astra-19.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 12551500 V 22000000 5
>>> tune to: 12551:v:0:22000
DVB-S IF freq is 1951500
0x0000 0x445c: pmt_pid 0x0060 ProSiebenSat.1 -- SAT.1 (running)
0x0000 0x445d: pmt_pid 0x0061 ProSiebenSat.1 -- ProSieben (running)
0x0000 0x445e: pmt_pid 0x0062 ProSiebenSat.1 -- kabel eins (running)
0x0000 0x445f: pmt_pid 0x0063 ProSiebenSat.1 -- N24 (running)
0x0000 0x4460: pmt_pid 0x0064 ProSiebenSat.1 -- SIXX (running)
0x0000 0x4461: pmt_pid 0x0065 ProSiebenSat.1 -- Sat.1 Comedy (running, scrambled)
0x0000 0x4462: pmt_pid 0x0066 ProSiebenSat.1 -- kabel eins classics (running, scrambled)
0x0000 0x4463: pmt_pid 0x0067 ProSiebenSat.1 -- SAT.1 Bayern (running)
0x0000 0x4464: pmt_pid 0x0068 ProSiebenSat.1 -- SAT.1 NRW (running)
WARNING: filter timeout pid 0x0010
dumping lists (9 services)
Done.


Trying once more:

$ sudo scan /usr/share/dvb/dvb-s/Astra-19.2E > channels.conf
scanning /usr/share/dvb/dvb-s/Astra-19.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 12551500 V 22000000 5
>>> tune to: 12551:v:0:22000
DVB-S IF freq is 1951500
WARNING: >>> tuning failed!!!
>>> tune to: 12551:v:0:22000 (tuning failed)
DVB-S IF freq is 1951500
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

---

### Post by Lampi on 2011-11-30
why do you use sudo?

add your default member to group audio and video, then it will work without sudo.

scan is unable to parse dvb-s2, that's why I recommend w_scan

---

### Post by Lampi on 2011-11-30
besides, scan will run if you use network ID scanning (Parameter -n)

---

### Post by aasgaa on 2011-11-30
Lampi, it's a pleasure working with you :-)

Your last proposal was working. w_scan has completed a long list of channels from Astra. I also tried scan afterwards – and now this is also running.

Next step will be to test together with tvheadend. 

Thanks a lot for your superb support!!

---

### Post by aasgaa on 2011-11-30
So far so good - the "Techni'Sat SkyStar HD2" is visible iin Tvheadend as "STB0899 Multistandard".

Next challenge: How to make it scan for muxes/channels?

Info from the web-interface of Tvheadend:

[SIZE=3]**Hardware**[/SIZE]
**Device path:**
/dev/dvb/adapter0
**Device name:**
STB0899 Multistandard
**Host connection:**
PCI
**Intermediate Frequency range:**
950000 kHz - 2150000 kHz, in steps of 0 kHz
**Symbolrate range**:
5000000 Baud - 45000000 Baud
**[SIZE=3]Status[/SIZE]**
**Currently tuned to:**
12,551,500 kHz Vertical (No satconf)
**Services:**
0
**Muxes:**
1
**Muxes awaiting initial scan:**
1

Any suggestions how to proceed?

---

### Post by Lampi on 2011-11-30
can't you import the list from scan or w_scan? I don't know much about Tvheadend, so I can't be of help.

---

### Post by aasgaa on 2011-11-30
Lampi, you have been a great help - thanks a lot!

I will spend some more time investigating this topic on the internet. If I do not succeed, I will post this issue as a separate Tvheadend issue...

New issue: [http://ubuntuforums.org/showthread.php?t=1888941](http://ubuntuforums.org/showthread.php?t=1888941)

---

