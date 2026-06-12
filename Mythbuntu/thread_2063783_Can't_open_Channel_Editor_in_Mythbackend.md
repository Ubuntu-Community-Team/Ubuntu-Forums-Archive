---
title: "Can't open Channel Editor in Mythbackend"
date: 2012-09-27
forum: Mythbuntu
---

### Post by dvjunk on 2012-09-27
I am running fixes/0.25 and when I try to go to the backend channel editor it doesn't do anything, just stays at the main menu. It worked when I first set up my system about a month ago. I can't seem to find this symptom in the forums.

TIA!

---

### Post by klc5555 on 2012-09-28
You might get a more illuminating symptom or error message by going to the desktop and running ```
sudo mythtv-setup
``` from a terminal.

Attempt to open the Channel Editor from there. When/if opening Channel Editor fails, immediately foreground the terminal window itself with alt-tab and note of any error messages that may have echoed in the terminal, if any did. Might be something someone can diagnose from.

---

### Post by nickrout on 2012-09-28
> **klc5555 said:**
> You might get a more illuminating symptom or error message by going to the desktop and running ```
sudo mythtv-setup
``` from a terminal.

Attempt to open the Channel Editor from there. When/if opening Channel Editor fails, immediately foreground the terminal window itself with alt-tab and note of any error messages that may have echoed in the terminal, if any did. Might be something someone can diagnose from.do not use sudo for mythtv-setup.

---

