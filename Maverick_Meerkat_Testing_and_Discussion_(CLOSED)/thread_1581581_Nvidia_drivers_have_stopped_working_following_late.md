---
title: "Nvidia drivers have stopped working following latest updates"
date: 2010-09-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Psychobudgie on 2010-09-25
Updated this morning with around 72 packages and on restart the nvidia driver is failing. Have had to deactivate the nvidia package to get booted up. Anyone had a similar issue or any ideas on the cause?

Sorry, just noticed [http://ubuntuforums.org/showthread.php?t=1549872](http://ubuntuforums.org/showthread.php?t=1549872) which seems to be the reason.

Will hold fire until the drivers catch up.

---

### Post by VinDSL on 2010-09-25
Yep, these forums are rife with this happening.

I've had to re-install my nVidia drivers (almost) every time there has been a kernel update.

A couple of times Compiz has quit working, after an update, and needed to be purged and re-installed.

Goes with the territory...  ;)

---

### Post by philinux on 2010-09-25
Just updated via chroot which included nvidia-current update. Rebooted and all was fine.

nVidia 8600GT.

---

### Post by Quackers on 2010-09-25
I just installed all the latest updates, which included some nvidia current stuff and on reboot it said the drive wasn't ready then it continued booting to a black screen, which then turned blue and then the desktop appeared. So, all in all a scary but successful reboot :-)

---

### Post by ronacc on 2010-09-25
updated via synaptic about 1/2 hr ago , reboot normal Nvidia 7600 gs and Nvidia-current .

---

### Post by skeeby on 2010-09-25
i still have this problem.

reinstalled nvidia-current and no difference.

---

### Post by ronacc on 2010-09-25
take a look at /home/<you>/.xsession-errors  that may give you a clue as to what is going wrong .

---

### Post by Psychobudgie on 2010-09-25
> **skeeby said:**
> i still have this problem.

reinstalled nvidia-current and no difference.

Same here, tried a complete purge and reinstall. On reboot the machine goes to a black screen followed by the display going to standby. Machine then becomes unresponsive and requires a hard power down to get it back to life.

---

### Post by TBerk on 2010-09-25
> **skeeby said:**
> i still have this problem.

reinstalled nvidia-current and no difference.



I think it'll help to also include your model of video card as well.  Nvidia made a whole lot of them over the years.

product: NV34 [GeForce FX 5200]

Found via:

```

$sudo lshw

```


TBerk

---

### Post by Psychobudgie on 2010-09-25
> **TBerk said:**
> I think it'll help to also include your model of video card as well.  Nvidia made a whole lot of them over the years.

TBerk
GeForce FX 5200

Using an Nvidia GeForce 8600 GT here. Having a quick scan through the logs of the last failed attempt I noticed the following. Any offers?

Sep 25 18:49:18 zarniwoop kernel: [   13.458521] [drm] nouveau 0000:03:00.0: allocated 1680x1050 fb: 0x40250000, bo f2db8800
Sep 25 18:49:18 zarniwoop kernel: [   13.458588] fb1: nouveaufb frame buffer device
Sep 25 18:49:18 zarniwoop kernel: [   13.458590] registered panic notifier
Sep 25 18:49:18 zarniwoop kernel: [   13.458595] [drm] Initialized nouveau 0.0.15 20090420 for 0000:03:00.0 on minor 0

---

### Post by cariboo on 2010-09-25
> **Psychobudgie said:**
> Using an Nvidia GeForce 8600 GT here. Having a quick scan through the logs of the last failed attempt I noticed the following. Any offers?

Sep 25 18:49:18 zarniwoop kernel: [   13.458521] [drm] nouveau 0000:03:00.0: allocated 1680x1050 fb: 0x40250000, bo f2db8800
Sep 25 18:49:18 zarniwoop kernel: [   13.458588] fb1: nouveaufb frame buffer device
Sep 25 18:49:18 zarniwoop kernel: [   13.458590] registered panic notifier
Sep 25 18:49:18 zarniwoop kernel: [   13.458595] [drm] Initialized nouveau 0.0.15 20090420 for 0000:03:00.0 on minor 0

It looks like your system is trying to load the nouveau drivers, do you have nouveau-firmware installed?

---

### Post by Psychobudgie on 2010-09-25
> **cariboo907 said:**
> It looks like your system is trying to load the nouveau drivers, do you have nouveau-firmware installed?

Nope.

Was configured to use the Nvidia Binary drivers so I'm bamboozled by this.

---

### Post by VinDSL on 2010-09-25
> **Psychobudgie said:**
> Nope.

Was configured to use the Nvidia Binary drivers so I'm bamboozled by this.You might try blacklisting...

```
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
```

---

### Post by TBerk on 2010-09-25
> **VinDSL said:**
> You might try blacklisting...

```
blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
```


Could you explain just a bit about 'blacklisting'?  Oh, wait...

HOWTO: Prevent (blacklist) modules from loading
[http://ubuntuforums.org/showthread.php?t=166624](http://ubuntuforums.org/showthread.php?t=166624)

Here are my thoughts going forward:

- Some people have older Nvidia video cards and others later models. That means there is a fork in the road in terms of what solutions are applicable.

- Older cards will likely need to retrograde and/or block the 'current' drivers/modules. Newer cards seem to need a few tweaks and/or specific drivers loaded and "Bobs yer Uncle".

- Eventually both types of cards, newer and older, will get 'new' drivers and work in Meerkat Maverick. Eventually.  (hopefully.)


It's almost the end of Sept and Oct is when 10.10 comes out. Will most of the interested people have a great experience w/ the new release? Probably. 

Will I, specifically? Most likely, but not guaranteed.  

I'm currently having trouble w/ a pre-released Beta version of a 'free' operating system. One I'm not spending a minute's time on coding, anything.

huh.


TBerk

---

### Post by ktp on 2010-09-25
You can also select the driver that you wish to use:

[https://wiki.ubuntu.com/X/Drivers](https://wiki.ubuntu.com/X/Drivers)
> sudo update-alternatives --config gl_conf
sudo ldconfig
sudo update-initramfs -u

---

### Post by VMC on 2010-09-25
> **ktp said:**
> You can also select the driver that you wish to use:

[https://wiki.ubuntu.com/X/Drivers](https://wiki.ubuntu.com/X/Drivers)

That's a good link, thanks. Lots of helpful information for the folks that have older nvidia cards.

---

