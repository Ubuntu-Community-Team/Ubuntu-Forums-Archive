---
title: "How to configure an ATi Radeon card 9250 after an hardware upgrade?"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by lignito on 2006-08-17
How to configure an ATi Radeon card 9250 after an hardware upgrade?
Now I can't start ubuntu....I only have the command line acesse...how can I configure Xorg in this case? any help will be apreciated,Thanks .

---

### Post by Greycloak on 2006-08-17
Did you update the graphics card or something else? If you need to edit xorg.conf from the command line, type:

```
sudo pico /etc/X11/xorg.conf
```

Without knowing exactly what you upgraded, I can't really offer any more help.

---

### Post by lignito on 2006-08-17
Thank you for your reply...I upgraded my AGP(nvidia) card with is new one Ati Radeon 9250,now i grafic mode doen't work

---

### Post by Darth Tux on 2006-08-26
just type:
```
sudo dpkg-reconfigure xserver-xorg 
``` 
then choose your driver, either "ati", or "fglrx" if you have the official ATI drivers installed. Then choose the defaults for the rest until you get to the modules screen. Make sure that you check "glx" and "dri". Then continue with the defaults till the end. When you restart you should be back in business.

---

