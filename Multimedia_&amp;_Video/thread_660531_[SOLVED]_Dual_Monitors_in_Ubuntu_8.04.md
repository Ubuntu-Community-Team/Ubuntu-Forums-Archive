---
title: "[SOLVED] Dual Monitors in Ubuntu 8.04"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by kyleabaker on 2008-01-06
I had some trouble with video drivers in Ubuntu 7.10 (x64) a while back so I reinstalled 7.04. Now I've installed 8.04 (clean install, x64) and it seems to be running fine for now. I just need to get my dual monitors working. Searching the forums and googling didn't provide any answers for me.

In 7.04 and 7.10 I was using restricted drivers for NVidia, but upon installing 8.04 I was not prompted to enable those restricted drivers. So now I basically don't know how to setup my 2nd monitor as a TwinView or just extended workspace.

In the 7.x versions I configured my screens using..
```
sudo nvidia-settings
```
..however, this doesn't seem to be available without the restricted drivers (I suppose).

"System->Administration->Screens and Graphics" is not listing any screens at all and I cannot figure out how to set it up through that. Could someone please help?

Thanks in advanced.

---

### Post by zero-9376 on 2008-01-06
do you have nvidia-glx or nvidia-glx-new installed, these are the nvidia drivers, nvidia-settings is also included in there.

---

### Post by kyleabaker on 2008-01-06
@zero-9376
Ok, so I checked in Synaptic Package Manager and it looks like it didn't setup either. I guess it is just running on generic drivers.

Which ones should I use? or would you suggest? nvidia-glx or nvidia-glx-new?

Thanks for the quick response.

---

### Post by zero-9376 on 2008-01-06
i think it depends on your graphics card. anything like a geforce 2 or mx400 uses nvidia-glx-legacy, while newer cards (7x00 or 8x00) require the nvidia-glx-new but older cards can use it as well. i think nvidia-glx is for people who have problems with the newest drivers. restricted driver manager recommended nvidia-glx-new for my fx5200 if i recall correctly.

---

### Post by kyleabaker on 2008-01-06
ok, thanks. I've installed the new drivers. I'll try them out for a while and hope that they don't cause problems like I was having in 7.10. Thanks for your help!

---

### Post by kyleabaker on 2008-01-07
Well, my xorg file went crazy so I started over. This time I've installed all of the updates and installed the restricted files from Add/Remove.

Now I can't get nvidia-glx-new enabled and nvidia-settings won't work for some reason. I had it working before, but it quit working somewhere around installing the Restricted stuff from Add/Remove.

Now when I run "nvidia-xconfig" (as suggested by the nvidia-settings app when I try to run it) my xorg file becomes corrupt and I have to start in basic mode or whatever. How do I get my nvidia drivers installed!?

EDIT:
Also, the Restricted Drivers Manager won't launch because it says I need to install linux-restricted-modules-2.6.24-3-generic...but that is already installed according to the Synaptic Manager...?

---

### Post by kyleabaker on 2008-01-07
Anyone? I'm still having a lot of trouble with this. Restricted Driver Manager isn't working. Maybe if I can get that working then it will enable the nvidia driver.

Please help!

---

### Post by kyleabaker on 2008-01-07
"System->Administration->Restricted Drivers Manager" produces the following error:
```
You need to install the package
  linux-restricted-modules-2.6.24-3-generic
for this program to work.
```

In Synaptic Package Manager it shows "linux-restricted-modules-2.6.24-2-generic", however, when I right click the item and click properties it says:
> Available versions:
2.6.24.3-2.9 (hardy)

I thought that installing this module would fix the Restricted Drivers Manager, but it still gives me the same error message. What to do?

---

### Post by zero-9376 on 2008-01-07
the only thing i can think of is to completely remove the restricted modules and nvidia components using synaptic and then reinstall.

however just having a look at the ubuntu package search it doesn't appear as though there are restricted modules which match the latest kernel. you may have better luck booting into the older kernel.

-----------------------------------------------------------------------------------

Package linux-restricted-modules

    * hardy (metapackages): Generic Linux restricted modules. [restricted]
      **2.6.24.3.3**: amd64 i386

but the latest modules are actually :

Package linux-restricted-modules-2.6.24-2-generic

    * hardy (misc): Non-free Linux 2.6.24 modules on x86/x86_64 [restricted]
      **2.6.24.3-2.9**: amd64 i386

And this is the latest kernel:
Package linux-image-2.6.24-3-generic

    * hardy (base): Linux kernel image for version 2.6.24 on x86/x86_64
      **2.6.24-3.5**: amd64 i386

--------------------------------------------------------------------------

im not an expert at this stuff and have never run a development release myself so someone in the dev section may be better help but i do know that you need to have the same kernel and module versions in order for nvidia (and probably a lot of other stuff) to work.

hope this helps

---

### Post by kyleabaker on 2008-01-07
Thanks zero-9376. It was the upgraded kernel that caused the problems. Booting with the previous kernel fixed everything.

---

### Post by alex_mayorga on 2008-01-08
> **kyleabaker said:**
> "System->Administration->Restricted Drivers Manager" produces the following error:
```
You need to install the package
  linux-restricted-modules-2.6.24-3-generic
for this program to work.
```

In Synaptic Package Manager it shows "linux-restricted-modules-2.6.24-2-generic", however, when I right click the item and click properties it says:


I thought that installing this module would fix the Restricted Drivers Manager, but it still gives me the same error message. What to do?
Did you filed a bug report for this one?

I'm seeing this exact same problem myself.

Thanks,
Alex

---

### Post by kyleabaker on 2008-01-08
@alex_mayorga
I googled it and came up with a similar problem and it was suggested to not file a bug report for a couple to 3 days. They said it was usually that some information that the update manager fetches isn't all updated at the same time so some packages need to be updated, but there is no update listed for some items yet. It takes a little while to propagate I guess.

I just got a bunch of updates that fixed mine today. If it happens again then jsut boot up with the old kernel as zero suggested until the updates are available.

---

### Post by kyleabaker on 2008-01-18
I'm still unable to bootup with the latest kernel (*-4). I've had to use *-2 because I cannot get my video drivers installed correctly. I'm not sure what the problem is or how to fix it.

EDIT:
I've solved the problem by installing "linux-restricted-modules-2.6.24-4-generic". This fixed the problem where the Restricted Drivers manager would not open and I just enabled the driver through that and configured it all with nvidia-settings.

---

