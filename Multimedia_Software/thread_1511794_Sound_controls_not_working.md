---
title: "Sound controls not working"
date: 2010-06-17
forum: Multimedia Software
---

### Post by loosends on 2010-06-17
After installing Lucid, I have reasonable quality sound for most media... but...

The volume controls in YouTube do not work, and it's the same for TVtime.  
Tvtime still has awful sound quality; it crackles and hiccups when the media volume increases. Sync appears ok, and sound from 'normal' conversation is ok, but background music (esp. bass) causes crackle.

Ubuntu 10.04

Hardware:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
      - this is an onboard device.  Motherboard is ASUS M3A78-CM

lsusb
Bus 001 Device 002: ID 2040:7240 Hauppauge  <-- usb tv adapter

dmesg | grep audio
[    9.937789] [drm] Enabling audio support
[   10.679669] tveeprom 4-0050: audio processor is AU8522 (idx 44)
[   10.931402] usbcore: registered new interface driver snd-usb-audio

lshw 
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64
             resources: irq:16 memory:fbcf4000-fbcf7fff
 
How do I get the controls back?  I currently need to use the panel applet, or the speaker knobs to control volume.

---

