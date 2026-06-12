---
title: "Mythbuntu will not boot if Network Share down"
date: 2014-04-10
forum: Mythbuntu
---

### Post by diesel48 on 2014-04-10
This must be a problem others have had. I mount my videos share from my NAS via FSTAB. I have found that if my NAS is down mythbuntu will not boot. It sits at a screen saying mount down. Press X to skip or try manually. Of course these options do not work. What do I need to do change in my FSTAB to just have it skip this mount if the NAS is down?

---

### Post by Kirboosy on 2014-04-10
What does your FSTAB look like currently?

You could try changing it from mounting on boot to mounting during login.
> 
If  for some reason/etc/rc0.d/S31umountnfs.sh (networking problems for  example) the automatic mounting during boot doesn't work, you can add  the "noauto" parameter to your smbfs fstab entry and then have the share  mounted at login. 

In /etc/fstab: 

//servername/sharename  /media/windowsshare  cifs  noauto,credentials=/home/ubuntuusername/.smbpasswd  0  0In /etc/rc.local: 
mount /media/windowsshare
exit 0

[Mount Windows Shares Permanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently#Mount_during_login_instead_of_boot")

Hope that helps!
~Caboose

---

