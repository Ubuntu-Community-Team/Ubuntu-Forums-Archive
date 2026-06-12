---
title: "Need Intel Video card driver"
date: 2011-02-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Typhoid on 2011-02-02
After upgrading to Natty, the Unity Plugin stopped working altogether. Furthermore, after rebooting after the upgrade, an error message showed up: "You do not have the hardware to run Unity. Installing a driver may be a help." After that, I discovered that my Video card driver inexplicably changed to "fbdev" (whatever that means). After much speculation on this thread: [http://ubuntuforums.org/showthread.php?t=1680305](http://ubuntuforums.org/showthread.php?t=1680305), I have concluded that I require an Intel driver for my Intel 945 GME graphics card. Note that this driver must work with Compiz and Unity and all that 3D stuff. I'd greatly appreciate anyone finding me such a driver and also offering installation instructions. Thanks in advance.

FYI I have a Toshiba NB100 Netbook running Ubuntu Netbook 11.04.

P.S. I don't understand why this thread was moved. This thread pertains more to video drivers than it does to Natty Narwhal. I would like this thread to be moved back to Multimedia & Video.

---

### Post by cariboo on 2011-02-02
You'll get complaints about not starting your thread in the correct subforum, so I moved it here before they can start.

The driver you need is in the repositories, just open synaptic package manager and search for xserver-xorg-video-intel, and mark it for installation. Install everything that is recommended.

---

### Post by Typhoid on 2011-02-02
Thread closed. Please continue this thread here: [http://ubuntuforums.org/showthread.php?t=1680305](http://ubuntuforums.org/showthread.php?t=1680305).

---

