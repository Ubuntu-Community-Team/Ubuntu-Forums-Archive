---
title: "cx8802_timeout?"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by darlomrh on 2007-04-29
Hi

Can anyone help me solve an issue I have at the moment. I can't seem to scan for any channels on any of my DVB-T cards. I'm not sure if its :

A Motherboard issue:- (ASUS K8U-X)
A Card issue :- Leadtek Winfast DTV1000-T (x2)
Or a build issue:- Ubuntu Feisty alternate (64 bit) command line install.

When I use scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-xxxxx> /root/.tzap/channels.conf

I get WARNING: filter timeout pid xxxxx
then at the end dumped no data

lspci:

02:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
Subsystem: LeadTek Research Inc. WinFast DTV1000-T
Flags: bus master, medium devsel, latency 64, IRQ 17
Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
Capabilities: [44] Vital Product Data
Capabilities: [4c] Power Management version 2

02:05.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
Subsystem: LeadTek Research Inc. Unknown device 665f
Flags: bus master, medium devsel, latency 64, IRQ 17
Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
Capabilities: [4c] Power Management version 2 

lsmod | grep cx :
cx22702 8196 2
cx88_dvb 18564 0
cx88_vp3054_i2c 6912 1 cx88_dvb
dvb_pll 17540 3 cx88_dvb
video_buf_dvb 8580 1 cx88_dvb
cx8800 41100 0
cx8802 21508 1 cx88_dvb
cx88xx 74532 3 cx88_dvb,cx8800,cx8802
ir_common 34308 1 cx88xx
i2c_algo_bit 9608 2 cx88_vp3054_i2c,cx88xx
tveeprom 19216 1 cx88xx
compat_ioctl32 11136 1 cx8800
btcx_risc 6664 3 cx8800,cx8802,cx88xx
videodev 29824 2 cx8800,cx88xx
v4l2_common 28800 3 cx8800,compat_ioctl32,videodev
v4l1_compat 14980 2 cx8800,videodev
video_buf 29700 5 cx88_dvb,video_buf_dvb,cx8800,cx8802,cx88xx
i2c_core 26624 11 i2c_ec,cx22702,cx88_dvb,cx88_vp3054_i2c,dvb_pll,cx88xx,i2c_algo_bit,tveeprom,i2c_ali1535,i2c_ali15x3,i2c_ali1563 

dmesg:
cx88[0]/2-mpeg: cx8802_timeout (multiple times)

I'm using an aerial that is used currently on a freeview box.

Any ideas

Thanks

---

### Post by darlomrh on 2007-04-29
UPDATE

out of sheer frustration I placed one of the cards into an old K7 system using via chipset and 32bit version desktop version of Feisty.

And surprise the card scanned and locked on to channels on my local transmitter.

lsmod:

cx22702                 7300  1
cx88_dvb               16644  0
cx88_vp3054_i2c         5376  1 cx88_dvb
dvb_pll                15364  2 cx88_dvb
video_buf_dvb           7684  1 cx88_dvb
cx8800                 35212  0
cx8802                 19332  1 cx88_dvb
cx88xx                 67364  3 cx88_dvb,cx8800,cx8802
ir_common              31236  1 cx88xx
i2c_algo_bit            8712  2 cx88_vp3054_i2c,cx88xx
tveeprom               15888  1 cx88xx
i2c_core               22784  9 i2c_ec,cx22702,cx88_dvb,cx88_vp3054_i2c,dvb_pll,i2c_viapro,cx88xx,i2c_algo_bit,tveeprom
compat_ioctl32          2304  1 cx8800
btcx_risc               5896  3 cx8800,cx8802,cx88xx
video_buf              26116  5 cx88_dvb,video_buf_dvb,cx8800,cx8802,cx88xx
videodev               28160  2 cx8800,cx88xx
v4l2_common            25216  2 cx8800,videodev
v4l1_compat            15236  2 cx8800,videodev
via82cxxx              10372  0 [permanent]

Quite a few of the mods listed are smaller in size to my other pc that fails. Could this be part of the issue?
or is it a mobo issue as it seems that the K8U-X has an issue with the sound controller not being correctly identified.

Any help would be nice as I've just about had enough.:(

---

### Post by darlomrh on 2007-05-01
I get the same issue on 32bit version. I'm running out of ideas. Can **anyone** confirm they have had DVB-T cards running on the ASUS K8U-X ?
I'll take any version of ubuntu ! lol

It looks like I may have to get another board *sigh* can anyone recommend a good socket 754 mobo

thanks

---

### Post by darlomrh on 2007-05-04
After much poking around it looks like its a IRQ issue. The bizarre thing is its usually the second of the cards that will tune.

I.E.

16: IO-APIC-fasteoi libata, cx88[1], cx88[1]
21: IO-APIC-fasteoi eth0, cx88[0], cx88[0]

Its cx88[1] that will tune but not cx88[0]

Is there anyway to set the IRQ's manually or is not that simple?
surely someone has had a similar experience?

---

### Post by darlomrh on 2007-05-07
I have decided to call it a day,

In desperation I shoved both cards in my other pc ASUS A7V600 and they both tuned without issue.
So I'm off to find a new mobo that has AGP and as many PCI slots as possible.


Steer clear of the K8U-X I say :( 
cheers

---

### Post by [S2] on 2007-06-06
I have the exact same issue with an ASUS M2N-VM DH. I have one DVB-S card in it (cx88[0]) and one DVB-T (cx88[1]). The DVB-S card works like a charm, but with the DVB-T card i can't tune any channels.

```
CORE cx88[0]: subsystem: 0070:9202, board: Hauppauge Nova-S-Plus DVB-S
[card=37]

```
and

```
CORE cx88[1]: subsystem: 0070:1402, board: Hauppauge WinTV-HVR3000
TriMode Analog/DVB-S/DVB-T [card=53]

```

The Nova-S-Plus works with DVB-S, and I wanted to use the HVR3000 for DVB-T reception, as that is supported in the stock kernel (i am using the default ubuntu feisty 2.6.20 kernel).
The cable and antenna work fine, as they have no problems connected directly with the TV (DVB-T tuner build in), and the card worked with kernel 2.6.17 and Stevens hvr3000 tree in another box and connected to the same antenna cable.
The dvb-utils scan utility is unable to find channels as well.
It looks like that when kaffeine is scanning a frequecy where indeed a mux is present in my location, it prints out:

```
Using DVB device 1:0 "Conexant CX22702 DVB-T"
tuning DVB-T to 658000000 Hz
inv:2 bw:0 fecH:9 fecL:9 mod:6 tm:2 gi:4 hier:4
.... LOCKED.
Transponders: 33/63

Invalid section length or timeout: pid=17


Invalid section length or timeout: pid=0

Frontend closed
```
At the same time dmesg says:
cx88[1]/2-mpeg: cx8802_timeout
I know that on 658000000 Hz i have transponder, because the TV has a channel 
on that frequency.
It looks like I can get a lock, but the driver is somehow unable to get the 
mpeg stream?

Please help! :)

---

### Post by mhakali on 2007-11-12
Same problem, using an ASUS P5W64 PRO and have tried a ASUS P5B deluxe.

Tell me if you reached any solution. :>

---

### Post by [S2] on 2007-11-13
> **mhakali said:**
> Tell me if you reached any solution. :>

I did. I bought a Skystar 2.

---

