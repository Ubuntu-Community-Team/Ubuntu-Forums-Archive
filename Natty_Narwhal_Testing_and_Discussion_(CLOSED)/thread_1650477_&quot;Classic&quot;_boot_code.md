---
title: "&quot;Classic&quot; boot code?"
date: 2010-12-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2010-12-21
Any way to specify "classic" panels when booting CD Live?  "Unity" and/or compiz broken on CD Live A1 on IBM Thinkpad T40 ati radeon mobility 7500 (yes there's a launchpad bug).

I can get CD live up by:
boot codes: single radeon.modeset=0
Select root prompt, do: nano /etc/X11/xorg.conf
Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSecton
Ctrl-o, Ctrl-x
sudo service gdm start

There's a bunch more to Natty to test than just Unity....

Sure would be nice to have a boot code specifying "classic".

Jerry

---

### Post by ronacc on 2010-12-21
I don't think thats in the boot code , its in the init scripts , you might be able to hack them and then remaster the cd , .

---

### Post by pferraro on 2010-12-22
> **jerrylamos said:**
> Any way to specify "classic" panels when booting CD Live?  "Unity" and/or compiz broken on CD Live A1 on IBM Thinkpad T40 ati radeon mobility 7500 (yes there's a launchpad bug).

I can get CD live up by:
boot codes: single radeon.modeset=0
Select root prompt, do: nano /etc/X11/xorg.conf
Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSecton
Ctrl-o, Ctrl-x
sudo service gdm start

There's a bunch more to Natty to test than just Unity....

Sure would be nice to have a boot code specifying "classic".

Jerry

gnome-classic is one of the xsessions found here:
/usr/share/xsession/
The xsession is selectable from the gdm, or an alternate default can be chosen via gdmsetup.

---

### Post by ronacc on 2010-12-22
he's testing live cd's not installing , if installed ou can just select at login and then that becomes the default until changed .

---

