---
title: "How to network share on Lubuntu"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by SteveDee on 2010-11-16
Having spent several evenings trying to work this out, I thought I'd share this information with you.

First let me say that Lubuntu is a lightweight version of Ubuntu, so there is not much point in loading it up with unnecessary packages. If you just want to share printers on a Linux network, you don't need Samba. And if you just want a way that users can "push" files to others on a network, use Giver (+ Avahi) as this is a better option. Especially as it sorts out file permissions for you.

To enable file sharing on a Lubuntu 10.10 machine, go to Preferences > Synaptic Package Manager and add the following:-
    * samba
    * system-config-samba
    * gvfs-bin
    * gvfs-backends
...accepting any dependancies, 11 packages in total.

I suggest you re-boot now.

As an initial test, go to file manager (pcmanfm) and enter:-
smb://localhost
You should see the local print$ folder listed.

To access folder shares remotely
    * open file manager (pcmanfm)
    * enter the IP address or computer name of the machine you wish to access
	e.g. smb://192.168.0.99 or smb://print-server

To share a folder:-
Go to: Preferences > Samba (enter password when requested)
In the Samba Configuration screen:-
    * File > Add Share
    * use Browse... to select folder to be shared
    * Tick "Visible" and (if required} "Writable"
    * In the "Access" select "Allow access to everyone"
Set the Linux permissions:-
    * locate the folder to share in file manager
    * right click on the folder and select Properties > Permissions
    * set the required permissions, e.g. Other: Read & Write (to allow anyone full access)

Happy networking!

For Lubuntu 11.xx: you also need to install: python-glade2

---

### Post by SteveDee on 2011-01-08
> **SteveDee said:**
> 
...To access folder shares remotely...


If you have installed Samba on Lubuntu, don't forget that you can access your network with a user friendly bookmark like this:-
 - open the file manager (PCManFM)
 - access your network by typing "smb://" in the address bar (there should now be a folder displayed with the name of your workgroup)
 - Select from menu Bookmarks > Add to Bookmarks
 - In the "Add to Bookmarks" dialog, change "smb://" to something friendly like "Network"
 - Click OK, and your bookmark should appear in the list.

---

### Post by ashickur.noor on 2011-01-30
Thank's a lot.
But I am getting error when I try to write file from remote computer. It is telling permission denied. But I have give write permission.

---

### Post by cavalier911 on 2011-01-30
Linux system permissions take precedence over Samba permissions. 
Default umask 022 for regular users is only writeable by owner.
Verify shared folder is writeable by others. 
```
ls -la  /path/to/shared/folder/on/local/computer
```

---

### Post by SteveDee on 2011-01-30
> **cavalier911 said:**
> Linux system permissions take precedence over Samba permissions....

Thanks Cavalier911, you are absolutely right! I have now updated Post#1 to cater for this.

---

### Post by ashickur.noor on 2011-01-30
I have not understand,what you are saying. Please tell in details.

---

### Post by cavalier911 on 2011-01-30
Follow this for folder your sharing in samba:
> **SteveDee said:**
> 
Set the Linux permissions:-
    * locate the folder to share in file manager
    * right click on the folder and select Properties > Permissions
    * set the required permissions, e.g. Other: Read & Write (to allow anyone full access)

---

### Post by ashickur.noor on 2011-01-31
Its work. Thank you.

---

### Post by alenis on 2011-10-30
Thank you very much for the guide. Samba is under "System tools" in 11.10.

---

### Post by woodyg on 2011-12-14
> **SteveDee said:**
> 

To enable file sharing on a Lubuntu 10.10 machine, go to Preferences > Synaptic Package Manager and add the following:-
    * samba
    * system-config-samba
    * gvfs-bin
    * gvfs-backends
...accepting any dependancies, 11 packages in total.


I have installed these packages on 11.10, but when trying to open Samba, after being prompted for password, all I get is a window flashing by on the screen for a fraction of a second... but nothing else. 

**Samba does not start/work. **Ideas?[B] :confused:
[/B]

---

### Post by SteveDee on 2011-12-15
> **woodyg said:**
> I have installed these packages on 11.10, but...Samba does not start/work...

As you will see from this: [http://ubuntuforums.org/showthread.php?t=1746055&highlight=samba](http://ubuntuforums.org/showthread.php?t=1746055&highlight=samba)

...you need to install: python-glade2.

I've now edited post#1 to relfect this change.

---

### Post by Unterseeboot_234 on 2011-12-15
Okay, Oneiric Ubuntu on AMD64. I have followed along installing:
* samba
* system-config-samba
* gvfs-bin
* gvfs-backends

trying to get samba to run so I can assign workgroup and shares. I have installed the above, the glade-2, etc. All I get is the password screen and then the flash of Samba-config trying to display but never runs.

If I terminal-launch
```
gksudo gedit /etc/samba/smb.conf
```

I get these errors
```
(gedit:2363): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2363): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.RAQR6V': No such file or directory

(gedit:2363): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2363): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.072G6V': No such file or directory

(gedit:2363): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```

any ideas? I do see that samba has changed. Some of the older diagnostic threads have commands that this samba does not recognize, eg, sudo service smbd restart

---

### Post by SteveDee on 2011-12-16
> **Unterseeboot_234 said:**
> ...trying to get samba to run so I can assign workgroup and shares. ... All I get is the password screen and then the flash of Samba-config trying to display but never runs...

Try opening a terminal and typing:-
```

gksu system-config-samba

```
...this may show you why the Samba config screen is not running correctly.

I thought that in Ubuntu you could right-click a file in Nautilus and share a file...does that approach work?

Are you running 64bit Ubuntu on AMD64?

---

### Post by Unterseeboot_234 on 2011-12-16
The ONLY response I get with samba is terminal-based launch. Samba installation puts a menu item in Ubuntu, but that always fails.

So, yes, Oneiric AMD64-Ubuntu, install from apt-get install, using the extra stuff mentioned in this thread. On two AMD64 boxes, I might add. It would seem I can't access samba_user_data in the samba.config (that's a guess).

```
~$ gksu system-config-samba
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 116, in __init__
    self.samba_user_data = sambaUserData.SambaUserData(self)
  File "/usr/share/system-config-samba/sambaUserData.py", line 46, in __init__
    self.readSmbPasswords()
  File "/usr/share/system-config-samba/sambaUserData.py", line 63, in readSmbPasswords
    raise RuntimeError, (_("You do not have permission to execute %s." % pdbeditcmd))
RuntimeError: You do not have permission to execute /usr/bin/pdbedit.



```

I get that error once, and all other attempts of terminal lauch gives me the silent fail. 

ANY advice. I never see a workgroup or a network to begin configuring, but I am using a wireless LAN that works for internet access.

---

### Post by SteveDee on 2011-12-16
> **Unterseeboot_234 said:**
> ...ANY advice....

I think your problem is beyond the scope of this Lubuntu thread, and as you are running Ubuntu I suggest you start a new thread.

---

### Post by Unterseeboot_234 on 2011-12-16
Many thanks. I will start another thread. Incidentally, other threads advise the same workaround of installing all the python and glade tools to try and get Samba to run. Thanks for your input...

---

### Post by giantslor on 2012-03-04
Thanks for the tutorial, SteveDee. I had one problem that you didn't address: my hostname was too long, which prevented me from accessing my Windows shares through WORKGROUP or my Lubuntu shares through my Windows machines. This seems like it must be a common problem, so here is the solution from another thread:

> **Morbius1 said:**
> Preliminary steps:
[1] Run the following command in lubuntu and count the number of characters:
```
hostname
```If it's 16 characters or more in length then your machine is invisible to the rest of the network.

[2] Change the order of how host names are resolved to ip addresses:

To do both:
Edit smb.conf as root ( I'm using gedit here because I don't know the default editor in Lubuntu ) [COLOR=Red]*[ed. note: I've changed gedit to leafpad]*[/COLOR]:
```
gksu leafpad /etc/samba/smb.conf
```Then add the following line  to the [global] section of smb.conf - right under the workgroup line to  fix the hostname problem if there is one:
```
netbios name = something
```[COLOR=Blue]*something must be 15 characters or less in length*[/COLOR]

Still in leafpad add another line under that one:
```
name resolve order = bcast host lmhosts wins
``` Save smb.conf and then restart samba services:
```
sudo service smbd restart
sudo service nmbd restart
```Note: Every time you restart samba  services the network has a fit so wait a few minutes and see how far  this advice got you.

---

### Post by SteveDee on 2012-03-04
> **giantslor said:**
> ...one problem that you didn't address: my hostname was too long...

Yeah, there are lots of variables with networking, so plenty of scope for things to go wrong.

Thanks for the input.

---

### Post by kimdino on 2012-10-09
I am getting exactly the same response as UnderSeeBoot in post #14 from Lubuntu 11.10. However, as I am running it on a tiny un-upgradeable drive (4Gb on EEE PC) I have no room to install all the python and glade tools. Has anyone found a proper fix rather than the given workaround?

---

### Post by Wolfpup on 2012-10-20
I have followed the directions here and have Samba up and running. I can now see the files on my Ubuntu 10.04 server but i can not access them to copy them or play them as the are mainly video files. the laptop im trying to do this from is running Lubuntu 12.04. my server has Samba properly setup and configured as i can access and play the files on the server from other devices( computers and media players) with no problems. i have the folders/files set for everyone to have full rights(read/write/delete). I even have another Ubuntu based laptop that can fully access and play said files with no problems. 

Any suggestions would be help full as im testing this as an OS upgrade for ALL my Ubuntu based system because they are all running a no longer supported version and i would prefer to not upgrade to the version of Ubuntu that have the 'Unity' environments.

---

### Post by SteveDee on 2012-10-21
> **Wolfpup said:**
> I have followed the directions here ....

I have a simple home peer-to-peer network with (currently) around 6 Lubuntu based computers connected (the number varies from week to week).

I just did a test where I accessed an MP4 video located on a Lubuntu 11.04 laptop from a Lubuntu 12.04 laptop, and it plays OK.

All of my Lubuntu computers (except the one running 12.10 that I'm just setting up at the moment) have been configured using the method used in Post#1 of this thread. So I would probably urge you to repeat the process on your Lubuntu 12.04 laptop.

As for fault finding, I suggest that you check you have the permissions you think you have by trying to access and open a range of files. Also check that the media files will play locally on your laptop (i.e. when transferred across to a directory on your laptop).

One other general point I'd like to make (not specifically to you Wolfpup) concerns the term "server". On a peer-to-peer network, where all networked computers have a few shared directories with read access, all computers are both clients & servers. In other words, any computer can access some files from any other computer.

You may chose to install the server version of 'buntu on a specific machine, and load it up with music and videos. But if the network is peer-to-peer, your server probably does not have any other unique duties. Its just a big computer that you leave on all the time. It does not validate users on the "network", it is not a Domain Controller.

So make sure you follow the full procedure in Post#1 because I don't know what problems you may encounter if you don't follow all steps on all your machines.

The process in Post#1 is also covered here: [http://captainbodgit.blogspot.co.uk/2012/10/networking-with-lubuntu-win7-and.html](http://captainbodgit.blogspot.co.uk/2012/10/networking-with-lubuntu-win7-and.html) which also includes some notes for Windows 7 and the Raspberry Pi.

Good luck. What you are trying to do will work, there's just the small detail of finding out why its not!

---

### Post by SteveDee on 2012-10-21
I hope this does not cloud the issue, but I'm going to share this with you anyway.

I have not yet run the Post#1 procedure on my new 12.10 install, but I can "see" the network from this new machine.

When I try to run an MP4 video file which is located on another machine, the default media player (GNOME MPlayer) cannot play it, although it can play it locally (when the file is copied to the 12.10 machine).

However, when I install VLC media player on 12.10, it CAN play this video when located on a remote machine!

---

### Post by aamer on 2013-02-10
Thank you so much sharing this, it works great with me

---

### Post by salem132 on 2013-03-17
I have a problem viewing files from a Win7 machine (i can see the lubuntu machine and drives, but cant view contents), and printing from Win7 machine isnt working either (the printer is connected to Lubuntu 12.10 machine and visible on Win7, but it looks like no printing jobs are sent to the printer over network)

I followed the steps in post #1, but wasnt able to: 
> **SteveDee said:**
> 
Set the Linux permissions:-
    * locate the folder to share in file manager
    * right click on the folder and select Properties > Permissions
    * set the required permissions, e.g. Other: Read & Write (to allow anyone full access)


 In PCManFM I go to Go > My Computer, right-click the drive, choose Properties > Permissions and change "View content", "Change content" and "Execute" to Anyone, but I get ": Operation not supported by backend" error message. 

What am I doing wrong, and how can I get access to files on lubuntu from my Win7 machine?

Thanx

EDIT:
Made it work by adding a user in samba - for some reason it didnt work when Anyone was allowed read/write. Found the tip here [http://www.liberiangeek.net/2012/10/share-files-between-windows-7-and-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/10/share-files-between-windows-7-and-ubuntu-12-10-quantal-quetzal/)

---

### Post by isaacfowler on 2013-05-05
> **giantslor said:**
>  ...I had one problem that you didn't address: my hostname was too long, which prevented me from accessing my Windows shares through WORKGROUP or my Lubuntu shares through my Windows machines....

You sir, are amazing. I've spent 5-6 hours trying to troubleshoot this problem and this fixed me right up! Thanks!

---

### Post by raedmohammadi on 2013-07-07
when i want to open any folder , i can't there is an error message "The specified location is not mounted"
any idea ?


[IMG]http://i.imagebanana.com/img/ej85pila/Screenshotfrom20130708010335.png[/IMG]

---

### Post by SteveDee on 2013-07-08
> **raedmohammadi said:**
> when i want to open any folder , i can't there is an error message "The specified location is not mounted...


If you are running 13.04, its a bug in PCManFM: [http://ubuntuforums.org/showthread.php?t=2139901&page=2](http://ubuntuforums.org/showthread.php?t=2139901&page=2)

---

