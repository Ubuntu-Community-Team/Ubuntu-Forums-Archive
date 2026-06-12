---
title: "&quot;net use z: \\pcname\c$&quot; equivalent?"
date: 2006-01-17
forum: Networking &amp; Wireless
---

### Post by kwanbis on 2006-01-17
Hi, where i work we log in to our windows machines, not to a domain, even if i think there is one. We are all part of an ARG workgroup. So, with windows, i just do a:

net use z: \\pcname\c$

and it maps \\pcname\c$ to my z drive.

how can i do the same in ubuntu? i tried:
javier@tux0ne:~$ smb://qp/c$
bash: smb://qp/c$: No such file or directory

and i can do it in windows.

---

### Post by Scotland on 2006-01-17
[QUOTE=kwanbis]Hi, where i work we log in to our windows machines, not to a domain, even if i think there is one. We are all part of an ARG workgroup. So, with windows, i just do a:

net use z: \\pcname\c$

and it maps \\pcname\c$ to my z drive.

how can i do the same in ubuntu? i tried:
javier@tux0ne:~$ smb://qp/c$
bash: smb://qp/c$: No such file or directory

and i can do it in windows.[/QUOTE]


from Konqueror I use the ip rather than the netbios name :-

smb://192.168.0.60/data

Use smbclient from command prompt e.g.

smbclient -L  yourpc


Dougie

---

### Post by nhartley on 2006-01-17
You could try adding your windows administrator login info...

smb://adminName:password@machine/C$


Shares with a dollar sign appended are hidden. Microsoft defaults to creating one for each physical hard drive. You could manually share the drive you are trying to access.

---

### Post by kwanbis on 2006-01-17
smbclient works:

> javier@tux0ne:~$ smbclient -L qcp -U qcp
Password:
Domain=[QP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        IPC$            IPC       Remote IPC
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
Domain=[QP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------


so, how do i map C$? can i use smbclient?

---

### Post by kwanbis on 2006-01-17
ok, [COLOR="DarkOrange"][B]i could use the smbclient to connect and "download" files with it. Its kinda an FTP client for shares, so i did>

javier@tux0ne:~/Desktop/firefox$ smbclient //qp/c$ -U qp
Password:
Domain=[QP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \>

i from there i used cd to get to the folder i wanted, and get file_name to copy the file to my machine.
[/B][/COLOR]
But i'm still unable to map the share. Looks like smb is not installed, even if smbclient is. Thanks.

---

### Post by mpvano on 2006-01-17
You don't need smb - you need a package called "smbfs".

If smbclient is working, you're half way there (the hard part is over).

Use system:administration:Synaptics Package manager to find out if "smbfs" is currently installed. If it is not, install it. Then, read the man pages for smbmount, smbmnt, and smbumount.

You may need to create a mount point.

In Unix, there are no other drives, so you can't have a "z" drive. You "mount" or attach a remote file system to an empty directory you've created for that purpose somewhere on your filesystem tree.

I usually make a directory named the same as the fileserver inside the directory named /mnt, which is traditionally reserved for such purposes.

Using smbmount, or the smb variations of the normal "mount" command, you can then hook up the server so that the contents of the share "magically" replace those of the directory. You can control whether the magic works for reading only or reading and writing depending on the options you use with the mount command. It's pretty straightforward, but you'll need to learn a little bit about access rights to do it properly.

The smbmount command is a helper that you can configure to allow non administrative users to mount and unmount smb shares without having to use sudo.

There are a few potential snags including the proper case for sharenames, user names, passwords and workgroups, but it sounds like you've already got all of that working if smbclient works.

One warning - it's easy to get confused between actually mounting the share (which works for all programs on your ubuntu system) and just opening it up in nautilus (which works sort of like smbclient for nautilus to transfer files ONLY, but doesn't really mount the share for general use), and actually mounting it to make it visible to other programs.

You can do BOTH under ubuntu, and the results can appear very similar in nautilus, but there's a fundamental difference....

hope this points you in the right direction...

Mario

---

