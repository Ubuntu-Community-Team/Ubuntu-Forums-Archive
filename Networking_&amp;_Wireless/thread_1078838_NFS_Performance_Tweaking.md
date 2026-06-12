---
title: "NFS Performance Tweaking"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by Deathmoon on 2009-02-23
I recently purchased a Netgear ReadyNAS Duo which I have on my home network.  It's running great, however file transfer speeds are fairly slow in my opinion with the avg being about 9MB/s.

The following is from my /etc/fstab file
```
192.168.15.148:/media /media/nasmedia nfs rsize=32768,wsize=32768 0 0 
```

I've done some performance testing by doing the following:

```
sudo umount /media/nasmedia
sug /etc/fstab
```

change the rsize & wsize from 8192 up to 32768 (16k, 24k)

```
sudo mount -a
time dd if=/dev/zero of=/media/nasmedia/testfile bs=16k count=16384
time dd if=/media/nasmedia/testfile of=/dev/null bs=16k
```

The final setting of 32768 produced the best results of 9MB/s but on a 100MB/s network that doesn't seem right (my router and NAS are both 1GB, not sure about my desktop NIC come to think of it).

Anyway, what other items can I do to increase the speed, or is this the best I'm going to get?

BTW, this is all on a wired network.  Thanks in advance.

---

### Post by Deathmoon on 2009-02-27
bump?

---

### Post by punx45 on 2009-02-27
this may seem like a stupid question, but are you confusing bits and bytes?

fast ethernet is a 100 mega bit /second system, so if your figure of 9 mega bytes a second  is correct (assuming an interface rounds up to the nearest unit, eg 9MB vs 9,xxx KB), then that translates to approximately 74 mega bits (says google calc) a second, which seems reasonable.

---

### Post by Deathmoon on 2009-02-28
Oh my...you are totally correct.  I didn't even think about that, thank you.

That said, if I'm getting 10MB it's roughly 80mb per second over my 100mb switch.  Thanks for pointing out my mistake.

---

### Post by punx45 on 2009-03-01
no problem :-D   dont feel bad, i have to think hard about it sometimes too :D

---

### Post by Dethecus on 2009-03-01
I pull 11MB/s over my 100mb network from Samba to Windows so more than 9MB/s is definitely achievable. I only get 8.3MB/s from Ubuntu to my Samba share though so I also have some tweaking to do :P

---

