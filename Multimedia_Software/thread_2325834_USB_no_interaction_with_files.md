---
title: "USB no interaction with files"
date: 2016-05-25
forum: Multimedia Software
---

### Post by theochenko on 2016-05-25
Hi,
i maybe "corrupt" my Kingstone USB flash drive when i kick it from the session without unmount (didn't know before, semi-new on linux).
I put on it Tails, but now i don't see any files on my USB stick (except on disks: 2,6G storage used on the Kingstone)
I had format it but no result, didn't work.
dmesg --> sdb1 = Device Recognized
i can mount and umount it with sudo (u)mount /dev/sdb1
But i can not paste a file or create a new file/folder.
And when i go to tails with virtualbox, an error message about my USB driver.

I can have some hope about it? or should i already go to the USB' shop...

++device operational on windows

---

### Post by sudodus on 2016-05-26
Welcome to the Ubuntu Forums :-)

Since you can mount and unmount the partition on the pendrive, it might still be good. I think it is mounted read-only, but if you have tough luck, it is gridlocked, read-only as a first step to getting totally dead.

Can you read a file from the pendrive?

Can you write a file to the pendrive with superuser permissions? And read that file afterwards?

Assuming that the pendrive is seen as device /dev/sd[COLOR="#cc0000"]b[/COLOR], change drive letter if necessary

```
sudo mount /dev/sd[COLOR="#cc0000"]b[/COLOR]1 /mnt
cd /mnt
sudo bash -c 'echo "Hello World" > hello.txt'
sudo cat hello.txt
```

If this works, it is only a problem with permissions, and you can get help to fix the permissions.

If you can't write to the file, you should check if there is a small mechanical switch on the pendrive, which can switch write protection on and off.

If nothing else helps and you have Tails on the pendrive I guess you have no personal files there. In that case I suggest that you try to wipe the first megabyte, create a new partition table and a file system. You can do that rather automatically with mkusb. See these links,

[mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

If still no luck, it is possible that the drive is gridlocked, and you had better get a new one. See this link,

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by theochenko on 2016-05-26
okay,
i have written your code and looks like right:

```
sudo mount /dev/sdb1 /mnt
cd /mnt
sudo bash -c 'echo "Hello World" > hello.txt'
/mnt$ sudo cat hello.txt
Hello World
```

So now i should have a problem with permissions, how can i fix it ?

I did:

```
ls -l
-rwxr-xr-x 1 root root 12 mai   26 23:46 hello.txt
```

And when i try to display the usb content, this message appear:

```
This location could not be displayed.
“usb-Kingston_DataTraveler_3.0_1C6F6581FDE2B03019AEAF21-0:0-part1” could not be found. Perhaps it has recently been deleted.
``` 

(maybe due to my failed formatting, or not)

**EDIT by DuckHook**
...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by sudodus on 2016-05-27
Good, the drive is healthy :-)

Different versions of Ubuntu organize mounting of pendrives in different ways, so it helps if you provide some information:

Which version of Ubuntu are you running?

Unmount and unplug the pendrive.

Plug the pendrive into the computer again.

Run the following command in a ***wide*** terminal window and post the output within [noparse]```
tags
```[/noparse] in a reply,

```
lsb_release -a
```

Is the pendrive auto-mounted? In that case how?

```
df
```
```
sudo lsblk -fm  # the output of this command looks best in a wide terminal window
```
```
ls -l /media
```
```
ls -l /media/*
```

-o-

It might work if you change the ownership and or permissions of a subdirectory of /media with the same name as your user name, but it helps to get the information from those commands to get things right.

Unmount and unplug the pendrive.

Run the following commands

```
sudo chown "$USER" /media/"$USER"
```
```
sudo chmod ug+rwx /media/"$USER"
```

and after that plug in the pendrive again.

Does it automount so that it can be written to now?

---

### Post by theochenko on 2016-05-27
In order,

```
omega3@omega3-K55VD:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.10[B]
Release:    15.10
Codename:    wily[/B]
```

I had disabled the Automatic Mount Options from "disks" (in Mount Options), so i always manually mount it (even activate, don't work).
From memory, i did:
```
sudo mkdir /media/usb
sudo mount -t vfat /dev/sdb1 /media/usb
```

i'm pretty sure

```
omega3@omega3-K55VD:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             2979844        0   2979844   0% /dev
tmpfs             599432     9064    590368   2% /run
/dev/sda8       65806076 11697420  50742768  19% /
tmpfs            2997144      636   2996508   1% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            2997144        0   2997144   0% /sys/fs/cgroup
/dev/sda1         303104    42828    260276  15% /boot/efi
cgmfs                100        0       100   0% /run/cgmanager/fs
tmpfs             599432       56    599376   1% /run/user/1000
**/dev/sdb1        2554992       12   2554980   1% /mnt/usb-Kingston_DataTraveler_3.0_1C6F6581FDE2B03019AEAF21-0:0-part1**
```

```
omega3@omega3-K55VD:~$ sudo lsblk -fm
NAME   FSTYPE LABEL    UUID                                 MOUNTPOINT                                                        NAME     SIZE OWNER GROUP MODE
sda                                                                                                                           sda    698,7G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat   SYSTEM   F0D9-0B91                            /boot/efi                                                         &#9500;&#9472;sda1   300M root  disk  brw-rw----
&#9500;&#9472;sda2 ntfs   Recovery B8DA1AE0DA1A9B28                                                                                       &#9500;&#9472;sda2   600M root  disk  brw-rw----
&#9500;&#9472;sda3                                                                                                                        &#9500;&#9472;sda3   128M root  disk  brw-rw----
&#9500;&#9472;sda4 ntfs   OS       94561EC4561EA6D0                                                                                       &#9500;&#9472;sda4 215,6G root  disk  brw-rw----
&#9500;&#9472;sda5 ntfs            B010CBBE10CB89B4                                                                                       &#9500;&#9472;sda5   450M root  disk  brw-rw----
&#9500;&#9472;sda6 ntfs   Data     D22020D42020C179                                                                                       &#9500;&#9472;sda6 181,9G root  disk  brw-rw----
&#9500;&#9472;sda7 ntfs   Restore  DEC4246FC4244C59                                                                                       &#9500;&#9472;sda7    20G root  disk  brw-rw----
&#9500;&#9472;sda8 ext4            bf076bdd-2275-4728-85dd-c6e6220fb201 /                                                                 &#9500;&#9472;sda8  63,9G root  disk  brw-rw----
&#9492;&#9472;sda9 swap            7c448bcb-c832-4cca-84ef-56712e1fd107 [SWAP]                                                            &#9492;&#9472;sda9   5,9G root  disk  brw-rw----
sdb                                                                                                                           sdb      7,2G root  disk  brw-rw----
&#9492;&#9472;**sdb1 vfat**            053A-E767                            /mnt/usb-Kingston_DataTraveler_3.0_1C6F6581FDE2B03019AEAF21-0:0-p &#9492;&#9472;sdb1   2,5G root  disk  brw-rw----
sr0                                                                                                                           sr0     1024M root  cdrom brw-rw----
```

```
omega3@omega3-K55VD:~$ ls -l /media
total 8
drwxr-x---+ 2 root root 4096 mai   27 14:25 omega3
drwxr-xr-x  2 root root 4096 mai   26 01:31 usb
```

```
omega3@omega3-K55VD:~$ ls -l /media/*
/media/omega3:
total 0

/media/usb:
total 0
```

So i should change permissions on a file, from root --> to "$user" with 'chown' cmd?

I'm stopping here the message too much informations, i'm going to glead some infos on File Permissions and back later.

---

### Post by sudodus on 2016-05-27
Thanks for this information :-)

Yes you have mounted the drive manually on the mount point /mnt, you are not using /media, at least not now.

If you want to mount several drives manually, you should create separate mountpoints for them, like you have created omega3 and **usb**. So instead of the commands in my previous post, I suggest the following:

- change ownership and permissions of **/media/usb**

- **mount the pendrive on /media/usb**

```
sudo umount /dev/sdb1

sudo chown "$USER" /media/usb

sudo chmod ug+rwx /media/usb

sudo mount /dev/sdb1 /media/usb
```

Now I think you should be able to read and write without superuser privileges. Maybe you need to unplug after unmounting, and then plug the pendrive back again.

---

### Post by theochenko on 2016-05-27
Ps: I have formatting from FAT to ext4, (quote:"*Don't use fat.  Format the drive in a Linux filesystem. The chown command will not work.  The ownership and permissions of  directories and files are determined enmass by the mount options.*") i have seen that from Linuxquestion. Did it solve the problem? I'm not sure, because i did what you advised me too.

First, yeah i can interact with my usb key, all looks like normal copy,paste etc... in /media/usb

```
omega3@omega3-K55VD:~$ ls -l /media/usb
total 16
drwx------ 2 root root 16384 mai   28 00:19 lost+found
```

but that's not my first motivation..... now i am feeling really confused. In one hand **/media/usb** where the pendrive is mounted and on the other hand **/mnt/usb-Kingston_DataTraveler_3.0_1C6F6581FDE2B03019AEAF21-0:0-part1$**. This last is used on Virtualbox to select a USB device for installing Tails, and i can't choose something like /media/usb as a device.

So i think the good thing to do is to go back in time, suppress the mountpoint /media/usb and relocate it as default location.

It looks like harassing......for you.....maybe.

[If you have an idea about, this is what the error says on Virtualbox when i configure the USB device:  Failed to create a proxy device for the USB device. (Error: VERR_PDM_NO_USB_PORTS).
 

 [TABLE]
 [TR]
 [TD] Code d'erreur : 
[/TD]
 [TD] NS_ERROR_FAILURE (0x80004005)
[/TD]
[/TR]
 [TR]
 [TD] Composant : 
[/TD]
 [TD] ConsoleWrap
[/TD]
[/TR]
 [TR]
 [TD] Interface : 
[/TD]
 [TD] IConsole {872da645-4a9b-1727-bee2-5585105b9eed}
[/TD]
[/TR]
[/TABLE]
]

---

### Post by sudodus on 2016-05-28
If you have ext4, you decide the permissions of files and directories individually. If that is what you want, that's fine. But I don't understand all you are writing.

- Can you read and write files in your pendrive now from the host operating system?

- Can you read and write files in your pendrive now from the guest operating system (inside VirtualBox)?

Don't worry about the way VirtualBox wants it mounted. Let it do it's job the way it wants to do it.

But I think the pendrive will be seen either by the host system or the guest system. I think you should disconnect it from the guest system (in VirtualBox), if you want to use it in the host system.

-o-

I think that the native linux virtual system "KVM and virt-manager" manages USB drives in a better way than VirtualBox.

---

