---
title: "Diskless/USB boot question"
date: 2009-03-10
forum: Mythbuntu
---

### Post by raptorjr on 2009-03-10
I have the diskless network boot up and running and i really like it. But i wonder if it is possible to put the created image on a USB but still use the overlay when the system is up and running? Or do i need to go a completely different way?
I like how easy it is to configure the image with the control center but i think it would be faster to boot if the image was on a USB. But i dont want anything to be written to the USB unless i make a new image.

Is this possible?

---

### Post by laga on 2009-03-12
Hi,

there is no facility for this. By default, it tries to connect to an NBD server on the network. 

You can hack the initramfs scripts to make it look on local storage, that shouldn't be too hard. Still, I don't believe it will be much faster - it does not download the whole image. Feel free to prove me wrong :)

---

