---
title: "Problems with nVidia GT 240 card in Hardy 8.04"
date: 2010-08-02
forum: Multimedia Software
---

### Post by shreepads on 2010-08-02
**_Issue:_** 
Unable to get high res, colour or 3-D acceleration working with 8.04 Hardy. Not a hardware problem as it works perfectly in dual-boot XP.

**_Setup:_**
a. Ubuntu 8.04 Kernel Linux 2.6.24-28 generic
- Occasional Win XP dual boot
b. Intel DG33FB motherboard
- Intel G33 Express Chipset
- Intel GMA 3100 onboard graphics card
- One PCI Express x16 connector (PCI Express v1.1)
c. Intel C2D E7200 @ 2.53Ghz
d. 2 GB RAM
e. 2 x 3 Gbps SATA drives
f. LG Flatron Wide 19" LCD monitor with DVI-D sockets
g. Corsair 400w PSU
h. Palit GT 240 1GB DDR5 Sonic PCIe card

```
> sudo lspci -vvnn | grep -i nvidia
01:00.0 VGA compatible controller [0300]: nVidia Corporation Unknown device [10de:0ca3] (rev a2) (prog-if 00 [VGA controller])
01:00.1 Audio device [0403]: nVidia Corporation Unknown device [10de:0be4] (rev a1)
```

**_Already Tried:_**

1. Plugging in the monitor to the VGA port and starting up Ubuntu. Result: Max 800x600 res, low colour, no 3-D acceleration.

2. Went to System > Admin > Hardware Drivers and nothing is listed there. Saw that the default nVidia proprietary drivers in the repository (v169.12) don't support GT 240 so instead decided to go with envy.

3. Installed envyng-core and ran envyng.
- First tried to let the system pick the right driver for the card but it gave up with an error: " Envy does not recognise your card as compatible with any version of the driver.."
- So I tried the manual install and was prompted with these choices:
    " 1 - 173.14.12 (latest)
      2 - 96.43.05 (new legacy)
      3 - 71.86.04 (legacy)
    "
-  Chose 173.14.12 even though the list at the link below doesn't list my card
[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.12/README/appendix-a.html)
- Ran thru with the installation and reboot. On restarting the system seemed to try a few times to get it working but gave it up and presented an error message stating that it could not get the card to work and was going to start in a low res mode.
- Back where I started 800x600, low colour, no 3-D acceleration

4. Just to try it out put in the 10.4 LiveCD and booted. 
- Came up perfectly with full res (1440 x 900) and colour. Also prompted me to install the nVidia proprietary drivers, which I did and the same went thru smoothly.
- Then to give them a push I tried to enable desktop effects from System > Preferences > Appearance > Visual Effects. Tried both Normal and Extra settings but both came back with a "Desktop effects could not be enabled" error.

5. Uninstalled the nVidia drivers using envyng. Uninstalled envyng as well.
- Set the BIOS to always use the onboard graphics, disabling the card, and connected monitor VGA to the motherboard socket. 
- Booted up Ubuntu but got the same error stating that it could not get the card to work and was going to start in a low res mode
- Thankfully envyng had backed up my xconf.org so restored the backed up version and was back to normal, except for a new graphics card that was sitting there doing nothing except consuming power.

6. Connected the DVI cable from the monitor to the DVI slot on the card and reset BIOS to use the graphics card. 
- Booted up Ubuntu and now its at 1024x768, low colour, no 3-D acceleration

Don't want to upgrade to Lucid till 10.04.1 is out...

---

### Post by shreepads on 2010-08-03
Nouveau drivers not available in Hardy repositories (all enabled).

Should I be trying the below now? Only want to do this as a last resort as it requires rework on every kernel and mesa update.

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Also anything in the manual that is not correct/ applicable for Hardy 8.04?

---

### Post by shreepads on 2010-08-04
Finally got the blessed thing working, primarily based on the link in my last post to the Ubuntu nVidia Manual.
 
Also went thru the 'Installing the nVidia Driver', 'Frequently Asked Questions', 'Common Problems' pages in the nVidia driver README pages at the following link:
  [http://us.download.nvidia.com/XFree86/Linux-x86/256.44/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/256.44/README/index.html)

Thought I'll put this down for the benefit of any noob like me who has not installed stuff outside of the repositories.

This should work for anyone who
- Uses the standard Ubuntu 8.04 desktop 32-bit release (full updated with all updates)
- Is installing a new nVidia GeForce 200/ 300/ 400 series card  (although I have done it on GT 240)
- Doesn't have any proprietary nVidia drivers already installed (if so you would need to uninstall them first)

_**Preparation:**_

- Really works best if you have another desktop/ laptop. Use it to open the Ubuntu nVidia Manual and all the relevant pages from the nVidia driver README pages described above.

- If you have only one internet connection connect this to the computer you need to install your nVidia drivers on

- Read thru the Ubuntu nVidia Manual once. The 'Appendix I. Tips for New Linux Users' in the nVidia README is also helpful if you're new to Linux

- Download the nVidia driver appropriate for you from the links provided in the Ubuntu nVidia Manual. 
  I used the latest one 256.44 for 32-bit Linux
  Use 'chmod' to make the downloaded file an executable as described in the Ubuntu nVidia Manual

**_Installation:_**

- Just follow the steps outlined in the Ubuntu nVidia Manual, I'll only highlight the options/ additional stuff I did

- Backup you xorg.conf file, making the backup file name a little more obvious
```
  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.prenvidiadrivers.bak
```

- Install the build-essentials package. 
  The command as given in the Ubuntu nVidia Manual doesn't work exactly like that
  You need to first run 'uname -r' from the prompt (to print the kernel release) and then copy-paste the output of that to replace the 'uname -r' at the end of the command given in the manual, like so
```
   sudo apt-get install build-essential linux-headers-2.6.24-19-generic
```
  This might seem bleeding obvious but was a little confusing for me
  Depending on what you already have installed on your system this should download all the necessary build-essentials

- I skipped the next part about installing the linux-source packages

- Remove any conflicting packages
  The first instruction, to remove 'nvidia-glx, nvidia-glx-legacy, nvidia-glx-new and nvidia-settings' can be done by opening System -> Administration -> Synaptic Package Manager and searching for packages with 'nvidia' in their name
  Uninstall any 'nvidia-glx, nvidia-glx-legacy, nvidia-glx-new and nvidia-settings' packages, or packages starting with these names if already installed (The square to the left of the package name would be filled in if installed)
  Do not uninstall 'nvidia-kernel-common'or packages starting with 'linux-restricted-modules'

- Restrict other modules from loading. 
  It seems this is required as these drivers are part of the kernel or other essential packages and so can't be uninstalled
  While the Ubuntu nVidia Manual doesn't say this, I always backup any system config files before editing them, in this case using
  ```
sudo cp /etc/default/linux-restricted-modules-common /etc/default/linux-restricted-modules-common.prenvidiadrivers.bak
```

- Edit the existing xorg.conf
  I skipped this step as the manual says its not required for Hardy and the nVidia driver installer does this for you anyway towards the end

- Installing the drivers
  The nVidia driver README says that doing this after shutting down the X server isn't enough because some OpenGL programs may still be running. They recommend placing the system in a lower run level which uses only the terminal. Since I have no idea how this is done, I just settled for a reboot, after which I didn't start any applications (NB: 'Recovery Mode' didn't work as networking is disabled in this mode)
  Move to the terminal mode and stop the X server as described in the manual (just above 'Install the Driver')
  Before running the installer, I think its better to verify that it was downloaded correctly. While the installer does this on starting I felt it is safer to do this first
 ```
 sudo sh NVIDIA-Linux-x86-256.44.run --check
```

  Assuming this is fine run the installer
  - You first need to Accept the terms and conditions (use the arrow keys to move around)
  - The installer will then check for conflicting software and install the drivers
  - At the end it will ask you whether you want it to reconfigure your X server configuration ("Would you like to run nvidia-xconfig"), choose 'Yes'
  - And you should be done unless you have any errors
  Now startup the X server (using the command in the Ubuntu nVidia Manual just above 'Configure') and you should be in with a full res high colour desktop

- I didn't need to run NVIDIA X Server Settings or update /etc/modules to load the nVidia driver on boot as mentioned in the Ubuntu nVidia Manual
  Presumably this is done if you choose 'Yes' in the installer when asked whether you want the installer to configure X for you


**_Post Installation_**

- A few more things I noticed while testing out various aspects

- Run a video using Movie Player, the colours may be off if you had changed the default settings due to your earlier graphics. Go to Preferences -> Video in Movie Player and reset the Hue/ Saturation/ Contrast values to default via the button there

- If you have a separate 'normal user' login like me you will need to reset the screen resolution (via System -> Preferences) and colours (as described above) after logging in as that user

- I tried running a few simultaneous videos and Open GL games and worked perfectly in separate windows on the desktop. OpenArena (full screen) could be run in higher res and detail than before. And it was very smooth, reporting fps of 60+ at all times

- One glitch observed on setting the desktop effects (System -> Preferences -> Appearance -> Visual Effects) to High
  While you can set this and close the dialog properly, within a few seconds or when you attempt to open the first window the system will hang and will require a hard reset and re-boot
  But post re-boot all the effects work properly

---

### Post by shreepads on 2010-08-05
Had a couple of system freezes that require a hard power rest and re-boot. Funnily enough wasn't doing any heavy video/ 3D stuff. One anamoly noted that in all apps with text (Firefox, even System Log), scrolling the text caused the text to appear double/ vanish on some rows...

System log (/var/log/syslog) shows the same section as below at each such freeze:
```

Aug  4 01:17:22 UbuntuD kernel: [ 1982.142397]  =======================
Aug  4 01:17:33 UbuntuD kernel: [ 1993.938958] BUG: soft lockup - CPU#1 stuck for 11s! [Xorg:7306]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.938963] 
Aug  4 01:17:33 UbuntuD kernel: [ 1993.938965] Pid: 7306, comm: Xorg Tainted: P        (2.6.24-28-generic #1)
Aug  4 01:17:33 UbuntuD kernel: [ 1993.938968] EIP: 0060:[<f9e17c1e>] EFLAGS: 00003216 CPU: 1
Aug  4 01:17:33 Shuklas-UbuntuD kernel: [ 1993.939298] EIP is at _nv021088rm+0x23/0x24 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.939302] EAX: 30c09000 EBX: df9d0b00 ECX: 00400824 EDX: fa380000
Aug  4 01:17:33 UbuntuD kernel: [ 1993.939304] ESI: f66d4000 EDI: f7432400 EBP: f666bd88 ESP: dfa23d50
Aug  4 01:17:33 UbuntuD kernel: [ 1993.939307]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Aug  4 01:17:33 UbuntuD kernel: [ 1993.939309] CR0: 80050033 CR2: 084f35e0 CR3: 3758a000 CR4: 00000690
Aug  4 01:17:33 UbuntuD kernel: [ 1993.939311] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Aug  4 01:17:33 UbuntuD kernel: [ 1993.939313] DR6: ffff0ff0 DR7: 00000400
Aug  4 01:17:33 UbuntuD kernel: [ 1993.939315]  [<f9d6c7ed>] _nv021821rm+0x183/0x195 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.939680]  [<f9c75e41>] _nv014250rm+0xaa/0x112 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.940051]  [<f9ca54ed>] _nv015432rm+0x94/0x10f [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.940424]  [<f9bb9464>] _nv002671rm+0x98/0x11b [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.940771]  [<f9bb9660>] _nv002670rm+0x179/0x183 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.941117]  [<f9bb9a75>] _nv009765rm+0x368/0x4f7 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.941464]  [<f9bb3cb7>] _nv009855rm+0x3e7/0x3f6 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.941810]  [<f9bb0ae7>] _nv009554rm+0xc2c/0xcb5 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.942167]  [<f99b1134>] _nv002120rm+0x9fc/0xd25 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.942396]  [<f99bc36a>] _nv001721rm+0x6c/0xae [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.942629]  [<f9e22f70>] _nv002114rm+0x430/0x5e3 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.942958]  [<f9e1fbcd>] rm_ioctl+0x3e/0x6d [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.943287]  [<f9e3a286>] nv_kern_ioctl+0x126/0x450 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.943619]  [do_setitimer+0xde/0x330] do_setitimer+0xde/0x330
Aug  4 01:17:33 UbuntuD kernel: [ 1993.943627]  [<f9e3a5e8>] nv_kern_unlocked_ioctl+0x18/0x20 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.943951]  [<f9e3a5d0>] nv_kern_unlocked_ioctl+0x0/0x20 [nvidia]
Aug  4 01:17:33 UbuntuD kernel: [ 1993.944268]  [do_ioctl+0x2b/0x90] do_ioctl+0x2b/0x90
Aug  4 01:17:33 UbuntuD kernel: [ 1993.944283]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
Aug  4 01:17:33 UbuntuD kernel: [ 1993.944288]  [snd_pcm:ktime_get_ts+0x1e/0x4f0] ktime_get_ts+0x1e/0x60
Aug  4 01:17:33 UbuntuD kernel: [ 1993.944295]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70   
Aug  4 01:17:33 UbuntuD kernel: [ 1993.944301]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
Aug  4 01:17:33 UbuntuD kernel: [ 1993.944314]  =======================

```

And also the following, which, as per most, is a harmless message.
```
Aug  5 20:50:00 UbuntuD kernel: [   53.899570] nvidia: module license 'NVIDIA' taints kernel.

```

Googling this error reported several such problems and a Lunchpad bug report with no definite solution. Folks have tried replacing power supplies, graphics cards, drivers, nVidia X Settings, cooling solutions to no avail. Having pushed this card quite hard in WinXP I'm fairly sure its not a hardware problem.

I have switched desktop effects (System -> Preferences -> Appearance -> Visual Effects) back to None and haven't faced any freezes since. I don't really need them and my video/ 3D stuff is working fine.

Fingers crossed...

---

### Post by Stigmata13 on 2010-08-05
Just out of curiosity, is there any specific reason that you're using 8.04 instead of 10.04? Have you given Lucid a try?

---

### Post by shreepads on 2010-08-06
> **Stigmata13 said:**
> Just out of curiosity, is there any specific reason that you're using 8.04 instead of 10.04? Have you given Lucid a try?

Well I have tried the Lucid LiveCD as mentioned above and it seems to work OK on my existing hardware. Also, as I said I'm waiting for 10.04.1 to come out before I upgrade.

No specific reason I guess, just want to move to a reasonably stable OS and the initial reports on Lucid were not comletely complementary. I did face a few app-specific problems while using the Lucid LiveCD. These have probably been patched by now but I'd rather sit and wait for 10.04.1 before I go thru the whole install procedure.

Looked at the Lucid Release Schedule and 10.04.1 is expected on Aug 12th 2010!! Oh well...

---

### Post by shreepads on 2010-12-04
Well I was facing freeze problems while running CUDA apps and didn't know what to do. Then a new Linux kernel install caused this to go on the blink so I downloaded and installed the latest driver version (256.53).

Turns out this has a fix specifically for GT 240 and now CUDA apps are running extremely smoothly..

:D

EDIT:
Oh yes and Lucid 10.04.1 still hasn't fixed the problem re using USB phones + Skype, which is working perfectly for me in Hardy..

---

