---
title: "Newbie's NVIDIA driver problem"
date: 2010-06-08
forum: Multimedia Software
---

### Post by mulehollandaise on 2010-06-08
Hello,

I tried installing Ubuntu yesterday for the first time ever ; I was on Windows Vista before, and so I tried using Wubi. The installation completed successfully, but when I rebooted my computer I saw a Ubuntu logo and then a black screen with horizontal blue rays, looking like a graphics bug...

I have a ASUS K50IN laptop with a NVIDIA GeForce G102M. The bug looked like a driver problem, so I tried various solutions :
- hitting [ESC] when booting to enter Safe Graphics Mode or ACPI Workarounds : same bug
- hitting [CTRL][ALT][F2] and entering "sudo dpkg-reconfigure xserver-xorg" : the message "debconf: DbDriver "config" : /var/cache/debconf/config.dat is locked by another process : Ressource temporairement indisponible" prompted

I don't really know what's going on, does anyone have an idea ?
Thanks a lot in advance ! :)

PS: I forgot to mention : I noticed that when booting, there are a couple of messages like this displaying : "ureadahead-other main process (2526) terminated with status 4" ; no idea about what it means, but it's the only thing that seem "odd" in the booting messages...

---

### Post by farbird on 2010-06-08
press CTRL ALT F2
login with your name and password

sudo nano /boot/grub/grub.cfg
look for something that says vga=xxx

delete away these [vga=***] without deleting the rest of the lines.
[if it is not present in the grub.cfg file, then its ok ]
CTRL X and save.

make sure you have your ethernet plugged in

sudo apt-get update && sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot

see what happens when u do a reboot

---

### Post by mulehollandaise on 2010-06-08
Thank you soooooooooo much ! It works perfectly ! I had a little bit of trouble getting to the login because what I had was "ubuntu@ubuntu" or something like that... But once I got to the login, everything worked just fine ! Thank you !!! :p

---

### Post by farbird on 2010-06-10
/me loves to help anyone to get a proper linux os up and running on their hardware.

Would love to do it for $$, but GPL advise against it..

---

