---
title: "[SOLVED] Changing monitor and video adapter"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by LtPitt on 2008-03-13
Hello there!

I have an nvidia FX 5200 (yuuuck!) and a crappy 17 crt monitor...
I've installed mythbuntu and now I'm outta buying a samsung 2032mw and a 7600gt...
Do you think I'll have problem with Linux?
Should I do something special to let my new hardware work without destroying my installation?

My newbie plan was:

Turn the pc off
Plug in all the new hardware
Run envy
Uninstall nvidia
Reinstall nvidia

Done that...
Will I be happy?
What about my new monitor resolution?
Should I change something in xorg.conf?
Maybe auto configuring it again?

Thank you all!

---

### Post by rklauco on 2008-03-13
No reinstallation necessary.
Simply turn off the PC, reinstall the HW and start it back.
If it does not work (it probably will), than boot to recovery mode, insert the sudo password and in console run the command
```
dpkg-reconfigure xserver-xorg
```
and set the correct parameters (probably the refresh rate and resolution for LCD screen will be a problem).
Than, when the values are saved, just hit the CTRL+D key tocontinue and you should start with your usual login/gnome desktop.

---

