---
title: "ALSA vs two sound devices"
date: 2008-11-20
forum: Multimedia Software
---

### Post by Cirroz on 2008-11-20
Hi, all.
First, Sorry for my English.

Ubuntu 8.10
I have two sound devices. First is onboard soundcard, second is USB skype-phone.
When the phone is connected alsa always play through it.
I'm try to change default sound device many ways, but default is usb-phone.
I think alsa setting default device as first loaded module, because when I switch the phone off before load OS, my onboard card is default device. After Ubuntu started I can connect usb-phone and all works coorect.

When I check sound output in System->Preferences->Sound I hear sound from onboard card. But when I start any application it plays in usb-phone.

I tried to create /etc/asound.conf and ~/.asoundrc with manual from official alsa site and forums, tried to configure card with /usr/bin/asoundconf, but nothing works.

Help me, please, to find solution when I don't need to disconnect usb-phone before reboot.

---

### Post by psyke83 on 2008-11-20
The ~/.asoundrc and /etc/asound.conf files no longer apply for Intrepid, as PulseAudio is used by default.

Look here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Read the FAQ and Appendix B.

---

### Post by Cirroz on 2008-11-21
Thanks a lot!

---

