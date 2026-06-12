---
title: "Bluetooth Stereo Headset: Connection yes, output no"
date: 2012-08-14
forum: Multimedia Software
---

### Post by bennypr0fane on 2012-08-14
Hello,
I hope I'm in the right subforum for this (if not, please advise me where to).
I have a Nokia BH-505 bluetooth stereo headset that works fine with my phone, it connects with AVRCP.
It is detected by my Laptop and I can make a connection, and bluetooth manager also shows data being sent back and forth, but sound keeps coming out of the laptop's loudspeakers only, the headset remains silent.
On the same machine, this behavior is the same under Win7.
How could I diagnose it?

EDIT: I also tried asking at Nokia forums, they're sort of broken and my post is not coming through

---

### Post by kostkon on 2012-08-14
After connecting it, did you open your sound preferences to set your headset as the current output device?

---

### Post by bennypr0fane on 2012-08-15
> **kostkon said:**
> After connecting it, did you open your sound preferences to set your headset as the current output device?

I have no entry for regulating audio in the settings menu.
I found out blueman wanted to connect to Pulse Audio which I didn't have installed (only Alsamixer). I installed it now along with pavucontrol and got a menu entry for it under Multimedia, but with the headset connected, pavucontrol doesn't list it in output devices, so I can't change that setting (there's only "dummy output"?) 
Also, blueman still crashes with the same error msg about not being able to connect to pulse audio daemon.

---

