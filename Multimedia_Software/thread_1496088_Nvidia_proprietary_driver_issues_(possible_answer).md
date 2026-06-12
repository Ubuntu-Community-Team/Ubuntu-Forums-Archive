---
title: "Nvidia proprietary driver issues (possible answer)"
date: 2010-05-28
forum: Multimedia Software
---

### Post by pyrr on 2010-05-28
I wanted to share a possible solution to an nvidia proprietary driver issue.

I just performed a clean install of Kubuntu Lucid earlier this week after deciding it was time to upgrade from Hardy. Pretty much everything worked, until I attempted to install the proprietary NVIDIA driver.

OS details: Kubuntu 10.04 x64 Kernel 2.6.32.22.

What happened when I tried to install the proprietary nvidia-current package was simply that it didn't work. I could open the nvidia utility, it would say the driver was not in use. Attempts to force the issue by running nvidia-xconfig would render the X server unable to start, which gave me some quality time in a shell console with APT or restoring the xorg.conf file from backup. Trying to compile and install the driver from nvidia also wasn't working out so well.

I think the issue boiled-down to the install presumably attempting to upgrade the kernel during initial install from CD, but not doing so completely. I had all the appropriate 2.6.32.22 kernel and header packages, but GRUB was apparently still booting to the 2.6.32.21 kernel (which had no headers or anything) and not giving options to boot to the upgraded kernel.

How I fixed this was to remove all packages related to the 2.6.32.22 kernel via APT, then remove all the 2.6.32.21 kernel packages. That second operation triggered the 2.6.32.22 kernel to be reinstalled, and GRUB to be configured correctly to boot to it. At that point, I reinstalled nvidia-current, and it worked. I tried this after determining I was on the 2.6.32.21 kernel, and had no option to boot to the 2.6.32.22 one.

Your mileage may vary. In retrospect, I probably could've fixed it by fixing GRUB to boot to the current kernel. This appears to be a consistent issue, as I reinstalled at one point, just to start over, and went through the same thing again.

I suspect the driver I obtained from the nvidia website and patched (due to issues it has with recent kernels) might work now that I'm booting to the correct kernel with headers, but I think I'll save that for another time since nvidia-current is working great for me at the moment.

I'd be curious to know how my hypothesis bears out with others' experiences and experimentation with these drivers.

---

### Post by WinterRain on 2010-05-28
If I'm not mistaken, you'll have to reinstall the nvidia drivers if you update your kernel.

---

### Post by pyrr on 2010-05-30
> **WinterRain said:**
> If I'm not mistaken, you'll have to reinstall the nvidia drivers if you update your kernel.

Indeed, they do have to be recompiled if you're using the version from nvidia's website (and that needs to be patched to work correctly on Lucid). 

I'm not sure that's the case nvidia-current though; yes, on some level, the driver would have to be upgraded to match the new kernel, but I'd hope the package manager would catch the video driver upgrade along with the kernel upgrade to make sure they are compatible, without the end user having to perform that action manually. In this case, something appears to be wrong with the nvidia-current package, in that it fails to work, which may be due to it not being appropriate for the 2.6.32.21 kernel. That would definitely be the case if the driver packages are precompiled, and happen to be compiled for a different kernel than is running.

---

### Post by ankspo71 on 2010-05-30
> **pyrr said:**
> 
What happened when I tried to install the proprietary nvidia-current package was simply that it didn't work. I could open the nvidia utility, it would say the driver was not in use.

Hi, I know that this type of thing can happen if there is nothing in the apt-cache when a distribution is first installed. Offhand, I think two distributions effected are Crunchbang and Kubuntu, but I'm not sure. What happens is when the hardware manager starts, it searches the offline apt cache for available packages to install, and if there is none in there, then it will say no drivers are is in use (or something like that). I've noticed that the hardware manager will only scan for hardware once per boot session too. So this could pose a problem with making people think there are no drivers available. What needs to be done in this case is to refresh/reload the repositories, to give the apt cache a list of applications to choose from, then it will be necessary for person to restart the system so the hardware manager will be able to scan again. On the other hand, if the update manager automatically scans for updates  first, it won't ever be a problem because the update manager actually goes online to check for updates (I think), which downloads the necessary info into the apt cache. I think this is why there is such a long delay set for the hardware manager to automatically scan for drivers.

---

### Post by pyrr on 2010-05-30
> **ankspo71 said:**
> Hi, I know that this type of thing can happen if there is nothing in the apt-cache when a distribution is first installed. Offhand, I think two distributions effected are Crunchbang and Kubuntu, but I'm not sure. What happens is when the hardware manager starts, it searches the offline apt cache for available packages to install, and if there is none in there, then it will say no drivers are is in use (or something like that). I've noticed that the hardware manager will only scan for hardware once per boot session too. So this could pose a problem with making people think there are no drivers available. What needs to be done in this case is to refresh/reload the repositories, to give the apt cache a list of applications to choose from, then it will be necessary for person to restart the system so the hardware manager will be able to scan again. On the other hand, if the update manager automatically scans for updates  first, it won't ever be a problem because the update manager actually goes online to check for updates (I think), which downloads the necessary info into the apt cache. I think this is why there is such a long delay set for the hardware manager to automatically scan for drivers.

I did encounter this issue too, when I attempted to use Jockey. I just installed the nvidia-current driver through APT when it wouldn't detect the video adapter. It didn't seem to matter how many times I rebooted, it simply wouldn't detect the hardware and make the proprietary driver packages available automatically.

I still don't know why I was getting stuck booting to an old kernel with no way to select the newer kernel in GRUB, or the precise reason nvidia-xconfig was breaking the GUI when I installed it on the old kernel which was loading. 

I just performed an identical install on a nearly identical machine, and had far fewer issues. I simply upgraded the kernel to 2.6.32.22, confirmed that Kubuntu had booted into that kernel (the GRUB menu I'm accustomed to if I have multiple kernels available to boot to still wasn't appearing though), and installed nvidia-current. I had no broken GUI after running nvidia-xconfig at that point, and the driver was loading properly. Something has either changed, or I was just really unlucky last week.

---

