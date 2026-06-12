---
title: "Problem with Brasero"
date: 2009-09-11
forum: Multimedia Software
---

### Post by seancyril on 2009-09-11
Hi everyone. I have been using Brasero for ages to burn DVDs and CDs with Ubuntu 8.10 and never had a problem. Now suddenly it keeps crashing on me. Whenever I click on new audio project I get a beep from the motherboard speaker. When I start browsing to select a file in the bottom of the programme I can see the number of files selected start racing away 6 files selected, 12 files selected etc. It does this for a while and then the whole thing just crashes. This is even before I have got round to selecting any files to add to the new project!
I've tried uninstalling it completley form synaptic but when I re-install it just comes back with the same glitches. 
Has anyone else had this problem and know any solutions? I have installed K3b and it works fine but I prefer Brasero so would like to get it up and running if possible.
Thanks in advance for any replies:confused:

Sean

Ubuntu 8.10, GNOME, Amd Athlon XP, 1 GB Ram

---

### Post by ahbart on 2009-09-11
> **seancyril said:**
> I've tried uninstalling it completley form synaptic but when I re-install it just comes back with the same glitches. 

Removing and reinstall won't help a lot. If you suspect it is a configuration issue you could remove the configuration files in you home directory. I think this would be:
- /home/username/.gconf/apps/brasero
and retry.

---

### Post by seancyril on 2009-09-11
I tried this and reinstalled but  it is still broken. When I go to Applications> Sound and Video the icon for Brasero isn't even displaying. Just a generic icon

---

### Post by boron on 2009-09-11
> **seancyril said:**
> Hi everyone. I have been using Brasero for ages to burn DVDs and CDs with Ubuntu 8.10 and never had a problem. Now suddenly it keeps crashing on me. Whenever I click on new audio project I get a beep from the motherboard speaker. When I start browsing to select a file in the bottom of the programme I can see the number of files selected start racing away 6 files selected, 12 files selected etc. It does this for a while and then the whole thing just crashes. This is even before I have got round to selecting any files to add to the new project!
I've tried uninstalling it completley form synaptic but when I re-install it just comes back with the same glitches. 
Has anyone else had this problem and know any solutions? I have installed K3b and it works fine but I prefer Brasero so would like to get it up and running if possible.
Thanks in advance for any replies:confused:


Ubuntu 8.10, GNOME, Amd Athlon XP, 1 GB Ram
Sean
Hi Sean,
I've got a problem with brasero, too. When copying a dvd I get a message saying that it is unable to save the copied information, try another location? But when I tried that, this returned a similar message saying I did not have permissions to the location I'd selected (a new folder created in my home directory).  I had no problems with K3b so that's what I use.  But good luck with finding a solution .:)

---

### Post by gwm on 2009-09-12
Hi SeanCyril,
I'm running Hardy Heron on this box and I've also found Brasero just hangs on me. I use System Monitor to kill it and try again a couple of times. Each time it gets a bit further and eventually I have my CD.
As far as I can remember, for several years now, it has always hung on me when I close it.

---

