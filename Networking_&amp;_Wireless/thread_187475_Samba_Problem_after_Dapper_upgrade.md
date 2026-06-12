---
title: "Samba Problem after Dapper upgrade"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by jlhughes on 2006-06-03
I have five computers in a LAN. All of the computers can ping each other.

I have Samba running on one XP box, one OSX box and my Ubuntu box.

Before I upgraded to Dapper everything worked as expected. I could browse the network with Samba and see all of the machines and mount the shares.

After the Dapper upgrade, I can see and mount the Ubuntu share FROM the Windows and OSX boxes. But I CANNOT see or mount the Windows or OSX shares FROM the Ubuntu box.  Sharing Ubuntu from network OK; sharing network shares from Ubuntu  broken.

I am new to Ubuntu and I would appreciate any help in figuring out what needs to be fixed.

This is the output from smbtree:

john@UBUNTU:~$ smbtree
Password:
PRICOM
JOMARI
        \\UBUNTU                        UBUNTU server (Samba, Ubuntu)
                \\UBUNTU\john                   Home Directories
                \\UBUNTU\AdobePDF               Adobe PDF
                \\UBUNTU\AdobePDF7              Adobe PDF 7.0
                \\UBUNTU\Fax_Print              Fax Print
                \\UBUNTU\ML-1710                ML-1710
                \\UBUNTU\ADMIN$                 IPC Service (UBUNTU server (Samba, Ubuntu))
                \\UBUNTU\IPC$                   IPC Service (UBUNTU server (Samba, Ubuntu))
                \\UBUNTU\print$                 Printer Drivers
        \\IMAC                          imac
timeout connecting to 192.168.1.5:445
                \\IMAC\Fax Print        FAXstf Fax Print
                \\IMAC\Adobe PDF        Adobe PDF 3015.102
                \\IMAC\ADMIN$           IPC Service (imac)
                \\IMAC\IPC$             IPC Service (imac)
        \\GIGHZ
                \\GIGHZ\GighzDOCs
                \\GIGHZ\HD2backup
                \\GIGHZ\gighz
                \\GIGHZ\fireweb
                \\GIGHZ\PRINTER3
                \\GIGHZ\GIGHZDesktop
                \\GIGHZ\EPSON           \\PR37498A\USB1
                \\GIGHZ\print$          Printer Drivers
                \\GIGHZ\IPC$            Remote IPC
                \\GIGHZ\My Documents
                \\GIGHZ\mary
                \\GIGHZ\SAMLASER        Samsung ML-1710 Series

Here's the output from smbclient for GIGHZ

john@UBUNTU:~$ smbclient -L GIGHZ
Password:
Domain=[GIGHZ] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        SAMLASER        Printer   Samsung ML-1710 Series
        mary            Disk
        My Documents    Disk
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        EPSON           Printer   \\PR37498A\USB1
        GIGHZDesktop    Disk
        PRINTER3        Printer
        fireweb         Disk
        gighz           Disk
        HD2backup       Disk
        GighzDOCs       Disk
Domain=[GIGHZ] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

When I attempt smb:\\GIGHZ\ from the Network File Browser I get the error message "smb:\\GIGHZ\" is not a valid location.

---

### Post by Uta on 2006-06-03
Your issue is well noted in this forum. It seems Nautilus has got a Samba bug.
You'll have to mount your shares manually until there is a 'fix' posted.

1.) Be sure the smbfs package is installed (search for it in synaptic)
2.) open terminal and go to /mnt
3.) sudo mkdir samba
4.) sudo mount -t smbfs -o username=your_user_name //your_server/your_share /mnt/samba/

This worked for me after I installed a missing file (in my case it was 'smbfs')
It's a pain, maybe someone will share their desktop mount script with all of us?

---

### Post by s31523 on 2006-06-03
Nice instructions Uta :p 

You can also add password to the mount command, as in, password=password, which would be the samba user password, if you have one.

To create a shortcut, right-click on your desktop and select 'Create Launcher'.  In the name type "Mount Samba Share", or whatever you like, and for the command, put your mount command.  Be sure to select the 'Run in terminal' checkbox.  This will create an icon on your desktop that you can click to get to.  Make sure you debug your command (i.e. try it in a terminal window first) before putting it in a launcher script, since the launcher script will flash the terminal window and you won't see the output of the mount command.  You may want an umount script as well...

---

### Post by Uta on 2006-06-03
Hi "s31523", your instructions were excellent and well worth passing on and now your launch tip, glad you are a forum regular! Thank You.

In reference to your launch tip: 1)first where in the line do you include the password so the launcher has everything it needs, 2) when connecting to my G5 it does connect but first gets a time out and asks for my password again (timeout connecting to 192.168.0.101:445) I do the password again and it connects and 3) my smbumount's path is /usr/bin/smbumount so to unmount a mounted share at /mnt/samba what is the command? I keep getting errors, when I do '"/usr/bin/smbumount  /mnt/samba/" produces  "Device or resource busy"

---

### Post by s31523 on 2006-06-03
OK, first, I am not sure if my setup is the best way to set this up, maybe someone out there with more experience can provide a better way, or maybe those wonderful Ubuntu guys/gals can get Nautilus fixed :mrgreen: 

Since my original suggestion was just a quick way to mount the SMB share to prove Samba is working, I wanted a "better" way which provides me read write access and allows me to mount as a user.  This required several steps.

1.) Create local mount point in my home directory (use whatever name you like):
```

cd
mkdir mysambamount

```
2.) Create credentials file so that I don't have to enter username/password.
```

cd
echo username=user > .smbpasswd
echo password=userpassword >> .smbpasswd

```
3.) Put some security on my cedentials file (This is NOT windows, remember? ;) )
```

chmod 600 .smbpasswd

```
4.) Edit /etc/fstab and add the following line (customize to your settings)
```

//server/share   path_to_folder_from_step_1    smbfs   credentials=/home/hans/.smbpasswd,rw,user,noauto    0       0

```
5.) Set permissions on smbmnt and smbumount so that users can call
```

chmod u+s /usr/bin/smbmnt
chmod u+s /usr/bin/smbumount

```

6.) Mount
```

mount //server/share

```

7.) Un Mount
```

smbumount mount_folder_from_step_1

```
8.) Put mount and unmount Launcher Scripts on desktop.
NOTE: mounting will cause a desktop icon to appear, trying to unmount by right-clicking on icon will fail, hence a launcher script is needed...

---

### Post by Uta on 2006-06-03
Again thanks for the steps. I got stuck on step #4 it said my samba share (which is on another laptop on the network) "No such file or directory" which after doing "smbtree" it does indeed exist right where I said it did. 
Why is it tripping on this?

---

### Post by s31523 on 2006-06-03
> got stuck on step #4 
How did you get stuck on step 4?  This was editing the fstab file.  Post output of your terminal session for the commands you entered.  Not all the specifics I mentioned are literal, they require some interpretation and changes to your specific setup.

---

### Post by Uta on 2006-06-04
myname@ubuntu:~$ //IBOOKG4/MACLINUX   /home/myname/mysambamnt    smbfs   credentials=/home/myname/.smbpasswd,rw,user,noauto    0       0
bash: //IBOOKG4/MACLINUX: No such file or directory

I am assuming that "//IBOOKG4/MACLINUX" is the laptop name and share on my network I am trying to reach? When I do "smbtree" it lists the laptop as "\\IBOOKG4\MACLINUX " 

and yes I know I have to put in my individual settings (ie) myname really would be inputted as my real name. Thanks!

---

### Post by s31523 on 2006-06-04
> //IBOOKG4/MACLINUX /home/myname/mysambamnt smbfs credentials=/home/myname/.smbpasswd,rw,user,noauto 0 0

This needs to go into the fstab file, which is in /etc. From the looks of your post it seemed as if you were typing that in the terminal console.

The folder ~/mysambamnt can be anything you want.  It just needs to be in your home directory so that the permissions on the folder are set so that you can do the mount call.  Once you add the above line into /etc/fstab then just go to a terminal session and type:
```
mount //IBOOKG4/MACLINUX
```

If that works you can create a launcher script on your desktop with that command.

---

### Post by Uta on 2006-06-04
you're right I was typing in the terminal (oops), I misunderstood your instructions. Again thanks for your continuing help!

---

### Post by Uta on 2006-06-04
Ok Here I am again after some hardware repairs, the keyboard on my laptop stopped having a functional "-" and "+" so had to reseat the keyboard. 
So what I currently have is an umount launcher that works but not a launcher to mount. It's a permission step I must have misconfigured? In the terminal when I use "mount //ibookg4/MACLINUX" it still asks me for my password, and after entering it, it mounts the share on my desktop. Perhaps I have misconstrued step #2?
I looked in the .smbpasswd file and it has myname=user
mypassword=userpassword? Do I have it backwards? 
 pls note (myname is my real name and mypassword is my password) Thanks!
[EDITED]
Later that evening zzzzz, Yep, I had it backwards, everything is launching proper now, just in time for them to fix samba mounting via Nautilus! Thank you so much for your help!

---

### Post by nekr0z on 2006-06-05
Hello there! Maybe you guys (and girls) could help me, too... Anyway, I don't know whom else to ask.

The situation: I have a workstation running Breezy Badger, with a huge file storage on it. I used to use samba to access those files from my laptop running WinXP, as well as for other guys on the network to access some files, too.

I have had a little trouble with all this, but finally the things worked just as good as possible. Now I have switched to Dapper on my laptop, and I want those files accessed once again.

As I connect to a shared folder using Konqueror, everything works just fine: I enter username and password, and see all files, no problem. The problems appear as I try to mount a shared folder to my laptop's filesystem (this is the thing I actually need).

Again, mount -t smbfs works just good, but the files with Cyrillic (Russian) characters in filenames can't be seen. I can see and access them in Konqueror using smb://server/share, but not on mounted filesystem.

Looks like a problem in smbfs package, or am I doing something wrong?

---

### Post by s31523 on 2006-06-06
Try this:
[http://www.linuxquestions.org/questions/showthread.php?t=152048](http://www.linuxquestions.org/questions/showthread.php?t=152048)

Be sure to report back!

---

### Post by nekr0z on 2006-06-06
Not an option, sorry.

First of all, they use an obsolete KOI8-R locale on both Slackware and Gentoo, while Ubuntu uses the more up-to-date UTF-8 one.

Second: all those HOWTOs are about adding Cyrillics fonts and keyboard layouts, which work close to perfectly out-of-the-box in Ubuntu.

Anyway, my problem is not in how console displays Russian filenames (it anyway displays and uses them perfectly in local filesystem). The problem, as I understand it, is in smbfs not transferring them properly.

---

