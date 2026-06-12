---
title: "Automount in fstab"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by hisotaso on 2010-03-30
I run ubuntu 9.10, and my wife runs winxp. I am trying to setup an automount of her storage (D) drive in my fstab. here is the line in fstab:

//192.168.1.102/D /media/Heather cifs  credentials=/home/jeremiah/.smbcredentials,noexec  0 0

The share mounts with no errors, but when i go into palces and view the share, it is blank, totally empty. I can create and delete documents here, but the next time I open the share, i cant see anything. If i connect to the share using places>connect to server, everything is fine. If i connect using places, network, and browse to her machine, it works just fine. 

Today i did a fresh install of karmic, installed smbfs, added the above line to fstab, same issue. I have searced and searched but I haven't found a problem exactly like this. This setup has been working fine until sometime recently. I cant be sure exactly when it stopped working, or why. The reason I need it to automount is I have several applications that point to that drive. It is worth noting i have tried several variations on the line in fstab, all with the same results. Any ideas?

---

### Post by johnson.d on 2010-03-30
You can try mounting the share manually using the following command and troubleshoot using the error message displayed.

$ sudo mount -t cifs //192.168.1.102/D /media/Heather -o user=<username>

---

### Post by hisotaso on 2010-03-30
johnson thanks for the reply. When i use that command i get the exact same result. It asks for my password, i enter it, then it proceeds to mount the drive with no errors. However, i cannot see anything on the drive.

---

### Post by hisotaso on 2010-03-31
bump

---

### Post by hisotaso on 2010-03-31
herry, while I appreciate any and all assistance, your post does not seem...helpful? All I am trying to do is automount a windows share OVER THE NETWORK, not physically connected to my machine on boot. Ive had it setup this way for a couple years now with no issues. This should be as simple as install smbfs and add a line in fstab per [https://wiki.ubuntu.com/MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently"). Are you saying that this method is no longer valid and I must use LVM? "LVM allows you to create logical volumes out of the physical storage resources on your machine"...this is not my issue at all...I can browse to the drive through places, but cannot view the files if i use the mount command at command line or mount through fstab...

---

### Post by feistybird on 2010-04-06
> **hisotaso said:**
> herry, while I appreciate any and all assistance, your post does not seem...helpful? All I am trying to do is automount a windows share OVER THE NETWORK, not physically connected to my machine on boot. Ive had it setup this way for a couple years now with no issues. This should be as simple as install smbfs and add a line in fstab per [https://wiki.ubuntu.com/MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently"). Are you saying that this method is no longer valid and I must use LVM? "LVM allows you to create logical volumes out of the physical storage resources on your machine"...this is not my issue at all...I can browse to the drive through places, but cannot view the files if i use the mount command at command line or mount through fstab...

I've similar problems, my samba share stopped to auto mount by the fstab, (it was working correctly before) , and I have to manually re-mount the fstab again by : sudo mount -a after login...

I also tried to write a script to auto mount my samba shares by using  "update-rc.d" which runs the script automatically on boot up, but this old trick failed to work too...  then I tried to put my script manually into /etc/rc1.d ~ rc5.d, but Ubuntu still doesn't want to run it automatically... it's really annoying 

My OS is Ubuntu 9.10

---

