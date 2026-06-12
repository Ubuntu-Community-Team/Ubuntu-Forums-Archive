---
title: "RF multipoint modem: can i make it an ethernet adapter?"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by erupter on 2010-11-05
I have some Digi X24-019PKC modems.
They are RF multipoint modems effectively realizing a shared wireless bus.
Everything one modem sends, is received by all other modems in range.
Interference allowing.
I/O stream is RS232.
Now is there a way i can have one such modem be used by the OS as an ethernet port?
I'd really need to run IP over this ensemble.
This way i could use my laptop with a dedicated DHCP and have multiple entities connect to the network without resorting to developing my own network stack.
Any advice as to how use these in an interoperable way is welcome.
Keep in mind that my main needs are two:
1st have multiple entities communicate in a simple and possibly transparent way
2nd have different operating systems sharing information on this network (linux and windows).

I hope you can come up with something!

edit:
i figured...what about tunnelling? tunnelling IP over RS232 would work... Fantasy? Crazyness? Feasibility?

---

