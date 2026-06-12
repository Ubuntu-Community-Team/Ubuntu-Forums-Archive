---
title: "Ubuntu is running in low graphics mode, but only when monitor is turned off at boot"
date: 2009-03-21
forum: Multimedia Software
---

### Post by swalke66 on 2009-03-21
I have a mythbuntu 8.10 installed on a Shuttle system with Intel G33 chipset.  I've got the HDMI output from the Shuttle connected to a Sharp LCD TV.  For the most part everything works well, except:

If I boot the computer without the television turned on I get the
Ubuntu is running in low graphics mode popup with the error 'no modes found'

If I boot the computer with the television turned on I don't get this problem.

Does this mean Xorg is reconfiguring everytime I boot?  Can anyone help resolve this?

I'd like to be able to netboot my machine so that I can record, which will never happen if I keep getting this error. (this machine is both my mythtv backend and frontend)

---

### Post by amadeus266 on 2009-03-21
This sounds like Ubuntu is trying to identify your monitor on every boot. I have this problem when I use my KVM switch. The only way I know how to avoid this is to have the monitor turned on. Since I rarely turn this computer off, I haven't needed to find a workaround. Maybe someone else can give more information.

---

### Post by swalke66 on 2009-03-22
Is it possible to force a certain mode in my xorg.conf file?
Does anyone know how to do that?

---

