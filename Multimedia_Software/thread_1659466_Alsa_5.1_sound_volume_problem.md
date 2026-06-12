---
title: "Alsa 5.1 sound volume problem"
date: 2011-01-04
forum: Multimedia Software
---

### Post by Shadow Player on 2011-01-04
Hi everybody

I'm running into small trouble with my new USB external 5.1 soundcard.

The card is supported and works out-of-the-box, no driver problems.

- but -

Each time I boot I have to open alsamixer, select my sound card, and pull all the volume levels up. When I reboot all the volume levels are 0 again.

- and -

The channels in alsamixer are in the wrong order i.e. when I rise the "Side Speakers" volume, the rear speakers will go louder.

This leaves me with a doubt; if I play 5.1 sound in let's say Audacious - will the "Side Speaker" channel play in the rear speakers?

- Additional info -

This is my sound card:

```
Bus 004 Device 002: ID 0d8c:0102 C-Media Electronics, Inc. CM106 Like Sound Device
```

The sound card has the following out/inputs:

6 x 3.5mm jacks output (Front, Surround, Center/Bass, Back - Headphones and Line-In)
2 x S/PDIF (In and Out)
1 x USB input.

It supports up to 7.1 channels, but my speakers are 5.1 - connected are: Front, Surround, Center/Bass.

I'm running Ubuntu Lucid.

The sound profile I chose in gnome-volume-control is 'Analog Surround 5.1 Output'.

---

### Post by Shadow Player on 2011-01-06
shameless self-bump...

---

### Post by Shadow Player on 2011-01-07
I upgraded to Maverick, but the problem persists.
Please - if anyone has a starting point for me I'll try everything out.

---

### Post by BicyclerBoy on 2011-01-07
This was happening to lots of MythTV users about 1 to 1.5 years ago...
Seems to recur year after year 

From memory the pulseaudio startup process was causing the levels to be set to zero

alsamixer
(set your levels)
alsactl store

may need sudo alsactl store...

---

### Post by Shadow Player on 2011-01-12
thank you for your reply. I have been testing this solution and here's what I've figured out:

When I do
```
sudo alsactl store
```
It stores the configurations as expected, but:

- If I then reboot **without** my USB sound card connected, the stored levels remain but when I connect my sound card after the boot it only sounds on the front speakers L and R.

- If I reboot **with** my USB sound card connected, the stored levels get lost and are reset to zero again, but my speakers sound on all 6 channels.

---

### Post by Shadow Player on 2011-01-13
And additionally, I noticed that when I boot without my USB sound card connected, once I connect it, thou the alsa volume levels are ok, I can't choose 5.1 in gnome-volume-control.

[edit]

this can be fixed by doing

```
sudo alsactl force-reload
```

(normal reload won't)

Once Alsa is reloaded, I can proceed to assign the correct 5.1 surround profile in gnome-volume-control, and go to alsamixer and pull the volume levels up again...
headache!!!

---

