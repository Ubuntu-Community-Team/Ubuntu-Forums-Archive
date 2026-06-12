---
title: "Latest kernel (2.6.32-30) update breaks Realtek wifi support"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by Paddy Launch on 2011-03-18
Hi all, I upgraded the kernel (to 2.6.32-30) in this morning's updates and it broke wifi for me. I have a workaround if this affects you too.

I am using lucid netbook remix on a Dell Mini 1018 which has a Realtek rtl8192CE wireless card. Up until now I have been successfully using the wireless driver from this PPA: [https://launchpad.net/~lexical/+archive/hwe-wireless](https://launchpad.net/~lexical/+archive/hwe-wireless)

After the kernel upgrade, no wireless hardware is visible at all. 

The workaround is simply to go back to using the previous kernel (2.6.32-29), and one way to do this (at the command line) is as follows:

1. ```
$ sudo gedit /etc/default/grub
```

2. change the line GRUB_DEFAULT=0 to 
```
GRUB_DEFAULT=**saved**
``` and then save
(This will allow you to change the default kernel to boot at the command line using the grub-set-default command).

3. ```
$ sudo update-grub
```

4. ```
$ sudo grub-set-default 2
```
(This should set the default kernel to the last one before the update, i.e. 2.6.32-29).

5. reboot

6. ```
$ uname -r
2.6.32-29-generic
``` 
(to check which kernel you are running now)

Wireless should now be working, if it was working before!

I suppose that when a new kernel update comes out you may have to remember to type "sudo grub-set-default 0", in order to use it, but I'm not sure...

---

