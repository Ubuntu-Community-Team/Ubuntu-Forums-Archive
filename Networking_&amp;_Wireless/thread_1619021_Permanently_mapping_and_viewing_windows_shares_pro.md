---
title: "Permanently mapping and viewing windows shares problems (outside of Nautilus)"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by MarkWod on 2010-11-11
Hi All,

I'st just installed 10.10 on Virtual Box. I'm trying to map some windows drives (On the host) permanently. Using Places->Connect To Server etc I can connect to my windows box no problem and see the directories etc in Nautilus (2.32.0) all ok.

But rebooting the system results in my having to log in again - I've looked at [https://help.ubuntu.com/community/MountWindowsSharesPermanently#Two%20methods,%20depending%20on%20share%20host](https://help.ubuntu.com/community/MountWindowsSharesPermanently#Two%20methods,%20depending%20on%20share%20host) is that the only what to get this to work permanently?

Also, and more importantly K-Develop (And possibly others) can't see this mapped drive when I want to open a file from it? What would be the problem here?

Many Thanks

Mark

---

### Post by SeijiSensei on 2010-11-11
> **MarkWod said:**
> But rebooting the system results in my having to log in again - I've looked at [https://help.ubuntu.com/community/MountWindowsSharesPermanently#Two%20methods,%20depending%20on%20share%20host](https://help.ubuntu.com/community/MountWindowsSharesPermanently#Two%20methods,%20depending%20on%20share%20host) is that the only what to get this to work permanently?

That how-to seemed awfully complicated for what is basically a not very complicated task.  You'll need to have the smbfs package installed. If the share you're mounting requires a username and password create a file with the credentials and assign its ownership to root:

```

echo 'username=[Windows username]' > /etc/creds
echo 'password=[Windows password]' >> /etc/creds
chown root.root /etc/creds
chmod 0600 /etc/creds

```

You'll need to do this with sudo.  Replace the items in brackets with the necessary Windows username and password.

Create a mount point for the Windows share; let's call it /media/windows.  Now just enter the command:

```
sudo smbmount //server_name/share_name /media/windows -o credentials=/etc/creds
```

Replace "server_name" with the Windows server name, or if that doesn't work, it's IP address, and "share_name" with the exported share you wish to mount.

Automating this process is a bit tricky in desktop Ubuntu because the network interfaces are not started at boot but by the user.  If you set up a static IP in Ubuntu, you can place the smbmount command in /etc/init.d/rc.local (without the initial sudo).  Otherwise you'll need to run it from a terminal after logging in and starting the network.

(It's also possible to create an entry in /etc/fstab to mount the share, but I forget the syntax for that.)

---

### Post by MarkWod on 2010-11-11
[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"),

Thanks for the reply - okay so i hold my hands up, dumb request - how do  get the root access? I've tried su - root  et al with my system password. It's not playing ball and logging out isn't either.

and does:

username=[Windows username]

become 

username-mark
or
username=[mark]

Many thanks

Mark

---

### Post by SeijiSensei on 2010-11-12
Ubuntu uses the "sudo" command.  You can open a root shell with "sudo su" and entering your password when prompted.  Alternatively you can just prepend each command above with "sudo".  You'll be prompted for the password after the first command, but you'll then have root privileges for a while (fifteen minutes, I think).  The smbmount command I gave you uses sudo.

No brackets needed in the credentials file; just "mark" and your Windows password.

---

### Post by MarkWod on 2010-11-15
Brilliant I'm almost there! I can see the folder etc from KDevelop, but seem unable to create directories/files?

Thanks

Mark

---

