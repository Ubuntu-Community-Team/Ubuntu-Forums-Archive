---
title: "No sound on Creative Labs SB Live! Value card"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by sirdeets on 2006-11-01
I did an upgrade from dapper to edgy but lost sound in the process. I scoured the forums and did the basics (made sure nothing was muted in alsamixer, etc.). I verified my card using lspci: 

```

$ lspci -v

02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs CT4780 SBLive! Value
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at d400 [size=32]
        Capabilities: [dc] Power Management version 1

```

I added the emu10k1 driver as a module as well. Still no luck. I'm really stumped. ](*,) 

I'd really appreciate any pointers or advice! Thanks a bunch!

---

### Post by ndowens on 2006-11-01
try actually building the module in kernel instead of using it as a module, and see if it will work. if u must have it as a module, then try making it autoload.

---

