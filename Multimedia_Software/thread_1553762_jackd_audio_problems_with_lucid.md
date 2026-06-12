---
title: "jackd audio problems with lucid"
date: 2010-08-15
forum: Multimedia Software
---

### Post by smaring on 2010-08-15
I'm trying to get jackd running properly on my HP Pavilion dv7 with an updated Lucid Lynx so that I can do some midi stuff with QSynth and Rosegarden.

I've followed the directions in [UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation?highlight=%28\bCategoryAudio\b%29") but still having problems.

```
smaring@lappy:~$ jackd -v -r -dalsa -dhw:0 -r44100 -p256 -n2
jackdmp 1.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in non-realtime mode
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackSocketServerChannel::Open
Jack: Bind: addr.sun_path /dev/shm/jack_default_1000_0
Jack: JackSocketServerChannel::BuildPoolTable size = 1
Jack: JackEngine::Open
Jack: Connect: addr.sun_path /dev/shm/jack_default_1000_0
Jack: playback device hw:0
Jack: capture device hw:0
Jack: apparent rate = 44100
Jack: frames per period = 256
Jack: JackDriver::Open capture_driver_name = hw:0
Jack: JackDriver::Open playback_driver_name = hw:0
Jack: JackEngine::ClientInternalOpen: name = system
Jack: JackEngine::AllocateRefNum ref = 0
Jack: JackFifo::Allocate name = /dev/shm/jack_fifo.1000_default_system
Jack: JackEngine::NotifyAddClient: name = system
Jack: JackGraphManager::SetBufferSize size = 256
Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackDriver::SetupDriverSync driver sem in flush mode
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xdf300000 irq 22
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Jack: JackDriver::Close
Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackEngine::ClientCloseAux ref = 0
Jack: JackGraphManager::RemoveAllPorts ref = 0
Jack: JackFifo::Destroy name = /dev/shm/jack_fifo.1000_default_system
Jack: ~JackDriver
Cannot initialize driver
Jack: JackEngine::Close
Jack: JackClientSocket::Close
Jack: JackServerSocket::Close /dev/shm/jack_default_1000_0
Jack: no message buffer overruns
Jack: JackPosixThread::Stop
Jack: ThreadHandler: exit
JackServer::Open() failed with -1
Jack: Succeeded in unlocking 82208666 byte memory area
Jack: JackShmMem::delete size = 0 index = 0
Jack: ~JackDriver
Jack: JackEngine::~JackEngine
Jack: Succeeded in unlocking 994 byte memory area
Jack: JackShmMem::delete size = 0 index = 1
Jack: cleaning up shared memory
Jack: cleaning up files
Jack: unregistering server `default'
Failed to start server
```

and then, if I reload alsa ...

```
smaring@lappy:~$ sudo alsa force-reload
[sudo] password for smaring: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/smaring/.gvfs
      Output information may be incomplete.
Terminating processes: 2883 29951Terminated
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/smaring/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/smaring/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/smaring/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-pcm-oss snd-mixer-oss snd-usb-audio snd-usb-lib snd-seq-dummy snd-seq-oss snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-intel snd-hda-codec-nvhdmi snd-hda-codec-idt snd-hda-codec snd-pcm snd-hwdep snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-pcm-oss snd-mixer-oss snd-usb-audio snd-usb-lib snd-seq-dummy snd-seq-oss snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-intel snd-hda-codec-nvhdmi snd-hda-codec-idt snd-hda-codec snd-pcm snd-hwdep snd-timer snd-page-alloc.
```

I can get a little bit further ...

```
smaring@lappy:~$ jackd -v -r -dalsa -dhw:0 -r44100 -p256 -n2
jackdmp 1.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2009 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in non-realtime mode
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackSocketServerChannel::Open
Jack: Bind: addr.sun_path /dev/shm/jack_default_1000_0
Jack: JackSocketServerChannel::BuildPoolTable size = 1
Jack: JackEngine::Open
Jack: Connect: addr.sun_path /dev/shm/jack_default_1000_0
Jack: playback device hw:0
Jack: capture device hw:0
Jack: apparent rate = 44100
Jack: frames per period = 256
Jack: JackDriver::Open capture_driver_name = hw:0
Jack: JackDriver::Open playback_driver_name = hw:0
Jack: JackEngine::ClientInternalOpen: name = system
Jack: JackEngine::AllocateRefNum ref = 0
Jack: JackFifo::Allocate name = /dev/shm/jack_fifo.1000_default_system
Jack: JackEngine::NotifyAddClient: name = system
Jack: JackGraphManager::SetBufferSize size = 256
Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackDriver::SetupDriverSync driver sem in flush mode
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xdf300000 irq 22
configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
Jack: JackEngine::ClientInternalOpen: name = freewheel
Jack: JackEngine::AllocateRefNum ref = 1
Jack: JackFifo::Allocate name = /dev/shm/jack_fifo.1000_default_freewheel
Jack: JackEngine::NotifyAddClient: name = freewheel
Jack: JackConnectionManager::DirectConnect first: ref1 = 1 ref2 = 1
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Jack: JackDriver::SetupDriverSync driver sem in flush mode
Jack: JackGraphManager::SetBufferSize size = 256
Jack: JackAudioDriver::Attach fBufferSize 256 fSampleRate 44100
Jack: JackGraphManager::AllocatePortAux port_index = 1 name = system:capture_1 type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 1
Jack: JackAudioDriver::Attach fCapturePortList[i] 1 
Jack: JackGraphManager::AllocatePortAux port_index = 2 name = system:capture_2 type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 2
Jack: JackAudioDriver::Attach fCapturePortList[i] 2 
Jack: JackGraphManager::AllocatePortAux port_index = 3 name = system:playback_1 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 3
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 3 
Jack: JackGraphManager::AllocatePortAux port_index = 4 name = system:playback_2 type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 4
Jack: JackAudioDriver::Attach fPlaybackPortList[i] 4 
Jack: Clock source : system clock via clock_gettime
Jack: JackServer::Start
Jack: JackThreadedDriver::Start
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackSocketServerChannel::ClientCreate socket
Jack: JackSocketServerChannel::BuildPoolTable size = 2
Jack: fSocketTable i = 1 fd = 11
ALSA: poll time out, polled for 8714933 usecs
JackAudioDriver::ProcessAsync: read error, skip cycle
Jack: fPollTable i = 1 fd = 11
ALSA: poll time out, polled for 8714810 usecs
JackAudioDriver::ProcessAsync: read error, skip cycle
Jack: fPollTable i = 1 fd = 11
ALSA: poll time out, polled for 8714694 usecs
JackAudioDriver::ProcessAsync: read error, skip cycle
Jack: fPollTable i = 1 fd = 11
ALSA: poll time out, polled for 8714132 usecs
JackAudioDriver::ProcessAsync: read error, skip cycle
Jack: fPollTable i = 1 fd = 11
ALSA: poll time out, polled for 8714939 usecs
JackAudioDriver::ProcessAsync: read error, skip cycle
^Cjack main caught signal 2
...
```

```

smaring@lappy:~$ uname -a
Linux lappy 2.6.32-24-lowlatency #39-Ubuntu SMP PREEMPT Thu Aug 5 22:22:06 UTC 2010 x86_64 GNU/Linux
```

I should also note that my pulse audio mixer fails to connect to the pulseaudio server, even though I don't see any complaints when I start it (could be a lack of logging, not sure).  So, I basically have no audio at all right now.

When I force the reload of alsa I see this in the logs:

```
[44189.356105] HDA Intel 0000:00:1b.0: PCI INT B disabled
[44189.362162] usbcore: deregistering interface driver snd-usb-audio
[44189.460157] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[44189.472126] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[44189.472135] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[44189.472291] HDA Intel 0000:00:1b.0: setting latency timer to 64
[44190.486007] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x000f0000
[44190.561924] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input20
[44190.584572] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input21
[44190.584683] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input22
```


Any thoughts on how to debug this would be greatly appreciated.

-Steve Maring
Tampa, FL  USA

---

### Post by lidex on 2010-08-15
Try the first link here:
[https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=004599128559784038176%3Avj_p0xo-nng&ie=UTF-8&q=HowToJACKConfiguration&sa=Search](https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=004599128559784038176%3Avj_p0xo-nng&ie=UTF-8&q=HowToJACKConfiguration&sa=Search)

---

### Post by smaring on 2010-08-15
I've tried all the recommended settings in the HowToJACKConfiguration, but I always get the same result.

---

### Post by cchhrriiss121212 on 2010-08-16
Try changing the settings a bit:
Leave your interface set as hw:0 and your input/output device as default. Leave your input/output channels as default. Increase the frame rate to 1024.
Your first instance did not start due to something else using ALSA, so shut down all programs using sound before starting jack.

---

### Post by madeinfamous on 2010-08-16
allo smaring,

[I]Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xdf300000 irq 22
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Jack: JackDriver::Close[/I]


do you have the sound system enable ? if so, untick the checkbox,

i've notice jack don't start properly lately if the sound system is enable,

if it's not the case, forget about what i said :P

---

### Post by smaring on 2010-08-16
I've tried frame rates 64 - 1024.  I'm guessing the "sound system" is already disabled, since when I try to open System -> Preferences -> Sound, it complains that the sound system isn't running.

Any other thoughts?  Is it normal that my sound should be broken now even before I try to start jackd?

---

### Post by cchhrriiss121212 on 2010-08-16
It is not normal that your regular sound (ie pulse and ALSA) is broken, and it may be result of you restarting ALSA (which is not necessary to use jack) without restarting pulse. 
Regular sound will only be suspended when you start jack.

Also I see you are using jack2, where did you get this from?

---

### Post by smaring on 2010-08-17
I'm guessing that I probably should not have added the "ppa:falk-t-j/lucid" repository, suggested in the UbuntuStudioPreparation docs.  That's where I ended up with jack2 and a now broken sound system.

I've tried removing the repository, updating, and reinstalling all the sound packages, but my attempt at a downgrade seems to be leaving me with broken packages everywhere.

---

### Post by AutoStatic on 2010-08-17
In case you just installed Jack2 from FalkTX's PPA you should be able to uninstall it and reinstall the default Jack1 packages from the Ubuntu repo's.
After reinstalling Jack1, also install the alsa-backports package otherwise JACK will die within like 10 sec. I have a DV7 too and JACK won't run without alsa-backports.
Also try using hw:Intel instead of hw:0 in QjackCtl.

---

