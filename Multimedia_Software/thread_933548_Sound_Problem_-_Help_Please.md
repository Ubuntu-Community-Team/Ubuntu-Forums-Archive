---
title: "Sound Problem - Help Please"
date: 2008-09-29
forum: Multimedia Software
---

### Post by dgoddard1 on 2008-09-29
My new Dell Studio 1535 came with a working sound system.  Shortly after my nubi efforts to install the modem (US Robotics Model 5637 USB Modem) I noticed that I have no sound for any applications whatsoever. The modem works.

Based on the comments at  
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)
It is fairly evident to my nubi mind that the modem installation process somehow did in the sound system.  However since I was neither upgrading Ubuntu nor the kernel, I do not believe that I should try to execute the fixes there and I am not knowledgeable enough to figure out which parts of what is given there are relevant to me.  

Prior to following the instructions on the US Robotics Disk I did install gnome-ppp dial up tool from the .deb file I downloaded but I did not notice whether the sound was turned off by that or the subsequent "Trouble Shooting" instructions I executed from the US Robotics CD.  After I executed the U.S. Robotics instructions I had a functioning modem.

There is also the possibility that something else has caused the problem

##### US Robotics Trouble Shooting instructions follow: #####

Troubleshooting:

Open a terminal shell and log in as root.

1. Verify modem enumeration with the following command:

lsusb

Below is an example output.

Bus 001 Device 002: ID 0baf:0303 U.S. Robotics

2. Verify the CDC ACM module as loaded with the following command:

lsmod

If the version of Linux kernel has the CDC ACM driver compiled into it, you
should now be able to use a terminal emulator program (for example: minicom)
to attach to the modem.

If the kernel has the CDC ACM driver built as a module, then you may have to
enable the driver with the following command:

modprobe acm
(used in 2.4.x kernels)

modprobe cdc_acm
(used in 2.6.x kernels)

3. Verify device node creation.

Some distributions will automatically create a device node
for the modem in /dev. Below is the device node as created in Fedora 7.

crw-rw----  1 root   uucp 166,   0 2007-09-12 10:33 ttyACM0

The CDC ACM driver allows up to 32 modems. If the device node does not exist,
create one using the following command:

mknod /dev/ttyACM0 c 166 0

Additional device nodes can be created for additional modems as follows:

mknod /dev/ttyACM1 c 166 1 
mknod /dev/ttyACM2 c 166 2 
mknod /dev/ttyACM3 c 166 3

4. Access the modem.

Use a terminal emulator program (for example: minicom) to access the modem using
the device node created above. For example, setup the serial port for minicom to
use the device node /dev/ttyACM0.

5. Internet dialers.

Applications such as WvDial and KPPP may require access to the modem via the
/dev/modem device node.

You can set up a symbolic link from /dev/modem to the ACM modem device by using
the following command:

ln -s /dev/ttyACM0 /dev/modem

##### US Robotics Trouble Shooting instructions end: #####

---

### Post by markbuntu on 2008-09-29
Modems are treated like sound cards since that is what they basically are. There is a section in this guide about setting the default order of your sound cards for ALSA which should fix you up:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

