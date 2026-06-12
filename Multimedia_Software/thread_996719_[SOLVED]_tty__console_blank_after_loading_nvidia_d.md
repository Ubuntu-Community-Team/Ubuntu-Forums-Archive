---
title: "[SOLVED] tty / console blank after loading nvidia drivers"
date: 2008-11-29
forum: Multimedia Software
---

### Post by antiplex on 2008-11-29
hello dear community!

i've experienced this problem for some time now but simply didn't find any time to solve it.
i've got a mainboard with an integrated nvidia graphics chipset (nforce 630a) and the correct drivers (v 177.82) installed. the problem is that when gdm is started my tty's run on a resolution/mode that is not supported by my tft-screen. (says 'out if range ...').
as this seems to have been addressed before, i found [this thread]("http://ubuntuforums.org/showthread.php?t=585454") quite helpful.

so i tried everything just like described and it seems to be in affect at first (during startup, the console resolution is influenced by what i set through vga=771 for 800x600 resolution), but when the x-session has started (and i guess thats when the nvidia-driver is loaded), the tty's can't get displayed no more (monitor gives 'out of range'-message).

to me, it seems as if the nvidia driver kills the vesafb that is correctly loaded (at least lsmod says so).
i also tried to additionally load vga16fb but this didn't help either.

has anybody experienced something similar? how might i solve this? any suggestions are very welcome! thanks...

ps: just to be make sure; i unblacklisted 'vesafb' from '/etc/modprobe.d/blacklist-framebuffer' , added 'fbcon' and 'vesafb' to '/etc/initramfs-tools/modules', ran 'sudo update-initramfs -u' and of course added a 'vga=XXX' (with XXX being a [linux video mode number]("http://en.wikipedia.org/wiki/VBE#Linux_video_mode_numbers")) to the kernel boot parameter.

---

### Post by antiplex on 2008-11-30
ah, right... i forgot to mention that i use ubuntu 8.04. i'm not completely aware of what role the xserver-driver (nvidia proprietary in my case) plays for the virtual tty consoles. i guess it somehow must do something sice the boot-up-console works fine.
so what i tried is to add a modeline to my xorg.conf for the resolution i chose for the console (vga=771 =~ 800x600). this (rather conservative) resolution should be available, at least the output of 'sudo hwinfo --framebuffer' says so (Mode 0x0303: 800x600 (+800), 8 bits).

really nobody got a hint for me?

---

### Post by antiplex on 2008-12-01
some more details: 

- no suspicious warnings or errors in /var/log/Xorg.0.log found
- when switching to tty[1-6], my display says: ```
frequency out of range: 65 khz / 52 hz, 
please change the display mode to 1600x1200 with 60hz
``` i then checked the specs for my display and while the 65 khz (horizsync) are within the specificiations, 52hz (vertrefresh) is too low and the minimum accepted frequency would be 56hz.
my modelines in xorg.conf should be fine though, Xorg.0.log says ```
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200@60"
(II) NVIDIA(0):     "1280x1024@60"
(II) NVIDIA(0):     "1024x768@70"
(II) NVIDIA(0):     "800x600@70"
(II) NVIDIA(0):     "640x480@72"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200 
``` which looks fine to me.
also a bit further above in Xorg.0.log i find ```
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver 
``` this also appears correct
then there are two entries that i am not sure about: ```
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3 
``` well, fb probably stands for framebuffer and from what i found out until now, a framebuffer is what is needed for the vitual tty consoles. i just wonder if these are the right ones or if they somehow interfere with vesafb???

one thing that i would like to find out is where the 52hz vertical refresh come from, they are certainly NOT from the modelines i added. but i guess this must be set somewhere, so if anybody has a clue where, please let me know!

---

### Post by antiplex on 2008-12-01
\\:D/ GOOD NEWS! I JUST SOLVED THIS ISSUE! \\:D/

before telling how, i'd like to mention that while looking for a solution i came across numerous reports about bugs or problematic behaviour of usplash (the ubuntu splash screen). usplash is active on default but one can easily disable it through editing /boot/grub/menu.lst , but please make a backup first in case something goes wrong!

this is what you need to do in order to disable usplash which as i mentioned could lead to additional problems:
in the menu.lst file, first look for the 'defoptions' section somewhere near the middle and remove 'splash' there, so it won't be added to the default kernel parameters again on the next kernel-update.
then, also remove the word 'splash' from the lines starting with 'kernel    /vmlinuz-...'.


and here is what i did to finally get a working console:
in /etc/modprobe.d/nvidia-kernel-nkc i added an additional parameter 'NVreg_UseVBios=0' at the end of the existing ones. after rebooting, everything worked fine with the settings described in my previous postings.
after the reboot, the output of 'cat /proc/driver/nvidia/registry' should contain the line 'UseVBios: 0'; this read 'UseVBios: 1' before adding the parameter.
the idea for this came from [this thread at the nvidia-forums]("http://www.nvnews.net/vbulletin/showthread.php?t=120492"), so props to the ones there who figured things with this the parameter out! =D>

another nice thing now is that i can use higher resolutions on the virtual consoles tty[1-6] using the vga=XXX parameter mentioned earlier.
1600x1200 (code 796) wont work in my case but 1280x1024 (code 775) is also pretty fine with me.
the reason for the not working 1600x1200 resolution is probably that vesafb doesn't support it (not part of the vesa standard anyway). there seems to be another frambuffer driver called 'uvesafb' which should be capable of this, but as far as i have found out now, the usage of uvesafb would require to recompile the kernel with a different configuration.

---

### Post by OkydOky on 2009-04-11
I am wondering if anyone can help me:
I am running the 64bit 8.10 live CD.

and I can not find the file:
/etc/modprobe.d/nvidia-kernel-nkc

Therefore I can not set UseVBios to 0 to try it.


I am trying this out on the live CD because I want everything working properly before I take the plunge. This issue with the blank tty's is the only thing holding me back.


I am trying to get this running on a Clevo M860TU with an Nvdia 9800M GT

---

### Post by antiplex on 2009-04-14
if you run the live-cd you probably don't have any nvidia-driver installed. this is one thing that doesn't work really good one live-systems since afaik the system needs to be rebooted for external proprietary graphics drivers (like nvidia) to work, which is what doesn't work with a live-system because it can't store its state.

but why are you sticking to 6.10? there has been huge progress since these old days of 6.10, i really recommend using a more recent version, also on older hardware! if you need LTS take 8.04, 9.04 is to be released officially in about a week, but is not LTS.
the problem with the missing nvidia-kernel-nkc on live-systems will be the same here though.


EDIT: note that handling of kernel-module options seems to have changed in 9.04 (beta); there might be no file 'nvidia-kernel-nkc' in /etc/modprobe.d (and no options-file as well), at least on my machine running ubuntu 9.04 64bit beta this was the case.
but setting NVreg_UseVBios=0 can also be done more directly via kernel-options in /boot/grub/menu.lst . at least this way i got it working for nvidia-driver version 180.44.
for further reading i suggest [this thread on ubuntuforums]("http://ubuntuforums.org/showthread.php?p=7066102") and then [https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions").

---

### Post by OkydOky on 2009-04-15
I am sorry - that was a silly Typo.
It's 64bit 8.10

I can get the Nvidia Drivers to load (or at least have the issue with the blank tty) with downloading the Drivers, insalling them, and simply restarting x.

Once that is done, ttys are blank, and useless.

I will try the kernel options way - it makes sence, simpy did not think or it...

---

### Post by SlonUA on 2009-04-30
sudo nano /etc/modprobe.conf

add this line
options nvidia NVreg_UseVBios=0

---

### Post by garuhhh on 2009-05-04
any news as to how to set NVreg_UseVBios to 0 in Jaunty?
thanks! been searching for a while, but found no solution..

---

### Post by K. Hendrik on 2009-05-05
You can set NVreg_UseVBios to 0 in Jaunty by creating a new file in /etc/modprobe.d/ with just this line as content
```
options nvidia NVreg_UseVBios=0
```

i named it nvidia-fix.conf but the name doesn't really matter it changed the NVreg_UseVBios to 0 i can see the change by the result of cat /proc/driver/nvidia/registry

but I still have a blank console.

---

### Post by garuhhh on 2009-05-05
yes you're right.. putting NVBios=0 didn't solve the problem.
but "vga=791" in boot options solved the problem of not having a console/tty.

---

### Post by K. Hendrik on 2009-05-05
I tried a few different options as vga parameter but nothing I allways just get a blank console

---

### Post by K. Hendrik on 2009-05-05
I just installed ubuntu on my other pc it also has a nvidia card and it also had no tty's i set the vga parameter and it worked so why doesn't it work on my laptop? the only difference i can see is the laptop is 1980*1020 (16:9) and my pc is 1280*1024 (5:4)

---

### Post by garuhhh on 2009-05-06
@K.Hendrix, did you try the steps did by antiplex in the first few posts?

---

### Post by K. Hendrik on 2009-05-06
> **garuhhh said:**
> @K.Hendrix, did you try the steps did by antiplex in the first few posts?

yes i did but it didn't work

in my Xorg.0.log I found these warnings
```

(WW) NVIDIA(0): ACPI: Error: Unable to find the DOS (Enable/Disable output
(WW) NVIDIA(0):     switching) file path under /proc/acpi/video. The NVIDIA X
(WW) NVIDIA(0):     driver will not be able to respond to ACPI display change
(WW) NVIDIA(0):     hotkey events.

```

I really don't know what could be the problem

---

### Post by garuhhh on 2009-05-06
hmmm.. i don't know either what they mean! :D
let's wait for reponses :)

---

### Post by K. Hendrik on 2009-05-07
OK to give you some more informations:

Im running ubuntu 9.04 on an Acer Aspire 6935 with a NVIDIA GeForce 9600M GT and the NVIDIA driver 180.44

---

### Post by InF3XioN on 2009-05-11
Well it worked for me too. I use an HP Pavillion dv6541ev with a NVidia GForce 8400GS. The only resolution that seemed to fit on my screen was 1280x800 (at 32-bit), since it's a wide one (16:9). So I put the value "vga=0x361" (it accepted only hexadecimal values. 361(HEX)=865(10)). But now I face another issue. The splash screen was replaced by boot messages even if the value "splash" exists in the grub menu configuration file. The issue appears with every resolution chosen, and the splash screen remains only if I remove the resolution option from the grub menu. Please help.

---

### Post by K. Hendrik on 2009-05-11
I don't know if this will solve your problem but you could try to change the usplash resolution by editing the file /etc/usplash.conf and running sudo update-initramfs -u

---

### Post by InF3XioN on 2009-05-11
> **K. Hendrik said:**
> I don't know if this will solve your problem but you could try to change the usplash resolution by editing the file /etc/usplash.conf and running sudo update-initramfs -u

No, the problem still exists. I forgot to mention that the splash screen appears for a while, but when the progress bar is about to start loading, the boot messages start appearing.

---

### Post by K. Hendrik on 2009-05-13
I don't really know what the problem could be.

I tried the same resolution for 16:9 as vga parameter but it doesn't work i think it's a problem with the 9600M GT hast anyone managed to get this working with an 9600 card?

---

### Post by user-max on 2009-05-20
I had the same problem. Im running Ubuntu 9.04 on a widescreen HP laptop. My ttys didnt appear after Nvidia driver installation. What I did to fix the problem was go into Start-up manager, change resolution to 800x600, and after that my ttys started working !!! (If you dont have start-up manager installed, install it by sudo apt-get install startupmanager) Simple as that.

---

### Post by K. Hendrik on 2009-05-22
Hi, I tried the startupmanager trick but still the tty's are not working I realy think it must be something special with the 9600 card's anyone got these working?

---

### Post by technogeeky on 2009-05-22
> **K. Hendrik said:**
> Hi, I tried the startupmanager trick but still the tty's are not working I realy think it must be something special with the 9600 card's anyone got these working?

I am beginning to think the same thing. I have a 9600 GT on a desktop, and I can't seem to fix the problem either. This is in addition to a whole slew of other oddities.

I'll report any updates.

---

### Post by gpstar on 2009-05-22
I had this problem for ages, and the new nvidia beta driver version: 185.18.10 solves the problem, all the virtual tty's now work.

can grab the beta driver from here

[ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.10/](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.10/)

or can install it from here and stay up to date when new versions come out. I recommend the below version as I had problems compiling the driver from the nvidia file with jaunty.

Repo
[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

or links to debs if you prefer that way.
[https://launchpad.net/~thefirstm/+archive/ppa/+sourcepub/634198/+listing-archive-extra](https://launchpad.net/~thefirstm/+archive/ppa/+sourcepub/634198/+listing-archive-extra)

---

### Post by K. Hendrik on 2009-05-23
Didn't think it would work because I already tried the 185.18.08 but 185.18.10 really did the trick, downloaded it from the ftp site and it works like a charm, now this thread is really solved.

---

### Post by garuhhh on 2009-05-25
> **gpstar said:**
> I had this problem for ages, and the new nvidia beta driver version: 185.18.10 solves the problem, all the virtual tty's now work.

can grab the beta driver from here

[ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.10/](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.10/)

or can install it from here and stay up to date when new versions come out. I recommend the below version as I had problems compiling the driver from the nvidia file with jaunty.

Repo
[https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)

or links to debs if you prefer that way.
[https://launchpad.net/~thefirstm/+archive/ppa/+sourcepub/634198/+listing-archive-extra](https://launchpad.net/~thefirstm/+archive/ppa/+sourcepub/634198/+listing-archive-extra)

hey thanks gpstar! this works! i removed the vga=791 option from my boot options.. everything is working well.
kinda weird though, on my first restart tty was not available, but now it's ok. after the first restart, i restarted again, and it's all working well now.

but still i have to press Enter a couple of times when hibernating/suspending/resuming for it to work.. or else,there is no harddisk activity.

---

### Post by edeion on 2009-07-29
Excellent! Thanks gpstar, it did solve my blank ttys problem. I had been wondering about this one for long. (installed package: nvidia-glx-190)

---

### Post by lipidicman on 2010-05-08
Eek, can anyone help me get that beta driver installed.  Launchpad wont let me get the files and the one from the ftp link needs compiling?

---

