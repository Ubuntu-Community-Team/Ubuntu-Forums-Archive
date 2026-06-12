---
title: "So I caused the X server to die when I upgraded my video card."
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by YourSurrogateGod on 2006-10-15
Ok, I recently upgraded my video card (not as much gameage with the old one.) Now, when I decided to boot Ubuntu, I get this blue screen saying that X server no longer works.

My video card is Nvidia GeForce 7600GS.

How could I go back to a basic display that's in Linux without having hardware 3D acceleration?

Then when that basic display is working, I could try to re-install the drivers for Linux.

Thoughts?

---

### Post by adwait on 2006-10-15
Try 
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by YourSurrogateGod on 2006-10-15
Umm... if there's a manual to that config guide, could you please link it :) .

Better yet, how would I re-install x server? I'm guessing that when I re-install it, I won't get any of the hardware 3D acceleration, but it's not that difficult to reinstall the drivers.

---

### Post by taurus on 2006-10-15
The above command will allow you to reconfigure your X again.  And once you have X up and running, you can install nVidia driver for your new graphic card.  So at the prompt, do

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tseliot on 2006-10-15
You can follow these instructions:

type:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "nv" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
sudo /etc/init.d/gdm restart (or "kdm restart" if you use KDM)
```

the Xserver should work fine


NOTE: if the problem is not solved try using "vesa" or "vga" instead of "nv" and try again.


Then you might want to install Nvidia's proprietary driver

---

### Post by YourSurrogateGod on 2006-10-15
I'll try that tseliot.

---

### Post by YourSurrogateGod on 2006-10-15
Oh yeh, I meant to ask. What does lpsci -X do?

---

### Post by YourSurrogateGod on 2006-10-15
Hmm... the desktop came up without a problem now. *shrug* Seems like all systems are green. Thanks for your help guys.

---

