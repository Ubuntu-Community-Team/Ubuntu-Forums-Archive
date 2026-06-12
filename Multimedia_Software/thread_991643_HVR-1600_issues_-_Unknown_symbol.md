---
title: "HVR-1600 issues - Unknown symbol"
date: 2008-11-24
forum: Multimedia Software
---

### Post by MikeCheck on 2008-11-24
I am trying to get my HVR-1600 working with Ubuntu 8.04.  I am following the directions from here: [http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600]("http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600")

When I get to the modprobe step, it tells me this:
```
FATAL: Error inserting cx18 (/lib/modules/2.6.24-21-generic/kernel/drivers/media/video/cx18/cx18.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

So I check dmesg, and it gives me this:
```
mike@mikedesk:~$ dmesg | grep cx
[   32.934825] cx18: disagrees about version of symbol v4l_compat_ioctl32
[   32.934830] cx18: Unknown symbol v4l_compat_ioctl32
```

Could anyone help me with this?  Would it be easier if I upgraded to 8.10?  I will most likely upgrade soon anyway.

---

### Post by TenGees on 2008-11-24
Exactly the same problem here... you're not alone.

Sorry I don't have a solution. I had the card somewhat working before updates (digital tuner in MeTV), maybe I should look in the trash for the old driver versions?

-------------------------------------------------

Update:
I installed an older version (v4l-dvb-9273407ca6e1), now it's working like it did before. Maybe you can still find the older version somewhere. Mine was in the trash. ;-)
I first ran:
sudo modprobe -r cx18
Not sure if that was necessary.

---

### Post by MikeCheck on 2008-11-24
> **TenGees said:**
> 
Update:
I installed an older version (v4l-dvb-9273407ca6e1), now it's working like it did before. Maybe you can still find the older version somewhere. Mine was in the trash. ;-)
I first ran:
sudo modprobe -r cx18
Not sure if that was necessary.

Do you think you could send me your older version?

---

### Post by Sonthun on 2008-11-30
I'm also having the same problem.  MikeCheck - Were you able to get a copy of the older version and did it work for you?

Thanks.

---

### Post by Sonthun on 2008-11-30
Okay.  I downloaded an old version of V4l and I still got:
```
qdan@LearnEd:~/v4l-dvb$ sudo modprobe cx18
FATAL: Error inserting cx18 (/lib/modules/2.6.24-22-generic/kernel/drivers/media/video/cx18/cx18.ko): Unknown symbol in module, or unknown parameter (see dmesg) 

```

Anybody have any ideas on how to fix this?

---

### Post by MikeCheck on 2008-11-30
> **Sonthun said:**
> I'm also having the same problem.  MikeCheck - Were you able to get a copy of the older version and did it work for you?

Thanks.

No, I never found the older version.

---

### Post by anupindi007 on 2009-05-31
Hi,

I have also save same issue and could you share the v4l-dvb-9273407ca6e1 repository link?

I am using M2n68-vm mother board and hvr-1600 card on ubuntu 2.6.27.14.

Thanks,
Srinivas

---

