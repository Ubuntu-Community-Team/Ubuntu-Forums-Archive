---
title: "Network Shares"
date: 2009-10-15
forum: Mythbuntu
---

### Post by CodeFreakC on 2009-10-15
Hi Guys and Gals,
I'm a complete n00b on all Linuxes and this is my first post, so here goes.
I have a Windows XP computer that is sharing a USB 1TB Hard drive over our network. I would like to be able to access and play the files from that HDD on MythVideo. Anyone know how any guides??
Thanks loads , CodeFreakC

---

### Post by belly917 on 2009-10-16
> **CodeFreakC said:**
> Hi Guys and Gals,
I'm a complete n00b on all Linuxes and this is my first post, so here goes.
I have a Windows XP computer that is sharing a USB 1TB Hard drive over our network. I would like to be able to access and play the files from that HDD on MythVideo. Anyone know how any guides??
Thanks loads , CodeFreakC

I recently tried figuring this out for myself and came accross [this page](http://ubuntuforums.org/showthread.php?t=288534)

Basically I made a sub directory (Desktop) in the folder where mythtv looks for videos and then mounted the windows share to that.  To test the mount I did this command:
```
 mount -t cifs -o username=<winuser>,password=<winpassword> \\\\192.168.1.28\\Movies /home/media/video/Desktop/
```

I was having issues with a few of the different options causing the mount to fail.  This is what finally worked. Your directories may vary.  Once you've confirmed that this works, you'll want to modify your /etc/fstab in order to make the mount permanent at each reboot

I didn't get that far yet, but it is covered in the link above.

One important note:  Is your backend and frontend combined?  If so you shouldn't have problems provided your network can keep up.

I have a seperate frontend and when I mounted the samba share to my backend, the backend could play the files just fine.  But the frontend was unable to obtain permission to the files.  The permissions on first inspection looked alright, but I think the problem is that I mounted a windows share on my backend, and then my frontend mounts my backend's data directory via NFS.. so in effect, all the windows video files are being passed through my backend unnecessarily.

Instead I think I might have both the frontend and the backend mount the windows share directly in a directory that isn't included in the NFS directory.

*edited for spelling and clarification of terms

---

### Post by CodeFreakC on 2009-10-16
But Samba is a file server that needs to run on linux, right? The file server is windows

---

### Post by belly917 on 2009-10-16
> **CodeFreakC said:**
> But Samba is a file server that needs to run on linux, right? The file server is windows

Sorry, I was a little sloppy with my terms.  The file server discussed here is windows using the smb/cifs protocol.  Samba is the linux implementation of server and client of the smb/cifs protocol.

---

### Post by doas777 on 2009-10-16
yep, you need to use an SMB/CIFS client, but it shoudl be preinstalled.
just go to places -> network and you shoudl be able to browse to the Xp box.
or just type into a nautilus address bar:
```
smb://<server>/<share>
```

---

### Post by joshoekstra on 2009-10-18
Just remember to not edit videodata when not all the shares are connected, otherwise you'll end up running it over and over again to get the data in the DB.
An option I used in the past is automount, it mounts the shares when needed, it however caused a bit of a slow response when accessing the cideos for the first time.

---

### Post by neutron68 on 2011-01-19
What is the best GUI SAMBA client program to install on the Mythbuntu 10.10 machine?  PyNeighborhood?

I'd like to do the same thing as the original post.

I've been trying to connect to SAMBA shares in my windows computers, but NO remote computers or networks show up in either panel of pyNeighborhood.
In fact, the left panel in pyNeighborhood does not show GROUPS or any computers like they do in the screenshots on the developer's page.  

[IMG]http://sourceforge.net/dbimage.php?id=164079[/IMG]

I am suspecting something is broken?

Any pyneighborhood experts on the forum?

Eric

---

### Post by neutron68 on 2011-01-19
I'm hoping this secret is the key.

```
Installation

Installation is simple, but there is one piece that the installation does not catch and pyNeighborhood will not fully function without. To install everything you need open up your Add/Remove Software utility and do the following:

   1. Search for pyNeighborhood and mark the results for installation.
   2. Search for mc (Midnight Commander) and mark the results for installation.
   3. Click Apply to install.

That&#8217;s it. If you do not install Midnight Commander the mount command will not work successfully.
```

UPDATE:  It didn't help.

Please HELP!!
Eric

---

### Post by neutron68 on 2011-01-20
I just contacted the developers of pyNeighborhood via their webpage:


They suggested using the newer version of pyNeighborhood.  Unfortunately, the older version is in the Ubuntu repositories. 

**How can we get the newer version into the Ubuntu repository??**

> 
version 0.5.0x is outdated. We've fixed several Bugs and Errors in this version. Maybe you will try our PPA ([https://launchpad.net/~pyneighborhood/+archive/stable](https://launchpad.net/~pyneighborhood/+archive/stable)) to install the latest version 0.5.3. This version contains lots of improvements and bugfixes. Besides, its easier to find errors (we've added a debug-area). Unfortunately, the ubuntu archives only contain the outdated version pyneighborhood 0.5.0.

Please try this version and report any bugs you may encounter. If you have problems with installing pyneighborhood, I sure can provide help.

Greetz,

Linus

---

### Post by neutron68 on 2011-01-20
I just contacted the developers of pyNeighborhood via their webpage:
[http://launchpad.net/pyneighborhood](http://launchpad.net/pyneighborhood)

They suggested using the newer version of pyNeighborhood.  Unfortunately, the older version is in the Ubuntu repositories. 

**How can we get the newer version into the Ubuntu repository??**

> 
version 0.5.0x is outdated. We've fixed several Bugs and Errors in this version. Maybe you will try our PPA ([https://launchpad.net/~pyneighborhood/+archive/stable](https://launchpad.net/~pyneighborhood/+archive/stable)) to install the latest version 0.5.3. This version contains lots of improvements and bugfixes. Besides, its easier to find errors (we've added a debug-area). Unfortunately, the ubuntu archives only contain the outdated version pyneighborhood 0.5.0.

Please try this version and report any bugs you may encounter. If you have problems with installing pyneighborhood, I sure can provide help.

Greetz,

Linus

---

### Post by neutron68 on 2011-01-20
I just contacted the developers of pyNeighborhood via their webpage:


They suggested using the newer version of pyNeighborhood.  Unfortunately, the older version is in the Ubuntu repositories. 

**How can we get the newer version into the Ubuntu repository??**

> 
version 0.5.0x is outdated. We've fixed several Bugs and Errors in this version. Maybe you will try our PPA ([https://launchpad.net/~pyneighborhood/+archive/stable](https://launchpad.net/~pyneighborhood/+archive/stable)) to install the latest version 0.5.3. This version contains lots of improvements and bugfixes. Besides, its easier to find errors (we've added a debug-area). Unfortunately, the ubuntu archives only contain the outdated version pyneighborhood 0.5.0.

Please try this version and report any bugs you may encounter. If you have problems with installing pyneighborhood, I sure can provide help.

Greetz,

Linus

---

### Post by neutron68 on 2011-01-20
I just contacted the developers of pyNeighborhood via their webpage:
[https://launchpad.net/pyneighborhood](https://launchpad.net/pyneighborhood)

They suggested using the newer version of pyNeighborhood.  Unfortunately, the older version is in the Ubuntu repositories. 

**How can we get the newer version into the Ubuntu repository??**

> 
version 0.5.0x is outdated. We've fixed several Bugs and Errors in this version. Maybe you will try our PPA ([https://launchpad.net/~pyneighborhood/+archive/stable](https://launchpad.net/~pyneighborhood/+archive/stable)) to install the latest version 0.5.3. This version contains lots of improvements and bugfixes. Besides, its easier to find errors (we've added a debug-area). Unfortunately, the ubuntu archives only contain the outdated version pyneighborhood 0.5.0.

Please try this version and report any bugs you may encounter. If you have problems with installing pyneighborhood, I sure can provide help.

Greetz,

Linus

---

### Post by neutron68 on 2011-01-20
I just contacted the developers of pyNeighborhood via their webpage:
[http://launchpad.net/pyneighborhood](http://launchpad.net/pyneighborhood)

They suggested using the newer version of pyNeighborhood.  Unfortunately, the older version is in the Ubuntu repositories. 

**How can we get the newer version into the Ubuntu repository??**

> 
version 0.5.0x is outdated. We've fixed several Bugs and Errors in this version. Maybe you will try our PPA ([https://launchpad.net/~pyneighborhood/+archive/stable](https://launchpad.net/~pyneighborhood/+archive/stable)) to install the latest version 0.5.3. This version contains lots of improvements and bugfixes. Besides, its easier to find errors (we've added a debug-area). Unfortunately, the ubuntu archives only contain the outdated version pyneighborhood 0.5.0.

Please try this version and report any bugs you may encounter. If you have problems with installing pyneighborhood, I sure can provide help.

Greetz,

Linus

---

### Post by neutron68 on 2011-01-20
I got the new version (0.5.3) into my system by trying the advice on the pyNeighborhood page:
[http://launchpad.net/~pyneighborhood/+archive/stable](http://launchpad.net/~pyneighborhood/+archive/stable)
I clicked on the link that says "Technical details about this PPA".

I added these lines to my "/etc/apt/sources.list" file:
deb [http://ppa.launchpad.net/pyneighborhood/stable/ubuntu](http://ppa.launchpad.net/pyneighborhood/stable/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/pyneighborhood/stable/ubuntu](http://ppa.launchpad.net/pyneighborhood/stable/ubuntu) maverick main

I launched the Synaptic Package manager and clicked UPDATE.

I searched for pyNeighborhood, right-clicked on it and selected the update choice.

I clicked APPLY.

I've now got 0.5.3 on my Mythbuntu 10.10 machine. I started it and right away it found all my shared computers without ANY configuration from me.

I can SEE the files in the SAMBA and Windows shares! WOO HOO!

**I still think it is a good idea to update the Ubuntu repository with version 0.5.3 - given that it works fine and version 0.5.0 does NOT work!**

Eric

---

