---
title: "speaker/headphone make sound at the same time"
date: 2005-12-23
forum: Multimedia &amp; Video
---

### Post by chomg on 2005-12-23
Hi, all,

I recently installed Ubuntu 5.10 on my Dell Dimension 9100 machine. During the installation, the sound devices seem to be configured properly without any problem. Although, I found out that the speaker makes sound even though I attach a headphone to the haedphone jack on the front panel. When I booted the machine with Windows XP, the speaker doesn't make sound as expected.

Could anyone give me the direction what configuration files I should change? Thanks in advance.

I put some of configuration files even though I don't know what files I should put here. If you need more of my configuration files, let me know. Thanks a lot in advance.

$ cat /proc/devices
Character devices:
  1 mem
  2 pty
  3 ttyp
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 29 fb
116 alsa
119 vmnet
128 ptm
136 pts
180 usb
216 rfcomm
254 devfs

$ cat /proc/modules | grep snd
snd_hda_intel 17856 1 - Live 0xf8bcb000
snd_hda_codec 80448 1 snd_hda_intel, Live 0xf8c50000
snd_pcm_oss 53760 0 - Live 0xf8c41000
snd_mixer_oss 19584 1 snd_pcm_oss, Live 0xf8b24000
snd_pcm 92900 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss, Live 0xf8be7000
snd_timer 25956 1 snd_pcm, Live 0xf8bb1000
snd 57764 8
snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer, Live
0xf8bbb000
soundcore 10176 1 snd, Live 0xf8ba4000
snd_page_alloc 10824 2 snd_hda_intel,snd_pcm, Live 0xf8b01000

$ cat /etc/udev/alsa-utils.rules
KERNEL=="controlC[0-7]", ACTION=="add", RUN+="/lib/alsa-utils/udev"

---

### Post by dsmoney on 2006-02-17
Chomg

---

### Post by dsmoney on 2006-02-17
I own a dell B130 laptop and am having the same issue. It is rather inconvenient and unfortunately I cannot offer any assistance.

If there is anyone who knows a fix for this please post!

Thanks a ton

---

### Post by blucia0a on 2006-05-24
I am having exactly the same problem with a Dell Inspiron B130 with the intel HDA chipset.  kernel 2.6.15-18-386, the following relevant modules loaded at boot time

/lib/modules/2.6.15-18-386/kernel/sound/pci/snd-intel8x0.ko
/lib/modules/2.6.15-18-386/kernel/sound/pci/snd-intel8x0m.ko
/lib/modules/2.6.15-18-386/kernel/sound/pci/hda/snd-hda-intel.ko

I read (forget where) in my search for  solution to this that a kernel patch exists to fix this.  If anyone has information on this, or some other means of workaround, i'd appreciate it.

Does anyone know what bit of the system senses the headphones?  is it part of the intel module, or something else?

---

### Post by blucia0a on 2006-05-26
i found a workaround to this problem:
plug in the headphone/external line *before* booting.  This way, the card's auto-sensing doesn't have to do anything, it just starts in external line mode.  This is speculation on my part, but it works, and its the only explanation i can think of.  Anyhow, try that.  Also, anyone else here have occasional choppy playback?  I'm going to compile the module into the kernel and see if it stops, but anyone with experience who could lend insight would be appreciated.

---

### Post by juicybananahead on 2006-06-01
!

---

