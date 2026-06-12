---
title: "i810 (945gm), dri, google earth on dapper: works"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by bigblondbear on 2006-09-06
Just thought I share my findings with the community :-)

After having ](*,) for a while trying to get dual head & direct rendering to work on a Dell D820 with a 945GM chipset (GMA950), I finally found the right combination of things.

All it requires is to use the following .debs from the compiz ([http://xgl.compiz.info](http://xgl.compiz.info)) repository:

xserver-xorg-driver-i810_1%3a1.5.0.1-0ubuntu2_i386.deb
libgl1-mesa_6.5.1+cvs20060824_i386.deb
libgl1-mesa-dri_6.5.1+cvs20060824_i386.deb
libglu1-mesa_6.5.1+cvs20060824_i386.deb
mesa-utils_6.5.1+cvs20060824_i386.deb

These can be installed "on top of" the existing .debs but require the following order (hope I recall it OK :-)):

dpkg -i xserver-xorg-driver-i810_1%3a1.5.0.1-0ubuntu2_i386.deb
dpkg -i libgl1-mesa-dri_6.5.1+cvs20060824_i386.deb
dpkg -i libgl1-mesa_6.5.1+cvs20060824_i386.deb
dpkg -i libglu1-mesa_6.5.1+cvs20060824_i386.deb
dpkg -i mesa-utils_6.5.1+cvs20060824_i386.deb

Hopefully these debs will make it into the main dapper repository one day...

---

### Post by ediot34 on 2006-09-11
Whoa,

Are you using Xinerama to get the dual screen working?  I assume so since this is the only way I know of to get dual-head working with the i810 driver.
Xinerama disables DRI though doesn't it?

Could you post your xorg.conf?

Do you have compiz/AIGLX working with the dual screens?

I've been trying to get this to work for ages now...

---

