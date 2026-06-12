---
title: "Can't Set Nvidia Screen Resolution"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by igb on 2006-06-12
I have an Asus motherboard with integrated nForce 2 graphics. With Hoary and Breezy I had no problem setting 1280x1024 resolution. I have just done a clean install of Dapper and I can't get anything more than 1024x768.

Things I have done so far:

Install nvidia-glx.
Edited xorg.conf to use the nvidia driver (I get the splash screen so I know it's using the driver).
Added  "1280x1024"  to the various Modes sections in xorg.conf.
Edited the monitor section in xorg.conf so it's the same as the the identical monitor on another working computer.
Tried the legacy nVidia driver.

Whenever I select Screen Resolution from System/Preferences the max. resolution it displays is 1024x768.

Ian.

---

### Post by zugu on 2006-06-12
Didi you restart GNOME (CTRL+ALT+BACKSPACE) after editing the xorg.conf file?

---

### Post by frodon on 2006-06-12
You can often solve this problem adding the horizontal and vertical refresh rate parameters of your screen in the xorg.conf file.

---

### Post by igb on 2006-06-12
Thanks, but I rebooted after each change. Also I have Horiz and Vert refresh rates in xorg.conf.

Ian.

---

### Post by igb on 2006-06-12
I have made some progress. Changing the default colour depth from 24 to 16 lets me run it at 1280x1024. However, it ran fine at 24 bit in Hoary and Breezy and under Windows.

Ian.

---

### Post by zugu on 2006-06-12
It would be interesting to see the contents your xorg.conf file. Could you please paste it to [http://paste.ubuntu-nl.org/](http://paste.ubuntu-nl.org/) and provide us the link?

---

