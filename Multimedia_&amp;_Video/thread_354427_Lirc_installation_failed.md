---
title: "Lirc installation failed"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by JayDoubleM on 2007-02-05
Hello,
I tried to install lirc using the HowTo at Ubuntu Community, it failed when i tried to build the kernel/install modules. The weird thing is that I'm installing the receiver of the Hauppauge PVR150 which is i2c, and the log file shows errors about gpio.  During the configuration of the lirc modules i2c and gpio were preselected, however I selected i2c and pushed Enter to continue, I feel not unselecting gpio has something to do with this failing. However I found no way to unselect gpio.
I attached the error log.
I would appreciate help. I just recently migrated from Fedora to Ubuntu, I had the whole lirc working on Fedora, so Im sure its not a hardware issue. Im running Edgy.

---

### Post by JayDoubleM on 2007-02-06
problem solved

---

### Post by Roebi on 2007-02-07
> **JayDoubleM said:**
> problem solved

Can you please be more explicit?
I am also experiencing problems with lirc, and am trying to get as many clues as possible.

Thank you in advance


Roebi

---

### Post by JayDoubleM on 2007-02-07
[https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

On the bottom it says know problem for i2 and gpio, thats what helped me get itit working.

---

