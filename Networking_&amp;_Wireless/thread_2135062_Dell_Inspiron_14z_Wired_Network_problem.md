---
title: "Dell Inspiron 14z Wired Network problem"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by Lupi on 2013-04-13
Hello. I have just bought a Dell Inspiron 14z. Now, being eager to install Linux on it, I used a live Linux Mint CD and everything worked flawlessly by being connected to the internet through a wire. Then, I used some life USB (Ubuntu and Linux Mint), but they couldn't see the wired network anymore. They can see the wireless networks, but not the wired one. The strange things is that in Windows 8, the wired network works well and now the same live CD I used initially doesn't see the wired network either.

As an additional information, I did play with the BIOS in order to run the live USB sticks (went from UEFI to Legacy and turned off the secure boot).

Any ideas on how to fix this?

---

### Post by Lupi on 2013-04-13
SOLVED

I used the tip in this forum [http://forums.linuxmint.com/viewtopic.php?f=150&t=109661](http://forums.linuxmint.com/viewtopic.php?f=150&t=109661)

> OK got it working so thought I would post what I did so others can benefit.
Go to [http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx)
Under Code subheading download the tarball.
To make it simple for those not in the know like me.
Extract the tarball to your desktop
Open terminal and type cd ~/Desktop/compat-wireless-2012-05-10-p
Then type ./scripts/driver-select alx
Then type make
Then type sudo make install
Then type sudo modprobe alx or restart computer.
Hope this helps others.

And now my wired network is also detected. The only thing I had to change is the name of the tarball as it has been updated.

---

