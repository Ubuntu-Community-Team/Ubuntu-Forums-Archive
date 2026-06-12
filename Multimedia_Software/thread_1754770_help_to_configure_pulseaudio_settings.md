---
title: "help to configure pulseaudio settings"
date: 2011-05-10
forum: Multimedia Software
---

### Post by doubleOh on 2011-05-10
I have just upgraded to 11.04 and the sound on my skype isn't working...please help me configure my pulseaudio settings.
whenever i try opening pulseaudio volume control, it says "Connection failed: Connection refused"
thanks

---

### Post by lidex on 2011-05-10
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by doubleOh on 2011-05-12
thanks a bunch...it worked :)

---

### Post by agestrada on 2012-09-25
After a lot of searching and trying I found this and it worked for me too!. Many thanks,

---

