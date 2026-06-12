---
title: "Issues..."
date: 2009-11-29
forum: Multimedia Software
---

### Post by /4:06-A on 2009-11-29
So my sound does not work in any case. It won't play through headsets or the laptop speakers.
I'm running 9.10, on a HP computer that has vista on a separate partition. 
Running the aplay -l command:
aplay: device_list:223: no soundcards found...

lspci -v:
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
    Subsystem: Hewlett-Packard Company Device 30d6
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
    Memory at fc480000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Was wondering if the <Access deneid> had anything to do with it, or if this is a deeper problem.



~~~


On an unrelated note:
When I boot my computer, through Grub, I can boot to vista, or to Linux. When I get a large update, both the original version of Ubuntu and the newer version show. But only the original version (9.10-11 is the first I got) boots. Subsequent updates (-14 , -15) boot, but get stuck at a terminal-esque screen where it flashes and prompts a login but does not accept characters... So in the long run, the computer still works and I can boot, but not to newer versions of Ubuntu. 
The above may be a little vague...

---

### Post by omnipotentperson on 2009-11-29
By 'where it flashes,' do you mean that the screen blinks on and off?

I have a problem like that, due to the fact that my NVidia drivers are deleted every time the kernel updates. You can only type letters when the screen is on, so I recommend that you change your password to a single character. However, I have only managed to get new kernels to work after lots of wasted time.

The best thing to do would be to stick with the kernel that works until a major upgrade, and clean up your grub boot menu.

I had the same problem as you with sound for a while, and I can't remember how I fixed it. I think that I had a corrupted file somewhere in my sound configuration, so you should check for that and delete it if you find it.

Hope it helps, and good luck if it doesn't.

---

