---
title: "[SOLVED] new graphics card fails to load x server"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by sagarhshah on 2008-02-15
Hi,

I recently bought an NVIDIA 7800 GS AGP graphics card and installed it on my desktop system.
Until then I used to use the onboard UniChrome graphics on the motherboard.

Now when I boot I get this message.

```
Failed To load the X server (your graphical interface). 
It is likely that it is not set up correctly. 
Would you like to display the X Server output to diagnose the problem?
```

and  I clicked  [yes] to that it shows me a bunch of stuff I don't understand,I check [ok] and it asks me if I want to have an even more detailed description of the problem. After viewing it,, i click [ok] again and it continues onto the command line login.

As far as I understand I have to edit the xorg.conf file to use the new graphics card, but I don't know what edit I have to make.
I remember reading a thread a few months ago where someone was in the same situation as me but I can't find it anymore.

Could anyone help me out with this please?

Any help would be appreciated

Thanks
Sagar

---

### Post by PmDematagoda on 2008-02-15
Boot Ubuntu in Recovery Mode and then execute:-
```
dpkg-reconfigure -phigh xserver-xorg
```

After that is done reboot Ubuntu using:-
```
reboot
```

That should allow you to use the "nv" driver and the X-Server should work again after which you can start installing the Nvidia driver.

---

### Post by sagarhshah on 2008-02-15
Thanks you very much PmDematagoda

It worked like a charm.
Now I can enjoy linux in full graphics glory :D

marking it as solved for others who might find this useful

Sagar

---

### Post by PmDematagoda on 2008-02-15
You can install the Nvidia driver by going to System>Administration>Restricted Drivers Manager.

Just thought you might want to know:).

---

