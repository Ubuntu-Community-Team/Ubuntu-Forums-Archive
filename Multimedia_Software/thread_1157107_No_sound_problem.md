---
title: "No sound problem"
date: 2009-05-12
forum: Multimedia Software
---

### Post by itsmathias on 2009-05-12
I have no sound when I'm using ubuntu and I tried things that I found on google but it didn't work

I'm new at this so I'll need explanations.

When I type:
[SIZE=2]aplay -l

[/SIZE]
Into a shell it says

card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

What am I supose to do with this?

---

### Post by caracuri on 2009-05-12
i have the same problem, i think that you have tried this [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578).
for me in PulseAudio Volume Control's Playback tab:
# The application does not play audio and does list an entry in the Playback tab;
- the application is using PulseAudio but there is a problem, such as: a bug in PulseAudio, a problem with your ALSA kernel module or libraries, or your PCM/Master volume is muted.

---

### Post by itsmathias on 2009-05-12
Where do I use the first code? -_- lol
I'm new to this...

it doesn't work in Terminal

---

### Post by caracuri on 2009-05-12
try to remove pulseaudio and use alsa

---

### Post by itsmathias on 2009-05-12
> **caracuri said:**
> try to remove pulseaudio and use alsa
didn't work

---

### Post by prol on 2009-05-12
I have the same prblm,no sound at all happened after an update and reboot

---

### Post by cjsteele on 2009-05-12
welcome to the growing list of poor bastards with Intel HDA chipsets that are presently screwed because the kernel in 9.04 frags the support for the Intel HDA chipset.  You can:
** upgrade to Karmic testing, or
** back-rev to an 8.04 kernel that works, or
** wait patiently for developers to fix the issue, or
** dig in and fix the problem yourself.

I opted for upgrading to Karmic

---

### Post by itsmathias on 2009-05-12
> **cjsteele said:**
> welcome to the growing list of poor bastards with Intel HDA chipsets that are presently screwed because the kernel in 9.04 frags the support for the Intel HDA chipset.  You can:
** upgrade to Karmic testing, or
** back-rev to an 8.04 kernel that works, or
** wait patiently for developers to fix the issue, or
** dig in and fix the problem yourself.

I opted for upgrading to Karmic

What is karmic? because I know I won't be able to fix it by myself :P

---

### Post by itsmathias on 2009-05-13
and BTW I can hear sound when I test it in the sound preferences

---

### Post by caracuri on 2009-05-13
> **cjsteele said:**
> welcome to the growing list of poor bastards with Intel HDA chipsets that are presently screwed because the kernel in 9.04 frags the support for the Intel HDA chipset.  You can:
** upgrade to Karmic testing, or
** back-rev to an 8.04 kernel that works, or
** wait patiently for developers to fix the issue, or
** dig in and fix the problem yourself.

I opted for upgrading to Karmic

where do you have founded this news?

---

### Post by itsmathias on 2009-05-13
> **caracuri said:**
> where do you have founded this news?

Well I sure would like to know that too.

---

### Post by cjsteele on 2009-05-13
consider yourself added to the long (now very long) list of disgruntled users of the Intel HDA chipset.  Its a kernel bug.  We have to wait for it to be fixed, or roll our own.

---

### Post by cjsteele on 2009-05-13
karmic == the next version of ubuntu

---

### Post by cjsteele on 2009-05-13
> **itsmathias said:**
> and BTW I can hear sound when I test it in the sound preferences

Oh, then this is a different problem altogether.

---

### Post by psyke83 on 2009-05-13
> **cjsteele said:**
> consider yourself added to the long (now very long) list of disgruntled users of the Intel HDA chipset.  Its a kernel bug.  We have to wait for it to be fixed, or roll our own.

Not quite. Enable the "proposed" repository and upgrade to kernel 2.6.28-12-generic.

See: [https://lists.ubuntu.com/archives/jaunty-changes/2009-May/009771.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-May/009771.html)

---

### Post by caracuri on 2009-05-14
> **psyke83 said:**
> Not quite. Enable the "proposed" repository and upgrade to kernel 2.6.28-12-generic.

See: [https://lists.ubuntu.com/archives/jaunty-changes/2009-May/009771.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-May/009771.html)

also this kernel gives me problem.

---

### Post by cjsteele on 2009-05-14
I see nothing there that indicates that version fixed it... only indication is they disabled beep.

---

### Post by cjsteele on 2009-05-14
in order... 
** I updated to Karmic and it worked, briefly, but with garbled sound (this was more than I got in 9.04)
** I back-rev'd to 2.6.28-11 and it is working fabulously
** the natural path for things to be fixed
** the geek path for things to be fixed.

---

### Post by itsmathias on 2009-05-14
> **cjsteele said:**
> in order... 
** I updated to Karmic and it worked, briefly, but with garbled sound (this was more than I got in 9.04)
** I back-rev'd to 2.6.28-11 and it is working fabulously
** the natural path for things to be fixed
** the geek path for things to be fixed.

I have no idea how to do this, I'll try to search for infos and I'll give news

---

