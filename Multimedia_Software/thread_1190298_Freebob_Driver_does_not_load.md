---
title: "Freebob Driver does not load"
date: 2009-06-17
forum: Multimedia Software
---

### Post by Valenz on 2009-06-17
Hello,
I have just bought a Presonus Firebox. I am trying to get it to work for 2 days now. 

I followed Instructions I found in this forum. Added §User to group disk, loaded the modules ieee1394 and raw1394 and configured JACK as it was recommended. 

But everytime I try to start JACK with the freebob driver, JACK tells me that: 


23:15:36.277 JACK is starting...
23:15:36.277 /usr/bin/jackd -R -P75 -dfreebob -dhw:0 -r96000 -p128 -n3 -D
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
23:15:36.303 JACK was started with PID=6963.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: Invalid argument
Is ieee1394 and raw1394 driver loaded?
[31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
[0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
cannot load driver module freebob
[0m
23:15:36.371 JACK was stopped successfully.


It seems so me, that freebob is the problem. My pci card is detected:


marcel@marcel-desktop:~$ lspci | grep 1394
01:07.0 Multimedia video controller: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)


the modules are also loaded 


marcel@marcel-desktop:~$ lsmod | grep 1394
raw1394                35592  0 
ieee1394              108288  1 raw1394


I have done a lot of research the past two days but haven't found something that could have helped me with this.

Maybe i am wrong and the pci firewire card does not work properly and that causes freebob to crash? 

If anyone has any idea or is facing similar problems - let me hear! ;)



All the best

Marcel

---

