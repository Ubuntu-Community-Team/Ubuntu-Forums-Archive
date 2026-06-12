---
title: "Hardy and NVIDIA Driver Issue"
date: 2008-04-30
forum: Multimedia Software
---

### Post by tmada on 2008-04-30
I have a 8600gts on hardy using the 2.6.22-14 kernel. I have tried using the hardware drivers application, installing the new 172...drivers off the nvidia site, and using envy ng to install nvidia drivers. Each time I have tried it has brought me back into a low resolution mode. 
Does anyone have any solutions that can help me out.
Thanks,

---

### Post by damis648 on 2008-04-30
Try downloading the official Nvidia driver: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
and select the 169.12 driver for your platform.

After you have downloaded it, move it to /home and rename it to nvid.run.

Now, close all applications and press ctrl+alt+f1 to drop back to terminal.

Now to stop the X server type

```
sudo /etc/init.d/gdm stop
```

then just run

```
sudo sh ./nvid.run
```

and follow the directions to install the driver. Let it automatically reconfigure the xorg.conf.

EDIT: I FORGOT!! FIRST REMOVE THE nvidia-glx-gew package FROM THE TERMINAL AFTER YOU CLOSE THE X SERVER!

run from the shell

```
sudo apt-get remove nvdia-glx-new
```

---

### Post by vexorian on 2008-04-30
My advice would be that it is better to shoot yourself in the foot than to install nvidia drivers from their site unless it is TERRIBLY necessary, and if you do everything will be broken from the time you did. For example, youi'll have to recompile the driver everytime the kernel is updated - unless you want Xorg crashes...

---

### Post by damis648 on 2008-04-30
It is not terribly important, for me at least, to upgrade my kernel. I just wait until the next Ubuntu release for a kernel upgrade. Also, the Nvidia drivers from the site are not terribly bad to install. I have installed them twice and it still works.

---

### Post by tmada on 2008-04-30
ok so when it makes it into the installer 
it first lets me know that there was no matching precompiled kernel interface.
Next it then tells me CC version failed "The kernel version (gcc4.1) does not match the compiler (gcc4.2)...and asks me if I would like to continue. I hit abort to ask further advice.

---

### Post by damis648 on 2008-04-30
search "g++" on synaptic and install it and try again.

---

### Post by damis648 on 2008-04-30
and its fine to let it compile its own kernel module.

---

### Post by tmada on 2008-04-30
I reinstalled and same issue. I even went through with the installation and ended up with low resolution. Just got done uninstalling the drivers and changing the xorg file back to the the orig

---

### Post by damis648 on 2008-04-30
hmm interesting...

---

### Post by tmada on 2008-04-30
Does anyone else have any ideas? Stuck. I would be using the 2.6.24-16 kernel but I cannot get my wireless working on it using ndiswrapper. I switched down and was able to get ndiswrapper installed. I am not able to get my vid card drivers installed on the 2.6.22 kernel.

---

### Post by arch stanton on 2008-04-30
no solution here .. i've been f*&%ing around with this since the 24th and still no 3d ..i'm ready to scuttle this install and go back to 7.10, except that I made the mistake of upgrading a perfectly good ubuntu installation .. I should have known better .. anyway i'll mess round tonight and then I give up :(

---

### Post by arch stanton on 2008-04-30
ok finally made it work 


1) checked this blacklist file .. nvidia was blacklisted ..

sudo nano /etc/modprobe.d/blacklist-restricted


2) realized my grub boot menu was fubared ..was loading kernel 2.6.20.16 generic
instead of 2.6.24.16 generic

so simple eh ??  yeah right!

---

### Post by damis648 on 2008-05-03
for the record, i have upgraded my kernel and reinstalling the nvidia drivers was not difficult. I just had to boot up recovery with the new kernel and run the installer again. Luckily i didnt delete it :).

---

### Post by vexorian on 2008-05-05
Does anyone know if the updated kernel and restricted modules from the repos got the nvidia issues fixed? I would like to get rid of nvidia site's driver asap.

Edit: I didn't notice the kernel and similar updates came from hardy proposed...

---

### Post by OpenFish on 2008-05-05
i have this card and shouting ur self in the foot would be a positivly enjoyable compared to setting it up

i use etch by the way and i dont have x when i netinstall so be thankfull of ur low resilution  --> i must say the pain is worth it beryl is the best on a 22" mointor with a good card

i dont know the code tags sorry

first use 

  #apt-get install build-essential

get the kernel name 

  $uname -r

get the kernal headers

  $apt-cache search $(uname -r)

install the appropriate pacige

stop gdm

  #/etc/init.d/gdm stop  (i think u need root??)

(there wont be any windows now so copy the location of wget (ctl+C) or do that first i dont notice as i havent had x at all and have copy the hole damn thing out (ctl+sft+C/V in terminal ctl+C stops what ever ur up to ) )

remove this i foget why but my little black book of expiriance tells me to (i atualy have real blank black book where i write down the trikes to install or compile complicated stuff) (may work with out)

  #apt purge nvidia-glx

get the driver  (this is for any 64-bit Linux or Unix mechanic, 32bit users look on the site)

  #wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run)

and run it 

  #./NVIDIA-Linux-x86_64-169.12-pkg2.run

then get gnome back

    #/etc/init.d/gdm start  (i think u need root??)

but beryl wont work well until u mess with the the xorg config file

i think thats every thing??

good luck

---

