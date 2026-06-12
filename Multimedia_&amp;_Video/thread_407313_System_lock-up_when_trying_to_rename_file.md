---
title: "System lock-up when trying to rename file"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by uboltun on 2007-04-12
This is not the first report of the problem and as far as I know it is caused by nvidia driver. The only bit of information I would like to add is that I tracked it down to a certain action and it might be helpfull to find a more resonable solution then turning off acceleration, hdparm etc. 

The graphical interface (Xfce ) locks up and does not respond to keyboard or mouse. This happans when I right click on the file in pcman and try to rename it.  Below is the system log messeges.

Apr 11 23:36:07 localhost kernel: NVRM: Xid: 13, 0000 02005600 00000056
00000c28 01400000 00000080
Apr 11 23:36:57 localhost shutdown[7429]: shutting down for system halt
Apr 11 23:36:58 localhost init: Switching to runlevel: 0
Apr 11 23:36:59 localhost gconfd (####-6464): Received signal 15,
shutting down cleanly
Apr 11 23:36:59 localhost gconfd (####-6464): Exiting
Apr 11 23:37:01 localhost shutdown[7458]: shutting down for system halt

lsmod | grep nvidia
nvidia               3922060  12
agpgart                26184  1 nvidia

lspci | grep -i nvidia
0000:01:00.0 VGA compatible controller: nVidia Corporation NV15BR [GeForce2 Ultra, Bladerunner] (rev a4)

NVIDIA driver was installed from NVIDIA-Linux-x86-1.0-7184-pkg1.run.
This is the driver section of xorg.conf : 

Section "Device"
        Driver  "nvidia"
        Option  "RenderAccel"   "true"
        Option  "AllowGLXWithComposite" "true"
        Identifier "NVIDIA Corporation NV15BR [GeForce2 Ultra, Bladerunner]"
        Option "DPMS" "true"
        Option "NvAGP" "1"
EndSection

I remamber experimenting and I think turning off "RenderAccel" would fix the problem ,  but I would rather not do that.

I hope this gives one more little peace to the puzzle and may be one day I will enjoy my ubuntu box without nasty lockups.

P.S. I have recently experimented with xcommgr and found that running xcommgr -cC would lock the screen as well. When I turn on windows shadows in compisite manager of xfwm4 and try to resize the window the same thing happans. All other effects work just fine (enjoing right now). Running xcommpgr -fF , xcompmgr -a is also withou problems.

---

