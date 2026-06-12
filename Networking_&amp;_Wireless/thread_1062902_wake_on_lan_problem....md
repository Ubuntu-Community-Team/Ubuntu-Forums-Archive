---
title: "wake on lan problem..."
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by Til_Valhall_vi_drar! on 2009-02-07
hi, i have enabled wake on lan in the bios, and when i shutdown from windows, its working fine, but with ubuntu its not working, i have tried this:

sudo ethtool -s eth0 wol g && halt -i

i can se on the switch that the light is on, i mean the light on the port that is connected to the computer, so it is listening when its off, but it just won't respond to magic packets

i have tried waking it up with wakeonlan 00:1f:c6:73:63:02 and i have tried with netcat: perl -e 'printf "\xff" x 6 . "\x00\x1f\xc6\x73\x63\x02" x 16' | nc -u -b 255.255.255.255 9

anyone have any ideas?

---

### Post by Til_Valhall_vi_drar! on 2009-02-07
bump

---

### Post by Til_Valhall_vi_drar! on 2009-02-07
do you belive in god?

---

### Post by Til_Valhall_vi_drar! on 2009-02-07
bump

---

### Post by BuntuFreak on 2009-02-08
> **Til_Valhall_vi_drar! said:**
> bump

Stop bumping and humping. And don't bring god into it

:D

Okay, now let me understand what you are saying because it might be the same as my problem.

You want your Ubuntu machine to go on standby. And when someone wishes to make a "connection" to it, i.e. access a folder on the hard drive you have shared over the network, you want it to come off standby.

Is this correct? I hope so, because that's my problem. I'm using my old Dell Computer computer with Ubuntu as a file server. And I have regular Ubuntu desktop OS on it, not Ubuntu server, which has higher hardware requirements. Now that by itself could be my problem.

Could you state your problem a little more clearly. Then maybe I can help. Or we can help each other. Or maybe someone else will feel like helping the both of us.

God? Whether anyone believes in HIM or HER, I'm sure God has better things to do than solve Wake-Up-On-Lan issues with Ubuntu.

Best.

---

### Post by Til_Valhall_vi_drar! on 2009-02-10
Thanks for replying, and im sorry about the god question.

it is a ubuntu 8.10 64bit desktop system, not server. (i have another computer with server edition on, but the hardware is to bad to suppord wakeonlan)

i have surround sound hardware and what i was doing before with windowns is that i put a job into my servers crontab so it will wake my computer up everymorning, and play some music so i have atleast some hope off getting up in the morning. the weird thing is that i have installed ubuntu on my old computer that i had winxp and wol was working great, but not with ubuntu. so i don't think its something the hardware. how can i describe my problem better?

---

