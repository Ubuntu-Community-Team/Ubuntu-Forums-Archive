---
title: "sound card not detected"
date: 2006-05-29
forum: Multimedia &amp; Video
---

### Post by u04f061 on 2006-05-29
ubuntu some times fail to detect my sound card.this happens almost 40%of time.
60% of time it detects.
  my sound card is ess maestro.how to fix it i don't know,but the error it gives is that
  

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

---

### Post by Matten on 2006-05-30
I have also the same problem! But here the sound never works! I'm using Dapper and under Breezy I had the same problem, even on the site of alsa they say my soundcard is supported.

I'm using a C-media CM8738 soundcard.....

Anyone knows how we can fix this?

---

### Post by az on 2006-05-30
[QUOTE=Matten]I have also the same problem! But here the sound never works! I'm using Dapper and under Breezy I had the same problem, even on the site of alsa they say my soundcard is supported.

I'm using a C-media CM8738 soundcard.....

Anyone knows how we can fix this?[/QUOTE]

It is an older machine and do you have pnp-os dissabled in your BIOS.  Linux is not pnp compatible, so your bios may make assumptions about how to assicgn pci IRQs which can result in a conflict.

Is the snd-cmipci module loaded?

lsmod |grep snd-cmipci


u04f061:  Run 
dmesg
when your card works, and the keep rebooting until it doesn't and then run another dmesg and look for differences.

You can post both as attachments if you cannot find anything.

---

### Post by Matten on 2006-05-30
lsmod |grep snd-cmipci returns me nothing I put in attachment lsmod and dmesg.

I also looked in my BIOS and pnp-os stands on "no"

---

### Post by u04f061 on 2006-05-30
this is the result when sound card was working.still it is working.when it will lose i'll post that also

ejaz@msiddique:~$ dmesg
ey pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297180.224000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297180.306000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297180.306000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297181.292000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297181.292000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297181.395000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297181.395000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297250.715000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297250.715000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297250.794000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297250.794000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297251.157000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297251.157000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297251.234000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297251.234000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297251.507000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297251.507000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297251.579000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297251.579000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297739.072000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297739.072000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297739.463000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297739.463000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297739.637000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297739.637000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297739.738000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297739.738000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297739.851000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297739.851000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297739.944000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297739.944000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297740.070000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297740.070000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297740.147000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297740.147000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297756.161000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297756.161000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297756.265000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297756.265000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297756.691000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297756.691000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297757.250000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297757.250000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297757.454000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297757.454000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297757.531000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297757.531000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297759.657000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297759.657000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297759.726000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297759.726000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297760.008000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297760.008000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297760.069000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297760.069000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297760.276000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297760.276000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297760.347000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297760.347000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297760.508000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297760.508000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297760.540000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297760.540000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297762.358000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297762.358000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297762.429000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297762.429000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297763.717000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297763.717000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297763.783000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297763.783000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297764.979000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297764.979000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297765.039000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297765.039000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297765.276000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297765.276000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297765.332000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297765.332000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297765.541000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297765.541000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297765.610000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297765.610000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297765.811000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297765.811000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297765.899000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297765.899000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297766.063000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297766.063000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297766.150000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297766.150000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297766.314000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297766.314000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297766.385000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297766.385000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297766.517000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297766.517000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297766.586000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297766.586000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297766.720000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297766.720000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297766.791000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297766.791000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297766.958000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297766.958000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297767.029000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297767.029000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297767.341000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297767.341000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297767.407000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297767.407000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297767.697000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297767.697000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297767.768000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297767.768000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297871.024000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297871.024000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297871.128000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297871.128000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297872.198000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297872.198000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297872.315000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297872.315000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297872.449000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297872.449000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297872.534000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297872.534000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297872.671000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297872.671000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297872.788000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297872.788000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297872.882000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297872.882000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297872.978000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297872.978000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297873.075000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297873.075000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297873.159000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297873.159000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297894.379000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297894.379000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297894.533000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297894.533000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297895.280000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297895.280000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297895.395000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297895.395000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297899.761000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297899.761000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297899.919000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297899.919000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297901.072000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297901.072000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297901.213000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297901.213000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297901.697000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297901.697000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297901.835000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297901.835000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297902.522000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297902.522000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297902.725000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297902.725000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297904.155000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297904.155000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297904.258000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297904.258000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297904.690000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297904.690000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297904.813000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297904.813000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297905.920000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297905.920000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297906.078000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297906.078000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297906.954000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297906.954000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297907.111000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297907.111000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297908.305000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4297908.305000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4297908.462000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4297908.462000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
e

---

### Post by az on 2006-05-30
[QUOTE=Matten]lsmod |grep snd-cmipci returns me nothing I put in attachment lsmod and dmesg.

I also looked in my BIOS and pnp-os stands on "no"[/QUOTE]
snd_cmipci             34336  0

It is loaded.  Is it muted?

---

### Post by Matten on 2006-05-31
I can't even select any soundcard or system. So when I clik on the soundcontrol I get something about "No soundcard configurated" or "Gstreamer". 

lspci gives me:

0000:00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

So Ubuntu detects my soundcard.

matthias@Ubuntu-desktop:~$ lsmod | grep snd
snd_cmipci             34336  0
gameport               15496  1 snd_cmipci
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         10632  1 snd_pcm
snd_opl3_lib           10624  1 snd_cmipci
snd_timer              25220  2 snd_pcm,snd_opl3_lib
snd_hwdep               9376  1 snd_opl3_lib
snd_mpu401_uart         7808  1 snd_cmipci
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
snd                    55268  10 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd

matthias@Ubuntu-desktop:~$ amixer
amixer: Mixer attach default error: No such device

matthias@Ubuntu-desktop:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by u04f061 on 2006-06-05
this is the output when my sound card is not working

ejaz@msiddique:~$ dmesg
[4294667.296000] Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000feac000 (usable)
[4294667.296000]  BIOS-e820: 000000000feac000 - 0000000010000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 254MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 65196
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 61100 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fd790
[4294667.296000] ACPI: RSDT (v001 DELL    GX110   0x00000007 ASL  0x00000061) @ 0x000fd7a4
[4294667.296000] ACPI: FADT (v001 DELL    GX110   0x00000007 ASL  0x00000061) @ 0x000fd7cc
[4294667.296000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000b) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 10000000:efb00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda3 ro single
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (011ff000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 930.362 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294670.216000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)[4294670.216000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.244000] Memory: 250500k/260784k available (1415k kernel code, 9748k reserved, 763k data, 224k init, 0k highmem)
[4294670.244000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294670.245000] Calibrating delay loop... 1843.20 BogoMIPS (lpj=921600)
[4294670.267000] Security Framework v1.0.0 initialized
[4294670.267000] SELinux:  Disabled at boot.
[4294670.267000] Mount-cache hash table entries: 512
[4294670.267000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.267000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294670.267000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294670.267000] CPU: L2 cache: 256K
[4294670.267000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294670.267000] CPU: Intel Pentium III (Coppermine) stepping 06
[4294670.267000] Enabling fast FPU save and restore... done.
[4294670.267000] Enabling unmasked SIMD FPU exception support... done.
[4294670.267000] Checking 'hlt' instruction... OK.
[4294670.271000] Checking for popad bug... OK.
[4294670.271000] checking if image is initramfs... it is
[4294671.113000] Freeing initrd memory: 4821k freed
[4294671.120000] ACPI: Looking for DSDT in initrd... not found!
[4294671.257000]  not found!
[4294671.280000] ACPI: setting ELCR to 0200 (from 0e20)
[4294671.281000] NET: Registered protocol family 16
[4294671.281000] EISA bus registered
[4294671.281000] ACPI: bus type pci registered
[4294671.294000] PCI: PCI BIOS revision 2.10 entry at 0xfc0ce, last bus=1
[4294671.294000] PCI: Using configuration type 1
[4294671.294000] mtrr: v2.0 (20020519)
[4294671.295000] ACPI: Subsystem revision 20050729
[4294671.308000] ACPI: Interpreter enabled
[4294671.308000] ACPI: Using PIC for interrupt routing
[4294671.309000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294671.309000] PCI: Probing PCI hardware (bus 00)
[4294671.309000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294671.309000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294671.312000] Boot video device is 0000:00:01.0
[4294671.313000] PCI: Transparent bridge - 0000:00:1e.0
[4294671.315000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294671.315000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294671.323000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)[4294671.324000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)[4294671.325000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)[4294671.326000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 15)[4294671.326000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294671.326000] pnp: PnP ACPI init
[4294671.344000] pnp: PnP ACPI: found 13 devices
[4294671.344000] PnPBIOS: Disabled by ACPI PNP
[4294671.345000] PCI: Using ACPI for IRQ routing
[4294671.345000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294671.352000] pnp: 00:0c: ioport range 0x800-0x85f could not be reserved
[4294671.352000] pnp: 00:0c: ioport range 0xc00-0xc7f has been reserved
[4294671.352000] pnp: 00:0c: ioport range 0x860-0x8ff could not be reserved
[4294671.353000] audit: initializing netlink socket (disabled)
[4294671.353000] audit: initialized
[4294671.354000] VFS: Disk quotas dquot_6.5.1
[4294671.354000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294671.354000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294671.354000] devfs: boot_options: 0x0
[4294671.354000] Initializing Cryptographic API
[4294671.354000] isapnp: Scanning for PnP cards...
[4294671.708000] isapnp: No Plug & Play device found
[4294671.741000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[4294671.745000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294671.745000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294671.745000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294671.745000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.746000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.750000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294671.750000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294671.750000] io scheduler noop registered
[4294671.750000] io scheduler anticipatory registered
[4294671.750000] io scheduler deadline registered
[4294671.750000] io scheduler cfq registered
[4294671.751000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294671.752000] EISA: Probing bus 0 at eisa.0
[4294671.752000] EISA: Detected 0 cards.
[4294671.752000] NET: Registered protocol family 2
[4294671.761000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294671.761000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[4294671.761000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[4294671.761000] TCP: Hash tables configured (established 8192 bind 8192)
[4294671.762000] NET: Registered protocol family 8
[4294671.762000] NET: Registered protocol family 20
[4294671.762000] ACPI wakeup devices:
[4294671.762000] PCI0 USB0 PCI1  KBD
[4294671.762000] ACPI: (supports S0 S1 S4 S5)
[4294671.763000] Freeing unused kernel memory: 224k freed
[4294671.789000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.857000] Capability LSM initialized
[4294671.889000] NET: Registered protocol family 1
[4294671.918000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.918000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.919000] ACPI: bus type ide registered
[4294671.929000] ICH: IDE controller at PCI slot 0000:00:1f.1
[4294671.929000] ICH: chipset revision 2
[4294671.929000] ICH: not 100% native mode: will probe irqs later
[4294671.929000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294671.929000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[4294671.930000] Probing IDE interface ide0...
[4294672.194000] hda: WDC WD200BB-75CAA0, ATA DISK drive
[4294672.806000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.807000] Probing IDE interface ide1...
[4294673.479000] hdc: SAMSUNG CDRW/DVD SM-308B, ATAPI CD/DVD-ROM drive
[4294674.091000] ide1 at 0x170-0x177,0x376 on irq 15
[4294674.091000] Probing IDE interface ide2...
[4294674.604000] Probing IDE interface ide3...
[4294675.116000] Probing IDE interface ide4...
[4294675.628000] Probing IDE interface ide5...
[4294676.149000] hda: max request size: 128KiB
[4294676.156000] hda: Host Protected Area detected.
[4294676.156000]        current capacity is 39062500 sectors (20000 MB)
[4294676.156000]        native  capacity is 39063024 sectors (20000 MB)
[4294676.158000] hda: Host Protected Area disabled.
[4294676.158000] hda: 39063024 sectors (20000 MB) w/2048KiB Cache, CHS=38753/16/63, UDMA(66)
[4294676.159000] hda: cache flushes not supported
[4294676.159000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 > p3
[4294676.198000] hdc: ATAPI 32X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294676.198000] Uniform CD-ROM driver Revision: 3.20
[4294676.837000] Attempting manual resume
[4294676.838000] swsusp: Suspend partition has wrong signature?
[4294676.940000] usbcore: registered new driver usbfs
[4294676.940000] usbcore: registered new driver hub
[4294676.943000] USB Universal Host Controller Interface driver v2.2
[4294676.944000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294676.944000] PCI: setting IRQ 11 as level-triggered
[4294676.945000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294676.945000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294676.945000] uhci_hcd 0000:00:1f.2: Intel Corporation 82801AA USB
[4294677.007000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294677.007000] uhci_hcd 0000:00:1f.2: irq 11, io base 0x0000ff80
[4294677.007000] hub 1-0:1.0: USB hub found
[4294677.007000] hub 1-0:1.0: 2 ports detected
[4294677.047000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[4294677.048000] PCI: setting IRQ 5 as level-triggered
[4294677.048000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294677.048000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[4294677.048000] 0000:01:0c.0: 3Com PCI 3c905C Tornado at 0xec80. Vers LK1.1.19
[4294679.758000] ACPI: CPU0 (power states: C1[C1])
[4294679.915000] Attempting manual resume
[4294679.916000] swsusp: Suspend partition has wrong signature?
[4294679.957000] kjournald starting.  Commit interval 5 seconds
[4294679.957000] EXT3-fs: mounted filesystem with ordered data mode.
[4294681.766000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294686.498000] Adding 369424k swap on /dev/hda6.  Priority:-1 extents:1
[4294686.693000] EXT3 FS on hda3, internal journal
[4294693.608000] parport: PnPBIOS parport detected.
[4294693.609000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[4294693.705000] lp0: using parport0 (interrupt-driven).
[4294693.773000] mice: PS/2 mouse device common for all mice
[4294694.115000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294694.938000] ts: Compaq touchscreen protocol output
[4294697.484000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294698.150000] cdrom: open failed.
[4294698.885000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294698.954000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294700.324000] Linux agpgart interface v0.101 (c) Dave Jones
[4294700.349000] agpgart: Detected an Intel i810 E Chipset.
[4294700.354000] agpgart: detected 4MB dedicated video ram.
[4294700.401000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294700.638000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294700.654000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294700.654000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294700.845000] hw_random hardware driver 1.0.0 loaded
[4294703.412000] input: PC Speaker
[4294703.691000] Real Time Clock Driver v1.12
[4294703.797000] FDC 0 is a National Semiconductor PC87306
[4294705.906000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294718.523000] ACPI: Power Button (FF) [PWRF]
[4294718.805000] ibm_acpi: ec object not found
[4294726.508000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294726.508000] apm: overridden by ACPI.
[4294729.530000] Bluetooth: Core ver 2.7
[4294729.530000] NET: Registered protocol family 31
[4294729.530000] Bluetooth: HCI device and connection manager initialized
[4294729.531000] Bluetooth: HCI socket layer initialized
[4294729.570000] Bluetooth: L2CAP ver 2.7
[4294729.570000] Bluetooth: L2CAP socket layer initialized
[4294729.617000] Bluetooth: RFCOMM ver 1.5
[4294729.617000] Bluetooth: RFCOMM socket layer initialized
[4294729.617000] Bluetooth: RFCOMM TTY layer initialized
[4294740.476000] NET: Registered protocol family 10
[4294740.476000] Disabled Privacy Extensions on device c02eb280(lo)
[4294740.477000] IPv6 over IPv4 tunneling driver
[4294750.890000] eth0: no IPv6 routers present
ejaz@msiddique:~$

---

### Post by az on 2006-06-05
Can you try the Dapper live cd to see if your card is detected?

Nothing in dmesg seems relevant.

---

