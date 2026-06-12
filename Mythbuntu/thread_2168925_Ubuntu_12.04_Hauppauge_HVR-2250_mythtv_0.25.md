---
title: "Ubuntu 12.04 Hauppauge HVR-2250 mythtv 0.25"
date: 2013-08-19
forum: Mythbuntu
---

### Post by jrocor on 2013-08-19
Ubuntu 12.04 64bit Mythtv.25 

Hello all, I am seeking help with setting up my system and am stuck with channel scanning.  I am trying to get OTA TV broadcast working with my Hauppauage HVR-2250 card but am unable to get most channels.

If I plug the coax cable into my TV it can tune all channels so its not a cable/connection issue.

I followed the guide here to get the driver as it seemed to be the most recent post regarding this card.  [http://askubuntu.com/questions/214166/how-to-set-up-hvr-2250-tv-card-in-ubuntu-12-10](http://askubuntu.com/questions/214166/how-to-set-up-hvr-2250-tv-card-in-ubuntu-12-10)

```

dmesg | grep saa7164 

[   13.200490] saa7164 driver loaded
[   13.200532] saa7164 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.202820] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   13.202825] saa7164[0]/0: found at 0000:01:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xf7800000
[   13.202830] saa7164 0000:01:00.0: setting latency timer to 64
[   13.359355] saa7164_downloadfirmware() no first image
[   13.359365] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   13.374067] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   13.374070] saa7164_downloadfirmware() firmware loaded.
[   13.374077] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   13.374083] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   13.374084] saa7164_downloadfirmware() BSLSize = 0x0
[   13.374085] saa7164_downloadfirmware() Reserved = 0x0
[   13.374087] saa7164_downloadfirmware() Version = 0x1661c00
[   20.288038] saa7164_downloadimage() Image downloaded, booting...
[   20.391991] saa7164_downloadimage() Image booted successfully.
[   22.435015] saa7164_downloadimage() Image downloaded, booting...
[   24.306126] saa7164_downloadimage() Image booted successfully.
[   24.350572] saa7164[0]: Hauppauge eeprom: model=88061
[   25.003013] DVB: registering new adapter (saa7164)
[   28.171626] DVB: registering new adapter (saa7164)
[   28.172125] saa7164[0]: registered device video0 [mpeg]
[   28.402907] saa7164[0]: registered device video1 [mpeg]
[   28.617883] saa7164[0]: registered device vbi0 [vbi]
[   28.617988] saa7164[0]: registered device vbi1 [vbi]

```

In the Backend Setup, on the Connect Source To Input page, if I click Fetch Channels From Listing Source, nothing happens, no feedback.
In the Video Source page, if I click Retrieve Lineups, again, nothing happens, no feedback, I don't know if its doing anything or not.
I did not check Perform EIT Scan.

On the channel editor page, if I scan for channels it only sees a few channels on 7, 9, 10, 11 and 13.  Everything from 2 through 6 says: Timed out, no channels.  I have increased the timeout to 5000ms but no help there.  I manually added a channel (channel 2_1) but if I try to change to it in the frontend it says Irrecoverable Recorder Error, and exits out to the frontend.

Any advice on how to proceed would be greatly appreciated.  Thanks!

---

