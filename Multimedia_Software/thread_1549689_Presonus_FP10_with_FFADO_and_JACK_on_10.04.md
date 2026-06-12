---
title: "Presonus FP10 with FFADO and JACK on 10.04"
date: 2010-08-10
forum: Multimedia Software
---

### Post by seanlano on 2010-08-10
I am having enormous trouble getting an FP10 to work with Lucid. 

I have been able to get exactly the same hardware to work together with previous versions of Ubuntu, it is only now that I am having problems. 

Firstly, I have installed Kernel 2.6.33-26-realtime from Abogani's PPA. I also have installed FFADO, JACK and libraw1394 from SVN source. This is on a 64-bit system (previously when I used the FP10 on Karmic and Jaunty I used 32-bit). 

When I plug in and turn on the FP10, I run ffado-test and get :
```
ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-1880
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x000a9200c8100982  0x00000A92  0x00010066   Presonus  - PreSonus FP10
   1       0x00016c00005d4833  0x0000016C  0x00000000   Linux - ohci1394  - 
no message buffer overruns

```

This leads me to believe that FFADO can "see" the FP10. At this stage the status light on the FP10 is red. I am pretty sure I am using the old firewire stack (I'm not really sure what that even means), but I tried to use the new one by changing the /etc/modprobe.d/blacklist-firewire.conf file and updating initramfs, but then ffado-test saw nothing, so I changed it back. 

Next, when I use qjackctl to attempt to start JACK, I get: ```
17:14:42.807 Startup script...
17:14:42.808 artsshell -q terminate
sh: artsshell: not found
17:14:43.211 Startup script terminated with exit status=32512.
17:14:43.211 JACK is starting...
17:14:43.212 /usr/bin/jackd -P80 -dfirewire -r44100 -p1024 -n3
jackd 0.119.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
17:14:43.224 JACK was started with PID=2475.
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1535469
no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
00144422674:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0-1880 built Aug  7 2010 15:36:03
firewire ERR: Error creating FFADO streaming device
cannot load driver module firewire
no message buffer overruns
17:14:43.621 JACK was stopped successfully.
17:14:43.622 Post-shutdown script...
17:14:43.623 killall jackd
jackd: no process found
17:14:44.037 Post-shutdown script terminated with exit status=256.
17:14:45.399 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

The server fails to start, the indicator light stays red. 
Sometimes the server actually starts and the FP10's light turns blue, but as soon as I try to actually do anything (i.e. open patchage) it freezes and then fails, and the light goes red again. The relevant part of the message log: ```
15:47:05.621 ALSA connection graph change.
firewire ERR: wait status < 0! (= -1)
DRIVER NT: could not run driver cycle
jackd watchdog: timeout - killing jackd
cannot read server event (Success)
cannot continue execution of the processing graph (Bad file descriptor)
zombified - calling shutdown handler
15:47:32.781 Shutdown notification.
15:47:32.781 JACK is stopping...
15:47:32.782 JACK is being forced...
15:47:32.785 JACK has crashed.
15:47:32.982 JACK was stopped successfully.
15:47:32.982 Post-shutdown script...
15:47:32.986 killall jackd
jackd: no process found
15:47:33.427 Post-shutdown script terminated with exit status=256.
15:47:40.228 ALSA connection graph change.
```

Immediately after running qjackctl and it failing, ffado-test gives: ```
ffado-test ListDevices
-----------------------------------------------
FFADO test and diagnostic utility
Part of the FFADO project -- www.ffado.org
Version: 2.999.0-1880
(C) 2008, Daniel Wagner, Pieter Palmers
This program comes with ABSOLUTELY NO WARRANTY.
-----------------------------------------------

=== 1394 PORT 0 ===
  Node id  GUID                  VendorId     ModelId   Vendor - Model
   0       0x00016c00005d4833  0x0000016C  0x00000000   Linux - ohci1394  - 
no message buffer overruns

```
The FP10 has disappeared. I need to turn off the FP10 and then turn it back on again for it to then show up again on the ffado-test list. Then I can repeat the above, and exactly the same happens. 

It either won't start at all, or it does briefly and then crashes. 


So, what on Earth is going on here? It's so annoying having it so close to working, but not quite. 
I would like to try the new firewire stack with FFADO, but it just plainly doesn't work. The FP10 doesn't register with JuJu. What do I need to do to use the new stack?
Why else would FFADO not work? As I said, I've used exactly the same computer and cable and FP10 and it worked before. 

Any help much appreciated!

---

### Post by seanlano on 2010-08-13
OK, I thought that it might be the actual device causing the problems, because the 1st firewire port on the FP10 is broken (forcing me to use the 2nd port). So just to be sure I booted up Windows (for the first time in a while) with the intention of testing it with the Presonus driver to see if it would work. It did. I also installed the latest Presonus driver for Windows, which supposedly also updates the firmware of the FP10. 
After this I rebooted into Ubuntu, and now it works perfectly! Better than ever before. 
So I guess the firmware update fixed whatever it was that was causing the problems - so technically it was a hardware problem, not a bug in FFADO or Ubuntu. Although it would be nice if FFADO could do firmware updates... but anyway it's all happy days now.

---

