---
title: "No sound (instantly after GDM) on Ubuntu 9.04"
date: 2009-06-02
forum: Multimedia Software
---

### Post by atari130xe on 2009-06-02
Hello forum, I have installed Ubuntu 9.04 to my sister Computer, everything works realy well, but got a problem with sounds.
If I start the PC there is sound in GDM (Login) but then no more sound ( starting sound, etc.) It seem that PulseAudio starts "twice" or something like that (I really don know).

```
juana@juana-desktop:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: VT82xx [HDA VIA VT82xx], dispositivo 0: ALC662 Analog [ALC662 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: VT82xx [HDA VIA VT82xx], dispositivo 1: ALC662 Digital [ALC662 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```

```
juana@juana-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
04:04.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
juana@juana-desktop:~$
```

```
Jun 1 14:15:20 juana-desktop pulseaudio[3132]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 1 14:15:20 juana-desktop pulseaudio[3132]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
un 1 14:24:25 juana-desktop pulseaudio[4103]: pid.c: Stale PID file, overwriting.
Jun 1 14:24:25 juana-desktop pulseaudio[4103]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
Jun 1 14:24:25 juana-desktop pulseaudio[4103]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
```

Once in a sesion (with no sound) I do the following, I get sound back:

```
juana@juana-desktop:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() falló.
```

```
juana@juana-desktop:~$ killall pulseaudio
```

```
juana@juana-desktop:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
W: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 48000 Hz.
W: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
```

After this I got sound but it die if If close the console.

Any suggestions? help?
thanks!

---

### Post by atari130xe on 2009-06-04
bumer... noone to give me a hand?

---

### Post by atari130xe on 2009-06-06
No one help me?

---

