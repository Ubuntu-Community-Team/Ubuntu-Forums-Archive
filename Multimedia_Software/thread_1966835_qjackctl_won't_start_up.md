---
title: "qjackctl won't start up"
date: 2012-04-27
forum: Multimedia Software
---

### Post by baruch60610 on 2012-04-27
I'm trying to get Rosegarden working.  It requires jack.  When I try to run qjackctl, I am told it can't start (see message listing below).

I'm using an ASUS UL80JT laptop and running Kubuntu.  I've got an Intel ALC269VB Analog sound card.  I'm using alsa, whatever that means (it came with the distro).  The only major change I've made was that, upon advice I got here, I removed pulseaudio.  I don't know whether this would mess up qjackctl, but removing it did help with another audio problem I had.

Can anyone tell me what's going wrong - or, better yet - tell me where I can find information about how to set up the audio stuff?  I've Googled around trying to find answers, but apparently either this isn't a common problem, or else I'm just not getting it.

Thanks.

I found a sort of "solution" though I'm not happy with it.  For reasons that have eluded my feeble understanding, when I set qjackctl's driver to "net" it suddenly works.  Or at least, it lets me run Rosegarden and get sound out of it.

While it's nice to get sound now, I am concerned about this "voodoo programming" sort of thing.  Since I don't know why it works, if it stops working, I won't know why it stopped working.  Still, since I *already* didn't know why it wasn't working, I guess I'm no worse off.



```

Cannot connect to server socket
 jack server is not running or cannot be started
 11:10:28.247 D-BUS: JACK server could not be started. Sorry
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: driver "alsa" selected
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Saving settings to "/home/baruch/.config/jack/conf.xml" ...
 Fri Apr 27 11:10:28 2012: Starting jack server...
 Fri Apr 27 11:10:28 2012: Jack: server `default' registered
 Fri Apr 27 11:10:28 2012: Jack: JackConnectionManager::InitConnections size = 6522944 
 Fri Apr 27 11:10:28 2012: Jack: JackConnectionManager::InitClients
 Fri Apr 27 11:10:28 2012: JACK server starting in realtime mode with priority 10
 Fri Apr 27 11:10:28 2012: Jack: JackShmMem::new index = 0 attached = 9eeb3000 size = 82241434 
 Fri Apr 27 11:10:28 2012: Jack: JackShmMem::new placement size = 13047706
 Fri Apr 27 11:10:28 2012: [1m[31mERROR: Cannot lock down memory area (Cannot allocate memory)[0m
 Fri Apr 27 11:10:28 2012: Jack: JackConnectionManager::InitConnections size = 6522944 
 Fri Apr 27 11:10:28 2012: Jack: JackConnectionManager::InitClients
 Fri Apr 27 11:10:28 2012: Jack: JackConnectionManager::InitConnections size = 6522944 
 Fri Apr 27 11:10:28 2012: Jack: JackConnectionManager::InitClients
 Fri Apr 27 11:10:28 2012: Jack: JackShmMem::new index = 1 attached = a5c8b000 size = 994 
 Fri Apr 27 11:10:28 2012: Jack: Succeeded in locking 994 byte memory area
 Fri Apr 27 11:10:28 2012: Jack: Create non RT thread
 Fri Apr 27 11:10:28 2012: Jack: ThreadHandler: start
 Fri Apr 27 11:10:28 2012: Jack: playback device hw:0
 Fri Apr 27 11:10:28 2012: Jack: capture device hw:0
 Fri Apr 27 11:10:28 2012: Jack: apparent rate = 44100
 Fri Apr 27 11:10:28 2012: Jack: frames per period = 1024
 Fri Apr 27 11:10:28 2012: Jack: JackDriver::Open capture_driver_name = hw:0
 Fri Apr 27 11:10:28 2012: Jack: JackDriver::Open playback_driver_name = hw:0
 Fri Apr 27 11:10:28 2012: Jack: Check protocol client 8 server = 8
 Fri Apr 27 11:10:28 2012: Jack: JackEngine::ClientInternalOpen: name = system
 Fri Apr 27 11:10:28 2012: Jack: JackEngine::AllocateRefNum ref = 0
 Fri Apr 27 11:10:28 2012: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_system val = 0
 Fri Apr 27 11:10:28 2012: Jack: JackEngine::NotifyAddClient: name = system
 Fri Apr 27 11:10:28 2012: Jack: JackGraphManager::SetBufferSize size = 1024
 Fri Apr 27 11:10:28 2012: Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
 Fri Apr 27 11:10:28 2012: Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
 Fri Apr 27 11:10:28 2012: Jack: JackDriver::SetupDriverSync driver sem in flush mode
 Fri Apr 27 11:10:28 2012: control device hw:0
 Fri Apr 27 11:10:28 2012: control device hw:0
 Fri Apr 27 11:10:28 2012: [1m[31mERROR: Failed to acquire device name : Audio0 error : Input/output error[0m
 Fri Apr 27 11:10:28 2012: [1m[31mERROR: Audio device hw:0 cannot be acquired, trying to open it anyway...[0m
 Fri Apr 27 11:10:28 2012: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|2|nomon|swmeter|-|32bit
 Fri Apr 27 11:10:28 2012: control device hw:0
 Fri Apr 27 11:10:28 2012: [1m[31mERROR: the playback device "hw:0" is already in use. Please stop the application using it and run JACK again[0m
 Fri Apr 27 11:10:28 2012: Jack: JackDriver::Close
 Fri Apr 27 11:10:28 2012: Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
 Fri Apr 27 11:10:28 2012: Jack: JackGraphManager::DisconnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
 Fri Apr 27 11:10:28 2012: Jack: JackEngine::ClientCloseAux ref = 0
 Fri Apr 27 11:10:28 2012: Jack: JackGraphManager::RemoveAllPorts ref = 0
 Fri Apr 27 11:10:28 2012: Jack: JackPosixSemaphore::Destroy
 Fri Apr 27 11:10:28 2012: Jack: ~JackDriver
 Fri Apr 27 11:10:28 2012: [1m[31mERROR: Cannot initialize driver[0m
 Fri Apr 27 11:10:28 2012: Jack: no message buffer overruns
 Fri Apr 27 11:10:28 2012: Jack: JackPosixThread::Stop
 Fri Apr 27 11:10:28 2012: Jack: ThreadHandler: exit
 Fri Apr 27 11:10:28 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
 Fri Apr 27 11:10:28 2012: Jack: Succeeded in unlocking 82241434 byte memory area
 Fri Apr 27 11:10:28 2012: Jack: JackShmMem::delete size = 0 index = 0
 Fri Apr 27 11:10:28 2012: Jack: ~JackDriver
 Fri Apr 27 11:10:28 2012: Jack: Succeeded in unlocking 994 byte memory area
 Fri Apr 27 11:10:28 2012: Jack: JackShmMem::delete size = 0 index = 1
 Fri Apr 27 11:10:28 2012: Jack: cleaning up shared memory
 Fri Apr 27 11:10:28 2012: Jack: cleaning up files
 Fri Apr 27 11:10:28 2012: Jack: unregistering server `default'
 Fri Apr 27 11:10:28 2012: [1m[31mERROR: Failed to open server[0m
 11:10:30.271 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started

```

---

### Post by lykwydchykyn on 2012-04-27
Looks like the problem is that it can't "claim" the audio hardware.  My guess is that it's conflicting with pulseaudio.

See this page about jack and pulseaudio:

[http://jackaudio.org/pulseaudio_and_jack](http://jackaudio.org/pulseaudio_and_jack)

---

### Post by baruch60610 on 2012-04-27
Hi, [lykwydchykyn]("http://ubuntuforums.org/member.php?u=603141").  Thanks for your suggestion.  Unfortunately, I already removed PulseAudio, so that wasn't the problem - or at least, it wasn't a conflict with jack.

But I am going to go through the site you linked to, which will probably have the information I need to fix the problem.  That should be a big help.  If I find a solution, of course I'll post it here.

---

