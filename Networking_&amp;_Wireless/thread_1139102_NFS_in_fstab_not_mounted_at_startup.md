---
title: "NFS in fstab not mounted at startup"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by noahhomsky on 2009-04-26
I have some workstations on ubuntu. On this workstations some network paths is mounted by NFS. But after upgrade to Jaunty I have one problem: NFS mounts in fstab not mounted automatically at startup. Strange thing: NFS paths mounts successfully by command "mount -a".

/etc/fstab:
```
proc            /proc           proc    defaults        0       0
UUID=6718dc6d-85e8-4d04-8f7b-8aaecb4da9b0 /               ext4    relatime,errors=remount-ro 0       1
UUID=9262692e-49e7-4efc-836d-fc7f2a70a363 none            swap    sw              0       0
192.168.0.40/drop     /home/locadmin/drop     nfs4    defaults        0       2
```

On Intrepid all works good. There I'm wrong?

---

### Post by jatatar on 2009-04-28
I too am having this trouble...with dlink-NAS 323.  It is new with Juanty, intrepid works fine.  Anyone got a fix?

---

### Post by drs305 on 2009-04-28
> 
**192.168.0.40/**drop     /home/locadmin/drop     nfs4    defaults        0       2

I believe you are missing a colon.
> 
**192.168.0.40[COLOR="Red"][B]:**[/COLOR]/[/B]drop     /home/locadmin/drop     nfs4    defaults        0       2

---

### Post by noahhomsky on 2009-04-28
> **drs305 said:**
> I believe you are missing a colon.

Sorry. It is strange but in my fstab colon is present. Maybe it's my or forum bug.

---

### Post by drs305 on 2009-04-28
I didn't notice your bean count (either of you). Welcome to the ubuntu forums.

Once your system is fully booted, and with the NFS unmounted, what messages related to your NFS do you get in terminal when you run:
```

sudo mount -a

```

---

### Post by noahhomsky on 2009-04-28
> **drs305 said:**
> I didn't notice your bean count (either of you). Welcome to the ubuntu forums.

Once your system is fully booted, and with the NFS unmounted, what messages related to your NFS do you get in terminal when you run:
```

sudo mount -a

```

Its first what I find in google. But at some servers (in virtual enviroment) NFS need to be mounted before some daemons. I do quick fix in init.d scripts. Its works but I prefer "native" way. I post [bug to launchpad]("https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/367675") but it still Undecided.

Maybe nfs-common conflicts with another package?

---

### Post by noahhomsky on 2009-05-04
Problem solved with add "ASYNCMOUNTNFS=no" to /etc/defaults/rcS

---

### Post by kw1502 on 2009-05-14
I'm having the same problem. Adding ASYNCMOUNTNFS=no did NOT work for me. Here are the entries in my fstab that don't work 

```
fserver:/home/shared	/media/MyDocuments	nfs	user,auto,rsize=8192,wsize=8192,timeo=14,rw,soft,intr	0	0
fserver:/backups/AVFiles/Ken	/mnt/MyAV	nfs	user,auto,rsize=8192,wsize=8192,timeo=14,rw,soft,intr	0	0
```

I also tried once using the IP address and that did not work either.
sudo mount -a does work.

---

### Post by kw1502 on 2009-05-15
After thinking about this more, I realize on Jaunty, I used to be able to have NFS shares mounted at boot time from /etc/fstab. I recently, changed my Ethernet adapter and since then, the NFS shares don’t auto mount and I need to do sudo mount –a.

The new NIC is obviously supported since I can surf the internet, get an IP address, etc. I’ve checked /var/log/* and see nothing that indicates a problem. Adding ASYNCMOUNTNFS=no to /etc/default/rcS did not help.

Any ideas what could be going wrong?

---

### Post by kw1502 on 2009-05-15
Problem has been solved. The problem is that
the new NIC was called eth1 and the old NIC eth0.
/etc/network/interfaces started eth0 only.

More detail can be found in [http://ubuntuforums.org/showthread.php?t=473944]("http://ubuntuforums.org/showthread.php?t=473944")

I also had to remove ASYNCMOUNTNFS=no from rcS to make things work.

---

