---
title: "Google Earth in OpenGL with software emulation"
date: 2010-02-16
forum: Multimedia Software
---

### Post by groundnut on 2010-02-16
Recently I installed Google Earth on my Ubuntu computer.

I downloaded it form Google's website and got it installed.

However it is running slow. A notice says: 

You are currently running Google Earth in 'OpenGL' with software emulation.

How do I get Google Earth running on the hardware OpenGL?

---

### Post by RJARRRPCGP on 2010-02-16
It's probably because your video is Nvidia or ATI. 

Nvidia support and ATI support is not included out of the box.

---

### Post by groundnut on 2010-02-17
So installing the generic linux driver from Nvidia probably would solve the problem.

---

### Post by RJARRRPCGP on 2010-02-21
> **groundnut said:**
> So installing the generic linux driver from Nvidia probably would solve the problem.

No! The generic Nvidia driver don't support 3D! It's unfortunately like the generic Windows XP VGA driver.

---

### Post by groundnut on 2010-02-21
@ RJARRRPCGP: What would be your solution?

---

### Post by nos09 on 2010-02-21
mine is runnig just fine. can you please describe your computer's configuration.?

---

### Post by groundnut on 2010-02-22
hello nos09,

my setup consist of:

Ubuntu 9.10
Graphics card: GeForce 9600GT 512MB DDR3 PCI-E
Processor: Intel Core2Quad Q8200 4x2,33 GHz
Memory: 4 GB DDR2/800 Dimm Bulk

---

### Post by Yellow Pasque on 2010-02-22
Ok, so did you install the proprietary nvidia driver? If so, and you still have issues, what does glxinfo command say?
```
LIBGL_DEBUG=verbose glxinfo
```

---

### Post by groundnut on 2010-02-22
Thanks Temüjin,

Now with Ubuntu 9.10 I did not install a display driver.

Before with Ubuntu 9.04 I installed the proprietary nvidia driver.


**Do you think the proprietary nvidia driver might solve my problem?**

---

### Post by Yellow Pasque on 2010-02-22
Yes, if you install it correctly, it gives you 3D hardware accel.

---

### Post by nos09 on 2010-02-22
> **groundnut said:**
> Thanks Temüjin,

Now with Ubuntu 9.10 I did not install a display driver.

Before with Ubuntu 9.04 I installed the proprietary nvidia driver.


**Do you think the proprietary nvidia driver might solve my problem?**

the nvidia driver may be the problem. if you dont know how to install Nvidia drivers then you can install by the help of EnvyNG. it will help you a lot. try to install graphic card drivers and then tell us if the problem continues .

---

### Post by groundnut on 2010-02-23
This time installing the proprietary nvidia driver did not go well.

During start up Ubuntu does not reach the login screen. Just before it would reach the login screen the Ubuntu logo appears and then disappears. Then the system freezes.

Do I have to reinstall Ubuntu now or can I solve this problem?

---

### Post by nos09 on 2010-02-23
> **groundnut said:**
> This time installing the proprietary nvidia driver did not go well.

During start up Ubuntu does not reach the login screen. Just before it would reach the login screen the Ubuntu logo appears and then disappears. Then the system freezes.

Do I have to reinstall Ubuntu now or can I solve this problem?

well if you can then do it.
but remember to back up the your data.
you can access your data by inserting live cd.( somebody tell me if i m wrong )
and then install your nvidia driver in new installation.

---

### Post by groundnut on 2010-02-24
I reinstalled Ubuntu today.

I used EnvyNG, but it did not install the driver.

Then I used system > administration > restricted drivers manager.
That worked.

At last I installed Google Earth, which works perfectly.

Problem solved!

Thanks guys!

---

### Post by nos09 on 2010-02-24
> **groundnut said:**
> I reinstalled Ubuntu today.

I used EnvyNG, but it did not install the driver.

Then I used system > administration > restricted drivers manager.
That worked.

At last I installed Google Earth, which works perfectly.

Problem solved!

Thanks guys!

your welcome. enjoy the power of linux.

---

