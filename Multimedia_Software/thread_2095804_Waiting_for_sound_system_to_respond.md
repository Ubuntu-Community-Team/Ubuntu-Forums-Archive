---
title: "Waiting for sound system to respond"
date: 2012-12-18
forum: Multimedia Software
---

### Post by heinstein101 on 2012-12-18
I've got Ubuntu 10.04 running on thin clients, but there's no sound! (Upgrading Ubuntu now is not an option at this stage)
Kernel: 2.6.36
Alsa driver version: 1.0.23
When checking lspci for hardware:

[I]Audio device: ATI Technologies Inc Device 1314
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HD) (rev 40)[/I]

But what I don't understand is, when I'm running "gnome-volume-control" (either from the gnome control center or from terminal) it doesn't show the audio settings dialog, instead it shows a popup saying "Waiting for sound system to respond"

And in the terminal it  prints out:
[I](gnome-volume-control:3311): WARNING **: Connection failed, reconnecting...
(gnome-volume-control:3311): WARNING **: Failed to connect context: Connection refused[/I]

Can anyone please advise what this means.. I really need the sound to work
Thanks.

---

