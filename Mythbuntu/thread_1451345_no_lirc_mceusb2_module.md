---
title: "no lirc_mceusb2 module"
date: 2010-04-10
forum: Mythbuntu
---

### Post by sbradley07 on 2010-04-10
I continue to have problems with my IR blaster and noticed something that I think is wrong...but don't know how to fix.

My /etc/lirc/hardware.conf file specifies the following for the remote and the transmitter:
REMOTE_MODULES="lirc_dev lirc_mceusb" and
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"

But when I do lsmod, I only see the lirc_dev and lirc_mceusb modules. _There is no lirc_mceusb2_.

Shouldn't this module being loading?  I don't see any errors that indicate it's failing to load, so I assume I am missing something that tells it to load.  Any ideas?

---

### Post by tgm4883 on 2010-04-10
> **sbradley07 said:**
> I continue to have problems with my IR blaster and noticed something that I think is wrong...but don't know how to fix.

My /etc/lirc/hardware.conf file specifies the following for the remote and the transmitter:
REMOTE_MODULES="lirc_dev lirc_mceusb" and
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"

But when I do lsmod, I only see the lirc_dev and lirc_mceusb modules. _There is no lirc_mceusb2_.

Shouldn't this module being loading?  I don't see any errors that indicate it's failing to load, so I assume I am missing something that tells it to load.  Any ideas?

What version of Mythbuntu are you on? There is now a single module for MCEUSB remotes, no need for MCEUSB2

---

### Post by sbradley07 on 2010-04-10
I am on 0.22.  

If there is only one module, do I need to change my hardware.conf to have:

TRANSMITTER_MODULES="lirc_dev lirc_mceusb"

---

### Post by tgm4883 on 2010-04-10
> **sbradley07 said:**
> I am on 0.22.  

If there is only one module, do I need to change my hardware.conf to have:

TRANSMITTER_MODULES="lirc_dev lirc_mceusb"

That i'm not sure on since I don't use the transmitter. I just know that there isn't a lirc_mceusb2 anymore

---

### Post by nickrout on 2010-04-10
> **sbradley07 said:**
> I am on 0.22.  

If there is only one module, do I need to change my hardware.conf to have:

TRANSMITTER_MODULES="lirc_dev lirc_mceusb"

you still have not said what version of mythbuntu you are on - 0.22 is a version of mythtv, not of mythbuntu.

---

### Post by sbradley07 on 2010-04-10
I am on Mythbuntu 9.10.  

I made the change mentioned above, with no noticeable difference, so I guess it doesn't matter either way.

---

### Post by nickrout on 2010-04-11
and did you reboot?

also try manually removing the module and reloading it with debug enabled, than see what dmesg tells you.

```
sudo modprobe -r lirc_mceusb
sudo modprobe lirc_mceusb debug=1
dmesg

```

---

