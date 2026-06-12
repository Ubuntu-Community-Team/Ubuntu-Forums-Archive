---
title: "NFS mounting from server"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by sd@ksu on 2012-03-11
I have three computers with Ubuntu 11.04, one of them being treated as the NFS server. Now what I want is the following:
I am mounting the /home of the server (with same uid and gid) on both the clients. But I want to keep the settings/configuration for each user belonging to the individual client machine only. Say, I have an user called user in all three machines with same uid and gid. His files and settings are in /home/user on the individual machines. Now if I mount the /home of server on the clients then the settings corresponding to the server machine is available on the clients. The individual clients may have different resolution settings or other settings. But when the user logs in after nfs mount of server's home on client's home, the user will avail the settings corresponding to the server machine which might not be proper for the client machine. 
...
My aim is to keep same set of files in /home/user/Documents and all other visible folders in /home/user across the machines but the configuration settings of individual users should be local to the individual computer only. Can anyone tell me how to do it ?
...
At present I mount the server home on top of clients' home at boot when the filesystem comes up. But this does not help as in that case the /home is mounted from server before the users log in. And when the user logs in, he logs into the nfs filesystem and avails the settings from the server. But if I do not mount the nfs filesystem from the server at boot time and log into the client, I log into the local home of the client. And then if I manually mount the nfs filesystem (AFTER user HAS LOGGED INTO HIS ACCOUNT) on top of the local home of client, I still retain my local desktop background and settings but the files in the Documents , Downloads etc. are from the server itself, which is what I want precisely. But I want to automate the process. 
.....
If anyone can tell me how to start an upstart job at user log in, that might also help.

---

### Post by DrPotoroo on 2012-03-12
I could be wrong, but the manual mount after login approach sounds problematic - I imagine that at login time the user config files are READ, and the settings stored in memory. Then you are mounting the remote home dir over the top of those config files. So if the user then, say, changes their background image, the change will be WRITTEN to a config file on the server. Not what you want.

My recommendation would be to change your approach. Everything the user wants to be available from the server should be a subdirectory of home. Or you could even mount a few subdirectories from the server (would this create performance issues? - no idea).

Personally, for my setup I have a /share on my server that mounts to a /share on my local machines, and then in my user home dirs I use symlinks to subdirectories of that.

There probably is a better way to get closer to what you are after - but I can't think of one.

---

### Post by sd@ksu on 2012-03-12
@ DrPotoroo: Yes you are right when you say :
>  I imagine that at login time the user config files are READ, and the settings stored in memory. Then you are mounting the remote home dir over the top of those config files. So if the user then, say, changes their background image, the change will be WRITTEN to a config file on the server. Not what you want.

You have said : 
> Personally, for my setup I have a /share on my server that mounts to a /share on my local machines, and then in my user home dirs I use symlinks to subdirectories of that.
................
I have also mounted server/home to /local-share on each client. But then, when you create symlinks in your user home directory to the subdirectories there, they will be created separately right? I mean /home/user still has the Documents,Downloads, Programs etc. directories which belong to the local machine. Are you talking about creating a symbolic link such that when the user clicks or tries to access say, his Documents directory (by clicking on the /home/user/Documents or via command line), he/she will be directed to the same but in the /local-share/user/Documents? What happens in case he saves a file in /home/user/Documents ? Does it get saved in /local-share/user/Documents or not ? If you edit a file, does the actual changes get saved in the actual file ? If yes, this probably solves my problem. Please let me know.

---

### Post by DrPotoroo on 2012-03-12
Let's say you have two users, tarzan and jane. On your remote machine you have:
/home/tarzan
/home/jane

You have mounted this to /local-share on your client machines. So when the server is connected your local machines have:
/home/tarzan
/local-share/tarzan
/home/jane
/local-share/jane

What I am suggesting could be done in a few different ways. For example, on a client machine:
```
ln -s /local-share/tarzan /home/tarzan/share
ln -s /local-share/jane /home/jane/share
```From the user's perspective, this would put everything from the user's home on the server into a subdirectory called share in their local home directory. If they navigate into this directory, open a file there, save it, create a new file there - all of these things are actually happening on the server.  In practice whenever the user goes into that share folder in their home directory the filesystem is actually getting pointed to /local-share/user/. But to the user this is pretty transparent.

If the server gets disconnected the user will no longer be able to navigate into their share directory - but once the server is connected again, it is available to the users without having to recreate it with the above commands.

The alternative, which might be a little more intuitive for users because it would keep the same structure on the server as the client machines (if they ever work directly on the server), would be to create individual symlinks between EACH subdirectory of /home/user to an identically named link on each client. E.g.:
```
ln -s /local-share/tarzan/Documents /home/tarzan/Documents
ln -s /local-share/tarzan/Pictures /home/tarzan/Pictures
ln -s /local-share/tarzan/Videos /home/tarzan/Videos
...
```The down-side of this approach is if, say, Tarzan was to decide he wanted to have a directory My_Stuff in /home/tarzan. So on client machine 1 he creates My_Stuff in /home/tarzan. The next day he is on client machine 2 and wonders why /home/tarzan/My_Stuff isn't on that machine. That is because with the second approach he may not have realised that only certain directories WITHIN his home are on the server, and anything new he creates in his home is local only. But anything new he created in /home/tarzan/Documents WOULD be on the server. The first example works the same way, but it is probably easier for users to work out that there is just ONE parent directory under which EVERYTHING is shared than to understand there are two or three or more shared directories in their home.

Hope that makes sense.

EDIT: By the way, make sure when you create a link that the target doesn't already exist. For example, you would need to delete the local /home/tarzan/Documents before making a link from /local-share/... to that.

---

### Post by sd@ksu on 2012-03-14
After your suggestion and some reading for my user specific customization, I have done the following:
1) NFS mount: server:/home is mounted to /local-mount on clients. Using same UID and GID./local-mount has permissions 750 and is owned by root:root.

2) Also, I have edited /etc/xdg/user-dirs.defaults. In the NFS server, it is: 
```
# Default settings for user directories
DESKTOP=Desktop
BIN=Documents/bin
DATA=Documents/Data
#DESKTOP=Documents/Desktop
DOWNLOADS=Documents/Downloads
PAPERS=Documents/Papers
PRESENTATIONS=Documents/Presentations
TEMPLATES=Documents/Templates
WORK=Documents/Work

```
............
and in clients, everything inside /etc/xdg/user-dirs.defaults is commented out except DESKTOP=Desktop. This means no additional user directory is created when the user logs in. Instead, in next step, I use /etc/skel/.bashrc to generate a symbolic link to the relevant nfs mount.

3) In the /etc/skel/.bashrc, I have added the following:
```
# Create symbolic link if it does not exist
if [ ! -h $HOME/Documents ] ; then
#	echo "Creating symbolic link $HOME/Documents"
	ln -s /local-mount/$USER/Documents $HOME/Documents
fi

```
.....
This will create the symbolic link as desired.

4) I have removed examples.desktop from /etc/skel as it is not needed for any user.
5) In /etc/adduser.conf ,I have made the changes below:
> 
USERGROUPS=no  # this then assigns each user a group called users (gid=100)
#...
# also i have set 
DIR_MODE=0750
#...
# for desktop user
EXTRA_GROUPS="adm dialout fax cdrom floppy tape dip audio video plugdev fuse"
ADD_EXTRA_GROUPS=1

..............................
Now I reboot. And then 1st add a user by "adduser user" to the server. Log in. Next I go to the clients 1 and 2 and do the same.
And it does work!!!
But with a small problem.
If the server goes down while the clients are logged in, I have a small problem. If I want to cd to $HOME or pwd at $HOME it works, but if I do ll or ls in $HOME, the cursor will go on blinking indefinitely without giving any output. It seems I can mkdir aDirectory in $HOME but if I do ll it does not respond. The cursor goes down a line and keeps on blinking forever.If I open the home directory from the Places tab, it will open but shows it is busy (the mouse cursor) and nothing will show on the nautilus file viewer. If the server comes back inbetween, then after a considerable time of its coming back, things will become normal again. Can you please tell me where is the problem ? I am using UBUNTU 11.04. And VMWARE for these simulations before implementing on the real systems.

---

### Post by DrPotoroo on 2012-03-14
Unfortunately I don't think I can offer a solution to the hanging problem. I don't use NFS myself, I use samba because I am also sharing with a windows machine. But I have seen the same problem - if the server is mounted on a client then disconnects, the clients hang if the system in any way tries to look at the shared location. I would assume this is what happens when you ll in home - it tries to resolve the link to the share.

If you can "know" that the server is going to go down, unmounting the share on all the clients should prevent hanging. I have been trying to work out a way myself to send a wake-on-lan packet to my server if a client is trying to access a file on the share and detects the server is not running - but I have yet to work out how calls to certain file locations could trigger an upstart event.

---

### Post by sd@ksu on 2012-03-15
Ya it just persists...annoying...could it be a bug ? [REFER HERE]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760744")

---

### Post by sd@ksu on 2012-03-15
It is really annoying..As few people suggested, I have used "soft" and "intr" options but with no luck!! I think I have to bear with this as long as I am using NFS. Any other suggestion is waited.

---

