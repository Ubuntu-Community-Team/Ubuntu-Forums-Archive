---
title: "No video, Mythbuntu 11.10 new install, legacy nvidia card"
date: 2011-11-04
forum: Mythbuntu
---

### Post by ransae on 2011-11-04
After an unsuccessful online upgrade attempt, I tried to install Mythbuntu 11.10 using a CD. 

All seemed to go well during the install, however, on start up I get no video after the PCs splash screen. Can't access the text terminals either. 

Analogue TV using component video. Selected the nvidia driver, PAL B (for Australia)

I think the problem is probably the nvidia driver. I'm pretty sure I need the **96.43.xx **version.

Does MythB 11.10 support the legacy driver? Is there any trick during install to get it to use the correct version?

Any help much appreciated.

---

### Post by nickrout on 2011-11-04
> **ransae said:**
> After an unsuccessful online upgrade attempt, I tried to install Mythbuntu 11.10 using a CD. 

All seemed to go well during the install, however, on start up I get no video after the PCs splash screen. Can't access the text terminals either. 

Analogue TV using component video. Selected the nvidia driver, PAL B (for Australia)

I think the problem is probably the nvidia driver. I'm pretty sure I need the **96.43.xx **version.

Does MythB 11.10 support the legacy driver? Is there any trick during install to get it to use the correct version?

Any help much appreciated.

It would appear so:

[http://packages.ubuntu.com/search?keywords=nvidia-96&suite=default&section=all&arch=any&searchon=names](http://packages.ubuntu.com/search?keywords=nvidia-96&suite=default&section=all&arch=any&searchon=names)

---

### Post by ransae on 2011-11-04
Given that the drivers exist ...

Is there any way to get the installer to use the legacy driver?

or ..

How can I get the box to boot in safe mode so I can get to a terminal and change it by hand?

---

### Post by ransae on 2011-11-04
Had a play around with the system this morning and fixed the problem.

Logged in using safe mode (press esc on boot) and found that no nvidia drivers had been installed.

Used ssh -X  to log in from another box. Opened the Control Centre and installed the drivers from there. The box boots up fine now.

There is a bug in the installer, as it doesn't seem to pick up legacy nvidia card on install.

---

