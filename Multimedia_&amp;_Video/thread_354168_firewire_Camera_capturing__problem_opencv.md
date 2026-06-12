---
title: "firewire Camera capturing  problem opencv"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by fan_ubu on 2007-02-05
Hi all,

I have installed opencv 1.0 in Ubuntu 6.10, but when i try to run some
of the examples that import video from my camera (dv using firewire)
(e.g lkdemo) it doesn't work and I have the following message

Could not initialize capturing...

My camera works with Kino when I use /dev/dv1394/0
but not when I use /dev/raw1394

Moreover I can capture with dvgrab and
gscanbus also works,

when i do testlibraw it says:

current generation number: 1
1 card(s) found
nodes on bus: 2, card name: ohci1394
using first card found: 2 nodes on bus, local ID is 1, IRM is 1

doing transactions with custom tag handler
trying to send read request to node 0... completed with value 0xa995bae2
trying to send read request to node 1... completed with value 0x3fb8bae2

using standard tag handler and synchronous calls
trying to read from node 0... completed with value 0xfe3bbce2
trying to read from node 1... completed with value 0xe159bce2

testing FCP monitoring on local node
got fcp command from node 1 of 8 bytes: 01 23 45 67 89 ab cd ef
got fcp response from node 1 of 8 bytes: 01 23 45 67 89 ab cd ef
testing config rom stuff
get_config_rom returned 0, romsize 120, rom_version 5
here are the first 10 quadlets:
0. quadlet: 0x1de50404
1. quadlet: 0x34393331
2. quadlet: 0x32a264e0
3. quadlet: 0x014c0000
4. quadlet: 0x562b0007
5. quadlet: 0x05390400
6. quadlet: 0x4c000003
7. quadlet: 0x03000081
8. quadlet: 0x090000d1
9. quadlet: 0xc083000c
update_config_rom returned 0

polling for leftover messages

when i do sudo lsmod |grep 1394


video1394 20184 0
dv1394 22104 0
raw1394 30584 0
ohci1394 37040 2 video1394,dv1394
ieee1394 306104 5 sbp2,video1394,dv1394,raw1394,ohci1394


Do I have to do something extra to setup up the firewire support?
May be I am missing something....


any help is highly appreciated,

many thanks

---

### Post by markedman on 2007-02-13
Is the provided OpenCv package compiled against ffmpeg?

---

