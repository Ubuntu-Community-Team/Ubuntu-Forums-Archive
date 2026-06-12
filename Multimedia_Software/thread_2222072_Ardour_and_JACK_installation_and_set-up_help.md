---
title: "Ardour and JACK installation and set-up help"
date: 2014-05-05
forum: Multimedia Software
---

### Post by james_birkbeck on 2014-05-05
Hello.
I am brand new at Linux and have spent the whole day trying to get my HP laptop to have the capability of running a multitrack recording app in Ubuntu.
So, I downloaded a program called Ardour. I haven't installed it yet, because I noticed it said I need to have something called JACK first.
So, I downloaded JACK, and did my best to follow instructions on how to install it, and configure it to work with my Avid Fast Track.
However, when I try to start it, I get the following error:

[COLOR=#ff0000]22:48:56.655 D-BUS: JACK server could not be started. Sorry[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server request channel[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Starting jack server...[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: Server `default' registered[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackConnectionManager::InitConnections size = 6522944 [/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackConnectionManager::InitClients[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: JACK server starting in non-realtime mode[/COLOR]

 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackShmMem::new index = 0 attached = ae180000 size = 82274202 [/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackShmMem::new placement size = 13047706[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: ERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackConnectionManager::InitConnections size = 6522944 [/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackConnectionManager::InitClients[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackConnectionManager::InitConnections size = 6522944 [/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackConnectionManager::InitClients[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackShmMem::new index = 1 attached = bf220000 size = 1186 [/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: Succeeded in locking 1186 byte memory area[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackPosixThread::StartImp : create non RT thread[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackPosixThread::ThreadHandler : start[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: playback device hw:0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: capture device hw:0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: capture device hw:0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: playback device hw:0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: apparent rate = 48000[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: frames per period = 256[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackDriver::Open capture_driver_name = hw:0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackDriver::Open playback_driver_name = hw:0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: Check protocol client = 8 server = 8[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackEngine::ClientInternalOpen: name = system[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackEngine::AllocateRefNum ref = 0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackEngine::NotifyAddClient: name = system[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackGraphManager::SetBufferSize size = 256[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackDriver::SetupDriverSync driver sem in flush mode[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: ERROR: Audio device hw:0 cannot be acquired...[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: ~JackDriver[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: ERROR: Cannot initialize driver[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: no message buffer overruns[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackPosixThread::Stop[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackPosixThread::ThreadHandler : exit[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: ERROR: JackServer::Open failed with -1[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: Succeeded in unlocking 82274202 byte memory area[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackShmMem::delete size = 0 index = 0[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: ~JackDriver[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: Succeeded in unlocking 1186 byte memory area[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: JackShmMem::delete size = 0 index = 1[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: Cleaning up shared memory[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: Cleaning up files[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: Jack: Unregistering server `default'[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:56 2014: ERROR: Failed to open server[/COLOR]
 [COLOR=#999999]Sun May  4 22:48:57 2014: Saving settings to "/home/james/.config/jack/conf.xml" ...[/COLOR]
 [COLOR=#ff0000]22:48:58.669 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server request channel[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]

Any help would be greatly appreciated.
:confused:

Thank you.
~James

---

### Post by CraigPid on 2014-05-06
Forget about trying to set up Ubuntu for audio recording and install Ubuntu Studio instead. Jack and Ardour are installed along with a lot of other multimedia software you could try out. And the system is configured properly for multi-track audio recording. If you're new to Linux you have enough to learn without having to configure your system to run Ardour.

---

### Post by CraigPid on 2014-05-06
About you Jack issue anyway? Are you starting it from command line? What is the command? Does your laptop have onboard sound. Jack could be trying to use that card instead of the Fast Track. Still your best bet would be Ubuntu Studio. There's a section in the forum.

---

