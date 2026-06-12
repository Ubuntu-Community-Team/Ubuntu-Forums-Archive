---
title: "NTFS External USB shared for Windows users"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by SabreWolfy on 2009-10-14
I've spent a good few days searching here and elsewhere for assistance, but I seem to be going in circles.

I have an external USB NTFS drive connected to my Ubuntu desktop machine. I want to share this as a backup drive with a few Windows users. Each user will have a folder on the drive that only they can access. I've installed samba and created a test user, etc. Sharing the folder is not the problem.

How do I ensure that only Bob (accessing the share on the LAN from a Windows machine) can access folder "Bob"?

I think I did get this "working" if I created a test share on the ext3 Ubuntu drive. The NTFS drive does not store permissions -- is this the problem? I tried to create a softlink on the ext3 drive (with permissions) to the NTSF one but this did not work.

Any suggestions welcome. Thanks.

---

### Post by swerdna on 2009-10-14
Make folders on the NTFS drive called maybe gabrielle, elspeth, sandra etc

Mount the drive readable to the world drwxrwxrwx in the Linux server

Make a share in the Samba configuration file for each user using this template:
```
[elspeth]
path = /path_to/mount_directory/elspeth
valid users = elspeth
read only = no
```
Then only elspeth can enter that share

and so on for gabrielle, sandra etc.

FFI: [HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubuntfs.html")
FFI: [Defining and Using File Shares (Services)]("http://ubuntu.swerdna.org/ubusambaserver.html#shares")

---

### Post by SabreWolfy on 2009-10-14
Thanks. I've created the shared user as an Ubuntu user and made a password and I've created them with smbpassword and made the same password.

I edited smb.conf as per your post and restarted samba. On a Vista machine, the user is presented with a dialog when accessing the share (\\IP.ADDRESS.OF.SERVER\username) which is the same as the folder name. Entering the username and password does not work and neither does entering the workgroup\username and password.

Do I need to explicitly share the user's folder, or is specifying it in smb.conf enough?

PS: The USB is mounted with drwx for me only. a sudo chmod 777 FOLDER -R does not seem to change this. I'm trying to figure this out now too.

Whee! Thanks for the links at the end of your message! :) NTFS mounted with proper permissions now, but still no success with user access.

Update: Ok, the user can access the share. The username is \\SERVER.IP\username. They can see files in their folder but they have no write/delete access. Little steps.

---

### Post by swerdna on 2009-10-14
> **SabreWolfy said:**
> Thanks. I've created the shared user as an Ubuntu user and made a password and I've created them with smbpassword and made the same password.

I edited smb.conf as per your post and restarted samba. On a Vista machine, the user is presented with a dialog when accessing the share (\\IP.ADDRESS.OF.SERVER\username) which is the same as the folder name. Entering the username and password does not work and neither does entering the workgroup\username and password.

Do I need to explicitly share the user's folder, or is specifying it in smb.conf enough?

PS: The USB is mounted with drwx for me only. a sudo chmod 777 FOLDER -R does not seem to change this. I'm trying to figure this out now too.

Whee! Thanks for the links at the end of your message! :) NTFS mounted with proper permissions now, but still no success with user access.

Chmod (and chown) does not work on ntfs -- that's why to mount it drwxrwxrwx as per the link.

Each name (gabrielle, elspeth, sandra etc) is made a standard Ubuntu user. Each name is added to the Samba user database with a different password, using the command ```
sudo smbpasswd -a gabrielle
```etc for each name.

Do not share the folders named gabrielle, elspeth, sandra etc with Nautilus. Don't share either the NTFS folders (or the home folders) that way. If you have done that, then undo it. Share the folders only by setting up stanzas in smb.conf, one for each name.

You don't use this: \\server IP\username. That will attempt to link to the home directories of the users. You want to link to the shared folders on the NTFS drive, which is different. It occurs to me that the scheme here will be interfered with by an entry in the smb.conf file that must be fixed. Look in smb.conf for this entry:
```
;[homes]
;comment = Home Directories
;browseable = no
```
If that stanza exists, make sure the semicolons start each line, to make the share inactive.

Temporarily disable the firewall with this command:```
sudo ufw disable
```Worry about the firewall later.
FFI: [Opening the UFW Firewall for Samba]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")

After you've done all that, reboot every involved machine, one at a time, sequentially. Go round the loop twice.

Then you browse to the Ubuntu machine and drill down to the shares. If you cant browse and drill, post here the contents of smb.conf and we'll attempt to setup good browsing for you.

FFI: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home or Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by SabreWolfy on 2009-10-14
Thanks for the detailed reply. Those lines were already commented out in smb.conf.

I can now browse to the share and enter "servername\username" and the password and I can enter the share and see files.

However, I don't have write/delete access. I only have read access. The drive was mounted as described in your tutorial to give full permissions. The entry in smb.conf has "read only = no".

Edit: I created a second user and this one works fine -- write and delete access! I created this user by copying the first user, who can't write or delete for some reason.

---

### Post by SabreWolfy on 2009-10-14
Out of sheer frustration, I created a new "user" (call it username2) for the first one and this now works -- the user can login and write/delete. This new user has the same username as before (call it username1), just with one character less.

When I was testing out sharing previously, I used the original username (username1) so I think that that share is still active and "hidden" somewhere -- why else would "username1" not work, but "username2" does work. Also, I've added a second user which is also working fine.

Is there a limit to the length of the usernames/shares? username1 was 9 characters long, username2 is only 8 and the second user is only 5. I am using the same "name" for their Ubuntu account, their samba account and the folder name.

---

### Post by swerdna on 2009-10-14
It can be hidden in the directory /var/lib/samba/usershares. List the hidden usershares with ```
sudo ls -l /var/lib/samba/usershares
```and delete them with ```
sudo rm -Rf /var/lib/samba/usershares/*
```NB make no typos with that command

Length of names: somewhere I read 15, not sure, but 8 is fine.

---

### Post by AfrikaDietmar on 2010-06-14
Hi there,

i'm trying to realise something similar, short beginners basic question to what you posted at the top:

> Mount the drive readable to the world  drwxrwxrwx in the Linux serverWhen i attach the hard drive via USB, will it not show up automatically in Ubuntu 10.04 ?
Should i then make it readable 0777 with chmod in terminal ?

Security issue question, if someone plugs off the USB Hard drive from the Ubuntu PC and connects it to his windows machine, will that user be able to access all the files ? 

What i'm trying to make is, my USB Hard drive is composed of 2 disks, one in there should be for file sharing, the other one making constant parallel backups. The disc should only work if plugged in anywhere else with login/password. Probably files should be encrypted...

---

### Post by AfrikaDietmar on 2010-06-15
Hi Swerdna,

i spent some time last night reading your great ressources:

> FFI: [HowTo  Mount NTFS Partitions Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubuntfs.html")
FFI: [Defining and Using File Shares (Services)]("http://ubuntu.swerdna.org/ubusambaserver.html#shares")

Now I'm wondering, cause you mentioned there: > "Permissions and Ownership on NTFS Partitions The NTFS filesystem does not support Linux permissions or ownership  per se. You can't successfully change ownership with the Linux command chown and you can't successfully change permissions  with the Linux command chmod. Ownership and  permissions are set only in the mount command."

So, in other words, if i want to make a safe USB Backup drive, i should make it use Ubuntu Linux filesystem only ? Thus have a network completely based on linux, and don't use windows at all ?

The thing is, if someone would simply take the USB file sharing and backup drive, the access to files should be protected and not simply easily accessible by just connecting it back to another computer... Or can this not be achieved with a USB drive ?

---

