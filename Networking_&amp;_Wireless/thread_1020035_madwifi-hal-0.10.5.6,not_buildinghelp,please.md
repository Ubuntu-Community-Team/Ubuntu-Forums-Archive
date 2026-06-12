---
title: "madwifi-hal-0.10.5.6,not building?????help,please"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by rixtr66 on 2008-12-23
ive built and installed this driver in ubuntu 8.04 and 8.10.
im trying to build it in ubuntu studio 8.04,ive never had this problem
with this driver its built every time?
```
root@ubuntuS:~/Desktop/madwifi-hal-0.10.5.6# make
cd: 1: can't cd to /lib/modules/2.6.24-22-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-22-rt/build is missing, please set KERNELPATH.  Stop.
root@ubuntuS:~/Desktop/madwifi-hal-0.10.5.6# 

```
ive installed build essential,kernel headers for 2.6.24-22-rt,
please help!! wireless is my only connection to the internet!!
i use this driver and wicd and it worked flawlessly??????
in 8.04,8.10,any help would be appreciated!!
Rick ](*,)

---

### Post by jamesonjlee on 2008-12-25
> **rixtr66 said:**
> ive built and installed this driver in ubuntu 8.04 and 8.10.
im trying to build it in ubuntu studio 8.04,ive never had this problem
with this driver its built every time?
```
root@ubuntuS:~/Desktop/madwifi-hal-0.10.5.6# make
cd: 1: can't cd to /lib/modules/2.6.24-22-rt/build
Makefile.inc:66: *** /lib/modules/2.6.24-22-rt/build is missing, please set KERNELPATH.  Stop.
root@ubuntuS:~/Desktop/madwifi-hal-0.10.5.6# 

```
ive installed build essential,kernel headers for 2.6.24-22-rt,
please help!! wireless is my only connection to the internet!!
i use this driver and wicd and it worked flawlessly??????
in 8.04,8.10,any help would be appreciated!!
Rick ](*,)

you have to include the linux-header.

**Update**
try
```

sudo apt-get install linux-headers-`uname -r`

```

I forgot why, but I ended up rolling back to 2.6.24-21-rt

---

