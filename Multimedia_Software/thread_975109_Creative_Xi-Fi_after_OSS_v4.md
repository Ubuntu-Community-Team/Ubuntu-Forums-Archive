---
title: "Creative Xi-Fi after OSS v4?"
date: 2008-11-08
forum: Multimedia Software
---

### Post by m.afifi on 2008-11-08
Using **intrepid** I've installed OSS v4 to get sound working on my Xi-Fi card in the past.

I've followed [Temüjin's instructions](https://help.ubuntu.com/community/OpenSound) on getting it to work (although I had to get the latest source code, more on why here, [http://4front-tech.com/forum/viewtopic.php?t=2922](http://4front-tech.com/forum/viewtopic.php?t=2922))


With the release of the latest open source driver from Creative I wanted to give it a try.

Followed these instructions

[https://help.ubuntu.com/community/OpenSound#Reverting%20to%20ALSA](https://help.ubuntu.com/community/OpenSound#Reverting%20to%20ALSA)

Most worrying thing is there is no evidence of oss-linux being installed?!

```

sudo dpkg -r oss-linux
dpkg - warning: ignoring request to remove oss-linux which isn't installed.

```

```

/var/lib/dpkg/info$ sudo oss-linux*
sudo: oss-linux*: command not found

```

However every time I reboot, OSS is still there?

Moved on and tried installing the Creative driver, and now I've ended up with these errors,

```

XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-7-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1

```

```

dmesg
*<snip/>*
[ 1177.941779] ctxfi: Unknown symbol snd_ctl_add
[ 1177.941832] ctxfi: Unknown symbol snd_pcm_new
[ 1177.941879] ctxfi: Unknown symbol snd_card_register
[ 1177.941926] ctxfi: Unknown symbol snd_card_free
[ 1177.941973] ctxfi: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 1177.942036] ctxfi: Unknown symbol snd_pcm_hw_constraint_minmax
[ 1177.942122] ctxfi: Unknown symbol snd_ctl_new1
[ 1177.942203] ctxfi: Unknown symbol snd_card_new
[ 1177.942250] ctxfi: Unknown symbol snd_pcm_lib_malloc_pages
[ 1177.942299] ctxfi: Unknown symbol snd_pcm_lib_ioctl
[ 1177.942350] ctxfi: Unknown symbol snd_pcm_lib_free_pages
[ 1177.942411] ctxfi: Unknown symbol snd_ctl_notify
[ 1177.942458] ctxfi: Unknown symbol snd_pcm_set_ops
[ 1177.942520] ctxfi: Unknown symbol snd_device_new
[ 1177.942583] ctxfi: Unknown symbol snd_pcm_hw_constraint_integer
[ 1177.942676] ctxfi: Unknown symbol snd_pcm_period_elapsed

```

What am I doing wrong?

---

### Post by m.afifi on 2008-11-08
```

sudo rm -r /lib/modules/$(uname -r)/kernel/oss
sudo rm -r /usr/lib/oss
sudo rm -r /usr/lib64/oss
*Delete the start commands point to /etc/init.d/oss in /etc/rc**
sudo rm -r /etc/init.d/oss
sudo apt-get install --reinstall linux-image-$(uname -r)86-64)

```

Reboot your machine and get back into the creative install directory

```

make clean
make
sudo make install

```

Impressions in just the last few minutes

[LIST]
[*]Sound is *much* better than OSS for me.
[*]Front panel works just fine (except it still plays through both outputs)
[*]No more pops etc... with any programs :D
[/LIST]

---

### Post by frankidem on 2008-11-12
My friend i have the same problem can you describe the solution with more details?

---

### Post by vernsh on 2009-05-16
In my very limited to be sure experience, I've found that the Creative X-Fi driver works fine with intrepid if OSS v4 is NOT installed.  However, the driver will not install in jaunty at all, giving the error message described above. If you upgrade to jaunty from intrepid with the driver already installed, you can get sound for applications, only if you install OSS v4, but not for system sounds.  I plan to stick with intrepid for now in the hope ( I've made the request) that Creative update it's driver to work with jaunty.

---

