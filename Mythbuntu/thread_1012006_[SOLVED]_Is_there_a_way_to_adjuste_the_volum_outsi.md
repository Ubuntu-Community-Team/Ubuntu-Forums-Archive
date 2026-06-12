---
title: "[SOLVED] Is there a way to adjuste the volum outside MythTV?"
date: 2008-12-15
forum: Mythbuntu
---

### Post by Archmage on 2008-12-15
I don't know if this should be a Mythbuntu or Xbuntu-Problem. But is there a easy way to acces my volume-control? I know in Ubuntu I just click on the volume bar in the task bar and than I can adjust everything, but there isn't such in Mythbuntu, is it?

I can only go in my settings manager in the aduion option an can set what I want to adjust (microphone, speaker and so on). But there seems no way to adjust them.

---

### Post by volkswagner on 2008-12-15
To adjust the volume while in mythtv use keyboard [ and ] for volume up and down respectively.

To set a preset sound level within mythfrontend go to >Utilities/Setup >Setup>General, on the third page you can adjust the PCM and Master Mixer volume sliders to increase or decrease the default start sound level.  

Use Internal Volume Control box must be checked to reveal the above sliders.

---

### Post by Archmage on 2008-12-16
Thanks. But how can I do this Outside of Mythtv/Mythfront?

Or should I better ask this in the Xbuntu-Forum?

---

### Post by EasyRiderOnTheStorm on 2008-12-16
As I understand what you're asking is how to control volume on a Mythbuntu-installation, but not using the "[" / "]" keys or the remote (not from within the frontend).

If you're outside the frontend, you should have a taskbar on the top; if you right-click on it, you can add widgets to it next to the clock. One such widget you'll find in the list that opens is a volume control.

Or you can open the Synaptics package manager and search for "mixer" - there are several different ones, pick one, install, done - they should show up in your menu.

Or you can open a terminal, type "alsa-mixer", and get a text-mode semi-graphic mixer with sliders and switches.

Good luck, I hope one of these is what you're looking for... ;)

---

