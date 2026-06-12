---
title: "Can't Disable Totem Autoplay w/ VCDs"
date: 2007-08-11
forum: Multimedia &amp; Video
---

### Post by Sean Babu on 2007-08-11
Hi All,

I looked but couldn't find a solution to this one.

Whenever I insert a VCD into the CD-ROM drive, Totem starts up. This is not good because it's not playing them for me. (I use mplayer instead.)

I went to **System>Preferences>Removable Drives & Media**. I disabled autoplay for all media, but it still happens. (It did however stop the auptoplay of DVDs.)

Is there somewhere else I should be looking?

---

### Post by klytu on 2007-08-11
> **Sean Babu said:**
> Hi All,

I looked but couldn't find a solution to this one.

Whenever I insert a VCD into the CD-ROM drive, Totem starts up. This is not good because it's not playing them for me. (I use mplayer instead.)

I went to **System>Preferences>Removable Drives & Media**. I disabled autoplay for all media, but it still happens. (It did however stop the auptoplay of DVDs.)

Is there somewhere else I should be looking?

Try: ```
gconf-editor
``` Navigate to desktop>gnome and highlight volume_manager.  In the right-hand pane scroll down to autoplay_vcd and clear that checkbox. You can then close the editor and test to see if VCD autoplay has stopped. If this works (it should), you can then re-enable autoplay for the rest of your media. 

Incidentally, if you want VCDs to automatically  playback with mplayer, try ```
mplayer vcd://2
``` as your autoplay_vcd_command in gconf-editor and leave the autoplay_vcd checkbox checked.

---

### Post by Sean Babu on 2007-08-11
> **klytu said:**
> Try: ```
gconf-editor
``` Navigate to desktop>gnome and highlight volume_manager.  In the right-hand pane scroll down to autoplay_vcd and clear that checkbox. You can then close the editor and test to see if VCD autoplay has stopped. If this works (it should), you can then re-enable autoplay for the rest of your media. 

Incidentally, if you want VCDs to automatically  playback with mplayer, try ```
mplayer vcd://2
``` as your autoplay_vcd_command in gconf-editor and leave the autoplay_vcd checkbox checked.

Thanks for the help.

Hmmm. I tried that just now, and I'm sorry to say that it didn't work. Seems like it should. I even rebooted. Any other ideas?

---

### Post by klytu on 2007-08-11
> **Sean Babu said:**
> Thanks for the help.

Hmmm. I tried that just now, and I'm sorry to say that it didn't work. Seems like it should. I even rebooted. Any other ideas?

Which part didn't work? Do you mean that clearing the autoplay_vcd checkbox didn't stop autoplay of  VCDs? Or do you mean mplayer wouldn't play VCDs automatically with the second suggestion? Or did neither of those work? You wouldn't need to reboot ....

---

### Post by Sean Babu on 2007-08-11
Sorry. (Precision is the key to clear communications.)

Clearing the checkbox didn't stop the autoplay. I'm not too interested in having mplayer automatically start. I like to stick in discs and then have them do nothing until I tell them. (I've been burned recently on Windows, can you tell?)

---

### Post by klytu on 2007-08-11
> **Sean Babu said:**
> Sorry. (Precision is the key to clear communications.)

Clearing the checkbox didn't stop the autoplay. I'm not too interested in having mplayer automatically start. I like to stick in discs and then have them do nothing until I tell them. (I've been burned recently on Windows, can you tell?)

I am at a loss at to why clearing the autoplay_vcd checkbox didn't stop autoplay for you (I confirmed it works for me on all three of my computers that run Ubuntu - 2 are running Feisty and one is running Dapper). My intuition is that probably the VCD in question is not actually recognized by Gnome's volume manager as being a VCD for some reason.  At the moment I don't know a simple procedure you could use to test this.

---

### Post by Sean Babu on 2007-08-11
Ah well. It's not a big deal. Thanks anyway.

---

### Post by Sean Babu on 2007-08-12
The bumpage of hope.

---

