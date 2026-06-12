---
title: "nvidia driver problem"
date: 2006-07-16
forum: Multimedia &amp; Video
---

### Post by martinielsen on 2006-07-16
Hi.

I'm an absolute Linux newbe and was recommended Ubuntu. I have installed Dapper Drake 6.06 but the nvidia driver installation has been keeping me up all night. I get some errors in the process and i have searched on Google for solutions, but now i find myself in a dead end ](*,) I think i need some help :( 

I use this guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

But when i run the "sudo nvidia-glx-config enable" i get the error described here:
[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/11743](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/11743)

I try to use the "fix" command "md5sum /etc/X11/XF86Config-4 | sudo tee /var/lib/xfree86/XF86Config-4.md5sum" suggested in the link above, but something must be wrong because the terminal return this:

:~$ md5sum /etc/X11/XF86Config-4 | sudo tee /var/lib/xfree86/XF86Config-4.md5sum
md5sum: /etc/X11/XF86Config-4: No such file or directory
Password:
tee: /var/lib/xfree86/XF86Config-4.md5sum: No such file or directory

I can see that the folder and filename may not be right, so i tried to correct it to:

md5sum /etc/X11/config/cf/xorg.cf | sudo tee /var/lib/x11/xorg.conf.md5sum
bca6b5c88f05a882dcca74767cd6512e  /etc/X11/config/cf/xorg.cf

and

md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
f0618b3f9dacad97212ebafb7087ff87  /etc/X11/xorg.conf

None of the commands works though, and i realize that i must do something wrong.

I'm beginning to get desperate, does anyone know the exact and correct command line? :confused:

---

### Post by tseliot on 2006-07-16
Try with:
```
sudo dpkg-reconfigure xserver-xorg
```

and select the "nvidia" driver. Press ENTER whenever you don't know the answer to a question.


And BTW next time please use my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

The guide on the official Wiki uses "nvidia-glx-config enable" which is broken in Dapper.

---

### Post by martinielsen on 2006-07-17
It worked perfect with method 1 - thanks!

My Ubuntu Dapper Drake 6.06 is a new installation so there were a lot of available updates in the auto update notification (about 129 updates). I downloaded all the updates (after installing the nvidia driver with method 1) and after reboot there was 2 different kernel versions in the GRUB loader, version 2.6.15-26-386 and 2.6.15-23-386, so i think the kernel was updated somehow from 2.6.15-23-386 to 2.6.15-26-386 with all the updates. I can read in your guide that when the kernel is updated i have to reinstall the nvidia driver, but i have not done anything after the kernel was updated and the driver still works fine even when i load kernel 2.6.15-26-386. Should i repeat method 1 now that the kernel is updated - even if i works?

Martin

---

### Post by tseliot on 2006-07-17
> **martinielsen said:**
> It worked perfect with method 1 - thanks!

My Ubuntu Dapper Drake 6.06 is a new installation so there were a lot of available updates in the auto update notification (about 129 updates). I downloaded all the updates (after installing the nvidia driver with method 1) and after reboot there was 2 different kernel versions in the GRUB loader, version 2.6.15-26-386 and 2.6.15-23-386, so i think the kernel was updated somehow from 2.6.15-23-386 to 2.6.15-26-386 with all the updates. I can read in your guide that when the kernel is updated i have to reinstall the nvidia driver, but i have not done anything after the kernel was updated and the driver still works fine even when i load kernel 2.6.15-26-386. Should i repeat method 1 now that the kernel is updated - even if i works?

Martin

Please, read this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

---

### Post by martinielsen on 2006-07-17
Thanks for your help, and great guides! :-D

---

