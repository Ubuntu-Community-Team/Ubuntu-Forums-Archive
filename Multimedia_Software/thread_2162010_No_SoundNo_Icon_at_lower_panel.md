---
title: "No Sound/No Icon at lower panel"
date: 2013-07-12
forum: Multimedia Software
---

### Post by ssulaco on 2013-07-12
Acer Aspire one Netbook,No sound....New install of Lubuntu 13.04

I run ```
alsamixer
```see alsamixer1
and I select the HDA ATI,see alsamixer2 and 3
but when I close and reopen the terminal alsamixer reverts back to alsamixer1

and when I click on Add/Remove panel Items "volume control" shows it should be sitting on the panel but is not.
.....Thanks in Advance

---

### Post by ajgreeny on 2013-07-12
Your HDA ATI is muted according to the third pic.  Use "M" key to unmute then ESC to save those settings to see if that helps.

---

### Post by ssulaco on 2013-07-12
> **ajgreeny said:**
> Your HDA ATI is muted according to the third pic.

Which one is muted?They appear to be all unmuted "OO"

---

### Post by ssulaco on 2013-07-12
Ive also tried this procedure and editing alsa.conf.......no luck
[http://ubuntuforums.org/showthread.php?t=2051697](http://ubuntuforums.org/showthread.php?t=2051697)

---

### Post by ajgreeny on 2013-07-13
> **ssulaco said:**
> Which one is muted?They appear to be all unmuted "OO"

The two "MM" showing above the device in your third screenshot mean it is muted.  With that showing in alsamixer hit "M" key and it should then show "00" instead, meaning unmuted.

---

### Post by ssulaco on 2013-07-13
Thanks...ajgreeny,my apologies.....Some how i couldn't see the tree for the Forest,(looking at wrong pic),Its unmuted,and alsa.conf is set back to card 0,still no go on sound after reboot,I know sound card/speakers are good,...dual-booting Windows works fine....

---

### Post by ajgreeny on 2013-07-13
In that case I think I am now as baffled as you are.

Sorry!

---

### Post by Yellow Pasque on 2013-07-13
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by ssulaco on 2013-07-13
> **ajgreeny said:**
> In that case I think I am now as baffled as you are.
Sorry!
Thanks ajgreeny,I appreciate your help,....Im running Lubuntu on an old Optiplex GX280 and 2 year old Asus Eeepc,both work flawlessly.

> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Temüjin....That was pretty cool,didnt know that existed....Here is the link to my script,
[http://www.alsa-project.org/db/?f=1e5a612fbda5995dea56a13c2eb33e8461a48be9](http://www.alsa-project.org/db/?f=1e5a612fbda5995dea56a13c2eb33e8461a48be9)

---

### Post by JimS on 2013-07-13
I see I'm not the only one
who has issue with no sound.
My pc in a new HP2000 laptop.
I've loaded several distros
and only Lubuntu has had no sound.
LinuxMint 15, Sabayon, Manjaro, and Ubuntu 12.10
all had NO troubles with sound.
I'm liking LM15xfce the best.

---

### Post by Yellow Pasque on 2013-07-13
It's probably tripping up on getting the right card (i.e. it's trying to use the HDMI audio).

You'll probably want to install pulseaudio (especially if you want multiple programs to use the sound at once), but alternatively you could try something like: [http://alsa.opensrc.org/FAQ026](http://alsa.opensrc.org/FAQ026)

---

### Post by ssulaco on 2013-07-14
> **Temüjin said:**
> It's probably tripping up on getting the right card (i.e. it's trying to use the HDMI audio).
You'll probably want to install pulseaudio (especially if you want multiple programs to use the sound at once), but alternatively you could try something like: [http://alsa.opensrc.org/FAQ026](http://alsa.opensrc.org/FAQ026)
Installed pulseaudio via synaptic.....:D I now have volume control......Thank you Temüjin
> **ajgreeny said:**
> The two "MM" showing above the device in your third screenshot mean it is muted.  With that showing in alsamixer hit "M" key and it should then show "00" instead, meaning unmuted.
ajgreeny....Thanks again for the headsup on the muted device.

NOTE:You guys wouldnt know off the top of your head why the "Fn" volume keys dont work,using the Fn+display brightness keys do work,Yes I can adjust volume with pointer.

---

