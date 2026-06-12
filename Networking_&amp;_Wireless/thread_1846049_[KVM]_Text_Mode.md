---
title: "[KVM] Text Mode"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by Skyo on 2011-09-18
Hey Forum,

how do I start a (qemu-) KVM guest system in pure textmode within the bash?
I want to do this remotely via SSH and keep this machine running.
A Text mode + GNU Screen seems to be a perfect selution fot this job.


Thx. ):P

---

### Post by gmargo on 2011-09-18
You're probably looking for the [virsh]("http://linux.die.net/man/1/virsh") command.

[https://help.ubuntu.com/community/KVM/Managing](https://help.ubuntu.com/community/KVM/Managing)

---

### Post by Skyo on 2011-09-18
Tanky you very much.
This works pretty well ,too:

```
 kvm -curses -hda ubuntu.img

```But: If GUEST-VM is not server Version, you have to follow this tutorial:
[http://blog.zorinaq.com/?e=7](http://blog.zorinaq.com/?e=7)

And edit /etc/default grub

Change into text mode (edit):
```
 GRUB_CMDLINE_LINUX_DEFAULT="text" 
```And disable graphical terminal (just uncomment)
```
 GRUB_TERMINAL=console 
```If keyboard layout get messed up, -k option has to be used.
Save with:
```
 sudo update-grub 
```

---

