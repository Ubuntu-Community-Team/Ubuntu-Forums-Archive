---
title: "No sound"
date: 2008-05-10
forum: Multimedia Software
---

### Post by user-unit on 2008-05-10
this latest bug I'm getting is that I have no sound. I was using 7.10 because I was having issues that where new with 8.04, I was plugging along doing my thing and then I decided to upgrade from 7.10. so I did, and I had no sound. I tried a fresh install of 8.04 from CD and still have no sound. What happened? everything appears to be running normally, it detects my sound card and what kind it is so where does it fail to give me sound?

---

### Post by presston on 2008-05-10
what is your soundcard?

---

### Post by user-unit on 2008-05-10
it is a sound blaster live 5.1

used lspci -v in the terminal and this comes up

01:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
	Subsystem: Creative Labs Gameport Joystick
	Flags: bus master, medium devsel, latency 32
	I/O ports at a800 [size=8]
	Capabilities: <access denied>

---

### Post by boomtisk on 2008-05-10
That is mighty strange, I have the exact same card and never had any problems with it in any version of Ubuntu I installed. Are you sure it's not simply muted in your audio mixer?

Also, have you tried putting your card into a different PCI slot? As weird as it sounds, it sometimes helps.

---

### Post by user-unit on 2008-05-10
i feel so stupid.... the mute button on my speakers was pressed.

---

