---
title: "Sound only partly working Ensoniq Creative Sound Blaster"
date: 2007-09-10
forum: Multimedia &amp; Video
---

### Post by skipx on 2007-09-10
I'm using 5 ubuntu installed pc's for an art project. They will be put on different locations next weekend, and from there they will stream the environment sound (mics via mixing deck, into line-input of pc) to my server.

I did not think i would get problems, because my audio card seemed to be working. Everything audible  in my system (also flash eg, though not really needed) plays through my speakers when needed. Also the line in is working, i can record it, also i can play it straight to line out.

Problem is, trusting all was ok, i tested streaming (ices2) on a different machine. Now i start using it on one of the 5 pc's it just doesn't work. Checking a different USB audio card did not solve the problem, thereby also jackd has problems with my alsa setup (it plays in playback mode only, also gives load of playback errors till it crashes).

When i use OSS to stream /dev/dsp i get a working stream, but there's no audio. 

I hope somebody can help getting alsa to work!
Thanks,

bart

streamer1@stream5:~$ hwinfo --sound
17: PCI 0d.0: 0401 Multimedia audio controller                  
  [Created at pci.281]
  UDI: /org/freedesktop/Hal/devices/pci_1274_1371
  Unique ID: qnJ_.JYL4K7uOcf9
  SysFS ID: /devices/pci0000:00/0000:00:0d.0
  SysFS BusID: 0000:00:0d.0
  Hardware Class: sound
  Model: "Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128"
  Vendor: pci 0x1274 "Ensoniq"
  Device: pci 0x1371 "ES1371 [AudioPCI-97]"
  SubVendor: pci 0x1274 "Ensoniq"
  SubDevice: pci 0x1371 "Creative Sound Blaster AudioPCI64V, AudioPCI128"
  Revision: 0x06
  Driver: "ENS1371"
  Driver Modules: "snd_ens1371"
  I/O Ports: 0xc800-0xc83f (rw)
  IRQ: 10 (249 events)
  Module Alias: "pci:v00001274d00001371sv00001274sd00001371bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_ens1371 is active
    Driver Activation Cmd: "modprobe snd_ens1371"
  Driver Info #1:
    Driver Status: es1371 is not active
    Driver Activation Cmd: "modprobe es1371"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


Interface options in Jack:
hw:0 Ensoniq AudioPCI
hw:0,0 ES1371 DAC2/ADC
hw:0,1 ES1371 DAC1

Jack output:
08:22:49.697 Patchbay deactivated.
08:22:50.095 Statistics reset.
08:22:50.827 MIDI connection graph change.
08:22:50.835 MIDI connection change.
08:22:54.823 Startup script...
08:22:54.824 artsshell -q terminate
can't create mcop directory
Creating link /home/streamer1/.kde/socket-stream5.
08:22:56.698 Startup script terminated with exit status=256.
08:22:56.758 JACK is starting...
08:22:56.759 /usr/bin/jackd -dalsa -dhw:0 -r48000 -p1024 -n2
08:22:56.827 JACK was started with PID=16182 (0x3f36).
jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
08:22:59.093 Server configuration saved to "/home/streamer1/.jackdrc".
08:22:59.096 Statistics reset.
08:22:59.100 Client activated.
08:22:59.150 Audio connection graph change.
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
08:23:00.774 Buffer size change (1024).
08:23:01.195 Audio connection graph change.
08:23:01.218 XRUN callback (1).
ALSA: use 2 periods for playback
08:23:01.854 Audio connection change.
**** alsa_pcm: xrun of at least 6.351 msecs
**** alsa_pcm: xrun of at least 2.130 msecs
**** alsa_pcm: xrun of at least 6.613 msecs
08:23:03.945 XRUN callback (2 skipped).
08:23:04.236 XRUN callback (4).
**** alsa_pcm: xrun of at least 4.873 msecs
**** alsa_pcm: xrun of at least 8.358 msecs
**** alsa_pcm: xrun of at least 16.007 msecs
**** alsa_pcm: xrun of at least 7.138 msecs
08:23:06.380 XRUN callback (15 skipped).
**** alsa_pcm: xrun of at least 7.047 msecs
**** alsa_pcm: xrun of at least 2.636 msecs
**** alsa_pcm: xrun of at least 34.013 msecs

(here i stop jack)

08:23:08.170 Client deactivated.
08:23:08.300 JACK is stopping...
**** alsa_pcm: xrun of at least 4.835 msecs
**** alsa_pcm: xrun of at least 2.750 msecs
**** alsa_pcm: xrun of at least 38.218 msecs
**** alsa_pcm: xrun of at least 4.605 msecs
**** alsa_pcm: xrun of at least 7.061 msecs
**** alsa_pcm: xrun of at least 7.307 msecs
**** alsa_pcm: xrun of at least 6.988 msecs
**** alsa_pcm: xrun of at least 3.265 msecs
**** alsa_pcm: xrun of at least 6.700 msecs
**** alsa_pcm: xrun of at least 8.568 msecs
**** alsa_pcm: xrun of at least 4.328 msecs
**** alsa_pcm: xrun of at least 15.079 msecs
**** alsa_pcm: xrun of at least 37.872 msecs
**** alsa_pcm: xrun of at least 6.185 msecs
**** alsa_pcm: xrun of at least 8.327 msecs
**** alsa_pcm: xrun of at least 0.084 msecs
**** alsa_pcm: xrun of at least 0.282 msecs
**** alsa_pcm: xrun of at least 8.052 msecs
**** alsa_pcm: xrun of at least 3.215 msecs
**** alsa_pcm: xrun of at least 9.754 msecs
**** alsa_pcm: xrun of at least 3.296 msecs
**** alsa_pcm: xrun of at least 1.694 msecs
jack main caught signal 15
no message buffer overruns
08:23:14.466 JACK was stopped successfully.
08:23:14.479 Post-shutdown script...
08:23:14.502 killall jackd
jackd: no process killed
08:23:15.487 Post-shutdown script terminated with exit status=256.

And from my ices2 log
2007-09-09  18:57:51] EROR input/input_loop Couldn't initialise input module "alsa"
[2007-09-09  18:57:51] INFO ices-core/main Shutdown complete
[2007-09-09  19:00:16] INFO ices-core/main IceS 2.0.1 started...
[2007-09-09  19:00:17] EROR input-alsa/alsa_open_module Failed to open audio device plughw:default: No such device

ices alsa input module:
        <input>
            <module>alsa</module>
            <param name="rate">48000</param>
            <param name="channels">2</param>
            <param name="device">hw:0,0</param>
            <!-- <param name="periods">2</param> -->
            <!-- <param name="buffer-time">500</param> -->
            <!-- Read metadata (from stdin by default, or -->
            <!-- filename defined below (if the latter, only on SIGUSR1) -->
            <param name="metadata">1</param>
            <param name="metadatafilename">test</param>
        </input>

---

