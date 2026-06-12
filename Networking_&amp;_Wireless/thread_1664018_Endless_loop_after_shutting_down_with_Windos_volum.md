---
title: "Endless loop after shutting down with Windos volume still mounted"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by dryder on 2011-01-10
Hi
Ubuntu 10.04 64-bit
Samba shared with Windows folders

I shut down Ubuntu without unmounting a Windows volume. Now on my desktop there is a file:
"database (f) on study-raid.volume"
with the location: x-nautilus-desktop:///

I can not not delete it. Using gksudo nautilus, I can not see the file on the desktop yet it is there.

I can mount any volume from any computer on the network - except for "DATABASE (F)", location smb://study-raid/ - which is what this file refers to.

If I try to mount that drive, the desktop clears of anything I have put there and Ubuntu goes into an endless loop with folders 'Starting File Manager' opening all along the bottom panel - so rapidly that 'Starting File Manager' is the best guess I can make of the name of all the identical folders opening. I can not stop it and have to switch off the computer.

Any help would be appreciated.

Many thanks
David

---

### Post by PatchesTheCaveman on 2011-01-11
Go to Applications > Accessories > Terminal and type each of the following commands, pressing Enter after each one:
```
sudo umount ~/.gvfs
rm -rf ~/.gvfs
```

Hopefully your icon will disappear.  You should also now be able to access the Windows share again.  If not, you might need to reboot to regain access.

---

### Post by dryder on 2011-01-11
Thanks for replying PatchesTheCaveman.

Unfortunately it made no difference.

I am enclosing a jpg of the file on the desktop (with my mouse pointer) and the highlighted windows volume I am trying to re-enable mounting.

I don't understand why 'database (f) on study-raid.volume' exists on my david/Desktop but can not be seen using gksudo nautilus. Nor is it anywhere else that I can find. If I open office, it is not even listed as a file in the Open menu (all file types selected).

Thanks for any help,
David

---

### Post by PatchesTheCaveman on 2011-01-11
Installing the *gnome-volume-manager* package from the Ubuntu Software Center, Synaptic, or by running this command on a terminal:
```
sudo apt-get install gnome-volume-manager
```

Then see if that program can get rid of that file.

---

### Post by dryder on 2011-01-12
Hi,

gnome-volume-manager is not in synaptic nor is it available via terminal. Sourceforge says it is obsolete now. gvfs/nautilus do that now but that isn't that what you suggested in your first reply? I can't find any nautilus gui that might make it easier for me.

I really appreciate your help - thanks. It is an important volume to be able to mount for me.

David

---

### Post by PatchesTheCaveman on 2011-01-12
Sorry about that.  I should have looked deeper.  Let's try something else.

Install gvfs-bin (this one really exists!):
```
sudo apt-get install gvfs-bin
```

Now try to unmount it:
```
gnome-mount -u "//study-raid/database (f)/"
```

---

### Post by dryder on 2011-01-12
Hi,

command not found ...

David
PS - didn't mean to be cryptic - somebody came to door ...

---

### Post by PatchesTheCaveman on 2011-01-12
Every so often I get in a thread where I can't get a command right to save my life.  :-s

The correct command is
```
gvfs-mount -u "//study-raid/database (f)/"
```

---

### Post by dryder on 2011-01-12
Tried> gvfs-mount -u "//study-raid/database (f)/" and received > Error finding enclosing mount: Containing mount does not exist

David

---

### Post by PatchesTheCaveman on 2011-01-12
It can't be easy, can it?  I'm going to look into this further.

In the meantime, since I believe you said you can't access this share at all, here's a workaround that will get you into it until we can get rid of that rogue desktop file:
```
sudo mkdir /mnt/dbf
sudo smbmount -o user=*<username>* "//study-raid/database (f)/" /mnt/dbf
```
If the file share does not require you to login in you can replace *user=username* with *guest*.

You can then run:
```
nautilus /mnt/dbf
```
to see it in the file manager and you can access it in that location in all programs.

---

### Post by dryder on 2011-01-12
Umm ...
```
smbmount
```

should that be just ```
mount
```?

sudo smbmount -o guest "//study-raid/database (f)/" /mnt/dbf
gave
> Warning: mapping 'guest' to 'guest,sec=none'

Mounting the DFS root for domain not implemented yet
No ip address specified and hostname not found


It's a weird one isn't it?



David

---

### Post by PatchesTheCaveman on 2011-01-12
You can also use
```
mount -t smb
```

*smbmount* is a shortcut.

*[Never mind...]*

---

### Post by PatchesTheCaveman on 2011-01-12
That's weird.  If nautilus can find it by name smbmount should be able to.  Figure out study-raid's IP address, probably most easily by:
```
ping -c4 study-raid
```
and substitute that for its name in the smbmount command.

---

### Post by dryder on 2011-01-12
Weirder - it can't find the name - but can the ip address ...

I'm checking the router connection and windows name - it used to be study1-raid but I changed the name (dropping '1') some time ago.

Get back to you ...

David

---

### Post by PatchesTheCaveman on 2011-01-12
If you know the IP address, you can mount it with it.  e.g.
```
sudo smbmount -o guest "//192.168.0.10/database (f)/" /mnt/dbf
```

ETA:  On some networks you can't ping a Windows machine from a Linux one by name.  That's not necessarily a problem.

---

### Post by dryder on 2011-01-12
Hi,

XP computer:
Checked the router - STUDY-RAID (caps) is attached to 192.168.0.2. The router's LanIP setup (fixed address table ayk) has the same ip address, computer name and the MAC number is the same in both attached devices and LanIP setup.

The computer (Start>My Computer>Properties) has the same name, workgroup is correct.

```
sudo smbmount -o guest "//192.168.0.2/database (f)/" /mnt/dbf
```
gives me:
> david@ubuntu64:~$ sudo smbmount -o guest "//192.168.0.2/database/" /mnt/dbf
Warning: mapping 'guest' to 'guest,sec=none'

Mounting the DFS root for domain not implemented yet
No ip address specified and hostname not found
david@ubuntu64:~$ 


Samba used to be so easy ....

David

---

### Post by PatchesTheCaveman on 2011-01-12
Try:
```
sudo smbmount -o guest,netbiosname=study-raid,ip=192.168.0.2,servern=ubuntu "//study-raid/database (f)/" /mnt/dbf
```

Short of some sort of map outlining the exact electrical path to the other system that's about as specific as you can get!

---

### Post by dryder on 2011-01-13
Hi,
Apologies for the delay in replying.

No joy:> david@ubuntu64:~$ sudo smbmount -o guest,netbiosname=study-raid,ip=192.168.0.2,servern=ubuntu "//study-raid/database (f)/" /mnt/dbf
Warning: mapping 'guest' to 'guest,sec=none'

Mounting the DFS root for domain not implemented yet
mount error: can not change directory into mount target guest,sec=none,netbiosname=study-raid,ip=192.168.0.2,servern=ubuntu
david@ubuntu64:~$ 

I tried it with a different windows drive and got the same result.

As a matter of interest, when trying to delete the rogue file, this is the error message:> Error while deleting.
There was an error getting information about "database (f) on study-raid.volume".
The specified location is not supported

Is "The specified location is not supported" referring to the rogue file or "database (f)"?

I will be away until Saturday so will resume the solving of this then. I very much appreciate you helping with a problem I frankly just don't understand.

David

---

### Post by dryder on 2011-01-15
Hi,

I tried with a different folder but received the same message:> david@ubuntu64:~$ sudo smbmount -o guest "//192.168.0.2/Gnucash books/" /mnt/dbf
[sudo] password for david: 
Warning: mapping 'guest' to 'guest,sec=none'

Mounting the DFS root for domain not implemented yet
No ip address specified and hostname not found
david@ubuntu64:~$ 
 then for a different shared volume - it, too, gave the same error.

Any help would be appreciated.

David

---

### Post by PatchesTheCaveman on 2011-01-15
Make sure the capitalization matches exactly that of the file share and try again.  Apparently capitalization matters sometimes and causes the unhelpful DFS error.

---

### Post by dryder on 2011-01-15
Hi,
Thanks for your perseverance.

All the case matching is correct - I copied and pasted the command and names - they match Windows share names exactly.

Is there a way of renewing a possibly corrupted DFS database or would I Perhaps be better trying a samba re-install? Could my smb.conf file be at fault? (attached .txt extension added just for upload)


David

---

### Post by PatchesTheCaveman on 2011-01-15
First I would try to create a new user account on the Linux machine and see if you can access the share the usual graphical way that way.

---

### Post by dryder on 2011-01-16
Hi,

Yes - under a new User Account everything is fine - I can mount "DATABASE (F)". (I have not tried mounting in /mnt as nothing would).

David

---

### Post by dryder on 2011-01-18
In case it helps, I tried dragging the rogue volume on the Desktop to terminal.

terminal reported:> x-nautilus-desktop:///database%20(f)%20on%20study-raid.volume 

Does help in trying to track it down or remove it?

David

---

### Post by dryder on 2011-02-05
There was a link to the network folder in Home - how I do not know. Removing it solved the problem  .... thanks for all your help ... and I understand more too.

---

