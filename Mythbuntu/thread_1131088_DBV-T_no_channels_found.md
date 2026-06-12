---
title: "DBV-T no channels found"
date: 2009-04-20
forum: Mythbuntu
---

### Post by Chris Musampa on 2009-04-20
Hi Gurus,
I have a Nebula DigiTV PCI card which was working fine with Hardy, after a hard drive failure I decided to give Jaunty a go.

The card is detected but no channels are found in either backend setup or in kaffeine.  

I've left a spare partition on the new drive so can put hardy on there if needed but would rather get this working if possible.  I've never had this problem in either gutsy or hardy so don't know where to start.

Your help would be greatly appreciated.



lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:09.0 Ethernet controller: Accton Technology Corporation EN-1216 Ethernet Adapter (rev 11)
00:0c.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
00:0c.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

```

---

### Post by Chris Musampa on 2009-04-20
A little more info, hope its of use:
Having installed dvbutils a scan gives the following

scan /usr/share/dvb/dvb-t/uk-WinterHill     
```
                                                                                     
scanning /usr/share/dvb/dvb-t/uk-WinterHill                                                                                                    
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'                                                                             
initial transponder 754167000 0 3 9 1 0 0 0                                                                                                    
initial transponder 834167000 0 2 9 3 0 0 0                                                                                                    
initial transponder 850167000 0 2 9 3 0 0 0                                                                                                    
initial transponder 842167000 0 3 9 1 0 0 0                                                                                                    
initial transponder 786167000 0 3 9 1 0 0 0
initial transponder 810167000 0 3 9 1 0 0 0
initial transponder 650000000 0 3 9 1 0 0 0
initial transponder 626000000 0 3 9 1 0 0 0
>>> tune to: 754167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
__tune_to_transponder:1516: ERROR: FE_READ_STATUS failed: 121 Remote I/O error

```
(last line repeated many times)

A google of the above error gave few english results and none which gave me any clue.

---

### Post by Chris Musampa on 2009-04-21
Well I installed hardy on the spare partition and it works no problem so I guess that confirms this as a jaunty issue.

Although I now have a working myth box again (phew!) it would still be useful to troubleshoot the jaunty install if possible.  If anyone has any pointers feel free to chime in, cheers.

---

### Post by virgo17 on 2009-05-15
I have exactly the same problem with the same card. In my case I swapped the card for an old Winfast DVT1000T and it works perfectly.

Looks like the Nebula driver is borked in Jaunty.

---

### Post by ian dobson on 2009-05-15
Hi,

Could it be a missing/corrupt firmware problem?

Do you see and error messages in dmesg?

Regards
Ian Dobson

(I'm sticking with 8.10 as long as I can, the old saying is "Never change a running system")

---

### Post by Chris Musampa on 2009-05-15
I went back to hardy until the card died (pretty sure its hardware) a week later.  I replaced it with a Hauppauge Wintv Nova TD-500 and switched back to jaunty, all is good.

Edit: I came across this the night before it died [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366606](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366606)

---

### Post by virgo17 on 2009-05-15
> **ian dobson said:**
> Hi,

Do you see and error messages in dmesg?



The reports in dmesg seemed normal to me, with no obvious errors. I just spent an hour or two reinstalling 8.10 and the Nebula card is working fine now. Because of this I can no longer see the dmesg for the Jaunty installation as I used the same hard disk for the new installation.

Looking on Google shows a few people have the same problem and Ubuntu have it listed as a bug.

Pity really because the Nebula is IMHO a better card than the Winfast and I would like to be running Jaunty.

I'm sure it will be sorted eventually.

---

