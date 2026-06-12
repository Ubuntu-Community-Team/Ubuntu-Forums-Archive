---
title: "Help with mythbuntu and bttv card"
date: 2009-05-31
forum: Mythbuntu
---

### Post by a6s0lu7 on 2009-05-31
lo everyone after much googling around i gave up on trying to get a pci tv card running, and decided its time to go to the forums.

So: after starting up my mythbuntu box if i type this: dmesg i get this info on the card:
[    9.689508] Linux video capture interface: v2.00
[    9.924436] bttv: driver version 0.9.17 loaded
[    9.924447] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    9.925124] bttv: Bt8xx card found (0).
[    9.925163] bttv 0000:01:00.0: enabling device (0000 -> 0002)
[    9.925190] bttv 0000:01:00.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    9.925215] bttv0: Bt878 (rev 17) at 0000:01:00.0, irq: 11, latency: 132, mmio: 0xf4000000
[    9.925380] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[    9.925453] bttv0: gpio: en=00000000, out=00000000 in=009fc0ff [init]
[    9.994152] tveeprom 0-0050: Huh, no eeprom present (err=-6)?
[    9.994169] bttv0: tuner type unset
[    9.994177] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   10.004140] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   10.004885] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   10.005986] bttv0: registered device video0
[   10.006157] bttv0: registered device vbi0

right, so i know which card is mine so i type this:
modprobe -r bttv
modprobe -r tuner
modprobe bttv card=72 tuner=44

then dmesg again and i get this: 

[ 3712.359851] Linux video capture interface: v2.00
[ 3712.422132] bttv: driver version 0.9.17 loaded
[ 3712.422145] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 3712.422309] bttv: Bt8xx card found (0).
[ 3712.422342] bttv0: Bt878 (rev 17) at 0000:01:00.0, irq: 11, latency: 132, mmio: 0xf4000000
[ 3712.422551] bttv0: using: Prolink Pixelview PV-BT878P+9B (PlayTV Pro rev.9B FM+NICAM) [card=72,insmod option]
[ 3712.422615] bttv0: gpio: en=00000000, out=00000000 in=009fc0ff [init]
[ 3712.422720] bttv0: tuner type=44
[ 3712.422731] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[ 3712.546544] All bytes are equal. It is not a TEA5767
[ 3712.546889] tuner' 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[ 3712.581714] tuner-simple 0-0060: creating new instance
[ 3712.581729] tuner-simple 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[ 3712.582525] tuner' 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[ 3712.593100] bttv0: registered device video0
[ 3712.593173] bttv0: registered device vbi0
[ 3712.593239] bttv0: registered device radio0
[ 3712.593288] bttv0: PLL: 28636363 => 35468950 .. ok
[ 3712.625024] input: bttv IR (card=72) as /devices/pci0000:00/0000:00:1e.0/0000:01:00.0/input/input4
[ 4027.816494] bttv0: unloading
[ 4027.827440] tuner-simple 0-0060: destroying instance

if i start tvtime i get a bluescreen on the program and then closes itself

if i start tvtime at a terminal i get:
videoinput: Cannot open capture device /dev/video0: No such file or directory

    Cannot allocate enough off-screen video memory.  This may be fixed by:

      1. Closing or restarting large X applications.
      2. Lowering the input width of tvtime (--inputwidth parameter).
      3. Lowering your colour depth or highest configured resolution.
      4. Increasing the amount of video memory in your X config file
         (for example, if you are using the i810 XFree86 driver.)

    See [http://tvtime.net/](http://tvtime.net/) for more information.

on folder /dev there is really video0

another thing, everytime i type modprobe... i get the warning: 
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

Can any1 plz help me? :)

btw im fairly new to linux. thx

---

### Post by ian dobson on 2009-06-01
Hi,

What PCI TV card is it? Manufacturer etc.

The modprobe error comes as  /etc/modprobe.d/oss-compat does not have the .conf extension. So just rename /etc/modprobe.d/oss-compat to /etc/modprobe.d/oss-compat.conf

Regards
Ian Dobson

---

### Post by a6s0lu7 on 2009-06-04
hello Ian, and thanks for u reply :)

I got my tvcard to work with tvtime now. :) the card i have is a pixelview playTV pro2, i tried a configuration with card=139 tuner=65 and its working great now.

But unfortunately i havent run out of problems, right now i cant use my TV within MYTHBUNTU, and i have some strange behaviour with tvtime.

Basicaly, i went to Mythbuntu, to MythTV settings, on capture cards i set mine to use V4L, the cards shows there, all good. then i go into "input connections", and i select the option for television, on video source it says NONE and there nothing else i can change to, so im stuck without a signal.

Regarding the strange behaviour with tvtime: i can get tvtime to work but it cant be as a Root. everytime i try to run it as root it says: "videoinput: Cannot open capture device --device=/dev/video0: No such file or directory
xvoutput: Out of memory."
But i can run it without a problem with my user alone.
Is this normal?? cause i dont think it is........ this sounds very strange to me.

Can any help me plz.

tyvm

edit: i dont really want to run tvtime as root, its just i think that behaviour might be influencing Mythbuntu....

---

### Post by a6s0lu7 on 2009-06-05
problem has been fixed, dunno how but on root tvtime settings device was: V4Ldevice="--device=/dev/video0".
i juste removed the  --device and its gd now.

On myth i got the card to work too, there was going on some really heavy distraction in me since i was moving from step 2 to 4 on mythbuntu setup.

for it seems im out of problems...

---

