---
title: "[SOLVED] USB Headphones in VLC Player"
date: 2008-08-24
forum: Multimedia Software
---

### Post by fballem on 2008-08-24
I recently got a set of Logitech USB Headphones and got them to work through most sound applications except VLC. After some puttering, I finally got them to work through VLC. I am attaching some screen shots that I will be referring to in the rest of this note.

This note assumes that the Logitech USB Headphones are installed and working in other players and that the ALSA modules are installed. I believe the ALSA modules are installed by default in Ubuntu.

[LIST=1]
[*]Open VLC Player
[*]Select Settings | Preferences from the menu.
[*]Open the Audio portion of the resulting screen (see VLC Media Player-02.jpg)
[*]In the lower-right corner of the screen, click on Advanced Options. This should result in a screen similar to VLC Media Player-03.jpg
[*]Change the Audio output module to ALSA audio output - see VLC Media Player-04.jpg
[*]Save the setting - using the Save Button in the lower left of the Screen. This will close this screen and return you to the main menu of the VLC Player.
[*]Close the VLC Player (the setting will be applied the next time you open VLC)
[*]Open VLC Player and select Settings | Preferences | Audio | Output modules | ALSA (see VLC Media Player-06.jpg)
[*]If the Logitech USB Headphones are not in the list, then select the Refresh button.
[*]Select the Logitech USB Headphones from the list, then select the Save button. (see VLC Media Player-07.jpg)
[/LIST]

You will not need to restart VLC to change settings. If you want to go through speakers, just select Settings | Preferences | Audio | Output Modules | ALSA, change the device, and then Save.

I don't guarantee that this will work for everyone, but it may help.

Regards,

---

