---
title: "CT2504S VIBRA16S fixed modprobe sb, next?"
date: 2006-02-08
forum: Multimedia &amp; Video
---

### Post by Paul Dufresne on 2006-02-08
I have a IBM PC 300 GL, PII 300MHz, with a creative lab sound card on which
the chip reads "CT2504S Vibra 16S". Well, I did not opened it recently, but I wrote
that on the case.

I have added a one line /etc/modprobe.d/sb file:
options sb io=0x220 irq=5 dma=1 dma16=5

because sudo modprobe sb was not working.

I had read dma16=3 on a web page, but I think only 5 works for me.

Now I have after sudo modprobe sb at the end of dmesg:
[4296959.214000] sb: Init: Starting Probe...
[4296959.214000] sb: Probing legacy card with io=220, irq=5, dma=1, dma16=5
[4296959.214000] SB 4.13 detected OK (220)
[4296959.238000] sb: Init: Done
and I now get the /dev/dsp file fine, and can now do:
ls /dev > /dev/dsp and hear a nice clear and load noise.

Ok, but I was expecting that now I would be able to reboot, and that the
sound would magically work. But after rebooting, the /dev/dsp file is absent,
and I need to redo sudo modprobe sb to make it back.

Was adding this sb file in /etc/modprobe.d directory suppose to fix booting with
my sound card? What should I do now, first to make the /dev/dsp automatically
load, next, to run the sound server for GNOME?

Also, I believe this is mainly because the kernel does not detect this sound card.
Right? Then would it not make sense to fill a bug on the kernel? 

cat /proc/version:
paul@Arcturus:~$ cat /proc/version
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005

Ask the result of other commands if you think it would be usefull.

---

### Post by FarEast on 2006-02-08
> Was adding this sb file in /etc/modprobe.d directory suppose to
> fix booting with my sound card?
> What should I do now, first to make the /dev/dsp automatically
> load, next, to run the sound server for GNOME?

Add an item 'sb' to /etc/modules .
Then the module will be loaded on boot and /dev/dsp will be available.

---

### Post by Paul Dufresne on 2006-02-09
[QUOTE=FarEast]> 
Add an item 'sb' to /etc/modules .
Then the module will be loaded on boot and /dev/dsp will be available.[/QUOTE]

Thanks, this help a bit. Indeed I do have /dev/dsp there and working after
rebooting. Still unable to have ALSA see my card, and esd to work.

I'll post more on this on an other reply.

---

### Post by Paul Dufresne on 2006-02-09
Now if I do:

paul@Arcturus:~$ sudo esd -d /dev/dsp
- using device /dev/dsp
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM /dev/dsp
paul@Arcturus:~$

I may looks like someone that knows what he does, but fifteen minutes ago, I
was not even knowing (remembering) esd was the sound server. It's more that
I am reading some stuff on the net on before posting here.

CT2504S Vibra 16S is a NON PNP (ISA?) card.

But it had always been a bit harder to configure, because sb module was never
able to see it without giving is some clues. On 2.4 kernel, it was mostly done by
giving an isapnp file found on the net giving pnp hints, and then this card was
working. And then came 2.6 with udev, and I was never able back to make it
work.

Enough historic, now if I explore /proc/asound:

pcm is empty

cards:
--- no soundcards ---

devices:
 33:       : timer

modules is empty

version:
Advanced Linux Sound Architecture Driver Version 1.0.9 (Sun May 29 07:31:02 2005 UTC).

oss/devides is empty

oss/sndstat:
===
Sound Driver:3.8.1a-980706 (ALSA v1.0.9 emulation code)
Kernel: Linux Arcturus 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers: NOT ENABLED IN CONFIG
===
paul@Arcturus:~$ lsmod
Module                  Size  Used by
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  1 snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  4 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10120  1 snd_pcm
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
lp                     11460  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipt_TCPMSS              4096  1
ipt_tcpmss              2304  1
iptable_filter          2944  1
ip_tables              18176  3 ipt_TCPMSS,ipt_tcpmss,iptable_filter
pppoe                  13120  2
pppox                   3464  1 pppoe
ipv6                  217408  8
af_packet              20232  2
ppp_generic            25748  6 pppoe,pppox
slhc                    6656  1 ppp_generic
pcspkr                  3652  0
rtc                    11832  0
parport_pc             31812  1
parport                32072  2 lp,parport_pc
floppy                 52692  0
i2c_piix4               8336  0
i2c_core               19728  2 i2c_acpi_ec,i2c_piix4
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
sb                     12932  1
sb_lib                 42288  1 sb
uart401                11204  1 sb_lib
sound                  70444  3 sb_lib,uart401
soundcore               9184  4 snd,sb_lib,sound
psmouse                26116  0
...

I am reading now on [http://alsa.opensrc.org/faq/:](http://alsa.opensrc.org/faq/:)
===
If you need to change the default soundcard you need to edit one of the ALSA configuration files:

*/etc/asound.conf for system-wide options that affect all users *~/.asoundrc for options that affect only your own user account
===

So I'll try to find more infos on this asound.conf file, even if I find no man page
for it.

Any clue?

---

### Post by Paul Dufresne on 2006-02-09
Just after posting last message, I then realized that the sound do work
with totem player. And I can adjust volume. :D 

I suppose Totem and other directly open and use /dev/dsp?
And how esd try to do things? Using Alsa library calls?

Anyway, I still would like to find out how to have esd working.

---

### Post by FarEast on 2006-02-09
You are now driving the sound card(VIBRA16S) with the OSS module 'sb.ko'.
I suggest you to do it with the ALSA module 'snd-sb16.ko'.

[http://www.alsa-project.org/alsa-doc/index.php?vendor=.%23vendor-Creative_Labs.1.1.1.1](http://www.alsa-project.org/alsa-doc/index.php?vendor=.%23vendor-Creative_Labs.1.1.1.1)

First, remove 'sb' from /etc/modules and add 'snd-sb16'.
Then describe the options in /etc/modrobe.d/sound .
```
options snd-sb16 isapnp=0 port=0x220 irq=5 dma8=1 dma16=5
```

Execute 'sudo update-modules' and restart the system.
You may need to do 'sudo modprobe snd-pcm-oss' to make /dev/dsp available.

---

### Post by Paul Dufresne on 2006-02-11
I appled your suggestion.
Everything seems to work fine now! :D 
Thanks!

Is it considered normal configuration for pre-PNP sound card, or should I report
something to help autodetect this hardware?

---

### Post by FarEast on 2006-02-12
Congratulations!
> Is it considered normal configuration for pre-PNP sound card...
I think so.  What you call 'pre-PNP sound cards' cannot be detected
automatically.  Earlier package of 'alsa-utils' had a nice script 'alsaconf'.
It had helped many people configure the sort of sound cards.
I hope you will help your fellows!

---

