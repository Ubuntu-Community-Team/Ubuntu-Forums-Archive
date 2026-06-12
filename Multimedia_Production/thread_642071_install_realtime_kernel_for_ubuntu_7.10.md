---
title: "install realtime kernel for ubuntu 7.10"
date: 2007-12-16
forum: Multimedia Production
---

### Post by FredoV on 2007-12-16
Hi!

Ubuntu Studio looks like overkill for me. If I could install only the Music/Sound section of it I would be happy!

So the idea of "upgrading" the Feisty Kernel to RealTime, and install Rosegarden, Lilypond, FluidSynth and Audacity (and the stuff these depend on!) sounds more reasonable to me. As reference: at present time I STILL do my music stuff under Win (Cakewalk, Audacity, FluidSynth, Sibelius), but writing + Inet is already at Ubuntu. "Migrating to Lin" is the name of the game.


QUESTIONS:

Can this be done?
Is there some script available to get it done? 
Or can it be done via Synaptic Package Manager?
Would there be a change in the Maintenance/Upgrade Procedures of Ubuntu?


Any suggestions or help I will appreciate!

FredoV (Valencia, Spain)

---

### Post by salamba on 2007-12-16
for the RT kernel only, through package manager,  install package named:  linux-rt

---

### Post by philc on 2007-12-16
When installing Ubuntu studio from the Live CD it is possible to just select the main elements you need. So, for example, if you don't want the Video Production section, simply don't select it for installation.

---

### Post by BLTicklemonster on 2007-12-16
What is the advantage to the casual observer to install linux -rt if they decided to do so?

---

### Post by FredoV on 2007-12-16
Thank you! 

When asking the package manager to get "linux-rt" the answer was "Package Not Found". 

Continuing the search, a script was seen at 
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy"), and after evaluation of risk it it was executed (I do have confidence on Ubuntu Forums!).

Again, it returned a "linux-rt" not found, altough the Package Manager DID find it after insisting!

All is running. 

Only a detail: at startup, it stops at a Terminal Screen with a Command Prompt "FredoV@myPC"! I dont know what is required, but typing "Exit" continues the load and gets my up and running. 

Obviously I DO NOT want to enter that command every time the Computer is booted!
Any hint about a remedy?

:-)

FredoV  (Valencia, Spain)

---

### Post by crush304 on 2007-12-16
linux-rt is in multiverse

you can also install ubuntustudio-audio (universe) for the ubuntu studio audio packages

---

### Post by FredoV on 2007-12-16
As said: RealTime is running now. Thanks for the Help!

Only a detail: at startup, my (now) present setup stops at a Terminal Screen with a Command Prompt "FredoV@myPC"! I dont know what is required, but typing "Exit" continues the load and gets my up and running. 

Obviously I DO NOT want to enter that command every time the Computer is booted!
Any hint about a remedy?


Your help IS appreciated!
FredoV (Valencia, Spain)

---

