---
title: "Jaunty .ssh file does not appear in Home Dir"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by JoeEndUser on 2009-12-11
I'm using Jaunty Desktop. I can connect fine to two users on my desktop via ssh. The user management page [http://help.ubuntu.com/9.04/serverguide/C/user-management.html]("http://help.ubuntu.com/9.04/serverguide/C/user-management.html") says that their should be an .ssh file in the users' home directory, but I only find one in the originally created users' home folder.

The goal is to turn off ssh/sftp access to individual users. Denying passwords and users doesn't seem to work after someone already has a key. 

Maybe there is a difference in handling between desktop and server?

If anyone could point me in the right direction, I would really appreciate it.

---

### Post by lewisforlife on 2009-12-11
You can just create a .ssh directory in the home folders of whatever users that you need to configure.  Once the directory is created, you can creat files like .authorized_hosts etc...
 
Did you say you were trying to connect to users on your desktop, from another user on your desktop?  If this is so, why are you using ssh?  Or did I misunderstan?

---

### Post by JoeEndUser on 2009-12-11
Thank you for the reply. I see now that I wasn't very clear there. Besides wanting remote access for myself, occasionally I need to set up secure ftp for someone. Instead of creating and deleting accounts, I thought it would be nice to have a generic account that I could turn on and off.

I was expecting the .SSH file to be auto-generated, but it sounds like I need to research how to generate keys or copy keys and create a .ssh/authorized_keys file in the generic account.

BTY, the same user management page states rather glibly, "Be sure to check for any established SSH connections by the disabled user." Any idea how I would do that? Maybe I need a server monitor?

---

### Post by lewisforlife on 2009-12-11
Not sure about the last part, but check out [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys), there is some really good information on setting up OpenSSH Keys.

---

