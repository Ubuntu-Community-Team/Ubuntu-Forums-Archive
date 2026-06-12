---
title: "Jack control errors"
date: 2011-01-19
forum: Multimedia Software
---

### Post by nnjond on 2011-01-19
Hi,

Can anyone help me please?

Evidently I need to run Jack Control in combination with Qsynth to play my midi keyboard. That was ok for about a week or so, then Jack developed a problem. This was solved the first time by me unticking the Realtime box in Jack setup, but that has not worked this time.

Must I rely on Jack just to have my midi keyboard sound?

The errors mssges I recieve are:

Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.

and;
```

12:45:12.427 Patchbay deactivated.
12:45:12.480 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
12:45:12.533 ALSA connection graph change.
12:45:12.971 ALSA connection change.
12:45:44.736 Startup script...
12:45:44.737 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
12:45:45.142 Startup script terminated with exit status=32512.
12:45:45.142 JACK is starting...
12:45:45.142 /usr/bin/jackd -r -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
12:45:45.153 JACK was started with PID=2008.
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in non-realtime mode
Cannot lock down memory area (Cannot allocate memory)
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 0 - Alesis Q25 at usb-0000:00:02.0-3, full speed
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
12:45:45.364 JACK was stopped with exit status=255.
12:45:45.364 Post-shutdown script...
12:45:45.364 killall jackd
jackd: no process found
12:45:45.771 Post-shutdown script terminated with exit status=256.
12:45:47.294 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
12:45:55.100 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

---

### Post by cchhrriiss121212 on 2011-01-19
Try this:
```
sudo dpkg-reconfigure -p high jackd2 && sudo adduser yourusername audio
```
Then reboot.

---

### Post by nnjond on 2011-01-19
Thanks for your advice.

udo dpkg-reconfigure -p high jackd2

and
sudo adduser myusername audio


Returned:

14:54:43.409 Patchbay deactivated.
14:54:43.467 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
14:54:43.571 ALSA connection graph change.
14:54:43.908 ALSA connection change.

---

### Post by cchhrriiss121212 on 2011-01-19
Did you reboot? You also should be able to run jack with the realtime box checked now. And can you post what sound card you are using?

---

### Post by nnjond on 2011-01-19
Yes I rebooted.

nnjond@nnjond-GeForce6100PM-M2:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller                                                                         
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control                                                                   
nnjond@nnjond-GeForce6100PM-M2:~$

---

### Post by nnjond on 2011-01-19
Yes I rebooted.

nnjond@nnjond-GeForce6100PM-M2:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller                                                                         
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control                                                                   
nnjond@nnjond-GeForce6100PM-M2:~$

---

### Post by nnjond on 2011-01-19
Yes I rebooted.

nnjond@nnjond-GeForce6100PM-M2:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller                                                                         
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control                                                                   
nnjond@nnjond-GeForce6100PM-M2:~$

---

### Post by cchhrriiss121212 on 2011-01-19
Up there you had a USB card mentioned in the output. Is that the one you want to use? If not, which one is?
The trouble with USB devices is that they often get disconnected to different ports but jack will still look for them in the old port. Try posting aplay -l.

---

### Post by cchhrriiss121212 on 2011-01-19
Up there you had a USB card mentioned in the output. Is that the one you want to use? If not, which one is?
The trouble with USB devices is that they often get disconnected to different ports but jack will still look for them in the old port. Try posting aplay -l.

---

### Post by nnjond on 2011-01-19
Yes I rebooted.

nnjond@nnjond-GeForce6100PM-M2:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller                                                                         
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control                                                                   
nnjond@nnjond-GeForce6100PM-M2:~$

---

### Post by nnjond on 2011-01-19
I rebooted

nnjond@nnjond-GeForce6100PM-M2:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller                                                                         
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control                                                                   
nnjond@nnjond-GeForce6100PM-M2:~$

---

### Post by nnjond on 2011-01-19
Thanks again


njond@nnjond-GeForce6100PM-M2:~$ aplay -l                                      
**** List of PLAYBACK Hardware Devices ****                                     
card 2: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]  
  Subdevices: 1/1                                                               
  Subdevice #0: subdevice #0                                                    
card 2: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1                                                               
  Subdevice #0: subdevice #0
nnjond@nnjond-GeForce6100PM-M2:~$

---

### Post by nnjond on 2011-01-19
Thanks again

njond@nnjond-GeForce6100PM-M2:~$ aplay -l                                      
**** List of PLAYBACK Hardware Devices ****                                     
card 2: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]  
  Subdevices: 1/1                                                               
  Subdevice #0: subdevice #0                                                    
card 2: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1                                                               
  Subdevice #0: subdevice #0
nnjond@nnjond-GeForce6100PM-M2:~$

---

### Post by nnjond on 2011-01-19
Thanks again

njond@nnjond-GeForce6100PM-M2:~$ aplay -l                                      
**** List of PLAYBACK Hardware Devices ****                                     
card 2: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]  
  Subdevices: 1/1                                                               
  Subdevice #0: subdevice #0                                                    
card 2: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1                                                               
  Subdevice #0: subdevice #0
nnjond@nnjond-GeForce6100PM-M2:~$

---

### Post by nnjond on 2011-01-19
Thanks again.

I unpluged the irrelevant usb and followed your advice again.


nnjond@nnjond-GeForce6100PM-M2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nnjond@nnjond-GeForce6100PM-M2:~$ 


But no joy.

16:31:41.738 Patchbay deactivated.
16:31:41.811 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:31:41.874 ALSA connection graph change.
16:31:42.262 ALSA connection change.
16:31:42.320 ALSA connection graph change.
16:32:10.960 Startup script...
16:32:10.961 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:32:11.396 Startup script terminated with exit status=32512.
16:32:11.396 JACK is starting...
16:32:11.397 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
16:32:11.410 JACK was started with PID=1777.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 0 - Alesis Q25 at usb-0000:00:02.0-3, full speed
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
16:32:11.800 JACK was stopped with exit status=255.
16:32:11.801 Post-shutdown script...
16:32:11.801 killall jackd
jackd: no process found
16:32:12.225 Post-shutdown script terminated with exit status=256.
16:32:13.449 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:32:21.843 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

### Post by nnjond on 2011-01-19
Thanks again.

I unpluged the irrelevant usb and followed your advice again.


nnjond@nnjond-GeForce6100PM-M2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nnjond@nnjond-GeForce6100PM-M2:~$ 


But no joy.

16:31:41.738 Patchbay deactivated.
16:31:41.811 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:31:41.874 ALSA connection graph change.
16:31:42.262 ALSA connection change.
16:31:42.320 ALSA connection graph change.
16:32:10.960 Startup script...
16:32:10.961 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:32:11.396 Startup script terminated with exit status=32512.
16:32:11.396 JACK is starting...
16:32:11.397 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
16:32:11.410 JACK was started with PID=1777.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 0 - Alesis Q25 at usb-0000:00:02.0-3, full speed
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
16:32:11.800 JACK was stopped with exit status=255.
16:32:11.801 Post-shutdown script...
16:32:11.801 killall jackd
jackd: no process found
16:32:12.225 Post-shutdown script terminated with exit status=256.
16:32:13.449 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:32:21.843 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

### Post by nnjond on 2011-01-19
Thanks again.

I removed the irrelevant usb, and followed your advice again.

nnjond@nnjond-GeForce6100PM-M2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nnjond@nnjond-GeForce6100PM-M2:~$ 


But no joy.


16:31:41.738 Patchbay deactivated.
16:31:41.811 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:31:41.874 ALSA connection graph change.
16:31:42.262 ALSA connection change.
16:31:42.320 ALSA connection graph change.
16:32:10.960 Startup script...
16:32:10.961 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:32:11.396 Startup script terminated with exit status=32512.
16:32:11.396 JACK is starting...
16:32:11.397 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
16:32:11.410 JACK was started with PID=1777.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 0 - Alesis Q25 at usb-0000:00:02.0-3, full speed
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
16:32:11.800 JACK was stopped with exit status=255.
16:32:11.801 Post-shutdown script...
16:32:11.801 killall jackd
jackd: no process found
16:32:12.225 Post-shutdown script terminated with exit status=256.
16:32:13.449 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:32:21.843 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

### Post by nnjond on 2011-01-19
Thanks again.

I removed the irrelevant usb, and followed your advice again.

nnjond@nnjond-GeForce6100PM-M2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nnjond@nnjond-GeForce6100PM-M2:~$ 


But no joy.


16:31:41.738 Patchbay deactivated.
16:31:41.811 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:31:41.874 ALSA connection graph change.
16:31:42.262 ALSA connection change.
16:31:42.320 ALSA connection graph change.
16:32:10.960 Startup script...
16:32:10.961 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:32:11.396 Startup script terminated with exit status=32512.
16:32:11.396 JACK is starting...
16:32:11.397 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
16:32:11.410 JACK was started with PID=1777.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 0 - Alesis Q25 at usb-0000:00:02.0-3, full speed
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
16:32:11.800 JACK was stopped with exit status=255.
16:32:11.801 Post-shutdown script...
16:32:11.801 killall jackd
jackd: no process found
16:32:12.225 Post-shutdown script terminated with exit status=256.
16:32:13.449 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:32:21.843 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

### Post by nnjond on 2011-01-19
Thanks again.

I removed the irrelevant usb, and followed your advice again.

nnjond@nnjond-GeForce6100PM-M2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nnjond@nnjond-GeForce6100PM-M2:~$ 


But no joy.


16:31:41.738 Patchbay deactivated.
16:31:41.811 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:31:41.874 ALSA connection graph change.
16:31:42.262 ALSA connection change.
16:31:42.320 ALSA connection graph change.
16:32:10.960 Startup script...
16:32:10.961 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:32:11.396 Startup script terminated with exit status=32512.
16:32:11.396 JACK is starting...
16:32:11.397 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
16:32:11.410 JACK was started with PID=1777.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 0 - Alesis Q25 at usb-0000:00:02.0-3, full speed
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
16:32:11.800 JACK was stopped with exit status=255.
16:32:11.801 Post-shutdown script...
16:32:11.801 killall jackd
jackd: no process found
16:32:12.225 Post-shutdown script terminated with exit status=256.
16:32:13.449 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:32:21.843 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

### Post by nnjond on 2011-01-19
Thanks again.

I removed the irrelevant usb, and followed your advice again.

nnjond@nnjond-GeForce6100PM-M2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nnjond@nnjond-GeForce6100PM-M2:~$ 


But no joy.


16:31:41.738 Patchbay deactivated.
16:31:41.811 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:31:41.874 ALSA connection graph change.
16:31:42.262 ALSA connection change.
16:31:42.320 ALSA connection graph change.
16:32:10.960 Startup script...
16:32:10.961 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:32:11.396 Startup script terminated with exit status=32512.
16:32:11.396 JACK is starting...
16:32:11.397 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
16:32:11.410 JACK was started with PID=1777.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 0 - Alesis Q25 at usb-0000:00:02.0-3, full speed
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
16:32:11.800 JACK was stopped with exit status=255.
16:32:11.801 Post-shutdown script...
16:32:11.801 killall jackd
jackd: no process found
16:32:12.225 Post-shutdown script terminated with exit status=256.
16:32:13.449 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:32:21.843 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

### Post by nnjond on 2011-01-19
Thanks again.

I removed the irrelevant usb, and followed your advice again.

nnjond@nnjond-GeForce6100PM-M2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nnjond@nnjond-GeForce6100PM-M2:~$ 


But no joy.


16:31:41.738 Patchbay deactivated.
16:31:41.811 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:31:41.874 ALSA connection graph change.
16:31:42.262 ALSA connection change.
16:31:42.320 ALSA connection graph change.
16:32:10.960 Startup script...
16:32:10.961 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:32:11.396 Startup script terminated with exit status=32512.
16:32:11.396 JACK is starting...
16:32:11.397 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
16:32:11.410 JACK was started with PID=1777.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 0 - Alesis Q25 at usb-0000:00:02.0-3, full speed
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
16:32:11.800 JACK was stopped with exit status=255.
16:32:11.801 Post-shutdown script...
16:32:11.801 killall jackd
jackd: no process found
16:32:12.225 Post-shutdown script terminated with exit status=256.
16:32:13.449 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:32:21.843 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

### Post by nnjond on 2011-01-19
Thanks again.

I removed the irrelevant usb, and followed your advice again.

nnjond@nnjond-GeForce6100PM-M2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nnjond@nnjond-GeForce6100PM-M2:~$ 


But no joy.


16:31:41.738 Patchbay deactivated.
16:31:41.811 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:31:41.874 ALSA connection graph change.
16:31:42.262 ALSA connection change.
16:31:42.320 ALSA connection graph change.
16:32:10.960 Startup script...
16:32:10.961 artsshell -q terminate
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
16:32:11.396 Startup script terminated with exit status=32512.
16:32:11.396 JACK is starting...
16:32:11.397 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -Xseq
16:32:11.410 JACK was started with PID=1777.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 0 - Alesis Q25 at usb-0000:00:02.0-3, full speed
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
16:32:11.800 JACK was stopped with exit status=255.
16:32:11.801 Post-shutdown script...
16:32:11.801 killall jackd
jackd: no process found
16:32:12.225 Post-shutdown script terminated with exit status=256.
16:32:13.449 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
16:32:21.843 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

### Post by cchhrriiss121212 on 2011-01-19
The output shows jack is still trying to use the USB device, so go into setup and specify the onboard device under the interface option.

---

### Post by inobe on 2011-01-19
if you are using kubuntu with kde 4.5+ i think it may be a pulseAudio issue but i am just assuming and only wish to offer this information and hope it's helpful.

let me explain, several months back till recently i helped a few get their devices to work on kubunt and pulse was the culprit. 

the devices worked after removing pulseAudio ank kmix revealed configure channels, and various other controls that were missing when pulse was installed.


**""i am not saying to do that""**

i checked [http://www.google.com/search?client=ubuntu&channel=fs&q=kubuntu+pulseaudio+and+jack&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=kubuntu+pulseaudio+and+jack&ie=utf-8&oe=utf-8)

i would also search this forum with those key words.

---

### Post by inobe on 2011-01-19
if you are using kubuntu with kde 4.5+ i think it may be a pulseAudio issue but i am just assuming and only wish to offer this information and hope it's helpful.

let me explain, several months back till recently i helped a few get their devices to work on kubunt and pulse was the culprit. 

the devices worked after removing pulseAudio ank kmix revealed configure channels, and various other controls that were missing when pulse was installed.


**""i am not saying to do that""**

i checked [http://www.google.com/search?client=ubuntu&channel=fs&q=kubuntu+pulseaudio+and+jack&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=kubuntu+pulseaudio+and+jack&ie=utf-8&oe=utf-8)

i would also search this forum with those key words.

---

