---
title: "Share a folder from Ubuntu - access rights"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by Mujaheiden on 2009-02-18
Hi, I've made a folder, /home/shared/ and shared it via the default 8.10 share this folder procedure. I have set the permissions to 777 as I have no concern that the other user will mess up the files. The folder is owned by "root" 

However, whenever the windows user, who is using the shared folder too, is putting files there, they are owned by "nobody", and "nogroup". And if I then want modify them, i get permission errors. 

What do I have to change that we all have the same - full - rights on this shared folder?

---

### Post by theDaveTheRave on 2009-02-18
Mujaheiden

it sounds like you have a users and groups issue.

make sure that the user name and password for the remote access is in the same group as you are.

Or alternatively, you have probably allready set up a user <samba> and group <samba>, but it sounds like you need to add the name for the samba user to this group (or another newly created one) and then ensure that your personal username is also added to the group of <samba>.

There is another alternative.

If you have the space to have a separate partition you could create a partition in fat32 - which doesn't support this type of user/group password access (if I remember correctly that is) - but that is probably a bit silly!

hope that helps.

David.

---

### Post by mozkill on 2009-02-18
i think there is a config file for Samba that lets you map a windows use to a Linux user.  in that case files would be created "as" the linux user and would therefore have a group.

i think "nobody" is the same group that Samba runs as and so when files are created, samba is masking the user and using its own group to create the files. 

to fix the problem you have to configure samba 1 of 2 ways:

-----------

class_a=fsmith
class_a=bsmith
class_b=lsmith
class_c=gsmith
class_c=rsmith

Once you've created the username map file, put a reference to its location in the [global] section of the /etc/samba/smb.conf file. I placed it in the /etc/samba directory, because that made sense organizationally. Therefore, that line looks like this ...


username map = /etc/samba/user.map

OR OR  OR


mabye this would work:

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
[homes]
comment = Home Directories
browseable = yes

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
valid users = %S

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
writable = yes


then map the drive from windows using:
\\ubuntumachine\username



Please let us know which idea works for you.

---

### Post by Mujaheiden on 2009-02-19
Hi, thanks for your fast feedback. I dont really consider myself as a noob, but somehow this samba thing always catcvhed me offguard.

But there have been some developments here -there was this funny malware in the Win machine disguising as a virusscannere "AV 360" (yeah right), and were new working here, so decided what the heck, and moved the other pc to ubuntu too. But the issue is still the same. I've now added a group samba and put myself and user samab in it (I cant add "nobody"). But the issue remains - the remote user can do whatever, but when she creates files, i cant modify them. There still in the nobody/nogroup permission group?

---

### Post by Mujaheiden on 2009-02-20
oh silly me, when using ubuntu i can just share a folder over ssh. isnt there a way to do that on a win32 box too, to "mount" an ssh folder?

---

### Post by Mujaheiden on 2009-02-24
many things happened - i even created a fat 32 partition, but as im not the owner, i dont think i can share it. Finally i did this;

in smb.conf, ni global i wrote

guest account = Mujaheiden
force group = Mujaheiden
force user = Mujaheiden

which is me, the root. Probably some securityhazard, but i dont think my colleague will do me over. I spend almost a day to figure this out...

---

