---
title: "Diskless Frontends"
date: 2008-01-04
forum: Mythbuntu
---

### Post by BustedChicken on 2008-01-04
Does Mythbuntu support diskless frontends? The last reference I have seen on the forums was from Nov.

---

### Post by superm1 on 2008-01-04
It's possible to set one up, but a wee bit convoluted to do so.  There is a spec that is being worked on (hopefully for Hardy) that should eventually automate things further.

---

### Post by BustedChicken on 2008-01-07
Any chance of getting a quick write up, or instructions on how to do so.

---

### Post by superm1 on 2008-01-11
Not a direct one at this point.  I'm not the one working on the diskless spec.

You have two basic options.

1) Install to a hard drive in the server you will be booting from

2) Build an install from a chroot.  This can get very messy.

Once you have a base install to work from, you can follow any of the existing diskless howtos for any Ubuntu install (reconfiguring the initramfs for NFS boot, setting up dhcp server with the proper options, etc).

The spec will eventually aim to set some of this stuff up for you.

---

### Post by laga on 2008-01-12
I'm the guy working on the spec for diskless frontends. We'll most likely be using modified LTSP scripts to automate most of our stuff.

I could give you a few hints how to get a diskless frontend up and running, but I was not very successful with that method to be honest. Anyways, the simplest thing to do would be:

* Come up with a way to load the kernel + initramfs into memory. That's normallydone with a bootloader; I used extlinux which is in the syslinux package. 
* Pass some options to the kernel (initramfs really) to make it mount an nfs share as its root file system. My config for extlinux looked like this:

```
default diskless
timeout 150
prompt 1
label diskless
kernel vmlinuz-${KVER}
append initrd=initrd-${KVER} nfsroot=${SERVER}:${ROOT} ip=dhcp root=/dev/nfs

```

Make sure to replace all variables with sensible stuff.

Of course, you need to have a Mythbuntu install you can export via nfs. Of course, you could just use your existing Mythbuntu install but won't work well. You don't want two computers use the same install simultaneously :)

I'd suggest you use debootstrap to create a new install in a directory on your harddisk and export that directory. Also see "man chroot".

Good luck, it's not an easy task. With the method I've just described, I failed because / would never get mounted rw on the client, only read-only. Maybe you have better luck.. there are workarounds, though.

Feel free to ask questions if you get stuck.

Regards,

Michael

---

### Post by rickyble on 2008-02-27
I am very interested in a modified version of this.  I was thinking about booting from a CD and have a config on the CD for the frontend.  I was wondering if I booted and got everything right hardware connection etc and saved it to a zip attached could you then use it to create a CD boot to use on that client.   Trnasfer all your setting to the appropriate place on the CD.  You could also even use a DVD and a CD drive and use the diskless as a music or video DVD player I think.   As cheap as CD are you could recreate it very easily if the hardware changed.  Is that possible?  I know you probably could do the pxe boot for the diskless but I dont about setting all that up and which would be better.  Anyway would that be possible?

---

### Post by laga on 2008-02-29
Creating a client-specific live disk sounds like a nice idea. I don't know if it's currently possible. Maybe you can write up a spec at [https://blueprints.launchpad.net/mythbuntu/](https://blueprints.launchpad.net/mythbuntu/)

Regarding mythbuntu-diskless, you don't have to set up PXE. It'll be possible to boot strap the client from a USB pen drive or from a disk. The kernel and the initramfs are pulled from that location while the rest of the system is mounted over the network.

It *should* already work in hardy, but I haven't tried it and there are no instructions yet. I'll post updates in this thread: [http://ubuntuforums.org/showthread.php?t=711079](http://ubuntuforums.org/showthread.php?t=711079)

---

