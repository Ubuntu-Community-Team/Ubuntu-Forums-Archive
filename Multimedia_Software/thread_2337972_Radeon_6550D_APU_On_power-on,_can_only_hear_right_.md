---
title: "Radeon 6550D APU: On power-on, can only hear right channel of audio"
date: 2016-09-23
forum: Multimedia Software
---

### Post by martinwguy on 2016-09-23
! Every time I turn my computer on, there is only sound in the right channel.

Alsamixer shows that I have two sound devices:
[Hit F6]:
[FONT=courier new][/FONT][FONT=courier new]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Scheda audio &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;- (predefinita)              &#9474;
&#9474;0 HD-Audio Generic[FONT=courier new]           &#9474;[/FONT]
 &#9474;1 HD-Audio Generic           &#9474;
&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[/FONT][FONT=courier new]
[/FONT]The first only has one toggle button labelled "S/PDIF".
The second is the real McCoy, with volume sliders and stuff.

Always, "Front" slider has the left channel at volume zero and the right channel at 100%.
I up the volume of that to max and presto I hear sound in both ears but when I shut down and boot again, it comes up the same way, with only the right channel making noises, so every time I have to open a terminal, start alsamixer, F6, down, enter, scroll left to "Front" and max the volume.

I thought ALSA saved the mixer settings from session to session, but it seems not to be doing so. It *does* save and restore the master volume setting for this device from session to session, so it doesn't seem to be a second-alsa-device issue.
Maybe it fails to save the "Front" setting?

The audio devices are built into the CPU (sorry, APU) and lspci says:
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]

How can I work around this?

---

