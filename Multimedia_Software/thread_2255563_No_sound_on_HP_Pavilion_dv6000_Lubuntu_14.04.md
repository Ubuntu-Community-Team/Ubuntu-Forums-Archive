---
title: "No sound on HP Pavilion dv6000 Lubuntu 14.04"
date: 2014-12-05
forum: Multimedia Software
---

### Post by jean10 on 2014-12-05
Hello to everyone.

I just installed Lubuntu 14.04 on an old HP Pavilion dv6000. I had some problems (weird display colors, and got stuck after the mouse cursor appeared) so I used the **acpi=off**, **noapic** and **nolapic** options when installing. After that everything worked fine, except for the sound. There was no speaker icon on the tray, and when i run **aplay -l** there are no soundcards listed. 

If this helps, when i run the system profiler I get these lines that I thought might be of interest:

On summary:
**Audio Adapter **     (null)

On pci devices:
**Audio device**        NVIDIA Corporation MCP51 High Definition Audio (rev a2)

I need help to get my soundcard to work, since I've been using this distro for three weeks on another pc and I'm loving it. This is my father's laptop, and I would like him to use Lubuntu too, but I won't be able to unless I manage to fix the sound problem.


Thanks in advance :p.


Jean.

---

### Post by jean10 on 2014-12-06
I finally solved it by editing** /etc/default/grub** line:

**GRUB_CMDLINE_LINUX="acpi=off noapic nolapic"**

leaving only

**GRUB_CMDLINE_LINUX="nolapic"**

then 

**update-grub**

and restarting. 


Hope it helps someone.


Jean.

---

