---
title: "vlc plugin fluidsynth"
date: 2023-05-24
forum: Multimedia Software
---

### Post by wmrp on 2023-05-24
I want to install the vlc plugin fluidsynth, but I don't know which one to choose as there are several options. I run ubuntu 20.04 on my desktop. [https://packages.ubuntu.com/focal/vlc-plugin-fluidsynth](https://packages.ubuntu.com/focal/vlc-plugin-fluidsynth)

---

### Post by Holger_Gehrke on 2023-05-24
The packages you see at that URL are for various different architectures of hardware (specifically different kinds of processors, modern PC systems are usually amd64). When downloading and installing packages through the package manager, it will automatically select the one that's right for your hardware. Just enter 'sudo apt-get install vlc-plugin-fluidsynth' on the command line and the plugin and everything it needs to work that isn't yet installed will be.

Holger

---

### Post by wmrp on 2023-05-25
Thank you for that. I installed the plugin, but am not sure why it does not add to the vlc player.

---

### Post by Holger_Gehrke on 2023-05-25
It doesn't do anything visible, but if it's installed and vlc is using it, then vlc will play MIDI-files by feeding them into Fluidsynth. Just try to open a MIDI file in VLC ...

Holger

---

### Post by wmrp on 2023-05-29
I get this error message.    [COLOR=#ff0000]Codec not supported:[/COLOR]
 [COLOR=#000000]VLC could not decode the format "MIDI" (MIDI Audio)[/COLOR]
 [COLOR=#000000]

[/COLOR]

---

### Post by Holger_Gehrke on 2023-05-29
How did you install vlc ? If it's installed as a snap, then I don't know whether it's even possible to install plug-ins. To find out try 'snap list' in a terminal. If vlc is in the list you get after entering that command then it's a snap.

Holger

---

### Post by wmrp on 2023-06-06
I tried via synaptic and also as a terminal command.

---

