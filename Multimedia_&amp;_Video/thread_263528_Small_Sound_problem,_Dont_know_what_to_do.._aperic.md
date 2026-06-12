---
title: "Small Sound problem, Dont know what to do.. apericate if you can help"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by atnishry on 2006-09-23
So to the problem, I have this old machine that as an on-bord sound card, after I have done a fresh install of Ubuntu I got this error msg
> Sep 23 09:18:47 localhost kernel: [17187199.648000] es18xx: [0x220] ESS chip not found
Sep 23 09:18:47 localhost kernel: [17187199.652000] ESS AudioDrive ES18xx soundcard not found or device busy
Sep 23 09:19:28 localhost kernel: [17187240.756000] snd_maestro3: Unknown parameter `isapnp'
Sep 23 09:20:09 localhost kernel: [17187281.624000] snd_maestro3: Unknown parameter `isapnp'
Sep 23 09:20:23 localhost kernel: [17187295.360000] snd_maestro3: Unknown parameter `mpu_port'
Sep 23 09:20:35 localhost kernel: [17187307.940000] snd_maestro3: Unknown parameter `dma1'
Sep 23 09:20:50 localhost kernel: [17187323.000000] snd_maestro3: Unknown parameter `port'
Sep 23 09:21:00 localhost kernel: [17187332.748000] snd_maestro3: Unknown parameter `port'
Sep 23 09:23:32 localhost kernel: [17187484.216000] snd_maestro3: Unknown parameter `irq'

and then it goes
> Sep 23 09:24:06 localhost kernel: [17187518.868000] ac97 serial bus busy

Ok and now there is the problem this is the on-bord sound card:
> 0000:01:05.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
        Subsystem: Compaq Computer Corporation: Unknown device b19d
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 1000 [size=256]
        Capabilities: <available only to root>


and this sound card need to load a driver that call "snd-maestro3" and from some reason it's load a diffrent model.
I dont know how to make it work.

---

### Post by ropers on 2006-09-23
Ok, so you've got no sound. THe ac97 stuff could be a red herring. Do you KNOW what king of hardware you've got in your box? can you upload your dmesg somewhere and post a link to it here? Does sound work in other operating systems and/or if you boot from a LiveCD, eg. Knoppix? I trust you've checked all the really obvious stuff like cables, batteries, etc.?

---

### Post by atnishry on 2006-09-24
I have just installed Windows to see if I get the same sound problem and yes it doesn't work, and yes I try to see if I get sound with Knoppix and no, I dont have sound with Knoppix and Windows, and the sound card is on-board, to me it's look like a hardware conflict cus in the bios the irq for the sound card is 5 and Windows detect it as 7 same for the netork card bios irq is 11 and Windows detect it as 7 like the sound card and I dont have un automatic option in the bios... so yhe Dont Know. I just need to find what is the bord.. and to try to fix the prob.
10x

---

