---
title: "Prevent camera auto-mount with udev rules, or unmount via script?"
date: 2012-11-02
forum: Multimedia Software
---

### Post by JD Hupp on 2012-11-02
[SIZE=-1][FONT=Arial]I'm trying to get a Canon         Powershot G1 USB-connected digital camera working with [SIZE=-1]remote           capture (tethering) using either Entangle or [SIZE=-1]Gtkam[SIZE=-1].

I prefer Entangle (home page: [/SIZE][/SIZE][/SIZE][/FONT][/SIZE][http://entangle-photo.org/](http://entangle-photo.org/)[SIZE=-1][FONT=Arial][SIZE=-1][SIZE=-1], installed via GetDeb at [/SIZE][/SIZE][/FONT][/SIZE]
[http://www.getdeb.net/software/Entangle](http://www.getdeb.net/software/Entangle)[SIZE=-1][FONT=Arial][SIZE=-1]) b[/SIZE]ecause it seems to be at higher stage of development for remote capture, but both programs initially fail with the same prob[SIZE=-1]lem.
[SIZE=-1] 
            [SIZE=-1]Both apps get tripped up on the fact that               Lubuntu auto-mount[SIZE=-1]ed the cam[SIZE=-1]era's built-in memory.  Gtkam simply generates an error                   message about the camer[SIZE=-1]a already b[SIZE=-1]eing in use.  Entangle notes the same                       condition and offers to unmount the camera, but                       approving that causes the program to lock up.
                      
                      [SIZE=-1][SIZE=-1]Either program                           launches OK if I manually unmount the camera                           from the pcmanfm file manager first.[/SIZE][/SIZE]
                      
                      [SIZE=-1]So one [SIZE=-1]work-around to better operation would seem to be to [/SIZE]lau[SIZE=-1]nch [/SIZE]the camera                         program from a script that first unmounts the                         camera.[/SIZE]
                      
                      [SIZE=-1]Post #2 [SIZE=-1]in [http://ubuntuforums.org/showthread.php?t=967104](http://ubuntuforums.org/showthread.php?t=967104)[SIZE=-1] had a solution in the command                             "gvfs-mount -s gphoto2[SIZE=-1].[/SIZE]"[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT]  [SIZE=-1]G[/SIZE]vfs-mount is not installed by default in                       Lubunt[SIZE=-1]u, but [SIZE=-1]i[/SIZE][/SIZE]t's install[SIZE=-1]ed with the[/SIZE] [/SIZE][SIZE=-1][FONT=Arial][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][FONT=Arial][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1]gvfs-bin [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE]package, [SIZE=-1]which i[SIZE=-1]s av[SIZE=-1]ailable from the default                             repos[SIZE=-1].[/SIZE]
                            
                            [SIZE=-1]I also tried "sudo umount                               /home/<user>/.gvfs,"[/SIZE] which                             was the mount point suggested to me by "sudo                             mount."  That ran with[SIZE=-1]out                               error, but the camera did not seem to be                               trul[SIZE=-1]y unmounted[SIZE=-1], and both cam apps errored                                   as before[SIZE=-1].
-----------------------------------

[SIZE=-1]Some[SIZE=-1]one suggested that a cleaner, less-hackish metho[SIZE=-1]d would be to write a udev rule[SIZE=-1] that prevents the ca[SIZE=-1]mera from auto-loading.

[SIZE=-1]So I read up on the topic at [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][http://manpages.ubuntu.com/manpages/karmic/en/man7/udev.7.html](http://manpages.ubuntu.com/manpages/karmic/en/man7/udev.7.html)[SIZE=-1][FONT=Arial][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1][SIZE=-1], but I [SIZE=-1]have[/SIZE] not yet found a way to apply that[SIZE=-1].  Some[SIZE=-1]where[/SIZE] there is probably further reading that w[SIZE=-1]ould[/SIZE] tell me [/SIZE][/SIZE]how to locate the rule that causes the camera auto-mount, but just taking a guess that the [SIZE=-1]go[SIZE=-1]verning rule file was /lib/udev/rules.d/40-libgphoto2-2.rules (since the camera mounts as gphoto2://[usb:00[SIZE=-1]3,004]), I didn't see any rule that would govern auto-mount.

[SIZE=-1][SIZE=-1]I could upload 40-libgphoto2-2.rules [SIZE=-1]some[SIZE=-1]where if any[/SIZE][/SIZE]one wants to see it, but it's 179KB, which is 160KB bigger than this for[SIZE=-1]um allows for text files.[/SIZE]

[SIZE=-1]So unless I can get some pointed advice on where to locate the rule of inter[SIZE=-1]est, it [SIZE=-1]looks to me like [SIZE=-1]trying to write a udev rule would be jumping down a pretty deep rabbit hole.  (I mean deeper than the one I've already jumped down.)[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT]
[/SIZE]

---

### Post by p1977p on 2012-11-02
Go to Removable Drives configuration from the Settings menu. Disable the automount and autoBrowse options. Hope this works. Good luck!!

---

### Post by JD Hupp on 2012-11-02
An interesting idea, but that setting has no granularity -- it's all or nothing with removable drives.  So USB flash drives would not auto-mount either, which is, I'll venture to say, universally expected behavior in desktop environments.

---

### Post by steeldriver on 2012-11-02
I was going to suggest a udev rule matching the device (by vendor / product ID) and using the  ignore_device option... but apparently that's been disabled and the way to do it now is by unbinding the driver from the specific device - have a look here

 [http://superuser.com/questions/148412/remove-kernel-lock-from-unmounted-mass-storage-usb-device-from-the-command-line](http://superuser.com/questions/148412/remove-kernel-lock-from-unmounted-mass-storage-usb-device-from-the-command-line)

[http://lwn.net/Articles/143397/](http://lwn.net/Articles/143397/)

DISCLAIMER: I have never tried this - let us know if it works!

---

### Post by JD Hupp on 2012-11-03
Marcus Meissner from the Gphoto email list helpfully wrote:

[I]gvfs does "virtual" mounts of devices, not only just USB mass storage kinds.

Most remote controllable cameras are not USB Mass storage devices,
and the USB access is in userland, via libusb.

gvfs turns this into a virtual drive that it can represent to Nautilus et.al.
and offers it via "fuse" (userland filesystem) below the ~/.gvfs/ tree.

So looking at udev rules does not help.[/I]

---

