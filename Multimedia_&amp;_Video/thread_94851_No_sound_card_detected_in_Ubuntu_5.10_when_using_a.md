---
title: "No sound card detected in Ubuntu 5.10 when using as a VMWare guest OS"
date: 2005-11-25
forum: Multimedia &amp; Video
---

### Post by Miro on 2005-11-25
(Sorry for double posting, I just realized that I posted the wrong forum first).

I have installed Ubuntu 5.10 as a guest OS to VMWare viewer (the host is WinXP), both from scratch and updating from the Browser Appliance -virtual machine. Everything else I have tried has worked ok but no matter what I do, I can't get any sounds from Ubuntu. At (Ubuntu) Preferences -> Sound I can see that Ubuntu thinks I have no sound card, the Default sound card -field is empty. I have tried to change sound.virtualDev="es1371" to sound.virtualdev = "sb16" in the .vmx-file with no help. When I run a WinXP-guest with the same viewer sounds work as they should. Can anyone help?

I think here are specifications for the system that VMWare Viewer emulates:
[http://www.vmware.com/support/ws4/doc/intro_vmspec_ws.html](http://www.vmware.com/support/ws4/doc/intro_vmspec_ws.html)

---

