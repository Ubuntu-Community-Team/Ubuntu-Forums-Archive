---
title: "wine + jack + 6fire = no sound"
date: 2008-05-19
forum: Multimedia Software
---

### Post by Skrelpawin on 2008-05-19
Hi everyone,

i'm new to all this Linux stuff. I've installed UbuntuStudio (AMD64). Most Applications working fine. But:

Run VSTHOST.exe in wine. Success
Start RealGuitar as Plugin from VSTHOST.exe. Success
Play Guitar using Mouse. Success
Hearing what i play. Succes
Start Jack. Error!!!
The other way round it doesn't work better:
Start Jack. Success
Run VSTHOST.exe in wine. Success
Start RealGuitar as Plugin from VSTHOST.exe. Success
Play Guitar using Mouse. Success
Hearing what i play. Error!!! No sound = yes!

I've taken a look in the VSTHOST.exe config. When Jack is down when VSTHOST.exe starts i have 2 Wave-Channes (1 Input (Stereo)/ 1 Output (Stereo). Starting Jack fails.
When Jack is up an running while i'm starting VSTHOST.exe the two Channes (Wave In- & Output) are not there.

I don't think that wineasio is installed because i don't find any wineasio.dll on my system.

Anybody an idea? 
Skrelpawin

---

