---
title: "Terrarec Phase 26 USB"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by skarp on 2007-11-04
Hello!

I've checked with ALSA that there is no support for my external soundcard (Terratec Phase 26 USB) today. Anyone having this card who knows if it's comming?:confused:

---

### Post by matsverige on 2007-11-08
Hello!

I installed Ubuntu on my pc a few days ago and I'm also using a Terratec Phase 26 usb. Any news about drivers or any kind of support?

Please, help us if you can!

---

### Post by neocoretech on 2008-02-19
I have also problems with my phase 26...

The strange thing is, that at the login screen i hear the ubuntu "drum",
and with jack the card is working fine...

But all "normal" audio applications like vlc and amarok does not output any sound...
When I want to test the sound in the ubuntu sound administrative panel,
after clicking the test button a short beep comes out, and then the window closes... :/

---

### Post by neocoretech on 2008-03-03
I found a workaround on the net...

if you switch the phase 26 to 16/48 mode,
and then set the device USB1648 as your default device
for alsa (with asoundconf on the commandline) it should work fine...

this seems to be a gutsy related problems, as in older
ubuntu versions the 24/48 mode worked fine...

---

