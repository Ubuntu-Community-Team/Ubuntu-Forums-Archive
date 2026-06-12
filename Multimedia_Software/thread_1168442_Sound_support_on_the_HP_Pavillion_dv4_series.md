---
title: "Sound support on the HP Pavillion dv4 series"
date: 2009-05-24
forum: Multimedia Software
---

### Post by maxislinux on 2009-05-24
I just istalled Ubuntu 9.04 on the Pavillion dv4 laptop. The sound at first doesnt seem to work. But then, i changed the drivers to ALSA. The login screen now has an endless flourish of drum-beats. :(

---

### Post by cazo on 2009-08-28
Open */etc/modprobe.d/alsa-base.conf* and add the following lines at the end of the file:

[FONT="Courier New"]alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1[/FONT]

Reboot and everything should work again (or just reload the snd-hda-intel with the new parameters).

I hope that helps,
Claudio

---

### Post by crgutierrez on 2009-08-28
Gracias!!!!! It works!!

HP Pavillion dv4 - 1435 dx with freshly installed Jaunty 64amd

---

### Post by cusinmex on 2010-03-14
thank you so much!!!

ive been looking for this everywhere :P

---

### Post by DTCantwell on 2010-03-16
I am new ubuntu, linux for that matter. This did not work for me. All that happens is that the speaker light on the computer will come on now but I still don't get any sound. What should I do?

Oh yeah. I have a HP Pavilion dv4-2045dx

---

### Post by Eliot89 on 2010-09-28
I'm having the same problem as DTCantwell and I have the same computer. I'm using the Lucid distribution. Ideas anyone?

---

### Post by lidex on 2010-09-30
> **Eliot89 said:**
> I'm having the same problem as DTCantwell and I have the same computer. I'm using the Lucid distribution. Ideas anyone?

Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

