---
title: "Midi problems with Cmedia based sound card"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by Moonchunk on 2007-10-01
I'm beaten down by my inability to make an external midi keyboard work with ubuntu Feisty, using a PCI Diamond Xtreme 16bit card based using the C-Media Electronics Inc CM8738 chip.  I'm trying to play and connect a casio keyboard through a midi/joystick connect cable.  It works with Windows on the same computer on a different partition.  I've disabled the onboard Nvidia sound on my Asus motherboard in bios because there's no midi/joystick port.  I've left the Midi settings in bios as irq 10 and port 330.

Non-midi sound works great.  The mpu-401 is present as hardware and recognized by alsa and jack control.  If I connect the uart midi by using aconnect or by jackcontrol to Qsynth (or other synthesizer), no sound or recognition of midi keyboard keypresses that I can tell.  Using the same process, I can get the synths to work by connecting a virtual midi keyboard.

The alsa_base file in modprobe.d already has the last line:

options snd-cmipci mpu_port=0x330 fm_port=0x388

Help...I'm ready to go back to Windows!


Moonchunk




Installed drivers:
Type 10: ALSA emulation

Card config:
C-Media PCI CMI8738-MC6 (model 55) at 0x9000, irq 209
MPU-401 UART at 0x330, irq 10

Audio devices:
0: C-Media PCI DAC/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
1: MPU-401 UART MIDI

Timers:
7: system timer

Mixers:
0: CMedia PCI
1: mixer10

---

