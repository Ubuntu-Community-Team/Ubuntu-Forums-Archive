---
title: "Front headphone jacks not working in Ubuntu, but they do work in Windows."
date: 2012-12-24
forum: Multimedia Software
---

### Post by CrankyCurmudgeon on 2012-12-24
Ubuntu is copping an attitude with me.  I'm using the mainboard's native sound chips (I'll post all that good stuff at the end of the posting) and for some reason, Ubuntu's not too willing to enable the front microphone and headphone jacks.  The rear outputs work wonderfully, but the front jacks are a no go.

I use them in Windows, so I know the connections are sound.  Even though there's no sound.  Hm.  But you know what's really annoying?  *They used to work before on Ubuntu 11.xx*.  My hard drive died so I had to reinstall everything, but for some reason, this time I can't get the front jacks to work, even though I installed the same version of Ubuntu on which they worked before.  I just upgraded today to Ubuntu 12.04.1 and the problem persists.

The mainboard is an MSI 770-G45.  As promised, here's what I get from terminal prompts:[B]
sudo aplay -l:[/B]
card 0: SB [HDA ATI SB], device 0: VT1828S Analog [VT1828S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: VT1828S Digital [VT1828S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: VT1828S HP [VT1828S HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**lspci -v | grep -A7 -i "audio":**
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
    Subsystem: Micro-Star International Co., Ltd. Device 7599
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

Both front and rear work fine in Windows XP, but only the rear ones work in Ubuntu.  Where lies the confusion?  If anyone needs any more information, tell me what to type in and I'll send it along.

By the way, dumb down your answers a bit.  I don't compile (my last computing experiences were in the 80s using hex code...my geek cred has long since been expended and my nerd card revoked) so try not to use excessively big words, include lots of pictures, and type very, very slowly so I can keep up!  Grazie, gracias, and thankyouverymuch.

Edit:  Wow.  Who knew the Ubuntu community could be so helpful?  Looks like it's back to Windows to get some real computing done.  Maybe in Ubuntu 257.354.0 there will be an OS worthy of replacing Windows or Mac.

---

