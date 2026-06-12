---
title: "Mythbuntu 12.04 and InfiniTV install problems"
date: 2012-07-11
forum: Mythbuntu
---

### Post by Memorex636 on 2012-07-11
I just installed Mythbuntu 12.04 (x64)  popped in my new infinitv 4 pcie card. Downloaded the linux drivers.
From talking with the InfiniTV support the drivers are not installing properly. 
I extracted the drivers and ran. 
sudo make install 
sudo modprobe ctn91xx

and I get a FATAL: Module ctn91xx not found.

has anyone else run it to issues with this. Is there something else I need to do first?

Any assistance would be helpful

---

### Post by klc5555 on 2012-07-11
Not a card I use. However, if the driver module you have installed is a kernel module, and has, in fact installed to the correct place, you'll still need either to run sudo depmod from a prompt or to reboot (which will also run depmod) before modprobe will know that the module is there.

---

### Post by Memorex636 on 2012-07-11
> **klc5555 said:**
> Not a card I use. However, if the driver module you have installed is a kernel module, and has, in fact installed to the correct place, you'll still need either to run sudo depmod from a prompt or to reboot (which will also run depmod) before modprobe will know that the module is there.

its these drivers they wont install
i just installed an 11.04 and its still doing the same thing so its not changes in the OS its something I need in order to run sudo make install command...

---

### Post by Memorex636 on 2012-07-11
> **Memorex636 said:**
> its these drivers they wont install
i just installed an 11.04 and its still doing the same thing so its not changes in the OS its something I need in order to run sudo make install command...

I'm an idiot.... I got it

thanks

I didn't realize "make" was a command

---

