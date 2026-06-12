---
title: "ATI Radeon 9600 Customization Idea"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by t.z0n3 on 2008-01-06
My computer pukes with the restricted drivers. I had to end up reloading over the / directory to fix my graphics problems. Anyway, my computer can (and HAS) run at 1280x1024, but it keeps defaulting. I wanted to know if this would work:

It defaults at 1024x768, and sometimes (for no explained reason) goes to a widescreen format (which my computer isn't). What if I were to go into xorg.conf and delete all the resolutions except 1280x1024? Theoretically, my computer COULDN'T run anything else at that point, because there simply WOULDN'T be anything else to run. Since I know it can do it, would this be recommended? If it doesn't work, I can always go back into the terminals (F1-F6) and undo it via text commands.

---

### Post by archivator on 2008-01-06
It would work, should you not mess up your xorg.conf.
Before doing that, however, I recommend backing up your xorg.conf and first trying the Screen & Graphics Properties (or whatever that new tool is called). Chances are, it won't help much but no (serious) damage can come from trying.

---

### Post by erfahren on 2008-01-06
just make a backup of xorg.conf before editing it. If it doesn't work you can replace it with the command line.

---

### Post by t.z0n3 on 2008-01-09
It hasn't worked. The xorg.conf simply gets reset as a backup file when I reboot or tell it to update the file. *sigh* Okay, nevermind. I thought I had a brilliant solution, but I just got blasted. DX

---

