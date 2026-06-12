---
title: "Flickering vertical columns"
date: 2010-07-13
forum: Multimedia Software
---

### Post by glubbdrubb on 2010-07-13
After a fresh install of Lubuntu 10.04, my lcd monitor is covered by flickering vertical columns.

lsmod shows I am using the vga16fb module on an intel onboard graphics card.

I am updated to the latest available xserver available by to synaptics. Everything else is also uptated.

I have tried lower refresh rates and resolutions. The only change is in the width of the columns. This monitor works fine in other systems. Its native resolution is 1440 x 900.

What should I do ?

---

### Post by cavalier911 on 2010-07-13
Try editing the grub2 menu with some of the intel kernel options listed in my tutorial.
See thread #8 here:
[http://ubuntuforums.org/showthread.php?t=1525156](http://ubuntuforums.org/showthread.php?t=1525156)

If that doesn't help,post your graphics hardware info from lspci,lshw.Attach to your reply as text /var/log/Xorg.0.log ,or use paste.ubuntu.com and post URL.

---

### Post by glubbdrubb on 2010-07-14
I tried both intel drivers and xforcevesa, none of them worked.

Here is the info you asked for:

[http://paste.ubuntu.com/463499/](http://paste.ubuntu.com/463499/)
[http://paste.ubuntu.com/463501/](http://paste.ubuntu.com/463501/)

---

### Post by cavalier911 on 2010-07-14
You have sis graphics on your systemboard. 
Now I need more information.
What kernel modules are autoloaded
Does your system have the sis modules.
What is xorg experiencing/detecting as it attempts to start.

Please open terminal:

Run this command to remap kernel modules.

```
sudo depmod -a
```

Combine 1 and 2 on same paste at paste.ubuntu.com and post URL
1.```
lsmod
```

2.```
modprobe -l | grep sis
```

Make copy of Xorg.0.log
```
cat /var/log/Xorg.0.log > xorg.txt
```
Verify xorg.txt contains Xorg.0.log
```
less xorg.txt
```

Attach to Reply to Thread

Additional Options/Manage Attachments/Choose file/xorg.txt/upload

---

### Post by glubbdrubb on 2010-07-15
Here you go:

[http://paste.ubuntu.com/463883/](http://paste.ubuntu.com/463883/)

The X logfile was to large to upload, so I am giving you a this pastbin url instead:

[http://paste.ubuntu.com/463885/](http://paste.ubuntu.com/463885/)

P.S. I do appreciate the help you have given me so far.

---

### Post by cavalier911 on 2010-07-16
If your grub menu is hidden start to tap on the shift key when the MB bios shows to make the grub menu appear. 
Choose the recover option from the boot menu,
There is a failsafeX choice,I tried and it booted me to a black screen,maybe you'll get lucky.
If not,highlight in the recovery menu **root drop to root shell**,tab to ok hit enter login with your root password.

Run this command
```
root@lubuntu:~$ X -configure
```to probe hardware generate xorg.conf.new
```
root@lubuntu:~$ nano xorg.conf.new
```
     Section Screen add what's in bold,save.
        SubSection "Display"
                Viewport   0 0
                Depth     24
             **Modes     "1024x768"**
        EndSubSection

Rename 
```
root@lubuntu:~$ mv xorg.conf.new xorg.conf
```
Move
```
root@lubuntu:~$ mv xorg.conf /etc/X11
```
Reboot
```
root@lubuntu:~$ reboot
```
If that fails
Add what's in bold,save,reboot.
```
root@lubuntu:~$ nano /etc/X11/xorg.conf
```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName	 "Monitor Model"
     **HorizSync     28-64**
     **VertRefresh   60**
EndSection

If that fails
Add what's in bold,save,reboot.
```
root@lubuntu:~$ nano /etc/X11/xorg.conf
```
Section Device
        **#**Driver "sis"
         **Driver "vesa"**

Paste the xorg.conf if you need more help.

---

