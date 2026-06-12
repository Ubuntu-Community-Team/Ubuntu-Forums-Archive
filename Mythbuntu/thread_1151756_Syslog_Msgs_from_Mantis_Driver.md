---
title: "Syslog Msgs from Mantis Driver"
date: 2009-05-07
forum: Mythbuntu
---

### Post by tobiz on 2009-05-07
I'm getting a lot of msgs in syslog such as:

May  7 12:06:12 hms kernel: [130516.601556] mantis stop feed and dma
May  7 12:07:20 hms kernel: [130584.084018] stb6100_set_bandwidth: Bandwidth=61262500
May  7 12:07:20 hms kernel: [130584.180020] stb6100_get_bandwidth: Bandwidth=62000000
May  7 12:07:20 hms kernel: [130584.700025] stb6100_get_bandwidth: Bandwidth=62000000
May  7 12:07:21 hms kernel: [130585.208586] stb6100_set_frequency: Frequency=1738460
May  7 12:07:21 hms kernel: [130585.308020] stb6100_get_frequency: Frequency=1738441
May  7 12:07:21 hms kernel: [130585.412018] stb6100_get_bandwidth: Bandwidth=62000000
May  7 12:07:24 hms kernel: [130588.109042] mantis start feed & dma

Is it possible to stop these? Do they mean anything significant? If they can be stopped, how?

---

### Post by ian dobson on 2009-05-07
Hi,

Maybe you could try adding the option verbose=0 to the mantis driver by editing /etc/modprobe.d/options and adding:-

options mantis verbose=0

And maybe try disabling the EPG scan for that card in myth-setup.

Regards
Ian Dobson

---

### Post by tobiz on 2009-05-07
> **ian dobson said:**
> Hi,

Maybe you could try adding the option verbose=0 to the mantis driver by editing /etc/modprobe.d/options and adding:-

options mantis verbose=0

And maybe try disabling the EPG scan for that card in myth-setup.

Regards
Ian Dobson
Ian, thanks, just what I wanted to know; I'll try them.

---

