---
title: "DiBcom STK7070P finds channel, but TV doesn't work"
date: 2009-05-31
forum: Multimedia Software
---

### Post by lpm11 on 2009-05-31
Problem is as in the title. I use w_scan to find channel, and everything is ok, but when I try to run mplayer, there is nothing:

lukasz@lukasz-laptop:/$ mplayer dvb://TVP1
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU T2300 @ 1.66GHz (Family: 6, Model: 14, Stepping:
CPUflags: MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://TVP1.
dvb_tune Freq: 506000
<after five seconds>
TS file format detected.

and mplayer hangs(I use ctrl+c to stop). there is no window with TV.

my ~/.mplayer/channels.conf :
TVP1:506000:I999B8C999D999M999T999G999Y999:T:27500:102:104=pol;103:105:0:1:0:0:0
TVP2:506000:I999B8C999D999M999T999G999Y999:T:27500:202:204=pol;206:205:0:2:0:0:0
TVP INFO:506000:I999B8C999D999M999T999G999Y999:T:27500:302:304=pol:0:0:3:0:0:0
TVP Sport:506000:I999B8C999D999M999T999G999Y999:T:27500:702:704=pol:0:0:4:0:0:0
TVP HD:506000:I999B8C999D999M999T999G999Y999:T:27500:402:404=pol;406:0:0:5:0:0:0
(I used w_scan).

and femon output:

FE: DiBcom 7000PC (DVBT)
status       | signal 0000 | snr 0000 | ber 001fffff | unc 00000000 | 
status       | signal 0000 | snr 0000 | ber 001fffff | unc 00000000 | 
status       | signal 0000 | snr 0000 | ber 001fffff | unc 00000000 | 
status       | signal 0000 | snr 0000 | ber 001fffff | unc 00000000 | 
status       | signal 0000 | snr 0000 | ber 001fffff | unc 00000000 | 
<I lanuch mplayer here>
status SCVYL | signal ae9c | snr 0000 | ber 00001ab0 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal ae36 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal ad6c | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal ad13 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK
status SCVYL | signal ad48 | snr 0000 | ber 00000000 | unc 00000000 | FE_HAS_LOCK

My dmesg output:
 2479.476069] usb 1-2: new high speed USB device using ehci_hcd and address 11
[ 2479.609109] usb 1-2: configuration #1 chosen from 1 choice
[ 2479.609454] dvb-usb: found a 'DiBcom STK7070P reference design' in cold state, will try to load a firmware
[ 2479.609462] usb 1-2: firmware: requesting dvb-usb-dib0700-1.20.fw
[ 2479.614324] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[ 2479.833335] dib0700: firmware started successfully.
[ 2480.336083] dvb-usb: found a 'DiBcom STK7070P reference design' in warm state.
[ 2480.336355] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 2480.336612] DVB: registering new adapter (DiBcom STK7070P reference design)
[ 2480.551334] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[ 2480.732330] DiB0070: successfully identified
[ 2480.732623] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/input/input14
[ 2480.732764] dvb-usb: schedule remote query interval to 50 msecs.
[ 2480.732771] dvb-usb: DiBcom STK7070P reference design successfully initialized and connected.

There is everything OK on M$ operating system, signal is very strong, and clean.

OS: Ubuntu 9.04
Kernel:2.6.28-12-generic
Maybe codecs?

Please help me!

---

### Post by xc3RnbFO8P on 2009-05-31
Try **Kaffeine** in Synaptic Package Manager

---

### Post by wirbel2 on 2009-05-31
Try to read w_scans README first if using it - you selected a **wrong output** file format, which mplayer cannot understand.

You need to set the right output format on command line.

---

### Post by lpm11 on 2009-05-31
thanks! kaffeine works :)
It had to install one plugin, I don't remember what.

But I don't like KDE (I use Ubuntu and GNOME:)

I have changed channels.conf entries look like:
TVP1:506000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_AUTO:FEC_AUTO:QAM_AUTO:TRANSMISSION_MODE_AUTO:GUARD_INTERVAL_AUTO:HIERARCHY_AUTO:102:104:1
Is this correct?

and mplayer output:

Playing dvb://TVP1.
dvb_tune Freq: 506000000
TS file format detected.
VIDEO MPEG2(pid=102) AUDIO MPA(pid=104) NO SUBS (yet)!  PROGRAM N. 0
(in smplayer video buffers, and then stops)

but I have MPEG4 H.264!
So that is MPlayer.

I've tried to use VLC. After manually entering frequency and Bitrate it is working. But how to remove interlace effect?

Totem fails at all.


Thaks for replies:)

---

### Post by xc3RnbFO8P on 2009-05-31
> But I don't like KDE (I use Ubuntu and GNOME
Then use **Me-TV**  :)

---

