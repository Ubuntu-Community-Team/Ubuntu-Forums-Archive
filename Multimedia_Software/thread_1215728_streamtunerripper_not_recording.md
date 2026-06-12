---
title: "streamtuner/ripper not recording"
date: 2009-07-17
forum: Multimedia Software
---

### Post by bootdoc on 2009-07-17
just installed streamtuner and streamripper. When I hit the record button nothing happens.  I tried editing the record application in preferences changing 
x-terminal-emulator -e streamripper %q 
to 
konsole -e streamripper %q.  

when I hit the record button Konsole opens then immediately closes.

any idea how to get streamripper running.

EDIT: Here is more info.  Got konsole to stay open and got this error:
Warning: Could not find 'streamripperhttp://209.9.233.11:9310/grr-hidef.ogg', starting '/bin/bash' instead.  Please check your profile settings.
The streamripper setting is konsole -e streamripper%q

solved:
changed command to konsole -e streamripper %q

---

