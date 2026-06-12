---
title: "Samba and WindowsXP login error"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by elbryan on 2006-06-09
Hi!
I'm sorry if this will be a repeated question but I haven't found an answer for my problem.

I've just installed and configured my Samba daemon on kubuntu.

This is my home-network:
PC (Ubuntu) --> Router --> Notebooks

On Notebooks there are Windows XP and I want to share a partition with samba.

When I try to connect on ubuntu (192.168.0.1) show up my shared connections but when I try to open a folder I reached 3 different answer.
- You can't connect. Contact administrator
- Login (user e password)
- Login (with user: 192.168.0.1/Guest [That i can't modify]) and it asks only for a password that I don't know.

My Samba is configured with Share but I can't surf the network ..

What should I do? Have I to add some user?
If you need to see my samba.conf or some screenshot from samba server let me know, I'll show them up to you ^^

Bye :)

---

### Post by RudolfMDLT on 2006-06-09
Hi there!

First - make sure all the PC's are on the same workgroup - Change it to HOMENET or BRYANNET or
any other clever name you can think of.

Then share files on all the PC's. In windows, don't use the wizard - just enable file sharing.

Then you have to add users to the Ubuntu machine so that the windows PC's can access it.
First you have to add users to the Unbuntu PC user list:
SYSTEM=>ADMINISTRATION=>USERS AND GROUPS.
Add a user for every laptop that you have.


Now you need to add the users to Samba:
This is done in the terminal:

1) sudo smbpasswd -e yourname (you're user name)
2)Type and retype new Samba password
3)sudo smbpasswd -a XP username (kitchenpc)
(the usernames of your network users)
4)Type and retype their passwords

You have to redo step 1 and 2 every terminal session - so first add all the users to the users and groups list and then do the Terminal part where you only have to repeat steps 3 and 4 for every user added.

Now when the login pops up from the XP side you can just login and everything should work fine!

When sharing files on the ubuntu side, under the "windows settings", also make sure that you have a workgroup identical to your windows machines and disable wins server.

After doing all of the above, go to the terminal and type "smbtree" and see if you can see all the computers on your network.

For more, see this how to:

[http://ubuntuguide.org/#networking](http://ubuntuguide.org/#networking)

---

### Post by elbryan on 2006-06-09
Thank you!!
The thing i hadn't understood was to create the user in linux with XP username ..
Now it works very well .. no login prompt .. fantastic ^^

Thank you! :)

---

### Post by RudolfMDLT on 2006-06-10
[QUOTE=elbryan]Thank you!!
The thing i hadn't understood was to create the user in linux with XP username ..
Now it works very well .. no login prompt .. fantastic ^^

Thank you! :)[/QUOTE]
My pleasure! I'm glad that you got sorted! :cool:

---

