---
title: "BENQ FP231W LCD Monitor will not operate in highest resolution mode"
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by kimwong on 2006-10-15
Since switching to Ubuntu, I have not been able to run my monitor (BENQ FP231W) in its highest native resolution of 1920x1200.  The options given  from the menu "System Setting"->"Display" do not go above 1600x1200.

The xorg.conf file lists a max resolution of 1920x1080, which is not quite correct for this monitor, however, I cannot switch into that mode either.

Monitor:
BENQ FP231W

Video Card:
ATI Radeon X1900GT 256MB PCI-E

Graphics Driver:
VESA

I have tried running sudo dpkg-reconfigure xserver-xorg and selecting the 1920x1200 option, however, the generated xorg.conf file does not seem to work.  Any help would be appreciated.  Thanks

---

