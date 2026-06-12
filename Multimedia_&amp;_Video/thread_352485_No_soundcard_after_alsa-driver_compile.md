---
title: "No soundcard after alsa-driver compile"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by Garyu on 2007-02-03
I was having some problems with sound. Actually, listening worked great with 5.1 surround sound, but the mic was not working.

So what I did was that I followed the "Comprehensive sound solutions" sticky thread and compiled the 1.0.13 version of alsa-driver, alsa-lib and alsa-utils. After that nothing changed. So I rebooted my computer. Now nothing works. It says I don't have a soundcard. 

aplay -l gives me "no soundcard found", but of course lspci will show it. I tried "sudo modprobe snd-intel8x0" with no errors but still no difference... So I thought I would try to reinstall alsa from repositories:

sudo aptitude reinstall alsa alsa-base alsa-utils 

Still, no difference, even after a reboot. So... Anyone who can tell me how to restore my system? I will gladly accept that the mic isn't working if I can just get back my 5.1 surround sound...

EDIT:
Right, my soundcard is onboard nForce... I think it's nForce4... if that would matter.

---

### Post by Garyu on 2007-02-04
OK, so you can forget this. I tried lots of different ways of getting sound back, but each new method I tried reduced the functionality of my system even more. Finally it wouldn't even boot. Even though I never meddled with anything else than alsa-related stuff.

Anyways, now I did a complete reinstall of Ubuntu. So now everything is back to normal. But my microphone still won't work. Oh well...

---

### Post by darkeale on 2007-02-23
id like a solution if anyone has one. i also followed that howto and no have no soundcard found. i did it because of the old only have sound in one app. problem so if anyone has any ideas on that too they would be most appreciated

---

### Post by darkeale on 2007-02-23
just tried lspci -v and the sound device shows up. any ideas?

---

### Post by darkeale on 2007-02-23
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 40)
        Subsystem: C-Media Electronics Inc: Unknown device 0301
        Flags: medium devsel, IRQ 5
        I/O ports at e000 [size=256]
        Capabilities: <available only to root>

this is my soundcard in lspci -v

ithink the problem is where i configured using this line -

sudo ./configure --with-cards=hda-intel

what would i change hda-intel to to correctly configure my soundcard?

---

### Post by darkeale on 2007-02-23
fixed. run the configure line with hw instead of hda-intel. then make and make install again

---

