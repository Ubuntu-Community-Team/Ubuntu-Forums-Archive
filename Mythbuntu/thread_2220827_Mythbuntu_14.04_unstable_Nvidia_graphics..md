---
title: "Mythbuntu 14.04 unstable Nvidia graphics."
date: 2014-04-29
forum: Mythbuntu
---

### Post by khPWXxF on 2014-04-29
I tried Mythbuntu 14.04 64 bit this weekend on an Asus M3N78-EM mobo with on-board Nvidia 8300 graphics processor and HDMI output.   With  Mythbuntu12.04, mythtv 0.25 and Nvidia drivers 295.40 this hardware is very stable.

  lspci confirms it is Nvidia 8300:
> VGA compatible controller: Nvidia Corporation C77 [GeForce 8300] (rev a2)
   
  Unfortunately, with 14.04 (and Nvidia 331.38 drivers) the graphics are totally unstable.  It will start stuttering sounds, flashing then lock up the whole system after a minute or so after boot up, even with what would appear to be an undemanding load like a terminal session.  This is with both ‘normal’ configuration setting and ‘vdpau slim’.  Debugging is therefore a bit tricky.
   
  Checking logs 'in situ' is impossible but I can see them if I connect the drive to another system via USB and load PMagic.
   
  cat /var/log/syslog ¦ grep –i nvidia ¦ grep 'Apr 28 20:34'
   
  > Apr 28 20:34:14 Mythtv kernel: [   11.182152] nvidia: module license 'NVIDIA' taints kernel.

  Apr 28 20:34:14 Mythtv kernel: [   11.201821] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
  Apr 28 20:34:14 Mythtv kernel: [   11.214970] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:02:00.0 on minor 0
  Apr 28 20:34:14 Mythtv kernel: [   11.214979] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.38  Wed Jan  8 19:32:30 PST 2014
  Apr 28 20:34:15 Mythtv kernel: [   14.062284] input: HDA NVidia HDMI/DP,pcm=7 Phantom as /devices/pci0000:00/0000:00:07.0/sound/card0/input21
  Apr 28 20:34:15 Mythtv kernel: [   14.062520] input: HDA NVidia Front Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input20
  Apr 28 20:34:15 Mythtv kernel: [   14.062599] input: HDA NVidia Line Out Side as /devices/pci0000:00/0000:00:07.0/sound/card0/input19
  Apr 28 20:34:15 Mythtv kernel: [   14.062661] input: HDA NVidia Line Out CLFE as /devices/pci0000:00/0000:00:07.0/sound/card0/input18
  Apr 28 20:34:15 Mythtv kernel: [   14.062724] input: HDA NVidia Line Out Surround as /devices/pci0000:00/0000:00:07.0/sound/card0/input17
  Apr 28 20:34:15 Mythtv kernel: [   14.062785] input: HDA NVidia Line Out Front as /devices/pci0000:00/0000:00:07.0/sound/card0/input16
  Apr 28 20:34:15 Mythtv kernel: [   14.062848] input: HDA NVidia Line as /devices/pci0000:00/0000:00:07.0/sound/card0/input15
  Apr 28 20:34:15 Mythtv kernel: [   14.062912] input: HDA NVidia Rear Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input14
  Apr 28 20:34:15 Mythtv kernel: [   14.062975] input: HDA NVidia Front Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input13
  Apr 28 20:34:19 Mythtv kernel: [   17.780580] nvidia 0000:02:00.0: irq 42 for MSI/MSI-X
  Apr 28 20:34:25 Mythtv nvidia-persistenced: Started (2007)
   
   
  /etc/log/nvidia-prime-upstart.log has only one message 'sorry but your hardware configuration is not supported'.
   
  I've found these web articles which describe similar symptoms:
   
  [https://bbs.archlinux.org/viewtopic.php?id=175820](https://bbs.archlinux.org/viewtopic.php?id=175820) 
   I’ve checked /etc/X11/xorg.conf – no such file but there is one xorg.conf.04172014 which has the suggested option lines in but copying this to xorg.conf has made no difference.
   
  [http://ubuntuforums.org/showthread.php?t=2200321](http://ubuntuforums.org/showthread.php?t=2200321)  in Unicorn development.
   
  This software system is not stable enough to do any configuration or compiling (assuming I could climb that learning curve) – my only reliable way of changing the disk is externally via (say) a Pmagic disk or a total reload.
   
  Any one else had these symptoms?  Any suggestions?

  Phil

---

### Post by blm-ubunet on 2014-04-29
You can boot the machine in "safe graphics mode" from the grub boot menu (hold down <shift>).
You can also choose a previous kernel version that does not have the nVidia module.

I would get into PC via grub/safe-mode & try install the latest legacy driver nVidia 304 (by jockey - additional drivers app)

---

### Post by khPWXxF on 2014-04-30
Sounds good.  Will try it asap and report back.  Thanks
Phil

---

### Post by khPWXxF on 2014-05-01
Success, but a tortuous path it was.  This is what I found:
 
Use of the left shift key to get recovery mode is a bit hit and miss.   Tapping usually works, holding down at other times worked.
 
Advanced option gives a menu the most likely item being “Root Option – drop to shell prompt” but that opens the disk in read-only mode so is not helpful.
 
If you choose “Network option” first it gives a (fatal) warning :   
Mode Manager – couldn’t find support for device at ‘/sys/devices/pci0000:00.0a.0’ not supported by any plugin.    However, this switches the disk to read/write mode and puts you back at the safe options menu.
 
You can then use the “Root” option – this time, (illogically) to a shell with read/write mode.
 
Unfortunately,
```
sudo apt-get update
sudo apt-get install jockey-gkt.
``` 
says that jockey has been replaced by ubuntu-drivers-common – a change which came in with 12.10.  Since ubuntu-drivers-common seems to be gui based that’s not helpful.
 
I found a program via google called ubuntu-drivers but documentation on this is pretty hard to find:
```
Ubuntu-drivers list
```
Showed a list of drivers including nvidia 311 and nvidia 304.   The 311 was  replaced with 304 with:
```
sudo apt-get install nvidia-304
```
This driver is more stable than 311 but not as good as 295.  Limited testing with VDPAU slim and VDPAU normal works fine with SD recordings but the HD demo in setup (man trudging through snow) flickers a bit but it was 100% solid with 295.

Thanks for the hints [blm-ubunet]("http://ubuntuforums.org/member.php?u=1899844")
 Now for the other problems.

Phil

PS how do I change the title to [SOLVED] ?

---

### Post by blm-ubunet on 2014-05-01
Sorry should have given you some cmd line options to install nVidia driver..

AFAIK You need to hold down <shift> immediately because the grub delay can be set to zero.
The disk check remounts filesystem as r/w.
I get the modemmanager error as well..just <ctrl>+<c> to move on.

I would have used:
dpkg -l nvidia*
to see what was installed & then apt-get to purge/install

You do know that most cmds auto-complete/hint with possible solns with <TAB> key?
apt-get install nvid

I've been using 304 (on 10.04) for many months with GT240. rock solid.
I have read that nVidia had problems with recent kernels &/or with last Xorg abi changes.

---

