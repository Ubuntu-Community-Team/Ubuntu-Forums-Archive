---
title: "Jack Failed to acquire device name"
date: 2013-04-20
forum: Multimedia Software
---

### Post by fauzie on 2013-04-20
I am a happy ardour user for quite a while, until my computer crashed and I have to change my motherboard. I move all of my old hardware in the new motherboard. I expect problems, but apparently everything worked just fine, until the moment I tried to run jack, which is used to work perfectly. I tried to remove and reinstall jack, but still cannot get it to work. I'm pretty sure it is just a simple misconfiguration, but I cannot find what's wrong :(

I hope someone here can help me out.
Here is the code from jack's output

```

07:23:00.431 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Sun Apr 21 07:23:00 2013: Starting jack server...
Sun Apr 21 07:23:00 2013: Jack: server `default' registered
Sun Apr 21 07:23:00 2013: Jack: JackConnectionManager::InitConnections size = 6522944 
Sun Apr 21 07:23:00 2013: Jack: JackConnectionManager::InitClients
Sun Apr 21 07:23:00 2013: JACK server starting in realtime mode with priority 10
Sun Apr 21 07:23:00 2013: Jack: JackShmMem::new index = 0 attached = b04d5000 size = 82241434 
Sun Apr 21 07:23:00 2013: Jack: JackShmMem::new placement size = 13047706
Sun Apr 21 07:23:00 2013: Jack: Succeeded in locking 82241434 byte memory area
Sun Apr 21 07:23:00 2013: Jack: JackConnectionManager::InitConnections size = 6522944 
Sun Apr 21 07:23:00 2013: Jack: JackConnectionManager::InitClients
Sun Apr 21 07:23:00 2013: Jack: JackConnectionManager::InitConnections size = 6522944 
Sun Apr 21 07:23:00 2013: Jack: JackConnectionManager::InitClients
Sun Apr 21 07:23:00 2013: Jack: JackShmMem::new index = 1 attached = b77ad000 size = 994 
Sun Apr 21 07:23:00 2013: Jack: Succeeded in locking 994 byte memory area
Sun Apr 21 07:23:00 2013: Jack: Create non RT thread
Sun Apr 21 07:23:00 2013: Jack: ThreadHandler: start
Sun Apr 21 07:23:00 2013: Jack: capture device hw:1
Sun Apr 21 07:23:00 2013: Jack: playback device hw:0
Sun Apr 21 07:23:00 2013: Jack: playback device hw:1
Sun Apr 21 07:23:00 2013: Jack: capture device hw:1
Sun Apr 21 07:23:00 2013: Jack: apparent rate = 44100
Sun Apr 21 07:23:00 2013: Jack: frames per period = 1024
Sun Apr 21 07:23:00 2013: Jack: JackDriver::Open capture_driver_name = hw:1
Sun Apr 21 07:23:00 2013: Jack: JackDriver::Open playback_driver_name = hw:1
Sun Apr 21 07:23:00 2013: Jack: Check protocol client = 8 server = 8
Sun Apr 21 07:23:00 2013: Jack: JackEngine::ClientInternalOpen: name = system
Sun Apr 21 07:23:00 2013: Jack: JackEngine::AllocateRefNum ref = 0
Sun Apr 21 07:23:00 2013: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
Sun Apr 21 07:23:00 2013: Jack: JackEngine::NotifyAddClient: name = system
Sun Apr 21 07:23:00 2013: Jack: JackGraphManager::SetBufferSize size = 1024
Sun Apr 21 07:23:00 2013: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Sun Apr 21 07:23:00 2013: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Sun Apr 21 07:23:00 2013: Jack: JackDriver::SetupDriverSync driver sem in flush mode
Sun Apr 21 07:23:00 2013: control device hw:1
Sun Apr 21 07:23:00 2013: control device hw:1
Sun Apr 21 07:23:00 2013: [1m[31mERROR: Failed to acquire device name : Audio1 error : Cannot allocate memory[0m
Sun Apr 21 07:23:00 2013: [1m[31mERROR: Audio device hw:1 cannot be acquired...[0m
Sun Apr 21 07:23:00 2013: Jack: ~JackDriver
Sun Apr 21 07:23:00 2013: [1m[31mERROR: Cannot initialize driver[0m
Sun Apr 21 07:23:00 2013: Jack: no message buffer overruns
Sun Apr 21 07:23:00 2013: Jack: JackPosixThread::Stop
Sun Apr 21 07:23:00 2013: Jack: ThreadHandler: exit
Sun Apr 21 07:23:00 2013: [1m[31mERROR: JackServer::Open() failed with -1[0m
Sun Apr 21 07:23:00 2013: Jack: Succeeded in unlocking 82241434 byte memory area
Sun Apr 21 07:23:00 2013: Jack: JackShmMem::delete size = 0 index = 0
Sun Apr 21 07:23:00 2013: Jack: ~JackDriver
Sun Apr 21 07:23:00 2013: Jack: Succeeded in unlocking 994 byte memory area
Sun Apr 21 07:23:00 2013: Jack: JackShmMem::delete size = 0 index = 1
Sun Apr 21 07:23:00 2013: Jack: cleaning up shared memory
Sun Apr 21 07:23:00 2013: Jack: cleaning up files
Sun Apr 21 07:23:00 2013: Jack: unregistering server `default'
Sun Apr 21 07:23:00 2013: [1m[31mERROR: Failed to open server[0m
```

It seems to keep saying something along this line
Failed to acquire device name : Audio1

I used pasuspender to stop pulseaudio to mess with jack. I also tried to use the other soundcard present in my system, with the same result (the error message simply changed to "Failed to acquire device name : Audio0".

Any help will be greatly appreciated.

---

### Post by fauzie on 2013-04-22
I don't think I did anything useful ... but it works now. I've tried to record with Ardour, it works just fine.

This morning I turned on my box and launched QJackCtl. I changed the sample rate to 48000 from 44100, and changed the Priority from 10 to 89. I clicked on Start and jack started without complains. Then I received tons of XRuns messages. I changed the Priority setting back to 10 and the XRuns disappeared. So the only thing changed was the sample rate. 

Being curious I changed the sample rate back to 44100. No problem. So I guess jack managed to fixed itself somehow ... I cannot reproduce the error.

---

