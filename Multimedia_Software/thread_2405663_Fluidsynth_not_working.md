---
title: "Fluidsynth not working"
date: 2018-11-09
forum: Multimedia Software
---

### Post by mr-mister on 2018-11-09
Hi! i was trying get fliuidsynth working following this [guide]("http://tedfelix.com/linux/linux-midi.html") , but when i run 

```
fluidsynth --audio-driver=alsa -o audio.alsa.device=hw:1 /usr/share/sounds/sf2/FluidR3_GS.sf2 alb_esp1.mid
```

to test it i get:
```

fluidsynth: warning: No preset found on channel 0 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 1 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 2 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 3 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 4 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 5 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 6 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 7 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 8 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 9 [bank=128 prog=0]
fluidsynth: warning: No preset found on channel 10 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 11 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 12 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 13 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 14 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 15 [bank=0 prog=0]
fluidsynth: warning: Failed to set thread to high priority
Type 'help' for help topics.

fluidsynth: warning: Failed to set thread to high priority
fluidsynth: warning: No preset found on channel 0 [bank=0 prog=0]
fluidsynth: warning: No preset found on channel 0 [bank=0 prog=0]

```
These are my cards: 
```

 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xc1318000 irq 48
 1 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xc131c000 irq 47

```
and devices: 
```

card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC3227 Analog [ALC3227 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by mr-mister on 2018-11-09
Sorry! i  tried with the /usr/share/sounds/sf2/FluidR3_GM.sf2 soundfont and worked

---

