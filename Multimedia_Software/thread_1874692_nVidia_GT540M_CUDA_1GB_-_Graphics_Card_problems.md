---
title: "nVidia GT540M CUDA 1GB - Graphics Card problems"
date: 2011-11-03
forum: Multimedia Software
---

### Post by muzikayise on 2011-11-03
hi guys,

i'm noob in ubuntu, been trying to sort out graphics issue for a while but still not happy because i don't think its done correctly. 

I got an Asus N53SV-S1830X laptop recently with core i7 2670QM. I installed  ubuntu 11.10 and everything is working smoothly but when i navigate to  System Settings -> System Info -> the graphics comes up as  ''Unknown" when i boot into the "other" OS i can see the nVidia card  alongside with nVidia software and so on. 

i installed bumblebee but that didn't work so i installed ironhide, it looked like everything installed fine but not working well. i tried testing by running:
```
muzi@muzi-N53SV-LL:~$ optirun glxgears
```but i get the following errors:
```

 * Starting Ironhide X server ironhide                                          
ON Enabling NVIDIA card succeeded.
FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-12-generic/updates/dkms/nvidia_current.ko): No such device
.                                                                        [ OK ]
 * Stopping Ironhide X server ironhide                                   [fail] 

``` please will someone kindly assist regarding this issue?

thanks in advance

---

### Post by muzikayise on 2011-11-04
is there no one who may kindly assist?

even a simple link or two would be much appreciated?

---

### Post by papibe on 2011-11-04
Could you post the result of these command?
```
lspci | grep -i vga
```
Regards.

---

### Post by muzikayise on 2011-11-13
> **papibe said:**
> Could you post the result of these command?
```
lspci | grep -i vga
```Regards.

thanks buddy for kindly getting back to me, as requested herewith results from above command:

```

muzi@muzi-N53SV-LL:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev a1)

```

---

### Post by papibe on 2011-11-13
muzikayise: you have Nvidia [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is. And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that can either disable it, or simplify things by turning off the Nvidia card. Check your BIOS if you have any of those options.

I hope that helps,
Regards.

---

### Post by muzikayise on 2011-11-15
> **papibe said:**
> muzikayise: you have Nvidia [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux.
Wow this sucks... So Nvidia not supporting Optimus on Linux, but they support the "Other OS" not cool from Nvidia.

anyway thanks for your kind assistance, at least this clarifies things and now I know. The good news is the laptop is working fine so no worries, i will check out the other threads as suggested.

thanks again bro :D

---

### Post by erickjbc on 2011-11-23
hey muzikayise, I had the same problem on my laptop. I fixed it on ironhide doin a little trick I found investigating. Apparently on the configuration files there is an error... I fixed it doing the following:

1. Go into /etc/default/ironhide and open it
2. change IRONHIDE_ACPI_MODE=1 to IRONHIDE_ACPI_MODE=0
3. save file
4. reboot

it should work now

---

