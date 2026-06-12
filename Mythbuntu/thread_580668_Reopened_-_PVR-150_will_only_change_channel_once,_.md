---
title: "Reopened - PVR-150 will only change channel once, then needs a hard reboot"
date: 2007-10-19
forum: Mythbuntu
---

### Post by dhorkoff on 2007-10-19
I've restarted this thread since the old one was flagged as SOLVED before it has actually been solved.

I've just installed the latest RC build of Mythbuntu and I'm having problems with it only changing channels on my PVR-150 the very first time. After that, the channel is stuck on the first channel it went to and all recordings come from that channel.

I've done some testing via the command line using ivtv-tune --channel=x and it works properly until Mythbuntu tries to change and channel, at which point things get stuck again. Also, after this happens I must do a hard restart of the PC to get it work again, if I only do a soft reboot (by using the reboot command, for example) the boot process hangs when loading the ivtv driver saying it can't recognise the eeprom of my PVR-150 card. Very strange.

As a work around I've thought of putting in a custom channel change script to explicitly run ivtv-tune when channels, but this seems like it could be a lot of work.

Anyone have any thoughts on this problem or seen it before?

As an additional note, the ivtv module on boot up says it detects firmware encoder revision 0x02050032 and then a few lines later says it recommends revision 0x02060039. Any ideas on how to get the latest firmware update? Doesn't seem to be included in the latest kernel build.


A couple of days later:

Though the latest upgrade has helped things but I'm still running into the same problem, just slightly delayed now! It seemingly works fine when I first start it up. I can change channels using LiveTV and can schedule a variety of channels to record and they all seem to come through fine. However, when I leave the system running for a couple of hours things stop working and show the same symptoms of not being able to change channels and being stuck on the last channel that was either recorded from or selected for LiveTV. I'm then forced to do a cold reboot to get things back to the initial state for another round. Am I experiencing some kind of a time-out problem? Some sort of power saving mode kicking in and "sleeping" my PVR-150? I've updated the firmware files so that isn't the solution.

Here's my dmesg output for ivtv on a cold boot:
```
[   26.439517] Linux video capture interface: v2.00
[   26.552327] ivtv:  ==================== START INIT IVTV ====================
[   26.552334] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   26.552509] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   26.552561] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 18
[   26.552577] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   26.818092] input: PC Speaker as /class/input/input2
[   27.436285] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3751533624 bytes)
[   27.484556] input: PS/2 Generic Mouse as /class/input/input3
[   27.487614] parport_pc 00:09: reported by Plug and Play ACPI
[   27.487670] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   27.650729] ivtv0: Encoder revision: 0x02060039
[   27.710316] tveeprom 1-0050: Hauppauge model 26032, rev C599, serial# 8478218
[   27.710324] tveeprom 1-0050: tuner model is TCL 2002N 5H (idx 99, type 50)
[   27.710328] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   27.710331] tveeprom 1-0050: audio processor is CX25841 (idx 35)
[   27.710333] tveeprom 1-0050: decoder processor is CX25841 (idx 28)
[   27.710336] tveeprom 1-0050: has no radio, has IR receiver, has IR transmitter
[   27.710340] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   27.710343] ivtv0: reopen i2c bus for IR-blaster support
[   27.785776] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   27.972515] cx25840 1-0044: cx25841-23 found @ 0x88 (ivtv i2c driver #0)
[   31.685297] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   31.789712] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   31.839334] tuner 1-0061: type set to 50 (TCL 2002N)
[   32.163304] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   32.163723] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   32.164135] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   32.164376] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   32.188377] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   32.188464] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 20
[   32.193283] ivtv:  ====================  END INIT IVTV  ====================
```

Here's the dmesg output after a "warm" reboot:

```
[   25.452276] Linux video capture interface: v2.00
[   25.507174] ivtv:  ==================== START INIT IVTV ====================
[   25.507246] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   25.509137] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   25.509293] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 19
[   25.509407] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   26.004290] input: PC Speaker as /class/input/input2
[   26.395746] input: PS/2 Generic Mouse as /class/input/input3
[   26.399195] parport_pc 00:09: reported by Plug and Play ACPI
[   26.399314] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   26.606638] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3752626600 bytes)
[   26.819852] ivtv0: Encoder revision: 0x02060039
[   35.188576] eth0: no IPv6 routers present
[   39.622864] tveeprom 1-0050: Huh, no eeprom present (err=-121)?
[   39.622930] tveeprom 1-0050: Encountered bad packet header [00]. Corrupt or not a Hauppauge eeprom.
[   39.623008] ivtv0: Invalid EEPROM
[  180.432328] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[  180.432418] ivtv0: i2c addr 0x44 not found for command 0x4008646f!
[  180.432476] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[  180.432550] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0x4008646d!
[  180.540104] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[  180.540181] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[  180.648061] ivtv0: i2c hardware 0x00000001 (cx2584x) not found for command 0xc008561c!
[  180.648509] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[  180.648994] ivtv0: Registered device video32 for encoder YUV (2 MB)
[  180.649448] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[  180.649744] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[  180.650170] ivtv0: Registered device radio0 for encoder radio
[  180.650249] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[  180.650339] ivtv:  ====================  END INIT IVTV  ====================
```

One more piece of information: If I do a cold boot and then immediately do a warm boot, the dmesg output of the warm boot is identical to the dmesg output of the cold boot. If I do a cold boot, then change channels with LiveTV (which works, channels change as expected), then do a warm boot, the dmesg output for that warm boot is identical to the dmesg output of a cold boot.

So, there is definitely something happening over time that is putting my PVR-150 card into an invalid state. I've turned off all possible power-saving modes just to make sure it isn't my BIOS that is somehow causing these symptoms. I don't believe it is, though, since I've only had this problem since I moved to Mythbuntu from Knoppmyth. All of the hardware is identical and unchanged.

Any ideas? Thanks in advance.

---

### Post by superm1 on 2007-10-19
Well if you'd like to rule out the firmware issue, you can download the newer firmware and place it in ```
/lib/firmware/2.6.22-14-generic
```

---

### Post by superm1 on 2007-10-19
Oh i spoke too soon.  Didn't look at your "a few days later".

Have you considered bringing this up on the ivtv mailing list?

---

### Post by dhorkoff on 2007-10-19
> **superm1 said:**
> 
Have you considered bringing this up on the ivtv mailing list?

Have just done so. Thanks for your help.

---

### Post by dhorkoff on 2007-10-21
Well, I've solved my problem by replacing my PVR-150 card with a new PVR-500 MCE card. Fortunately I have another remote control and so don't need the one attached to my PVR-150.

I haven't received a reason why my PVR-150 card isn't working, but I've seen other people posting similar problems on the ivtvdriver mailing list. Seems that there may be ivtv driver problems with PVR-150 revision C599 cards. Just a guess though. Time will tell.

---

### Post by sikk on 2008-01-15
Gents,

I also have seen these exact errors. Though my situation was a little different.

I resolved the issue by removing a Leadtek Winfast DTV2000 H from my system. I also did not see the issue upon warm boot, but on every boot.

---

