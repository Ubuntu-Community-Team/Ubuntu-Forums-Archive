---
title: "Sound Problems in Dapper"
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by Jvaldezjr on 2006-06-22
Add this thread to the list of people with sound problems.

When I was using breezy with (I think ALSA 1.9) I had 5.1 sound, everything was clear, and beautiful sounding.  Now I've installed Dapper, and at best my sound is very low and full of static.  I've configured my /etc/asound.conf file a million different ways, and I've search and read EVERY thread on these forums in regard to sound- and nothing has helped.  On my system I have an AMD Athlon64 processcor, 1GB ram, and a NFORCE 3 motherboard with onboard sound.

About the onboard sound, right now I've disabled it because it only gives me sound on 2 channels.  It's a Realtek Chip - actually listed as Nforce CK8S with an ALC850 chipset- which means 8 channel sound, and I have NOT been able to configure alsa right with this card.  So I disabled my onboard sound for the time being, and I have been using an old SoundBlaster Audigy card (not Platinum, not LS, not Gamer, just regular Audigy- revision 3), and I'm stuck with this poor excuse for noise comming out of my speakers.  So here is what I have so far.

'cat /proc/asound/cards' says:
```

0 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                     Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xc000, irq 225
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 10

```

'cat /proc/asound/devices | grep "audio" ' says:
```

 19: [0- 3]: digital audio playback
 18: [0- 2]: digital audio playback
 26: [0- 2]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture

```

'aplay -l' says:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy [Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

'alsamixer' says:
```

Card: Audigy 1 (SB0090)
Chip: TriTech TR28602
and lists the following items:
Line, CD, Mic Boost, Phone, PC, Aux, Audigy A, External
-everything is unmuted and 100% volume

```

'/etc/asound.conf' (which is long) says:
[my /etc/asound.conf]("http://filebox.vt.edu/users/juromero/asound.conf")

Does anyone have any idea where to start?  What other information do I need to provide to help with this situation?  Upgrading to the alsa 1.11 drivers (from source) do not help this either.  I'm all out of ideas.  What I would like is to eventually be able to get my onboard sound to work properly, i'm only using the Audigy card for the firewire port, since I have an IPod, and it's my only firewire port.

Thanks
JValdezjr

---

### Post by Epskampie on 2006-08-30
Sorry, no solution here, just reporting in with the same problem.
I'm using an Asus k8n-e deluxe motherboard with nForce 3 250gb chipset. The audio chip is reported as:
```
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
Subsystem: ASUSTeK Computer Inc.: Unknown device 812a
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
I/O ports at e800 [size=256]
I/O ports at e400 [size=128]
Memory at ff6fb000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [44] Power Management version 2
```
The noise isn't there the whole time, but it is very clear during some louder parts of songs.
It's working perfect under windows, so the hardware is fine.

Will post if I find a solution!

[SIZE="3"]Edit:[/SIZE]

My bad, my bad. I fixed by using the suggestion posted in [this](http://www.ubuntuforums.org/showthread.php?t=185316&highlight=nforce+noise) thread, lowering the PCM volume. The stupid thing is that I thought of this myself, but only tried the master volume. Meesa so stupid!

Hope you find a solution to your problem too... I guess you checked the [comprehensive sound guide](http://www.ubuntuforums.org/showthread.php?t=205449)?

---

