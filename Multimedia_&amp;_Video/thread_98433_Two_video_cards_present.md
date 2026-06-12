---
title: "Two video cards present"
date: 2005-12-03
forum: Multimedia &amp; Video
---

### Post by johnmd on 2005-12-03
I installed Ubuntu on a P III 500 and everything is working fine but a bit slow.
I have another computer , a P III 933 that is presently running XP. Both computers have 384 mb's of ram.
I tried to switch these around by changing the hard drives, modems and sound cards.
The problem I ran into was with the video card.
There is a Rage 128 in the Linux machine and the Windows is running on an on board card.
I put the Rage 128 in the Linux computer and tried it but that was a no no.
Ubuntu found both cards and shut down X server after much complaining.
I put things back as they were and Ubuntu booted just fine.
Today I thought I would try it without installing the Rage 128.
This time Ubuntu found the on board card but also went looking for the Rage 128.
I got a message saying ALSA card 0 and after that ALSA card 1.
At that point the system froze.
I tried to disable the on board card. There are two settings and I tried both but Ubuntu still tries to find that second card.
Is there any way short of reinstalling Ubuntu to pick one card or the other.
If I had a choice I would rather use the rage 128 but as long as the on board card worked I could use it.
Being an HP computer I don't expect that it is too good of a card but it works fine with Windows but not as good as the Rage 128.
Windows tells me that the on board card is a Intel 82815.

Thanks
John

---

### Post by teaker1s on 2005-12-03
hit escape at boot select recovery and then 
sudo dpkg-reconfigure xserver-xorg

then
sudo reboot

---

