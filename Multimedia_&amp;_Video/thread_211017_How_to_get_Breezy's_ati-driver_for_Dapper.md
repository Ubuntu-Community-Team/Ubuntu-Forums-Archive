---
title: "How to get Breezy's ati-driver for Dapper ?"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by zak- on 2006-07-07
I can't use Dapper's ati-driver since it only gives me a black screen in X. Fglrx-driver works fine otherwise, but causes the GPU-fan to run at full speed even in normal desktop use, which is unbearable (I've read other X800 owners having the same problem. This needs to be fixed by ati damn it..). 

It seems my only option is to use Breezy's ati-driver with wich I  had no problems. So my question is, how can I get them for Dapper? I already tried by reinstalling Breezy, checking ”lock version” for  xserver-xorg-driver-ati in synaptic and then doing the upgrade to Dapper. This didn't work since the ati-drivers were updated anyway in spite of being locked..

Any advice on getting Dapper's ati-driver or the fglrx-driver to work better are also welcome of course.

---

### Post by Ctrl+Alt+Del on 2006-07-07
running the breezy package in dapper will result in breakage, a better way would be installing this older version manually by using the binary from the ati page

---

### Post by zak- on 2006-07-09
> **Ctrl+Alt+Del said:**
> running the breezy package in dapper will result in breakage, a better way would be installing this older version manually by using the binary from the ati page

But as I understand, the drivers provided by ati are the "fglrx" ones? I've already tried older versions of them just the way you suggested, but they all had the same problem with the GPU-fan. What  I would like to install, is the driver Breezy uses by default; the one you use by having the string &#8221;ati&#8221; in the &#8221;Device&#8221; section of xorg.conf. If that is not possible, I would appreciate any help on how to resolve the black screen problem I'm having with Dapper's default ati-drivers.

---

### Post by tommohawk on 2006-07-09
make sure you have installed xorg-driver-ati in synaptic and then make sure that "ati" is the driver used in your xorg.conf file.

That will ensure that the "ati" driver is used and not "fglrx".

Alternatively, download the 8.23.7 or 8.24.8 drivers from the ati website and use them.  They are know to work better.

---

