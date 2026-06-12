---
title: "Yet another MCE Remote Problem"
date: 2010-02-16
forum: Mythbuntu
---

### Post by psybernoid on 2010-02-16
I'm running Mythbuntu 9.10 - clean install, with a full apt-get update.
As per title, MCE remote isn't working correctly. It does work occasionally, but not with any reliability, and certainly not with any method I can replicate to get it working.
Seems it works just when it feels like :-\

Here's the output of lsusb```

tv@PsyTV:~$ lsusb
Bus 001 Device 004: ID 0bda:0151 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 046d:c714 Logitech, Inc. 
Bus 003 Device 004: ID 046d:c713 Logitech, Inc. 
Bus 003 Device 003: ID 046d:0b04 Logitech, Inc. 
Bus 003 Device 002: ID 046d:c51a Logitech, Inc. MX Revolution/G7 Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0471:0815 Philips eHome Infrared Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

irw responds
```
tv@PsyTV:~$ irw
000000037ff07be0 00 Down mceusb
000000037ff07be0 01 Down mceusb
000000037ff07be1 00 Up mceusb
000000037ff07be1 01 Up mceusb
000000037ff07bdf 00 Left mceusb
000000037ff07bdf 01 Left mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bde 01 Right mceusb
000000037ff07bdd 00 OK mceusb
000000037ff07bdd 01 OK mceusb
```

And I only have one lirc device listed in /dev
```
tv@PsyTV:~$ ls /dev/lirc*
/dev/lirc0  /dev/lircd
```

I have the required files in ~/.lirc, ~/.mythtv & /etc/lirc

Anyone have any ideas?

Like I mentioned, somestimes it does work, but not with any regularity.

Interestingly, I just installed Boxee, and that worked as soon as I fired it up, without any configuration whatsoever.

---

### Post by nickrout on 2010-02-17
are you using mythbuntu control centre to set up your remote? If not, try that.

---

### Post by psybernoid on 2010-02-17
Yes, the remote was set up with the Mythbuntu Control center.

One though has occured (whilst I'm sat here at work) I have an Hauppage winTV Nova-DVB-S2 card, which of course has it's own remote control.

Now, the remote control for this is not used in any way (I've never even put batteries in it) and the infra red 'eye' is not connected to the card itself.

Is it at all possible that this is interfering with the MCE reciever?

---

