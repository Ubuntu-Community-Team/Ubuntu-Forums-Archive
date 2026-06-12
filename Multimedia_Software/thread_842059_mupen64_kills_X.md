---
title: "mupen64 kills X"
date: 2008-06-27
forum: Multimedia Software
---

### Post by Johnny K on 2008-06-27
Has anyone else experienced the problem of mupen64 0.5 crashing and killing X?

When I try to load a ROM, a black window opens, but after only a few seconds X dies and I am back at the Ubuntu login screen.

I was able to get a runtime report of mupnen64 by redirecting terminal output to a file which I inspected after the crash. Everything seems normal, except for this line:

```
Allocating memory for audio buffer: 65536 bytes.
```

The number 65536 stands out as the largest possible unsigned 16-bit number, plus one. Could this have anything to do with the crash?

---

### Post by Johnny K on 2008-06-27
I installed mupen64plus v1.4, but I am still experiencing a similar problem.

The emulator starts up fine. But when I try to start a ROM, a black window opens and then the whole program immediately closes. X, thankfully, does not crash.

The terminal output gives me:
```
Signal number 4 caught:
	errno = 0 (Success)
```

Any ideas?

---

### Post by rubicon on 2008-06-28
Faulty/unemulated rom?

Have you tried official demo roms for Mupen64, and what happens?

---

### Post by Johnny K on 2008-06-28
> **rubicon said:**
> Faulty/unemulated rom?

Have you tried official demo roms for Mupen64, and what happens?

I tried a couple of different ROMs with the same results.

Where could I find the demo ROMs?

---

### Post by rubicon on 2008-06-29
> **Johnny K said:**
> I tried a couple of different ROMs with the same results.

Where could I find the demo ROMs?
On mupen64 website.

---

### Post by Johnny K on 2008-06-29
> **rubicon said:**
> On mupen64 website.
Ahh, thanks. I had been looking on the mupen64plus site.

I was able to get the following ROMs to load without crashing mupen64plus:
-XtraLife Dextrose Demo by RedboX (PD)
-Soncrap Golden Eye Intro (PD)
-Absolute Crap Intro 1 by Kid Stardust (PD)
-Pong by Oman (PD)
-Rotating Demo USA by Rene (PD)

Sometimes they display properly, other times they simply display a black screen that says only "Mupen64Plus Started..."

All other demo ROMs cause mupen64plus to crash completely.

---

### Post by argor on 2008-07-02
i think you need to report the isou here [http://code.google.com/p/mupen64plus/issues/list](http://code.google.com/p/mupen64plus/issues/list)

---

