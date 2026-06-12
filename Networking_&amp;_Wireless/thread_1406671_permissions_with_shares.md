---
title: "permissions with shares"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by crewbie21 on 2010-02-14
Hi,

   I've been using Ubuntu for about 2 years now, but still have trouble with some of the finer workings of linux. I have a laptop that I use for general computing, and a desktop hooked up to a TV as sort of a remote backup/htpc. A problem I run into is when I transfer files, they get transfered with the owner set as the original computer's account, and I can't do anything until I open a remote viewer and gksudo nautilus to change the permissions of the file. I looked at articles about permissions and uid's, gid's, and umask but can't figure out how to apply it to my situation. I thought about doing something with groups but am not sure exactly what, and anyway, default group settings only give read access and what I'm really looking for is the ability to manipulate files and folders across the entire /home dir on my desktop from my laptop. Desktop is running 8.04 and laptop is running 9.10.

   BTW I am currently sharing through smbfs. I read that this has been replaced by cifs, but at the moment I would prefer not the mess with things if I don't need to.

Thank you in advance for your help.

---

### Post by supershin on 2010-02-14
I think you want to make a group, say home, and add the username of your laptop and desktop to the group. Then set the group permissions. That way users in the group have the same permissions so both users can do the same things.

---

### Post by crewbie21 on 2010-02-14
i added my laptop account to the same group as my desktop account, then went to the Home folder and set the correct group with read and write permissions for folders and files, and hit the button to apply the settings to all enclosed files, but when I transfer a test file is still gets set with the owner as my laptop account and group settings are read only.

---

### Post by supershin on 2010-02-20
Is it that you're trying to set the home folder of the desktop to be read/write by the group? 
Then i suppose you could try executing these commands on the desktop.
sudo addgroup <groupname>
sudo adduser <desktop-username> <groupname>
sudo adduser <laptop-username> <groupname>
sudo chmod 774 /<desktop-username>/home

Above should:
create a group with the name you specify.
add the desktop username to the group.
add the laptop username to the group.
set the desktop home folder to be read/write/execute by the owner, the group and only be read by others.

Note the desktop home folder owner will still be the desktop-username but you should be able to read/write/execute with members of the group.

Any more ideas, anyone?

---

