---
title: "network not working"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by Daboo on 2006-06-02
I've got an onboard nvidia nforce ethernet adapter, which was working fine in breezy, however it's not working in Dapper for some reason. I tried disabling eth0 and reenabling it, but it fails with a DHCP error message every time I try. So far I've tried:

1) [http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)
2) physically removing another ethernet card I had installed

Any ideas? :-k Back to XP for now...:(

---

### Post by s31523 on 2006-06-02
Try installing Network Manager via synaptic then edit your /etc/network/interfaces file to comment out (or remove) everything except references to loop back (lo).  Then give a good ol re-boot.

Maybe Network Manager will manage it better?

---

### Post by h3h_timo on 2006-06-02
Yeah, ive heard of problems with the nforce adapter, im sorry my way didnt work for you, it sucks to not have internet access. You could try this:

"You may need to specify a gateway for that setup to work (mine didn't work until I did so). Here's what that part of my /etc/network/interfaces looks like:

auto eth0
iface eth0 inet dhcp
gateway 192.168.1.1

Also, I had a lot of trouble with the forcedeth driver, but after installing the official nForce drivers from Nvidia's site, everything worked fine."

I got this from [here]("https://launchpad.net/distros/ubuntu/+bug/42608").

Good luck tho, keep trying and eventually you will figure it out.

---

### Post by wuch on 2006-06-03
I have an onboard nvidia nforce ethernet adapter as well. The problem and solution is described in this thread.

[http://ubuntuforums.org/showthread.php?t=186848](http://ubuntuforums.org/showthread.php?t=186848)

---

### Post by Belarios on 2006-06-03
What about if you physically pull the plug out of the power supply for 15 seconds and then boot into linux?

If that solves your problem, check here:

[http://ubuntuforums.org/showthread.php?p=1083320#post1083320](http://ubuntuforums.org/showthread.php?p=1083320#post1083320)

---

### Post by Daboo on 2006-06-03
I tried the power thing, but that had no effect. The problem is that once I hit disable, I can't even reenable it. It was never working at all, not even intermittently. I tried replacing the forcedeth.ko anyways to no avail.

I tried installing nvidia's drivers but I'm getting stuck. I got a message saying I needed binutils installed, and if it is, "ld" must be in the path. Well, I found that in /bin, but it was ld_static. I symlinked ld to ld_static, then it complained about "objcopy." However, the version of binutils installed only has ld apparently. Not sure where to go from here.

---

### Post by Daboo on 2006-06-04
Anyone?

---

### Post by vanlol on 2006-06-05
Insert your dapper cd and go to synaptic
Search for binutils and install it

You'll be able to start up the nvidia package but I bet you'll get stuck at 
[http://members.optusnet.com.au/melonfresh/Screenshot6.png](http://members.optusnet.com.au/melonfresh/Screenshot6.png)
[http://members.optusnet.com.au/melonfresh/Screenshot7.png](http://members.optusnet.com.au/melonfresh/Screenshot7.png)

I don't know what to do here so maybe someone else does.. :) Also networkless here with my nvidia ethernet

---

### Post by Tombius on 2006-06-05
I had the same problem, and the shut down and turn off the power source just worked. before messing up the kernel, why dont you try again and shut down, turn the power source switch to off, wait something like 40 seconds turn on the power source switch, turn on your machine, select Ubuntu in grub (if sharing the disk with XP perhaps), and see if that works. 

It worked for me, i happy because version 5.04 didnt support SATA HDD 5.10 Didnt support Nvidia 6100/Nforce430, 
and i tought dapper 6.06 didnt support the ethernet card but that is not true.

Try it again just one more time. 

I am just as noob as hell and still not as naive to not know that fancy solutions are 100% screwups 80% of the time.

---

### Post by Daboo on 2006-06-05
[QUOTE=vanlol]Insert your dapper cd and go to synaptic
Search for binutils and install it

You'll be able to start up the nvidia package but I bet you'll get stuck at 
[http://members.optusnet.com.au/melonfresh/Screenshot6.png](http://members.optusnet.com.au/melonfresh/Screenshot6.png)
[http://members.optusnet.com.au/melonfresh/Screenshot7.png](http://members.optusnet.com.au/melonfresh/Screenshot7.png)

I don't know what to do here so maybe someone else does.. :) Also networkless here with my nvidia ethernet[/QUOTE]

Thanks, I'll give this a shot after work today.

---

### Post by Daboo on 2006-06-05
Yup, got the same thing. How do I install the source?

---

### Post by Belarios on 2006-06-05
You don't need to install the full kernel source.  Just installing the headers will be enough.

```
sudo aptitude install linux-headers-2.6.15-23
```

---

### Post by Daboo on 2006-06-05
[QUOTE=vanlol]Insert your dapper cd and go to synaptic
Search for binutils and install it

You'll be able to start up the nvidia package but I bet you'll get stuck at 
[http://members.optusnet.com.au/melonfresh/Screenshot6.png](http://members.optusnet.com.au/melonfresh/Screenshot6.png)
[http://members.optusnet.com.au/melonfresh/Screenshot7.png](http://members.optusnet.com.au/melonfresh/Screenshot7.png)

I don't know what to do here so maybe someone else does.. :) Also networkless here with my nvidia ethernet[/QUOTE]

I got past this and got the driver installed, but I'm stuck at the configuration. Anyways here's how to at least get it installed:

install these two packages (sudo dpkg -i file.deb):

[http://packages.ubuntulinux.org/dapper/devel/linux-headers-2.6.15-23-386](http://packages.ubuntulinux.org/dapper/devel/linux-headers-2.6.15-23-386)
[http://packages.ubuntulinux.org/dapper/devel/build-essential](http://packages.ubuntulinux.org/dapper/devel/build-essential)

These are also on your Dapper cd. 

then install drivers with:
sudo sh NVIDIA-blah-long-file-name --kernel-source-path /usr/src/linux-headers-2.6.15-23-386 

I think the above path is right, but double check it.

Now the problem is, I don't know how to configure it. Poked around in nvidia's readme... I tried adding 'nvnet'  to /etc/modules, but that didn't do anything. I also tried adding 'alias eth0 nvnet' to /etc/modprobe.d/nvidia-something-other. No joy there either. Not sure what I'm doing, can someone help?

---

### Post by Daboo on 2006-06-06
Can anyone please help me out? I'm almost there, I just need to know how to configure it.

---

### Post by cracker on 2006-07-22
I have this same problem. I had no eth0, so I installed nforce drivers. After installing all the sources and gcc and all that, it successfully ran, but it still doesn't work, and I have no idea how to get it to work. I tried loading the module, but still no eth0.

---

### Post by Daboo on 2006-07-22
Yea unfortunately this is the only thing keeping me from using Ubuntu. I never did find a solution to this :/

---

