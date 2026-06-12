---
title: "M-Audio FireWire Solo Vs. Maverick... FIGHT!"
date: 2011-01-04
forum: Multimedia Software
---

### Post by Forum User on 2011-01-04
So, after two days of reading every result about hooking up my firewire solo sound card to Ubuntu, here I am, posting my own thread. I WILL see this work, or die trying.

Basics. I am on maverick meercat, using jackd2 to try to connect. I have added the libfreebob driver, and Maverick knows this:

```
dpkg -l | grep freebob
ii  libfreebob0                          1.0.11-1build1
```

But when I try to get jackd2 to use the driver it says:

```
jackd -d freebob
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
Unknown driver "freebob"

```

LOL WUT??? It said that I had it installed, but now its not there?

HOW do I get jack to see the freebob driver?

---

### Post by Forum User on 2011-01-05
So I thought, "I wonder if the damn firewire is working at all back there?" and went through this:

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

which told me YES, it was working.

... so I checked the packages for firewire installed:

```
ii  jackd2-firewire                      1.9.5~dfsg-19ubuntu1                              JACK Audio Connection Kit (FFADO and FreeBoB backends)
```

So  its there. Lets run jackQT and go with the settings from the firewire help page:

```
started
16:58:38.657 Startup script...
16:58:38.658 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:58:39.063 Startup script terminated with exit status=32512.
16:58:39.064 JACK is starting...
16:58:39.064 /usr/bin/jackd -v -P70 -p128 -dfirewire -dhw:0 -r44100 -p128 -n2 -i8 -o8
16:58:39.079 JACK was started with PID=1867.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 70
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackSocketServerChannel::Open
Jack: Bind: addr.sun_path /dev/shm/jack_default_1001_0
Jack: JackSocketServerChannel::BuildPoolTable size = 1
Jack: JackEngine::Open
Jack: Connect: addr.sun_path /dev/shm/jack_default_1001_0
Jack: JackDriver::Open capture_driver_name = 
Jack: JackDriver::Open playback_driver_name = 
Jack: JackEngine::ClientInternalOpen: name = system
Jack: JackEngine::AllocateRefNum ref = 0
Jack: JackPosixSemaphore::Allocate name = jack_sem.1001_default_system val = 0
Jack: JackEngine::NotifyAddClient: name = system
Jack: JackGraphManager::SetBufferSize size = 128
Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackDriver::SetupDriverSync driver sem in flush mode
Jack: JackEngine::ClientInternalOpen: name = freewheel
Jack: JackEngine::AllocateRefNum ref = 1
Jack: JackPosixSemaphore::Allocate name = jack_sem.1001_default_freewheel val = 0
Jack: JackEngine::NotifyAddClient: name = freewheel
Jack: JackConnectionManager::DirectConnect first: ref1 = 1 ref2 = 1
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Jack: JackDriver::SetupDriverSync driver sem in flush mode
Jack: JackFFADODriver::Attach fBufferSize 128 fSampleRate 44100
00729154337:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0- built Aug 11 2010 00:12:04
firewire MSG: Streaming thread running with Realtime scheduling, priority 75
firewire MSG: Registering audio capture port firewire_pcm:000d6c0b0007221f_LineIn 1+2 left_in
Jack: JackGraphManager::AllocatePortAux port_index = 1 name = firewire_pcm:000d6c0b0007221f_LineIn 1+2 left_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 1
Jack: JackFFADODriver::Attach fCapturePortList[i] 1 
firewire MSG: Registering audio capture port firewire_pcm:000d6c0b0007221f_LineIn 1+2 right_in
Jack: JackGraphManager::AllocatePortAux port_index = 2 name = firewire_pcm:000d6c0b0007221f_LineIn 1+2 right_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 2
Jack: JackFFADODriver::Attach fCapturePortList[i] 2 
firewire MSG: Registering audio capture port firewire_pcm:000d6c0b0007221f_SpdifIn 1+2 left_in
Jack: JackGraphManager::AllocatePortAux port_index = 3 name = firewire_pcm:000d6c0b0007221f_SpdifIn 1+2 left_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 3
Jack: JackFFADODriver::Attach fCapturePortList[i] 3 
firewire MSG: Registering audio capture port firewire_pcm:000d6c0b0007221f_SpdifIn 1+2 right_in
Jack: JackGraphManager::AllocatePortAux port_index = 4 name = firewire_pcm:000d6c0b0007221f_SpdifIn 1+2 right_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 4
Jack: JackFFADODriver::Attach fCapturePortList[i] 4 
firewire MSG: Registering audio playback port firewire_pcm:000d6c0b0007221f_LineOut 1+2 left_out
Jack: JackGraphManager::AllocatePortAux port_index = 5 name = firewire_pcm:000d6c0b0007221f_LineOut 1+2 left_out type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 5
Jack: JackFFADODriver::Attach fPlaybackPortList[i] 5 
firewire MSG: Registering audio playback port firewire_pcm:000d6c0b0007221f_LineOut 1+2 right_out
Jack: JackGraphManager::AllocatePortAux port_index = 6 name = firewire_pcm:000d6c0b0007221f_LineOut 1+2 right_out type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 6
Jack: JackFFADODriver::Attach fPlaybackPortList[i] 6 
firewire MSG: Registering audio playback port firewire_pcm:000d6c0b0007221f_SpdifOut 1+2 left_out
Jack: JackGraphManager::AllocatePortAux port_index = 7 name = firewire_pcm:000d6c0b0007221f_SpdifOut 1+2 left_out type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 7
Jack: JackFFADODriver::Attach fPlaybackPortList[i] 7 
firewire MSG: Registering audio playback port firewire_pcm:000d6c0b0007221f_SpdifOut 1+2 right_out
Jack: JackGraphManager::AllocatePortAux port_index = 8 name = firewire_pcm:000d6c0b0007221f_SpdifOut 1+2 right_out type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 8
Jack: JackFFADODriver::Attach fPlaybackPortList[i] 8 
Jack: Clock source : system clock via clock_gettime
Jack: JackServer::Start
Jack: JackThreadedDriver::Start
[B][COLOR="Red"]libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 0.
firewire ERR: Could not start streaming threads
Cannot start driver
JackServer::Start() failed with -1[/COLOR][/B]
Jack: JackServer::Close
Jack: JackServerSocket::Close /dev/shm/jack_default_1001_0
Jack: JackFFADODriver::Detach
Jack: JackAudioDriver::Detach
Jack: JackGraphManager::DisconnectAllOutput port_index = 1 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 1 
Jack: JackGraphManager::DisconnectAllOutput port_index = 2 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 2 
Jack: JackGraphManager::DisconnectAllOutput port_index = 3 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 3 
Jack: JackGraphManager::DisconnectAllOutput port_index = 4 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 4 
Jack: JackGraphManager::DisconnectAllInput port_index = 5
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 5 
Jack: JackGraphManager::DisconnectAllInput port_index = 6
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 6 
Jack: JackGraphManager::DisconnectAllInput port_index = 7
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 7 
Jack: JackGraphManager::DisconnectAllInput port_index = 8
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 8 
Jack: JackDriver::Close
Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackEngine::ClientCloseAux ref = 0
Jack: JackGraphManager::RemoveAllPorts ref = 0
Jack: JackPosixSemaphore::Destroy
Jack: JackDriver::Close
Jack: JackConnectionManager::DirectDisconnect last: ref1 = 1 ref2 = 1
Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Jack: JackEngine::ClientCloseAux ref = 1
Jack: JackGraphManager::RemoveAllPorts ref = 1
Jack: JackPosixSemaphore::Destroy
Jack: JackEngine::Close
Jack: JackClientSocket::Close
Jack: no message buffer overruns
Jack: JackPosixThread::Stop
Jack: ThreadHandler: exit
Jack: Succeeded in unlocking 17370908 byte memory area
Jack: JackShmMem::delete size = 0 index = 0
Jack: ~JackDriver
no message buffer overruns
Jack: ~JackDriver
Jack: JackEngine::~JackEngine
Jack: Succeeded in unlocking 1012 byte memory area
Jack: JackShmMem::delete size = 0 index = 1
Jack: cleaning up shared memory
Jack: cleaning up files
Jack: unregistering server `default'
Failed to start server
16:58:40.537 JACK was stopped with exit status=255.
16:58:40.538 Post-shutdown script...
16:58:40.539 killall jackd
jackd: no process found
16:58:40.949 Post-shutdown script terminated with exit status=256.
```

So the issue is now:

```
libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 0.
firewire ERR: Could not start streaming threads

```

SO... this seems to be an issue with the FFADO backend. Ideas?

---

### Post by Forum User on 2011-01-05
Tested FFADO:

```
ffado-test -n0 ListDevices

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x000d6c0b0007221f  0x00000D6C  0x00010062   M-Audio - FW Solo
02627200176: Error (configrom.cpp)[ 150] initialize: Could not parse config rom of node 1 on port 0

```

Wait, what? It sees the FW Solo, but it can't... something... in Jackd. Lets check the ports in jack:

```
[COLOR="Blue"]~$ jackd -R -dfirewire -p1024 -r48000 -n0 -v3[/COLOR]
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
03215249766:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0- built Aug 11 2010 00:12:04
03215345103: [COLOR="Red"]Warning (ieee1394service.cpp)[ 375] initialize: Could not set SPLIT_TIMEOUT to min requested (1000000)[/COLOR]
03215345131: [COLOR="red"]Warning (ieee1394service.cpp)[ 379] initialize: Set SPLIT_TIMEOUT to min requested (1000000) did not succeed[/COLOR]
libiec61883 [COLOR="red"]warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 0.[/COLOR]
03216078477: Error (ieee1394service.cpp)[1413] allocateIsoChannelCMP: Could not do CMP from FFC0:00 to FFC1:-1
03216078515: Error (avc_avdevice.cpp)[ 816] startStreamByIndex: Could not allocate ISO channel for SP 0
03216078547: [COLOR="red"]Warning (devicemanager.cpp)[ 863] startStreamingOnDevice: Could not start stream 0 of device 0x97ff508[/COLOR]
03216078560: [COLOR="red"]Warning (devicemanager.cpp)[ 900] startStreaming: Could not start streaming on device 0x97ff508![/COLOR]
firewire ERR: Could not start streaming threads
Cannot start driver
JackServer::Start() failed with -1
03216078572: Fatal (ffado.cpp)[ 211] ffado_streaming_start: Could not start the streaming system
no message buffer overruns
Failed to start server

```

Problem seems to be with the line [FONT="Lucida Console"]Could not set SPLIT_TIMEOUT to min requested (1000000)[/FONT]... Anyone know what that means?

---

### Post by Forum User on 2011-01-07
Here is the solution: use the onboard soundcard the motherboard has. Works fine. No recording, but Windows can do that. Sigh.

---

### Post by pedrogent on 2011-01-09
Sorry to read about your pain. I've been trying, off & on, for about 3 years now to get the M-Audio FireWire Solo to work with Ubuntu ([http://brainstorm.ubuntu.com/idea/2800/](http://brainstorm.ubuntu.com/idea/2800/)). I've given up now as I really can't see it happening.

It's either OS X or Windows if you want to record with this card. 'Tis a shame.

---

### Post by cchhrriiss121212 on 2011-01-09
With maverick and natty, supported firewire devices should be plug and play. This is because of the new stack, if you load the old stack you will need to follow the old setup methods:
> **trulan said:**
> On Maverick - Don't run Ubuntu Studio Controls, and don't start up your computer with the device plugged in.  You may need to reconfigure jackd to enable memlocking and rt scheduling, if you did not select allowing these when jack was installed.  Other than that, it should just work.  Start the computer, plug in the firewire device, start Jack, and have fun!

On Lucid - exactly the opposite.  Do run Ubuntu Studio Controls and enable raw1394, do reboot your computer with the device plugged in.


Regarding the solo, someone here reports it does not work with the new stack:
[http://www.ffado.org/?q=node/13]("http://www.ffado.org/?q=node/13")

FWIW, I suggested a mod move this to the studio forum as there are many firewire experts there, but that was ignored for some reason.

---

### Post by bdlandry on 2011-03-12
M-Audio firewire solo does work ... at least it does with KXStudio 10.04.3.

Just plug it in (supposedly the proper procedure is to turn everything off, computer and solo ... plug the solo into the computer .. power up the solo and then the computer ... this is to protect your solo and computer, not necessarily needed, but M-Audio warns that "hot-plugging" has been known to permanently damage hardware.)

Start ladish (if it starts Jack, then in ladish go to  "Studio - Stop Studio") then go to "Tools -> Configure Jack -> Jack engine parameters -> change "driver" from alsa to firewire.

Just got my solo yesterday, so haven't had a lot of time to mess with it ... one problem I see is that it looks like it's only operating at 16bit samples. So far I've been able to run it at a period of between 32 to 96 depending upon how complex the sound I am trying to make ... I just got it mostly to so some recording with acoustic guitar, vocals, maybe some fiddle and mandolin and use a little bit of computer bass and drums .. and just for fun, so 16bit is probably good enough for that.

---

