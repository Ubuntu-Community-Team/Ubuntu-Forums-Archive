---
title: "Problems with linuxtv drivers and Hauppauge WinTV HVR-1800"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by tsm1723 on 2008-01-13
Hi,

I recently bought a Hauppauge WinTV HVR-1800 for use in a Gutsy (7.10 x86) MythTV setup. According to [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800) the digital (but not analog) capabilities of this card are already supported by the linuxtv.org drivers, but since I'm using kernel 2.6.22-14-generic, it was necessary to manually install the drivers. Following the advice at [http://ubuntuforums.org/showthread.php?t=550276&highlight=hvr1800](http://ubuntuforums.org/showthread.php?t=550276&highlight=hvr1800) I used:

```
sudo apt-get install mercurial

mkdir v4l_source

cd v4l_source

hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb

make & make install
```

to install the drivers and after a reboot the card was recognized by the system:

[dmesg output]

```
[   33.826082] Linux video capture interface: v2.00
[   33.848515] cx23885 driver version 0.0.1 loaded
[   33.848802] ACPI: PCI Interrupt Link [AXV6] enabled at IRQ 16
[   33.848804] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [AXV6] -> GSI 16 (level, low) -> IRQ 21
[   33.848812] CORE cx23885[0]: subsystem: 0070:7801, board: Hauppauge WinTV-HVR1800 [card=2,autodetected]
[   34.007624] cx23885[0]: i2c bus 0 registered
[   34.007771] cx23885[0]: i2c bus 1 registered
[   34.007826] cx23885[0]: i2c bus 2 registered
[   34.034320] tveeprom 2-0050: Hauppauge model 78521, rev C1E9, serial# 2967483
[   34.034323] tveeprom 2-0050: MAC address is 00-0D-FE-2D-47-BB
[   34.034324] tveeprom 2-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   34.034326] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   34.034328] tveeprom 2-0050: audio processor is CX23887 (idx 42)
[   34.034329] tveeprom 2-0050: decoder processor is CX23887 (idx 37)
[   34.034330] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   34.034332] cx23885[0]: hauppauge eeprom: model=78521
[   34.034383] cx23885[0]/0: registered device video0 [v4l2]
[   34.034385] cx23885[0]: cx23885 based dvb card
[   34.097313] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   34.097316] ACPI: PCI Interrupt 0000:00:0f.1[B] -> Link [AAZA] -> GSI 20 (level, low) -> IRQ 20
[   34.097327] PCI: Setting latency timer of device 0000:00:0f.1 to 64
[   34.115918] MT2131: successfully identified at address 0x61
[   34.115921] DVB: registering new adapter (cx23885[0])
[   34.115923] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   34.116346] cx23885_dev_checkrevision() Hardware revision = 0xb1
[   34.116352] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 21, latency: 0, mmio: 0xcfc00000
[   34.116357] PCI: Setting latency timer of device 0000:03:00.0 to 64

```

[partial lsmod output]

```
cx23885                68336  1 
snd_seq_midi            9600  0 
videodev               29184  1 cx23885
v4l2_common            19200  2 cx23885,videodev
v4l1_compat            15364  1 videodev
compat_ioctl32          2304  1 cx23885
btcx_risc               5896  1 cx23885
snd_rawmidi            25728  1 snd_seq_midi
tveeprom               16912  1 cx23885
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
videobuf_dvb            7812  1 cx23885
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dvb_core               80668  1 videobuf_dvb
nvidia               6221648  34 
xpad                    9988  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                35016  1 nvidia
videobuf_dma_sg        14852  2 cx23885,videobuf_dvb
videobuf_core          19460  3 cx23885,videobuf_dvb,videobuf_dma_sg

```

It also created the following device files:

```
# ls -l /dev/dvb/adapter0/
total 0
crw-rw---- 1 root video 212, 4 2008-01-12 23:43 demux0
crw-rw---- 1 root video 212, 5 2008-01-12 23:43 dvr0
crw-rw---- 1 root video 212, 3 2008-01-12 23:43 frontend0
crw-rw---- 1 root video 212, 7 2008-01-12 23:43 net0

```

However, when I try to use the "scan" utility to scan for chennels, I get the following output:

```
# scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-CA-SF-Bay-Area
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-CA-SF-Bay-Area
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy
```

can anyone offer advice on how to fix this?

Thanks

---

### Post by elcapuchino on 2008-01-13
I have the same problem, I followed the instructions at :
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV_Nova-T_500_PCI)
wich is similar to what you've done and it doesnt work...

WinTV-HVR-1800 has the same driver file _dvb-usb-dib0700-1.10.fw_

"dmesg | grep tv" gives me : 

[46904.157689] ivtv:  Start initialization, version 1.2.0
[46904.158606] ivtv:  End initialization
[46904.245049] bttv: driver version 0.9.17 loaded
[46904.245053] bttv: using 8 buffers with 2080k (520 pages) each for capture
[46907.786815] usbcore: registered new interface driver stv680
[46907.787171] /home/myself/v4l-dvb/v4l/stv680.c: [usb_stv680_init:1553] STV(i): usb camera driver version v0.25 registering
[46907.787174] /home/myself/v4l-dvb/v4l/stv680.c: STV0680 USB Camera Driver v0.25
[46907.818215] usbcore: registered new interface driver dvb_usb_digitv
[46908.136365] ivtvfb:  no cards found<6>usbcore: registered new interface driver ultracam

I get device /dev/video0 but no /dev/dvb folder
when I scan video0, I get the same problem :

scanning video0
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

hauppage are not ubuntu friendly....

If you have more clues, I could need help too...
:confused:

---

### Post by tsm1723 on 2008-01-13
Hi,

I'm still working on this and searching various forums, but so far I haven't had any luck. I'll post here if I make any breakthroughs, though it sounds like your problem is slightly different since your /dev/dvb files are actually missing and not just busy. I think I saw something on a linuxtv forum about needing to use mknod to manually create these devices in some cases - you might want to look into that.

In the meantime - suggestions, anyone?

---

### Post by tsm1723 on 2008-01-15
Still no progress... Any ideas?

Thanks

---

### Post by chuck2 on 2008-01-16
I cant even get the cx23885 to compile, it compiles a bunch of other modules though, but not that one.

---

### Post by raider6 on 2008-01-17
Could someone please tell me why I can't get cx23885 to compile, everything else builds but this one module. I downloaded the linuxtv mercurial and followed the instructions.
 amd64 2.2 ubuntu 7.10 64bit. I cannot find any errors.

---

### Post by Blaze1024 on 2008-01-17
I feel your pain!! I have the same card "HVR-1800" I bought it because it was listed as supported  BULL !!!!

 I have been working on trying to get this card up and running for 2 weeks so far no luck I think it's time they list this card as unsupported. 

 Sometimes I really wonder why I put up with Linux. I have been trying to build a Mythtv box for over a month now and have had nothing but problems. Windows MCE  is starting to look really promising, at least it works!

Over the last 4 weeks I have bought 3 motherboards 4 video cards 3 different brands of ram and a grand total of 8 "that's right eight HDTV tuners " all to get something that resembles a working MythTV box.

So far the only HDTV tuner that worked was the USB HVR-950. I tried a pcHDTV card and it's reception SUCKED. Channels that my HDTV had no problems tuning could not be tuned with the PCHDTV card The PCHDTV card could only tune 2 out of 8 local HD channels, the HVR-950 was slightly better at 4 and my TV flawlessly tunes 8. 

In Windows  HVR-1800 manages to tune all 8 local HDTV stations.  

It's real frustrating to have a product that works perfectly out of the box in Windows. Yet have to spend weeks trying to get the same product to work in Linux ARGGGGGGGG.

Hopefully someone can come up with a solution to this problem

---

### Post by chuck2 on 2008-01-17
heres what i dug up so far
[http://linuxtv.org/pipermail/linux-dvb/2008-January/022965.html]("http://linuxtv.org/pipermail/linux-dvb/2008-January/022965.html")

I did what they said (ran sudo make menuconfig, and unchecked the radio stuff)  and it built the drivers

---

### Post by MrLaister on 2008-01-18
Hi,

I have just been through something very similar, it turned out that the firmware was incompatible and a newer version fixed it.

Are you still having problems with the error device not ready? if so i'll go through what I did for you

MrL

---

### Post by tsm1723 on 2008-01-21
Hi MrL,

Yes, I still have the same issue with the device being in use. I'd appreciate any advice you can offer about fixing this.

Thanks

---

### Post by breaking on 2008-01-26
```

# scan uk-divis
scanning uk-divis
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy

```

This error plagued me for a good few hours then i ran
```
lsof /dev/dvb/adapter0/frontend0
```
to see what was causing it to report as busy

Low and behold it was the damn mythtv-backend process all along ::pulls hair out::

A simple 
```
sudo /etc/init.d/mythtv-backend stop
```
followed by
```
scan /root/.tzap/uk-region > /root/.tzap/channels.conf
```
cured the problem

Dont foget to start up mythtv-backend after this


Running on ubuntu 7.10

---

### Post by Blaze1024 on 2008-01-26
Finally success !!! :popcorn:

I finally managed to find the fix for my HVR-1800.

If you are still having problems loading modules for cx23885 based cards such as the HVR-1800 then you should try this patched  v4l-dvb tree.

[http://linuxtv.org/hg/~mkrufky/build-fix/](http://linuxtv.org/hg/~mkrufky/build-fix/)

The thread is here 

[http://linuxtv.org/pipermail/linux-dvb/2008-January/022992.html](http://linuxtv.org/pipermail/linux-dvb/2008-January/022992.html)

---

### Post by bpasham on 2008-02-24
> **Blaze1024 said:**
> Finally success !!! :popcorn:

I finally managed to find the fix for my HVR-1800.

If you are still having problems loading modules for cx23885 based cards such as the HVR-1800 then you should try this patched  v4l-dvb tree.

[http://linuxtv.org/hg/~mkrufky/build-fix/](http://linuxtv.org/hg/~mkrufky/build-fix/)

The thread is here 

[http://linuxtv.org/pipermail/linux-dvb/2008-January/022992.html](http://linuxtv.org/pipermail/linux-dvb/2008-January/022992.html)
This option worked last week but NOt anymore.
[I]"Mercurial Repositories
The specified repository "~mkrufky" is unknown, sorry. Please go back to the main repository list page."[/I]

Please help me ..

---

### Post by cenwesi on 2008-02-29
So i can't seem to get mine to work...and that site no longer exist? Can someone tell me where to get the drivers from????

---

### Post by trigg on 2008-03-01
I found this on the linuxtv.org site. I haven't tried it yet, but it might help.  Here is the link describing the card and explaining compatibility:

[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800)

Here is a link to the v4l/dvb mercurial tree:

[http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

(this replaces the original hg site listed above)

---

### Post by cenwesi on 2008-03-02
i am actually trying to get this to work with sagetv. I even tried the cat /dev/video0 > file0.mpg and it saves... When i try to load the mpg file i get error.

---

### Post by myfiddle on 2008-03-31
Hi all,
I am absolutely newbe, an I have another card (b2c2 flexcop), but I had the same problem.
I resolved making first

sudo lsof /dev/dvb/adapter0/frontend0

the result was that there was vdr running.
Stopping it with 

sudo /etc/init.d/vdr stop

the scan was successfully done.

I hope to help you.

Bye
Myfiddle

---

### Post by beartard on 2008-04-12
With this card on a fresh install of hardy, it's working out of the box.  Well, maybe I should clarify.  I used the mercurial repos earlier in the hardy development cycle.  On recent kernel upgrades, however, it seems to work fine without my intervention.  Haven't managed to get the radio capabilities working, but ATSC television is fine.  There is no analog, but no one ever claimed to support it.  Analog won't be any good after this year anyway.

---

### Post by UBBU88 on 2008-04-12
> **tsm1723 said:**
> Hi,

I recently bought a Hauppauge WinTV HVR-1800 for use in a Gutsy (7.10 x86) MythTV setup. According to [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1800) the digital (but not analog) capabilities of this card are already supported by the linuxtv.org drivers, but since I'm using kernel 2.6.22-14-generic, it was necessary to manually install the drivers. Following the advice at [http://ubuntuforums.org/showthread.php?t=550276&highlight=hvr1800](http://ubuntuforums.org/showthread.php?t=550276&highlight=hvr1800) I used:

```
sudo apt-get install mercurial

mkdir v4l_source

cd v4l_source

hg clone http://linuxtv.org/hg/v4l-dvb
cd v4l-dvb

make & make install
```


to install the drivers and after a reboot the card was recognized by the system:

[dmesg output]

```
[   33.826082] Linux video capture interface: v2.00
[   33.848515] cx23885 driver version 0.0.1 loaded
[   33.848802] ACPI: PCI Interrupt Link [AXV6] enabled at IRQ 16
[   33.848804] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [AXV6] -> GSI 16 (level, low) -> IRQ 21
[   33.848812] CORE cx23885[0]: subsystem: 0070:7801, board: Hauppauge WinTV-HVR1800 [card=2,autodetected]
[   34.007624] cx23885[0]: i2c bus 0 registered
[   34.007771] cx23885[0]: i2c bus 1 registered
[   34.007826] cx23885[0]: i2c bus 2 registered
[   34.034320] tveeprom 2-0050: Hauppauge model 78521, rev C1E9, serial# 2967483
[   34.034323] tveeprom 2-0050: MAC address is 00-0D-FE-2D-47-BB
[   34.034324] tveeprom 2-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   34.034326] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   34.034328] tveeprom 2-0050: audio processor is CX23887 (idx 42)
[   34.034329] tveeprom 2-0050: decoder processor is CX23887 (idx 37)
[   34.034330] tveeprom 2-0050: has radio, has no IR receiver, has no IR transmitter
[   34.034332] cx23885[0]: hauppauge eeprom: model=78521
[   34.034383] cx23885[0]/0: registered device video0 [v4l2]
[   34.034385] cx23885[0]: cx23885 based dvb card
[   34.097313] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   34.097316] ACPI: PCI Interrupt 0000:00:0f.1[B] -> Link [AAZA] -> GSI 20 (level, low) -> IRQ 20
[   34.097327] PCI: Setting latency timer of device 0000:00:0f.1 to 64
[   34.115918] MT2131: successfully identified at address 0x61
[   34.115921] DVB: registering new adapter (cx23885[0])
[   34.115923] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   34.116346] cx23885_dev_checkrevision() Hardware revision = 0xb1
[   34.116352] cx23885[0]/0: found at 0000:03:00.0, rev: 15, irq: 21, latency: 0, mmio: 0xcfc00000
[   34.116357] PCI: Setting latency timer of device 0000:03:00.0 to 64

```

[partial lsmod output]

```
cx23885                68336  1 
snd_seq_midi            9600  0 
videodev               29184  1 cx23885
v4l2_common            19200  2 cx23885,videodev
v4l1_compat            15364  1 videodev
compat_ioctl32          2304  1 cx23885
btcx_risc               5896  1 cx23885
snd_rawmidi            25728  1 snd_seq_midi
tveeprom               16912  1 cx23885
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
videobuf_dvb            7812  1 cx23885
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
dvb_core               80668  1 videobuf_dvb
nvidia               6221648  34 
xpad                    9988  0 
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
agpgart                35016  1 nvidia
videobuf_dma_sg        14852  2 cx23885,videobuf_dvb
videobuf_core          19460  3 cx23885,videobuf_dvb,videobuf_dma_sg

```

It also created the following device files:

```
# ls -l /dev/dvb/adapter0/
total 0
crw-rw---- 1 root video 212, 4 2008-01-12 23:43 demux0
crw-rw---- 1 root video 212, 5 2008-01-12 23:43 dvr0
crw-rw---- 1 root video 212, 3 2008-01-12 23:43 frontend0
crw-rw---- 1 root video 212, 7 2008-01-12 23:43 net0

```

However, when I try to use the "scan" utility to scan for chennels, I get the following output:

```
# scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-CA-SF-Bay-Area
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-CA-SF-Bay-Area
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2247: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 16 Device or resource busy
```

can anyone offer advice on how to fix this?

Thanks


Try this.

> apt-get install mercurial linux-headers-$(uname -r) linux-source build-essential
cd /lib/firmware
wget [http://konstantin.filtschew.de/v4l-f...irmware_v4.tgz](http://konstantin.filtschew.de/v4l-f...irmware_v4.tgz)
tar xvzf firmware_v4.tgz
hg clone [http://mcentral.de/hg/~mrec/v4l-dvb-experimental](http://mcentral.de/hg/~mrec/v4l-dvb-experimental)
cd v4l-dvb-experimental
make
make install

and for audio

> apt-get install sox

And to get audio working, in terminal type.
/usr/bin/sox -r 48000 -w -c 2 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp

---

### Post by psyguy1 on 2008-04-19
For anyone getting a 404 on the /mkrufky/build-fix link, you should find this link more helpful.  [http://linuxtv.org/hg/~mkrufky/cx23885/](http://linuxtv.org/hg/~mkrufky/cx23885/)

---

### Post by ssokolow on 2008-04-27
> **beartard said:**
> Analog won't be any good after this year anyway.

For you maybe. Here in Canada, Analog will be around until 2011.

Besides, I'd probably buy a card like that for converting old VHS tapes that were never re-released on DVD.

---

### Post by Za5od on 2008-05-05
> **ssokolow said:**
> For you maybe. Here in Canada, Analog will be around until 2011.

Besides, I'd probably buy a card like that for converting old VHS tapes that were never re-released on DVD.

Actually, in the US the switch from Analog to Digital is ONLY for broadcast TV (ie, over the air).  Cable companies are not required to make the switch.  I expect most of them don't want to, that way they can still offer the "digital/hd" experience for a premium.

So, if you have cable or satellite, and you want to watch shows on your computer, you'll most likely still need a TV card capable of analog input.  Currently I don't know if it's possible to go straight from satellite with a digital feed directly into a computer.  

Dave

---

### Post by loudnlownoma on 2008-06-12
May be a little late, but I'm using the same HVR-1800 card.  After the v4l drivers and some updates through the update manager - TVTime is now receiving a video feed from my satellite tuner through the S-Video input.  However, audio running through the composite cas doesn't seem to be coming through, and an lspci still shows the card as an unknown Conexant device.  Any special settings or changes that may need to be made to get audio working this way?

---

