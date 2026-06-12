---
title: "Wake on lan, dell, phoenix award 6.00pg bios"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by Qifor on 2011-01-30
I'm trying to get WoL working on a new home server ive setup, however the bios doesnt include an option to do so. Ive searched around and found that this is by design but Dell offers a free tool that lets you change the settings, however its windows only. [http://www.delltechcenter.com/page/Dell+Client+Configuration+Utility+3.0](http://www.delltechcenter.com/page/Dell+Client+Configuration+Utility+3.0)

Does anyone know if there is a tool or a way to get this working in Ubuntu?

---

### Post by grahammechanical on 2011-01-30
There is something I do not understand. If the BIOS of a machine does not have an option to either enable or disable Wake up on Lan, then why do you think that it is possible to do that using a web browser that is running on another machine?

The program that you are looking at seems to me (in my ignorance) to be designed for system administrators to allow them to change BIOS settings in machines on a network over the network. Even this clever program will not be able to change settings in a machine's BIOS that do not exist in that BIOS program.

Furthermore I think that the main purpose of this program is to simplify the updating of the BIOS of machines on the network. It may do its job by making adjustments to the new BIOS before it is flashed onto the machine.

If the BIOS of the machine does not support Wake up on Lan then you will not be able to adjust it to allow Wake up on Lan. But a BIOS update may add this feature. Try researching BIOS updates for your motherboard. There might be a newer version of the BIOS that allows Wake up on Lan.

Regards.

---

### Post by Qifor on 2011-01-30
I know it comes across as weird but from what others have said the option isn't there in the BIOS screen but the BIOS does support it and it works perfectly fine once enabled by the DCCU.

The manual actually lists the wol options as being in the BIOS but they aren't.

---

