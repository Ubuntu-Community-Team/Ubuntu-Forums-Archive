---
title: "Mythbuntu noob - no LiveTV, setup problem?"
date: 2011-02-10
forum: Mythbuntu
---

### Post by floh-511 on 2011-02-10
Hey,

first of all I have to say that I am a total Linux newbie. I installed Mythbuntu 10.10 on my brand new HTPC that I built up using an Asus IonT5 board and a cineS2 DVB-S2 satellite tuner card. The system runs on a 64 GB SSD, and contains a Bluray-ROM drive. That´s it.

I´ve solved some of my problems already, such as getting digital audio to work. XBMC runs just fine, plays HD content, and the remote worked out of the box. I even managed to mount the drives of my fileserver (not permanently at startup, but that´s another issue).
God, it´s been 15 years since I sat before a black screen typing commands into a terminal window ;-)

I have also installed the firmware and driver for my TV card as described here:
[http://www.linuxtv.org/wiki/index.php/Linux4Media_cineS2_DVB-S2_Twin_Tuner](http://www.linuxtv.org/wiki/index.php/Linux4Media_cineS2_DVB-S2_Twin_Tuner)

I got some error messages during that install, but nothing I can make sense of (and I am currently not sitting at that system so I can´t post the console contents).

After some further reading, I also managed to insert the two input devices in the MythTV backend and connect them to video sources.
Now, starting a channel scan gives me a message like "Error: could not set parameters" or similar, and nothing happens.

What should I do now?
1. I would like to check with different software for LiveTV whether the problem is my tuner hardware or MythTV configuration, but I have not found any other application for LiveTV.
2. Plugging the sat cable into my standalone tuner gives me television, so nothing wrong on the dish end.
3. Reinstall Mythbuntu?
4. Go back to an older release?
5. Something I haven´t thought of?

---

### Post by P4man on 2011-02-10
A quick test to see if the tuner is working, is using VLC. Install VLC, run it and open a capture device.  DVB should be listed, see if it produces a signal

---

### Post by floh-511 on 2011-02-10
VLC is installed, I didn´t know it could capture video.
Good idea, thanks.

---

### Post by P4man on 2011-02-10
VLC is great. 
I tried installing myth-tv on my htpc (thats used primarly for xbmc),  but frankly, despite weeks of trying, I failed. Couldnt get it to work. The closest I got was a distorted video with no sound.

in the end, I just used VLC to stream the tv to my other PCs. VLC cant only capture, it can stream and optionally recode on the fly as well. The only problem with that is changing channels needs to be done through a command on the HTPC, so I need to SSH in and run something like 

ivtv-tune -f206.25 /dev/video0

to switch channels.(I got an analogue tuner). I may write a little app to do that as I cant find any, but other than that it works great for mne, unlike myth, which Ive given up on. Dont let that discourage you though, its great if you can get it to work :)

---

### Post by floh-511 on 2011-02-10
yeah, from reading all the forums that I could find the current subtotal is "MythTV is great, but a pain to set up".
So far I haven´t been able to test claim no.1, but I´ll sign off on claim no.2.

---

### Post by floh-511 on 2011-02-10
welll... VLC doesn´t work either. Maybe I don´t know which frequencies I have to input, but I get the error message: "VLC cannot open MRL 'dvb:frequency=xxxx'

I opened the case again and supplied power to the tuner card since I read in another forum that this might be the reason. Fully expected everything to work now, but no cigar.

This is what I get from sudo lspci -vvnn :
0b:00.0 Multimedia video controller [0400]: Micronas Semiconductor Holding AG Device [18c3:0720] (rev 01)
    Subsystem: Micronas Semiconductor Holding AG Device [18c3:dd00]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at fbff0000 (32-bit, non-prefetchable) [size=64K]
    Region 1: Memory at fbfe0000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [58] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr+ NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s, Latency L0 unlimited, L1 unlimited
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [100 v1] Device Serial Number 00-00-00-00-00-00-00-00
    Capabilities: [400 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
            Status:    NegoPending- InProgress-
    Kernel driver in use: ngene
    Kernel modules: ngene

when trying to install Driver, I get (for command "make"):
make -C /home/florian/v4l-dvb/v4l 
make[1]: Entering directory `/home/florian/v4l-dvb/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/florian/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/florian/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/florian/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/florian/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.35-22-generic/build
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/florian/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/florian/v4l-dvb/v4l/firedtv-1394.o
/home/florian/v4l-dvb/v4l/firedtv-1394.c:22: fatal error: dma.h: No such file or directory
compilation terminated.
make[3]: *** [/home/florian/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/florian/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/florian/v4l-dvb/v4l'
make: *** [all] Error 2

While "make install" seems to work:

make -C /home/florian/v4l-dvb/v4l install
make[1]: Entering directory `/home/florian/v4l-dvb/v4l'
-e 
Removing obsolete files from /lib/modules/2.6.35-22-generic/kernel/drivers/media/video:
-e 
Removing obsolete files from /lib/modules/2.6.35-22-generic/kernel/drivers/media/dvb/cinergyT2:
-e 
Removing obsolete files from /lib/modules/2.6.35-22-generic/kernel/drivers/media/common:
-e 
Removing obsolete files from /lib/modules/2.6.35-22-generic/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.35-22-generic/kernel/drivers/media/:
/sbin/depmod -a 2.6.35-22-generic 
make -C firmware install
make[2]: Entering directory `/home/florian/v4l-dvb/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/home/florian/v4l-dvb/v4l/firmware'
make[1]: Leaving directory `/home/florian/v4l-dvb/v4l'

Is there anyone who can make sense of this and maybe tell me what I am doing wrong (write permissions?)

MythTV backend still claims the card is not connected and gives me "Error parsing parameters" when I try to scan.

EDIT: I would like to try importing a channels.conf for German Astra satellite. Can anyone help me out with such a file?

---

### Post by AlecJ on 2011-02-11
In the backend do you see your card listed?
did you select LNB for both cards?
The frequency's are added in Hz so 8 digits?

---

### Post by floh-511 on 2011-02-18
Well, here's an update.
I did not have LNBs connected to the capture cards. I finally found this in a guide on the web, but I have to say the documentation should point this out since more and more people are using DVB-S (digital satelllite TV). It doesn't say ANYTHING but "UNCONNECTED" and what's more, even sat noobs expect NOT to need Disecq since most associate this with motorized dish control (not setting up your LNB) so it never crosse my mind to look in there (and when I did, it said "unconnected" which I took to be an error message).

Please people, this software is hard enough to set up without making people GUESS what to do ;-)

I would never have thought of highlighting "unconnected" and then pressing OK to bring up the selection menu...

So I can scan for channels and pretty much everything I need is found.

LiveTV still doesn't work though, but I will post that in a new thread since this issue is basically solved.

Thanks to linuxtv.org, check that for good answers about hardware which works and is supported by Linux, and to whoever wrote the step-by-step setup guide for satellite TV in Mythbuntu

---

