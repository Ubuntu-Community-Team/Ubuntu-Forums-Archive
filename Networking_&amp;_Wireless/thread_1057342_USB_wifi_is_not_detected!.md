---
title: "USB wifi is not detected!"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by retro-starr on 2009-02-01
I have the latest version of Xubuntu, using Xfce, and I made it my main OS. Completely wiped the HDD and put xubuntu on. Well after I edited "/boot/grub/menu.lst" my external usb wifi stick no longer works.

_Changes I made_
```
timeout 0
#hiddenmenu
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		02f999bc-731c-4e9d-9a01-1d1b1450773a
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=02f999bc-731c-4e9d-9a01-1d1b1450773a
initrd		/boot/initrd.img-2.6.27-11-generic
```[I][SIZE="1"]
I removed "ro quite splash" from kernel and "quiet" from under initrd[/SIZE][/I]

It worked for the first two times, then failed booting several times after that. I know the wifi works because I've been using for the entire time. I've looked at the trouble-shooting for ndiswrapper, that didn't help, but it did say that it was detected and ndisgtk says it's installed and present. Reinstalling via ndisgtk doesn't work either.

The wifi stick fails during times of change, I don't know why. I hope to learn how to solve this little bugger. Thanks in advance.

---

