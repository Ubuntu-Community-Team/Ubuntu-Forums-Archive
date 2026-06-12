---
title: "Have to reinstall nVidia-drivers after every reboot"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by DaVinciXL on 2007-04-14
Hi everyone.

After some trouble with the nvidia-packages for Feisty, I decided to try the drivers provided by nvidia.com.

Installation works without any errors and after restarting the XServer, everything works as expected.

BUT: Whenever I reboot the machine, Feisty boots into text mode because the kernel module cannot be loaded (the error message varies, this, however, is the most common error).
When I log in on the console and do nothing but reinstalling the driver using the same script as before, followed by a plain and simple "startx" everything's fine again.

Since I'm running Feisty on my laptop which I use in different places, I have to reboot it a couple of times per day. And it's quite annoying to reinstall those drivers 5-10 times per day.

Of course I could use "nv" instead of "nvidia". But neat little applications, such as GoogleEarth, won't work with nv. And since my laptop has quite a strange screen resolution everything looks... uhm... slushy...

Any ideas?

---

### Post by reclusivemonkey on 2007-04-14
What trouble were you having with the packaged nvidia drivers? I would suggest you stick to these, as they are compiled for the current kernel in the repos. I've not had a single problem under feisty; under Edgy they used to get out of sync but I think the devs have realised this and made sure there is always a working nvidia-glx available.

---

### Post by DaVinciXL on 2007-04-14
[http://ubuntuforums.org/showthread.php?t=406573](http://ubuntuforums.org/showthread.php?t=406573)

However, by now none of the nvidia-packages work for me at all.
Neither nvidia-glx, nor nvidia-glx-new... that's why I gave the drivers from nvidia.com a shot.

---

### Post by DaVinciXL on 2007-04-15
Guess I found out what's wrong...

Whenever I update the nvidia-packages, the old ones are not being removed. In combination with the Feisty kernel updates this seems to result in:
a) new kernel
b) new nvidia-glx package
c) old nvidia-kernel package - which, of course, is not compatible with the first two packages...

---

### Post by Fatmaxlim on 2007-04-15
I have the same problem, is it possible to completely remove old nvidia-packages?

---

### Post by reclusivemonkey on 2007-04-15
```

sudo aptitude search nvidia-kernel

```

Will show you which nvidia kernel packages you have installed. On my system this reads;

```

monkey@mother:~$ sudo aptitude search nvidia-kernel
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-1.0.9631          -                                           
v   nvidia-kernel-1.0.9755          -                                           
i   nvidia-kernel-common            - NVIDIA binary kernel module common files  
p   nvidia-kernel-source            - NVIDIA binary kernel module source

```

If you have any of the first four installed, maybe you could try

```

sudo apt-get remove nvidia-kernel-1.0.7184

```

---

### Post by Fatmaxlim on 2007-04-15
> **reclusivemonkey said:**
> ```

sudo aptitude search nvidia-kernel

```

Will show you which nvidia kernel packages you have installed. On my system this reads;

```

monkey@mother:~$ sudo aptitude search nvidia-kernel
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-1.0.9631          -                                           
v   nvidia-kernel-1.0.9755          -                                           
i   nvidia-kernel-common            - NVIDIA binary kernel module common files  
p   nvidia-kernel-source            - NVIDIA binary kernel module source

```

If you have any of the first four installed, maybe you could try

```

sudo apt-get remove nvidia-kernel-1.0.7184

```
 I have none of those packages instaled

---

### Post by reclusivemonkey on 2007-04-15
> **Fatmaxlim said:**
> I have none of those packages instaled

What does 

```

sudo aptitude search nvidia

```

show?

---

### Post by Fatmaxlim on 2007-04-15
root@maxim-desktop:/home/maxim# aptitude search nvidia
p   nvidia-glx                      - NVIDIA binary XFree86 4.x/X.Org driver    
p   nvidia-glx-dev                  - NVIDIA binary XFree86 4.x/X.Org driver dev
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-1.0.8776          -                                           
i   nvidia-kernel-common            - NVIDIA binary kernel module common files  
i   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr

---

### Post by reclusivemonkey on 2007-04-15
> **Fatmaxlim said:**
> root@maxim-desktop:/home/maxim# aptitude search nvidia
p   nvidia-glx                      - NVIDIA binary XFree86 4.x/X.Org driver    
p   nvidia-glx-dev                  - NVIDIA binary XFree86 4.x/X.Org driver dev
v   nvidia-kernel-1.0.7184          -                                           
v   nvidia-kernel-1.0.8774          -                                           
v   nvidia-kernel-1.0.8776          -                                           
i   nvidia-kernel-common            - NVIDIA binary kernel module common files  
i   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr

Try installing the nvidia-glx package. Have you used envy?

---

### Post by Fatmaxlim on 2007-04-15
> **reclusivemonkey said:**
> Try installing the nvidia-glx package. Have you used envy?
 I've installed glx package, but I still have the same problem.
No I havent used envy, actually, I dont even know what is it)

---

### Post by Tanoku on 2007-04-15
There are some serious issues with all the Nvidia packages on Festy.

I was having the same issues as you (nvidia-glx and nvidia-glx-new not installing, and the drivers from nvidia.com resetting after each reboot), and fixed them the "easy" way:

Just remove all the 2.6.20 kernel images (linux-image-2.6.20-15-386, linux-image-2.6.20-15-generic) and stick to 2.6.17-11 which seems to work flawlessly with the Nvidia.com drivers.

...If you are still having some trouble with the Nvidia.com drivers under 2.6.17, then I suggest completely wiping all the old Nvidia garabage and all the **** that came with Festy. Do so either manually or with Envy's textual interface.

In order to make Envy work under Festy you are going to need to do a little edit on one of the python files (the thing checks for Edgy, but if you comment out that check, the program runs OK under Festy).

Anyways, as stated above I had the same trouble as you and my system is working kind of flawlessly now. I know that downgrading the kernel is a bit "cheap", but hopefully when the release version of Festy comes out, I'll be able to upgrade again to 2.6.20. ^^

So, feel free to ask if you are having any more issues following these incredibly detailed guidelines (yes, I know, I'm a tad tired to type right now).

---

### Post by DaVinciXL on 2007-04-15
First of all: i have linux-image-2.6.20-15-386, linux-image-2.6.20-15-generic installed and by/for now working fine with nvidia-packages.

I reached this status by logging into the system on the console and doing a 
```
sudo apt-get remove nvidia*
```.

This, as you may have guessed *g*, removes all nvidia-packages from the system. However, it also will remove the package called linux-restricted-modules. But that doesn't really matter.

Then I rebooted my machine (better to be safe than sorry).

Of course it booted right up into console mode - since the driver "nvidia" was no longer installed.

I than searched for all linux images on the machine and deleted every single one of them - except for the latest.

Reboot again.

Than I did a
```
sudo apt-get install nvidia-glx-new
```
which installs the driver package (and of course all its dependencies) and also the package linux-restricted-modules in the "correct" version.

After these easy, though annoying, steps everything is now working as I expect it to work.

Even my WLAN-setup survived the procedure of un- and re-installing the restricted modules. ;)

---

### Post by ArgAthens on 2007-04-24
This fixed my problems...

---

### Post by DaVinciXL on 2007-04-24
Glad I could help...

---

