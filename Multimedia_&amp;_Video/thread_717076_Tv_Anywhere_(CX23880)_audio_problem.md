---
title: "Tv Anywhere (CX23880) audio problem"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by StiveG on 2008-03-06
Hi all,

This is my first week with Ubuntu and love it ;)

Had problems with my graphic card but fixed it (P965)

The problem I have now is with my Tv @nywhere card.

I can see images, change channel, but no sound at all. When I go to the sound mixer (little speaker icon in the lower right) I do have Conexant cx8801 (alsa mixer) but when I select it, I only have a grey box, no way to adjust the sound.

here are some infos :

tail -2 /proc/asound/oss/sndstat

> 
0: SigmaTel STAC9227
1: CX88

lspci

> 00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
04:01.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)
 
dmesg :

> [   77.187866] cx2388x v4l2 driver version 0.0.6 loaded
[   77.187966] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 22 (level, low) -> IRQ 22
[   77.188007] CORE cx88[0]: subsystem: 1462:8606, board: MSI TV-@nywhere Master [card=7,autodetected]
[   77.188010] TV tuner 33 at 0x1fe, Radio tuner -1 at 0x1fe
[   77.206313] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   77.206320] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   77.224407] Initializing USB Mass Storage driver...
[   77.224512] scsi4 : SCSI emulation for USB Mass Storage devices
[   77.224584] usb-storage: device found at 5
[   77.224587] usb-storage: waiting for device to settle before scanning
[   77.224596] usbcore: registered new interface driver usb-storage
[   77.224599] USB Mass Storage support registered.
[   77.303509] cx2388x alsa driver version 0.0.6 loaded
[   77.350007] input: cx88 IR (MSI TV-@nywhere Master as /class/input/input4
[   77.350044] cx88[0]/0: found at 0000:04:01.0, rev: 5, irq: 22, latency: 32, mmio: 0x51000000
[   77.388522] tuner 0-0043: chip found @ 0x86 (cx88[0])
[   77.388561] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   77.392849] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[   77.396580] tuner 0-0061: microtune: companycode=3cbf part=42 rev=22
[   77.398245] tuner 0-0061: microtune MT2050 found, OK
[   77.401927] tuner 0-0061: microtune: companycode=3cbf part=42 rev=22
[   77.403603] tuner 0-0061: microtune MT2050 found, OK
[   77.414383] cx88[0]/0: registered device video0 [v4l2]
[   77.414419] cx88[0]/0: registered device vbi0
[   77.414449] cx88[0]/0: registered device radio0
[   77.416833] ACPI: PCI Interrupt 0000:04:01.1[A] -> GSI 22 (level, low) -> IRQ 22
[   77.416861] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   77.586360] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   77.586688] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   78.542713] lp0: using parport0 (interrupt-driven).
[   78.620163] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   79.045885] EXT3 FS on sda1, internal journal



sudo lspci -v | grep -i audio

> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
04:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
04:01.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)


mplayer tv:// -tv driver=v4l2:chanlist=us-cable:alsa:adevice=hw.0,1:amode=1:audiorate=48000:forceaudio:volume=100:immediatemode=0:norm=NTSC-M
> 
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU            2140  @ 1.60GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: MSI TV-@nywhere Master
 Tuner cap:
 Tuner rxs:
 Capabilites:  video capture  VBI capture device  tuner  read/write  streaming
 supported norms: 0 = PAL-BG; 1 = PAL-DK; 2 = PAL-I; 3 = PAL-M; 4 = PAL-N; 5 = PAL-Nc; 6 = PAL-60; 7 = NTSC-M; 8 = NTSC-M-JP; 9 = NTSC-443; 10 = SECAM-DK; 11 = SECAM-L;
 inputs: 0 = Television; 1 = Composite1; 2 = S-Video;
 Current input: 0
 Current format: BGR24
v4l2: current audio mode is : STEREO
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
Error opening audio: No such file or directory
Error opening audio: No such file or directory
Error opening audio: No such file or directory
v4l2: 0 frames successfully processed, 0 frames dropped.
v4l2: ioctl set mute failed: Bad file descriptor
v4l2: 0 frames successfully processed, 0 frames dropped.


Exiting... (End of file)




I tried to add "options tda9887 qss=0" in /etc/modprobe.d/alsa-base and reboot but changed nothing...

I really don't know what to do to next... Is someone could help me, that would be really appreciate :)

Thanks

---

### Post by warp99 on 2008-03-10
The code for module tda9887 was moved after kernel 2.6.18, add the following to your /etc/modprobe.d/options:

```
options tuner qss=0
```

I like to place all parameter changes into one file, but you can place this in /etc/modprobe.d/alsa-base if you like. :)

---

