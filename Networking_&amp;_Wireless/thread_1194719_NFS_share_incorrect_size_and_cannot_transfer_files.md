---
title: "NFS share incorrect size and cannot transfer files."
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by steelsparky on 2009-06-23
Hello, I recently set up a Freenas server, set up NFS, and mounted the NFS share. However, the share is a 1.5tb external hd and while mount in Ubuntu it only shows to be 35mb. And on the freenas machine it shows the correct values. Any help would be appreciated.

---

### Post by dmizer on 2009-06-23
How are you accessing the share? Do you have an /etc/fstab line? If so, please post it. If you are not mounting via /etc/fstab, please see the client section of the NFS tutorial in my sig (4th link).

---

### Post by steelsparky on 2009-06-23
> **dmizer said:**
> How are you accessing the share? Do you have an /etc/fstab line? If so, please post it. If you are not mounting via /etc/fstab, please see the client section of the NFS tutorial in my sig (4th link).


Thanks for a quick response. Ok I am a little new to all this, so in my search on how to do this, I came across this line and put it in my fstab so I could automount.

I mount using..
```
sudo mount -t nfs 192.168.2.7:/mnt /home/steelsparky/freenas
``` so I can access it in nautilus


```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
192.168.2.7:/mnt   /home/steelsparky/freenas   nfs   user,sync,tcp,rsize=131072,wsize=131072   0   3
```

---

### Post by dmizer on 2009-06-23
Okay, after you've mounted the share, then run this command:
```
ls -ln /home/steelsparky/freenas
```
And post the output here.

---

### Post by steelsparky on 2009-06-23
> **dmizer said:**
> Okay, after you've mounted the share, then run this command:
```
ls -ln /home/steelsparky/freenas
```And post the output here.


```

steelsparky@ubuntu:~$ ls -ln /home/steelsparky/freenas
total 14
-rw-r--r-- 1 0 0 12288 2009-06-21 17:07 fuppes.db
drwxr-xr-x 2 0 0   512 2009-06-22 14:29 hdd
```

fuppes is for my xbox, and hdd is actually where the hard drive is mount inside freenas.

---

### Post by dmizer on 2009-06-23
Okay ... one last thing, please post the output of:
```
ifconfig
```

---

### Post by steelsparky on 2009-06-23
> **dmizer said:**
> Okay ... one last thing, please post the output of:
```
ifconfig
```

```
steelsparky@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:67:cc:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30420 (30.4 KB)  TX bytes:30420 (30.4 KB)

ra0       Link encap:Ethernet  HWaddr 00:22:43:6e:08:f3  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe6e:8f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:385663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69609755 (69.6 MB)  TX bytes:9374749 (9.3 MB)
          Interrupt:19 
```

---

### Post by dmizer on 2009-06-23
Try this fstab line instead:
```
192.168.2.7:/mnt[COLOR="Red"]/hdd[/COLOR]   /home/steelsparky/freenas   nfs   rsize=[COLOR="Red"]8192[/COLOR],wsize=[COLOR="Red"]8192,timeo=14,intr[/COLOR]
```
(changes marked in red)

---

### Post by steelsparky on 2009-06-23
> **dmizer said:**
> Try this fstab line instead:
```
192.168.2.7:/mnt[COLOR=Red]/hdd[/COLOR]   /home/steelsparky/freenas   nfs   rsize=[COLOR=Red]8192[/COLOR],wsize=[COLOR=Red]8192,timeo=14,intr[/COLOR]
```(changes marked in red)


Yeah I tried that and it won't auto mount at all now.:confused:

---

### Post by dmizer on 2009-06-23
> **steelsparky said:**
> Yeah I tried that and it won't auto mount at all now.:confused:

Okay, try this then:
```
192.168.2.7:/mnt   /home/steelsparky/freenas   nfs   rsize=8192,wsize=8192,timeo=14,intr
```

For further troubleshooting, it would help to see the /etc/exports file from your freenas server.

---

### Post by steelsparky on 2009-06-24
> **dmizer said:**
> Okay, try this then:
```
192.168.2.7:/mnt   /home/steelsparky/freenas   nfs   rsize=8192,wsize=8192,timeo=14,intr
```For further troubleshooting, it would help to see the /etc/exports file from your freenas server.

Ok, I still get the same thing with the new fstab line and here is my /etc/exports from the Freenas. And sorry I couldn't get back earlier, been busy with work. I appreciate your help very much.
```
/mnt -alldirs -mapall=root -network 192.168.2.0 -mask 255.255.255.0

```

---

### Post by dmizer on 2009-06-24
Well, everything looks OK on the client side as far as I can see, and the exports also looks ok. The only thing I have left to suggest is to bring this before the FreeNAS folks to see if they have any additional input.

Try posting here: [http://sourceforge.net/apps/phpbb/freenas/index.php](http://sourceforge.net/apps/phpbb/freenas/index.php)

---

### Post by steelsparky on 2009-06-25
[solved] 

I finally figured this out. I guess it was a rookie mistake on my part. I did some reading and THOUGHT ext3 partition would work. I suppose I should have mentioned this earlier. Come to find out they can only transfer files to other large devices. So I reformatted to the more compatible UFS freenas partition. Only shows 1.25tb of the total 1.5 but still work. Thanks again for all your support.

---

