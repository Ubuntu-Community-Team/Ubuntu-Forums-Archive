---
title: "PulseAudio Applet shows signal, but still no sound"
date: 2009-08-08
forum: Multimedia Software
---

### Post by haaxerei on 2009-08-08
I've searched now for two days but none of the solutions did work for me - so I post my problem here.

Like so many Ubuntu users, I don't have sound, but when I click on the "PulseAudio applet>Volume Control", it shows me that it has a signal, but I still can't hear something. I thought I'd might blown up my Laptop-Speakers, but now I have plugged in some Earphones and I still can't hear something.

Does anyone know what I might have ignored?
If u need a log file or smth, just post what, i'll give it to you x)
And yes i rebooted the laptop ah few times and i restarted and reconfigured alsa etc...

- Ah I forgot, I can hear a very gentle swoosh all the time

---

### Post by haaxerei on 2009-08-09
noone knows what to do?

---

### Post by markbuntu on 2009-08-09
right click in the volume control on the moving bars and try to move the stream. There is more on setting up your sound properly here


[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by haaxerei on 2009-08-09
> **markbuntu said:**
> right click in the volume control on the moving bars and try to move the stream. There is more on setting up your sound properly here


[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
```

killall pulseaudio

sudo alsa force-reload

pulseaudio -D
```When I use your code to restart the whole soundserver thing, then i have to error messages: 
When I force ALSA to reload
```
WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/oops/.gvfs
      Output information may be incomplete.
```Or with pulseaudio:
```
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: main.c: Start des Dämons fehlgeschlagen.
```As I see something with the userrights or some space?? not correct?

edit:// ah forgot, i can't right click on the moving bars, then i can just choose "default" and that's all over the upper part of the window...
thx

---

### Post by haaxerei on 2009-08-10
So, I found the error, if I open the Pulseaudio Volume Control via the terminal
```
pavucontrol
```
And then i click on "output devices" and try to change the volume, then this happens in the terminal:
```

oops@4n0nyM:~$ pavucontrol
(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver
** (pavucontrol:15485): DEBUG: blah: alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
** (pavucontrol:15485): DEBUG: -5 = No such driver

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

(pavucontrol:15485): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Fehler in Zeile 1, Zeichen 25: »>« ist kein gültiges Zeichen, wenn es auf die Zeichen »</« folgt; »>« darf keinen Elementnamen beginnen

```

---

### Post by haaxerei on 2009-08-19
sry for triplepost -.-

So, i got finally the solution and i thought if someone has the same problem with this Laptop...

hp pavillon dv7 1053 
... it would just be fair to post it here...


then you should upgrade to kernel  "2.6.28-14-generic"
and then it works

greets

---

