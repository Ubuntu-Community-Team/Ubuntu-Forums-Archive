---
title: "Natty Alpha 2 won't boot by itself."
date: 2011-02-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by frankzen on 2011-02-05
Installed the alpha 2 last night on a clean partition...but discovered it won't boot without removing everything (except the basics) from the kernel boot line. No biggie except I'm lacking a graphic boot. Because this machine has Intel onboard graphics (865) can't run any desktop with effects, so Natty looks a lot like all its predecessors. 
Anybody got a solution to the boot problem. If I do a regular boot with no editing, 4 seconds later, the caps lock and scroll lock lights start blinking and that's the end of the boot process.

---

### Post by jerrylamos on 2011-02-05
I make an 06_custom file on my multiboot system with the Natty entry like so:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Narwhal on sda7' {
set root=(hd0,7)
linux /vmlinuz root=/dev/sda7 ro 
initrd /initrd.img
}
```
Then I make it executable:
sudo chmod 777 06_custom 
sudo cp 06_custom /etc/grub.d
sudo update-grub
sudo grub-install /dev/sda

Note you have to modify sda7 to where ever the natty was,
and /dev/sda to your boot hard drive.

And yes it's running Unity.  I don't like it but as a tester I'm looking for bugs.

Now I sometimes get the kernel hang while booting with flashing lights on the keyboard depending on the state of the Natty updates.

Good luck. Jerry

---

### Post by frankzen on 2011-02-05
Thanks, I'll give it a try - I am trying to figure out whether it's the graphical logon, or the tty=7 directive which is messing up the boot.

---

### Post by cariboo on 2011-02-06
> **jerrylamos said:**
> I make an 06_custom file on my multiboot system with the Natty entry like so:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Narwhal on sda7' {
set root=(hd0,7)
linux /vmlinuz root=/dev/sda7 ro 
initrd /initrd.img
}
```
Then I make it executable:
sudo chmod 777 06_custom 
sudo cp 06_custom /etc/grub.d
sudo update-grub
sudo grub-install /dev/sda

Note you have to modify sda7 to where ever the natty was,
and /dev/sda to your boot hard drive.

And yes it's running Unity.  I don't like it but as a tester I'm looking for bugs.

Now I sometimes get the kernel hang while booting with flashing lights on the keyboard depending on the state of the Natty updates.

Good luck. Jerry

Why are you making 06_custom world read/writeable, it only needs permissions of 755?

---

### Post by jerrylamos on 2011-02-06
> **cariboo907 said:**
> Why are you making 06_custom world read/writeable, it only needs permissions of 755?
Cariboo, I was just doing what was easy.  I'll try 755 next time.

30_os-prober is marked as
rwxr-xr-x
whatever that translates to.

Jerry

---

