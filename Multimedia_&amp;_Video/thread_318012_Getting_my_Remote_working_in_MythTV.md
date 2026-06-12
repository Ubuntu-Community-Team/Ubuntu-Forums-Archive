---
title: "Getting my Remote working in MythTV"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by Gibble on 2006-12-13
Hi everyone.

I have had a lot of success installing MythTV in Edgy, everything is working great, except one thing, my remote.

I followed these instructions
[http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft](http://www.mythtv.org/wiki/index.php/LIRC_on_Ubuntu_Edgy_Eft)

and everything seemed fine, the only things I noticed that were out of the ordinary is when testing and it asks me to run 

```
 sudo modprobe lirc_i2c
 dmesg | tail
```

My output is missing the middle line of expected output.
```
 lirc_i2c: chip found @ 0x71 (Hauppauge IR (PVR150))
** ivtv0: i2c attach to card #0 ok [client=Hauppauge IR (PVR150), addr=71]**
 lirc_dev: lirc_register_plugin: sample_rate: 10
```

I can run irw and see the buttons that are mapped, but in MythTV, nothing works.  Not sure what's not right, probably a file somewhere...but who knows.

I'm running two PVR150s with the standard A415 remote.

Thanks for the help,
--Gibbs

---

### Post by superm1 on 2006-12-15
Do you have a ~/.mythtv/lircrc?

MythTV doesn't use the user wide ~/.lircrc unless you make a symlink to it

```
ln -s ~/.lircrc .mythtv/lircrc
```

---

### Post by Gibble on 2006-12-15
Yes I do.

---

### Post by majoridiot on 2006-12-15
> **superm1 said:**
> Do you have a ~/.mythtv/lircrc?

MythTV doesn't use the user wide ~/.lircrc unless you make a symlink to it...

you left out a "/", mario.  should be...

```
ln -s ~/.lircrc ~/.mythtv/lircrc
```

;)

---

### Post by superm1 on 2006-12-15
> **majoridiot said:**
> you left out a "/", mario.  should be...

```
ln -s ~/.lircrc ~/.mythtv/lircrc
```;)
hehe thanks :D

---

