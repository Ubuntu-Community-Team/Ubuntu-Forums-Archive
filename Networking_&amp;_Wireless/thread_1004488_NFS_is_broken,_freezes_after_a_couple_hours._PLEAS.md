---
title: "NFS is broken, freezes after a couple hours. PLEASE HELP!"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by mike503 on 2008-12-07
I upgraded my Ubuntu Hardy server to Intrepid the night before last.
When I woke up yesterday morning, my main server I use as my ssh
gateway into the others was totally messed up.

My server is FreeBSD. I haven't had to touch it since I set it up.

My clients are 6 Ubuntu servers. All are identical in packages,
configs (I diff'ed /etc), kernel versions, network setup, etc.

Only *one* of the machines is suffering (and of course, one of the
most important ones) - and it isn't even one of the busiest.

I've tried downgrading the kernel on the box suffering the issue from
2.6.27-10 to 2.6.27-7, my next attempt will be picking a kernel .deb
that was from the previous Ubuntu release...

What is odd is that it works great after reboot and lasts for a couple
hours, then stops working. I can umount -l /home and then try to
remount it (see below) but it never gets anywhere and eventually dies
with a generic message. I tried to strace -f it, and it gave me
nothing to work with. The FreeBSD server doesn't give me anything in
logs to go off of either. I can ping and ssh between the two no
problem at this point still. It's just NFS that is odd. Also I did
notice trying to restart services manually and try to debug them that
portmap seemed to throw a kernel error in my logs once in a while. But
I don't get a connection to portmap when I run the mount command, and
I would assume if portmap is required for mounting NFS shares that it
would need to contact it. That could totally be irrelevant though.

Any help or insight or request for additional information is
appreciated. On-list or off-list is fine. I will pay someone via
Paypal who can help me resolve this quickly...

[root@lvs01 ~]# mount -vvvv /home
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: spec:  "raid01:/home"
mount: node:  "/home"
mount: types: "nfs"
mount: opts:  "rsize=8192,rsize=8192,tcp,rw,acregmin=30"
mount: external mount: argv[0] = "/sbin/mount.nfs"
mount: external mount: argv[1] = "raid01:/home"
mount: external mount: argv[2] = "/home"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,rsize=8192,rsize=8192,tcp,acregmin=30"
mount.nfs: timeout set for Sun Dec  7 06:36:39 2008
mount.nfs: text-based options:
'rsize=8192,rsize=8192,tcp,acregmin=30,addr=10.13.220.94'
(just stalls here, normally a connection is near instant. eventually
it will die with a generic error message. i can control-C to quit it
too, so it's not frozen completely)



thanks...

---

### Post by dmizer on 2008-12-08
Is your network connection dropping for some reason? If so, this could be part of your problem: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258734](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258734)

What the bug report doesn't say, is that it also effects CLI and non-gnome resources.

The best way I've found to get around an unstable network connection is to mount NFS with autofs: [http://ubuntuforums.org/showthread.php?t=760326](http://ubuntuforums.org/showthread.php?t=760326)

---

### Post by mike503 on 2008-12-08
> **dmizer said:**
> Is your network connection dropping for some reason? If so, this could be part of your problem: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258734](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/258734)

What the bug report doesn't say, is that it also effects CLI and non-gnome resources.

The best way I've found to get around an unstable network connection is to mount NFS with autofs: [http://ubuntuforums.org/showthread.php?t=760326](http://ubuntuforums.org/showthread.php?t=760326)

Nope. It's a dedicated wired gigabit LAN connection in a datacenter. During this time I can ping/ssh back and forth without an issue. It is localized to NFS (and perhaps portmap/other supporting products)

I went back to linux-image-2.6.24-16-server and right now it seems to be working fine.

which means:
linux-image-2.6.27-10-server
linux-image-2.6.27-7-server
linux-image-2.6.28-2-server

all suffer from this for me (only on that machine. 5 other machines are using linux-image-2.6.27-10-server and seem to be just fine)

---

### Post by dmizer on 2008-12-08
What gigabit card are you using? I've been seeing some reports of gigabit lan cards getting disconnected under high load. It's really the only thing I can think of that would give you the symptoms you're experiencing.

That's not to say that it IS what's causing your problem. Only that I can't think of another reason.

---

### Post by mike503 on 2008-12-08
> **dmizer said:**
> What gigabit card are you using? I've been seeing some reports of gigabit lan cards getting disconnected under high load. It's really the only thing I can think of that would give you the symptoms you're experiencing.

That's not to say that it IS what's causing your problem. Only that I can't think of another reason.

0d:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)
0e:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

these don't have any issues on the 5 other servers, and i'm not pushing enough traffic for "high load" - other servers on the LAN are pushing more. the kernel downgrade seems to have resolved this for the moment. but that means all of the kernels available in intrepid may have some funky issue in them.

also i am connected to these machines remotely and i can connect in and out of them it is only nfs that has the issues, not the entire interface.

---

### Post by dmizer on 2008-12-08
Okay what options do you have in exports on your FreeBSD server?

Also, what are you using for your /etc/fstab mount line on the Ubuntu server?

---

### Post by mike503 on 2008-12-08
> **dmizer said:**
> Okay what options do you have in exports on your FreeBSD server?

Also, what are you using for your /etc/fstab mount line on the Ubuntu server?

freebsd server /etc/exports:

/home -maproot=root -network 10.13.5.0 -mask 255.255.255.192
/home -maproot=root -network 10.13.220.80 -mask 255.255.255.240

ubuntu /etc/fstab:

raid01:/home    /home                   nfs             rsize=8192,rsize=8192,tcp,rw,acregmin=30        0       0

Remember this works fine on 5 other identical boxes. It's just this one box. Like I said, I downgraded the kernel to linux-image-2.6.24-16-server and things have stabilized now for a couple days which is longer than the couple hours I got with the "unstable" setup.

I can't really tell if this is a true bug, if it's with the Ubuntu kernels, or the NFS utils + kernel combination or what. Or if it's even a bug...

but I have a script to dpkg -l and md5sum it, all my servers are identical there. /etc is identical according to rsync (well, all relevant files), same network connections etc... and it does mount and work just fine after reboot it just seems to go stale and I have nothing in logs to go off of on client or server.

---

### Post by dmizer on 2008-12-08
> **mike503 said:**
> ```
raid01:/home /home nfs [COLOR="Red"]rsize[/COLOR]=8192,[COLOR="Red"]rsize[/COLOR]=8192,tcp,rw,acregmin=30 0 0
```

Does your fstab line really have two rsize options or is one of them actually wsize?

Edit:

According to the verbose mount output in your first post, you do have two rsize options.
> **mike503 said:**
> ```
mount.nfs: text-based options:
'rsize=8192,rsize=8192,tcp,acregmin=30,addr=10.13.220.94'

```
Since your NFS is also set for write (rw option), you should change one of these to wsize. You could be getting disconnected on a write? Why some kernels work and others don't is beyond me.

---

### Post by mike503 on 2008-12-09
> **dmizer said:**
> Does your fstab line really have two rsize options or is one of them actually wsize?

Edit:

According to the verbose mount output in your first post, you do have two rsize options.

Since your NFS is also set for write (rw option), you should change one of these to wsize. You could be getting disconnected on a write? Why some kernels work and others don't is beyond me.

hah!

that's a good catch. it's the same on all my servers though - just like everything else. i will fix that. funny nobody else i've ran this by said anything about that :)

that being said i still don't think it's the issue, since the other boxes are identical too.

---

### Post by dmizer on 2008-12-16
Is this still an issue for you?

I noticed there were some NFS updates in my queue, so I thought perhaps your problem may be solved after updating?

---

### Post by mike503 on 2008-12-16
> **dmizer said:**
> Is this still an issue for you?

I noticed there were some NFS updates in my queue, so I thought perhaps your problem may be solved after updating?

i did do an update. but i don't know if it fixed anything. i didn't check what got updated, but i just looked and didn't see any NFS updates since i last did an apt-get dist-upgrade.

---

### Post by ejstacey on 2009-04-29
Did you ever find the cause of this?  This is happening to me (same setup, freebsd nfs server.. sharing out a zfs filesystem.. wonder if that matters?).  It's driving me nuts!

Thanks.

---

### Post by dmizer on 2009-04-29
Try adding the "soft" option to your NFS mount like so:
```
server.mydomain.com:/share /mountpoint nfs [COLOR="Red"]soft,[/COLOR]rsize=8192,wsize=8192,timeo=14,intr
```
That won't solve your disconnect problem, but it will prevent your computer from becoming unresponsive as a result.

---

### Post by ejstacey on 2009-04-29
I've done it.  We'll see how it goes for the rebooting/freezing problem ;)

For reference, my line is: 

rsize=65536,wsize=65536,intr,tcp,timeo=600,soft

I've tried 1024, 4096, 8092, and 65536 as the rsize and wsize numbers.

---

### Post by mike503 on 2009-04-29
Oddly enough, I was able to upgrade 5 of my 6 machines to the latest kernel (Intrepid at the time) without an issue. 3 of th ose machines used NFS much more heavily than the machine with the issue.

The machine with the issue -still- had an issue though.

So I had to install an older kernel...

I have not tried Jaunty yet though. I'm hoping once again I can have everything run the same. Right now a dpkg -l is identical (using md5) other than the one older kernel package on the one server. Everything else is identical on every other server without issue. Odd that only this one machine has the issue.

---

### Post by ejstacey on 2009-04-29
I'm on Jaunty and it still happens to me, so I don't like your chances if you decide to upgrade ;)


I'll look into kernel stuff, and trying different ones.  Thanks for the suggestion.

---

