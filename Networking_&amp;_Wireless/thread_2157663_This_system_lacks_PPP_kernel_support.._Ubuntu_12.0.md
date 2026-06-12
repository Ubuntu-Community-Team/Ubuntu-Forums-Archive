---
title: "This system lacks PPP kernel support.. Ubuntu 12.04 LTS"
date: 2013-06-26
forum: Networking &amp; Wireless
---

### Post by m4uri on 2013-06-26
I try to setup a VPN Connection from a Ubuntu 12.04 LTS to  Microsoft VPN Server ( Ubuntu is the Client in this Case ),
but i only get this error message:

[COLOR=#333333][FONT=sans-serif][B]

".. connection failed! Check the log messages below for information why.[/B][/FONT][/COLOR]

Couldn't open the /dev/ppp device: Operation not permittedFATAL: Module ppp_generic not found./usr/sbin/pppd: Sorry - this system lacks PPP kernel support"

Details you may need:

modprobe -v ppp > FATAL: Module ppp not found.
uname -r -> 2.6.32-042stab076.8

---

### Post by praseodym on 2013-06-26
Sure you are using 12.04? The kernel looks like 10.04...

Check:

```
dpkg -l linux-image-* | grep ii
lsb_release -a
```

---

### Post by m4uri on 2013-06-26
> **praseodym said:**
> Sure you are using 12.04? The kernel looks like 10.04...

Check:

```
dpkg -l linux-image-* | grep ii
lsb_release -a
```

it was a 10.04 ( its just what we got from our provider, we updated the machine using:


sudo apt-get install update-manager-core
do-release-upgrade -d
everything else was untouched.

**dpkg -l linux-image-* | grep ii **
Result: *Nothing*

[B]lsb_release -a
[/B]Result:

*No LSB modules are available.*
*Distributor ID: Ubuntu*
*Description:    Ubuntu Saucy Salamander (development branch)*
*Release:        13.10*
[I]Codename:       saucy

any suggestions ?[/I]

---

### Post by m4uri on 2013-06-26
added dpkg -l results -> attachement.

---

### Post by praseodym on 2013-06-26
Wow, obviously you upgraded from 10.04 to 13.10 via all versions in between?!

Is it 32 or 64 bit?

---

### Post by m4uri on 2013-06-26
its 64bit, but still no vpn....can you help me out on that one ?

---

### Post by praseodym on 2013-06-26
Save these files in "Downloads":

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-headers-3.9.0-030900-generic_3.9.0-030900.201305071030_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-headers-3.9.0-030900-generic_3.9.0-030900.201305071030_amd64.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-headers-3.9.0-030900_3.9.0-030900.201305071030_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-headers-3.9.0-030900_3.9.0-030900.201305071030_all.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-image-3.9.0-030900-generic_3.9.0-030900.201305071030_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-image-3.9.0-030900-generic_3.9.0-030900.201305071030_amd64.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/linux-*.deb
```

---

### Post by m4uri on 2013-06-26
> **praseodym said:**
> Save these files in "Downloads":

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-headers-3.9.0-030900-generic_3.9.0-030900.201305071030_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-headers-3.9.0-030900-generic_3.9.0-030900.201305071030_amd64.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-headers-3.9.0-030900_3.9.0-030900.201305071030_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-headers-3.9.0-030900_3.9.0-030900.201305071030_all.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-image-3.9.0-030900-generic_3.9.0-030900.201305071030_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-saucy/linux-image-3.9.0-030900-generic_3.9.0-030900.201305071030_amd64.deb)

Installation via:
```

sudo dpkg -i ~/Downloads/linux-*.deb
```


we are running on a VPS @ some providers network, which youses virtuozzo containers, is there some knwon problem connected to openVZ/virtuozzo and ppp/vpns ?
i will try your downloads and report soon.

---

