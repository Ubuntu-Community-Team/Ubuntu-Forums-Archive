---
title: "Does kvm work for you?"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by decoherence on 2010-09-08
I just upgraded to maverick (i686) had a problem with kvm similar to this bug: [https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/627514](https://bugs.launchpad.net/ubuntu/+source/virt-manager/+bug/627514)
which basically means I can't create or run virtual machines with kvm. When I try I get

> Error starting domain: internal error Process exited while reading console log output: libvir: Security Labeling error : internal error error calling aa_change_profile()

I just did a search and it doesn't look like it has come up here yet. As I was investigating I found this old bug [https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/448671](https://bugs.launchpad.net/ubuntu/+source/libvirt/+bug/448671) which gave me the hint to put apparmor in to complain mode (rather than enforce mode) for libvirtd.

So here's the command, in case anyone else is having similar trouble with kvm/libvirt.

```
sudo aa-complain /usr/sbin/libvirtd
```

And you should have working KVM again. When the bug gets fixed re-enable security.

```
sudo aa-enforce /usr/sbin/libvirtd
```

Unfortunately my system is no good for generating bug reports. I use a lot of 3rd party repos and had to fight with apt just to get it from lucid to maverick. So it could just be me, but I thought I'd put it out there in case anyone went searching and because I'm curious if anyone can reproduce this on a 'clean' system and maybe take a look at that first bug report I posted.

cheers,

---

