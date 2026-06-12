---
title: "Help managing a secondary Desktop user account from a primary 'Administrator' account"
date: 2020-04-15
forum: MINT
---

### Post by PaulM55 on 2020-04-15
I'm a long time user of Ubuntu, and recently Linux Mint, but have to date only had a single user on each of my PCs. I now find myself needing to create a PC with two users, an Administrator, with access to all files and folders, and a Desktop user (my granddaughter for home schooling) with a limited Desktop user account login.

I can easily create the accounts and set them up, but I've hit a problem with permissions. If I log in to my administrator account I don't have full access to the desktop user files and folders unless I use the 'sudo' command. If I use 'sudo' access to create any files or folders in the desktop user account they are not accessible by the desktop user, as the are owned by 'root', unless I manually change the permissions of each file and folder as I go along. I've also set up Timeline and DejaDup in my administrator account, writing data to a third disk partition (I have root and home partitions set up) but their access mounts this partition as 'root' so it cannot be accessed from either of the two user accounts. Additionally if I SSH into the PC from elsewhere using my administrator credentials I also don't have full access to the desktop user files or folders or the third partition.

What I would like to do is to set up the administrator account as normal, then add the desktop user account such that the administrator login has full access to everything in the desktop user account and any files I create in the desktop user account are automatically accessible by the desktop user. I need the same for a remote SSH connection logged in with the administrator user credentials. I've googled this at length, and posted a request for help in the Linux Mint forums, but failed to find a workable solution to date. I know it's to do with setting permissions and groups, but exactly how to set up the second user and third data partition to achieve what I want to do has so far eluded me. Any pointers to how to do this would be most welcome.

Regards
PaulM

---

### Post by howefield on 2020-04-15
Moved to the "MINT" forum.

---

### Post by yancek on 2020-04-15
Some of what you describe is standard and expected behavior.  Copying a file as root (using sudo) will make the owner of the file root.  There are ways to recursively change owner:group and permissions.  You can add a user to a group and give that group write permissions. Directories on partitions outside the /home/user directory are generally owned by root, that is default behavior and again can be changed. The link below is the Ubuntu documentation on using sudo which should be useful reading.  The second link has some detailed documentation on permissions in ubuntu as well as changing owner:group.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by PaulM55 on 2020-04-16
> **howefield said:**
> Moved to the "MINT" forum.

Thanks, I've already asked in the Mint forums and had no replies.

PaulM

---

### Post by PaulM55 on 2020-04-16
> **yancek said:**
> Some of what you describe is standard and expected behavior.  Copying a file as root (using sudo) will make the owner of the file root.  There are ways to recursively change owner:group and permissions.  You can add a user to a group and give that group write permissions. Directories on partitions outside the /home/user directory are generally owned by root, that is default behavior and again can be changed. The link below is the Ubuntu documentation on using sudo which should be useful reading.  The second link has some detailed documentation on permissions in ubuntu as well as changing owner:group.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thanks for your reply.

Yes I'm aware some of this is standard behaviour and I'm familiar with the sudo system which allows manual intervention when required. I spent a while trawling through docs on permissions, groups etc. and concluded what I am trying to achieve is not easily done on a Linux PC. Pity, I'm old enough to remember this sort of thing used to be standard practice on the old multi-user Unix computers that were around when I was growing up.

I shall just set up another PC solely for my granddaughter, give her administrative rights and sort out the problems when she manages to mess things up. At least SSH will work without any problem so I can sort it out remotely.

PaulM

---

### Post by TheFu on 2020-04-16
> **PaulM55 said:**
>   what I am trying to achieve is not easily done on a Linux PC.  

That is incorrect.  I can understand someone not used to dealing with groups and users and permissions getting confused.  There is nothing special about the Ubuntu permissions, groups, or users. They work exactly as they would on a Unix server.  Local and remote, doesn't matter, provided you use normal Unix tools like ssh, NFS, and tools based on those for your admin use (scp, rsync, sftp).

The "administrator account", as you call it,  a normal user account that happens to be a member of the sudo group.  Nothing magical about it. Any userid that is part of the sudo group would have the same level of control, be able to use sudo to elevate permissions to different accounts, not just root.  This is all standard stuff.

I'm unwilling to provide step-by-step instructions.  There are many trivial details, but the broad strokes are very easy.

Let's assume pc1 and pc2, both running Ubuntu Server or Desktop
Let's also assume user1 and user2 are created on each - in that order.
user1 with 1000:1000
user2 with 1001:1001
for the uid:gid

The version of the OS doesn't matter any supported release - so 16.04, 18.04, 19.10 or 20.04 if you are feeling lucky.  I won't be installing 20.04 until at least mid-June and only on test systems.  What comes next isn't ubuntu or Linux or Unix specific. These are all VERY, VERY, standard things.

Install pc1 and pc2 using the same userid when prompted.  This will create that first account with a uid and gid of 1000:1000 on both machines.  Verify that the uid/gid on each system for each user1/2 match. The id command will help
```
id user1
id user2

```
user1 is in the sudo group, but user2 is not.  That's as desired.
Add user1 into the user2 group on both systems.  I don't recall off the top of my head how to do that. I'd just edit the file group directly. There are commands for that if you prefer or probably a GUI.  Logout and login again as user1 so the system sees the newgrp was added.  You can just type **newgrp** into a terminal, but that only makes the newgroup seen in that one terminal session and any child programs.  Probably easier to logout and login.

Again, the **id user1** will prove that user1 is in both the user1 and user2 groups (there will be a few others too).

Now you just need to ensure that user2 has a umask set to 002. This can be handled in many different ways, actually, I think that is the default.  Check it with the umask command.  0002 and 002 are the same, so don't worry.

Now that is done you don't need to use sudo to see or modify files in user2's directories.

Let's start with that.  For mounting storage, just make certain that the user2 group has the permissions you want. Don't confuse the user2 userid and the user2 groupid. They are completely separate. The names matching is unimportant and coincidence only.  IF you like, you could edit the files in /etc for passwd, groups and gshadow to change the name to something else - "users" is common. Don't change the gid (the number/1001) and all will be fine.

By keeping the numbers for uid/gid the same on all systems in your house, you'll make using NFS trivial.  Only the gid actually used by humans need to be correctly mapped 1-for-1. Don't worry about non-user accounts or groups.

When you setup storage, best to use native Linux file systems, so ext4 is best for ssd and spinning disks unless you have a specific need for another. The important part is to make normal Unix permissions work.  If NTFS or FAT-whatever are used, we don't have the same level of controls.  Mount the file system where you like, to make life easiest, probably best to put it under /media/ so that loosely constrained snap packages can access the storage.
With ext2/3/4 storage, you can just **chown** the storage as needed on the mount and setup group-sticky permissions so places that need to stay as user1 do and places that should be user2 for the group always default to that as well.  This is normal, Unix, permissions.

If NTFS or any other non-Linux file system is used, then the permissions are set across the entire file system at mount time. Different directories and files under the same mount cannot have different permissions .... well, without some multi-mount tricks.

This has steps to setup a directory that multiple userids can share and work in together:
[https://ubuntuforums.org/showthread.php?t=2382965](https://ubuntuforums.org/showthread.php?t=2382965)

For more coverage of users, groups, management commands, this book : [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has a chapter on each.

It really is simple stuff, once the concepts are understood.

---

### Post by PaulM55 on 2020-04-17
Thank you so much for that reply, I'm just about to sit down and set the system up. There are several things you mention that have clarified what I need to do, so thanks again for the info. I shall endeavour to document the process and post the instructions for others that may need to do the same.

PaulM

---

### Post by PaulM55 on 2020-04-17
Ok, I've made some progress. I've set up the PC with User1 as an Administrator (uid1000)  and Users as a Desktop user (uid1001).

I've run 'sudo usermod -a -G user2 user1', logged out and back in and this has added user1 to the user2 group.


Not sure about the 'umask' command, I've just assumed it's correct for now.

In order for user1 to have full access to the user2 desktop folders I did the following :


Navigated to /home and 'Opened as Administrator'.
Changed the user2 home folder 'Group' property to 'Create and delete files' and clicked 'Apply permissions to Enclosed Files'

I now have full create, read and write access to the user2 desktop from my user1 logon :-)

Now a question....

User1 can now create files and folders in the user2 desktop folders but they are understandably owned by user1, hence read only for user2. User and group permissions appear pretty straightforward and I can manually change permissions and ownership, but is there a simple way to automatically change the permissions or ownership of a file when I write it to the user2 folders so user2 automatically has read/write access ? I assume I could add user2 to the user1 group, but that would open the user1 desktop files and folders to abuse by user2. 

Many thanks for your assistance
PaulM

---

### Post by TheFu on 2020-04-17
Pretty easy when you know the concepts, right?

Learn about **chmod g+s** on directories to force a specific group to be applied to new files and subdirs. It only works when the group(s) involved are shared by the userids creating files. The goal is something like:
```
              drwxrw**s**---   user2    user2    Workspace/
```
although the "other" permissions of r-x are fine, which is what umask of 0002 causes.

I'm not certain what you've setup. Please post the output for **id user1** and **id user2**.  I'm concerned that the group inclusion is backwards. I've never used a GUI to manage permissions. Wouldn't trust any.

BTW, if your granddaughter is over 10, perhaps giving her full admin on the system, but not telling her, would be educational for her?  

Just make daily, versioned, backups of her files and the system settings and list of manually installed packages.  That should mean that restoring the system is something she can do in about 30 minutes ... or there will be a copy of important files so that 1 or 2 or a directory can be restored.  Just be certain that your backups track permissions over time.  A backup tool like duplicity or rdiff-backup captures not just the data, but the permissions as they change over time in extremely efficient versioning.  This is where simple mirror or cloning _cough_ backup tools fail.

When/if you want to setup NFS, post another thread if you need help.  NFS is really easy to setup assuming the userids and groupids are mapped 1-to-1 on all the systems.

---

### Post by PaulM55 on 2020-04-17
Yep, that's exactly what I needed, thank you, another step up the learning curve :-)

I applied 'chmod g+s .' in all the desktop folders, bar the desktop itself, and now all files written to or copied to those folders by user 1 have user2 as the group and are editable by user2.

The group inclusion isn't backwards, it's set up as required and the permissions are set up correctly.

Thanks for the offer, I already exclusively run NFS on our network. It always baffles me why Linux defaults to installing Windoze networking but omits NFS. I note your comment re user IDs being mapped 1:1 on all systems. The only niggle I have with NFS is I have mapped NAS drives on my PC and it hangs my desktop if the NAS goes offline for any reason. I gather from googling the problem this is a 'feature' of the NFS system.

My granddaughter is 12 and way ahead of me with phones and tablets. I'm encouraging her to become as technically competent with Linux but I think at present keeping the current home schooling requirement separate from her ability to delve into the OS will assist with retaining my sanity.

Thanks again for your assistance.

PaulM

---

### Post by TheFu on 2020-04-17
> **PaulM55 said:**
> <snip>
Thanks for the offer, I already exclusively run NFS on our network. It always baffles me why Linux defaults to installing Windoze networking but omits NFS. I note your comment re user IDs being mapped 1:1 on all systems. The only niggle I have with NFS is I have mapped NAS drives on my PC and it hangs my desktop if the NAS goes offline for any reason. I gather from googling the problem this is a 'feature' of the NFS system.
<snip> 

NFS supports a timeout, so when the remote storage isn't available, then it will only block for a short period.  Also, you can use the automounter, not a full-time fstab mount with NFS.

If you have a 100 Mbps network or faster, forcing all NFS to use TCP would reduce the chance of data corruption.

**autofs** is the older method to use the client-side automounter. It has well-used, well-understood, setup but is more complex than the newer, systemd-automount method available in 16.04 and later. An example:
[https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156](https://ubuntuforums.org/showthread.php?t=2437500&p=13935156#post13935156)

I've been using autofs for a very long time for NFS, CIFS, and USB storage. Basically, any storage that isn't always connected.  I wanted control over the mount options and especially the locations.  I've been badly burned by the /media/ use, plus permanent mounts aren't supposed to go there according to the file system hierarchy standards.  

Discovered the systemd-automount capability just a few months ago.  Been using it a few months.  Extremely solid and performs the same as autofs or simple fstab mounts. No issues with it at all.  I'll migrate off autofs completely. This is all client-side config. The NFS server still uses the /etc/exports file in the normal way.   My NFS servers never go off-line unless I take them down or there's a HW failure.

Guess we've beaten this topic.  If you think it is SOLVED, please use the Thread Tools and mark it so.

---

### Post by PaulM55 on 2020-04-18
Yes, this topic is now definitely solved thank you, the second PC is set up and working exactly as I wanted both locally and using remote access.

Ditto with my NAS server, on 24/7 unless I take it down. I run embedded XigmaNAS (was NAS4Free) from a USB memory stick on a Prolient MicroServer which, unfortunately, requires a reboot to upgrade the embedded software. It's quite slow upgrading, during which time my networked PCs are locked due to the NFS problem. I shall take a closer look at your comments re NFS when I get the time.

PaulM

---

### Post by PaulM55 on 2020-04-21
Not quite finally solved :-(

The files I'm copying to the desktop user folders are a mixture of created folders, downloaded doc, docx, pptx & pdf files and PDFs I've created. When copied some of them have the correct permissions applied, others don't, the group permission remains with me. Looking at the documentation for the 'g+s' option it's clear not all files and folders will necessarily have the changed permissions applied.

The simple solution seems to be to create a ZIP archive of the content to be copied, copy the *ZIP* archive across, then unzip the content. If I do this *ALL* content has the correct permissions applied :-)

PaulM

---

