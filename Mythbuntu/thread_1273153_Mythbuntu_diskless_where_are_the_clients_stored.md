---
title: "Mythbuntu diskless: where are the clients stored"
date: 2009-09-23
forum: Mythbuntu
---

### Post by Macus on 2009-09-23
Hi all

I have got mythbuntu to be a pxe server and can pxe to other computers on the network

but somthing i dont get is how it is able to remeber what iv done to each comp

for example I boot pxe mythbuntu on comp1 and install vlc
if I then reboot it, it still has it installed, without effecting comp2

my question is how does it remeber this?
it must be stored on the server, but where?

I suspect in the i386.img file, but how do I open/edit this 
I wish to delete one comp and then reboot it (wich should effectivly reinstall it)
thanks

---

### Post by jmeads on 2009-09-23
If you make changes on the client it'll alter the overlay for that machine, these can be found here

/var/cache/mythbuntu-diskless/overlay/${mac address}/

The image file is produced from /opt/ltsp/i386/ changes can be madeto all clients if you alter this inside a chroot and then rebuild the image see [https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless](https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless)

---

### Post by blackoper on 2009-09-24
this is good to know. Say I mess up with a client, if I delete the overlay mac address directory and everything inside it will it then basically be fresh on the next boot of that client?

---

