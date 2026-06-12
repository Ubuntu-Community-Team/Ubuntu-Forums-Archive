---
title: "ALC268 realtek soundcard on Ubuntu 9.10"
date: 2010-03-02
forum: Multimedia Software
---

### Post by raunhar on 2010-03-02
I am using 9.10 . Till around three hours back, sound was there. After restarting the computer, there was no sound.
I checked the sound pref. Nothing was mute. The sound icon showed:
Output 48%
-19.13dB, Dummy Output

What can be reason and the solution.

---

### Post by mikewhatever on 2010-03-02
Dummy Output means something must have gone wrong during bootup. Can you post the output of the following:

dmesg | grep -i hda

---

### Post by raunhar on 2010-03-02
dmesg | grep -i hda
[   12.266396] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.266447] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.455717] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   12.455830] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9


I removed pulseaudio from Syneptec and the sound was back, but the volume control vanished.
Esound is there

---

### Post by mikewhatever on 2010-03-02
Yea, that's a known problem for those opting to remove pulseaudio. Installing gnome-alsamixer lets you adjust sound levels, but there is still no icon in the menu. Anyway, guess the problem is solved for now.

---

### Post by raunhar on 2010-03-02
But I need the control icon, as many a times I have to decrease the volume and the function key volume control also does not show the status

---

### Post by raunhar on 2010-03-02
Done. Removed all: Pulseaudio, Esound, ALSa. reboot and reinstalled pulseaudio
Sound was back

---

