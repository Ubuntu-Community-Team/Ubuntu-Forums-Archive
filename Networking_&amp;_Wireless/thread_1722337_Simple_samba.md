---
title: "Simple samba"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by kadil on 2011-04-05
I am having difficulty doing something that I think should be simple, I want to share a folder with another user on the same computer, so we both have read and write access to the files and create and delete access to folders within. So I:
1. right click on a folder on my desktop
2.tick allow others to create and delete files in this folder 
3. allow nautilus to automatically add the correct permissions
4. log in as the other user & try to connect to the share with the other users credentials
5. not allowed to connect
6. I can connect with my credentials, but do not want to hand out my username and password to others.

What is the Ubuntu way of doing this properly?

---

### Post by kadil on 2011-04-05
My thoughts are that if I create a ntfs filesystem and mount it under /mnt than is will be read/writable by all users on this machine and not a network vulnerability.


thoughts?

---

### Post by bab1 on 2011-04-05
> **kadil said:**
> I am having difficulty doing something that I think should be simple, I want to share a folder with another user on the same computer, so we both have read and write access to the files and create and delete access to folders within. So I:
1. right click on a folder on my desktop
2.tick allow others to create and delete files in this folder 
3. allow nautilus to automatically add the correct permissions
4. log in as the other user & try to connect to the share with the other users credentials
5. not allowed to connect
6. I can connect with my credentials, but do not want to hand out my username and password to others.

What is the Ubuntu way of doing this properly?

The act of sharing data in a mutually accessible directory (folder) on one host has nothing to do with any of the above.

The share actions you are referring to are for sharing data from one host to another (via the network).

If you are only using one host (computer) then everything can be accomplished with both users being members of the same group.  Where this common group has the permissions to allow read/write (RW).  The folder that holds the information should **not **be in the /home file system.  I don't think you should use /mnt either.  The file system /mnt is really for removable media (CD, floppy, USB sticks, etc).

I would suggest using the /srv or /opt file systems.  You will need to create the folder using the ***sudo ***command and then you will need to change ownership and group of the folder.  If there is a common group that both of the users are a member of then you can use that group.  If not then you will have to create the group and add the users to the group.

On a single Linux machine the EXT 4 filesystem is very secure.  There is no need to use NTFS.

---

### Post by kadil on 2011-04-06
> **bab1 said:**
> The act of sharing data in a mutually accessible directory (folder) on one host has nothing to do with any of the above.

The share actions you are referring to are for sharing data from one host to another (via the network).

If you are only using one host (computer) then everything can be accomplished with both users being members of the same group.  Where this common group has the permissions to allow read/write (RW).  The folder that holds the information should **not **be in the /home file system.  I don't think you should use /mnt either.  The file system /mnt is really for removable media (CD, floppy, USB sticks, etc).

I would suggest using the /srv or /opt file systems.  You will need to create the folder using the ***sudo ***command and then you will need to change ownership and group of the folder.  If there is a common group that both of the users are a member of then you can use that group.  If not then you will have to create the group and add the users to the group.

On a single Linux machine the EXT 4 filesystem is very secure.  There is no need to use NTFS.

My experience with EXT4 has been that you can assign group privileges to a folder allowing file sharing on the same computer, but then every time a user saves a file in the folder, they have to set permissions to allow the group to read/write. Otherwise no one else can edit the file. This becomes tedious

My ntfs filesystems do not seem to suffer this situation. I would rather use the standard features if it will work well for me.

---

### Post by bab1 on 2011-04-06
> **kadil said:**
> My experience with EXT4 has been that you can assign group privileges to a folder allowing file sharing on the same computer, but then every time a user saves a file in the folder, they have to set permissions to allow the group to read/write. Otherwise no one else can edit the file. This becomes tedious

My ntfs filesystems do not seem to suffer this situation. I would rather use the standard features if it will work well for me.

I set the extended directory and file file permissions along with the stickey bit.  This allows you to set the directory owner:group and the files created will follow that ownership.  See [**[COLOR="Blue"]here[/COLOR]**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for a complete description.

---

### Post by kadil on 2011-04-06
> **bab1 said:**
> I set the extended directory and file file permissions along with the stickey bit.  This allows you to set the directory owner:group and the files created will follow that ownership.  See [**[COLOR="Blue"]here[/COLOR]**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for a complete description.

No gui ways to do this with gnome? mc is my friend

---

### Post by bab1 on 2011-04-06
> **kadil said:**
> No gui ways to do this with gnome? mc is my friend

Not that I know of in Gnome (Nautilus).  If you never learn the CLI, you will always be limited when using Linux.  What's mc?

---

### Post by kadil on 2011-04-06
> **bab1 said:**
> Not that I know of in Gnome (Nautilus).  If you never learn the CLI, you will always be limited when using Linux.  What's mc?

Yeah, I'm ok with the command line, but I would like to be able to get others to do it sometime and they are "more proficient with a mouse"

mc - midnight commander, very powerful text based file manager. It has been in my tool kit every install since the 2 floppy disk slackware days.

---

### Post by kadil on 2011-04-06
> **kadil said:**
> Yeah, I'm ok with the command line, but I would like to be able to get others to do it sometime and they are "more proficient with a mouse"

mc - midnight commander, very powerful text based file manager. It has been in my tool kit every install since the 2 floppy disk slackware days.

Interesting konqueror, dolphin and mc all have gui control. Come on Gnome, catch up

---

### Post by Morbius1 on 2011-04-06
> I want to share a folder with another user on the same computer, so we  both have read and write access to the files and create and delete  access to folders within.```
sudo chown :plugdev /path/to/shared/folder
sudo chmod 2770 /path/to/shared/folder
```Edit /etc/profile as root, Find the line at the bottom that references umask and change it to:
```
umask 002
```Logout and log back in again since profile is read only once at login.

- All users are members of the plugdev group by default in Ubuntu.
- The "2" in the chmod command sets the setgid bit on so that every new file added will inherit the group of the folder.
- By default ( in /etc/profile ) every new folder / file created will have permissions of 755 / 644. The owner can read and write but everyone else can only read. Changing the umask to 002 will make new entries have permissions of 775 / 664. The owner and group will now have read / write access.

You can have a gui do the chown / chmod stuff but there is no gui for the umask stuff.

If you want to make it more restrictive ( 2 users sharing a folder out of many ) then create a new group, add the users to that group, and change the chown command above to reflect that group.

*[COLOR=Blue] BTW, You might want to change the title of your topic to something other than Samba.[/COLOR]*

---

### Post by bab1 on 2011-04-06
> **Morbius1 said:**
> ...
- The "2" in the chmod command sets the setgid bit on so that every new file added will inherit the group of the folder...

I use "3" this also sets the sticky bit along with the setguid bit.  That way only the owner of the file is able to delete the file.

---

### Post by Morbius1 on 2011-04-06
> **bab1 said:**
> I use "3" this also sets the sticky bit along with the setguid bit.  That way only the owner of the file is able to delete the file.
I started out using a "3" but the original requirement of the user states:
> so we  both have read and write access to the files and create and delete  access to folders withinI interpreted that to mean either user can delete anyone's file. If my assumption is incorrect then you are quite right.

---

### Post by kadil on 2011-04-07
Thanks, looks perfect. BTW everyone is trusted to read, write, create, delete everyones files/directories.

---

### Post by kadil on 2011-04-09
Is there any down side to the setting umask 02? Risks?

---

### Post by kadil on 2011-04-09
This is very interesting, I have tested the group and umask method, and have found that I can read/write/create/delete as I specified, but an unexpected side effect is that you can only change the permissions of any file in the directory if you were the creator of the file. But I can create a copy, delete the original and then change permissions.

That works for me.

---

### Post by Morbius1 on 2011-04-09
> **kadil said:**
> Is there any down side to the setting umask 02? Risks?
Changing the default umask from 022 to 002 does look spooky at first since it then allows group write access to all new files. But what's really happening is this:

Default umask new file creation:
owner : group = morbius : morbius
permissions = 644
Only morbius can write to the file.

New default umask file creation:
owner : group = morbius : morbius
permissions = 664
Only morbius can write to the file. The exception would be those parent directors marked with setgid.

---

### Post by Morbius1 on 2011-04-09
> **kadil said:**
> Thanks, looks perfect. BTW everyone is trusted to read, write, create, delete everyones files/directories.
That's where the "3" suggested by bab1 comes in. If you change the chmod command to this:
```
sudo chmod 3770 /path/to/shared/folder
```Then everyone will be able to edit each others files and add files to the directory but only the owner of the file, the owner of the directory where the file is located, and root can delete the file.

---

