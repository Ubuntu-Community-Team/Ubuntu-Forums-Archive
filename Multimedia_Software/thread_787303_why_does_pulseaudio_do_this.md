---
title: "why does pulseaudio do this?"
date: 2008-05-08
forum: Multimedia Software
---

### Post by MemoryDump on 2008-05-08
after the system is up and running I lose my sound.. and when I check on my Pulse Manager I get what you see on the attachment. Connection refused? what? why does this happen? the only way I fix it is by rebooting. it's VERY annoying... really not liking pulse :(

-MD

---

### Post by MemoryDump on 2008-05-09
hello? nobody else has experienced this? :(

---

### Post by wkulecz on 2008-05-09
I've had plenty of weird audio issues that mostly automagically fix themselves or not :(

Where did you fine Pulse Manager tool?

--wally.

---

### Post by Zorael on 2008-05-09
Does it work if you restart the pulseaudio daemon? Just enter [FONT="Courier New"]**pulseaudio -D**[/FONT] in a run box (Alt+F2).

> **wkulecz said:**
> Where did you fine Pulse Manager tool?

--wally.

Install the [FONT="Courier New"]**paman**[/FONT] package. You may also want to grab [FONT="Courier New"]**pavucontrol**[/FONT], [FONT="Courier New"]**pavumeter**[/FONT], [FONT="Courier New"]**paprefs**[/FONT], and [FONT="Courier New"]**padevchooser**[/FONT]. Likely you already have some of them.

---

### Post by MemoryDump on 2008-05-09
> **Zorael said:**
> Does it work if you restart the pulseaudio daemon? Just enter [FONT="Courier New"]**pulseaudio -D**[/FONT] in a run box (Alt+F2).
I'm assuming it would since when I reboot it comes back to life.. actually.. now that I think of it I just have to restart my session (ctr-alt-backspace) and normally my sound returns.

it seems OK now.. since I disabled my second audio device.. but I need this other device for my headset for ventrilo and other voice chat.

---

