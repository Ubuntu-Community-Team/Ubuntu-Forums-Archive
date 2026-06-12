---
title: "No sound from aplaymidi"
date: 2015-11-19
forum: Multimedia Software
---

### Post by JohnEv on 2015-11-19
I have no sound output from the Soundblaster midi synthesiser.  I have Kubuntu 15.10 on a Gigabyte GA-F2A88X-D3H motherboard

aplaymidi -l output is:-

 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0 
 28:0    SB Audigy 2 ZS [SB0353]          Audigy MPU-401 (UART)
 28:32   SB Audigy 2 ZS [SB0353]          Audigy MPU-401 #2
 29:0    Emu10k1 WaveTable                Emu10k1 Port 0
 29:1    Emu10k1 WaveTable                Emu10k1 Port 1
 29:2    Emu10k1 WaveTable                Emu10k1 Port 2
 29:3    Emu10k1 WaveTable                Emu10k1 Port 3

asfxload loads sound font with no error and the same midi file works OK on other systems. Alsamixer shows the Synth output at max. 
All other sound inputs/outputs are working very well, with configuration as analogue stereo output  + mono input.

All the methods of checking/monitoring that I have tried indicate that all is working, there is just no sound. Any help will be greatly appreciated,

Same hardware worked OK with Kubuntu 14.10

---

