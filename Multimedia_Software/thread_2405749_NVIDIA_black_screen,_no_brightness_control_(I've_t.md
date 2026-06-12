---
title: "NVIDIA black screen, no brightness control (I've tried everything)"
date: 2018-11-10
forum: Multimedia Software
---

### Post by bennywas on 2018-11-10
*EDIT: In case this thread remains silent, you can check [my repost on the nvidia forums]("https://devtalk.nvidia.com/default/topic/1043967/linux/410-396-390-amp-340-all-boot-to-black-screen-on-geforce-gt-650m-mac-edition/") regarding the black screen boot issue.*

My initial problem: After installing nvidia-driver-410 from [the official PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"), brightness control keys didn't work. I tried every solution listed in [this thread]("https://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver") and [this one]("https://forums.linuxmint.com/viewtopic.php?t=185148") including bash scripts; no luck. The subsequent problem: I wanted to completely uninstall the 410 driver to see if reinstalling it or trying older versions would work, so I ran 'dpkg -l | grep -i nvidia' from root shell and purged every package listed (following the advice of threads like [this]("https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely")). Now, every nvidia version I try to install (including 410 again) leads to a black screen on boot (not sure if this is related to purging those packages).** So, I have two problems:** First, installing any nvidia driver without a black screen; second, if I get one up and running, figuring out how to change the brightness. Here are my computer's details...

[FONT=courier new]uname --all && lsb_release --all[/FONT]
```
Linux benny-MacBookPro 4.15.0-38-generic #41-Ubuntu SMP Wed Oct 10 10:59:38 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic
```
[FONT=courier new]lspci -vnn | grep -i vga && sudo lshw -C video[/FONT]
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107M [GeForce GT 650M Mac Edition] [10de:0fd5] (rev a1) (prog-if 00 [VGA controller])
  *-display                 
       description: VGA compatible controller
       product: GK107M [GeForce GT 650M Mac Edition]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:48 memory:c0000000-c0ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:2000(size=128) memory:c1000000-c107ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:50 memory:c1400000-c17fffff memory:b0000000-bfffffff ioport:3000(size=64)
```

**Black screen issue:**
- First noticed several weeks ago when I first tried switching to nvidia, but I didn't document it well. From what I remember, I was using the Software & Updates > Additional Drivers GUI, selected nvidia-driver-390, rebooted, and couldn't change brightness. So I selected nvidia-driver-340, rebooted, and got a black screen. I had to switch to nouveau using GRUB's older kernel version option. Then I forgot about all this because it seemed like a lot of effort.
- Now it is happening again while using the abovementioned PPA, although it didn't happen initially. The first version I installed from the PPA was 410, rebooted, and couldn't change brightness. When no solution worked, I purged everything listed from 'dpkg -l | grep -i nvidia', ran autoremove, rebooted, and tried again. Now, trying to install 410 from the PPA boots to a black screen...and recovery mode's root shell prompt freezes before fully loading, so to purge nvidia I have to boot with the older kernel version, which works for some reason.
- Same thing with 396, 390, and 340. (Slight difference: the root shell prompt of one of those versions *did* work, but I can't remember which.) Trying to install 304 returns "unmet dependencies" for xorg-video-abi-* and xserver-xorg-core.
- Those are all the drivers listed in 'ubuntu-drivers list'. I haven't tried any in-between versions, but I will if you think it'll help.

**No brightness control issue: ***(originally posted [here]("https://ubuntuforums.org/showthread.php?t=2405281") but no replies)*
- On nvidia 410 (unconfirmed with other versions), brightness is stuck very low, I assume because that's the default boot brightness. Keys can't control it.
- As you see, I have hybrid graphics / dual GPUs; I hear nvidia is especially difficult with these computers.
- I'm told brightness can be adjusted from the NVIDIA X Server Settings GUI, but found no option for brightness there. I'm also told that the GUI is supposed to include a "PRIME Profiles" tab, which I don't have. Opening the GUI from terminal returns "Is Prime supported? no" or similar.
- nvidia-settings does not include a BacklightBrightness attribute.
- Many solutions I found online assumed older versions of X with different conf files in different places, although I ended up trying all of them just in case.
_Things I tried (inspired by [this thread]("https://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver")):_
- Modified  '/usr/share/X11/xorg.conf.d/10-nvidia.conf'. The file previously only included an "OutputClass" section. I added a "Device" section with my BoardName and the "RegistryDwords" "EnableBrightnessControl=1" option.
- Added a similar conf file to that same directory. I created a 10-nvidia-brightness.conf with the same "Device" section, which I also tried renaming 20-nvidia-brightness.conf.
- Ran nvidia-xconfig (returns 'Warning: Package xorg-server was not found in the pkg-config search path. Perhaps you should add the directory containing 'xorg-server.pc' to the PKG_CONFIG_PATH environment variable', although I have no xorg-server.pc), which creates '/etc/X11/xorg.conf'. Modified that file's "Device" section to include the BoardName and RegistryDwords lines.
- 'sudo find / -iname *xorg*.conf' returns only '/usr/share/doc/xserver-xorg-video-intel/xorg.conf', with only a "Device" section in it about Intel. I tried modifying this to use the nvidia driver. I don't remember if I tried adding the RegistryDwords line as well. Anyway, this conf file is within a directory caled 'xserver-xorg-video-intel'...so...idk.
- There is a '/usr/share/doc/xserver-xorg-video-nvidia-410/', but it is empty except for a changelog and copyright. I didn't try adding an xorg.conf.
- By the way, I have no nvidia_backlight, intel_backlight, or acpi_video0 directories anyw[FONT=arial]here. 'sudo find / -iname *backlight*' [pastebin,]("https://paste.ubuntu.com/p/CNtNgNsctT/") 'sudo find / -iname *brightness*' [pastebin]("https://paste.ubuntu.com/p/dqFwcsQGtH/").[/FONT]
- BASH SCRIPT / NVIDIA-SETTINGS... The custom bash script posted in that thread is supposed to interact with nvidia-settings's BacklightBrightness attribute and the ~/.nvidia-settings-rc file. By default, my nvidia-settings has no BacklightBrightness attribute. I can get it to say it has the attribute by adding the RegistryDwords paragraph to '/usr/share/X11/xorg.conf.d/10-nvidia.conf', or by running nvidia-xconfig and adding those lines to the newly created '/etc/X11/xorg.conf'...but in either case, although it now shows as an attribute, calling it doesn't actually do anything. Calling it as an option of nvidia-settings doesn't do anything (though no errors show), and running the script doesn't do anything either but show the level it's "supposed" to be at (but the actual brightness stays the same). I notice ~/.nvidia-settings-rc includes lines of "RedBrightness" and "RedGamma"; maybe those can be edited directly to change it?
_Other things I tried (inspired by [this other thread]("https://forums.linuxmint.com/viewtopic.php?t=185148")):_
- Edited GRUB to include acpi_backlight=video, vendor, native, and none.
- Installed xbacklight.

It goes without saying, none of the above worked, and after I tried each one I undid it / deleted whatever files I'd created.
SOS! Thanks a ton. And let me know where else I should post this if it doesn't get any traction.

---

### Post by vidtek on 2018-11-19
> **bennywas said:**
> *EDIT: In case this thread remains silent, you can check [my repost on the nvidia forums]("https://devtalk.nvidia.com/default/topic/1043967/linux/410-396-390-amp-340-all-boot-to-black-screen-on-geforce-gt-650m-mac-edition/") regarding the black screen boot issue.*

My initial problem: After installing nvidia-driver-410 from [the official PPA]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa"), brightness control keys didn't work. I tried every solution listed in [this thread]("https://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver") and [this one]("https://forums.linuxmint.com/viewtopic.php?t=185148") including bash scripts; no luck. The subsequent problem: I wanted to completely uninstall the 410 driver to see if reinstalling it or trying older versions would work, so I ran 'dpkg -l | grep -i nvidia' from root shell and purged every package listed (following the advice of threads like [this]("https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely")). Now, every nvidia version I try to install (including 410 again) leads to a black screen on boot (not sure if this is related to purging those packages).** So, I have two problems:** First, installing any nvidia driver without a black screen; second, if I get one up and running, figuring out how to change the brightness. Here are my computer's details...

[FONT=courier new]uname --all && lsb_release --all[/FONT]
```
Linux benny-MacBookPro 4.15.0-38-generic #41-Ubuntu SMP Wed Oct 10 10:59:38 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic
```
[FONT=courier new]lspci -vnn | grep -i vga && sudo lshw -C video[/FONT]
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107M [GeForce GT 650M Mac Edition] [10de:0fd5] (rev a1) (prog-if 00 [VGA controller])
  *-display                 
       description: VGA compatible controller
       product: GK107M [GeForce GT 650M Mac Edition]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:48 memory:c0000000-c0ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:2000(size=128) memory:c1000000-c107ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:50 memory:c1400000-c17fffff memory:b0000000-bfffffff ioport:3000(size=64)
```

**Black screen issue:**
- First noticed several weeks ago when I first tried switching to nvidia, but I didn't document it well. From what I remember, I was using the Software & Updates > Additional Drivers GUI, selected nvidia-driver-390, rebooted, and couldn't change brightness. So I selected nvidia-driver-340, rebooted, and got a black screen. I had to switch to nouveau using GRUB's older kernel version option. Then I forgot about all this because it seemed like a lot of effort.
- Now it is happening again while using the abovementioned PPA, although it didn't happen initially. The first version I installed from the PPA was 410, rebooted, and couldn't change brightness. When no solution worked, I purged everything listed from 'dpkg -l | grep -i nvidia', ran autoremove, rebooted, and tried again. Now, trying to install 410 from the PPA boots to a black screen...and recovery mode's root shell prompt freezes before fully loading, so to purge nvidia I have to boot with the older kernel version, which works for some reason.
- Same thing with 396, 390, and 340. (Slight difference: the root shell prompt of one of those versions *did* work, but I can't remember which.) Trying to install 304 returns "unmet dependencies" for xorg-video-abi-* and xserver-xorg-core.
- Those are all the drivers listed in 'ubuntu-drivers list'. I haven't tried any in-between versions, but I will if you think it'll help.

**No brightness control issue: ***(originally posted [here]("https://ubuntuforums.org/showthread.php?t=2405281") but no replies)*
- On nvidia 410 (unconfirmed with other versions), brightness is stuck very low, I assume because that's the default boot brightness. Keys can't control it.
- As you see, I have hybrid graphics / dual GPUs; I hear nvidia is especially difficult with these computers.
- I'm told brightness can be adjusted from the NVIDIA X Server Settings GUI, but found no option for brightness there. I'm also told that the GUI is supposed to include a "PRIME Profiles" tab, which I don't have. Opening the GUI from terminal returns "Is Prime supported? no" or similar.
- nvidia-settings does not include a BacklightBrightness attribute.
- Many solutions I found online assumed older versions of X with different conf files in different places, although I ended up trying all of them just in case.
_Things I tried (inspired by [this thread]("https://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver")):_
- Modified  '/usr/share/X11/xorg.conf.d/10-nvidia.conf'. The file previously only included an "OutputClass" section. I added a "Device" section with my BoardName and the "RegistryDwords" "EnableBrightnessControl=1" option.
- Added a similar conf file to that same directory. I created a 10-nvidia-brightness.conf with the same "Device" section, which I also tried renaming 20-nvidia-brightness.conf.
- Ran nvidia-xconfig (returns 'Warning: Package xorg-server was not found in the pkg-config search path. Perhaps you should add the directory containing 'xorg-server.pc' to the PKG_CONFIG_PATH environment variable', although I have no xorg-server.pc), which creates '/etc/X11/xorg.conf'. Modified that file's "Device" section to include the BoardName and RegistryDwords lines.
- 'sudo find / -iname *xorg*.conf' returns only '/usr/share/doc/xserver-xorg-video-intel/xorg.conf', with only a "Device" section in it about Intel. I tried modifying this to use the nvidia driver. I don't remember if I tried adding the RegistryDwords line as well. Anyway, this conf file is within a directory caled 'xserver-xorg-video-intel'...so...idk.
- There is a '/usr/share/doc/xserver-xorg-video-nvidia-410/', but it is empty except for a changelog and copyright. I didn't try adding an xorg.conf.
- By the way, I have no nvidia_backlight, intel_backlight, or acpi_video0 directories anyw[FONT=arial]here. 'sudo find / -iname *backlight*' [pastebin,]("https://paste.ubuntu.com/p/CNtNgNsctT/") 'sudo find / -iname *brightness*' [pastebin]("https://paste.ubuntu.com/p/dqFwcsQGtH/").[/FONT]
- BASH SCRIPT / NVIDIA-SETTINGS... The custom bash script posted in that thread is supposed to interact with nvidia-settings's BacklightBrightness attribute and the ~/.nvidia-settings-rc file. By default, my nvidia-settings has no BacklightBrightness attribute. I can get it to say it has the attribute by adding the RegistryDwords paragraph to '/usr/share/X11/xorg.conf.d/10-nvidia.conf', or by running nvidia-xconfig and adding those lines to the newly created '/etc/X11/xorg.conf'...but in either case, although it now shows as an attribute, calling it doesn't actually do anything. Calling it as an option of nvidia-settings doesn't do anything (though no errors show), and running the script doesn't do anything either but show the level it's "supposed" to be at (but the actual brightness stays the same). I notice ~/.nvidia-settings-rc includes lines of "RedBrightness" and "RedGamma"; maybe those can be edited directly to change it?
_Other things I tried (inspired by [this other thread]("https://forums.linuxmint.com/viewtopic.php?t=185148")):_
- Edited GRUB to include acpi_backlight=video, vendor, native, and none.
- Installed xbacklight.

It goes without saying, none of the above worked, and after I tried each one I undid it / deleted whatever files I'd created.
SOS! Thanks a ton. And let me know where else I should post this if it doesn't get any traction.


Benny-

You have obviously tried a whole lot of stuff to fix this on your system.  There will be all sorts of legacy files left behind after all the tinkering you have done.

My advice would be a clean install of 8.10 and so you will at least be starting from a clean system.  Take a snapshot with qt5-fsarchiver before you make any change so you get back to where you were easily.
You have obviously spent hours on this so I would call it a day and start again mate.

Cheers, Tony.

---

### Post by Autodave on 2018-11-19
I have to agree with vidtek. However, I would go with 18.04 since it is an LTS.  If you go with 18.10, then you could very well have the same problem when you update (in 5 months) to 19.04.

---

### Post by vidtek on 2018-11-19
> **Autodave said:**
> I have to agree with vidtek. However, I would go with 18.04 since it is an LTS.  If you go with 18.10, then you could very well have the same problem when you update (in 5 months) to 19.04.

Dave is right, with your problems stick to an LTS.

Tony

---

