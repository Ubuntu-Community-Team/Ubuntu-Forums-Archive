---
title: "Correct XORG 'fglrx'-extension module with DPKG-RECONFIGURE??"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by perixx on 2008-02-03
Hi...

I'm not taking it anymore!! Every time I try to install an ATI driver (regardless of which version), the XORG extension modules seem not to be updated accordingly in: > /usr/lib/xorg/modules/extensions/libglx.so

Every time I'm running ```
sudo dpkg-reconfigure xserver-xorg
``` - I'll have to specify XORG's extension module; will choosing 'FGLRX' here implement a compatible xorg-extension for the respective installed driver version, or for the standard restricted driver 7.34?

perixx

---

### Post by perixx on 2008-02-03
If I'm not mistaken, > sudo dpkg-reconfigure -phigh xserver-xorg 
or
sudo dpkg-reconfigure xserver-xorg always revert to the standard restricted 'xorg-driver-fglrx' (7.34) or Vesa - so using this command for telling the X-server to use the 'latest' fglrx module won't work - is that correct? What WOULD work ?

perixx

---

### Post by perixx on 2008-02-04
somebody knows more..?

---

