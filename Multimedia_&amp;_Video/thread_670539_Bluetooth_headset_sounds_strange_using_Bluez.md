---
title: "Bluetooth headset sounds strange using Bluez"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by alexandersk on 2008-01-17
Hi!
I'm trying to use my Motorla H350 bluetooth headset in Ubuntu (for Skype conversations).

I have tried Bluez, btsco and headsetd. Using Bluez and btsco the headset sound is interupted all the time, it plays 1/2 second of sound, then silence for 1/2 sec, then sound again. Using headsetd it works, once, then I have to restart the bluetooth service. Using some kernels (2.6.24 for instance), it doesn't work at all.

I would prefer to get Bluez working, as it seems to be working as good (in this case bad) every time I try to using, without having to restart services etc. Its pretty annoying to have to restart the bluetooth service after every phone call, which is the case when I use headsetd.

Any one have any suggestions? I haven't found any posts about people who have managed to get Bluez "working", but with this kind of sound problems.

My .asound (for Bluez) config looks like this:

pcm.bluetooth_hw {
   type bluetooth
   device 00:19:1F:24:B2:D1
}

ctl.bluetooth {
   type bluetooth
   device bdaddrs
}

pcm.bluetooth {
    type plug
    slave.pcm "bluetooth_hw"
}


At the moment I'm using Hardy, but I upgraded yesterday from Feisty where I had the exact same problems.

Cheers,
Alex

---

### Post by alexandersk on 2008-01-17
Of course I forgot to post information about the headset I'm using, which could be the problem (but I don't see why it would work using headsetd then).

sudo hcitool info 00:19:1F:24:B2: D1
Requesting information ...
	BD Address:  00:19:1F:24:B2: D1
	Device Name: Motorola H350
	LMP Version: 2.0 (0x3) LMP Subversion: 0x978
	Manufacturer: Cambridge Silicon Radio (10)
	Features: 0xfc 0xfe 0x0f 0x80 0x0b 0xe8 0x00 0x00
		<encryption> <slot offset> <timing accuracy> <role switch> 
		<hold mode> <sniff mode> <RSSI> <channel quality> <SCO link> 
		<HV2 packets> <HV3 packets> <u-law log> <A-law log> <CVSD> 
		<paging scheme> <power control> <transparent SCO> 
		<extended SCO> <EV4 packets> <EV5 packets> <AFH cap. slave> 
		<AFH cap. master> <EDR eSCO 2 Mbps> <EDR eSCO 3 Mbps> 
		<3-slot EDR eSCO>

---

### Post by alexandersk on 2008-01-18
No one got any idea on how to solve this?

---

### Post by tighem on 2008-02-14
BT headset hasn't worked for me since Feisty. I'm really anxious to see this resolved.

---

