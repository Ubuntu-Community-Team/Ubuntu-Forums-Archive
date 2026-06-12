---
title: "Hauppauge NOVA-S Plus no channel scan under 0.23 after upgrade"
date: 2011-05-28
forum: Mythbuntu
---

### Post by MartinusEx on 2011-05-28
Folks,

I upgradet from Mythbuntu 8.04/mythtv0.21 to mythbuntu10.04/mythtv0.23

I'm having problems with mythconverg but partially could get rid of it.
My settings are all blown so I need to set up the box.

First of all set up the DVB-S card which worked fine until the upgrade
and define the video input.
When at last I try to scan for channels nothing works.

In the end I tried :
"complete scan of all known transponders"
this fails witherror messages:
"Error when setting transponder frequency"
"Programming error : tune ready not handled"
Both messages are in German, 
I tried to translate as best as I'm able to.

dmesg seems to show all is OK...
```

[   36.341850] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[   36.342716] cx88[0]: subsystem: 0070:9202, board: Hauppauge Nova-S-Plus DVB-S [card=37,autodetected], frontend(s): 1
[   36.342721] cx88[0]: TV tuner type 4, Radio tuner type -1
[   36.343085] lp0: using parport0 (interrupt-driven).
[   36.420081] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   36.456837] cx2388x alsa driver version 0.0.7 loaded
[   36.483592] psmouse serio1: ID: 00 00 3c
[   36.508630] tveeprom 0-0050: Hauppauge model 92001, rev B1B1, serial# 248136
[   36.508636] tveeprom 0-0050: MAC address is 00-0D-FE-03-C9-48
[   36.508641] tveeprom 0-0050: tuner model is Conexant_CX24109 (idx 111, type 4)
[   36.508647] tveeprom 0-0050: TV standards ATSC/DVB Digital (eeprom 0x80)
[   36.508652] tveeprom 0-0050: audio processor is CX883 (idx 32)
[   36.508656] tveeprom 0-0050: decoder processor is CX883 (idx 22)
[   36.508661] tveeprom 0-0050: has no radio, has IR receiver, has no IR transmitter
[   36.508665] cx88[0]: hauppauge eeprom: model=92001
[   36.553707] input: cx88 IR (Hauppauge Nova-S-Plus  as /devices/pci0000:00/0000:00:0c.2/input/input4
[   36.553902] cx88[0]/2: cx2388x 8802 Driver Manager
[   36.553927]   alloc irq_desc for 18 on node -1
[   36.553931]   alloc kstat_irqs on node -1
[   36.553944] cx88-mpeg driver manager 0000:00:0c.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   36.553957] cx88[0]/2: found at 0000:00:0c.2, rev: 5, irq: 18, latency: 64, mmio: 0xf7000000
[   36.553964] IRQ 18/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   36.554086] cx8800 0000:00:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   36.554101] cx88[0]/0: found at 0000:00:0c.0, rev: 5, irq: 18, latency: 165, mmio: 0xf5000000
[   36.554116] IRQ 18/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   36.554215] cx88[0]/0: registered device video0 [v4l2]
[   36.554271] cx88[0]/0: registered device vbi0
[   36.554934] cx88_audio 0000:00:0c.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   36.554948] IRQ 18/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   36.554997] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   36.594596] Console: switching to colour frame buffer device 80x30
[   36.631761] logips2pp: Detected unknown logitech mouse model 115
[   36.642227] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   36.642236] cx88/2: registering cx8802 driver, type: dvb access: shared
[   36.642245] cx88[0]/2: subsystem: 0070:9202, board: Hauppauge Nova-S-Plus DVB-S [card=37]
[   36.642252] cx88[0]/2: cx2388x based DVB/ATSC card
[   36.642257] cx8802_alloc_frontends() allocating 1 frontend(s)
[   36.678808] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   36.714789] CX24123: detected CX24123
[   36.735221] DVB: registering new adapter (cx88[0])
[   36.735234] DVB: registering adapter 0 frontend 0 (Conexant CX24123/CX24109)...

```

Ian Dobson provided a srcript to check mythbuntu which I ran, this is the output:
```

--.No command line options defined trying mysql.txt
--.Try /home/martin/bin/checkmythtv.pl -H for help
--.Looking for Database information in /usr/local/share/mythtv/mysql.txt
--.Looking for Database information in /usr/share/mythtv/mysql.txt
--.Looking for Database information in /etc/mythtv/mysql.txt
--.Found configuration file /etc/mythtv/mysql.txt
--.Looking for Database information in /usr/local/etc/mythtv/mysql.txt
--.Looking for Database information in /home/user/.mythtv/mysql.txt
--.Found configuration file /home/user/.mythtv/mysql.txt
--.Looking for Database information in mysql.txt
-- Using HostName 'MCE', DatabaseHost 'localhost', SQLUserName 'mythtv', SQLPassword 'xxx'
--.Checking configuration for host 'MCE' script running on host 'MCE'
OK .Found 1 video sources
OK .Videosource 1 'VIDEO' has a EPG source defined (eitonly)
OK .Videoinput 1 has 1 card inputs defined
-- .Checking start channel for each cardinput
!! .Cardinput (1) Start channel (Bitte Send)invalid
-- .Checking channel change script for each cardinput
OK .All InputCards are linked to a videosource
!! .Videosource 1 does not appear to have any channels defined
OK .cardinput 1 type DVB exists as device (/dev/dvb/adapter0/frontend0), file permissions are 0660 (rw- rw- ---) owner (root) group (video)
OK .All channels have a valid videosource
OK .All dtv_multiplex channels have a valid videosource
OK .All channel entries have a valid dtv_multiplex
OK .All dtv_multiplex entries have a valid channel
OK Found 1 storage groups for 'MCE'
OK.Storage group 'Default' exists in file system at (/home/mythtv/Video/)

```


All I can assume is that somehow the DVB card is locked by another program or mythtv reveals a bug.

Totally out of ideas.
Every suggestion is appreciatet

THX

Martin

---

### Post by MartinusEx on 2011-06-25
All right, no reply on this means no one encounterd this very problem?!

Still my mythtv is not able to scan my DVB-S card althoug it is visible.
System is Mythbuntu 10.04 and (now) mythtv 0.24

I now want to go for a clean install of mythbuntu/mythtv

Is there a wiki available what I need to deinstall before I can do a clean install.

I would like to select a certain package to deinstall all the stuff.
but just checkmarking mythtv doesn't do the trick and there are a lot of packages that relate to mythbuntu/mythtv.

Shall I deinstall every package which has  the "myth" incorporated?
Would I destroy my system?
How deep is it nested?


Thanks for your support

Martin

---

### Post by MartinusEx on 2011-10-10
I replaced the existing system by mythbuntu 11.04 / mythtv 024.
Still no scanning.

So I built a channels.conf via scan und fed this to mythtv instead of letting it scan all channels by itself..
This solved the issue.

---

### Post by MartinusEx on 2011-11-05
Using channels.conf opens up another issue.
EIT/EPG data does not work which is a nasty one.

A video source once worked with channels.conf can tune the card, but no EPG/EIT is possible.

Trying a fresh video source still tells me that mythtv is not able to tune the DVB-S card.

Any ideas available in the forum?

THX

Martin

---

