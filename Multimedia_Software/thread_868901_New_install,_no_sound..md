---
title: "New install, no sound."
date: 2008-07-24
forum: Multimedia Software
---

### Post by WhiteStorm on 2008-07-24
I just installed ubuntu on a dell pc which had xp home on it (as in replaced xp)... most things seemed to work fine and I did hear the sound that comes up for the log in screen, however there was nothing after that. No sound will play in any programs logged in, nor do any sound tests with any of the settings work.

I tried using the sound fixes in the sticky thread, and I know that the computer IS detecting the sound cards (which it says there are two, one by SoundBlaster and one by Intel). When I go to alsamixer however, no settings there make any difference. I don't know how I did it but I also switched from the SB card to the Intel one and tried alsamixer on both to no effect.

I looked at the permissions thing (don't remember command) but both "pulse" and this account have access to "audio".

Weird thing is, I restarted the computer to see if that helped, and now there's no sound at the log in screen either.

If it matters, I did let the updater run and download/install/reboot before I noticed any of this.

---

### Post by WhiteStorm on 2008-07-24
Oh, I should also mention that I checked all the cables, volume controls, etc. on the speakers (and all the other volume controls I could find) and those were fine.

---

### Post by kamirata on 2008-07-24
I'm having the same issue also. Able to view clips from youtube but no sound at all.

Any help?

---

### Post by XxsydenxX on 2008-07-24
Yes actually i may have a solution, really what you need to do is update..i believe you should either  use the terminal or the update update manager. In the terminal type "sudo apt-get update" without the quotations.

---

### Post by PCessna on 2008-07-24
> **XxsydenxX said:**
> Yes actually i may have a solution, really what you need to do is update..i believe you should either  use the terminal or the update update manager. In the terminal type "sudo apt-get update" without the quotations.

Updating works best, but after if you still have troubles,  One thing I also noticed, is going into sound settings and carefully messing with the sound options available may help, Even if you did, and all goes wrong, try a bit more

Edit: That's how I got mine to work =]

---

### Post by XxsydenxX on 2008-07-24
i also should mention if updating doesn't work or the soun d settings then try changeing the settings in alsa

---

### Post by WhiteStorm on 2008-07-24
Alsa as in the mixer? I tried that to no effect. Also, I tried to update again, but it hasn't improved anything (and probably only found it was already up-to-date anyway).

I also tried [>this<](http://ubuntuforums.org/showthread.php?t=868728) but I don't know how to access /etc/modprobe.d/alsa-base (I tried putting it into the terminal but it said permission denied).

---

### Post by xc3RnbFO8P on 2008-07-24
Do:
> gedit /etc/modprobe.d/alsa-base
if you want to change something:
> sudo gedit /etc/modprobe.d/alsa-base

---

### Post by WhiteStorm on 2008-07-24
Hmm... okay. That has no effect either.

---

### Post by WhiteStorm on 2008-07-24
I checked the cords and plugs once more, and tried running ubuntu from the live CD, still with no sound.

When I turn the speakers all the way up (which would normally damage my hearing if I so much as received an email) and use the sound test there is a very faint clicking noise.

---

### Post by WhiteStorm on 2008-07-25
I'm not sure if this means anything but today I have decided to go through the stickied thread again;

When I used the command "lspci -v" I noticed that when the cards were listed it says "access denied".

> 02:01.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
	Subsystem: Creative Labs Unknown device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at df20 [size=32]
	Capabilities: <access denied>

02:01.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
	Subsystem: Creative Labs Unknown device 1003
	Flags: bus master, medium devsel, latency 64
	I/O ports at df10 [size=8]
	Capabilities: <access denied>


What confuses me is that it says this also about my video card, which so far has worked unlike sound. Also, in the /etc/group thing...
> audio:**x:29:root,pulse,username


So what it means by access denied I've no clue.

---

### Post by gborges911 on 2008-07-25
I had a similar problem in Debian, and I solved it disabling the system sounds at System->Preferences->Sound, and after a reboot I got sound for playing music and stuff like that, but I had to sacrifice the system sounds! I guess this is a GNOME issue, I'm not sure!... I hope It woks for you or at least give you a lead to the solution!... good luck!...

---

### Post by WhiteStorm on 2008-07-25
Thanks but it doesn't work.

I may just put xp back on here eventually, it seems like all the fixes have no effect on this.

---

