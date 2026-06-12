---
title: "Sound card missing"
date: 2010-12-07
forum: Multimedia Software
---

### Post by beagley on 2010-12-07
My sound card has disappeared!

> [FONT="Courier New"][COLOR="Blue"]aplay -l[/COLOR]
aplay: device_list:223: no soundcards found...

[COLOR="blue"]lspci | grep EMU10k1[/COLOR]
04:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)

[COLOR="blue"]lsmod | grep snd[/COLOR]
# Nothing![/FONT]


Sound was working fine until:
[LIST]
[*]Installed icecast2 and darkice
[*]With icecast2 and darkice running I invoked [COLOR="Blue"]pavucontrol > Recording > ALSA capture from > Monitor of SB Live![/COLOR]  (I was now successfully streaming from my sound card and the sound card was still working normally, too.)
[*]Shut-down machine. Re-booted next day. No sound!
[/LIST]

[COLOR="Blue"]pavucontrol > Output Devices[/COLOR] now just shows "Dummy Output".
icecast2 is running as a daemon but I've left darkice as something to be run on demand. So, note that I do not currently have darkice running. icecast2 is running but (as I understand it) doesn't have anything to do with my sound card.

The fact that the issue seems to have occurred shortly after installing the icecast stuff may be a coincidence (but that seems unlikely).

I'm running Ubuntu 10.04.

Any suggestions much appreciated.

---

