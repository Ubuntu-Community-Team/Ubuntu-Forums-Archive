---
title: "Adding Nvidia GeForce 210 Video Card"
date: 2010-01-05
forum: Multimedia Software
---

### Post by Ian2222 on 2010-01-05
I have a 64 bit computer with a 64 bit distribution of Ubuntu. The driver for the onboard video card wasn't supported beyond 8.04, so I didn't upgrade. Yesterday, I bought a NVIDIA GeForce 210 video card. I installed it and Ubuntu detected it and worked, but the resolution was limited to 640x480 (I think). I figured this would be corrected by updating, so I updated to 9.04. When I had to restart, the option to select which OS (Linux or Win) came up, I selected 9.04, and the ubuntu symbol came on. The status bar went to the end and the screen turned black, flickered 5 times, turned black and stopped progressing. The xorg.conf file is:

Section"Driver"
Identifier  "Configured Video Device"
Driver  "vesa"
EndSection

Section"Monitor"
Identifier "Configured Monitor"
EndSection

Section"Screen"
Identifier  "Default Screen"
Monitor  "Configured Monitor"
Device  "Configured Video Device"
EndSection

I tried changing the driver from "vesa" to "nv" without any effect.

Does anyone have any idea what I should do to get this to work? Thanks in advance,

Ian

---

### Post by inobe on 2010-01-05
did you check in system> administration> hardware drivers ?

if there is a driver listed' activate it and restart.

btw in the xorg.conf it should be glx instead of nv but worry about that later.

---

### Post by Ian2222 on 2010-01-05
There wasn't after I updated. I can't check that now, as I can't get Ubuntu to start. I can use the terminal to check xorg.conf, but I can't get to the graphical interface.

---

### Post by RedSingularity on 2010-01-05
How about deleting the xorg file and setting up a fresh one?

---

### Post by Ian2222 on 2010-01-05
How do I set up a new xorg file from the terminal?

---

### Post by inobe on 2010-01-05
maybe reconfigure xorg ?

he has the new card installed, i guess that would be the best approach.

```
sudo dpkg-reconfigure xserver-xorg
```


run that and restart

---

### Post by gradinaruvasile on 2010-01-05
Its 

sudo dpkg-reconfigure -phigh xserver-xorg

If you want a fresh xorg.conf configuration.

Your card is new, so it may be that the opensource nv (basic nvidia driver without acceleration included in Ubuntu) driver isnt picking it up as a compatible device. It happened to me with a Nvidia 8200 integrated GPU. I had to install the full Nvidia driver to get X server work.
In this case the simplest method is to go to the Nvidia site, download the latest driver (you need the latest because the card is new):

[http://us.download.nvidia.com/XFree86/Linux-x86_64/195.30/NVIDIA-Linux-x86_64-195.30-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/195.30/NVIDIA-Linux-x86_64-195.30-pkg2.run)

and launch it in text mode:

go to the drivers folder:

cd /path/to/driver/

make the downloaded file executable:

chmod +x NVIDIA-Linux-x86_64-195.30-pkg2.run

and run the file:

sudo ./NVIDIA-Linux-x86_64-195.30-pkg2.run

Make sure you answer yes to the autoconfiguration question at the end.

If you installed this driver, DO NOT enable the hardware driver later in the graphical environment, because it is already installed with all its features.

---

### Post by inobe on 2010-01-05
with the directions above' when you get to your desktop don't run updates if it includes a linux kernel, if you update the linux kernel you will have to purge the old nvidia install and do it again, a linux kernel update will break your nvidia driver.

---

### Post by gradinaruvasile on 2010-01-05
No, no need to purge, just plain reinstall, exactly the same method as the above. It is a minor inconvenience because you do have to reboot anyway. Kernel updates dont happen that often though.

I corrected the link to point to the correct installer (i gave the 32-bit installer by mistake before).

---

### Post by Ian2222 on 2010-01-05
Thanks, but how can I read the driver? I'm in a terminal before Ubuntu starts up. I can see the media folder, the only subfolders are cdrom and cdrom0. When I have a CD in, it still doesn't see any files on it. I tried using a flash drive, but it didn't see it. How can I write this to the hard drive? I'm a windows partition currently. Thanks.

---

### Post by gradinaruvasile on 2010-01-06
If you boot from the cdrom, the cd-rom will be invisible. If you boot from an USB stick, that partition will be invisible. It has to do with the live-cd mounting its squashfs. 
The bottom line is: if you booted from a cdrom, and have the driver on a stick, insert the stick and type dmesg. In the message given by the system you will see the device that is auto created by the kernel, like /dev/sdb1, /dev/sdc1 etc. Now you have to mount that device.
First you have to create a mount point (folder):

sudo mkdir /media/disk

then you have to mount the USB partition:

sudo mount [COLOR="Red"]/dev/sdb1[/COLOR] /media/disk

The red device is example. You should mount the partition (with the number on its end like /dev/sdb1, NOT /dev/sdb, that is the device) that is seen with the dmesg command issued after inserting the stick. DO NOT boot with the stick in the USB port. Insert it just when you need to mount it.

Then 

cd /media/disk/the_folder_where_the_driver_is

and do the things i explained in the above post.


Example of dmesg output on inserting a USB drive:

[168490.496365] scsi 6:0:0:0: Direct-Access     Kingmax  USB2.0 FlashDisk 0.0  PQ: 0 ANSI: 0 CCS
[168490.498314] sd 6:0:0:0: Attached scsi generic sg2 type 0
[168490.513269] sd 6:0:0:0: [sdb] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[168490.514153] sd 6:0:0:0: [sdb] Write Protect is off
[168490.514157] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[168490.514159] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[168490.516893] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[168490.516898]  sdb: [COLOR="Red"]sdb1 sdb2[/COLOR]
[168490.535403] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[168490.535408] sd 6:0:0:0: [sdb] Attached SCSI removable disk

The red text is the interesting one - i have 2 partitions on this particular drive, you should have 1 if you did not partition it.

---

### Post by Ian2222 on 2010-01-06
Thanks, but I still have had no luck. I'm booting in recovery mode of 9.04, if that's not clear. I'm starting at "root@mycomputer". When I typed dmesg, the line where you have "sdb: sdb1 sdb 2", I have only "sdf:  " So, I still can't mount the flash drive. I'm not booting from the cd, but I can't see the contents of the cd. Any other ideas? thanks.

---

### Post by gradinaruvasile on 2010-01-06
Copy-paste the whole dmesg section as i did.

Is the USB drive formatted to vfat?

also, what does

sudo fdisk -l

return (after inserting the thumb drive)

---

### Post by gradinaruvasile on 2010-01-06
Hmmm.. on a second thought, i never tried mounting cds and USB drives in single user mode (recovery mode).
Try it by booting to normal and select "exit to console login" if you have error message or press alt+f1 and login from there with your user. That way the usb/cd mounting should work.

---

### Post by Ian2222 on 2010-01-06
The flash drive is formatted as fat32 as I'm on the windows partition now. I can't copy-paste the dmesg section because I'm on the windows partition. When I'm using the terminal it is in recovery mode and there's nowhere to paste it. 

When am I supposed to select "exit to console login"? I haven't seen that before. I can't get Ubuntu running, so I can't get anything from the graphical interface, if that's what you meant. Thanks.

---

### Post by gradinaruvasile on 2010-01-06
Boot from the normal boot option, not the recovery.
If the Xserver fails to start, you will be given a choice of 3 items, the last of them is to exit to console login. Choose that one and you can log in to text mode.

---

### Post by hysteresis on 2010-01-07
I have one if these cards. I had to load 9.10 to get the video to work correctly (it needs the 185 drivers). HDMI audio still doesn't work, though.

---

### Post by gradinaruvasile on 2010-01-07
The most recent drivers are 195.30 (beta). I recommend it. I use that version on 3 different computers and are rock stable.
I dont know if HDMI is supported, but try using Ubuntu 9.10 with PulseAudio, it may enable the HDMI sound.

---

