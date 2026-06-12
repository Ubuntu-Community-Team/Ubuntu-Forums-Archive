---
title: "pulseaudio daemon won't start after upgrade to 18.04"
date: 2019-03-12
forum: Multimedia Software
---

### Post by tmichaelmcn on 2019-03-12
After upgrading to 18.04 from 16.04 I have no sound.  In Settings>Sound the window under the question "Choose a device for sound output:" is empty. When I run "pulseaudio --start" in a terminal, I get the following output:
E: [pulseaudio] ltdl-bind-now.c: Failed to open module mbeq_1197.so: mbeq_1197.so: cannot open shared object file: No such file or directory
E: [pulseaudio] module-ladspa-sink.c: Failed to load LADSPA plugin: file not found
E: [pulseaudio] module.c: Failed to load module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=-6.9,-7.3,-2.6,1.0,3.0,3.0,3.0,1.5,0.0,0.3,2.0,-0.3,1.0,-1.0,0.0"): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.

I'm running a Dell Inspiron 3847 with an Intel® Core™ i3-4130 CPU @ 3.40GHz × 4 processor and 8 gb of memory.

Sound worked just fine this morning with 16.04.

---

### Post by wildmanne39 on 2019-03-12
*Thread moved to **Multimedia Software a more appropriate sub-forum**.*

---

### Post by mtodorov69 on 2019-03-13
> **tmichaelmcn said:**
> After upgrading to 18.04 from 16.04 I have no sound. In Settings>Sound the window under the question "Choose a device for sound output:" is empty. When I run "pulseaudio --start" in a terminal, I get the following output:
E: [pulseaudio] ltdl-bind-now.c: Failed to open module mbeq_1197.so: mbeq_1197.so: cannot open shared object file: No such file or directory
E: [pulseaudio] module-ladspa-sink.c: Failed to load LADSPA plugin: file not found
E: [pulseaudio] module.c: Failed to load module "module-ladspa-sink" (argument: "sink_name=ladspa_output.mbeq_1197.mbeq master=alsa_output.pci-0000_00_1b.0.analog-stereo plugin=mbeq_1197 label=mbeq control=-6.9,-7.3,-2.6,1.0,3.0,3.0,3.0,1.5,0.0,0.3,2.0,-0.3,1.0,-1.0,0.0"): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialize daemon.

I'm running a Dell Inspiron 3847 with an Intel® Core&#8482; i3-4130 CPU @ 3.40GHz × 4 processor and 8 gb of memory.

Sound worked just fine this morning with 16.04.

What I think I would have done is to attempt to find the mbeq_1197.so shared object and add its directory to LD_LIBRARY_PATH .

Try this:

```
# find / -name mbeq_1197.so -ls
```

If your mbeq_1197.so isn't included in LD_LIBRARY_PATH , you can alternatively try the solution from this link: [B][https://bugs.archlinux.org/task/59108](https://bugs.archlinux.org/task/59108)

[/B]

---

### Post by tmichaelmcn on 2019-03-14
> **mtodorov69 said:**
> What I think I would have done is to attempt to find the mbeq_1197.so shared object and add its directory to LD_LIBRARY_PATH .

Try this:

```
# find / -name mbeq_1197.so -ls
```

If your mbeq_1197.so isn't included in LD_LIBRARY_PATH , you can alternatively try the solution from this link: [B][https://bugs.archlinux.org/task/59108](https://bugs.archlinux.org/task/59108)

[/B]

Thank you.  Your suggestion yielded the following output:
  2491528      0 lrwxrwxrwx   1 root     root           28 Mar 14 14:08 /usr/lib/mbeq_1197.so -> /usr/lib/ladspa/mbeq_1197.so

I'm not sure what this means.  There is no /usr/lib/ladspa/ folder.

---

### Post by tmichaelmcn on 2019-03-14
I found a solution at [https://askubuntu.com/questions/1029403/no-sound-in-ubuntu-18-04-lts-after-upgrade-from-16-04-lts](https://askubuntu.com/questions/1029403/no-sound-in-ubuntu-18-04-lts-after-upgrade-from-16-04-lts).  Norbert S posted the following:

[LIST=1]
[*]delete .config/pulse/ and .pulse (the latter might not exist)
[*]reboot
[*]pulseaudio --start
[*]pavucontrol, go to Configuration tab and choose profile analog stereo output
[*]gnome-alsamixer  click unmute
[/LIST]

---

