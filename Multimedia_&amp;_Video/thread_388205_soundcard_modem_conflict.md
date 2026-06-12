---
title: "soundcard modem conflict"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by eggdeng on 2007-03-19
On a fresh install of Edgy, I am getting persistent crackling when I try to play any sound file. My set up is as follows:

lspci output:
VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)

cat /proc/asound/cards
 0 [V8233          ]: VIA8233 - VIA 8233
                      VIA 8233 with VIA1612A at 0x1800, irq 11
 1 [modem          ]: VIA82XX-MODEM - VIA 82XX modem
                      VIA 82XX modem at 0xe000, irq 11

cat/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.12rc1

As the sound card and modem are sharing an IRQ, I would like to follow a suggestion I have come across and disable the modem. Any ideas as to how to go about doing this?

---

### Post by eggdeng on 2007-03-19
bump

---

### Post by eggdeng on 2007-03-19
OK, one more time.

---

### Post by twidget on 2007-03-20
have you tried pulling the card or switching the modem off in bios?

---

### Post by eggdeng on 2007-03-21
Thanks for the suggestion. Unfortunately, the chip is integrated on the motherboard and the bios gives no option to disable. I finally got rid of the crackling by going to System->Sounds->Preferences and choosing the via sound card option on the devices tab.:)

---

### Post by eggdeng on 2007-04-01
But it came back again. In the end, it tuned out to be a known problem with VIA VT8233, documented at
[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg08159.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg08159.html)
The fix is to add the option ```
options snd-via82xx index=0 dxs_support=2
``` to the end of /etc/modprobe.d/alsa-base.

---

