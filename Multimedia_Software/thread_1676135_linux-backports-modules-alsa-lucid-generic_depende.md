---
title: "linux-backports-modules-alsa-lucid-generic dependency problem"
date: 2011-01-26
forum: Multimedia Software
---

### Post by potiphera on 2011-01-26
In the update manager today I saw there was an update for linux-backports-modules-alsa-lucid-generic, but it can't update.  I get this error when trying to update it:
```
linux-backports-modules-alsa-lucid-generic:
 Depends: linux-backports-modules-alsa-2.6.32-28-generic  but it is not installable
```
I also see a similar error when I try to install linux-backports-modules-alsa-lucid-preempt.  Is this a bug, or what?  I'm using Ubuntu Studio 10.04 64-bit.

---

### Post by notanumber67890 on 2011-01-27
I have the same issue on 10.04 64-bit after today's updates.  

No sound without the alsa backports.  Does anyone know how to install manually?

---

### Post by goerdi on 2011-01-27
Manual install fails because it can't find the packet, also i could not find it in any ppa

ciao goerdi

---

### Post by Chello on 2011-01-27
Looks like i have the same problem.

Today i updated the kernel to 2.6.32-28 via updatemanager and now im without sound as there is no alsa for this.

---

### Post by lidex on 2011-01-27
It looks like the backport for that kernel is not ready yet. Use the previous kernel until it is.

---

### Post by potiphera on 2011-01-28
I'd like to use a previous version of the preempt kernel, but I just installed it the other day so there aren't older versions available in GRUB.  Which packages do I need to install to get an older version?

---

### Post by BicyclerBoy on 2011-01-28
Had this error last few weeks..can get alsa 1.0.23 from ubuntu audio dev team ppa & not bother with source code.

Or you can use synaptic & search for the kernel version you wish..
You may need to force the version or just install the kernel version directly.
Remember to undo this 'version locking' when the alsa backports is available.

There is a Ubuntu kernel ppa that has the latest versions.

---

### Post by notanumber67890 on 2011-01-29
Thanks for the suggestions ...

Booting to the previous kernel does work.

Installing alsa from source also worked for me - I now have audio using the 2.6.32-28-generic kernel.

Quick steps, as root:

```

apt-get remove linux-backports-modules-alsa-lucid-generic
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2
tar jxvf alsa-driver-1.0.23.tar.bz2
cd alsa-driver-1.0.23
./configure --with-sequencer=yes
make
make install
./snddevices
reboot

```

Does anyone know whether I will have to re-install alsa after the next kernel update?

---

### Post by BicyclerBoy on 2011-01-29
Yes you will.

An alt pre-compiled ppa for alsa 1.0.23
[http://ppa.launchpad.net/team-iquik/alsa/ubuntu](http://ppa.launchpad.net/team-iquik/alsa/ubuntu)

I have used this to get alsa 1.0.23 & the alsa modules source to add the a52 encoder plug-in.

Another way is to use the kernel update ppa as alsa 1.0.23 is std in the later kernel.
[http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu)

---

