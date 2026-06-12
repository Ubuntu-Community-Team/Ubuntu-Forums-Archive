---
title: "PS3 Eye is no longer working"
date: 2013-11-08
forum: Multimedia Software
---

### Post by Midnight Star on 2013-11-08
The PS3 Eye worked flawlessly until a few days ago, which now doesn't seem to mount or be available as a video/audio device.

lsusb shows the following:

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1415:4000 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Which shows "Nam Tai" in the list (which should be the PS3 Eye cam). If I unplug the PS3 Eye and run an lsusb again this is what I get: 

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The Nam Tai entry clearly disappears. When the camera works, there appears to be 2 "Nam Tai" entries, one like you see above, and another one just below it that says the same thing but has "Sony Playstation" at the text line.

Does this imply that the device is there, but not being properly mounted? Cound I attempt to mount the camera manually from the information above? Should there be duplicate entries for it to work properly or is the Nam Tai entry above simply not complete or the model-id isn't being recognized by the os? 

Another symptom i've noticed, is when booting into Linux, the red (cam in use) light would come on just before booting into the gui. Now Linux completely boots up without activating the camera (in use light doesn't flash on then go off).

---

