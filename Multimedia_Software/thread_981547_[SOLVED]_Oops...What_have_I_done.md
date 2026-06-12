---
title: "[SOLVED] Oops...What have I done?"
date: 2008-11-13
forum: Multimedia Software
---

### Post by Samilong on 2008-11-13
And how can I fix it?

I upgraded to Ibex, and for several days had problems with my video card - A Geforce 4 MX 400.

I rebooted today. A little icon appeared on one of my panels informing me that I was now using the latest nvidia restricted drivers. "Whoopee doo!" I thought.

However, I still have no accelerated graphics (and I know I'll never have them with the current crop of drivers - possibly not even with this card). 

Now, though, the title bars have gone missing from every application. Whilst I quite like the look, it makes it impossible to move windows around, I can't install anything(the terminal window is blank, as is the password dialog in Add/Remove),  and I miss having the little cross in the corner to shut things down.

Anyone know how to get them back? :confused:

---

### Post by tuvw740 on 2008-11-13
I totally agree with your point.Tags:[Virtual Gold Zone](http://www.vgoldzone.com) [Dofus Kamas](http://www.vgoldzone.com/dofus-buy-cheap-gold-32.html) [Runescape Gold](http://www.vgoldzone.com/runescape-buy-cheap-gold-231.html)

---

### Post by squaregoldfish on 2008-11-14
I can't help you get your title bars back, but you can move the windows by holding down ALT and dragging them.

Steve.

---

### Post by finite9 on 2008-11-14
Hmm.  Are you sure about not being able to get accelerated graphics?  That is quite an old card you have, and the nVidia binary blob that you are referring to does have support for all GeForce cards.  It is only the Xorg nv driver that does not have 3D support.  Be aware that the driver that appeared in the repositories recently is NOT the latest and greatest driver...it has a lower revision number than the ones shipped with Intrepid.  Make sure you use the driver with the highest release number unless you experience specific problems with it that are addressed by downgrading to a previous release.

It sounds like a problem I used to have when enabling Compiz on Dapper, and the issue there was that I needed to enable 2 options in my xorg.conf file to make the title borders work again.  I do this automatically these days so don't really know if it is still needed, but apparently it is!

```
Option "AllowGLXWithComposite" "TRUE"
Option "AddARGBGLXVisuals" "TRUE"
```

Add these two options to your xorg.conf file located under /etc/X11.

Easiest way to edit this file is by opening a terminal and typing:

```
sudo gedit /etc/X11/xorg.conf
```

You will need to enter your password.

Then finding the [device] section and add these two lines under the lines that are already listed in that section. e.g.
```

Section "Device"
  Identifier  "Configured video device"
  Driver      "nvidia"
  Option      "AllowGLXWithComposite"  "TRUE"
  Option      "AddARGBGLXVisuals"      "TRUE"
EndSection
```

Save the file and close it.

Then you need to either restart X windows by using ctrl-alt-delete or reboot your system.

---

### Post by Samilong on 2008-11-15
finite9,

You're a genius... 

I added the two lines you provided (using vim - ouch, that was painful) and rebooted...

Bingo! Problem solved!

Thanks.

---

