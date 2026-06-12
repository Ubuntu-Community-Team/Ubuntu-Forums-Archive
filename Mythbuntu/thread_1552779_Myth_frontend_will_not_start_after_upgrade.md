---
title: "Myth frontend will not start after upgrade"
date: 2010-08-14
forum: Mythbuntu
---

### Post by meanmrmustard on 2010-08-14
I just upgraded my secondary (F/E/ B/E) machine to the Lynx version. I ran into a problem with the nvidia driver and resolved it but when I try to start myth frontend - either from the drop down menu or at the CLI nothing happens, though the cli returns "command not found".
I don't see anything in particular in the logs that would explain it, the backend log just says it cannot connect to the database on the primary ( F/E B/E) machine.
Tried to run mythtv-setup, the screen blinked and I was presented with the "do you want to run mythfilldatabase" dialog.
Does anyone have an idea what the problem could be?

---

### Post by NautiusMaximus on 2010-08-14
I also couldn't start my frontend after upgrading to 10.04.

I solved the problem by enabling auto-builds. I can't promise that will work for you, but I guess it's worth a try.

---

### Post by meanmrmustard on 2010-08-15
> **NautiusMaximus said:**
> I also couldn't start my frontend after upgrading to 10.04.

I solved the problem by enabling auto-builds. I can't promise that will work for you, but I guess it's worth a try.

 I just did a clean install of Lynx then added mythtv via apt-get (CLI) and it's doing the same thing.
Every install I've done in the past (from the Hardy version, I believe) has been flawless until Karmic.
I'm seriously disappointed.

---

### Post by Spr0k3t on 2010-08-16
Try removing pulseaudio.  Also check the mythtv log files to give you hints of what might be causing the issue.

---

### Post by NautiusMaximus on 2010-08-18
Does that way of doing it enable auto-builds? I found they were not enabled by default after the upgrade, so they may not be by your method either.

---

