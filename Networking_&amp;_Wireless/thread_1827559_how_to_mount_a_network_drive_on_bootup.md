---
title: "how to mount a network drive on bootup?"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by rebeltaz on 2011-08-18
My laptop is connected to my network through wifi. One of my desktops is always running as a file server for the rest of the network. Currently, to access that file server, I have to manually mount the network drive each time I boot the laptop. I have tried adding a line to fstab to have the drive mounted when the system first boots up, but since the wireless connection isn't active yet, the system hangs with an error message saying that the drive was not able to mount correctly and I have to press a key to continue. 

My question is this: is there any way to have the system automatically mount the network drive AFTER the network connection has become available AND, if for some reason the drive is not able to mount (i.e. I'm on the road and the laptop logs into a different network), it simply bypasses that and continues booting without displaying an error?

---

### Post by Phenex1978 on 2011-08-18
Are you using Samba or NFS or another network filesystem ?

Anyway, you have to edit fstab

In terminal, type :

sudo gedit /etc/fstab

then enter your password

You have then to add a line to the file with your network filesystem, but it depends of the file system you are using and the type of access you want to have.

You can also use Webmin web administration console if you prefer to edit it with a graphical interface

---

### Post by lmarmisa on 2011-08-18
I recommend to add a new bookmark on Nautilus with your network drive or create a launcher on the desktop pointing to the shared drive.

In the first case, open Nautilus -> Network and go to the remote folder of your network drive. Then select Bookmarks -> Add Bookmark.

If you prefer the launcher, right click on the desktop and Create Launcher, Type Location, give it a name, and Location smb://hostname/shared_folder.

Using these solutions, you will be able to mount your remote folder with only one or two cliks.

---

### Post by Morbius1 on 2011-08-18
One thing that meets all your requirements is Gigolo. Here's a mini HowTo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Gigolo when set up that way will probe the network at user specified intervals and mount the remote share when it becomes available. It has other advantages over the traditional fstab method as well but alas it does have one drawback. Just like mounting it through Nautilus the default mount point is in a hidden directory within your home directory:
/home/user-name/.gvfs/share-name on host-name.

That may not be an issue for you but if it is that's why the gods created symbolic links :wink:

---

### Post by rebeltaz on 2011-08-19
> **lmarmisa said:**
> I recommend to add a new bookmark on Nautilus with your network drive or create a launcher on the desktop pointing to the shared drive.

I tried both of these and I get the same problem as when I (usually) click on the folder in Nautilus - the folder cannot be mounted. Even when it does mount, it isn't really mounted in such a way that programs such as Banshee can access it.

> **Phenex1978 said:**
> Are you using Samba or NFS or another network filesystem ?

Anyway, you have to edit fstab

I am using Samba and I did try to add the line to fstab. That was my main complaint - fstab tries to mount the folder before the network is available.

> **Morbius1 said:**
> One thing that meets all your requirements is Gigolo. Here's a mini HowTo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Seems like a bit of a resource hog since it continually polls for new network connections to mount, but I will look at it this weekend.

---

### Post by fdrake on 2011-08-19
> **Morbius1 said:**
> One thing that meets all your requirements is _**[COLOR=Red][SIZE="4"]Gigolo[/SIZE][/COLOR]**_ 
first time I hear about this program, but I am sure I won't forget it for sure...:D:D:D

---

### Post by lmarmisa on 2011-08-20
> **rebeltaz said:**
> I tried both of these and I get the same problem as when I (usually) click on the folder in Nautilus - the folder cannot be mounted. Even when it does mount, it isn't really mounted in such a way that programs such as Banshee can access it.



If the shared folder cannot be mounted using Nautilus, I recommend to check the samba connection problem with the command **smbclient**. Open a terminal and type the command:

```

smbclient -U username //server/share

```

**smbclient** supports several commands: dir, cd, get, mget, put, mput, quit and many more.

This is an example where no problems were detected:

```

luis@UB1010ENG:~$ smbclient -U luis //server1/tmp
Enter luis's password: 
Domain=[SERVER1] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \> dir *.iso
  ubuntu-11.04-desktop-i386.iso       A 718583808  Thu Apr 28 14:13:12 2011

		55868 blocks of size 4194304. 13130 blocks available
smb: \> mget *.iso
Get file ubuntu-11.04-desktop-i386.iso? y
getting file \ubuntu-11.04-desktop-i386.iso of size 718583808 as ubuntu-11.04-desktop-i386.iso (11051.6 KiloBytes/sec) (average 11051.6 KiloBytes/sec)
smb: \> quit
luis@UB1010ENG:~$ 


```

---

### Post by Morbius1 on 2011-08-20
> 

                   [QUOTE]Originally Posted by **lmarmisa**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11163070#post11163070")                 
                 *I recommend to add a new bookmark  on Nautilus with your network drive or create a launcher on the desktop  pointing to the shared drive.*
I tried both of these and I get the same problem as when I  (usually) click on the folder in Nautilus - the folder cannot be  mounted. Even when it does mount, it isn't really mounted in such a way  that programs such as Banshee can access it.[/QUOTE]'Tis mounted but in an unlikely place: /home/user-name/.gvfs/share-name on server-name

---

### Post by rebeltaz on 2011-08-22
> **lmarmisa said:**
> If the shared folder cannot be mounted using Nautilus, I recommend to check the samba connection problem with the command **smbclient**.

I have done that. I've been having this trouble with Nautilus for over a year. One of the first things I did was try to connect with smbclient. I have never had any trouble doing that. And I never have any trouble as long as I actually mount the shared folders, either with fstab or mount.

---

### Post by gnulab on 2011-12-06
I find that when you "mount" through Nautilus, it is a pseudo mount. 

When I use firefox to attach a file that reside on a network that is "mounted" through nautilus, the "drive" isn't there. It's different if you mount it via /etc/fstab. It's there.

Hope I make sense.

---

### Post by Morbius1 on 2011-12-06
> When I use firefox to attach a file that reside on a network that is "mounted" through nautilus, the "drive" isn't thereSure it is:

* Make sure you actually mounted the network share through Nautilus first.
* In firefox when prompted for the location right click an empty space in the dialog box and select "Show Hidden Files"
* Then mozy on over to : .gvfs/share-name on server-name

---

