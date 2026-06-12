---
title: "Cant connect to windows pc's in network"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by kd0 on 2013-01-27
I get this screen shot here when i try to access my network windows PC's

[IMG]http://i.imgur.com/5BXd67N.png[/IMG]

I was wondering how to fix this, im a noob with linux and dont even know how to pull up a terminal in 12.04 LTS which is what im running

---

### Post by ahallubuntu on 2013-01-27
Is sharing enabled on that PC "KD0-PC" for sure?  What version of Windows is it?

FYI, you can get into a terminal in Ubuntu Desktop (aka "Unity") by searching for "terminal" in "dash" which is the thing in the top left (top of the column) where you can search for software.

If you prefer a more conventional look instead of Unity, you can go into Ubuntu Software Center and install "Gnome Shell" (search for it), then logout, log in again but choose "Gnome Classic" or "Gnome" from the list of options.  "Gnome Classic" is the look of the old Ubuntu if you ever used it with menus etc. like Windows.  That's what I use myself in 12.04.

---

### Post by kd0 on 2013-01-27
> **ahallubuntu said:**
> Is sharing enabled on that PC "KD0-PC" for sure?  What version of Windows is it?

FYI, you can get into a terminal in Ubuntu Desktop (aka "Unity") by searching for "terminal" in "dash" which is the thing in the top left (top of the column) where you can search for software.

If you prefer a more conventional look instead of Unity, you can go into Ubuntu Software Center and install "Gnome Shell" (search for it), then logout, log in again but choose "Gnome Classic" or "Gnome" from the list of options.  "Gnome Classic" is the look of the old Ubuntu if you ever used it with menus etc. like Windows.  That's what I use myself in 12.04.

Yes sharing is enabled for sure, and password protected sharing is off as well, i can share with the windows pcs amongst themselves but not with the linux box

---

### Post by texpat on 2013-01-27
I had the exact same problem some time ago. I'd forgotten to actually share folders on the server machine (we were all noobs at some point ;-) ). Could this be your case, too?

** OK, forget it.. just read the above **

---

### Post by Morbius1 on 2013-01-27
When you can get to your terminal see if the samba client itself is functioning by running the following command:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of KD0-PC*[/COLOR]

If you can't access with an ip address turn off the firewall if you are using it on Ubuntu:
```
sudo ufw disable
```and try the first command again.

If you can't access it by ip address something fundamental is wrong. If you can access it then edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line after the "workgroup" line near the beginning of the file:
```
name resolve order = bcast host lmhosts wins
```Save smb.conf and back in the terminal restart samba:
```
sudo sevice smbd restart
``````
sudo service nmbd restart
```Now go make a nice pot of tea or stare at the monitor for about 5 minutes and then see if you can connect.

---

### Post by VE6EFR on 2013-01-27
I had the same error a few days ago. I had samba installed on the ubuntu machine and had sharing setup correctly on both machines. What solved my issue is a restart of the windows computer. Once it rejoined the network everything worked as it was supposed to.

---

### Post by kd0 on 2013-01-27
> **Morbius1 said:**
> When you can get to your terminal see if the samba client itself is functioning by running the following command:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Change 192.168.0.100 to the ip address of KD0-PC*[/COLOR]

If you can't access with an ip address turn off the firewall if you are using it on Ubuntu:
```
sudo ufw disable
```and try the first command again.

If you can't access it by ip address something fundamental is wrong. If you can access it then edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line after the "workgroup" line near the beginning of the file:
```
name resolve order = bcast host lmhosts wins
```Save smb.conf and back in the terminal restart samba:
```
sudo sevice smbd restart
``````
sudo service nmbd restart
```Now go make a nice pot of tea or stare at the monitor for about 5 minutes and then see if you can connect.

running nautilus makes it work? what the heck? how do i get it to work for samba shares or make a shortcut to it on the desktop to that command in the terminal?

---

### Post by kd0 on 2013-01-27
samba shares doesnt work at all now, it says theres a firewall enabled causing it to not see it, but i disabled the ufw just like you said, so no firewall is running, it seemed to disable  samba shares after running nautilus

---

### Post by Morbius1 on 2013-01-28
> running nautilus makes it work? what the heck? how do i get it to work  for samba shares or make a shortcut to it on the desktop to that command  in the terminal?     ** Remember, the Unity Desktop / Gnome3 doesn't want you to have shortcuts on the desktop because that would be a feature. But if you must have one:

Install the following package:
```
sudo apt-get install --no-install-recommends gnome-panel
```Then run the following command:
```
gnome-desktop-item-edit ~/Desktop/ --create-new
```** Or you can bookmark it in Nautilus:
Run the command again:
```
nautilus smb://192.168.0.100
```Then select Bookmarks > Add Bookmark

[COLOR=Blue]*Note: This will only work of course if you have static ip addresses on all your machines since every time one of them boots they could have a different ip address.*[/COLOR]
> samba shares doesnt work at all now, it says theres a firewall enabled  causing it to not see it, but i disabled the ufw just like you said, so  no firewall is running, it seemed to disable  samba shares after running  nautilus     I'm not familiar with a Linux error message that mentions a firewall so I'm not sure which one it's referring to - a Linux firewall or a Windows firewall:

What system is giving you the error?
And can you post the exact error message?

---

### Post by kd0 on 2013-01-28
im actually running kubuntu, so i dont know if that gnomee panel stuff will work it says linux firewall, ill give the exact error here in a bit

---

### Post by kd0 on 2013-01-28
[http://i.imgur.com/Cfwhf0W.png]("http://i.imgur.com/Cfwhf0W.png")


Thats the message i get now when i try to open samba shares, but it was working before i ran nautilus

---

### Post by Morbius1 on 2013-01-28
> **kd0 said:**
> im actually running kubuntu
>  Thats the message i get now when i try to open samba shares, but it was working before i ran nautilus     Your very first post shows Ubuntu's Unity desktop so I'm very confused. If you are using Nautilus on top of KDE I can't imagine what that would do since Nautilus tries to control part of the desktop - so I'm in uncharted waters.

The dolphin error message is a guess. Find out if Linux can see the remote shares. Post the output of the following command:
```
smbtree
```

---

### Post by kd0 on 2013-01-28
> **Morbius1 said:**
> Your very first post shows Ubuntu's Unity desktop so I'm very confused. If you are using Nautilus on top of KDE I can't imagine what that would do since Nautilus tries to control part of the desktop - so I'm in uncharted waters.

The dolphin error message is a guess. Find out if Linux can see the remote shares. Post the output of the following command:
```
smbtree
```

its empty, smbtree shows nothing, sorry about the confusion, i was running unbuntu 12.10 but was having the same problem, now im running kubuntu cause i like KDE better, but am having a problem now where i cant see samba shares at all

---

### Post by furything on 2013-01-28
I am using KDE and nautilus. 

I find trying to see network items via gui times out but I have added network places.

In nautilus menu find where it states location editable and type
```
smb://ipadress/share
```replace with your ip and name of share

Once it sees a share you can go up a level and into a different share
Cannot remember how I made the permanent network places but try doing this by hand first

I note you have made a number of changes so this may not work for you but from a clean install it does.

---

### Post by kd0 on 2013-01-28
> **furything said:**
> I am using KDE and nautilus. 

I find trying to see network items via gui times out but I have added network places.

In nautilus menu find where it states location editable and type
```
smb://ipadress/share
```replace with your ip and name of share

Once it sees a share you can go up a level and into a different share
Cannot remember how I made the permanent network places but try doing this by hand first

I note you have made a number of changes so this may not work for you but from a clean install it does.

I get this [IMG]http://i.imgur.com/6TwZsbh.png[/IMG]

---

### Post by Morbius1 on 2013-01-28
> its empty, smbtree shows nothing,
Restart nmbd and try it again. If the samba client can't see the samba server on the same machine no one will - at least not by name:
> sudo service nmbd restart

---

### Post by kd0 on 2013-01-28
> **Morbius1 said:**
> Restart nmbd and try it again. If the samba client can't see the samba server on the same machine no one will - at least not by name:

nmbd unrecognized service

---

### Post by Morbius1 on 2013-01-28
[1] "Failed to mount" is a credentials problem. Change your command to this:
```
smb://user-name@192.168.1.101
```Where "user-name" is one on the Windows machine. Hopefully you know it's password.

[2] Start nmbd:
```
sudo service nmbd start
```
Then try smbtree again

---

### Post by kd0 on 2013-01-28
> **Morbius1 said:**
> [1] "Failed to mount" is a credentials problem. Change your command to this:
```
smb://user-name@192.168.1.101
```Where "user-name" is one on the Windows machine. Hopefully you know it's password.

[2] Start nmbd:
```
sudo service nmbd start
```Then try smbtree again

sudo service nmbd start
nmbd: unrecognized service
kd0@kd0-VirtualBox:~$

i also get the same error, failed to mount windows share

---

### Post by Morbius1 on 2013-01-28
VirtualBox? 

Do you have NAT or Bridged networking enabled in your VBox setting?
Are you trying to connect to a Windows host from a Linux guest?

---

### Post by kd0 on 2013-01-28
> **Morbius1 said:**
> VirtualBox? 

Do you have NAT or Bridged networking enabled in your VBox setting?
Are you trying to connect to a Windows host from a Linux guest?

Yes im trying to connect to my host windows 7 machine from my linux guest on virtual box, im on the virtual box right now talking to you so i guess i have NAT?

---

### Post by kd0 on 2013-01-28
i just thought it would be cool to share between the two machines, oh well.. i guess its not going to work, i guess i could always setup a ftp server or something like that

---

### Post by kd0 on 2013-01-28
know any good graphical ftp clients for linux?

---

### Post by furything on 2013-01-28
Have you tried to do the shared folder option through VM controller?
You may be able to see that as a network share.
I must admit my kubuntu is a full install not a vm

---

### Post by Morbius1 on 2013-01-28
> Yes im trying to connect to my host windows 7 machine from my linux guest on virtual box,Then you don't need to go through the network to do that. You can use Shared Folders in your VBox Settings. See attachment. In this particular case the the shared folder is automatically mounted to /media/sf_DATA on the Linux guest.

---

### Post by kd0 on 2013-01-28
ill give that a try here

---

### Post by kd0 on 2013-01-28
okay i shared a folder, where would it be located now within linux?

---

### Post by furything on 2013-01-28
from memory the server is vboxsvr
so

smb://vboxsvr/share name

I normally have windows as the vm so it is opposite to what I do

---

### Post by Morbius1 on 2013-01-28
After you restart the linux guest it's at /media/sf_XXXXX.

It does that automatically.

[COLOR=Blue] **EDIT**: You will need to add yourself to the correct group to actually access the mount point:[/COLOR]
```
 sudo gpasswd -a your-user-name vboxsf
```

Then logout and login again for the group membership to take affect.

---

### Post by furything on 2013-01-28
That would depend on if you checked the auto mount option if so Morbius1 is correct.
If NOT auto mount you will have to do 
\\vboxsvr\share which in linux is smb://vboxsvr/share

---

### Post by kd0 on 2013-01-28
> **Morbius1 said:**
> After you restart the linux guest it's at /media/sf_XXXXX.

It does that automatically.

[COLOR=Blue] **EDIT**: You will need to add yourself to the correct group to actually access the mount point:[/COLOR]
```
 sudo gpasswd -a your-user-name vboxsf
```

Then logout and login again for the group membership to take affect.

theres nothing under /media/ its empty

im not sure what gpasswd -a your user name vboxsf is suppose to do? do i just make up a user name

---

### Post by kd0 on 2013-01-28
kd0@kd0-VirtualBox:~$ sudo gpasswd -a kd0 D_DRIVE
[sudo] password for kd0: 
gpasswd: group 'D_DRIVE' does not exist in /etc/group
kd0@kd0-VirtualBox:~$

---

### Post by Morbius1 on 2013-01-28
It's your login user name on the the Linux guest.

If you don't have anything mounted to /media then you didn't check the "Auto-mount" box when you created the shared folder. See the attachment again:

Then shut down the linux guest and start it up again.

---

### Post by Morbius1 on 2013-01-28
The command you are looking for is this one:
```
sudo gpasswd -a kd0 vboxsf
```

---

### Post by kd0 on 2013-01-28
yeah i checked auto mount and rebooted the machine

---

### Post by kd0 on 2013-01-28
kd0@kd0-VirtualBox:~$ sudo gpasswd -a kd0 vboxsf
[sudo] password for kd0: 
gpasswd: group 'vboxsf' does not exist in /etc/group
kd0@kd0-VirtualBox:~$

---

### Post by Morbius1 on 2013-01-28
If I had to hazard a guess I think your VBox guest doesn't have "Guest Additions" installed.

In the VBox guest go to Devices > Install guest additions

---

### Post by kd0 on 2013-01-28
well it appears to have inserted an optical disk, but im not sure what to do next

---

### Post by kd0 on 2013-01-28
kd0@kd0-VirtualBox:/media/VBOXADDITIONS_4.2.6_82870$ ./VBoxLinuxAdditions.run
Verifying archive integrity... All good.
Uncompressing VirtualBox 4.2.6 Guest Additions for Linux..........
This program must be run with administrator privileges.  Aborting
kd0@kd0-VirtualBox:/media/VBOXADDITIONS_4.2.6_82870$

---

### Post by kd0 on 2013-01-28
ok i managed to install the guest additions

but i still dont see my shared folder anywhere in mnt or in media

it says guest additions is not installed or working correctly when i double click on the shared folder, im running kubuntu 12.10 so maybe the guest additions isnt compatible with it? 

anyway, i got nautilus to work and book marked my host pc so my problem is pretty much solved now, 

thanks you guys for all your help, it is much appreciated

---

### Post by furything on 2013-01-29
Although this was fixed by vmbox share it could also be the samba config
After suggesting the sahre I checked my samba config and a forum search and came up with this
[http://ubuntuforums.org/showthread.php?t=1612556](http://ubuntuforums.org/showthread.php?t=1612556)

I found my myth box which works perfectly with  shares  has exactly the same configuration as suggested in the link.

For anyone following this thread with a vm try both ways kd0 if you check back then give this config a try.

---

