---
title: "Wich Compat Wireless version should I compile?"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by DarknessssenkraD on 2012-04-28
So I installed 12.04 and all the drivers got updated so far so good.
I allways use aircrack for some reason I allways get the -1 channel error.
I use to manually compile the compat wireless driver
But now I dont know wich one to download and compile, it gives me errors when I try to compile, and I dont know why
Any help?

I currently have 3.2.0-24-generic
and I tried with all of this

[http://wireless.kernel.org/en/users/Download/stable/](http://wireless.kernel.org/en/users/Download/stable/)

I tried compiling all above 3.0
bellow the list from of the packages
```
Kernel release
sha1sum
size
ChangeLog-wireless
ckmake.log.bz2
compat-wireless-3.4-rc3-1.tar.bz2
0e2137bccce41cfb485e2554400d344413283f11
4.1 MB
ChangeLog-3.4-rc3
ckmake-3.4-rc3-1.log.bz2
compat-wireless 3.3 stable releases

Kernel release
sha1sum
size
ChangeLog-wireless
compat-wireless-3.3-1.tar.bz2
e100832be6d157043cb927ba184380dbddb40387
4.0 MB
ChangeLog-3.3-wireless
compat-wireless-3.3-2-n.tar.bz2
dd18cfabbe705a75440fd7fbe50a09d5fe34bb70
4.0 MB
ChangeLog-3.3-wireless
compat-wireless 3.2 stable releases

Kernel release
sha1sum
size
ChangeLog-wireless
compat-wireless-3.2.5-1.tar.bz2
e7bcdc038b9f85e74308b175b41560b6d5a31c50
4.0 MB
ChangeLog-3.2-wireless
compat-wireless 3.1 stable releases

Kernel release
sha1sum
size
ChangeLog-wireless
compat-wireless-3.1.1-1.tar.bz2
d0bb37b9643e21873a0edbe3f8a99f48a826c6e8
4.1 MB
ChangeLog-3.1-wireless
compat-wireless 3.0 stable releases

Kernel release
sha1sum
size
ChangeLog-wireless
compat-wireless-3.0.9-1.tar.bz2
388d2a76d70b0671d65383e121e0078c3aa9cc69
4.1 MB
ChangeLog-3.0-wireless
```


My question is, wich one should I use? and how do I know if they are compatible with this kernell 3.2.0-24-generic

And a extra one:
Oh and what packages should I get it to compile?

Greets!

---

### Post by jawilljr on 2012-04-28
> NOTE: Please be aware that the releases below contain code from the given version of the Linux kernel. Therefore to add functionality, you should select a version that is later than your kernel version.  from [here.](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_stable_releases)

Compat-wireless is a backport so you should always choose a version that is greater than you kernel. I would start with compat-wireless-3.4-rc3-1.tar.bz2.

Having said that did you install "build-essential" and the linux headers?

```
sudo apt-get install build-essential linux-headers-generic
```

BTW compat-wireless-3.4-rc3-1.tar.bz2 will compile and install in Lucid.

Jerry

---

### Post by DarknessssenkraD on 2012-04-30
Thanks Jerry, I got compat-wireless-3.4-rc3-1.tar.bz2 to compile withn not a Single error but now the wireless won't load =(

I don't know why.

I tried uninstalling all the packages that came with ubuntu linux-backports-modules-cw-*

But same result, wireless not working until I uninstall the compiled version

"sudo make uninstall"

---

### Post by DarknessssenkraD on 2012-04-30
I removed linux-backports-modules-cw* and removed the compiled versions and I still get signal :S
are there other packages that provide the services for the wireless?
How can I remove them? so that I can try to compile again?

---

