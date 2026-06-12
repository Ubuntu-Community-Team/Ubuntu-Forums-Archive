---
title: "K3B not seeing a cdrom"
date: 2008-12-10
forum: Multimedia Software
---

### Post by mastermindg on 2008-12-10
But Brasero is :mad:

Running Ubuntu 8.04 (updated), haven't really noticed this problem before, but haven't burned many discs before either.

Here is the output from running k3b:

kbuildsycoca running...
kdecore (KAction): WARNING: KActionCollection::KActionCollection( QObject *parent, const char *name, KInstance *instance )
(K3bDevice::HalConnection) initializing HAL >= 0.5
Mapping udi /org/freedesktop/Hal/devices/storage_model_DVD__RW_DH_16W1S to device /dev/scd0
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
(K3bDevice::ScsiCommand) failed: 
                           command:    INQUIRY (12)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) Unable to do inquiry. /dev/scd0 is not a cdrom device
/dev/scd0 resolved to /dev/scd0
/dev/scd0 is block device (0)
(K3bDevice::ScsiCommand) failed: 
                           command:    INQUIRY (12)
                           errorcode:  0
                           sense key:  NO SENSE (2)
                           asc:        0
                           ascq:       0
(K3bDevice::Device) Unable to do inquiry. /dev/scd0 is not a cdrom device
Devices:
------------------------------
kdecore (KAction): WARNING: KActionCollection::operator+=(): function is severely deprecated.

[1]+  Done                    k3b

---

