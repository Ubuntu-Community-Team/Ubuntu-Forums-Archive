---
title: "radeon 9250l installation"
date: 2010-10-02
forum: Multimedia Software
---

### Post by jgw on 2010-10-02
I have now installed a radeon 9250l display board.  I followed the Ubuntu Radeon documentation page.  It tells me that 3d is supported.  I am not sure that 3d is correct or running. I am running without a xorg.conf file and my current resolution os 1024x768 (which is fine).  I get no errors on boot but want to make sure its correct.
I also did:

sudo nano /etc/default/grub.
Add radeon.modeset=1 to the end of the line GRUB_CMDLINE_LINUX_DEFAULT=.
sudo update-grub

Here are some results of tests, etc.

don@don-desktop:~$ glxinfo |grep vendor
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15

don@don-desktop:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
[sudo] password for don: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libbulletml0d2 liblua5.1-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/2,991kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 185295 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri 7.7.1-1ubuntu3 (using .../libgl1-mesa-dri_7.7.1-1ubuntu3_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 7.7.1-1ubuntu3 (using .../libgl1-mesa-glx_7.7.1-1ubuntu3_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Setting up libgl1-mesa-dri (7.7.1-1ubuntu3) ...

Setting up libgl1-mesa-glx (7.7.1-1ubuntu3) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group gl_conf is broken.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group gl_conf) doesn't exist.

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
don@don-desktop:~$     * To see if your driver uses KMS (Kernel Mode Setting), run command 
bash: syntax error near unexpected token `('
don@don-desktop:~$ 
don@don-desktop:~$ dmesg | grep drm
[    0.000000] Linux version 2.6.32-25-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 (Ubuntu 2.6.32-25.44-generic 2.6.32.21+drm33.7)
[   15.427799] [drm] Initialized drm 1.1.0 20060810
[   15.658464] [drm] radeon kernel modesetting enabled.
[   15.697090] [drm] radeon: Initializing kernel modesetting.
[   15.703200] [drm] register mmio base: 0xDFEF0000
[   15.703207] [drm] register mmio size: 65536
[   15.704391] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   15.704836] [drm] Generation 2 PCI interface, using max accessible memory
[   15.704939] [drm] radeon: VRAM 128M
[   15.704941] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   15.704944] [drm] radeon: GTT 128M
[   15.704947] [drm] radeon: GTT from 0xE0000000 to 0xE7FFFFFF
[   15.705012] [drm] radeon: irq initialized.
[   15.705165] [drm] Detected VRAM RAM=128M, BAR=128M
[   15.705173] [drm] RAM width 64bits DDR
[   15.709754] [drm] radeon: 128M of VRAM memory ready
[   15.709758] [drm] radeon: 128M of GTT memory ready.
[   15.710025] [drm] radeon: cp idle (0x02000603)
[   15.710246] [drm] Loading R200 Microcode
[   15.960490] [drm] radeon: ring at 0x00000000E0000000
[   15.960515] [drm] ring test succeeded in 0 usecs
[   16.010010] [drm] radeon: ib pool ready.
[   16.010148] [drm] ib test succeeded in 0 usecs
[   16.015341] [drm] Default TV standard: NTSC
[   16.015350] [drm] 27.000000000 MHz TV ref clk
[   16.015359] [drm] DFP table revision: 3
[   16.020415] [drm] Default TV standard: NTSC
[   16.020423] [drm] 27.000000000 MHz TV ref clk
[   16.021898] [drm] Radeon Display Connectors
[   16.021904] [drm] Connector 0:
[   16.021907] [drm]   VGA
[   16.021911] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   16.021913] [drm]   Encoders:
[   16.021916] [drm]     CRT1: INTERNAL_DAC1
[   16.021918] [drm] Connector 1:
[   16.021920] [drm]   DVI-I
[   16.021922] [drm]   HPD1
[   16.021925] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   16.021928] [drm]   Encoders:
[   16.021930] [drm]     CRT2: INTERNAL_DAC2
[   16.021933] [drm]     DFP1: INTERNAL_TMDS1
[   16.021935] [drm] Connector 2:
[   16.021937] [drm]   S-video
[   16.021938] [drm]   Encoders:
[   16.021940] [drm]     TV1: INTERNAL_DAC2
[   16.346569] [drm] fb mappable at 0xD0040000
[   16.346575] [drm] vram apper at 0xD0000000
[   16.346578] [drm] size 3145728
[   16.346580] [drm] fb depth is 24
[   16.346582] [drm]    pitch is 4096
[   16.361333] fb1: radeondrmfb frame buffer device
[   16.361353] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   17.559423] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id

don@don-desktop:~$ glxinfo | grep vendor
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15

Since the documentation seems to apply to the previous version (mine is 10.04) that may be a problem.  I would sincerely appreciate anybody's thoughts on this

---

### Post by Mark Phelps on 2010-10-05
You shouldn't really be installing anything for your card.  

There are no proprietry drivers for your card that will work with current versions of Ubuntu, and the only working drivers, the open-source drivers, are installed by default as part of initial setup.

If you go hacking around installing other packages, you're liable to corrupt something in the display setup.

---

### Post by jgw on 2010-10-07
My problem is that the existing drivers are supposed to give me 3d which they do not.  I then found the radeon documentation that said there was a bug and suggested the fix.  I promptly did not read the screen and posted self inflicted frustration.  After finding the right package I did notice that it had been installed.  Due to the fact that I had screwed around I plan to reinstall and then follow the directions to fix the discussed bug.  Hopefully that will take care of everything.

Thank you for the the thought.

---

### Post by jgw on 2010-10-08
Mark Phelps suggested that I was screwing up and should do nothing.  What happened is that I switched displays (nvidia to radeon) and it was simply not right.  However, his suggestion proved to be exactly correct.  I reinstalled, with the radeon board (there was nothing important on the machine) and the board worked perfectly so I thank Mr. Phelps for pushing me in the right direction.

---

