---
title: "1080p and ATI chipset"
date: 2007-11-26
forum: Mythbuntu
---

### Post by kameleon25 on 2007-11-26
I am trying to figure out why my setup won't play any 1080p recorded media. My systems specs are:
GIGABYTE GA-MA69GM-S2H
AMD Athlon 64 X2 4600+ 65W AM2 2.4Ghz
1GB  DDR2 800
160GB SATA HD
dvd+/-rw drive
Running Mythbuntu 7.10 with a Streamzap PC remote
Output via HDMI to a Sharp Aquos 42" LCD panel

When I built the system I did alot of research and read that the Radeon Xpress 1250 video chipset on the gigabyte motherboard would support full 1080p. The lcd tv shows that it is receiving the 1080p signal but the pc will not play 1080p content. It plays 720p fine though. I did have some audio sync issues before i installed mythbuntu 7.10 on the 720p stuff though. I have all the codecs needed as far as I can tell. What could I be missing?

---

### Post by kameleon25 on 2007-11-27
After testing a few things on my laptop I have concluded that xine does not do to well for 1080p playback. On my laptop running ubuntu 7.10 I can play the 1080p file I have for about 20 seconds before it errors out about gnome screen saver or something. I can play it in mplayer the best (albeit with no sound) but vlc just errors out without playing. My laptop is running a celeron 530 (1.73Ghz) w/ 1gb ram (128 dedicated to video) and an intel video chipset. So I figure that my AMD 64 X2 4600+ cpu in my mediapc should be able to play this file no problem. I will mess with the player settings and report back what I turn up.

---

### Post by superm1 on 2007-11-27
There is a new version of mplayer in gutsy-backports.  You may consider trying that as it should have improved performance for high def stuff.

---

### Post by kameleon25 on 2007-11-27
That is definatley an option. Now how would I go about installing that version over the current one?

---

### Post by superm1 on 2007-11-27
> **kameleon25 said:**
> That is definatley an option. Now how would I go about installing that version over the current one?
Go applications->system->software sources and enable the backports repository.

When it asks to reload the package lists, let it.  Update manager should have a little orange thing in your task bar now about it.  If not, then open up synaptic and search for it and mark it to be installed.

---

