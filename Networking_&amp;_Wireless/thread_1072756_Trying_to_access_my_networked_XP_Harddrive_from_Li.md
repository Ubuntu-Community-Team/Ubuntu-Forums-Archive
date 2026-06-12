---
title: "Trying to access my networked XP Harddrive from Linux"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by scenerio on 2009-02-17
Hello, 

I am trying to access my XP Drive so that I can make a complete backup of it using my Linux server. I currently have Samba installed on my Linux (Ubuntu 8.04) box and I have been able to map some linux shares from Windows XP (using the map newtwork drive tool)

I am able to ping both computers from each other, but when I try to mount the XP Drive in Linux it cannot find my XP computer. I try to mount using the following command

```
sudo mount -t ntfs-3g //desktop/xpdrive /mnt/desktop
```

And I get the error message 

Failed to access volume '//desktop/xpdrive': No such file or directory Please type '/sbin/mount.ntfs-3g --help' for more information.)

Please help. Thank you - Phil

---

### Post by yoyoned on 2009-02-17
try this

sudo mount -t ntfs-3g /dev/sda1 /mnt/desktop

---

### Post by scenerio on 2009-02-17
Isn't /dev/sda1 the harddrive on my Linux machine? I want to mount a networked XP drive on another computer to my linux box. But I did try that command and got this message.

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by yoyoned on 2009-02-17
Normally XP is on either sda1 or sda2 depending on where the resote partition lives.  Do you know where your windows partition is?

---

### Post by yoyoned on 2009-02-17
I just noticed you said the drive is networked.  If it's on another machine and being shared with smb, you dont need ntfs-3g

---

### Post by scenerio on 2009-02-17
Hi yoyoned, 

Thank you for the help thus far, but I am still having issues. 

I took out the ntfs-3g and it still did not work. So I tried 

 ```
sudo mount //192.168.1.4/xpdrive/test /mnt/desktop
```

Where 192.168.1.4 is my XP desktop/xpdrive is hardrive and test is the folder. I am trying to mount to the /mnt/desktop directory in linux

I received the following message 

retrying with upper case share name
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

---

### Post by Iowan on 2009-02-17
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=288534") how-to for mounting Samba shares?

---

### Post by scenerio on 2009-02-17
Hi Iowan, 

I followed that tutorial and retried the command, and the commands they gave me. 

I still get this response

```
retrying with upper case share name
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

I know the netbios is correct b/c I can ping it by name from command line. 

This was my command. 

```
sudo mount -t cifs //xpdesktop/xpdrive /mnt/desktop -o guest,rw,guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0
777
```

Am I missing something basic here?

---

### Post by scenerio on 2009-02-18
It only took me 12 hours to figure this out, and per usual it came down to something basic. 

Sometimes when you share a drive in windows they automatically add in a space between the drive name and the drive letter that windows assigns to it. For example, 

My C: drive had the name USER - when windows shares this drive it shares it by the name of USER (C). This caused me problems when I tried to mount the drive because of the space and parenthesis in the share name. Make sure when you enter your commands to mount the drive you include quotes around any drive name with a space or other characters in it (or change the drive name to get rid of any complicating characters/spaces). 

mount -t cifs //DESKTOP/"USER (C)"/ /mnt/XPdesktop etc...etc...

To Mount any windows shares I would try the following website. - Very good and ultimately led me to the answer. Also the link IOWAN Posted above was useful. 

[http://industriousone.com/mounting-windows-shares-ubuntu]("http://industriousone.com/mounting-windows-shares-ubuntu")

This was the error I received when I had problems:

retrying with upper case share name
mount error 6 = No such device or address

---

