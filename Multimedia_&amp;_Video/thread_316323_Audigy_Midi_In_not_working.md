---
title: "Audigy Midi In not working"
date: 2006-12-10
forum: Multimedia &amp; Video
---

### Post by custommonkey on 2006-12-10
I've hooked up my keyboard to my Audigy and I can send midi data to the keyboard using ```
aplaymidi -p20:32 some.mid
``` but when I try and receive ```
amidi -d -p hw:1,1
``` I get nothing.

If I do the same for vkeybd I get get nice happy numbers.

Here's the device listing from both aplaymidi and amidi. As far as I can tell I'm using the correct device.
```

jeff@acidbox:~$ aplaymidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 20:0    Audigy 1 [SB0090]                Audigy MPU-401 (UART)
 20:32   Audigy 1 [SB0090]                Audigy MPU-401 #2
 21:0    Emu10k1 WaveTable                Emu10k1 Port 0
 21:1    Emu10k1 WaveTable                Emu10k1 Port 1
 21:2    Emu10k1 WaveTable                Emu10k1 Port 2
 21:3    Emu10k1 WaveTable                Emu10k1 Port 3
jeff@acidbox:~$ amidi -l
 Device    Name
 hw:1,0    Audigy MPU-401 (UART)
 hw:1,1    Audigy MPU-401 #2
 hw:1,2    Emu10k1 Synth MIDI (16 subdevices)
 hw:1,3    Emu10k1 Synth MIDI (16 subdevices)

```

I've tried swapping the cables round and I can send through both of them so it's not them.

Any suggestions for things to try would be most welcome.

---

