---
title: "updated to 11.04 now Wlan wont work properly."
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by anaconda on 2011-04-07
Ok.
I updated my asus eee pc 1005p, which had ubuntu 10.10 to 11.04 with "update-manager -d"

The new kernel wont boot at all. So I have to use the "boot previous ubuntu" option in grub, which boots using the 10.10:s kernel.

My problem is that now most of the time when I try to connect my laptop to internet with wlan. It complains that the wlan is disabled with a hardware switch...
But there is no hardware switch for disabling the wlan in eee pc 1005p. !?!

Sometimes (rarely) the wlan works... strange.
Any help will be appreciated. eg. is it possible to switch the "hardware" switch to ON? 


With the kernel not booting issue (which is not that important, since the 10.10:s kernel works. The machine seems to just hang, after selecting the new kernel from grub. It is doing something but wont respond to anythind except hard reset. 
Tried the Ctrl-Alt-F2 etc..

---

### Post by grahammechanical on 2011-04-08
Try

```
ifconfig wlano up
```

Do you have another OS installed? Sometimes, if you switch wireless off in the other OS it stays switched off in Ubuntu. You need to switch it back on in the other OS. Your computer may use a keyboard key combination such as fn + a f number key.

Regards.

---

### Post by 5149.5 on 2011-04-08
Try:

```
sudo rfkill unblock all
```

---

