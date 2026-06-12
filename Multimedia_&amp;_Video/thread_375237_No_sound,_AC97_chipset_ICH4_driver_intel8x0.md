---
title: "No sound, AC97 chipset ICH4 driver intel8x0"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by Aaronb2245 on 2007-03-03
Installed Dapper Drake yesterday on Gateway MX3562 using sound card Intel southbridge AC97 Audio Chipset ICH4 driver intel8x0.

I check the alsamixer and turned everything on except for the ext amplifier and tried various other settings. I also follow other instructions from the sticky in this thread on sound problems. Including trying this

[COLOR="Red"]# webbca01 figured out how to get AC'97 work with the help of the second last post here and this post. Basically, if you have an intel8x0 module, you can get AC'97 working by
Code:

sudo nano /etc/modprobe.d/alsa-base

and adding this as the last line:
Code:

"options snd-intel8x0 ac97_quirk=3"[/COLOR]

[COLOR="Black"][/COLOR]I also tried add to the /etc/modules file (at the end of the file) snd-intel8x0. Rebooted in hopes it would load the module but still no sound.

Perhaps I'm misunderstanding something in the Stick for sound problems, but I have gone over it time and time again, followed the steps and still have no sound. Perhaps I don't have the snd module setup or something to that degree? I really just don't know. <sigh>

If you believe you can help me resolve my problem please do so. As I would GREATLY appreciate it.

Thank you,

Aaron

---

### Post by Goat40 on 2007-04-25
I have essentially the exact same issue, I've tried all the suggestions (mute,additions to alsa-base check the bios(it's not in there anyway) etc...) nothing. The sound card shows up in modinfo, no errors in dmesg simply no sound. I also went through the suggestions regarding alsamixer both as a user and root.

Does this card simply not work ?

---

### Post by Goat40 on 2007-04-26
I've got it working now here's the details.
Ubuntu version Ubuntu 7.04
                - the Feisty Fawn
Toshiba Tecra TE2100
Sound Intel I820  driver snd_intel8x0
followed all the suggestions above to no avail, added the following kernel 
parameter on boot, pci=noacpi (in Grub) viola sound.

---

### Post by maafkoro on 2007-04-29
I have a gateway 3525 laptop with AC 97 audio card

How can I edit kernel commands in startup? specially which file?

Thanx.

---

