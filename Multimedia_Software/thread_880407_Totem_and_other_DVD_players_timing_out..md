---
title: "Totem and other DVD players timing out."
date: 2008-08-05
forum: Multimedia Software
---

### Post by dclinuxuser on 2008-08-05
I am trying to play dvds on Totem and it just hangs. I tried other players with the same results.  When I look at the System Monitor it reads that dev/scd0 is at 100%. Do I need to increase the amount of memory allocated to /dev/scd0 ?

---

### Post by dclinuxuser on 2008-08-05
Here is my usage:

root@ubuntu:/home/mike# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G  6.0G  209G   3% /
varrun                506M  112K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   60K  506M   1% /dev
devshm                506M   24K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/scd0             7.9G  7.9G     0 100% /media/MURDERBALL

---

