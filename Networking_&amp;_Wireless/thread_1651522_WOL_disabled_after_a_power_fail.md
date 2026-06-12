---
title: "WOL disabled after a power fail"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by Dsky on 2010-12-23
When there's a power fail I can't start my pc in WOL but i've to start it manually..

there's a soluction?

i dont think it's a OS problem..

---

### Post by grahammechanical on 2010-12-23
What is WOL? I always start my computer manually - I push a button. More seriously, I found this in my motherboard user guide regarding the BIOS settings options. It is under the Power tab and the ARM Configuration heading.

> **Restore On AC Power Loss [Power Off]** When set to Power Off, the system goes into off state after an AC power loss. When set to Power On, the system goes on after an AC power loss. When set to Last State, the system goes into either off or on state, whatever the system state was before the AC power loss.

I hope this helps.

regards

---

### Post by Dsky on 2010-12-23
I don't want the pc to restart after a power fail.. i just want the network card to be ready again to be WOL (wake(d) on lan)

---

### Post by tgalati4 on 2010-12-23
Ups?

---

### Post by psusi on 2010-12-23
Yea, I think you either need to get a UPS or set that bios option to automatically start up after a power fail.  Unless your bios has an option to enable WOL, it comes up disabled after a power fail and you have to boot the OS to turn it on.

---

### Post by Dsky on 2010-12-23
even if the pc is off if the power fails the network card get disabled and i've to go upstair starting manually the pc..

there's another way?  i dont want to take a ups just for keeping the network card enabled and ready to be "waked" 

but is it a network card problem or a mobo problem?

---

### Post by psusi on 2010-12-23
It is a "bios doesn't have an option to enable WOL" problem.

---

### Post by Dsky on 2010-12-23
:D so should i change mobo?

i've here another old mobo... a MSI (microstar) MS-6199VA... i should discover if this one has it

---

### Post by Dsky on 2010-12-23
wait maybe i understood...

there's a 3pin (WOL) in the mobo... i've to connect that to the network card...

it could be? the wol worked without that too... but maybe that connector restore the power even after a power fail... what do you think?

edit: i found this

> Some machines do not support Wake-on-LAN after they have been disconnected from power (e.g., when power is restored after a power failure). Use of an uninterruptible power supply (UPS) will give protection against a short period without power, although the battery will discharge during a prolonged power cut. If a machine that is not designed to support Wake-on-LAN is left powered down after power failure, it may be possible to set the BIOS to start it up automatically on restoration of power, so that it is never left in an unresponsive state. A typical BIOS setting is AC back function which may be on, off, or memory. On is the correct setting in this case; memory, which restores the machine to the state it was in when power was lost, may leave a machine which was hibernating in an unwakeable state.

uhm...

---

