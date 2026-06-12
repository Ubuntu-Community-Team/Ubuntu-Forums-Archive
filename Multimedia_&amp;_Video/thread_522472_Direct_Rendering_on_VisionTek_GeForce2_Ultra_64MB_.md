---
title: "Direct Rendering on VisionTek GeForce2 Ultra 64MB (DDR) 4x AGP"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by Redscare on 2007-08-10
I have a rather old (2001) computer that I now have to use because my hard drive failed on my laptop. This computer has a VisionTek GeForce2 Ultra 64MB (DDR) 4x AGP video card, and I was wondering if it was possible to get direct rendering on it? If so then how? Thank you in advance.

---

### Post by Redscare on 2007-08-11
Anyone?

---

### Post by RomeReactor on 2007-08-11
Hi. Are you using Ubuntu (Gnome)? If so, the easiest way to enable direct rendering (that I know of) is going to "System->Preferences->Desktop Effects" and enabling them; the installer dialog will ask you if you want to install the nVidia restricted drivers (the official nVidia binary drivers). Answer "Yes", and if your card is capable enough, you should then have Desktop Effects--and therefore direct rendering.

But before you do that, install this program--only so you can more easily manage or disable Desktop Effects (Compiz) if you so wish:
```
sudo apt-get install gnome-compiz-manager
```
After installation, you'll find it in "System->Preferences->GL Desktop".

---

### Post by Redscare on 2007-08-20
The problem is that xorg.conf and Desktop Effects say "Generic Video Card"...is there a way to get it correctly detected? it works in windows.

---

### Post by RomeReactor on 2007-08-21
Did you try enabling the drivers by going to "System->Preferences->Desktop Effects"? or by going to "System->Administration->Restricted Drivers Manager"? try those first.

If that didn't get you direct rendering, install the **nvidia-glx-legacy** drivers:
```
sudo apt-get install nvidia-glx-legacy
```
then
```
sudo nvidia-glx-config enable
```

---

### Post by Redscare on 2007-08-23
I have tried both and neither work. Please note that for the card it does not say GeForce2 Ultra in the xorg.conf, it says "Generic Video Card". Thank you for the answers and please help me a little more.

---

### Post by tseliot on 2007-08-23
> **Redscare said:**
> I have tried both and neither work. Please note that for the card it does not say GeForce2 Ultra in the xorg.conf, it says "Generic Video Card".
That's just a label and doesn't affect the functioning of your card.

P.S. remember to restart the Xserver

---

