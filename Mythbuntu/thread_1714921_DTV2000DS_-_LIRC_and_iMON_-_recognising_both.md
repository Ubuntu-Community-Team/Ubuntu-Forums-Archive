---
title: "DTV2000DS - LIRC and iMON - recognising both"
date: 2011-03-26
forum: Mythbuntu
---

### Post by acrowe on 2011-03-26
Hi all,
 
I am running Mythbuntu 10.10 with a DTV2000DS TV card and remote.
The remote on this card appears to be iMON (?) compatible - even when LICR is not running some remote control commands are recognised (mainly the up, down, left and right and a few other buttons).
 
I have configured LIRC for this remote and this is now working.
When in Mythbuntu Front end:
 
- if LIRC is running and I press an arrow button on the remote it jumps two menu selections
- if LIRC is stopped it only moves one menu selection.
 
This leads me to conclude that when LIRC is running and I press the arrow button both LIRC and the iMON (?) and receiving this signal and Mythtv is receiving two commands (arrow button presses)
 
I can't work out how to stop the iMON(?) signals being received so only LIRC is receiving and processing the remote control commands?
 
Also interestingly I was playing with the LIRC config files (thinking maybe it was a repeat or delay issue). To test LIRC I removed the ~/.lircrc file (after making a backup first) and restarted LIRC. Amazingly LIRC is still functioning and Mythtv is still recognising button presses through LIRC. Where would it be reading the config from if there is no ~/.lircrc file?

---

### Post by acrowe on 2011-03-26
Looking into this further it appears all button presses are generating '2' presses.
(if push 1 once and it generates 11)
 in irw it is only generating one code (0000000080010002 00 KEY_1 devinput) however in Mythtv when watching TV pushing the '1' key on the remote goes to channel 11
 
does anyone know why this might be occuring? I have reied editing ~/.lirc/mythtv however as when I removed ~/.lircrc and everything still runs I am confused now where the settings for LIRC and Mythtv are residing.

---

### Post by wyliecoyoteuk on 2011-03-26
~/.lirc.rc is just a pointer to the ~/.lirc folder, where mythtv has its own lirc config file, whereas irw reads from

/usr/share/lirc/remotes/your_remote.conf

which is where the defaults are set.

I think that effectively, any button press that emulates a keyboard command that Mythtv understands will work anyway.

---

