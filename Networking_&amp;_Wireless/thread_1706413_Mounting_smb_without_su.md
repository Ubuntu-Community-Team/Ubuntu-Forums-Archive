---
title: "Mounting smb without su"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by dargaardms on 2011-03-13
I have a small shell scrip that allows me to mount my smb shares when I'm connected to the correct wifi.  My wife would like the same however she is not and administrator.  The scrip is run manually using gksu.  Is there any way to use mount with out sudo/gksu etc?  

Currently every time my wife wants access to a network drives (4 of them) she clicks "places" then "network" then waits 3 to 5 seconds then clicks "windows network" waits 3 to 5 seconds clicks our workgroup, waits 3 to 5 seconds clicks the server then waits another 3 to 5 seconds then she can mount 2 file systems at a time. She cannot mount all 4 at once she has to unmount before mounting another seems to be a limit of 2 mounts using this method.  She watched how I do it.  I click an icon on my panel and type my password and the 4 drives pop up on the desktop.

She is a basic user, will not touch a command line and I would prefer not to make her an administrator.  Any ideas how to make this easier for her?  For example is there a way to add mount lines to the fstab that can't actually be mounted until a user logs in and connects to a wireless network?

---

### Post by dargaardms on 2011-04-14
bump

---

