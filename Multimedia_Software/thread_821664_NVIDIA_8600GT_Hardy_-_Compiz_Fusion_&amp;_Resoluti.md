---
title: "NVIDIA 8600GT Hardy - Compiz Fusion &amp; Resolution Issues"
date: 2008-06-07
forum: Multimedia Software
---

### Post by vandalous03 on 2008-06-07
Hello people.I really need your help.
I had an ATi Card (X700 Pro//open source driver) installed on my desktop.Recently i was forced to change this card with an Nvidia 8600 GT but unfortunately i couldn't manage to have 3d effects and high resolutions.
I tried the ENVY NG method with no good results.(My monitor was turning off after the reboot of ENVY NG installation)I also tried to install the drivers through the standard method from nvidia.com.What's th problem? 
I it a hardware incompatibility issue? Do i need to remove the ATi open source drivers and then re-install the nvidia?How can this be done?
Has anyone faced any situation similar to this?
Any suggestions would be appreciated...PLZ help!

---

### Post by pietjanjaap on 2008-06-07
Go to the envy website, write down the dos commands.
First do the last options, ubuntu searches for your hardware, videocard and monitor.
Go to texmode uninstall all video drivers with envy.

From here on try:
1 install with envy?
2 reboot, and install without envy?

---

### Post by mastermindg on 2008-06-07
I'm on Hardy and my Nvidia 8500GT works fine without the Envy drivers.

Use nvidia-settings. I've got Compiz working with twinview on two widescreen displays at 1400X900 Res.

---

### Post by vandalous03 on 2008-06-08
Unfortunately nothing worked out...
I tried every possible method and still i face this situation.
Some people talk about a fresh install though i don't want to choose this solution cause i really enjoy the way i made my desktop look like and i have a few important stuff.
Any other suggestions?
Sometimes i'm getting to a srceen that sais that i have to configure my display so i do all the appropriate configuration and unfortunately it doesn't change to my preferences...!
I'm really pissed off with that card, though it is a good one...What can i do to fix this?
The "nvidia-xconfig" from terminal didn't help and i also tried different versions and older versions of the driver.
Any help please, ideas,suggestions.Anything would be appreciated!
Thanx.
Just in case my desktop configuration is:
Nvidia 8600GT 512MB (Gigabyte)
Ubuntu Hardy Heron with all the latest updates

...I want my 3D_effects/Compiz Fusion back...!!!!!!!!!!!
plz help!

---

### Post by vandalous03 on 2008-06-09
Any help on this people?

---

### Post by vandalous03 on 2008-06-10
Any news???

---

### Post by Erlander on 2008-06-10
Envy has an option of removing old drivers.  I would do that both for your old ATI and the newer Nvidia.  You may have to reboot for each.

Then try to install and see if that works.

Rob

---

