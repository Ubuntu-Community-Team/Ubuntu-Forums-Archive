---
title: "[SOLVED] How to change default player"
date: 2008-06-29
forum: Multimedia Software
---

### Post by cova on 2008-06-29
I dont seem to be able to set my default media player. Trying to get Kaffeine for all my video and Exaile for audio. Not a fan of Totem and just love some of the extras on Exaile. Running Ubuntu Hardy.
Cheers!
Ben
EDIT: Using terminal or a GUI. not bothered, although wouldnt mind finding out both as Im trying to get to grips with the terminals ins and outs!

---

### Post by fiskking on 2008-06-29
in browser (firefox) click ´edit´, preferences, content, ´manage´ button for file type section.

---

### Post by cova on 2008-06-29
> **fiskking said:**
> in browser (firefox) click ´edit´, preferences, content, ´manage´ button for file type section.

edit, preferences, applications in ff3 right? surely that is only for downloading/using files through firefox?

---

### Post by Wobblybob on 2008-06-29
I think you want to change the default player for various input, if so you need to open Nautilus, go to [Edit], [Preferences], [Media] and in the [Music Player] option select the required paler in drop down boxes. If they are not present try this replacing my option with yours.

Copy and paste the following into a Terminal;

martin@linux: ~$ sudo gedit /etc/gnome/defaults.list

then edit the file changing the line 'x-content/audio-player=rhythmbox.desktop' to 'x-content/audio-player=amarok.desktop' then save the file and close gedit.

This creates several launcher files - amarok.desktop - but doesn't create one in '/usr/share/applications'. To solve this copy and paste the following into the Terminal;

martin@linux:~$ sudo cp /usr/share/app-install/desktop/amarok.desktop /usr/share/applications/

Now log out and back in, open Nautilus, go to [Edit], [Preferences], [Media] and in the [Music Player] option select Amarok from the drop down list. 

hope this helps

---

### Post by cova on 2008-06-30
By the looks of things I didnt need to go into Nautilus at all after reboot. File types were assigned correctly after the rest of it. Edited each input individually (ie ....-avi: kaffeine.desktop, ...mp3: exaile.desktop) and works like a charm!
Cheers!
Ben

EDIT: Ah, I see. The nautilus part is for setting DVD, VCD and Audio CD playback too.

---

