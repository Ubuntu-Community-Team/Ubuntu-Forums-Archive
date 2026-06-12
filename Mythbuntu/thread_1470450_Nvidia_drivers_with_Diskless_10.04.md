---
title: "Nvidia drivers with Diskless 10.04"
date: 2010-05-02
forum: Mythbuntu
---

### Post by lmclaren on 2010-05-02
Hi,

Has anyone got the Nvidia drivers to install on a diskless client with 10.04?

thanks

LM

---

### Post by jmatienzo on 2010-05-05
Yes, basically you have to blacklist module nouveau but for some reason adding it to /etc/module.d/blacklist.conf won't work. the only way I could blacklist it was to add "blacklist=nouveau" to the APPEND option in pxelinux.cfg/default

---

### Post by lmclaren on 2010-05-08
Thanks jmatienzo, I still haven't had any luck, I have blacklisted it via pxelinux.cfg/default and the modprob.d but cant get the Nvidia driver to install correctly.

Can you give me a bit more detail please.

best regards

Lee

---

### Post by kingmoffa on 2011-03-07
Hi, 

I had some luck with this eventually - thanks for the blacklist advice. That helped. 

You need to install the nvidia module (I used apt) inside the chroot on the tftp server - not inside the diskless client. 

Then update the image AND update the kernels. 

sudo ltsp-update-image
AND
sudo ltsp-update-kernels

---

