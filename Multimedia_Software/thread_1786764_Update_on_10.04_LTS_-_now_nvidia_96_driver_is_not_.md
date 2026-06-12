---
title: "Update on 10.04 LTS - now nvidia 96 driver is not working anymore"
date: 2011-06-20
forum: Multimedia Software
---

### Post by kridybel on 2011-06-20
I have an older pc in my son's game room with xubuntu 10.04 LTS installed on it. It has an old Geforce2 Ti 200 64MB which is supported by the Nvidia 96 driver. The system is only connected to a acer H5360 beamer. Until I performed the updates for 10.04 on 18 June 2011 (**NOT** migrating to 10.10 or 11.04) the system was working fine with a 1440x900 resolution. Now I get error messages at start up, need to boot in safe mode and cannot get the nvidia96 to work properly anymore. 

```
sudo nvidia-xconfig
``` doesn't make the deal.

Only lower dead ugly resolutions  (1024x768, 800x600 and 640x480) are possible. Any suggestions? I would not need 3D acceleration but would like to have my 1440x900 resolution back again.

---

### Post by sikander3786 on 2011-06-20
Try reconfiguring the graphics. At your login screen, press Ctrl + Alt + F1 and login to the tty1 using your credentials. Then follow the commands below:

```
sudo mv /etc/[COLOR="Red"]X[/COLOR]11/xorg.conf /etc/[COLOR="Red"]X[/COLOR]11/xorg.conf.old
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot now
```

If that doesn't solve the problem, we might need to see the outputs of these commands.

```
lshw -c video
dpkg -l | grep nvidia
```

---

### Post by kridybel on 2011-06-20
Thanks for the prompt reply.

The output of the first code line is:
```
beheerder@beheerder-desktop:~$ sudo lshw -c video
[sudo] password for beheerder: 
  *-display               
       description: VGA compatible controller
       product: NV20 [GeForce3 Ti 200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 bus_master cap_list rom
       configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
       resources: irq:11 memory:ec000000-ecffffff memory:e4000000-e7ffffff(prefetchable) memory:e8000000-e807ffff(prefetchable) memory:e8080000-e808ffff(prefetchable)

```

Appearantly the nouveau driver got in there somewhere...

The second code line gave following result:
```
beheerder@beheerder-desktop:~$ dpkg -l | grep nvidia
ii  nvidia-173-modaliases                 173.14.22-0ubuntu11                               Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96                             96.43.17-0ubuntu1                                 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-96-modaliases                  96.43.17-0ubuntu1                                 Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common                         0.2.23                                            Find obsolete NVIDIA drivers
ii  nvidia-current-modaliases             195.36.24-0ubuntu1~10.04                          Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-settings                       195.36.08-0ubuntu2                                Tool of configuring the NVIDIA graphics driver

```

---

### Post by kridybel on 2011-06-20
Hi,

I deleted the nouveau driver via synaptic, removed the nvidia hardware drivers, reinstalled the nvidia driver and poof 1440x900 back again.

Thanks again for the lshw tip!

Will leave the post unsolved for a couple of days just in case...

---

### Post by tyronenguyen on 2011-11-02
```
This fixed my problem as well.  Ubuntu 32-bit 10.04.  
1) fresh install
2) auto update
3) install hardware drivers (choices were: specific version vs 'recommended', I picked 'recommended')
4) ERROR! could not start x --- some crazy error message
5) Asked me if I wanted low graphics mode, something else, something else
6) Clicked frantically and eventually dumped me to console.
7) tried 'startx' and up comes generic xfce desktop
8) Find this thread
9)  ???
10) profit!
```

wrapped in code tags since it turned my 8 + ) into a smiley

---

