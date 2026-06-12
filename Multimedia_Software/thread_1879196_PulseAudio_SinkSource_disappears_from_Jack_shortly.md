---
title: "PulseAudio Sink/Source disappears from Jack shortly after start in 11.10"
date: 2011-11-11
forum: Multimedia Software
---

### Post by smaring on 2011-11-11
Prior to the upgrade to 11.10 on my 64bit laptop, I had the pulseaudio sink and source show up in qjackctl just fine.  Now, after the upgrade, I see them show up in the ports list for about 2 seconds after I click "start", and then they go away!

I still have:

exec on start:        pulseaudio -k
exec after start:     pulseaudio -DnF ~/.pulse/pulsejack.pa
exec on shutdown:     pulseaudio -k
exec after shutdown:  killall jackd; pulse-session


When I click "stop", I can see in the logs:

```
jackd: no process found
sh: pulse-session: not found
```


What exactly was "pulse-session", and where did it go?

Here's what the logs have to say about Pulse when I click "start":

```
Jack: JackClient::AddClient name = PulseAudio JACK Sink, ref = 4 
Jack: JackPosixSemaphore::Connect jack_sem.1000_default_PulseAudio JACK Sink
Jack: JackClient::kAddClient fName = qjackctl name = PulseAudio JACK Sink
Jack: JackClient::AddClient name = PulseAudio JACK Source, ref = 5 
Jack: JackPosixSemaphore::Connect jack_sem.1000_default_PulseAudio JACK Source
Jack: JackClient::kAddClient fName = qjackctl name = PulseAudio JACK Source
Fri Nov 11 04:59:02 2011: Jack: JackEngine::ClientExternalOpen: uuid = 1, name = PulseAudio JACK Sink 
Fri Nov 11 04:59:02 2011: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_PulseAudio JACK Sink val = 0
Fri Nov 11 04:59:02 2011: Jack: JackSocketNotifyChannel::Open name = PulseAudio JACK Sink
Fri Nov 11 04:59:02 2011: Jack: Connect: addr.sun_path /dev/shm/jack_PulseAudio JACK Sink_1000_0
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::Open name = PulseAudio JACK Sink index = 3 base = 99ea8000
Fri Nov 11 04:59:02 2011: Jack: JackEngine::NotifyAddClient: name = PulseAudio JACK Sink
Fri Nov 11 04:59:02 2011: Jack: JackClient::kAddClient fName = dbusapi name = PulseAudio JACK Sink
Fri Nov 11 04:59:02 2011: Jack: client 'PulseAudio JACK Sink' created
Fri Nov 11 04:59:02 2011: New client 'PulseAudio JACK Sink' with PID 28631
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 0
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 0
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 0
Fri Nov 11 04:59:02 2011: Jack: JackEngine::PortRegister ref = 4 name = PulseAudio JACK Sink:front-left type = 32 bit float mono audio flags = 18 buffer_size = 0
Fri Nov 11 04:59:02 2011: Jack: JackGraphManager::AllocatePortAux port_index = 7 name = PulseAudio JACK Sink:front-left type = 32 bit float mono audio
Fri Nov 11 04:59:02 2011: Jack: JackEngine::PortRegister ref = 4 name = PulseAudio JACK Sink:front-right type = 32 bit float mono audio flags = 18 buffer_size = 0
Fri Nov 11 04:59:02 2011: Jack: JackGraphManager::AllocatePortAux port_index = 8 name = PulseAudio JACK Sink:front-right type = 32 bit float mono audio
Fri Nov 11 04:59:02 2011: Jack: JackEngine::ClientActivate ref = 4 name = PulseAudio JACK Sink
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 2
Fri Nov 11 04:59:02 2011: Jack: port 'PulseAudio JACK Sink:front-left' created
Fri Nov 11 04:59:02 2011: Jack: port 'PulseAudio JACK Sink:front-right' created
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 18
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 18
Fri Nov 11 04:59:02 2011: Jack: JackEngine::PortConnect src = PulseAudio JACK Sink:front-left dst = system:playback_1
Fri Nov 11 04:59:02 2011: Jack: JackGraphManager::CheckConnect src_name = PulseAudio JACK Sink:front-left dst_name = system:playback_1
Fri Nov 11 04:59:02 2011: Connecting 'PulseAudio JACK Sink:front-left' to 'system:playback_1'
Fri Nov 11 04:59:02 2011: Jack: JackEngine::PortConnect src = PulseAudio JACK Sink:front-right dst = system:playback_2
Fri Nov 11 04:59:02 2011: Jack: JackGraphManager::CheckConnect src_name = PulseAudio JACK Sink:front-right dst_name = system:playback_2
Fri Nov 11 04:59:02 2011: Connecting 'PulseAudio JACK Sink:front-right' to 'system:playback_2'
Fri Nov 11 04:59:02 2011: Jack: JackEngine::ClientExternalOpen: uuid = 2, name = PulseAudio JACK Source 
Fri Nov 11 04:59:02 2011: Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_default_PulseAudio JACK Source val = 0
Fri Nov 11 04:59:02 2011: Jack: JackSocketNotifyChannel::Open name = PulseAudio JACK Source
Fri Nov 11 04:59:02 2011: Jack: Connect: addr.sun_path /dev/shm/jack_PulseAudio JACK Source_1000_0
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::Open name = PulseAudio JACK Source index = 4 base = 99ea6000
Fri Nov 11 04:59:02 2011: Jack: JackEngine::NotifyAddClient: name = PulseAudio JACK Source
Fri Nov 11 04:59:02 2011: Jack: JackClient::kAddClient fName = dbusapi name = PulseAudio JACK Source
Fri Nov 11 04:59:02 2011: Jack: client 'PulseAudio JACK Source' created
Fri Nov 11 04:59:02 2011: New client 'PulseAudio JACK Source' with PID 28631
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 0
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 0
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 0
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 0
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 0
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 18
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 18
Fri Nov 11 04:59:02 2011: Jack: JackEngine::PortRegister ref = 5 name = PulseAudio JACK Source:front-left type = 32 bit float mono audio flags = 17 buffer_size = 0
Fri Nov 11 04:59:02 2011: Jack: JackGraphManager::AllocatePortAux port_index = 9 name = PulseAudio JACK Source:front-left type = 32 bit float mono audio
Fri Nov 11 04:59:02 2011: Jack: JackEngine::PortRegister ref = 5 name = PulseAudio JACK Source:front-right type = 32 bit float mono audio flags = 17 buffer_size = 0
Fri Nov 11 04:59:02 2011: Jack: JackGraphManager::AllocatePortAux port_index = 10 name = PulseAudio JACK Source:front-right type = 32 bit float mono audio
Fri Nov 11 04:59:02 2011: Jack: JackEngine::ClientActivate ref = 5 name = PulseAudio JACK Source
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 2
Fri Nov 11 04:59:02 2011: Jack: port 'PulseAudio JACK Source:front-left' created
Fri Nov 11 04:59:02 2011: Jack: port 'PulseAudio JACK Source:front-right' created
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 18
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 18
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 18
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 18
Fri Nov 11 04:59:02 2011: Jack: JackEngine::PortConnect src = system:capture_1 dst = PulseAudio JACK Source:front-left
Fri Nov 11 04:59:02 2011: Jack: JackGraphManager::CheckConnect src_name = system:capture_1 dst_name = PulseAudio JACK Source:front-left
Fri Nov 11 04:59:02 2011: Connecting 'system:capture_1' to 'PulseAudio JACK Source:front-left'
Fri Nov 11 04:59:02 2011: Jack: JackEngine::PortConnect src = system:capture_2 dst = PulseAudio JACK Source:front-right
Fri Nov 11 04:59:02 2011: Jack: JackGraphManager::CheckConnect src_name = system:capture_2 dst_name = PulseAudio JACK Source:front-right
Fri Nov 11 04:59:02 2011: Connecting 'system:capture_2' to 'PulseAudio JACK Source:front-right'
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 18
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 18
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 18
Fri Nov 11 04:59:02 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 18
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not run: state = 1ESC[0m
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: JackEngine::XRun: client = PulseAudio JACK Source was not run: state = 1ESC[0m
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not run: state = 1ESC[0m
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: JackEngine::XRun: client = PulseAudio JACK Source was not run: state = 1ESC[0m
Fri Nov 11 04:59:03 2011: Jack: JackEngine::ClientDeactivate ref = 4 name = PulseAudio JACK Sink
Fri Nov 11 04:59:03 2011: Disconnecting 'PulseAudio JACK Sink:front-left' from 'system:playback_1'
Jack: JackClient::RemoveClient name = PulseAudio JACK Sink, ref = 4 
Jack: JackPosixSemaphore::Disconnect jack_sem.1000_default_PulseAudio JACK Sink
Jack: JackClient::kRemoveClient fName = qjackctl name = PulseAudio JACK Sink
Jack: JackClient::RemoveClient name = PulseAudio JACK Source, ref = 5 
Jack: JackPosixSemaphore::Disconnect jack_sem.1000_default_PulseAudio JACK Source
Jack: JackClient::kRemoveClient fName = qjackctl name = PulseAudio JACK Source
Fri Nov 11 04:59:03 2011: Disconnecting 'PulseAudio JACK Sink:front-right' from 'system:playback_2'
Fri Nov 11 04:59:03 2011: Jack: port 'PulseAudio JACK Sink:front-left' destroyed
Fri Nov 11 04:59:03 2011: Jack: port 'PulseAudio JACK Sink:front-right' destroyed
Fri Nov 11 04:59:03 2011: Jack: port 'PulseAudio JACK Sink:front-left' destroyed
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: Failed to find port 'PulseAudio JACK Sink:front-left' to destroyESC[0m
Fri Nov 11 04:59:03 2011: Jack: port 'PulseAudio JACK Sink:front-right' destroyed
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: Failed to find port 'PulseAudio JACK Sink:front-right' to destroyESC[0m
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: JackEngine::XRun: client = PulseAudio JACK Source was not run: state = 1ESC[0m
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: JackEngine::XRun: client = PulseAudio JACK Source was not run: state = 1ESC[0m
Fri Nov 11 04:59:03 2011: Jack: JackClient::kRemoveClient fName = dbusapi name = PulseAudio JACK Sink
Fri Nov 11 04:59:03 2011: Jack: client 'PulseAudio JACK Sink' destroyed
Fri Nov 11 04:59:03 2011: Client 'PulseAudio JACK Sink' with PID 28631 is out
Fri Nov 11 04:59:03 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 1
Fri Nov 11 04:59:03 2011: Jack: JackExternalClient::ClientNotify ref = 4 name = PulseAudio JACK Sink notify = 1
Fri Nov 11 04:59:03 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 18
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: NotifyClient fails name = PulseAudio JACK Source event = 18 val1 = 0 val2 = 0ESC[0m
Fri Nov 11 04:59:03 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 18
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: NotifyClient fails name = PulseAudio JACK Source event = 18 val1 = 1 val2 = 0ESC[0m
Fri Nov 11 04:59:03 2011: Jack: JackEngine::ClientDeactivate ref = 5 name = PulseAudio JACK Source
Fri Nov 11 04:59:03 2011: Disconnecting 'system:capture_1' from 'PulseAudio JACK Source:front-left'
Fri Nov 11 04:59:03 2011: Disconnecting 'system:capture_2' from 'PulseAudio JACK Source:front-right'
Fri Nov 11 04:59:03 2011: Jack: port 'PulseAudio JACK Source:front-left' destroyed
Fri Nov 11 04:59:03 2011: Jack: port 'PulseAudio JACK Source:front-right' destroyed
Fri Nov 11 04:59:03 2011: Jack: port 'PulseAudio JACK Source:front-left' destroyed
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: Failed to find port 'PulseAudio JACK Source:front-left' to destroyESC[0m
Fri Nov 11 04:59:03 2011: Jack: port 'PulseAudio JACK Source:front-right' destroyed
Fri Nov 11 04:59:03 2011: ESC[1mESC[31mERROR: Failed to find port 'PulseAudio JACK Source:front-right' to destroyESC[0m
Fri Nov 11 04:59:04 2011: Jack: JackClient::kRemoveClient fName = dbusapi name = PulseAudio JACK Source
Fri Nov 11 04:59:04 2011: Jack: client 'PulseAudio JACK Source' destroyed
Fri Nov 11 04:59:04 2011: Client 'PulseAudio JACK Source' with PID 28631 is out
Fri Nov 11 04:59:04 2011: Jack: JackExternalClient::ClientNotify ref = 5 name = PulseAudio JACK Source notify = 1
```


It looks like the start of my troubles are these lines:

ERROR: JackEngine::XRun: client = PulseAudio JACK Sink was not run: state = 1

... but I'm not real sure what that is telling me.


Thanks,
Steve Maring
Tampa, FL  USA

---

### Post by shaneo1 on 2011-11-16
I too have just done a fresh install of Ubuntu 11.10 and needed to setup pulseaudio to run through JACK so this should help you too.

In the USC (Ubuntu Software Centre) type pulseaudio-module-jack and install it.

Then open terminal
```
# sudo gedit /etc/pulse/default.pa
```Edit the text document:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=207333&stc=1&d=1321469841[/IMG]

Search the title highlighted in yellow and add the two lines in orange and save.

Now in terminal type:
```
# killall pulseaudio
```of course pulseaudio will restart.

Now open QJACKCTRL and click on the start button.  You should now have PulseAudioSink.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=207334&stc=1&d=1321470158[/IMG]

  ENJOY :guitar:

This method will direct pulseaudio through Jack on startup.  To kill the process you will need to type: killall pulseaudio to reset pulse to use your soundcard directly.  

If you want to only direct pulse on qjackctrl start up and disable it on shutdown use the following  4 scripts.  I would advise putting them in your home folder.

---

### Post by shaneo1 on 2011-11-16
The scripts are attached at the bottom of this post.

They will enable all apps that use pulseaudio to still be about to play through pulseaudio is sinked with Jack.

Make sure you go to set up in qjackctrl and click on options and enable execution of scripts in the following order:

pulse-jack-pre-start.sh
pulse-jack-post-start.sh
pulse-jack-pre-stop.sh
pulse-jack-post-stop.sh

Enjoy :popcorn:

---

### Post by shaneo1 on 2011-11-16
One thing I forgot to mention was to hear pulseaudio-jack ensure you enable the JackSink audio module in Sound settings to hear pulseaudio.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=207340&stc=1&d=1321472359[/IMG]

---

### Post by miscellanyous on 2012-10-23
Thanks this did the trick for me on Ubuntu 11.10. Banshee, Firefox sound works with qjackctl.

---

