---
title: "Sound is always &quot;0&quot; and muted after booting"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by ciacorp on 2006-06-04
So the title is my problem :)

even "sudo alsactl store" couldn't solve the problem although Ubuntu really saves my volume values at /var/lib/alsa/asound.state .

Someone with a resolution?
Thanks in advance!

ciacorp

---

### Post by Abel Hernandez Zanatta on 2006-06-05
Hi,

I have exactly the same problem, after the upgrade from breezy I have the volume "0" and always muted after reboot.

I mean.....  after set the volume control I have sound but after reboot it is the same again...

Anyone with a solution...?

---

### Post by al:x on 2006-06-11
Just to add another case here. Exactly the same problem for me.

Right after the upgrade it even didn't recognize my sound card: Intel Corporation 82801 Mobile PCI Bridge

I added the module snd-intel8x0 to /etc/modules to solve this.

But now I always have to unmute everything after startup...

Anybody able to solve this issue or got some hint?

---

### Post by al:x on 2006-06-11
This is solved for me...

...by updating the kernel to the new version.

Just installing the package linux-image-2.6.15-23-386 did the job ;-)

---

