---
title: "Dapper, AMD64, Nvidia - No 3D Accel."
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by be_placid on 2006-06-04
Ok, I know before you read this your probably sick of these sort of threads. The truth is though, I have searched these forums, google and had assistance from people more experienced than me, and I have still yet to find a solution ](*,) 

My problem is this:
After doing an upgrade from breezy to dapper last week, I realised a couple of days ago that I didn't in fact have 3D acceleration working. So, I scoured apt for nvidia drivers and have installed (in no particular order, and bear in mind that one removes the other etc):
[LIST]
[*]nvidia-kernel-source
[*]nvidia-legacy-kernel-source
[/LIST]
Now, neither of these have had any luck. What i've concluded, through many tries, is that Xorg has a problem finding the 'nvidia' module. modprobe'ing this module runs fine, but starting X (/etc/init.d/gdm start or startx) still doesn't find it, even after a shutdown -r now! :(
However, before I let you post, i'll give you some background info. as to what i've done, and some system information.

I have run through:
[LIST]
[*][https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)
[*]tseliot's guide (sorry, no URL): using Method 2
[*][http://www.ubuntuforums.org/showthread.php?t=186294](http://www.ubuntuforums.org/showthread.php?t=186294) (specifically the post owners last post on page 2, both links)
[/LIST]
I have used the default binary installer from nvidia.com (namely: NVIDIA-Linux-x86_64-1.0-8762-pkg2.run), changed xorg.conf MANY times to point to the nvidia module (under device) and added a "Load "nvidia"" section under modules. However, nothing has worked. I am really annoyed :\

I would really appreciate any opinions, suggestions, links or otherwise
Thanks in advance.

**System Details**
**Proc.:**AMD64
**RAM**:1024MB (1GB)
**Graphics Chip:**NVidia GeForce 440 Go
**Distro:**Ubuntu Dapper 6.06 LTS "Dapper Drake"

Here are my current xorg.conf,Xorg.0.log, dmesg | grep -i nvidia and lspci -vvv output:
[http://beplacid.com/~placid/dd/xorg.conf](http://beplacid.com/~placid/dd/xorg.conf)
[http://beplacid.com/~placid/dd/Xorg.0.log](http://beplacid.com/~placid/dd/Xorg.0.log) (please bear in mind I am currently under the nv module, so you might not find and error output)
[http://beplacid.com/~placid/dd/nvidia_dmesg](http://beplacid.com/~placid/dd/nvidia_dmesg)
[http://beplacid.com/~placid/dd/lspci](http://beplacid.com/~placid/dd/lspci)


Again, thank you in advance,


Alex

---

### Post by be_placid on 2006-06-04
Well, after writing this thread I checked my email, in which was a person on my local LUG (Linux User Group) that was having similar issues. Someone had replied to that post with a solution, which worked brilliantly, so now I have the drivers working.
Below is the solution for anyone that is having problems:
> The latest NVIDIA "kernel" should have been the latest NVIDIA "drivers"
from the NVIDIA website I guess? And you should have:

        NVIDIA-Linux-x86-1.0-8762-pkg1.run

This is the first version with proper support for Xorg 7.0, IIRC.

This is good! But uninstall the drivers:

        # sh ./NVIDIA-Linux-x86-1.0-8762-pkg1.run --uninstall

With Xorg 7, a lot of the paths changed.

Do the following:

        # cd /usr/X11R6/lib
        # mv modules modules.old
        # ln -s /usr/lib/xorg/modules .

Also check that /usr/X11R6/bin is a symlink to /usr/bin. If not:

        # cd /usr/X11R6
        # mv bin bin.old
        # ln -s ../bin .

Now install the NVIDIA drivers again:

        # sh ./NVIDIA- Linux-x86-1.0-8762-pkg1.run


---

### Post by JoWilly on 2006-06-04
Why do you want to install the nvidia drivers from source ?

The driver is included in linux-restricted-modules. Check that it matches your kernel version in synapitc.

You only need linux-restricted-modules and nvidia-glx, and replace nv with nvidia in xorg.conf.

On reboot, some modules are sometimes not detected.

A "sudo depmod -a" fixes that.


Edit: there's absolutely no need for Load "nvidia" in xorg. Remove it.
Edit2: no need for the binary driver from nvidia.com; as I said the driver is in linux-restricted-modules. I you install a fresh system you only need to install nvidia-glx and replace nv with nvidia in xorg.conf ( for that you can also do "sudo nvidia-glx-config enable")

---

### Post by be_placid on 2006-06-04
[QUOTE=JoWilly]Why do you want to install the nvidia drivers from source ?

The driver is included in linux-restricted-modules. Check that it maches your kernel version in synapitc.

You only need linux-restricte-modules and nvidia-glx, and replace nv with nvidia in xorg.conf.

On reboot, some modules are sometimes not detected.

A "sudo depmod -a" fixes that.[/QUOTE]
Here's why:
```
alex@murtagh:~/el2_cvs/elc$ apt-cache search linux-restricted-modules
avm-fritz-kernel-source - AVM Fritz! binary kernel module source
fglrx-kernel-source - ATI binary kernel module source
nvidia-kernel-source - NVIDIA binary kernel module source
nvidia-legacy-kernel-source - NVIDIA binary 'legacy' kernel module source
```
And similarly:
```
alex@murtagh:~/el2_cvs/elc$ apt-cache search nvidia-glx
nvidia-kernel-source - NVIDIA binary kernel module source
nvidia-legacy-kernel-source - NVIDIA binary 'legacy' kernel module source
```

Even with these installed, it still wasn't finding the 'nvidia' module. However I didn't try the depmod -a (just a depmod), so that might help others.

Thanks for your reply,

Alex

---

### Post by tseliot on 2006-06-04
Perhaps you saw only my guide for Breezy instead of the one for Dapper.
Please try it:
[http://ubuntuforums.org/showthread.php?t=139264]("http://ubuntuforums.org/showthread.php?t=139264")

and BTW who did tell you that you have to install the source???

---

### Post by JoWilly on 2006-06-04
[QUOTE=be_placid]Here's why:
```
alex@murtagh:~/el2_cvs/elc$ apt-cache search linux-restricted-modules
avm-fritz-kernel-source - AVM Fritz! binary kernel module source
fglrx-kernel-source - ATI binary kernel module source
nvidia-kernel-source - NVIDIA binary kernel module source
nvidia-legacy-kernel-source - NVIDIA binary 'legacy' kernel module source
```
And similarly:
```
alex@murtagh:~/el2_cvs/elc$ apt-cache search nvidia-glx
nvidia-kernel-source - NVIDIA binary kernel module source
nvidia-legacy-kernel-source - NVIDIA binary 'legacy' kernel module source
```

Even with these installed, it still wasn't finding the 'nvidia' module. However I didn't try the depmod -a (just a depmod), so that might help others.

Thanks for your reply,

Alex[/QUOTE]


From the 2 outputs I see only 1 thing : nvidia-glx and linux-restricted-modules are not installed.

Also, why do you install fglrx if you use nvidia ?

---

### Post by be_placid on 2006-06-04
> **JoWilly]Edit: there's absolutely no need for Load "nvidia" in xorg. Remove it.
Edit2: no need for the binary driver from nvidia.com said:**
> 
Firstly, the only reason I added the Load "nvidia" is due to a suggestion from a friend, either way, its working now.
Secondly, I couldn't find 'nvidia-glx-config' to enable it in the first place.

[QUOTE=JoWilly]From the 2 outputs I see only 1 thing : nvidia-glx and linux-restricted-modules are not installed.

Also, why do you install fglrx if you use nvidia ?
I didn't install the fglrx package, my quote output above was to prove what a search in apt for 'nvidia-glx' and 'linux-restricted-modules' produced, i'm well aware that I don't need to install the ATI based modules.

[QUOTE=tseliot]Perhaps you saw only my guide for Breezy instead of the one for Dapper.
Please try it:
[http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)

and BTW who did tell you that you have to install the source???[/QUOTE]
...If you read my quoted output, you'll see that both 'nvidia-glx' and 'linux-restricted-modules' BOTH point to that 'kernel-source' package, and thus the reason why I installed it.

ATI users can also use my posted solution, the only difference is that you will need to run 'sh /usr/share/fglrx/fglrx-uninstall.sh' instead of the NVIDIA based install/uninstall package.

---

### Post by JoWilly on 2006-06-04
Good to hear it's now working for you :)

---

### Post by be_placid on 2006-06-04
Thank you :)
I hope my posted solutions can help others too

---

### Post by tseliot on 2006-06-05
[QUOTE=be_placid]...If you read my quoted output, you'll see that both 'nvidia-glx' and 'linux-restricted-modules' BOTH point to that 'kernel-source' package, and thus the reason why I installed it.[/QUOTE]
Ok, I'll explain you the function of nvidia-kernel-source:
1) when you compile a new kernel you can build it with its nvidia modules thanks to "nvidia-kernel-source" (see Method 3)

2) or, if you use Modules assistant, you will need "nvidia-kernel-source" in order to compile your modules.

If you use Method 1 or Method 2 "nvidia-kernel-source" is useless, just like keeping the source code without compiling it.

---

### Post by be_placid on 2006-06-05
[QUOTE=tseliot]Ok, I'll explain you the function of nvidia-kernel-source:
1) when you compile a new kernel you can build it with its nvidia modules thanks to "nvidia-kernel-source" (see Method 3)

2) or, if you use Modules assistant, you will need "nvidia-kernel-source" in order to compile your modules.

If you use Method 1 or Method 2 "nvidia-kernel-source" is useless, just like keeping the source code without compiling it.[/QUOTE]
I'm sure your right. What has annoyed me about Dapper is that (for whatever reason) this (rather famously annoying) must-do when installing a GNU/Linux system was made even more complicated.
So what packages provide the nvidia-glx, tseliot?

---

### Post by tseliot on 2006-06-05
[QUOTE=be_placid]I'm sure your right. What has annoyed me about Dapper is that (for whatever reason) this (rather famously annoying) must-do when installing a GNU/Linux system was made even more complicated.
So what packages provide the nvidia-glx, tseliot?[/QUOTE]
I find Method 1 quite easy.

nvidia-glx has the following dependencies:
linux-restricted-modules-2.6.15-23-386 linux-restricted-modules-common nvidia-kernel-common

---

### Post by be_placid on 2006-06-07
....Well, the reason I didn't use method 1 is for the following reason:
(to quote yourself)
[quote=Instructions @ doc.gwos.org/index.php/Latest_Nvidia_Dapper]**METHOD 1** It is the usual (and easiest) way to install the Nvidia drivers. It allows you to install nvidia driver 8762 OR 7174, i.e. the Legacy driver that you need ONLY IF your graphic card belongs to the list in the "NOTES SECTION", which you will find near the end of the guide.[/quote]

[quote=Notes Section @ doc.gwos.org/index.php/Latest_Nvidia_Dapper]
chip name Device PCI ID
 ------------------------------- ------------------------------- 
RIVA TNT 0x0020 
RIVA TNT2/TNT2 Pro 0x0028 
RIVA TNT2 Ultra 0x0029 
Vanta/Vanta LT 0x002C 
RIVA TNT2 Model 64/Model 64 Pro 0x002D 
Aladdin TNT2 0x00A0 
GeForce 256 0x0100 
GeForce DDR 0x0101 
Quadro 0x0103 
GeForce2 GTS/GeForce2 Pro 0x0150 
GeForce2 Ti 0x0151 
GeForce2 Ultra 0x0152 
Quadro2 Pro 0x0153[/quote]

I used method two as I was installing the 87xx series drivers (i.e. the latest, NOT legacy) and furthermore, my chipset is GeForce4 440 Go

---

### Post by tseliot on 2006-06-07
[QUOTE=be_placid]....Well, the reason I didn't use method 1 is for the following reason:
(to quote yourself)




I used method two as I was installing the 87xx series drivers (i.e. the latest, NOT legacy) and furthermore, my chipset is GeForce4 440 Go[/QUOTE]
It's just a coincidence but (at least for now) the driver you can install with Method 1 is also the latest (8762).


Legacy driver (7174) is, as you know, for the cards in that list.

---

