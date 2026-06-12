---
title: "Mythbuntu 9.04 uses vesa instead intel driver"
date: 2009-03-30
forum: Mythbuntu
---

### Post by TheConsultant on 2009-03-30
Hi.

I have installed MB 9.04 Beta 1 and the xorg server is using the vesa driver instead of an intel driver, I have an Intel i865 graphics chipset, I think the "i810" driver fits to this chipset.

How can I advise the xorg server to use another driver?

Best regards

Martin

---

### Post by st0necol on 2009-04-02
Go in Terminal and type

sudo gedit /etc/X11/xorg.conf

See in Graphics Device Section 

If you find something like

Driver "vesa" 

Change it to 

Driver "intel"


With Xorg 7.4, they've kept only 'intel' for i8x and i9x chipsets.


If you do not find any Driver entries, try putting the whole line and then see.

---

