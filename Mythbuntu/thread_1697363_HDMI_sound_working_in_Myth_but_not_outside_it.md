---
title: "HDMI sound working in Myth but not outside it"
date: 2011-02-28
forum: Mythbuntu
---

### Post by jim.hitch on 2011-02-28
Hi

Using aplay -l I got the sound working on Mythbuntu 10.10 using ALSA: plughw:1,7. 

How do I repeat the success outside the mythtv system?

I have installed the alsa backports and when I F6 in alsamixer and choose the Nvidia card, all the channels say '00' (ie. not mute) but I'm unable to change the levels which are at zero.

I'd appreciate a hand in the right direction.

Thanks

Jim

---

### Post by dakota34 on 2011-03-01
you could try creating an /etc/asound.conf file with your audio devices in it. This worked for me for my GT430's hdmi port (card 1 and device 9 was correct for my case, sounds like you would need to change it to device 7)  eg :[PHP]pcm.!default {
type hw
card 1
device 9
}
[/PHP]

---

### Post by jim.hitch on 2011-03-03
dakota34

Bingo! Thanks so much, great solution.

Jim

---

